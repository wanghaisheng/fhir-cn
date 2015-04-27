title: 
date: 
categories: doc
---

  [首页](../home/index.html) >[文档](documentation.html) > **开发者指南**	

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

*   **HTTP/1.1 201** (line 1) - 操作成功. Note that HTTP/1.1 is strongly recommended but not required
*   **ETag** (line 5) - used in the [version aware update](http.html#update) pattern
*   **Location** (line 6) - the id the server assigned to the resource. The id in the url must match the id in the resource when it is subsequently returned
*   **operationOutcome** (line 9) - OperationOutcome resources in this context have no id or meta element (they have no managed identity)

#### 1.9.1.6.1 Error response

出于多种原因，服务器会返回一个错误信息，FHIR  内容相关的一些错误信息以HTTP 状态码加一个[OperationOutcome](operationoutcome.html)来表达.
如下是一个不满足服务器端业务规则时的返回信息:

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
`    "div": "<div xmlns=\"http://www.w3.org/1999/xhtml\">MRN冲突`
`   - the MRN 123456 is already assigned to a different patient</div>"`
`  },`
`}`
</pre>
</div>

Notes:

*   服务器可通过[OperationOutcome](operationoutcome.html)来表达更为详细的错误信息

### 1.9.1.7 Read Request

[读取资源内容](http.html#read)是通过HTTP GET请求来实现的. 

<div class="example">
<pre class="http linecounter">
`GET /Patient/347?_format=xml HTTP/1.1`
`Host: example.com`
`Accept: application/xml+fhir`
`Cache-Control: no-cache`
</pre>
</div>

Notes:

*   **347** (line 1) - 要访问资源的id
*   **_format=xml** (line 1) - 希望返回的数据格式，这种方式适合于客户端无法访问HTTP 头信息的情况，例如XSLT转换时，也可以通过HTTP 头中的accept字段来指定(see [Mime Types](http.html#mimetypes)
*   **cache control** (line 4) - 如何控制并发是很重要的，但FHIR中并未做出规定,更多信息请参考[http://www.w3.org/Protocols/rfc2616/rfc2616-sec13.html](http://www.w3.org/Protocols/rfc2616/rfc2616-sec13.html) 或者 [https://www.mnot.net/cache_docs/](https://www.mnot.net/cache_docs/)

### 1.9.1.8 Read Response

读取单个资源内容GET请求的响应是单独的一个资源. 

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

*   **id** (line 8) - 资源的id，与请求中的id一致 
*   **versionId** (line 11) - 该资源的最新版本. 最佳实践中要求该值与 ETag值匹配 (see [version aware update](http.html#update)), 对于客户端而言，不能认为二者总是匹配的.  一部分服务器并不记录资源的版本信息。
*   尽管建议服务器能够保留版本信息，但不做强制性要求
*   **lastUpdated** (line 12) - 如果存在该字段，字段值应与HTTP header中的值保持一致

### 1.9.1.9 Search Request

除了读取单个资源内容之外，也可以通过[查询参数和变量](search.html) [查询资源内容](http.html#search)，形式一般如下:

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

会返回该患者的所有处方信息.

### 1.9.1.10 Search Response

查询请求返回的对象是一个[bundle](extras.html#bundle): 如未明确要求，只返回满足查询参数要求的资源元数据:

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
*   **id** (line 3) -服务器为该次查询响应bundle的唯一标识. 有些情况下要求该id满足 [ 全球唯一](extras.html#bundle-unique)
*   **meta.lastUpdated** (line 10) - This should match the HTTP header, and should be the date the search was executed, or more recent, depending on how the [server handles ongoing updates](search.html#currency). The lastUpdated data SHALL be the same or more recent than the most recent resource in the results
*   **base** (line 12) - 返回的内容中所有[资源引用](references.html) 相对地址的根地址。
*   **total** (line 13) - 满足查询条件的记录数量. 这里的数量指的是总数，而非仅该bundle中所包含的数量，详情查看 [可以对结果进行分页查询](http.html#search)
*   **link** (line 14) - A set of named links that give related contexts to this bundle. Names defined in this specification: [first](http.html#search), [prev](http.html#search), [next](http.html#search), [last](http.html#search), [self](http.html#search)
*   **item** (line 23) - 用来表达满足查询条件的实际资源的元数据信息
*   如果加上include标签，可以强制要求服务器在返回结果中包含资源的内容，详情请参阅[return additional related resources](search.html#include)

### 1.9.1.11 Update Request

客户端用新版本的资源记录替换服务器中的老版本.

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

*   **resourceType** (line 1) - &quot;Patient&quot; URL请求中的资源类型必须与提交的数据中的资源类型保持一致 (line 9)
*   **resource id** (line 1, &quot;347&quot;) - URL中的资源id必须与提交的数据中id值保持一致(line 9)
*   **If-Match** (line 6) - 如果存在该字段，必须与资源内容中的meta.versionId值保持一致 (line 12), 服务器必须核实版本的完整性，如果不支持版本则返回412状态码
*   **meta.lastUpdated** (line 10) - This value is ignored, and will be updated by the server
*   **resource content** (line 14) - 这里省略了资源内容

### 1.9.1.12 Update Response

更新请求的响应包括了元数据、状态和OperationOutcome(可选):

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

所有资源都会包含的基础信息:

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

*   **resourceType** (line 2) - 每个资源都会资源类型的字段. XML的话也就是根节点
*   **id** (line 3) - 在资源新建之时分配后不再变化.只有在初次创建该资源时才没有该字段
*   **meta.versionId** (line 5) - 当资源内容(除了meta.security、meta.profile、meta.tag三个之外)发生变更时该值随之变化 
*   **meta.lastUpdated** (line 6) - 随versionId的变化而变化. 如果服务器不维护版本信息，则不用记录该字段
*   **meta.profile** (line 7) - 表示资源的内容是否遵循某个规范(比方说满足阿里健康的开放API的要求或者说满足卫计委共享文档中的要求). 更多信息请参考 [Extending and Restricting Resources](profiling.html#resources). 当规范、值集本身发生变动时可以更改该字段的值
*   **meta.security** (lines 8 - 11) - [安全类标签](securitylabels.html). 该标签将资源与某些安全策略、基础架构策略联系起来。该字段的值可随资源内容的变动而变动,或者随安全体系的控制。
*   **meta.tag** (lines 12 - 15) - [其他类型的标签](extras.html). 如需将资源与特定的工作流程关联起来可以使用此类标签.在解读资源内容时无需考虑此类标签的值 。对此类标签值的更新不会影响资源内容版本的变化 [updated](http.html#tags) (这里好像是说 可以不变更资源的版本就修改tag标签的值 还是说tag值的修改压根就不影响资源版本 其他的security和profile tag三个字段是否都适用呢？待考证)
*   **implicitRules** (lines 16) - 如何准确安全的处理资源内容而在发送接收双方达成的[协议](profiling.html#agreement). 由于使用了该字段就意味着其他系统要使用其中的数据可能会出现解读错误的情况，限制了数据的重复利用，故不推荐适用该字段
*   **language** (lines 17) -  [资源内容所采用的表达语言](narrative.html#language). 当前，资源内容中亦可包含其他语言的内容; 该字段表示的是资源的主要语言。


&copy; © HL7.org 2011+. FHIR DSTU (v0.5.0-5149) generated on Fri, Apr 3, 2015 14:36+1100\.  
  链接：[试行版是什么](http://hl7.org/implement/standards/fhir/dstu.html) |[版本更新情况](http://hl7.org/implement/standards/fhir/history.html) | [许可协议](http://hl7.org/implement/standards/fhir/license.html) |[提交变更建议](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemAdd&tracker_id=677)

