title: 
date: 
categories: doc
---

## <span class="sectioncount">1.9.1<a name="1.9.1"> </a></span> FHIR Overview - Developers

FHIR (Fast Health Interoperability Resources) is designed to 
enable the information exchange that supports the provision
of healthcare in a wide variety of processes. The specification
builds on and adapts standard industry RESTful practices
to enable the provision of integrated healthcare across a 
wide range of teams.

The intended scope of FHIR is broad, covering human and veterinary,
clinical care, public health, clinical trials, administration and
financial aspects.  The standard is intended for global use in a wide
variety of architectures and scenarios.

### <span class="sectioncount">1.9.1.1<a name="1.9.1.1"> </a></span> Framework

FHIR is based on &quot;Resources&quot; which are the common building block
for all exchanges.  Each resource has the following [common features](resources.html):

*   A URL that identifies it
*   Common metadata
*   A [human-readable XHTML summary](narrative.html)
*   A set of defined common data elements
*   An [extensibility framework](extensibility.html) to support variation in healthcare

Resources are represented as either [XML](xml.html) or [JSON](json.html). There are currently 99 
different [resource types defined](resourcelist.html) in the FHIR specification. 

### <span class="sectioncount">1.9.1.2<a name="1.9.1.2"> </a></span> Example Patient

This is an example of how a [patient](patient.html) is represented as a FHIR object in JSON. XML encoding is also defined in the specification.

<div class="example">
<pre class="json linecounter">
`{`
`  "resourceType": "Patient",`
`  "id" : "23434",`
`  "meta" : {`
`    "versionId" : "12",`
`    "lastUpdated" : "2014-08-18T01:43:30Z"`
`  }`
`  "text": {`
`    "status": "generated",`
`    "div": "<!-- Snipped for Brevity -->"`
`  },`
`  "extension": [`
`    {`
`      "url": "http://example.org/consent#trials",`
`      "valueCode": "renal"`
`    }`
`  ],`
`  "identifier": [`
`    {`
`      "use": "usual",`
`      "label": "MRN",`
`      "system": "http://www.goodhealth.org/identifiers/mrn",`
`      "value": "123456"`
`    }`
`  ],`
`  "name": [`
`    {`
`      "family": [`
`        "Levin"`
`      ],`
`      "given": [`
`        "Henry"`
`      ],`
`      "suffix": [`
`        "The 7th"`
`      ]`
`    }`
`  ],`
`  "gender": {`
`    "text": "Male"`
`  },`
`  "birthDate": "1932-09-24",`
`  "active": true`
`}`
</pre>
</div>

Each resource consists of:  

*   **resourceType** (line 2) - Required: FHIR defines many different types of resources. See [the full index](resourcelist.html)
*   **id** (line 3) - The id of the resource. Always present when a resource is exchanged, except during the create operation (below)
*   **meta** (lines 4 - 7) - Usually Present: [Common use/context data to all resources](resources.html#meta) and managed by the infrastructure. Missing if there is no metadata
*   **text** (lines 12 - 17) - Recommended: XHTML that provides a [human readable representation](narrative.html) for the resource
*   **extension** (lines 12 - 17) - Optional: [Extensions](extensibility.html) defined by the extensibility framework
*   **data** (lines 18 - 43) - Optional: data elements defined for each type of resource

Note that though this specification always shows the JSON properties in the order they are defined, many JSON libraries order properties by other criteria.

### <span class="sectioncount">1.9.1.3<a name="1.9.1.3"> </a></span> Interactions

For manipulation of resources, FHIR provides a [REST API](http.html) with a
rich but simple set of interactions:

*   [Create](http.html#create) = POST https://example.com/path/{resourceType}
*   [Read](http.html#read) = GET https://example.com/path/{resourceType}/{id}
*   [Update](http.html#update) = PUT https://example.com/path/{resourceType}/{id}
*   [Delete](http.html#delete) = DELETE https://example.com/path/{resourceType}/{id}
*   [Search](http.html#search) = GET https://example.com/path/{resourceType}?search parameters...
*   [History](http.html#history) = GET https://example.com/path/{resourceType}/{id}/_history
*   [Transaction](http.html#transaction) = POST https://example.com/path/
*   [Operation](operations.html) = GET https://example.com/path/{resourceType}/{id}/${opname}

The FHIR specification describes other kinds of exchanges beyond this simple RESTful API, 
including exchange of groups of resources as [Documents](documents.html), 
[Messages](messaging.html), and by using other kinds of [services](services.html). 

### <span class="sectioncount">1.9.1.4<a name="1.9.1.4"> </a></span> Managing Variability

One feature of the healthcare industry is that there is a wide variation
between different jurisdictions and sections of the industry, and no 
central authority to impose common business practices. Because of this, 
the FHIR specification defines a [common extension framework](extensibility.html), and defines
[a framework for managing variability](profiling.html).

### <span class="sectioncount">1.9.1.5<a name="1.9.1.5"> </a></span> Creating a resource

To [create a resource](http.html#create), send an HTTP POST request to the resource's respective end
point. In the example below we see the creation of a Patient.

<div class="example">
<pre class="http linecounter">
`POST {some base path}/Patient HTTP/1.1`
`Authorization: Bearer 37CC0B0E-C15B-4578-9AC1-D83DCED2B2F9`
`Accept: application/json+fhir`
`Content-Type: application/json+fhir`
`Content-Length: 1198`
` `
`{`
`  "resourceType": "Patient",`
`  ...`
`}`
</pre>
</div>

Submit a new patient to the server, and ask it to store the patient with an id of its own choice. Notes:

*   **/Patient** (line 1) - the manager for all patients - use the name of the type of resource
*   **Authorization** (line 2) - see [Security for FHIR](security.html)
*   **Accept, Content-Type** (lines 3-4) - the content type for all FHIR resources as represented in JSON (or application/xml+fhir for the XML version). FHIR resources are always represented in UTF-8
*   **id** (line 9) - No id for a resource that is being created - the server will assign one
*   Resource Content, lines 8+ - There's no meta property at this point. The rest of the resource is the same content as above

### <span class="sectioncount">1.9.1.6<a name="1.9.1.6"> </a></span> Create Response

A response contains an HTTP code 201 to indicate that the
Resource has been created successfully. A location header 
indicates where the resource can be fetched in subsequent requests.
The server may choose to return an [OperationOutcome](operationoutcome.html) resource, but is not required to
do so. 

<div class="example">
<pre class="http linecounter">
`HTTP/1.1 201 Created`
`Content-Length: 161`
`Content-Type: application/json+fhir`
`Date: Mon, 18 Aug 2014 01:43:30 GMT`
`ETag: "1"`
`Location: http://example.com/Patient/347`
` `
`{`
`  "resourceType": "OperationOutcome",`
`  "text": {`
`    "status": "generated",`
`    "div": "<div xmlns=\"http://www.w3.org/1999/xhtml\">The operation was successful</div>"`
`  }`
`}`
</pre>
</div>

Notes:

*   **HTTP/1.1 201** (line 1) - the operation was successful. Note that HTTP/1.1 is strongly recommended but not required
*   **ETag** (line 5) - used in the [version aware update](http.html#update) pattern
*   **Location** (line 6) - the id the server assigned to the resource. The id in the url must match the id in the resource when it is subsequently returned
*   **operationOutcome** (line 9) - OperationOutcome resources in this context have no id or meta element (they have no managed identity)

#### <span class="sectioncount">1.9.1.6.1<a name="1.9.1.6.1"> </a></span> Error response

For a variety of reasons, servers may need to return an error. Clients should be alert to 
authentication related responses, but FHIR content related errors should be returned using an 
appropriate HTTP status code, with an [OperationOutcome](operationoutcome.html) resource to provide additional information.
Here is an example of a server rejecting a resource because of server defined business rules:

<div class="example">
<pre class="http linecounter">
`HTTP/1.1 422 Unprocessable Entity`
`Content-Length: 161`
`Content-Type: application/json+fhir`
`Date: Mon, 18 Aug 2014 01:43:30 GMT`
` `
`{`
`  "resourceType": "OperationOutcome",`
`  "text": {`
`    "status": "generated",`
`    "div": "<div xmlns=\"http://www.w3.org/1999/xhtml\">MRN conflict`
`   - the MRN 123456 is already assigned to a different patient</div>"`
`  },`
`}`
</pre>
</div>

Notes:

*   The server can return additional structured information using the details of the [OperationOutcome](operationoutcome.html)

### <span class="sectioncount">1.9.1.7<a name="1.9.1.7"> </a></span> Read Request

[Reading a resource](http.html#read) is done by sending HTTP GET requests to the desired Resource
end point, as in this example. 

<div class="example">
<pre class="http linecounter">
`GET /Patient/347?_format=xml HTTP/1.1`
`Host: example.com`
`Accept: application/xml+fhir`
`Cache-Control: no-cache`
</pre>
</div>

Notes:

*   **347** (line 1) - The id of the resource that is being fetched
*   **_format=xml** (line 1) - this is another method for clients to indicate the desired response format, in addition to using the accept header, and is useful for clients that don't have access to the HTTP Headers (e.g. XSLT transforms) (see [Mime Types](http.html#mimetypes)
*   **cache control** (line 4) - Concurrency control is important, though FHIR itself says nothing about it - see [http://www.w3.org/Protocols/rfc2616/rfc2616-sec13.html](http://www.w3.org/Protocols/rfc2616/rfc2616-sec13.html) or [https://www.mnot.net/cache_docs/](https://www.mnot.net/cache_docs/)

### <span class="sectioncount">1.9.1.8<a name="1.9.1.8"> </a></span> Read Response

The response to a GET contains the Resource. 

<div class="example">
<pre class="http linecounter">
`HTTP/1.1 200 OK`
`Content-Length: 729`
`Content-Type: application/xml+fhir`
`Last-Modified: Sun, 17 Aug 2014 15:43:30 GMT`
`ETag: "1"`
` `
`<?xml version="1.0" encoding="UTF-8"?>`
`<Patient xmlns="http://hl7.org/fhir">`
`  <id value="347"/>`
`  <meta>`
`    <versionId value="1"/>`
`    <lastUpdated value="2014-08-18T01:43:30Z"/>`
`  </meta>`
`  <!-- content as shown above for patient -->  `
`</Patient>`
</pre>
</div>

Notes:

*   **id** (line 8) - The id of the resource. This must match the id in the read request
*   **versionId** (line 11) - The current version id of the resource. Best practice is that this value matches the ETag (see [version aware update](http.html#update)), but clients must never assume this. Note that some servers do not track the version of the resource
*   Note that servers are not required to support versioning, but are strongly encouraged to do so
*   **lastUpdated** (line 12) - if present, this must match the value in the HTTP header

### <span class="sectioncount">1.9.1.9<a name="1.9.1.9"> </a></span> Search Request

In addition to getting single known resources it is possible to find resources by 
[searching the resource end point](http.html#search) with a [set of 
criteria](search.html) describing the set of resources that should be retrieved and their order. The
general pattern is:

<div class="example">
<pre class="http">
GET base/{resourceType}?criteria HTTP/1.1
</pre>
</div>

or simply https://example.com/{resourceType}?criteria. The criteria is a set of 
http parameters that specify which resources to return. The search operation

<div class="example">
<pre class="http">
https://example.com/base/MedicationPrescription?patient=347
</pre>
</div>

returns all the prescriptions for the patient created above.

### <span class="sectioncount">1.9.1.10<a name="1.9.1.10"> </a></span> Search Response

The response to a search request is a [bundle](extras.html#bundle): list of matching resources with some metadata:

<div class="example">
<pre class="json linecounter">
`{`
`  "resourceType": "Bundle",`
`  "id" : "eceb4882-5c7e-4ca4-af62-995dfb8cef01"`
`  "meta" : {`
`    "lastUpdated" : "2014-08-19T15:43:30Z"`
`  },`
`  "base": "http://example.com/base",`
`  "total": "3",`
`  "link": [`
`    {`
`      "relation" : "next",`
`      "url" : "https://example.com/base/MedicationPrescription?patient=347&searchId=ff15fd40-ff71-4b48-b366-09c706bed9d0&page=2"`
`    }, {`
`      "relation" : "self",`
`      "url" : "https://example.com/base/MedicationPrescription?patient=347"`
`    }`
`  ],`
`  "item": [`
`    {`
`      "resourceType": "MedicationPrescription",`
`      "id" : "3123",`
`      "meta" : {`
`        "versionId" : "1",`
`        "lastUpdated" : "2014-08-16T05:31:17Z"`
`      }, `
`      ... content of resource ...`
`    }, `
`    ... 2 additional resources ....`
`  ]`
`}`
</pre>
</div>

Notes:

*   **resourceType** (line 7) - &quot;SearchResults&quot; is the name for a bundle returned from a search
*   **id** (line 3) - An identifier assigned to this particular bundle. The server should assign a unique id to this bundle that it will not be re-used. Note that in some bundles - though not search results - this must be [globally unique](extras.html#bundle-unique)
*   **meta.lastUpdated** (line 10) - This should match the HTTP header, and should be the date the search was executed, or more recent, depending on how the [server handles ongoing updates](search.html#currency). The lastUpdated data SHALL be the same or more recent than the most recent resource in the results
*   **base** (line 12) - The base URL for any relative [references](references.html) in the resources. The server SHOULD provide this value
*   **total** (line 13) - The total number of matches in the search results. Not the number of matches in this particular bundle, which may be a [paged view into the results](http.html#search)
*   **link** (line 14) - A set of named links that give related contexts to this bundle. Names defined in this specification: [first](http.html#search), [prev](http.html#search), [next](http.html#search), [last](http.html#search), [self](http.html#search)
*   **item** (line 23) - The actual resources in this set of results
*   In addition, the search operation is also able to [return additional related resources](search.html#include) as well

### <span class="sectioncount">1.9.1.11<a name="1.9.1.11"> </a></span> Update Request

The client sends the server a new version of the resource to replace the exist version.

<div class="example">
<pre class="http linecounter">
`PUT /Patient/347 HTTP/1.1`
`Host: example.com`
`Content-Type: application/json+fhir`
`Content-Length: 1435`
`Accept: application/json+fhir`
`If-Match: 1`
` `
`{`
`  "resourceType": "Patient",`
`  "id" : "347",`
`  "meta" : {`
`    "versionId" : "1",`
`    "lastUpdated" : "2014-08-18T01:43:30Z"    `
`  },`
`  ...`
`}`
</pre>
</div>

Notes:

*   **resourceType** (line 1) - &quot;Patient&quot; in the url must match the resource type in the resource (line 9)
*   **resource id** (line 1, &quot;347&quot;) - This must match the id in the resource (line 9)
*   **If-Match** (line 6) - if this is provided, it must match the value in meta.versionId (line 12), and the server must check the version integrity, or return 412 if it doesn't support versions
*   **meta.lastUpdated** (line 10) - This value is ignored, and will be updated by the server
*   **resource content** (line 14) - Not shown here, the same as Patient above

### <span class="sectioncount">1.9.1.12<a name="1.9.1.12"> </a></span> Update Response

The response to an update request has metadata / status, and optionally an OperationOutcome:

<div class="example">
<pre class="http linecounter">
`HTTP/1.1 200 OK`
`Content-Length: 161`
`Content-Type: application/json+fhir`
`Date: Mon, 18 Aug 2014 01:43:30 GMT`
`ETag: "2"`
` `
`{`
`  "resourceType": "OperationOutcome",`
`  "text": {`
`    "status": "generated",`
`    "div": "<div xmlns=\"http://www.w3.org/1999/xhtml\">The operation was successful</div>"`
`  }`
`}`
</pre>
</div>

Notes:

*   **ETag** (line 5) - This is the versionId of the new version

### <span class="sectioncount">1.9.1.13<a name="1.9.1.13"> </a></span> Base Resource Content

Here is an example that shows all the information found in all resources, fully populated:

<div class="example">
<pre class="json linecounter">
`{`
`  "resourceType" : "X",`
`  "id" : "12",`
`  "meta" : {`
`    "versionId" : "12",`
`    "lastUpdated" : "2014-08-18T01:43:30Z",`
`    "profile" : ["http://example-consortium.org/fhir/profile/patient"],`
`    "security" : [{`
`      "system" : "http://hl7.org/fhir/v3/ActCode",`
`      "code" : "EMP"`
`    }],`
`    "tag" : [{`
`      "system" : "http://example.com/codes/workflow",`
`      "code" : "needs-review"`
`    }]`
`  },`
`  "implicitRules" : "http://example-consortium.org/fhir/ehr-plugins",`
`  "language" : "X"`
`}`
</pre>
</div>

Implementers notes:  

*   **resourceType** (line 2) - always found in every resource. In XML, this is the name of the root element for the resource
*   **id** (line 3) - defined when the resource is created, and never changed. Only missing when the resource is first created
*   **meta.versionId** (line 5) - changes each time any resource contents change (except for the last 3 elements in meta)
*   **meta.lastUpdated** (line 6) - Changes when the versionId changes. Systems that don't support versions usually don't track lastUpdated either
*   **meta.profile** (line 7) - An assertion that the content conforms to a profile. See [Extending and Restricting Resources](profiling.html#resources) for further discussion. Can be changed as profiles and value sets change or the system rechecks conformance
*   **meta.security** (lines 8 - 11) - [Security labels](securitylabels.html) applied to this resource. These tags connect resources in specific ways to the overall security policy and infrastructure. Security tags can be updated when the resource changes, or whenever the security sub-system chooses to
*   **meta.tag** (lines 12 - 15) - [Tags](extras.html) applied to this resource. Tags are used to relate resources to process and workflow. Applications are not required to consider the tags when interpreting the meaning of a resource. Tags can be [updated](http.html#tags) without changing the resource version
*   **implicitRules** (lines 16) - indicates that there is a [custom agreement](profiling.html#agreement) about how the resources are used that must be understood in order to safely process the resource. Use of this is discouraged because it restricts sharing, but sometimes necessary
*   **language** (lines 17) - The [base language of the resource](narrative.html#language). The resource is allowed to have content from other languages; this is just the base, but should be the main language of the resource

</div>

				</div>  <!-- /inner-wrapper -->
            </div>  <!-- /row -->
        </div>  <!-- /container -->

    </div>  <!-- /segment-content -->

	<div id="segment-footer" class="segment">  <!-- segment-footer -->
		<div class="container">  <!-- container -->
			<div class="inner-wrapper">
				<p>
        © HL7.org 2011+. FHIR DSTU (v0.4.0-3900) generated on Sat, Dec 20, 2014 22:38+0000.   <!-- [QA Report](qa.html) -->   <!-- achive note -->

        <span style="color: #FFFF77">