title: 
date: 
categories: doc
---

  [首页](../home/index.html) >[文档](documentation.html) > **面向开发人员的简介**	

## 1.9.1 FHIR Overview - Developers

FHIR (Fast Health Interoperability Resources)旨在数据交换，能够支撑医疗领域的多种流程。该标准基于Restful的最佳实践，能够实现跨团队的医疗系统的集成。 

FHIR 所支持的范围很广泛，包括人、兽医、临床、公共卫生、临床试验、管理和财务等方面。全球通用且支持多种架构和场景。

### 1.9.1.1 框架

FHIR 是基于 `资源`这一通用组件.  每个资源都有如下 [通用特征](resources.html):

*   用URL来标识   
*   通用的元数据 
*   [供人可读的XHTML概述](narrative.html)
*   通用的数据元集合
*   [扩展的框架](extensibility.html)以支持医疗中的多样性

资源要么是 [XML](xml.html) ，要么是 [JSON](json.html)格式的. 目前已经定义了99种[资源类型](resourcelist.html)

### 1.9.1.2  Patient实例

如何用JSON来表示[patient](patient.html)。 标准中也定义了XML的表达方式。

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

每个资源包括如下内容:  

*   **resourceType** (line 2) - 必须要有: FHIR 中定义了多种资源类型，详细列表请查看[the full index](resourcelist.html)
*   **id** (line 3) - 资源自身的id(而非资源中数据的ID 相当于资源在数据库中的主键). 一般而言都是要有的，除了在新建时之外。
*   **meta** (lines 4 - 7) - 通常要由 : [所有资源都会有的属性(这里和其他地方对元数据的定义略有偏差，参考https://github.com/memect/hao/issues/296)](resources.html#meta)受基础架构控制. 如果没有元数据可以为空
*   **text** (lines 12 - 17) - 推荐使用: XHTML 包含了资源中 [供人可读的部分](narrative.html) 
*   **extension** (lines 12 - 17) - 可选: [Extensions](extensibility.html)由扩展框架所定义
*   **data** (lines 18 - 43) - 可选: 每种资源所定义的数据项。

备注 尽管标准中总是以所定义的顺序来显示JSON中数据的顺序，但很多JSON库有其他排序标准。
### 1.9.1.3 交互

为了操作数据，FHIR 定义了[REST API](http.html):

*   [Create](http.html#create) = POST https://example.com/path/{resourceType}
*   [Read](http.html#read) = GET https://example.com/path/{resourceType}/{id}
*   [Update](http.html#update) = PUT https://example.com/path/{resourceType}/{id}
*   [Delete](http.html#delete) = DELETE https://example.com/path/{resourceType}/{id}
*   [Search](http.html#search) = GET https://example.com/path/{resourceType}?search parameters...
*   [History](http.html#history) = GET https://example.com/path/{resourceType}/{id}/_history
*   [Transaction](http.html#transaction) = POST https://example.com/path/
*   [Operation](operations.html) = GET https://example.com/path/{resourceType}/{id}/${opname}

除了RESTful API之外,FHIR 中还定义了其他的数据交换方式，包括 [文档](documents.html), 
[消息](messaging.html)和其他类型的[服务](services.html). 

### 1.9.1.4 对多样性的管理

医疗行业的一大特点就是不同地区和细分行业都存在很大的差异性,并不存在一个集中式的权威机构来定义通用的行业规范。鉴于此, 
FHIR 中定义了[通用扩展框架](extensibility.html)和
[管理多样性的框架](profiling.html).

### 1.9.1.5 新增资源

为了[新增资源](http.html#create), 需要发送一个 HTTP 的 POST 请求到某个资源节点(也就是某个URL).如下所示

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

向服务器提交一条患者记录, 服务器可以根据自己的情况分配ID来存储该患者记录。备注：

*   **/Patient** (line 1) - 处理所有患者的节点- 这里使用资源类型的名称
*   **Authorization** (line 2) - 参考 [Security for FHIR](security.html)
*   **Accept, Content-Type** (lines 3-4) - 如果资源的数据是JSON格式，content type需要设置成这样application/json+fhir (XML的话设置成 application/xml+fhir). 数据的编码始终是UTF-8
*   **id** (line 9) - 待新建的记录中并没有id，由服务器来分配   
*   Resource Content, lines 8+ - 这时候也没有任何元数据。资源的其他部分同上述示例  

### 1.9.1.6 新增资源的响应 

响应中包含HTTP 201，表示服务器已经成功新建该条记录。location header 属性中包含了访问该资源的URL。响应中亦可包含[OperationOutcome](operationoutcome.html) 资源来表达处理的一些细节,并不做硬性要求。

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

#### 1.9.1.6.1 Error response

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

### 1.9.1.7 Read Request

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

### 1.9.1.8 Read Response

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

### 1.9.1.9 Search Request

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

### 1.9.1.10 Search Response

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

### 1.9.1.11 Update Request

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

### 1.9.1.12 Update Response

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

### 1.9.1.13 Base Resource Content

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


&copy; HL7.org 2011+. FHIR DSTU (v0.4.0-3900) 构建于2014  12月20号 2014 22:38+0000 星期六 . 
  链接：[试行版是什么](http://hl7.org/implement/standards/fhir/dstu.htmll) |[版本更新情况](http://hl7.org/implement/standards/fhir/history.htmll) | [许可协议](http://hl7.org/implement/standards/fhir/license.htmll) |[提交变更建议](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemAdd&tracker_id=677)

