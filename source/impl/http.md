title:
date:  
categories: impl
---

  [首页](../home/index.html) > [实现](implementation.html) >**Restful API**


本页内容:



*   [RESTful API](#)
*   [示例](datatypes-examples.html)
*   [详细描述](datatypes-definitions.html)
*   [映射](datatypes-mappings.html)

###   2.1.0 RESTful API

每种资源类型都定义了同样类型的交互/方法，可以一种高度模块化的方式来管理资源内容。 遵循这个框架也就是说遵循&quot;RESTful FHIR&quot;.

需要注意的是在Restful 框架中，使用 HTTP 请求和响应来对服务器中的资源进行直接操作.该API 中并没有直接规定认证、授权和审计的问题-更多详情请参考[Security Page](security.html).

这些API定义了FHIR资源的一些方法，也叫做交互，单个资源的实例是以类型的集合来管理的。FHIR服务器可以选择实现其中的一些方法并且支持那些资源类型。FHIR服务器
应该提供一个[符合性声明](conformance.html)的文件来描述它支持那些资源和交互。

定义了下列方法/交互:

<a name="interactions"> </a>
<a name="operations"> </a>
<table class="list">
  <tr><td>**实例层面的交互**</td><td/></tr>
  <tr><td>[read](#read)</td><td>读取资源的最新内容</td></tr>
  <tr><td>[vread](#vread)</td><td>读取某个版本的资源内容</td></tr>
  <tr><td>[update](#update)</td><td>更新资源内容</td></tr>
  <tr><td>[delete](#delete)</td><td>删除资源内容</td></tr>
  <tr><td>[history](#history)</td><td>获取某个资源的版本变更记录</td></tr>
  <tr><td colspan="2">**资源类型层面的交互**</td></tr>
  <tr><td>[create](#create)</td><td>新增一条资源记录</td></tr>
  <tr><td>[search](#search)</td><td>根据过滤条件查询某种资源类型</td></tr>
  <tr><td>[history](#history)</td><td>获取某种类型资源的版本变更记录</td></tr>
  <tr><td colspan="2">**系统层面的交互**</td></tr>
  <tr><td>[conformance](#conformance)</td><td>获取系统的符合性声明</td></tr>
  <tr><td>[transaction](#transaction)</td><td>以单个事务形式来批量新增、修改和删除资源</td></tr>
  <tr><td>[history](#history)</td><td>获取所有资源类型所有资源实例的版本变更记录</td></tr>
  <tr><td>[search](#search)</td><td>根据一些过滤条件在所有资源类型中进行查找</td></tr>
</table>

除了上述交互之外， 还有[operations framework](operations.html),其中包括了[validation](operation-resource-validate.html), [messaging](messaging.html#mailbox) 和 [Documents](documents.html#bundle).

**样式说明**
这部分定义的交互形式如下:

```
  VERB [base]/[type]/[id] {?_format=[mime-type]}
```

*   第一个指的是HTTP的POST/PUT/GET等动词
*   [] 中的内容是必须要存在的，可以使用相应的字符来替换。示例:

    *   **base**:  [Service Root URL](#root)
    *   **mime-type**:  [Mime Type](#mime-type)
    *   **type**: 资源类型的名称 (e.g. &quot;Patient&quot;)
    *   **id**:  资源的[逻辑标识Id](resource.html#id)
    *   **vid**: 资源的[版本标识 Id](resource.html#metadata)
    *   **compartment**: [compartment](extras.html#compartment)的名称
    *   **parameters**:某种方法中所定义的url参数
*   {}中的内容是可选项

开发中所生成的URLs应符合 [RFC 3986 Section 6 Appendix A](https://tools.ietf.org/html/rfc3986#appendix-A)
的要求，其中一些字符需要进行URL编码
which requires percent-encoding for a number of characters that occasionally appear in the URLs (mainly in search parameters).

<a name="root"> </a>
<a name="general"> </a>

####  2.1.0.1 服务根路径

所有资源都能够在服务的根路径中找到. 服务根路径的格式是：

```
http(s)://server{/path}
```
path这部分是可选的，并且不包含拖尾斜杠。每种资源类型的管理节点在&quot;/[type]&quot;
&quot;type&quot; 也就是资源类型的名称.比如
&quot;Patient&quot; 就形如:

```
https://server/path/Patient
```

所有的交互都是相对服务根路径来定义的。也就是说当你知道系统中任何一个资源的路径，也就可以推断出其他资源的地址。

注意：所有URL都是大小写敏感的。

注意：服务器可能会使用这种 &quot;http://server/...[xx]...&quot;形式的path，这里的[xx] 指的是一个可变的部分，
用于表示一个特殊的FHIR API。一般而言，
is some variable. Typically, the variable id
identifies a patient or a user, and the underlying information is completely compartmented
by the logical identity associated with [xx]. In this case, the FHIR API presents a
patient or user centric view of a record, where authentication/authorization is
explicitly granted to the URL, on the grounds that some identifiable user is associated
with the logical identity. It is not necessary to explicitly embed the patient id in the
URL - implementations can associate an FHIR end-point with a particular patient or
provider by using an OAuth login. See [Compartments](extras.html#compartments) for the logical underpinning.

### <span class="sectioncount">2.1.0.2<a name="2.1.0.2"> </a></span> Resource Metadata and Versioning

Each resource has an associated set of [resource metadata elements](resource.html#metadata). These map to the http request and response using the following fields:

<table class="grid">
  <tr><th>Metadata Item</th><th>Where found in HTTP</th></tr>
  <tr><td>[Logical Id (.id)](resource.html#id)</td><td>The Id is represented explicitly in the URL</td></tr>
  <tr><td>[Version Id (.meta.versionId)](resource.html#metadata)</td><td>The Version Id is represented in the `ETag` header. It SHOULD also be returned
    as a full canonical URL in the Content-Location header (see [vread](#vread) below)</td></tr>
  <tr><td>Last modified (.meta.lastUpdated)</td><td>HTTP Last-Modified header</td></tr>
</table>

Note that the Version Id is considered a &quot;weak&quot; ETag and `ETag` headers
	should be prefixed with &quot;W/&quot; and enclosed in quotes, for example:

<pre>
ETag: W/&quot;3141&quot;
</pre>

### <span class="sectioncount">2.1.0.3<a name="2.1.0.3"> </a></span> Security

Using HTTPS is optional, but all production exchange of healthcare data SHOULD use SSL and
additional security as appropriate. See [HTTP Security](security.html#http) for further information.

The choice of whether to return 403 or 404 depends upon the specific situation and specific
local policies, regulations, and laws. The decision of which error to use will include consideration
of whether disclosure of the existence of relevant records is considered an acceptable
disclosure of PI or  a prohibited disclosure of PI.

Note: to support browser-based client applications, recommend that servers SHOULD implement [cross-origin resource sharing](http://enable-cors.org/) for the operations documented here.

### <span class="sectioncount">2.1.0.4<a name="2.1.0.4"> </a></span> HTTP Status Codes

This specification makes rules about the use of specific HTTP status codes
in particular circumstances where the status codes SHALL map to particular
states correctly, and only where the correct status code is not obvious.
Other HTTP status codes may be used for other states as appropriate, and this particularly
includes various authentication related status codes and redirects.
Authentication redirects should not be interpreted to change the location
of the resource itself (a common web programming error).

FHIR defines an [OperationOutcome resource](operationoutcome.html) that can be used to convey specific detailed
processable error information. For a few combinations of interactions and specific
return codes, an OperationOutcomeis required to be returned as the content of the response.
The OperationOutcome may be returned with any HTTP 4xx or 5xx response, but is not required - many of
these errors may be generated by generic server frameworks underlying a FHIR server.

<a name="return"> </a>

### <span class="sectioncount">2.1.0.5<a name="2.1.0.5"> </a></span> Managing Return Content

In the interests of managing band-width, this specification allows clients
to specify what kind of content to return.

#### <span class="sectioncount">2.1.0.5.1<a name="2.1.0.5.1"> </a></span> conditional read

Clients may use the `If-Modified-Since`, or `If-None-Match` HTTP header on a `read` request.
If so, they MUST accept either a 304 Not Modified as a valid status code on the response (which means that the
content is unchanged since that date) or full content (either the content has not changed,
or the server does not support conditional request).

Servers can return 304 Not Modified where content is unchanged since the
`If-Modified-Since` date-time or the `If-None-Match` ETag specified or they can
return the full content as normal. This optimisation is relevant in reducing bandwidth for caching purposes and servers are encouraged but
not required to support this.

#### <span class="sectioncount">2.1.0.5.2<a name="2.1.0.5.2"> </a></span> create/update/transaction

These operations are performed using `POST`,`PUT` and `POST` respectively, and
it may be appropriate for a server to return either only a status
code, or also return the entire resource that is the outcome of the
create or update (which may be different to that provided by the
client). In the case of transactions this means returning a Bundle with just the `Bundle.entry.transactionResponse`,
not the `Bundle.entry.resource`.

The client can indicate whether the entire resource is
returned using the [HTTP
return preference](https://tools.ietf.org/html/rfc7240#section-4.2):

<pre>
Prefer: return=minimal
Prefer: return=representation
</pre>

The first of these two asks to return no body (or an operation outcome). The
second asks to return the full resource. Servers SHOULD honour this header.
In the absence of the header, servers may chose whether to return the
full resource or not.

<a name="mime-type"> </a>

### <span class="sectioncount">2.1.0.6<a name="2.1.0.6"> </a></span> Content Types and encodings

The formal MIME-type for FHIR resources is `application/xml+fhir` or `application/json+fhir`.
The correct mime type SHALL be used by clients and servers:

*   XML: **application/xml+fhir**
*   JSON: **application/json+fhir**

Servers SHALL support server-driven content negotiation
as described in [section 12](http://www.w3.org/Protocols/rfc2616/rfc2616-sec12.html#sec12)
of the HTTP specification.

However in order to support various implementation limitations, servers SHOULD
support the optional `_format` parameter to specify alternative response formats by their MIME-types.
This parameter allows a client to override the header value when it is unable to set it correctly
due to internal limitations.
For the `_format` parameter, the values &quot;xml&quot;, &quot;text/xml&quot;, &quot;application/xml&quot;, and &quot;application/xml+fhir&quot; SHALL be interpreted to mean
the normative XML format defined by FHIR and &quot;json&quot;, &quot;application/json&quot; and &quot;application/json+fhir&quot; SHALL be interpreted to mean the
informative JSON format.

FHIR uses UTF-8 for all request and response bodies. Since the HTTP specification (section 3.7.1)
defines a default character encoding of ISO-8859-1, requests and responses SHALL explicitly set
the character encoding to UTF-8 using the `charset` parameter of the MIME-type in the `Content-Type` header.
Requests MAY also specify this `charset` parameter in the `Accept` header and/or use the `Accept-Charset` header.

<a name="versioning"> </a>

### <span class="sectioncount">2.1.0.7<a name="2.1.0.7"> </a></span> Support for Versions

Servers that support this API SHOULD provide full version support - that is, populate and track
versionId correctly, support `vread`, and implement [version aware updates](#versionaware).
Supporting versions like this allows for related systems to track the correct version of information,
and to keep integrity in clinical records. However, many current operational systems do not
do this, and cannot easily be re-engineered to do so.

For this reason, Servers are allowed to not provide versioning support: this API does not enforce
that they are supported. Clients may elect to only interact with servers that do provide full
versioning support. Systems declare their support for versioning
in their [conformance statement](conformance-definitions.html#Conformance.rest.resource.noVersion).

<a name="read"> </a>

### <span class="sectioncount">2.1.0.8<a name="2.1.0.8"> </a></span> read

The `read` interaction accesses the current contents of a resource. The interaction
is performed by an HTTP `GET` command as shown:

<pre>
  GET [base]/[type]/[id] {?_format=[mime-type]}
</pre>

This returns a single instance with the content specified for the resource type.
This url may be accessed by a browser. The possible values for the
[Logical Id](resource.html#id) (id) itself are described in the [id type](datatypes.html#id).
The returned resource SHALL have an `id` element with a value that is the [id].
Servers SHOULD return an `ETag` header with the versionId and a `Content-Location` header with the response which is the full version
specific url (see vread below) and a `Last-Modified` header.

Note: Unknown resources and deleted resources are treated differently on a read: A `GET` for a deleted
resource returns a 410 status code, whereas a `GET` for an unknown resource returns 404. Systems that do
not track deleted records will treat deleted records as an unknown resource.

<a name="vread"> </a>

### <span class="sectioncount">2.1.0.9<a name="2.1.0.9"> </a></span> vread

The `vread` interaction preforms a version specific read of the resource. The interaction
is performed by an HTTP GET command as shown:

<pre>
  GET [base]/[type]/[id]/_history/[vid] {?_format=[mime-type]}
</pre>

This returns a single instance with the content specified for the resource type for that
version of the resource.
The returned resource SHALL have an `id` element with a value that is the [id], and a `meta.versionId`
element with a value of [vid]. Servers SHOULD return an `ETag` header with the versionId and a `Content-Location` header with the response which is the full version
specific url (see vread below) and a `Last-Modified` header.

The [Version Id](resource.html#metadata) (vid) is an opaque identifier that conforms to the same [format requirements](datatypes.html#id) as
a [Logical Id](resource.html#id). The id may have been found by performing a history interaction (see below), by recording the
version id from a content location returned from a read or from a version specific reference in a
content model. If the version referred to is actually one where the resource was deleted, the
server should return a 410 status code.

Servers are encouraged to support a version specific retrieval of the current version of the
resource even if they are do not provide access to previous versions. If a request
is made for a previous version of a resource, and the server does not support accessing
previous versions, it should return a 404 Not Found error, with an operation outcome
explaining that history is not supported for the underlying resource type.

<a name="update"> </a>

### <span class="sectioncount">2.1.0.10<a name="2.1.0.10"> </a></span> update

The `update` interaction creates a new current version for an existing resource or
creates an initial version if no resource already exists for the given id.
The `update` interaction is performed by an HTTP `PUT` command as shown:

<pre>
  PUT [base]/[type]/[id] {?_format=[mime-type]}
</pre>

The request body SHALL be a [Resource](resource.html) with an id element that has an identical value to the [id] in the URL.
If the request body includes a [meta](resource.html#meta), the server SHALL
ignore the existing `versionId` and `lastUpdated` values.
The server SHALL populate the `meta.versionId` and `meta.lastUpdated`
with the new correct values.
Servers are allowed to review and alter the other metadata values, but SHOULD refrain
from doing so (see [metadata description](resource.html#meta)  for further information).

A server SHOULD accept the resource as submitted when accepts the update, and return the same
content when it is subsequently read. However systems may not be able to do this; see
the note on [transactional integrity](#transactional-integrity) for discussion.

If the interaction is successful, the server SHALL return either a 200 OK HTTP status code if the resource was updated, or a 201 Created status code if the resource was created,
with a `Last-Modified` header, and an `ETag` header which contains the new `versionId` of the resource. A `Content-Location` header
that refers to the specific version created by the update interaction SHOULD also be returned. If the resource was created (i.e. the interaction resulted in a 201 Created), the server SHOULD
return a `Location` header.

The server MAY include a response body containing an [OperationOutcome](operationoutcome.html)
resource with hints and warnings about the resource; if one is sent it SHALL not include any errors.

#### <span class="sectioncount">2.1.0.10.1<a name="2.1.0.10.1"> </a></span> Conditional updates

The conditional update operation allows a client to update an existing resource based on some identification criteria,
rather than by  [logical id](resource.html#meta). To accomplish this, the client issues a `PUT` as shown:

<pre>
  PUT [base]/[type]/?[search parameters]
</pre>

When the server processes this update, it performs a search using its standard
[search facilities](search.html) for the resource type, with the goal of resolving a single logical id for this request. The action it takes depends
on how many matches are found:

*   **No matches**: The server performs a [create](#create) operation
*   **One Match**: The server performs the update against the matching resource
*   **Multiple matches**: The server returns a 412 Precondition Failed error indicating the the client's criteria were not selective enough

This variant can be used to allow a stateless client (such as an interface engine) to submit
updated results to a server, without having to remember the logical ids that the server has assigned.
For example, a client updating the status of a lab result from &quot;preliminary&quot; to &quot;final&quot;
might submit the finalized result using `PUT /Observation?identifier=http://my-lab-system|123`

#### <span class="sectioncount">2.1.0.10.2<a name="2.1.0.10.2"> </a></span> Rejecting Updates

Servers are permitted to reject update interactions because of integrity concerns or other business
returning HTTP status codes accordingly (usually a 422).

Common HTTP Status codes returned on FHIR-related errors (in addition to normal HTTP errors related to security, header and content type negotiation issues):

*   **400 Bad Request** - resource could not be parsed or failed basic FHIR validation rules (or multiple matches were found for*   **404 Not Found** - resource type not supported, or not a FHIR end point
*   **405 Method Not allowed** - the resource did not exist prior to the update, and the serer does not allow client defined ids
*   **409/412** - version conflict management - see above
*   **422 Unprocessable Entity** - the proposed resource violated applicable FHIR profiles or server business rules. This should be accompanied by an [OperationOutcome](operationoutcome.html) resource providing additional detail

Note: Servers MAY choose to preserve XML comments, instructions, and formatting or JSON whitespace when accepting updates, but are not required to do so. The impact of this on digital signatures may need to be considered.

For additional information on how systems may behave when processing updates, refer to the [Create and Update Behavior](updates.html) page.

<a name="versionaware"> </a>
<a name="concurrency"> </a>

### <span class="sectioncount">2.1.0.11<a name="2.1.0.11"> </a></span> Managing Resource Contention

[Lost Updates](http://www.w3.org/1999/04/Editing/), where two clients update the same
resource, and the second overwrites the updates of the first, can be prevented using a combination
of the [ETag](http://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html#sec14.19) and
[If-Match](http://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html#sec14.24) header.

To support this usage, servers SHOULD always return an `ETag` header with each resource:

<pre class="http">
HTTP 200 OK
Date: Sat, 09 Feb 2013 16:09:50 GMT
Last-Modified: Sat, 02 Feb 2013 12:02:47 GMT
ETag: W/&quot;23&quot;
Content-Type: application/json+fhir
</pre>

if provided, the value of the ETag SHALL match the value of the version id for the resource. Servers
are allowed to generate the version id in whatever fashion that they wish, so long
as they are valid according to the [id](datatypes.html#id) data type,
and are unique within the address space of all versions of the same resource.
When resources are returned as part of a bundle, there is no ETag, and the
versionId of the resources is used directly.

If the client wishes to request a version aware update, it submits the request with an
`If-Match` header that quotes the ETag from the server:

<pre class="http">
PUT /Patient/347 HTTP/1.1
If-Match: W/&quot;23&quot;
</pre>

If the version id given in the `If-Match` header does not match, the server returns a
412 Pre-condition failed status code instead of updating the resource.

Servers can require that clients provide an `If-Match` header by returning 412 Pre-condition failed
status codes when no `If-Match` header is found.

<a name="delete"> </a>

### <span class="sectioncount">2.1.0.12<a name="2.1.0.12"> </a></span> delete

The `delete` interaction removes an existing resource. The interaction
is performed by an HTTP DELETE command as shown:

<pre>
  DELETE [base]/[type]/[id]
</pre>

A delete interaction means that subsequent [non-version specific reads](#read) of a resource
return a 410 HTTP status code and that the resource is no longer found through [search](#search)
interactions. Upon successful deletion, or if the resource does not exist at all, the server should return
204 (No Content), or 200 OK status code, with an [OperationOutcome](operationoutcome.html)
resource containing hints and warnings about the deletion; if one is sent it SHALL not include any errors.

Whether to support delete at all, or for a particular resource type or a particular instance is at the
discretion of the server based on the business rules that apply in its context.  
If the server refuses to delete resources of that type as a blanket policy, then it should return the 405
Method not allowed status code. If the server refuses to delete a resource because of reasons specific
to that resource, such as referential integrity, it should return the 409 Conflict status code.
Performing this interaction on a resource that is already deleted has no effect, and the server should return a 204 or 200 response.
Resources that have been deleted may be &quot;brought back to life&quot; by a subsequent [update](#href) interaction using an HTTP `PUT`.

Many resources have a status element that overlaps with the idea of deletion. Each resource type
defines what the semantics of the deletion interactions are. If no documentation is provided, the
deletion interaction should be understood as deleting the record of the resource, with nothing
about the state of the real-world corresponding resource implied.

For servers that maintain a version history, the `delete` operation does not remove a resource's version history. From a version history respect,
deleting a resource is the equivalent of creating a special kind of history entry that has
no content and is marked as deleted.

#### <span class="sectioncount">2.1.0.12.1<a name="2.1.0.12.1"> </a></span> Conditional deletes

The conditional delete operation allows a client to update an existing resource based on some identification criteria,
rather than by  [logical id](resource.html#meta). To accomplish this, the client issues an HTTP DELETE as shown:

<pre>
  DELETE [base]/[type]/?[search parameters]
</pre>

When the server processes this update, it performs a search as specified using the standard
[search facilities](search.html) for the resource type. The action it takes depends
on how many matches are found:

*   **No matches**: The server returns 404 (Not found)
*   **One Match**: The server performs an ordinary `delete` on the matching resource
*   **Multiple matches**: The server returns a 412 Precondition Failed error indicating the the client's criteria were not selective enough

This variant can be used to allow a stateless client (such as an interface engine) to delete
a resource on a  server, without having to remember the logical ids that the server has assigned.
For example, a client deleting a lab atomic result might delete the resource using `DELETE /Observation?identifier=http://my-lab-system|123`.

<a name="create"> </a>

### <span class="sectioncount">2.1.0.13<a name="2.1.0.13"> </a></span> create

The `create` interaction creates a new resource in a server-assigned location. If the client
wishes to have control over the id of a newly submitted resource, it should use the [update](#update)
interaction instead. The `create` interaction is performed by an HTTP `POST` command as shown:

<pre>
  POST [base]/[type] {?_format=[mime-type]}
</pre>

The request body SHALL be a FHIR Resource without an id element (this is the
only case where a resource exists without an id element).
If the request body includes a [meta](resource.html#meta), the server SHALL
ignore the existing `versionId` and `lastUpdated` values.
The server SHALL populate the `meta.versionId` and `meta.lastUpdated`
with the new correct values.
Servers are allowed to review and alter the other metadata values, but SHOULD refrain
from doing so (see [metadata description](resource.html#meta)  for further information).

A server SHOULD accept the resource as submitted when it accepts the create, and return the same
content when it is subsequently read. However some systems may not be able to do this; see
the note on [transactional integrity](#transactional-integrity) for discussion.

The server returns a 201 Created HTTP status code, and SHOULD also return a `Location` header which
contains the new [Logical Id](resource.html#metadata) and [Version Id](resource.html#metadata) of
the created resource version:

<pre>
  Location: [base]/[type]/[id]/_history/[vid]
</pre>

where [id] and [vid] are the newly created id and version id for the resource version.

Servers SHOULD return an `ETag` header with the versionId and a `Content-Location` header with the response which is the full version
specific url (see vread below) and a `Last-Modified` header.
The server MAY include a response body containing an [OperationOutcome](operationoutcome.html) resource with hints and warnings about
the resource; if one is sent it SHALL not include any errors.

When the resource syntax or data is incorrect or invalid, and cannot be used to create a new resource, the server returns a 400 Bad Request HTTP status code.
When the server rejects the content of the resource because of business rules, the server returns a 422 Unprocessible Entity error HTTP status code.
In either case, the server SHOULD include a response body containing an [OperationOutcome](operationoutcome.html) with detailed error messages describing the reason for the error.

Common HTTP Status codes returned on FHIR-related errors (in addition to normal HTTP errors related to security, header and content type negotiation issues):

*   **400 Bad Request** - resource could not be parsed or failed basic FHIR validation rules
*   **404 Not Found** - resource type not supported, or not a FHIR end point
*   **422 Unprocessable Entity** - the proposed resource violated applicable FHIR profiles or server business rules. This should be accompanied by an [OperationOutcome](operationoutcome.html) resource providing additional detail

Note: Servers MAY choose to preserve XML comments, instructions, and formatting or JSON whitespace when accepting creates, but are not required to do so. The impact of this on digital signatures may need to be considered.

For additional information on how systems may behave when processing updates, refer to the [Create and Update Behavior](updates.html) page.

#### <span class="sectioncount">2.1.0.13.1<a name="2.1.0.13.1"> </a></span> Conditional create

The conditional `create` operation allows a client to create a new resource only if some equivalent resource
does not already exist on the server. The client defines what equivalence means in this case by supplying
a FHIR search query in an `If-None-Exist` header as shown:

<pre>
  If-None-Exist: base/[type]?[search parameters]
</pre>

When the server processes this update, it performs a search as specified using its standard
[search facilities](search.html) for the resource type. The action it takes depends
on how many matches are found:

*   **No matches**: The server processes the create as above
*   **One Match**: The server ignore the post and returns 200 OK
*   **Multiple matches**: The server returns a 412 Precondition Failed error indicating the the client's criteria were not selective enough

This variant can be used to avoid the risk of two clients
creating duplicate resources for the same record. For example, a client posting a new lab result might specify
`If-None-Exist: /Observation?identifier=http://my-lab-system|123` to ensure it is does not create a duplicate record.

<a name="search"> </a>

### <span class="sectioncount">2.1.0.14<a name="2.1.0.14"> </a></span> search

This interaction searches a set of resources based on some filter criteria. The interaction can be performed by several different HTTP commands.

<pre>
  GET [base]/[type]{?[parameters]{&amp;_format=[mime-type]}}
</pre>

This searches all resources of a particular type using the criteria represented in the parameters.

Because of the way that some user agents and proxies treat `GET` and `POST` requests, in addition
to the get based search method above, servers that support _search_ SHALL also support a `POST` based search:

<pre>
POST  [base]/[type]/_search{?[parameters]{&amp;_format=[mime-type]}}
</pre>

This has exactly the same semantics as the equivalent `GET` command. All these search interactions take a series of parameters that
are a series of name'='value pairs encoded in the URL (or as an `application/x-www-form-urlencoded` submission for a `POST`).
(See [W3C HTML forms](http://www.w3.org/TR/REC-html40/interact/forms.html#form-content-type)).
Searches are processed as specified for the [Search handling mechanism](search.html).

If the search fails, the return value is a status code 4xx or 5xx with an [OperationOutcome](operationoutcome.html).
If the search succeeds, the return content is a [Bundle](extras.html#bundle) with
[type](bundle-definitions.html#Bundle.type) = `searchset` containing the results of the search as a list of resources
in a defined order. The result list can be long, so servers may use paging. If they do, they SHALL use the method [described below](#paging)
(adapted from [RFC 5005 (Feed Paging and Archiving](https://tools.ietf.org/html/rfc5005)) for breaking the
list into pages if appropriate. The server MAY also return an OperationOutcome resource with additional information about the search;
if one is sent it SHALL not include any errors, and it shall be marked with an [entry
mode](search-entry-mode.html) of `include`.

#### <span class="sectioncount">2.1.0.14.1<a name="2.1.0.14.1"> </a></span> Variant Searches

To search a [compartment](extras.html#compartments), either all possible resources, or for a particular resource type, respectively:

<pre>
  GET [base]/[Compartment]/[id]/{*?[parameters]{&amp;_format=[mime-type]}}
  GET [base]/[Compartment]/[id]/[type]{?[parameters]{&amp;_format=[mime-type]}}
</pre>

For example, to retrieve all the observation resources for a particular LOINC code associated with a particular encounter:

<pre>
  GET [base]/Encounter/23423445/Observation?code=2951-2  {&amp;_format=[mime-type]}
</pre>

Note that there are a specific operations defined to support fetching [an entire patient record](patient-operations.html#everything)
or [all record for an encounter](encounter-operations.html#everything).

Finally, it's possible to search all resources at once:

<pre>
  GET [base]?[parameters]{&amp;_format=[mime-type]}
</pre>

When searching all resources at once, only the parameters defined for all resources
can be used.

<a name="conformance"> </a>

### <span class="sectioncount">2.1.0.15<a name="2.1.0.15"> </a></span> conformance

The conformance interaction retrieves the server's conformance statement that defines how it supports resources.
The interaction is performed by an HTTP OPTIONS or a `GET` command as shown:

<pre>
  GET [base]/metadata {?_format=[mime-type]}
  OPTIONS [base] {?_format=[mime-type]}
</pre>

Applications SHALL return a [Conformance Resource](conformance.html) that specifies which resource types and interactions are supported
for the `GET` command, and SHOULD do so for the `OPTIONS` command. If a 404 Unknown is returned from the GET, FHIR is not supported on the
nominated service url. The `GET` command is defined because not all client libraries are able to perform an `OPTIONS` command.
An `ETag` header SHALL be returned with the conformance resource. The value of the header SHALL change if the
conformance statement itself changes. In addition, a `Content-Location` header with a literal location where this version of the
conformance statement is (and will continue to be) available MAY be returned. Additional parameters that are required to be returned with
the `OPTIONS` command are defined in the [OMG hData RESTful Transport](#hdata) specification.

The Conformance statement returned typically has an arbitrary id, and no meta element, though it is not prohibited.

In addition to this conformance operation, a server may also choose to provide the
standard set of interactions (`read`, `search`, `create`, `update`) defined on this page
for the [Conformance Resource](conformance.html) end point.
This is different to the conformance operation:

<table class="grid">
 <tr><td>conformance operation</td><td>returns a conformance statement describes the server's current operational functionality</td></tr>
 <tr><td>Conformance end point</td><td>manages a repository of conformance statements (e.g. the HL7 conformance statement registry)</td></tr>
</table>

All servers are required to support the conformance operation, but servers may choose whether they wish to support the conformance end-point, just like any other end point.

<a name="transaction"> </a>

### <span class="sectioncount">2.1.0.16<a name="2.1.0.16"> </a></span> transaction

The transaction interaction submits a set of actions to perform on a server as a single atomic action.
Multiple actions on multiple resources of the same or different types may be submitted, and they may be a mix of other operations defined on this page (e.g. read, search, create, update, delete, etc).

This is especially useful where one would otherwise need multiple interactions, possibly
with a risk of loss of referential integrity if a later interaction fails (e.g. when storing
a Provenance resource and its corresponding target resource, or, on document repositories, a
document index entry and its accompanying document).

The transaction interaction is performed by an HTTP `POST` command as shown:

<pre>
  POST [base] {?_format=[mime-type]}
</pre>

The content of the post submission is a [Bundle](bundle.html) with type set to `transaction`.
Each entry carries a `transaction` ([Bundle.entry.transaction](bundle-definitions.html#Bundle.entry.transaction))
that provides the HTTP details of the operation in order to inform the system processing the transaction
what to do for the entry. If the HTTP operation is a `PUT` or `POST`, then the entry SHALL contain a resource for the body of the operation.
The resources in the bundle are each processed separately as if they were an individual
operation as otherwise described on this page, or for [Extended
Operations](operations.html). The operations are subject to the the normal processing for each,
including the [meta element](resource.html#meta), verification and version aware updates,
and [transactional integrity](#transactional-integrity).

Servers SHALL either accept all actions and return a 200 OK, along with a
response bundle (see below), or reject all resources and return an HTTP 400 or 500 type
response. It is not an error if the submitted bundle has no resources in it.
The outcome of the processing the transaction SHALL not depend on the order
of the resources in the transaction. A resource can only appear in a transaction
once (by identity).

**Processing Bundle Entries**

Because of the rules that a transaction is atomic, that all operations pass or fail
together, and that order of the entries doesn't matter, there is a particular order in which to process the operations:

1.  Process any `POST` operations
2.  Process any `PUT` operations
3.  Process any `DELETE` operations
4.  Process any `GET` operations

If any resource identities (including resolved identities from conditional update/delete) overlap in steps 1-3, then the transaction SHALL fail.

A transaction may include references from one resource to another in the bundle, including
circular references where resources refer to each other. If the server assigns
a new id to any resource in the bundle as part of the processing rules above,
it SHALL also update any references to that resource in the same bundle as they
are processed. References to resources that are not
part of the bundle are left untouched. Version-specific references should remain
as version-specific references after the references have been updated.
Servers SHALL be replace all matching links in the bundle, whether they are found in the resource ids,
resource references, url elements, or &lt;a href=&quot;&quot; &amp; &lt;img src=&quot;&quot; in the narrative.

<a name="transaction-response"> </a>

#### <span class="sectioncount">2.1.0.16.1<a name="2.1.0.16.1"> </a></span> Transaction Response

In order to allow the client to know the outcomes of processing the entry, and the identities
assigned to the resources by the server, the server SHALL return a [Bundle](extras.html#bundle) with
[type](bundle-definitions.html#Bundle.type) set to `transaction-response` that contains one entry for each entry in the
transaction, in the same order, with the outcome of processing the entry.

Each entry element SHALL contain a `transactionResponse` element which
details the outcome of processing the entry - the HTTP status code, and the location
and `ETag` header values, which are used for identifying and versioning the resources.
In addition, a resource may be included in the entry.

<a name="other-bundles"> </a>

#### <span class="sectioncount">2.1.0.16.2<a name="2.1.0.16.2"> </a></span> Accepting Other bundle types

A server may choose to accept bundle types other than `transaction` as transactions.

Bundles of type `history` inherently have the same structure as a transaction, and
can be treated as one, so servers SHOULD accept a history bundle - this makes it
possible to replicate data from one server to another easily. Not, however, that
existing transaction boundaries are not represented in a history list, and
a resource may occur more than once in a history list, so
servers processing history bundles must have some strategy to manage this.

For other bundle types, should the server choose to accept them, there will be
no `transaction` element (note that every entry will have a resource).
In this case, the server treats the entry as either a create or an update operation,
depending on whether it recognises the identity of the resource - if the identity
of the resource refers to a valid location on the server, it should treat it
as an update to that location. Note: this option allows a client to delegate
the matching process to the server.

<a name="history"> </a>

### <span class="sectioncount">2.1.0.17<a name="2.1.0.17"> </a></span> history

The history interaction retrieves the history of either a particular resource, all resources of
a given type, or all resources supported by the system. These three variations of the history
interaction are performed by HTTP `GET` command as shown:

<pre>
  GET [base]/[type]/[id]/_history{?[parameters]&amp;_format=[mime-type]}
  GET [base]/[type]/_history{?[parameters]&amp;_format=[mime-type]}
  GET [base]/_history{?[parameters]&amp;_format=[mime-type]}
</pre>

The return content is a [Bundle](extras.html#bundle) with
[type](bundle-definitions.html#Bundle.type) set to `history` containing the specified version history,
sorted with oldest versions last, and including deleted resources.
Each entry SHALL contain a `transaction`, and, if the `entry.transaction.method` is a `PUT` or a `POST`, a resource.
The entry SHALL contain the resource state at the conclusion of the operation.

The operations [create](#create), [update](#update), and [delete](#delete)
create history entries. Other operations do not (note that these operations may produce side-effects
such as new AuditEvent resources; these are represented as create operations in their own right).

A create operation is represented in a history operation in the following way:

<pre class="xml">
  &lt;entry&gt;
    &lt;resource&gt;
      &lt;Patient&gt;
        &lt;!-- the id of the created resource --&gt;
        &lt;id value=&quot;23424&quot;/&gt;
        &lt;!-- snip --&gt;
      &lt;/Patient&gt;
    &lt;/resource&gt;
    &lt;transaction&gt;
      &lt;!-- POST: this was a create --&gt;
      &lt;method value=&quot;POST&quot;/&gt;
      &lt;url value=&quot;Patient&quot;/&gt;
    &lt;/transaction&gt;
  &lt;/entry&gt;
</pre>

Note that conditional creates, updates and deletes are converted to direct
updates and deletes in a history list.

In addition to the standard `_format` parameter, the parameters to this interaction may also include:

<table class="list">
  <tr><td>_count : [integer](datatypes.html#integer)</td><td>single</td><td>Number of return records requested. The server is not bound to return the number requested, but cannot return more</td></tr>
  <tr><td>_since : [instant](datatypes.html#integer)</td><td>single</td><td>Only include resource versions that were created at or after the given instant in time</td></tr>
</table>

The history list can be restricted to a limited period by specifying a `_since` parameter which contains a full date time with time zone.
Clients should be aware that due to timing imprecision, they may receive notifications of a resource update on the boundary instant more than once. Servers are
not required to support a precision finer than by second.

The updates list can be long, so servers may use paging. If they do, they SHALL use the method [described
below](#paging) for breaking the list into pages if appropriate, and maintain the specified _count across pages.

The history interaction can be used to set up a subscription from one system
to another, so that resources are synchronized between them. Refer to the [Subscription resource](subscription.html)
for an alternate means of system synchronization.

<a name="transactional-integrity"> </a>

### <span class="sectioncount">2.1.0.18<a name="2.1.0.18"> </a></span> Transactional Integrity

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
be driven by security considerations. With regard to incomplete support, Clients can consult the server's
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
*   The client writes the result back as an [update](#update) operation, and is able to handle a 409 or 412 response (usually by trying again)

If clients follow this pattern, then information from other systems
that they do not understand will be maintained through the update.

Note that it's possible for a server to choose to maintain the
information that would be lost, but there is no defined way for
a server to determine whether the client omitted the information
because it wasn't supported (perhaps in this case) or whether it
wishes to delete the information.

#### <span class="sectioncount">2.1.0.18.1<a name="2.1.0.18.1"> </a></span> Conformance

Both client and server systems SHOULD clearly document how transaction
integrity is handled.

DSTU TODO: how?

<a name="paging"> </a>

### <span class="sectioncount">2.1.0.19<a name="2.1.0.19"> </a></span> Paging

If servers provide paging for the results of a [search](#search) or [history](#history) interaction,
they SHALL conform to this method (adapted from [RFC 5005 (Feed
Paging and Archiving)](https://tools.ietf.org/html/rfc5005) for sending continuation links to the client when returning a [Bundle](bundle.html)
(e.g. with history and search). If the server does not do this, there is no way to continue paging.

This example shows the third page of a search result:

<pre class="xml">
&lt;Bundle xmlns=&quot;http://hl7.org/fhir&quot;&gt;
  &lt;!-- snip metadata --&gt;
  &lt;!-- This Search. url starts with base search, and adds the effective
    parameters, and additional parameters for search state. All searches
    SHALL return this value.

	  In this case, the search continuation method is that the server
    maintains a state, with page references into the stateful list.
	--&gt;
  &lt;link&gt;
    &lt;relation value=&quot;self&quot;&gt;
    &lt;url value=&quot;http://example.org/Patient?name=peter&amp;stateid=23&amp;page=3&quot;/&gt;
  &lt;/link&gt;
  &lt;!-- 4 links for navigation in the search. All of these are optional, but recommended --&gt;

  &lt;link&gt;
    &lt;relation value=&quot;first&quot;/&gt;
    &lt;url value=&quot;http://example.org/Patient?name=peter&amp;stateid=23&amp;page=1&quot;/&gt;
  &lt;/link&gt;
  &lt;link&gt;
    &lt;relation value=&quot;previous&quot;/&gt;
    &lt;url value=&quot;http://example.org/Patient?name=peter&amp;stateid=23&amp;page=2&quot;/&gt;
  &lt;/link&gt;
  &lt;link&gt;
    &lt;relation value=&quot;next&quot;/&gt;
    &lt;url value=&quot;http://example.org/Patient?name=peter&amp;stateid=23&amp;page=4&quot;/&gt;
  &lt;/link&gt;
  &lt;link&gt;
    &lt;relation value=&quot;last&quot;/&gt;
    &lt;url value=&quot;http://example.org/Patient?name=peter&amp;stateid=23&amp;page=26&quot;/&gt;
  &lt;/link&gt;

  &lt;!-- then the search results... --&gt;
&lt;/Bundle&gt;
</pre>

The server need not use a stateful paging method as shown in this example - it is at
the discretion of the server how to best ensure that the continuation retains
integrity in the context of ongoing changes to the resources. An alternative approach
is to use version specific references to the records on the boundaries, but this is
subject to continuity failures when records are updated.

A server MAY inform the client of the total number of resources returned by the interaction for which the results are paged
using  the [Bundle.total](bundle-definitions.html#Bundle.total).

Note that for search, where _include can be used to return additional related resources, the total number
of resources in the feed may exceed the number indicated in totalResults.

### <span class="sectioncount">2.1.0.20<a name="2.1.0.20"> </a></span> Intermediaries

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

### <span class="sectioncount">2.1.0.21<a name="2.1.0.21"> </a></span> OMG hData RESTful Transport

This RESTful specification described here is based on the [OMG Health RESTful specification](http://www.omg.org) (specific reference to be provided when this is published).
In this regard, FHIR functions as a Record Format Profile as described in that specification. Note the following significant factors to be aware of:

*   FHIR maps the hData sections to resource types, and hData documents to resource instances. There are no subsections, and client systems are not able to create new sections,
 though [compartments](extras.html#compartments) behave somewhat like sections
*   Because clients cannot submit new sections (`POST` to service URL), `POST` to the service URL has been re-used for [the transaction
 interaction](#transaction) (difference under review)
*   FHIR does not (yet) define a root document. When defined, it will contain information about what the FHIR server has done (as opposed to a conformance statement, which describes what it is capable of doing)
*   Note that this specification does not repeat the rules in the hData RESTful Transport concerning the `OPTIONS` command on the service URL, but these rules (extra headers etc.) still apply

<a name="summary"> </a>

### <span class="sectioncount">2.1.0.22<a name="2.1.0.22"> </a></span> Summary

These tables present a summary of the interactions described here.

Note that _all_ requests may include an optional `Accept` header to indicate the format used for the response (this is even true for `DELETE` since an OperationOutcome may be returned).

<table class="grid">
<tr><th>Interaction</th>                <th>Path</th><th colspan="5">Request</th></tr>
<tr><th colspan="2"/>                                                       <th>Verb</th>           <th>Content-Type</th>   <th>Body</th>     <th>Prefer</th>         <th>Conditional</th></tr>
<tr><td>read</td>                       <td>/[type]/[id]</td>                   <td>GET</td>            <td>N/A</td>            <td>N/A</td>      <td>N/A</td>     		  <td>O: ETag, If-Modified-Since, If-None-Match</td></tr>
<tr><td>vread</td>                      <td>/[type]/[id]/_history/[vid]</td>    <td>GET</td>            <td>N/A</td>            <td>N/A</td>      <td>N/A</td>         	<td>N/A</td></tr>
<tr><td>update</td>                     <td>/[type]/[id]</td>                   <td>PUT</td>            <td>R</td>              <td>Resource</td> <td>O</td>         	<td>O: If-Match</td></tr>
<tr><td>delete</td>                     <td>/[type]/[id]</td>                   <td>DELETE</td>         <td>N/A</td>            <td>N/A</td>      <td>N/A</td>	         <td>N/A</td></tr>
<tr><td>create</td>                     <td>/[type]</td>                        <td>POST</td>           <td>R</td>              <td>Resource</td> <td>O</td>         <td>O: If-None-Exist</td></tr>
<tr><td rowspan="2">search</td>         <td>/[type]?</td>                       <td>GET</td>            <td>N/A</td>            <td>N/A</td>	  <td>N/A</td>			<td>N/A</td></tr>
<tr>                                    <td>/[type]/_search?</td>               <td>POST</td>           <td>application/x-www-form-urlencoded</td>         <td>form data</td> <td>N/A</td>  <td>N/A</td></tr>
<tr><td rowspan="2">search-all</td>     <td>/_search? or /?</td>                <td>GET</td>            <td>N/A</td>            <td>N/A</td>              <td>N/A</td>  <td>N/A</td></tr>
<tr>                                    <td>/_search?</td>			            <td>POST</td>           <td>application/x-www-form-urlencoded</td>         <td>form data</td> <td>N/A</td> <td>N/A</td></tr>
<tr><td>conformance</td>                <td>/ or /metadata</td>                 <td>OPTIONS or GET</td>  <td>N/A</td>           <td>N/A</td>	   <td>N/A</td>			   	<td>N/A</td></tr>
<tr><td>transaction</td>                <td>/</td>                              <td>POST</td>           <td>R</td>              <td>Bundle</td>    <td>O</td>        <td>N/A</td></tr>
<tr><td>history</td>                    <td>/[type]/[id]/_history</td>          <td>GET</td>            <td>N/A</td>            <td>N/A</td>       <td>N/A</td>         <td>N/A</td></tr>
<tr><td>history-type</td>               <td>/[type]/_history</td>               <td>GET</td>            <td>N/A</td>            <td>N/A</td>       <td>N/A</td>         <td>N/A</td></tr>
<tr><td>history-all</td>                <td>/_history</td>                      <td>GET</td>            <td>N/A</td>            <td>N/A</td>       <td>N/A</td>         <td>N/A</td></tr>
<tr><td rowspan="3">(operation)</td>    <td rowspan="3">/$[name], /[type]/$[name]
										or /[type]/[id]/$[name]</td> 		  	<td>POST</td>           <td>R</td>         		<td>Parameters</td><td>N/A</td>			<td>N/A</td></tr>
																		<tr>    <td>GET</td>           	<td>N/A</td>         	<td>N/A</td> 	   <td>N/A</td>  		<td>N/A</td></tr>
																		<tr>    <td>POST</td>          	<td>application/x-www-form-urlencoded</td>         	<td>form data</td> 	   <td>N/A</td>  		<td>N/A</td></tr>
</table>

Notes:

*   N/A = not present, R = Required, O = optional
*   For operations defined on all resources, including direct access to the meta element, see [Resource Operations](resource-operations.html)

<table class="grid">
<tr><th>Interaction</th><th colspan="6">Response</th></tr>
<tr><th colspan="1"/>   <th>Content-Type</th> <th>Body</th>               <th>Location</th> 	<th>Content-Location</th> <th>Versioning</th> 					<th>Status Codes</th></tr>
<tr><td>read</td>           <td>R</td>            <td>R: Resource</td>           <td>N/A</td>      	<td>R</td>                <td>R: ETag, Last-Modified</td>		<td>200, 404, 410</td></tr>
<tr><td>vread</td>          <td>R</td>            <td>R: Resource</td>           <td>N/A</td>      	<td>R</td>                <td>R: ETag, Last-Modified</td>		<td>200, 404</td></tr>
<tr><td>update</td>         <td>R if body</td>    <td>O: Resource (Prefer)</td>                  <td>R on create</td>	<td>R</td>                <td>R: ETag, Last-Modified</td>		<td>200, 201, 400, 404, 405, 409, 412, 422</td></tr>
<tr><td>delete</td>         <td>R if body</td><td>O: OperationOutcome</td>  <td>N/A</td>      	<td>N/A</td>              <td>N/A</td>							<td>200, 204, 404, 405, 409, 412</td></tr>
<tr><td>create</td>         <td>R if body</td>    <td>O : Resource (Prefer)</td>                <td>R</td>			<td>R</td>               <td>R: ETag, Last-Modified</td>		<td>201, 400, 404, 405, 422</td></tr>
<tr><td>search</td>         <td>R</td>            <td>R: Bundle</td>             <td>N/A</td>      	<td>N/A</td>              <td>N/A</td>							<td>200, 403?</td></tr>
<tr><td>search-all</td>     <td>R</td>            <td>R: Bundle</td>             <td>N/A</td>      	<td>N/A</td>              <td>N/A</td>							<td>200, 403?</td></tr>
<tr><td>conformance</td>    <td>R</td>            <td>R: Conformance</td>        <td>N/A</td>      	<td>O</td>                <td>N/A</td>							<td>200, 404</td></tr>
<tr><td>transaction</td>    <td>R</td>            <td>R: Bundle</td>             <td>N/A</td>      	<td>N/A</td>              <td>N/A</td>							<td>200, 400, 404, 405, 409, 412, 422</td></tr>
<tr><td>history</td>        <td>R</td>            <td>R: Bundle</td>             <td>N/A</td>     		<td>N/A</td>              <td>N/A</td>							<td>200</td></tr>
<tr><td>history-type</td>   <td>R</td>            <td>R: Bundle</td>             <td>N/A</td>      	<td>N/A</td>              <td>N/A</td>							<td>200</td></tr>
<tr><td>history-all</td>    <td>R</td>            <td>R: Bundle</td>             <td>N/A</td>      	<td>N/A</td>              <td>N/A</td>							<td>200</td></tr>
<tr><td>(operation)</td>   	<td>R</td> 			  <td>R: Parameters/Resource</td><td>N/A</td>    	<td>N/A</td>			  <td>N/A</td>							<td>200</td></tr>
</table>

Note: this table lists the status codes described here, but other status codes are possible as described by the HTTP specification.
Additional codes that are likely a server errors and various codes associated with authentication protocols.


 &copy; HL7.org 2011 - 2014. FHIR DSTU (v0.2.1-2606)构建于2014  7月2号 16:29+0800 星期三 .
链接：[试行版是什么](http://hl7.org/implement/standards/fhir/dstu.html) |[版本更新情况](http://hl7.org/implement/standards/fhir/history.html) | [许可协议](http://hl7.org/implement/standards/fhir/license.html) |[提交变更建议](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemAdd&tracker_id=677)
