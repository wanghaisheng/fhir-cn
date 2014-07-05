title:  
date:  
categories: impl
---

## <span class="sectioncount">2.1<a name="2.1"> </a></span> RESTful API

Each resource type has the same set of interactions defined that can be used to manage the resources 
in a highly granular fashion. Applications claiming conformance to this framework
claim to be conformant to &quot;RESTful FHIR&quot;.

Note that in this RESTful framework, transactions are performed directly on the server resource using an 
HTTP request/response. The API does not directly address authentication, authorization, and audit
collection - for further information, see the [Security Page](security.html).

The API describes the FHIR resources as a set of operations (known as &quot;interactions&quot;) on resources where individual
resource instances are managed in collections by their type. Servers can choose which of 
these interactions are made available and which resource types they support. Servers SHALL
provide a [conformance statement](conformance.html) that specifies what interactions and 
resources are supported.

The following logical interactions are defined:

<a name="interactions"> </a>
<a name="operations"> </a>
<table class="list"> 
  <tr><td>**Instance Level Interactions**</td><td/></tr>
  <tr><td>[read](#read)</td><td>Read the current state of the resource</td></tr>
  <tr><td>[vread](#vread)</td><td>Read the state of a specific version of the resource</td></tr>
  <tr><td>[update](#update)</td><td>Update an existing resource by its id (or create it if it is new)</td></tr>
  <tr><td>[delete](#delete)</td><td>Delete a resource</td></tr>
  <tr><td>[history](#history)</td><td>Retrieve the update history for a particular resource</td></tr>
  <tr><td colspan="2">**Type Level Interactions**</td></tr>
  <tr><td>[create](#create)</td><td>Create a new resource with a server assigned id</td></tr>
  <tr><td>[search](#search)</td><td>Search the resource type based on some filter criteria</td></tr>
  <tr><td>[history](#history)</td><td>Retrieve the update history for a particular resource type</td></tr>
  <tr><td>[validate](#validate)</td><td>Check that the content would be acceptable as an update</td></tr>
  <tr><td colspan="2">**Whole System Interactions**</td></tr>
  <tr><td>[conformance](#conformance)</td><td>Get a conformance statement for the system</td></tr>
  <tr><td>[transaction](#transaction)</td><td>Update, create or delete a set of resources as a single transaction</td></tr>
  <tr><td>[history](#history)</td><td>Retrieve the update history for all resources</td></tr>
  <tr><td>[search](#search)</td><td>Search across all resource types based on some filter criteria</td></tr>
</table>

In addition to these operations, there is a [Mailbox](messaging.html#mailbox) and [Document](documents.html#bundle) endpoint.

**Style Guide**

URL operations on this pages are defined like this:

<pre>
  OPERATION [base]/[type]/[id] {?_format=[mime-type]}
</pre>

*   The first word is the HTTP verb used for the operation
*   Content surrounded by [] is mandatory, and will be replaced the string literal identified. Possible insertion values:

        *   **base**: The [Service Root URL](#root)
    *   **mime-type**: The [Mime Type](#mime-type)
    *   **type**: The name of a resource type (e.g. &quot;Patient&quot;)
    *   **id**: The [Logical Id](resources.html#metadata) of a resource
    *   **vid**: The [Version Id](resources.html#metadata) of a resource
    *   **compartment**: The name of a [compartment](extras.html#compartment)
    *   **parameters**: URL parameters as defined for the particular operation
*   Content surrounded by {} is optional
<a name="root"> </a>
<a name="general"> </a>

### <span class="sectioncount">2.1.1<a name="2.1.1"> </a></span> Service Root URL

The Service Root URL is the address where all of the 
resources defined by this interface are found. The Service 
Root URL takes the form of 

<pre>
http(s)://server{/path}
</pre>

The path portion is optional, and does not include a trailing slash. Each 
resource type defined in this specification has a manager (or &quot;entity set&quot;)
that lives at the address &quot;/[type]&quot; where the
&quot;type&quot; is the name of the resource type. 
For instance, the resource manager for the type 
&quot;Patient&quot; will live at:

<pre>
https://server/path/Patient
</pre>

All the logical interactions are defined relative to the service root
URL. This means that if the address of any one FHIR resource on a system 
is known, the address of other resources may be determined. 

Note: All URLs (and ids that form part of the URL) defined by this specification are case sensitive.

Note that a server may use a path of the form &quot;http://server/...[xx]...&quot; where the [xx] is some variable 
portion that identifies a particular instantiation of the FHIR API. Typically, the variable id 
identifies a patient or a user, and the underlying information is completely compartmented 
by the logical identity associated with [xx]. In this case, the FHIR API presents a 
patient or user centric view of a record, where authentication/authorization is 
explicitly granted to the URL, on the grounds that some identifiable user is associated
with the logical identity. It is not necessary to explicitly embed the patient id in the 
URL - see [Compartments](extras.html#compartments) for an alternative approach.

### <span class="sectioncount">2.1.2<a name="2.1.2"> </a></span> Resource Metadata and Versioning

Each resource has an associated set of [resource metadata elements](resources.html#metadata). These map to the http request and response using the following fields:

<table class="grid">
  <tr><th>Metadata Item</th><th>Where found in HTTP</th></tr>
  <tr><td>[Logical Id](resources.html#metadata)</td><td>The Id is represented explicitly in the URL</td></tr>
  <tr><td>[Version Id](resources.html#metadata)</td><td>The Version Id is represented by the full canonical URL in the content-location header (see [vread](#vread) below). 
     The Version Id may also be represented in the http ETag, but the use of ETag is not needed by this specification</td></tr>
  <tr><td>Last Modified Date</td><td>HTTP Last-Modified header</td></tr>
</table>

### <span class="sectioncount">2.1.3<a name="2.1.3"> </a></span> Security

<p>
Using HTTPS is optional, but all production exchange of healthcare data SHOULD use SSL and additional security as appropriate. See [HTTP Security](security.html#http) for further information.

Note: to support browser-based client applications, recommend that servers SHOULD implement [cross-origin resource sharing](http://enable-cors.org/) for the operations documented here.  

### <span class="sectioncount">2.1.4<a name="2.1.4"> </a></span> HTTP Status Codes

This specification makes rules about the use of specific HTTP status codes 
in particular circumstances where the status codes SHALL map to particular 
states correctly, and only where the correct status code is not obvious. 
Other HTTP status codes may be used for other states as appropriate, and this particularly
includes various authentication related status codes and redirects. 
Authentication redirects should not be interpreted to change the location 
of the resource itself (a common web programming error). 

FHIR defines an [OperationOutcome resource](operationoutcome.html) that can be used to convey specific detailed
processable error information. For a few combinations of interactions and specific
return codes, an OperationOutcome is required to be returned as the content of the response. 
The OperationOutcome may be returned with any HTTP 4xx or 5xx response, but is not required - many of 
these errors may be generated by generic server frameworks underlying a FHIR server.

<a name="mime-type"> </a>

### <span class="sectioncount">2.1.5<a name="2.1.5"> </a></span> Content Types and encodings

The formal MIME-type for FHIR resources is application/xml+fhir or application/json+fhir.
The correct mime type SHALL be used by clients and servers:

<table class="grid">
<tr><th/><th>xml</th><th>json</th></tr>
<tr><td>Resource</td><td>application/xml+fhir</td><td>application/json+fhir</td></tr>
<tr><td>Bundle</td><td>application/atom+xml</td><td>application/json+fhir</td></tr>
<tr><td>TagList</td><td>application/xml+fhir</td><td>application/json+fhir</td></tr>
</table>

Servers SHALL support server-driven content negotiation
as described in [section 12](http://www.w3.org/Protocols/rfc2616/rfc2616-sec12.html#sec12) 
of the HTTP specification.

However in order to support various implementation limitations, servers SHOULD 
support the optional &quot;_format&quot; parameter to specify alternative response formats by their MIME-types.
This parameter allows a client to override the header value when it is unable to set it correctly 
due to internal limitations.
For the _format parameter, the values &quot;xml&quot;, &quot;text/xml&quot;, &quot;application/xml&quot;, and &quot;application/xml+fhir&quot; SHALL be interpreted to mean
the normative XML format defined by FHIR and &quot;json&quot;, &quot;application/json&quot; and &quot;application/json+fhir&quot; SHALL be interpreted to mean the
informative JSON format.

FHIR uses UTF-8 for all request and response bodies. Since the HTTP specification (section 3.7.1)
defines a default character encoding of ISO-8859-1, requests and responses SHALL explicitly set
the character encoding to UTF-8 using the 'charset' parameter of the MIME-type in the Content-Type header. 
Requests MAY also specify this charset parameter in the Accept header and/or use the Accept-Charset header.

<a name="read"> </a>

### <span class="sectioncount">2.1.6<a name="2.1.6"> </a></span> read

The read interaction accesses the current contents of a resource. The interaction
is performed by an HTTP GET command as shown:

<pre>
  GET [base]/[type]/[id] {?_format=[mime-type]}
</pre>

This returns a single instance with the content specified for the resource type.
This url may be accessed by a browser. The possible values for the 
[Logical Id](resources.html#metadata) (id) itself are described in the [id type](datatypes.html#id).
Servers are required to return a content-location header with the response which is the full version 
specific url (see vread below) and a Last-Modified header.
<p>
Note: Unknown resources and deleted resources are treated differently on a read: A GET for a deleted 
resource returns a 410 status code, whereas a GET for an unknown resource returns 404. Systems that do 
not track deleted records will treat deleted records as an unknown resource.

</p>
<a name="vread"> </a>

### <span class="sectioncount">2.1.7<a name="2.1.7"> </a></span> vread

The vread interaction preforms a version specific read of the resource. The interaction
is performed by an HTTP GET command as shown:

<pre>
  GET [base]/[type]/[id]/_history/[vid] {?_format=[mime-type]}
</pre>

This returns a single instance with the content specified for the resource type for that
version of the resource. 
  <!-- this - what does it mean?
Servers may return a content-location header with the response which is the url 
requested and a Last-Modified header. -->

The [Version Id](resources.html#metadata) (vid) is an opaque identifier that conforms to the same [format requirements](datatypes.html#id) as 
a [Logical Id](resources.html#metadata). The id may have been found by performing a history interaction (see below), by recording the 
version id from a content location returned from a read or from a version specific reference in a 
content model. If the version referred to is actually one where the resource was deleted, the 
server should return a 410 status code.

Servers are encouraged to support a version specific retrieval of the current version of the 
resource even if they are do not provide access to previous versions. If a request
is made for a previous version of a resource, and the server does not support accessing
previous versions, it should return a 405 Method Not Allowed error.

<a name="update"> </a>

### <span class="sectioncount">2.1.8<a name="2.1.8"> </a></span> update

The update interaction creates a new current version for an existing resource or 
creates a new resource if no resource already exists for the given id. 
The update interaction is performed by an HTTP PUT command as shown:

<pre>
  PUT [base]/[type]/[id] {?_format=[mime-type]}
</pre>

If the interaction is successful, the server SHALL return either a 200 OK if the resource was updated, or a 201 Created if the resource was created,
with a Last-Modified header, and a Location and Content-Location header that refers to the specific version created by the 
update interaction. The server MAY send an OperationOutcome resource with hints and warnings about the resource; if one is sent it SHALL not include any errors.

Servers are permitted to reject update interactions because of integrity concerns or business 
rules implemented on the server, and return HTTP status codes accordingly (usually 422). 
A server SHOULD accept the resource as submitted when accepts the update, and return the same
content when it is subsequently read. However systems may not be able to do this; see 
the note on [transactional integrity](#transactional-integrity) for discussion. 

In particular, servers may choose to implement version-aware updates, where the only updates that are 
accepted quote the current version of the resource. In this case, the client must submit the currently 
correct version specific URL in the Content-Location in the PUT request. If the value is missing, 
the server SHALL return a 412 Preconditions failed response. Clients SHOULD submit a proper Content-Location 
header and SHALL correctly understand a 409 response as an update conflict.

Common HTTP Status codes returned on FHIR-related errors (in addition to normal HTTP errors related to security, header and content type negotiation issues):

*   **400 Bad Request** - resource could not be parsed or failed basic FHIR validation rules
*   **404 Not Found** - resource type not supported, or not a FHIR end point
*   **405 Method Not allowed** - the resource did not exist prior to the update, and the serer does not allow client defined ids
*   **409/412** - version conflict management - see above
*   **422 Unprocessable Entity** - the proposed resource violated applicable FHIR profiles or server business rules. This should be accompanied by an [OperationOutcome](operationoutcome.html) resource providing additional detail

Note: Servers MAY choose to preserve XML comments, instructions, and formatting or JSON whitespace when accepting updates, but are not required to do so. The impact of this on digital signatures may need to be considered.

<a name="delete"> </a>

### <span class="sectioncount">2.1.9<a name="2.1.9"> </a></span> delete

The delete interaction removes an existing resource. The interaction
is performed by an HTTP DELETE command as shown:

<pre>
  DELETE [base]/[type]/[id] 
</pre>

A delete interaction means that [non-version specific reads](#read) of a resource 
return a 410 error and that the resource is no longer found through search interactions. Upon successful
deletion the server should return 204 (No Content). The server MAY send an OperationOutcome resource with hints and warnings about the deletion; if one is sent it SHALL not include any errors.

If the server refuses to delete resources of that type on principle, then it should return the status code 
405 method not allowed. If the server refuses to delete a resource because of reasons specific 
to that resource, such as referential integrity, it should return the status code 409 Conflict.
If the resource cannot be deleted because it does not exist on the server, the server SHALL return 404 (Not found).
Performing this interaction on a resource that is already deleted has no effect, and should return 204.
Resources that have been deleted may subsequently be brought back to life by PUTting an update to them 
subsequent to the deletion. 

Many resources have a status element that overlaps with the idea of deletion. Each resource type
defines what the semantics of the deletion interactions are. If no documentation is provided, the 
deletion interaction should be understood as deleting the record of the resource, with nothing
about the state of the real-world corresponding resource implied.

<a name="create"> </a>

### <span class="sectioncount">2.1.10<a name="2.1.10"> </a></span> create

The create interaction creates a new resource in a server assigned location. If the client 
wishes to have control over the id of a newly submitted resource, it should use the update 
interaction instead. The create interaction is performed by an HTTP POST command as shown:

<pre>
  POST [base]/[type] {?_format=[mime-type]}
</pre>

The server returns a 201 Created, along with 
a Location header which contains the new [Logical Id](resources.html#metadata) and [Version Id](resources.html#metadata) of the created resource:

<pre>
  Location: [base]/[type]/[id]/_history/[vid]
</pre>

Where [id] and [vid] are the newly created id and version id for the resource. The server MAY send an OperationOutcome resource with hints and warnings about the resource; if one is sent it SHALL not include any errors.

When the payload data is incorrect and cannot be used to create a new resource, the server returns a 400 Bad Request.

A server SHOULD accept the resource as submitted when accepts the create, and return the same
content when it is subsequently read. However systems may not be able to do this; see 
the note on [transactional integrity](#transactional-integrity) for discussion. 

Common HTTP Status codes returned on FHIR-related errors (in addition to normal HTTP errors related to security, header and content type negotiation issues):

*   **400 Bad Request** - resource could not be parsed or failed basic FHIR validation rules
*   **404 Not Found** - resource type not supported, or not a FHIR end point
*   **422 Unprocessable Entity** - the proposed resource violated applicable FHIR profiles or server business rules. This should be accompanied by an [OperationOutcome](operationoutcome.html) resource providing additional detail

Note: Servers MAY choose to preserve XML comments, instructions, and formatting or JSON whitespace when accepting creates, but are not required to do so. The impact of this on digital signatures may need to be considered.

<a name="search"> </a>

### <span class="sectioncount">2.1.11<a name="2.1.11"> </a></span> search

This interaction searches a set of resources based on some filter criteria. The interaction can be performed by several different HTTP commands. 
To search all resources at once:

<pre>
  GET [base]?[parameters] {&amp;_format=[mime-type]}
</pre>

To search a single resource type:

<pre>
  GET [base]/[type]?[parameters] {&amp;_format=[mime-type]}
  GET [base]/[type]/_search?[parameters] {&amp;_format=[mime-type]}
</pre>

To search a [compartment](extras.html#compartments):

<pre>
  GET [base]/[compartment]/[id]/?[parameters]  {&amp;_format=[mime-type]}
  GET [base]/[compartment]/[id]/[type]?[parameters]  {&amp;_format=[mime-type]}
</pre>

Because of the way that some user agents treat GET and POST requests, POST submissions to /_search 
are also allowed with exactly the same semantics as the equivalent GET command.
All these search interactions take a series of parameters that are a series of name'='value pairs 
encoded in the URL (or as an x-multi-part-form submission for a POST).
(See [W3C HTML forms](http://www.w3.org/TR/REC-html40/interact/forms.html#form-content-type)). 
Searches are processed as specified for the [Search/Query handling mechanism](search.html). 

If the search fails, the return value is a status code 4xx or 5xx with an [OperationOutcome](operationoutcome.html).
If the search succeeds, the return content is an [Bundle](extras.html#bundle) containing the results of the search as a list of resources
in a defined order. The result list can be long, so servers may use paging. If they do, they SHALL use the method described 
in [RFC 5005 (Feed Paging and Archiving)](https://tools.ietf.org/html/rfc5005) (also [see below](#paging)) for breaking the 
list into pages if appropriate. The server MAY also return an OperationOutcome resource with additional information about the search; if one is sent it SHALL not include any errors.

<a name="validate"> </a>
<a name="validation"> </a>

### <span class="sectioncount">2.1.12<a name="2.1.12"> </a></span> validate

The validate interaction checks whether the attached content would be acceptable as an 
update to an existing resource. The interaction is performed by an HTTP POST command as shown:

<pre>
  POST [base]/[type]/_validate{/[id]}
</pre>

The content is first checked against the general specification and against the conformance 
profile that applies to the application. Then, if the optional [id] section is 
also provided, the resource is considered as a proposed update to the specific resource, 
and additional instance specific rules such as referential integrity 
and update logic (including version control) are applied as well. 

The client can ask the server to validate against a particular resource by attaching
a [profile tag](extras.html#tags) to the resource. This is an assertion that 
the resource conforms to the specified profile(s), and the server can check this. 

How much checking to perform as part of the validation operation is at the 
discretion of the server. The server SHALL check all the things it requires
of the resource as part of it's normal operations, and MAY choose to validate
the resource against the schema and schematron provided as part of this
specification, and/or other profiles, including the one specified by the 
client.

The return content has one of the following values:

*   **400 Bad Request** - resource could not be parsed or had some basic FHIR validation error
*   **200 OK** - resource passed all validation rules
*   **422 Unprocessable Entity** - the resource was valid, but as a proposed update, it violates applicable FHIR profiles or server business rules

Unless the result is 200 OK, the response SHALL include an [OperationOutcome](operationoutcome.html) resource that lists the issues found on validation.

<a name="conformance"> </a>

### <span class="sectioncount">2.1.13<a name="2.1.13"> </a></span> conformance

The conformance interaction retrieves the server's conformance statement that defines how it supports resources. 
The interaction is performed by an HTTP OPTIONS or a GET command as shown:

<pre>
  GET [base]/metadata {?_format=[mime-type]}
  OPTIONS [base] {?_format=[mime-type]}
</pre>

Applications SHALL return a [Conformance Resource](conformance.html) that specifies which resource types and interactions are supported
for the GET command, and SHOULD do so for the OPTIONS command. If a 404 Unknown is returned from the GET, FHIR is not supported on the 
nominated service url. The GET command is defined because not all client libraries are able to perform an OPTIONS command. 
A Content-Location header SHALL be returned with the conformance resource. The value of the header SHALL change if the 
conformance statement itself changes. The URI provided in the header MAY be a literal location where this version of the
conformance statement is (and will continue to be) available. Additional parameters that are required to be returned with 
the OPTIONS command are defined in the [OMG hData RESTful Transport](#hdata) specification. 

In addition to this conformance operation, a server may also choose to provide the 
standard set of interactions (read, search, create, update) defined on this page 
for the [Conformance Resource](conformance.html) end-point. 
This is different to the conformance operation:

<table class="grid">
 <tr><td>conformance operation</td><td>returns a conformance statement describes the server's current operational functionality</td></tr>
 <tr><td>Conformance end-point</td><td>manages a repository of conformance statements (e.g. the HL7 conformance statement registry)</td></tr>
</table>

All servers are required to support the conformance operation, but servers may choose whether they wish to support the conformance end-point, just like any other end-point.

<a name="transaction"> </a>

### <span class="sectioncount">2.1.14<a name="2.1.14"> </a></span> transaction

The transaction interaction submits a set of resources to be updated, created or deleted on the server. 
This interaction allows multiple resources to be updated/created in a single transaction on a single server. Multiple 
resources of the same or different types may be submitted, and they may be a mix of new and existing resources. 

This is especially useful where one would otherwise need multiple interactions, possibly
leading to loss of referential integrity (e.g. when storing a Provenance resource and its 
corresponding target resource), or, on document repositories, a document index entry and its
accompanying document.

The transaction interaction is performed by an HTTP POST command as shown:

<pre>
  POST [base] {?_format=[mime-type]}
</pre>

The content of the post submission is a resource bundle. The resources in the bundle are each processed separately
as if they were an individual [create](#create), [update](#update) or 
[delete](#delete), along with the normal processing for each 
(such as tracking tags, verification and version aware updates, subject to
the note on [transactional integrity](#transactional-integrity)). 
Servers SHALL either accept all resources and return a 200 OK, along with a 
response bundle, or reject all resources and return an HTTP 400 or 500 type 
response. It is not an error if the submitted bundle has no resources in it.
The outcome of the processing the transaction SHALL not depend on the order 
of the resources in the transaction. Note that this means that a resource can 
only appear in a transaction once, and since bundles may have the same 
resource more than once or other order dependencies (e.g. update lists), some
kinds of bundles may not be able to be used in a transaction.

When a bundle is submitted in a transaction interaction, all the resources have an identity specified
in the bundle. If the identity of the resource matches an existing or possible resource location 
on the server, the server should treat this entry as an [update interaction](#update) 
(i.e. PUT to the given resource). If the identity is not one that the server recognizes as a resource location it can use, the 
server should treat the interaction as a [create interaction](#create) (i.e. POST to 
the given resource type URL), and create a new identity for the submitted resource. Note that the client SHALL provide
an identity in the bundle entry.id, but may also provide a version specific identity the
atom &quot;self&quot; link, and may refer to this for version specific references. Deleted resources are those marked 
using the method described for [XML](xml.html#atom-deleted) or 
[JSON](json.html#json-bundle-delete).

A transaction may include references from one resource to another in the bundle, which may 
include circular references where resources refer to each other. If the server assigns 
a new identity to any resource in the bundle, it SHALL also update any references to that 
resource in the same bundle as they are processed. References to resources that are not 
part of the bundle are left untouched. If a resource in the bundle carries a version-specific 
id (using its self-link), any version-specific references to it SHALL also be updated.
Servers SHALL be replace all matching links in the bundle, whether they are found in the resource ids, 
resource references, url elements, or &lt;a href=&quot;&quot; &amp; &lt;img src=&quot;&quot; in the narrative.

A client may assign temporary ids to new resources and then refer to
them from other places in the transaction. When the client intends a resource 
to have a transient identity that the server must replace, it should use a cid: 
url on the resource - that is, a url with the scheme 
&quot;cid:&quot; [per RFC 2392](http://tools.ietf.org/html/rfc2392). 
Servers SHALL replace these temporary ids when processing the transaction. 

In order to allow the client to know how newly created resources are now identified for future 
reference, the server SHALL return a bundle that contains one entry for each resource in the 
transaction, with the following properties:

*   The server assigned id in entry.id
*   If [vread](#vread) is supported, the specific version reference in a &quot;self&quot; link on the entry
*   The client assigned id in a &quot;alternate&quot; link on the entry
*   entry.content and entry.summary are not required

The server MAY also return an OperationOutcome resource with additional information about the transaction; if one is sent it SHALL not include any errors if the transaction was successful.

The application constructing a bundle may not be sure whether a particular resource will already exist
at the time that the transaction is executed; this is typically the case with reference resources such 
as patient and provider. In this case, the bundle should contain a candidate resource with
a cid: identifier, and an additional search parameter using an Atom link:

<pre>
 &lt;link href=&quot;http://localhost/Patient?[parameters]&quot; rel=&quot;search&quot;/&gt;
</pre>

A search link with a root of http://localhost means to search the local resource store for 
a match as specified in the parameters (which must conform to the servers capability for 
searching as specified in its conformance statement). If the search returns no matches, 
the server process the resource normally. If the search returns one match, the server
uses this matching resource instead, and ignores the submitted resource. If more than
one resource is found, the transaction SHALL be rejected.

If the server that is processing the transaction requires version aware updates, 
the client may need to reference what is the server's current version of
the resource, which is now the client's previous version:

<pre>
 &lt;link href=&quot;[base]/Patient/34/history/31&quot; rel=&quot;predecessor-version&quot;/&gt;
</pre>

A server SHOULD accept &quot;http://localhost&quot; in place of the [base] to ease
processing where the host name may be unknown (e.g. where proxies are involved).
The predecessor-version is treated as if it were the content-location header
on an update interaction.

<a name="history"> </a>

### <span class="sectioncount">2.1.15<a name="2.1.15"> </a></span> history

The history interaction retrieves the history of either a particular resource, all resources of 
a given type, or all resources supported by the system. These three variations of the history
interaction are performed by HTTP Get command as shown:

<pre>
  GET [base]/[type]/[id]/_history{?[parameters]&amp;_format=[mime-type]}
  GET [base]/[type]/_history{?[parameters]&amp;_format=[mime-type]}
  GET [base]/_history{?[parameters]&amp;_format=[mime-type]}
</pre>

The return content is a [Bundle](extras.html#bundle) containing the specified version history, 
sorted with oldest versions last, and including deleted resources, represented as described in bundles 
using the method described for [XML](xml.html#atom-deleted) or 
[JSON](json.html#json-bundle-delete). In addition to the standard _format
parameter, the parameters may also include:

<table class="list">
  <tr><td>_count : [integer](datatypes.html#integer)</td><td>single</td><td>Number of return records requested. The server is not bound to return the number requested, but cannot return more</td></tr>
  <tr><td>_since : [instant](datatypes.html#integer)</td><td>single</td><td>Only include resource versions that were created at or after the given instant in time</td></tr>
</table>

The history list can be restricted to a limited period by specifying a _since parameter which contains a full date time with time zone. 
Servers SHALL ensure that if a client uses the feed.updated date from the last response they received as 
the value of the _since parameter, no versions will be missed. Clients should be aware that due to timing imprecision, 
they may receive notifications of a resource update on the boundary instant more than once. Servers are 
not required to support a precision finer than by second. 

The updates list can be long, so servers may use paging. If they do, they SHALL use the method described 
in [RFC 5005 (Feed Paging and Archiving)](https://tools.ietf.org/html/rfc5005) (also [see Paging](#paging)) for breaking the 
list into pages if appropriate.

The history interaction is suitable for use with internet pub/sub systems based on rss/atom, 
including services such as [Feedly](http://www.feedly.com), allowing humans to easily subscribe to notifications
of updates to a resource (this is usually appropriate for low volume high knowledge resources like
profiles). In addition, the history interaction can be used to set up a subscription from one system
to another, so that resources are synchronized between them. Systems receiving such feeds and planning
on enforcing resource integrity should note that [transaction](#transaction) boundaries 
are not reflected in the history list.

 <a name="tags"> </a>

### <span class="sectioncount">2.1.16<a name="2.1.16"> </a></span> Tag Operations

[Tags](extras.html#tags) are attached to resources to define operational behavior. When resources are exchanged directly use HTTP on the read, vread, create and update interactions, the 
http header &quot;Category&quot; is used, following the method described for [Web Categories](http://tools.ietf.org/html/draft-johnston-http-category-header-02).

<pre>
 <a name="tags"> </a> Category: [Tag Term]; scheme=&quot;[Tag Scheme]&quot;; label=&quot;[Tag label]&quot;(, ...)
</pre>

The label portion is optional. Note that label may come before scheme. 
Although Category is described as a repeating header, many implementations 
require unique header names, so multiple tags are representing using the one header.

<table class="grid">
 <tr><td>**Interaction**</td><td>**Tag Actions**</td></tr>
 <tr><td>read/vread</td><td>The server returns all tags associated with the resource in the headers</td></tr>
 <tr><td>create</td><td>The server stores all the tags provided in the headers</td></tr>
 <tr><td>update</td><td>The server stores all the tags provided in the headers, and keeps any tags already associated with the resource</td></tr>
</table>

In the other interactions, the resources are wrapped in bundles, where tags are represented in the entry.category element
and servers populate these completely or process these as part of a transaction submission.

The following operations provide specific support for tags: <a name="tag-ops"> </a>

<table class="grid">
 <tr><td width="50%">**HTTP Command**</td><td valign="center">**description**</td></tr>
 <tr><td><pre>GET [base]/_tags</pre></td><td valign="center">get a list of all tags</td></tr>
 <tr><td><pre>GET [base]/[type]/_tags</pre></td><td valign="center">get a list of all tags used for the nominated resource type</td></tr>
 <tr><td><pre>GET [base]/[type]/[id]/_tags</pre></td><td valign="center">get a list of all tags affixed to the nominated resource. This duplicates the HTTP header entries</td></tr>
 <tr><td><pre>GET [base]/[type]/[id]/_history/[vid]/_tags</pre></td><td valign="center">get a list of all tags affixed to the nominated version of the resource. This duplicates the HTTP header entries</td></tr>
 <tr><td><pre>POST [base]/[type]/[id]/_tags</pre></td><td valign="center">Affix tags in the list to the nominated resource</td></tr>
 <tr><td><pre>POST [base]/[type]/[id]/_history/[vid]/_tags</pre></td><td valign="center">Affix tags in the list to the nominated version of the resource</td></tr>
 <tr><td><pre>POST [base]/[type]/[id]/_tags/_delete</pre></td><td valign="center">Remove all tags in the provided list from the list of tags for the nominated resource</td></tr>
 <tr><td><pre>POST [base]/[type]/[id]/_history/[vid]/_tags/_delete</pre></td><td valign="center">Remove tags in the provided list from the list of tags for the nominated version of the resource</td></tr>
</table>  

The tags of an old version can still be changed. Note that changing the tags on a resource does not create a new version of the resource. A tag list 
is represented like this in XML and JSON:

<pre class="spec">
&lt;taglist xmlns=&quot;http://hl7.org/fhir&quot;&gt; <span style="float: right">[![doco](help.png)](formats.html "Documentation for this format")</span>
    <span style="color:Gray;">&lt;!-- </span><span style="color:navy;">Tags in the list (<span style="color: brown;">**0..***</span>): </span> <span style="color: Gray"> --&gt; </span>
    &lt;category term=&quot;<span style="color:navy;">[Tag URI]</span>&quot; label=&quot;<span style="color:navy;">[Tag Label]</span>&quot; scheme=&quot;http://hl7.org/fhir/tag&quot;&gt; 
&lt;/taglist&gt;
</pre>

<pre class="json">
{
  &quot;resourceType&quot; : &quot;TagList&quot;,
  &quot;category&quot; : [{
      &quot;term&quot; : &quot;[Tag URI]&quot;,S
      &quot;label&quot; : &quot;[Tag Label]&quot;,
      &quot;scheme&quot; : &quot;http://hl7.org/fhir/tag&quot;
    }]
}
</pre>

Note that &quot;resourceType&quot; is used for consistency even though a tag list is not a FHIR &quot;resource&quot;.

<a name="transactional-integrity"> </a>

### <span class="sectioncount">2.1.17<a name="2.1.17"> </a></span> Transactional Integrity

When processing [create](#create) and [update](#update) 
operations, a FHIR server is not obliged to accept the entire resource as it 
is; when the resource is retrieved through a [read](#read) operation 
subsequently, the resource may be different. The difference may arise for
several reasons:

*   The server merged updated content with existing content
*   The server applied business rules and altered the content
*   The server does not fully support all the features or possible values of the resource

Note that there is no general purpose method to make merging with existing content or 
altering the content by business rules safe or predictable - what is possible,
safe and/or required is highly context dependent. These kind of behaviors may
be driven by security considerations. With regard incomplete support, Clients can consult the server's
base conformance statement profile references to determine which features or 
values the server does not support.

To the degree that the server alters the resource for any of 
the 3 reasons above, the FHIR server will create implementation 
consequences for the eco-system that it is part of, which will 
need to be managed (i.e. it will cost more). For this reason, 
servers SHOULD change the resource as little as possible. 
However due to the variability that exists within healthcare, 
this specification allows that servers MAY alter the resource on
create/update. 

Similarly, to the degree that an implementation context makes special 
rules about merging content or altering the content, that context will
become more expensive to maintain. 

Although these rules are stated with regard to servers, a similar 
concept applies to clients - to the degree that different client 
systems interacting with the server do not support the same feature 
set, the clients and/or the server will be forced to implement custom 
logic to prevent information from being lost or corrupted. 

Some of these problems can be mitigated by following a pattern 
built on top of version-aware updates. In this pattern:

*   The server provides a [read](#read) operation for any resource it accepts [update](#update) operations on
*   Before updating, the client [reads](#read) the latest version of the resource
*   The client applies the changes it wants to the resource, leaving other information intact (note the [extension related rules](extensibility.html#exchange) around this)
*   The client writes the result back as an [update](#update) operation, and is able to handle a 409 response (usually by trying again)

If clients follow this pattern, then information from other systems
that they do not understand will be maintained through the update.

Note that it's possible for a server to choose to maintain the 
information that would be lost, but there is no defined way for
a server to determine whether the client omitted the information
because it wasn't supported (perhaps in this case) or whether it 
wishes to delete the information. 

#### <span class="sectioncount">2.1.17.1<a name="2.1.17.1"> </a></span> Conformance

Both client and server systems SHOULD clearly document how transaction 
integrity is handled.

DSTU TODO: how? 

<a name="binary"> </a>

### <span class="sectioncount">2.1.18<a name="2.1.18"> </a></span> Binary Support

FHIR servers can choose to support [Binary Resources](extras.html#binary)
at the end point [base]/Binary. The binary end-point accepts
any kind of content, such as images and other media, documents (CDA, 
PDF, Word etc.), plain text, XML or anything else, and stores the 
content as is, along with the content type provided by the HTTP headers. 

Binary resources function with the same interactions as described
above, except that there is no support for the search interaction. 
The _format  parameter has no meaning when used with binary 
resources: they are always represented using their original content type.

Note that on GET, POST, and PUT operations, the http content-type
header is the mime type of the binary resource, and the HTTP body is
the resource in it's binary form. (The [XML](xml.html#binary) 
and [JSON](json.html#binary) Bundle Representations for binary 
resources are only used in bundles). 

<div class="example">

Here is the request and response to a read operation on a CDA document:

<pre>
GET /[path]/Binary/4 HTTP/1.1
Host: [server]
Accept: */*

HTTP/1.1 200 OK
Content-Type: text/xml
Access-Control-Allow-Origin: *
Last-Modified: Thu, 24 Oct 2013 00:41:55 +0000
Content-Location: http://[server]/[path]/Binary/4/_history/1

&lt;ClinicalDocument xmlns:xsi=&quot;http://www.w3.org/2001/XMLSchema-instance&quot; 
  xmlns=&quot;urn:hl7-org:v3&quot;xmlns:cda=&quot;urn:hl7-org:v3&quot;&gt;
...  [snip] ...
&lt;/ClinicalDocument&gt;
</pre>

</div>

<a name="paging"> </a>

### <span class="sectioncount">2.1.19<a name="2.1.19"> </a></span> Paging

If servers provide paging for the results of a [search](#search) or [history](#history) interaction,
they SHALL conform to the method described in [RFC 5005 (Feed 
Paging and Archiving)](https://tools.ietf.org/html/rfc5005) for sending continuation links to the client when returning a bundle
(e.g. with history and search). If the server does not do this, there is no way to continue paging.

This example shows the third page of a search result:

<pre class="xml">
&lt;feed xmlns=&quot;http://www.w3.org/2005/Atom&quot;&gt;
  &lt;title&gt;Search Page 3&lt;/title&gt;
  &lt;!-- This Search. url starts with base search, and adds the effective 
    parameters, and additional parameters for search state. All searches 
    SHALL return this value.    

	  In this case, the search continuation method is that the server 
    maintains a state, with page references into the stateful list.
	--&gt;
  &lt;link rel=&quot;self&quot; href=&quot;http://example.org/Patient?name=peter&amp;stateid=23&amp;page=3&quot;/&gt;

  &lt;!-- 4 links for navigation in the search. All of these are optional, but recommended --&gt;  
  &lt;link rel=&quot;first&quot; href=&quot;http://example.org/Patient?name=peter&amp;stateid=23&amp;page=1&quot;/&gt;
  &lt;link rel=&quot;previous&quot; href=&quot;http://example.org/Patient?name=peter&amp;stateid=23&amp;page=2&quot;/&gt;
  &lt;link rel=&quot;next&quot; href=&quot;http://example.org/Patient?name=peter&amp;stateid=23&amp;page=4&quot;/&gt;
  &lt;link rel=&quot;last&quot; href=&quot;http://example.org/Patient?name=peter&amp;stateid=23&amp;page=26&quot;/&gt;
  &lt;updated&gt;2003-12-13T18:30:02Z&lt;/updated&gt;

  &lt;!-- the rest of the search results... --&gt;  
&lt;/feed&gt;
</pre>

The server need not use a stateful paging method as shown in this example - it is at 
the discretion of the server how to best ensure that the continuation retains 
integrity in the context of ongoing changes to the resources. An alternative approach
is to use version specific references to the records on the boundaries, but this is 
subject to continuity failures when records are updated.

A server MAY inform the client of the total number of resources returned by the interaction for which the results are paged
using  the totalResults element from the [
OpenSearch specification](http://www.opensearch.org/Specifications/OpenSearch/1.1):

<pre class="xml">
&lt;feed xmlns=&quot;http://www.w3.org/2005/Atom&quot;&gt;
  &lt;title&gt;e.g. Search Page 3&lt;/title&gt;
  &lt;os:totalResults xmlns:os=&quot;http://a9.com/-/spec/opensearch/1.1/&quot;&gt;1432&lt;/os:totalResults&gt;

  &lt;!-- the rest of the search/history results... --&gt;  
&lt;/feed&gt;
</pre>

Note that for search, where _include can be used to return additional related resources, the total number 
of resources in the feed may exceed the number indicated in totalResults.

### <span class="sectioncount">2.1.20<a name="2.1.20"> </a></span> Intermediaries

The HTTP protocol may be routed through an HTTP proxy such as 
squid. Such proxies are transparent to the applications, though
implementers should be alert to the effects of caching, particularly
including the risk of receiving stale content. See the [HTTP specification](http://tools.ietf.org/html/rfc2616#page-74)
for further detail

Interface engines may also be placed between the consumer and
the provider. These differ from proxies because they actively
alter the content and/or destination of the HTTP exchange and are
not bound the rules that apply to HTTP proxies. Such agents are allowed, 
but SHALL mark the http header to assist with troubleshooting.

Any agent that modifies an HTTP request or Response content other
than under the rules for HTTP proxies SHALL add a stamp to the HTTP 
headers like this:

<pre>
  request-modified-[identity]: [purpose]
  response-modified-[identity]: [purpose]
</pre>

The identity SHALL be a single token defined by the administrator of the agent
that will sufficiently identify the agent in the context of use. The header
SHALL specify the agent's purpose in modifying the content. End point systems SHALL
not use this header for any purpose. Its aim is to assist with 
system troubleshooting.

<a name="hdata"> </a>

### <span class="sectioncount">2.1.21<a name="2.1.21"> </a></span> OMG hData RESTful Transport

This RESTful specification described here is based on the [OMG Health RESTful specification](http://www.omg.org) (specific reference to be provided when this is published). 
In this regard, FHIR functions as a Record Format Profile as described in that specification. Note the following significant factors to be aware of:

*   FHIR maps the hData sections to resource types, and hData documents to resource instances. There are no subsections, and client systems are not able to create new sections, though [compartments](extras.html#compartments) behave somewhat like sections
*   Because clients cannot submit new sections (POST to service URL), POST to the service URL has been re-used for [the transaction interaction](#transaction) (difference under review)
*   FHIR does not (yet) define a root document. When defined, it will contain information about what the FHIR server has done (as opposed to a conformance statement, which describes what it is capable of doing)
*   Note that this specification does not repeat the rules in the hData RESTful Transport concerning the OPTIONS command on the service URL, but these rules (extra headers etc.) still apply

<a name="summary"> </a>

### <span class="sectioncount">2.1.22<a name="2.1.22"> </a></span> Summary

These tables present a summary of the interactions described here.

<table class="grid">
<tr><th>Interaction</th><th>Path</th><th colspan="5">Request</th></tr>
<tr><th colspan="2"/>                                     <th>Verb</th>         <th>Content-Type</th> <th>Body</th>     <th>Accept</th> <th>Content-Location</th></tr>
<tr><td>read</td>       <td>/[type]/[id]</td>                <td>GET</td>          <td>N/A</td>          <td>N/A</td>      <td>O</td>      <td>N/A</td></tr>
<tr><td>vread</td>      <td>/[type]/[id]/_history/[vid]</td> <td>GET</td>          <td>N/A</td>          <td>N/A</td>      <td>O</td>      <td>N/A</td></tr>
<tr><td>conformance</td><td>/ or /metadata</td>               <td>OPTIONS / GET</td><td>N/A</td>          <td>N/A</td>      <td>O</td>      <td>N/A</td></tr>
<tr><td>update</td>     <td>/[type]/[id]</td>                <td>PUT</td>          <td>R</td>            <td>Resource</td> <td>N/A</td>      <td>O or R</td></tr>
<tr><td>create</td>     <td>/[type]</td>           		      <td>POST</td>         <td>R</td>            <td>Resource</td> <td>N/A</td>      <td>N/A</td></tr>
<tr><td>transaction</td><td>/</td>                            <td>POST</td>         <td>R</td>            <td>Bundle</td>   <td>O</td>      <td>N/A</td></tr>
<tr><td>delete</td>     <td>/[type]/[id]</td>                <td>DELETE</td>       <td>N/A</td>          <td>N/A</td>      <td>N/A</td>    <td>N/A</td></tr>
<tr><td>search</td>     <td>/[type]/_search? or /[type]?</td>    <td>GET</td>          <td>N/A</td>         <td>N/A</td>      <td>O</td>      <td>N/A</td></tr>
<tr><td>search-all</td>	<td>/</td>                   		  <td>GET</td>          <td>N/A</td>          <td>N/A</td>      <td>O</td>      <td>N/A</td></tr>
<tr><td>validate</td>   <td>/[type]/_validate{/[id]}</td>       <td>POST</td>         <td>R</td>            <td>Resource</td> <td>O</td>      <td>N/A</td></tr>
<tr><td>history</td>	<td>/[type]/[id]/_history</td> 		  <td>GET</td>          <td>N/A</td>          <td>N/A</td>      <td>O</td>      <td>N/A</td></tr>
<tr><td>history-type</td><td>/[type]/_history</td> 		  	  <td>GET</td>          <td>N/A</td>          <td>N/A</td>      <td>O</td>      <td>N/A</td></tr>
<tr><td>history-all</td><td>/_history</td> 		  			  <td>GET</td>          <td>N/A</td>          <td>N/A</td>      <td>O</td>      <td>N/A</td></tr>
<tr><td>tags-all</td>	<td>/_tags</td><td>GET</td><td>N/A</td><td>N/A</td><td>O</td><td>N/A</td></tr>
<tr><td>tags-type</td>	<td>/[type]/_tags</td><td>GET</td><td>N/A</td><td>N/A</td><td>O</td><td>N/A</td></tr>
<tr><td rowspan="2">tags</td><td rowspan="2">/[type]/[id]/_tags</td><td>GET</td><td>N/A</td><td>N/A</td><td>O</td><td>N/A</td></tr>
<tr><td>POST</td><td>R</td><td>TagList</td><td>N/A</td><td>N/A</td></tr>
<tr><td>tags-delete</td>	<td>/[type]/[id]/_tags/_delete</td><td>POST</td><td>R</td><td>TagList</td><td>N/A</td><td>N/A</td></tr>
<tr><td rowspan="2">tags-version</td><td rowspan="2">/[type]/[id]/_history/[vid]/_tags</td><td>GET</td><td>N/A</td><td>N/A</td><td>O</td><td>N/A</td></tr>
<tr><td>POST</td><td>R</td><td>TagList</td><td>N/A</td><td>N/A</td></tr>
<tr><td>tags-version-delete</td>	<td>/[type]/[id]/_history/[vid]/_tags/_delete</td><td>POST</td><td>R</td><td>TagList</td><td>N/A</td><td>N/A</td></tr>
<tr><td rowspan="2">mailbox</td>
<td>/Mailbox (Message)</td><td>POST</td><td>R</td><td>Bundle</td><td>R</td><td>N/A</td></tr>
<tr><td>/Mailbox (Document)</td><td>POST</td><td>R</td><td>Bundle</td><td>N/A</td><td>N/A</td></tr>
<tr><td>document</td>	<td>/Document</td><td>POST</td><td>R</td><td>Bundle</td><td>N/A</td><td>N/A</td></tr>
</table>

Note: N/A = not present, R = Required, O = optional.

<table class="grid">
<tr><th>Interaction</th><th colspan="5">Response</th></tr>
<tr><th colspan="1"/> <th>Content-Type</th> <th>Body</th>               <th>Location</th> <th>Content-Location</th> <th>Status Codes</th></tr>
<tr><td>read</td>         <td>R</td>            <td>Resource</td>           <td>N/A</td>      <td>R</td>                <td>200, 404, 410</td></tr>
<tr><td>vread</td>        <td>R</td>            <td>Resource</td>           <td>N/A</td>      <td>O</td>                <td>200, 404, 405</td></tr>
<tr><td>conformance</td>  <td>R</td>            <td>Conformance</td>        <td>N/A</td>      <td>O</td>                <td>200, 404</td></tr>
<tr><td>update</td>       <td>N/A</td>            <td>N/A</td>           <td>N/A</td>      <td>R</td>                <td>200, 201, 400, 404, 405, 409, 412, 422</td></tr>
<tr><td>create</td>       <td>N/A</td>            <td>N/A</td>           <td>R</td>        <td>O</td>                <td>201, 400, 404, 405, 422</td></tr>
<tr><td>transaction</td>  <td>R</td>            <td>Bundle</td>             <td>N/A</td>      <td>N/A</td>              <td>200, 400, 404, 405, 409, 412, 422</td></tr>
<tr><td>delete</td>       <td>N/A</td>          <td>N/A</td>                <td>N/A</td>      <td>N/A</td>              <td>204, 405, 404</td></tr>
<tr><td>search</td>       <td>R</td>            <td>Bundle</td>             <td>N/A</td>      <td>N/A</td>              <td>200, 403</td></tr>
<tr><td>search-all</td>   <td>R</td>            <td>Bundle</td>             <td>N/A</td>      <td>N/A</td>              <td>200, 403</td></tr>
<tr><td>validate</td>     <td>N/A or R</td>     <td>N/A or OperationOutcome</td> <td>N/A</td>      <td>N/A</td>              <td>400</td></tr>
<tr><td>history</td>   	  <td>R</td>            <td>Bundle</td>             <td>N/A</td>      <td>N/A</td>              <td>200</td></tr>
<tr><td>history-type</td> <td>R</td>            <td>Bundle</td>             <td>N/A</td>      <td>N/A</td>              <td>200</td></tr>
<tr><td>history-all</td>  <td>R</td>            <td>Bundle</td>             <td>N/A</td>      <td>N/A</td>              <td>200</td></tr>
<tr><td>tags-all</td><td>R</td><td>TagList</td><td>N/A</td><td>N/A</td><td>200</td></tr>
<tr><td>tags-type</td><td>R</td><td>TagList</td><td>N/A</td><td>N/A</td><td>200</td></tr><tr><td rowspan="2">tags</td><td>R (GET)</td><td>TagList</td><td>N/A</td><td>N
/A</td><td>200, 404, 410</td></tr>
<tr><td>N/A (POST)</td><td>N/A</td><td>N/A</td><td>N/A</td><td>204</td></tr>
<tr><td>tags-delete</td><td>N/A</td><td>N/A</td><td>N/A</td><td>N/A</td><td>204</td></tr>
<tr><td rowspan="2">tags-version</td><td>R (GET)</td><td>TagList</td><td>N/A</td><td>N/A</td><td>200, 404</td></tr>
<tr><td>N/A (POST)</td><td>N/A</td><td>N/A</td><td>N/A</td><td>204</td></tr>
<tr><td>tags-version-delete</td><td>N/A</td><td>N/A</td><td>N/A</td><td>N/A</td><td>204</td></tr>
<tr><td rowspan="2">mailbox</td>
	<td>R (Message)</td><td>Bundle</td><td>N/A</td><td>N/A</td><td>200</td></tr>
<tr><td>N/A (Document)</td><td>N/A</td><td>N/A</td><td>N/A</td><td>204</td></tr>
<tr><td>document</td><td>N/A</td><td>N/A</td><td>N/A</td><td>N/A</td><td>200</td></tr>
</table>

Note: this table lists the status codes described here, but other status codes are possible as described by the HTTP specification. 
Additional codes that are likely a server errors and various codes associated with authentication protocols.

</div>

<div class="col-3"><div class="itoc">

On This Page:

[Interactions](#interactions)

[Tag Operations](#tags)

[Binary Support](#binary)

[Paging](#paging)

[hData Information](#hdata)

[Summary](#summary)

</div></div>

				</div>  <!-- /inner-wrapper -->
            </div>  <!-- /row -->
        </div>  <!-- /container -->

    </div>  <!-- /segment-content -->

	<div id="segment-footer" class="segment">  <!-- segment-footer -->
		<div class="container">  <!-- container -->
			<div class="inner-wrapper">

        &copy; HL7.org 2011 - 2014. FHIR DSTU (v0.2.1-2606) generated on Wed, Jul 2, 2014 16:29+0800.   <!-- [QA Report](qa.html) -->   <!-- achive note -->

        <span style="color: #FFFF77">
        Links: [What's a DSTU?](dstu.html) | 
               [Version History](history.html) | 
               [Compare to DSTU](http://services.w3.org/htmldiff?doc1=http%3A%2F%2Fhl7.org%2Fimplement%2Fstandards%2Ffhir%2Fhttp.html&amp;doc2=http%3A%2F%2Fhl7.org%2Fimplement%2Fstandards%2FFHIR-Develop%2Fhttp.html) | 
               [License](license.html) | 
               [Propose a change](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemAdd&amp;tracker_id=677)   
        </span>

			</div>  <!-- /inner-wrapper -->
		</div>  <!-- /container -->
	</div>  <!-- /segment-footer -->
  <!-- disqus thread -->
  <!-- disqus -->
  <!-- end disqus -->        