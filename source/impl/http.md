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
用于表示某个具体的FHIR API的实现。一般而言，id能够标识患者或者用户， the underlying information is completely compartmented by the logical identity associated with [xx]。这样的话，FHIR API 提供了一个患者/用户为中心的病历视图，授权/认证信息是显式的赋予URL的，由于这样的原因，某些可标识的用户是于逻辑标识相关联的
显式的将患者id放在URL中并不是必须的，系统实现时可以利用OAuth 登录将患者或医疗机构与某个FHIR endpoint联系起来。具体参考 [Compartments](extras.html#compartments) for the logical underpinning.


Identity

系统常常要通过比较2个URL来确定是否指向同一个URL。鉴于此，因遵循如下规则:

* URL中查询的部分应忽略，也就是?之后的内容
* The comparison of the document portion of the URL (i.e. not the server/port) is case sensitive
* http: and https: 是可以互换的，且指的是同一个对象
* 如果指定了端口，端口必须一致否则是不同对象，只有端口对于服务器来讲是有意义的情况下才应该显式的体现

比如: http://myserver,com/patient/1 和 https://myserver.com/patient/1 是一样的, 而 http://myserver.com:80/patient/1 和前面两个都不一样


Note: the identity comparison for protocols other than http/https is undefined.

#### 2.1.0.2 Resource Metadata and Versioning

每个资源都有一些[资源的元数据字段](resource.html#metadata). 这些字段与http 请求和响应的字段对应如下：

<table class="grid">
  <tr><th>Metadata Item</th><th>Where found in HTTP</th></tr>
  <tr><td>[Logical Id (.id)](resource.html#id)</td><td> Id显式的包含在URL里面 </td></tr>
  <tr><td>[Version Id (.meta.versionId)](resource.html#metadata)</td><td>Version Id可以用`ETag` header表示. Content-Location 中表示的是一个完整的URL (see [vread](#vread) below)</td></tr>
  <tr><td>Last modified (.meta.lastUpdated)</td><td>HTTP Last-Modified header</td></tr>
</table>

需要注意的是Version Id是弱&quot;weak&quot; ETag ， `ETag` headers
	的值是以 &quot;W/&quot; 为前缀的，值是用引号引起来的，比如:

<pre>
ETag: W/&quot;3141&quot;
</pre>

####  2.1.0.3  安全Security

HTTPS 的使用是可选项，但任何生产环境下的医疗数据的交换与共享都应该使用SSL和其他的安全措施。详情请参考 [HTTP Security](security.html#http)

至于说到底是返回403还是404取决于具体的情况和具体的本地策略、法规和法律。选择哪个错误码需要考虑相应的病历的公开是否是正当的PI信息的公开还是说是禁止的PI的公开。


注意: 为了支持基于浏览器的客户端系统，建议服务端实现 [cross-origin resource sharing](http://enable-cors.org/)

#### 2.1.0.4 HTTP Status Codes

该标准规定了特殊的HTTP status codes状态码的使用，状态码必须与某种状态相对应，只有不明确正确的状态码的时候，才可以使用其他合适的状态码，尤其是涉及授权认证和重定向的状态码
认证重定向不应该被当做资源本身位置的变更。

FHIR 中定义了[OperationOutcome resource](operationoutcome.html) 来表示某些具体的处理错误信息。对于某些交互/接口和某些状态码，必须在响应中返回
OperationOutcome。HTTP 4XX或5xx状态码可能会返回OperationOutcome，但不强制规定，通用的服务端框架可能会产生很多此类错误。

#### 2.1.0.5  管理响应中返回的内容

处于“带宽”的考虑，spec允许客户端规定返回哪些内容

##### 2.1.0.5.1 条件读取 conditional read

客户端可以在 `read` 请求中使用`If-Modified-Since`, 或 `If-None-Match` HTTP 头参数。如果这样的话，客户端必须接受状态码304表示未变更或完整的内容(要么是内容未变化，要么是不支持条件读取)作为响应。

服务器可以根据指定的`If-Modified-Since` date-time or the `If-None-Match` ETag 来返回304表示内容未发生变更，或者正常的 返回整个资源内容
。这种优化在出于缓存的目的而减少带宽时是有意义的，鼓励服务器这样做但不做强制性规定


##### 2.1.0.5.2 create/update/transaction

增、改、和批量操作是通过`POST`,`PUT` and `POST` 来实现的，对于服务器而言，要么只返回一个状态码，要么返回新增或更改之后的完整内容。对于批量操作而言
，要返回一个有`Bundle.entry.transactionResponse`字段的Bundle，而不是有`Bundle.entry.resource`字段的Bundle。

客户端可以用 [HTTP
return preference](https://tools.ietf.org/html/rfc7240#section-4.2)头参数来表示是否想要返回完整的资源内容:

<pre>
Prefer: return=minimal
Prefer: return=representation
</pre>

第一个指的是只要状态码. 第二个指的是要返回完整内容.服务器应该能支持该头参数。
如果不存在该头参数,服务器可根据实际情况自行处理。

<a name="mime-type"> </a>

#### 2.1.0.6   Content Types and encodings

FHIR 资源的正式MIME-type 是`application/xml+fhir` 或 `application/json+fhir`.
客户端和服务器必须使用的MIME-type是:

*   XML: **application/xml+fhir**
*   JSON: **application/json+fhir**

服务器必须支持 [HTTP specification 标准中section 12的服务端内容协商](http://www.w3.org/Protocols/rfc2616/rfc2616-sec12.html#sec12)
但为了支持不同的系统实现，服务器应该支持可选项`_format` 参数来规定响应的格式。`_format` 能够让客户端在客户端没法正确设置头参数的值时使用format参数覆盖头参数
的值。`_format` 参数的值可以是&quot;xml&quot;, &quot;text/xml&quot;, &quot;application/xml&quot;, 和 &quot;application/xml+fhir&quot; &quot;json&quot;, &quot;application/json&quot; and &quot;application/json+fhir&quot; 不管是哪个都应该能转换成正式的MIME-type。

HTTP 请求和响应的体都使用的是UTF-8.由于HTTP标准 (section 3.7.1)定义了默认的字符编码为ISO-8859-1, 请求和响应中应在`Content-Type`头参数中
使用`charset`参数明确的规定字符编码。请求中也可以在`Accept` header and/or use the `Accept-Charset` header中使用`charset`参数来规定字符编码

<a name="versioning"> </a>

#### 2.1.0.7  对版本的支持

支持FHIR的服务器应该提供对完整版本的支持，也就是说正确的给versionId赋值，记录versionId的变化，支持`vread`, 实现 [version aware updates](#versionaware).
对版本的支持能够让相关的系统记录正确版本的信息，保证病历中信息的完整性。然而，现在的大多数系统是不支持版本的，要这么做是很困难的。

鉴于此，允许服务器不支持版本:FHIR 并不强迫必须支持版本。客户端可以选择那些提供完整版本支持的服务器进行交互。系统在[conformance statement](conformance-definitions.html#Conformance.rest.resource.noVersion)中记录是否支持版本.

<a name="read"> </a>

#### 2.1.0.8 read

`read` interaction读取操作获取资源当前最新的资源内容。使用HTTP `GET` :

```
  GET [base]/[type]/[id] {?_format=[mime-type]}
```

该接口返回的是一个某种资源类型的实例。可通过浏览器访问该url.
[Logical Id](resource.html#id) (id) 值的介绍在 [id type](datatypes.html#id).
返回的资源内容中应该包含 `id`字段，且值是[id].
服务器应该返回`ETag` 头参数，值为 versionId、`Content-Location` 头参数，值为完整的url和`Last-Modified` 头参数.

注意: 在读取时未知的资源和已删除资源的处理是不一样的: 已删除资源返回的是410状态码，而未知的资源返回的是404。不记录已删除记录的系统
将已删除记录视为未知资源。

<a name="vread"> </a>

#### 2.1.0.9  vread

`vread`  interaction特定版本读取操作获取资源某个版本的资源内容。使用HTTP GET:

```
  GET [base]/[type]/[id]/_history/[vid] {?_format=[mime-type]}
```

该方法返回的是指定的资源类型的某个特定版本的资源实例。返回在资源内容必须包含`id` 字段，值为[id],包含`meta.versionId`头参数，值为[vid].
服务器应返回`ETag` 头参数，值为versionId ，返回`Content-Location` 头参数，值为包含版本的完整url，返回`Last-Modified` 头参数.

 [Version Id](resource.html#metadata) (vid)是版本标识符，和[Logical Id](resource.html#id)一样遵循 [format requirements](datatypes.html#id) 。可以通过history方法获取id，通过read方法返回的内容中的content location中的version id，或者
 来自某个内容模型的针对版本的某个引用。如果规定的这个版本正好是被删除的资源，服务器应该返回410的状态码.

即使服务器不支持读取既往版本的资源内容，也鼓励服务器支持针对某个版本的当前版本的资源内容的获取。如果请求中访问的是之前版本的资源，服务器不支持访问之前版本
，应该返回404 未找到的状态码，同时用operation outcome来解释当前资源类型不支持history操作.

<a name="update"> </a>

#### 2.1.0.10  update

`update` interaction 新增一个已有资源的最新版本或者创建一个对应id不存在资源的初始版本.使用HTTP `PUT`:
```
  PUT [base]/[type]/[id] {?_format=[mime-type]}
```
请求的体是一个 [Resource](resource.html) ，其中id字段的值与url中的[id]一致.
如果资源内容中包含了 [meta](resource.html#meta), 服务器应该忽略提交的资源中的`versionId` 和 `lastUpdated` 的值.
服务器必须给`meta.versionId` and `meta.lastUpdated`字段赋值.也允许服务器审查和更改其他metadata的值，但不推荐这样做(see [metadata description](resource.html#meta)  for further information).

当服务器接受了更新时，服务器应该接受提交的资源，后续读取时应该返回同样的内容。然而，系统可能会不支持，具体讨论请参考[transactional integrity](#transactional-integrity) for.

如果更新成功，如果是更新的话，服务器必须返回200状态码, 如果是新增的话，必须返回201状态码,
以及 `Last-Modified` 头参数, 和  `ETag` 头参数(包含新的资源`versionId`)
。服务器应该返回 `Content-Location` header，其中包含了更新操作得到的具体版本。如果是新增资源的话，服务器应该返回`Location` 头参数.

服务器响应的body可包含[OperationOutcome](operationoutcome.html)资源来表示资源内容处理中的hints和警告，其中不应包含任何错误信息.

##### 2.1.0.10.1  条件更新Conditional updates

条件更新能够让客户端根据某些标识条件而非逻辑标识[logical id](resource.html#meta)来更新现有的资源。使用 `PUT` :
```
  PUT [base]/[type]/?[search parameters]
```
当服务器处理条件更新时,先使用标准的[search facilities](search.html) 来查询特定的资源类型，力图找到一个单独的逻辑id。后续的处理动作取决于查询得到的结果数目:

*   **未找到匹配项**: 服务器完成新增操作[create](#create) operation
*   **找到一个匹配项**: 服务器对找到的资源进行更新操作
*   **找到多个匹配项**: 服务器返回412状态码，预设条件错误表示客户端的条件不够精确

这个方法/接口能够让无状态的客户端提交更新后的结果给服务器，无需担心服务器分配的逻辑标识。比如客户端将实验室结果的状态从&quot;preliminary&quot;更改为
&quot;final&quot;，可以使用`PUT /Observation?identifier=http://my-lab-system|123`提交更新后的结果。

##### 2.1.0.10.2 拒绝更新操作 Rejecting Updates

允许服务器依据完整性或其他业务考虑拒绝更新操作，视具体情况返回HTTP 状态码(大多数是422).

表达与FHIR有关错误的常用HTTP 状态码(除了与一般的安全、请求头参数以及content type协商问题相关的错误码之外)如下:

*   **400 错误的请求** - 无法解析资源内容或未通过FHIR 的校验规则
*   **404 未找到** - 不支持的资源类型，或者错误的FHIR endpoint节点
*   **405 不允许的方法** - 此更新操作之前资源内容不存在，服务器不允许客户端自定义id
*   **409/412** - 资源内容版本冲突
*   **422 无法处理的实体** - 提交的资源内容违反了FHIR 规范中或者服务器业务规则的要求。与此同时应返回[OperationOutcome](operationoutcome.html)
表示详细的错误信息

注意：在接受更新操作时，服务器可能会保留XML中的批注、指令，格式相关的内容，JSON中的空格，但不做强制要求。可能需要考虑这些内容对数字签名的影响。
对于其他系统该如何处理更新操作，请参考 [Create and Update Behavior](updates.html)

<a name="versionaware"> </a>
<a name="concurrency"> </a>

#### 2.1.0.11 资源内容的管理

[Lost Updates](http://www.w3.org/1999/04/Editing/)，当两个客户端同时更新同一个资源，第二个客户端的操作会覆盖第一个客户端的更新，但这
可以通过[ETag](http://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html#sec14.19) 和
[If-Match](http://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html#sec14.24) HTTP 头参数组合使用来避免.

为了能够支持此类用途，服务器在返回每一个资源内容时都应包括一个`ETag` 头参数。

```
HTTP 200 OK
Date: Sat, 09 Feb 2013 16:09:50 GMT
Last-Modified: Sat, 02 Feb 2013 12:02:47 GMT
ETag: W/&quot;23&quot;
Content-Type: application/json+fhir
```

如果HTTP 响应中包含了Etag参数，其值必须与资源的版本标识相一致。服务器可以按照自己的方式来生成资源的版本标识，只要能够满足[id](datatypes.html#id) data type,
且在统一资源的所有版本的寻址空间内保持唯一性即可。当资源内容以bundle的一部分返回的情况下，不会存在ETag，直接使用版本的vernsionId即可。

如果客户端想要发送一次针对版本的更新操作，只需要在请求的HTTP头参数中包含`If-Match`，其值引用服务器中返回的ETag的值即可:

```
PUT /Patient/347 HTTP/1.1
If-Match: W/&quot;23&quot;
```

如果版本标识与`If-Match`头参数中的不一致，服务器返回412 未满足预设条件的状态码，而非直接更新资源内容。

如果服务器要求客户端在请求中包含头参数`If-Match`，但实际请求中并没有包含头参数`If-Match`，服务器可返回412 未满足预设条件的状态码。

<a name="delete"> </a>

#### 2.1.0.12  delete

 `delete` interaction 移除已经存在的资源内容。该交互使用 HTTP DELETE 方法:

```
  DELETE [base]/[type]/[id]
```
delete交互意味着之后的对资源内容的[非指定版本的读取操作](#read)将会得到410 状态码，而且 [查询操作](#search)也再也找不到该资源。
删除成功之后或资源内容压根不存在，服务器应该返回状态码204(无内容)或者200 OK,同时包含[OperationOutcome](operationoutcome.html)
资源来表示删除操作的一些提示或提醒内容，如果包含了[OperationOutcome](operationoutcome.html)，其中不应该包含任何错误信息。

无论服务器支持删除操作与否，或是支持对某个资源类型或某个资源实例的删除操作与否，都取决于服务器具体使用场景下的自身的业务规则。
如果服务器拒绝删除某类资源，应返回状态码405 不允许使用的方法。如果由于一些针对某个具体资源的原因如参考完整性，服务器拒绝删除该资源，应返回状态码
409 冲突。对一个已经删除过的资源再次执行该操作不会产生任何效果，服务器应返回204或200状态码。已删除的资源可以通过后续的 [更新操作](#href)恢复。

很多资源中会包含status字段，会与删除的作用有一些重叠。每种资源类型都会定义删除操作具体的语义。如果没有提供额外的说明文档，删除操作应该视为删除资源的记录，
并非对资源所表示的现实世界中的资源状态有任何影响。

对于那些会维护版本记录的服务器而言，删除操作并不会移除资源的版本记录，从版本记录的角度而言，删除资源相当于新增一个版本记录，数据内容为空，且标记为已删除状态。


##### 2.1.0.12.1 条件删除 Conditional deletes

条件删除操作允许客户端根据一些标识条件而非资源id逻辑标识来删除已有资源。客户端发起如下的HTTP请求：
```
  DELETE [base]/[type]/?[search parameters]
```
服务器在处理此类删除时，首先利用提交的查询参数使用[查询机制](search.html)进行资源的查询. 后续的处理动作依赖于查询到的结果数量：

*   **无匹配项**: 服务器返回状态码404(未找到待删除资源)
*   **一个匹配项**: 服务器对匹配到的资源进行普通的删除操作
*   **多个匹配项**: 服务器返回状态码412，未满足预设条件，表示客户端提交的 查询条件不足以确定唯一的待删除资源

这个操作可以用在无状态的客户端(比如接口引擎)在不知道服务器分配的资源逻辑标识的情况下来删除服务器上的一个资源。比如，客户端要删除一个实验室检验结果，
可以使用请求 `DELETE /Observation?identifier=http://my-lab-system|123`.

<a name="create"> </a>

#### 2.1.0.13  create


新增/创建 交互/操作会在服务器分配的位置新增/创建一个新的资源 。如果客户端想要控制新提交资源的逻辑标识，应该使用[更新操作](#update)。
创建操作使用的是HTTP `POST`方法:

```
  POST [base]/[type] {?_format=[mime-type]}
```

HTTP 请求的体应该是一个不包括id字段的FHIR 资源(这里是否应该不做要求，由服务器直接覆盖即可)，
如果提交的数据中包含了[meta](resource.html#meta)字段,服务区应该忽略其中存在的 `versionId` and `lastUpdated` 的值.
服务器应该为`meta.versionId` and `meta.lastUpdated`字段分配新的值.允许服务器改变meta中的其他字段的值，但应避免此类操作 (更多信息请参考 [metadata description](resource.html#meta)).

在完成新增的时候，服务器应该接受所提交的资源，返回随后读取操作返回的一样的内容，但一些系统可能不支持这样，参考[transactional integrity](#transactional-integrity) for 中的讨论.

完成新增操作之后，服务器应返回状态码201，同时也应返回头参数`Location` ，其值中包含服务器为资源分配的[Logical Id](resource.html#metadata)
 和新增资源的[Version Id](resource.html#metadata):
```
  Location: [base]/[type]/[id]/_history/[vid]
```
其中[id] and [vid]为新增的资源的id逻辑标识和版本标识

服务器应返回`ETag` 头参数，值为版本标识 vernsionId和`Content-Location` 头参数，值为包括版本编号的完整url，以及`Last-Modified` 头参数

服务器可以返回[OperationOutcome](operationoutcome.html) 资源来包括有关资源内容的提示和提醒，但不能包括任何错误信息.

当资源的语法或数据不正确，或不能够用来创建新的资源，服务器应返回状态码400 错误请求。

如果是由于业务规则，服务器拒绝了资源内容，应返回状态码422 表示无法处理的实体。

不管是那种不成功的情况，服务器都应返回 [OperationOutcome](operationoutcome.html)资源来表示操作失败的详细错误信息.

与FHIR相关的常见HTTP 状态码(除了那些安全、头参数、content type协商相关的状态码之外)有：

*   **400 错误的请求** - 无法解析资源内容或资源内容不满足基本的FHIR校验条件
*   **404 未找到资源** - 不支持的资源类型或无效的FHIR 节点
*   **422 无法处理的实体** - 提交的资源内容违反了FHIR 规范或业务规则。同时应该有一个[OperationOutcome](operationoutcome.html)来提供详细的错误信息


注意：在接受更新操作时，服务器可能会保留XML中的批注、指令，格式相关的内容，JSON中的空格，但不做强制要求。可能需要考虑这些内容对数字签名的影响。
对于其他系统该如何处理更新操作，请参考 [Create and Update Behavior](updates.html)

##### 2.1.0.13.1 条件新增  Conditional create

条件新增操作使得客户端只有在一些等效的资源不存在与服务器上的时候才进行新增。在这种情况下，客户端通过在`If-None-Exist` 头参数中包含查询参数来定义
等效的含义：
```
  If-None-Exist: base/[type]?[search parameters]
```


服务器在处理此类新增时，首先利用提交的查询参数使用[查询机制](search.html)进行资源的查询. 后续的处理动作依赖于查询到的结果数量：

*   **无匹配项**: 服务器进行正常的新增操作
*   **一个匹配项**: 服务器无视提交的数据返回200状态码
*   **多个匹配项**: 服务器返回状态码412，未满足预设条件，表示客户端提交的 查询条件不足以确定唯一的待删除资源

该操作可以用来避免两个客户端对同样的记录新增两条重复的资源。比如客户端新增实验室检验结果时可以使用
`If-None-Exist: /Observation?identifier=http://my-lab-system|123` 来确保它不会重复新增一条记录

<a name="search"> </a>

#### 2.1.0.14 查询 search

该操作根据一些过滤条件来查询资源。使用不同的HTTP 方法.
```
  GET [base]/[type]{?[parameters]{&amp;_format=[mime-type]}}
```

通过查询参数中的条件来查询/搜索某种类型的所有资源
由于用户代理和代理处理`GET` and `POST`请求的方式，除了基于get的查询方法之外，支持_search 的服务器也应支持基于'POST'的查询:
```
POST  [base]/[type]/_search{?[parameters]{&amp;_format=[mime-type]}}
```

这种方法和 `GET` 方法的效果一样.所有查询交互都使用形如参数名称'='参数值的查询参数，要么是在URL 中，要么是`application/x-www-form-urlencoded`的body
(参考 [W3C HTML forms](http://www.w3.org/TR/REC-html40/interact/forms.html#form-content-type)).
查询的处理在[查询处理机制Search handling mechanism](search.html)中进行了说明.

如果查询失败，返回的状态码为4xx或5xx，同时有一个[OperationOutcome](operationoutcome.html)。
如果查询成功，返回的结果是一个[type](bundle-definitions.html#Bundle.type) = `searchset` 的[Bundle](extras.html#bundle) 资源，其中包含了满足查询条件的所有资源，按特定的顺序排序。返回的结果列表可能会很长，服务器可以使用分页机制。如果要使用分页机制，应该使用下面所描述的
[described below](#paging)
(adapted from [RFC 5005 (Feed Paging and Archiving](https://tools.ietf.org/html/rfc5005))来将较长的列表拆成不同的页里面
服务器也可以返回 OperationOutcome 资源来表达查询操作的其他一些额外信息，且不能包含任何错误信息，且[entry
mode](search-entry-mode.html) 值为`include`.

##### 2.1.0.14.1  其他形式的查询 Variant Searches

要查询一个[compartment](extras.html#compartments),不论是所有可能的资源还是某种类型的资源：

```
  GET [base]/[Compartment]/[id]/{*?[parameters]{&amp;_format=[mime-type]}}
  GET [base]/[Compartment]/[id]/[type]{?[parameters]{&amp;_format=[mime-type]}}
```
比如，要查询与某次encounter就诊相关的类型为某个LOINC编码的所有观察项：

```
  GET [base]/Encounter/23423445/Observation?code=2951-2  {&amp;_format=[mime-type]}
```
注意：特别的定义了一种操作来[获取患者的所有病历](patient-operations.html#everything)或
 [某次就诊的所有病历](encounter-operations.html#everything).

也可能一次性查询所有的资源:

```
  GET [base]?[parameters]{&amp;_format=[mime-type]}

```
在一次性查询所有资源时，只能使用那些所有资源都支持的查询参数

<a name="conformance"> </a>

#### 2.1.0.15  conformance

符合性声明操作获取服务器的符合性声明，也就是服务器支持那些资源和操作的定义。使用 HTTP OPTIONS 或`GET` 方法:

```
  GET [base]/metadata {?_format=[mime-type]}
  OPTIONS [base] {?_format=[mime-type]}
```

对于上述两种方法，服务器应该返回一个[符合性声明 Conformance Resource](conformance.html)资源来表达服务器支持那些资源和交互。
如果返回了状态码404，也就是说服务器不支持FHIR。由于一些客户端库不支持`OPTIONS` 才定义了`GET` 方法。
返回符合性声明资源时应该也返回`ETag` 参数，其值随着符合性声明资源内容本身的变化而变化。也可以返回`Content-Location`头参数，其值为当前版本的
符合性声明资源的完整URL。[OMG hData RESTful Transport](#hdata)规范中还定义了一些`OPTIONS`方法应返回的额外参数。

返回的符合性声明资源一般都会有一个逻辑标识，不会有meta字段，但也不做限制。

除了此符合性声明操作之外，服务器可以选择本节中所定义的获取、查询、更新和新增[Conformance Resource](conformance.html) 节点的操作.
与符合性声明操作的不同之处在于:

<table class="grid">
 <tr><td>符合性声明操作conformance operation</td><td>返回描述当前服务器功能的符合性声明</td></tr>
 <tr><td>符合性声明节点Conformance end point</td><td>管理符合性资源的注册库(e.g. the HL7 conformance statement registry)</td></tr>
</table>
要求所有服务器都支持符合性声明操作，但服务器可以选择是否支持符合性节点。

<a name="transaction"> </a>

#### 2.1.0.16 事务 transaction

事务交互 transaction interaction 在单个原子性的动作中提交多个需要服务器完成的动作。可以提交同样类型或不同类型的多个资源的多个操作，也可以是相互混合在一起的(
如获取、查询、新增、更新或删除等 read, search, create, update, delete, etc).

尤其是在需要多个交互，如果某个交互失败就可能存在无法保证参考完整性的风险的情况下，特别适用(比如，在存储Provenance资源和对应的目标资源时，或
对于文档仓库而言，文档索引和文档本身).

该操作是使用HTTP `POST` 方法的:

```
  POST [base] {?_format=[mime-type]}

```

Post所提交的内容是一个[Bundle](bundle.html)资源， bundle的类型为(Bundle.type字段值为)`transaction`.每个entry都包含了操作的具体信息，
可以告诉处理该事务(transaction)的服务器如何处理该entry。如果其中HTTP 操作为`PUT` or `POST`, entry中应该包含该操作所需要的资源内容。
就像一个个单独的资源一样，bundle中的资源是分别按照本章中或是 [Extended
Operations](operations.html)中介绍的操作/交互来处理的。包括 [meta element](resource.html#meta),
verification and version aware updates,
and [transactional integrity](#transactional-integrity)，每个资源都是.**The operations are subject to the the normal processing for each(待考证)**

服务器要么接受所有操作，返回状态码 200 OK和一个bundle；要么拒绝所有资源，返回状态码400 或500.如果提交的bundle中并不包含任何资源，这不应
视为错误。事务的处理结果不应依赖于bundle中资源的顺序。单个资源在transaction的bundle中只能出现一次。

**Bundle entry的处理**
由于事务是原子性的，所有操作要么都成功，要么都失败，且entry的顺序是没有影响的，处理该操作的顺序为:

1.  处理所有的`POST` 操作
2.  处理所有的`PUT` 操作
3.  处理所有的`DELETE` 操作
4.  处理所有的`GET` 操作

在上述的步骤1-3中，如果有任何资源标识重复了，事务就应该失败。

事务的bundle中的资源可能会存在相互引用，包括循环引用的情况。如果在上面的处理过程中，服务器为bundle的任一资源分配了新的id，服务器应该也同时更新bundle中对该资源的引用。
不是bundle中引用该资源的资源则先不管他。如果是针对版本的引用，在引用更新之后，应该仍然是针对版本的引用。不论是出现在资源id、资源引用，
url类型的字段、叙述性文本中的 &lt;a href=&quot;&quot; &amp; &lt;img src=&quot;&quot;，服务器都应该替换bundle中所有匹配的link.

<a name="transaction-response"> </a>

##### 2.1.0.16.1 事务响应 Transaction Response

为了让客户端知道entry处理的结果，确定服务器分配给资源的标识，服务器应返回一个
[type](bundle-definitions.html#Bundle.type) 类型为`transaction-response` 的[Bundle](extras.html#bundle)资源，按照提交时一样的顺序，其中包含了每一个entry和处理的结果。

每个entry字段应包含`transactionResponse` ，用来表示entry的具体处理结果——HTTP 状态码、location和'ETag'头参数(用来表示资源的id和版本)，
除此之外，entry也可能会包括资源本身.

<a name="other-bundles"> </a>

###### 2.1.0.16.2  接受其他类型的bundle Accepting Other bundle types

服务器可以选择支持除了类型是transaction之外的bundle作为事务。

类型为`history`的Bundle本身和类型是transaction的Bundle结构一样，服务器应该支持history bundle，这也从一个服务器复制数据到另一个服务器上就
会很容易。但在history list中无法表示已有的translation的边界，在history list中同一个资源可能会出现不止一次，服务器应该存在一些处理该问题的策略。

对于类型为其他的Bundle，服务器也可以选择支持，这些Bundle中不存在'transaction'字段 ，这时候，服务器处理entry时要么是新增要么是更新操作，
取决于服务器是否能够识别出资源的标识——如果资源的标识存在于服务器中，应该当做更新操作。注意：这样的话，客户端就把匹配过程转移给服务器。

<a name="history"> </a>

#### 2.1.0.17   history

history 交互 获取单个资源、某类资源所有实例或服务器上所有按的变更记录。此三类history交互 使用的是HTTP `GET` 方法

```
  GET [base]/[type]/[id]/_history{?[parameters]&amp;_format=[mime-type]}
  GET [base]/[type]/_history{?[parameters]&amp;_format=[mime-type]}
  GET [base]/_history{?[parameters]&amp;_format=[mime-type]}
```

返回的是[类型](bundle-definitions.html#Bundle.type)为`history` 的[Bundle](extras.html#bundle)包含了资源的版本变更记录，按时间先后顺序排列，
其中也包含了被删除资源。
每个entry都包含`transaction`元素,如果`entry.transaction.method` 值为`PUT` 或`POST`, a resource(这里需要在gforge上问一下  把句子补全).
entry应包含操作完成之后的资源状态。

[create](#create), [update](#update), 和 [delete](#delete)会产生资源变更记录的entry。其他操作则不会(此类操作可能会产生诸如AuditEvent的资源； these are represented as create operations in their own right)

history operation中的新增操作如下所示:

```
<entry>
  <resource>
    <Patient>
      <!-- the id of the created resource -->
      <id value="23424"/>
      <!-- snip -->
    </Patient>
  </resource>
  <transaction>
    <!-- POST: this was a create -->
    <method value="POST"/>
    <url value="Patient"/>
  </transaction>
</entry>
```

注意：条件新增、条件更新和条件删除都转换成对现有的历史版本资源列表中资源的直接更新和删除(. in a history list, there's never an instruction about creating an unidentified resource; it's transformed to a record of creating one that is identified 也就是说在history返回的资源历史版本列表中，
由于条件新增、条件更新和条件删除操作产生的版本都记录为更新或删除操作)。

除了\`_format`参数以外，history交互还包括如下参数:

<table class="list">
  <tr><td>_count : [integer](datatypes.html#integer)</td><td>single</td><td>请求中规定应返回的记录条数。不要求服务器必须返回指定的条数，但不能超过这个数字</td></tr>
  <tr><td>_since : [instant](datatypes.html#integer)</td><td>single</td><td>只返回该时间点及以后所创建的资源版本实例</td></tr>
</table>

使用带有时区的完整日期时间类型的`_since`参数可以限定只返回一段时间段内的历史版本资源列表，
对于客户端而言，由于时间精度的问题，可能会收到不止一次在边界时间点资源内容发生更新的通知。不强求服务器支持比秒更高的精度。

历史版本的资源列表可能会很长，服务器可以使用分页。要用到分页的话，必须使用下面章节所描述的方法来进行分页，使用`_count_`来限定每页中条目的数量。

history 交互可以用于一个系统对另一个系统的订阅，这样系统间的资源内容就可以保持同步。系统间同步的另一种方式请参考[Subscription resource](subscription.html).

<a name="transactional-integrity"> </a>

####  2.1.0.18  事务的完备性

在处理 [create](#create) and [update](#update)操作时，不要求服务器完全接受提交的资源；随后如果使用[read](#read)
操作获取资源时，所获取的资源与提交的资源可能是不一样的。不同之处可以是由于以下原因：

*   服务器把提交的内容与已存在的内容进行合并
*   服务器使用业务规则，改变了内容
*   服务器不支持资源的所有内容或允许值

注意，并没有通用的方法来安全或可预测地实现与现有内容的合并或根据业务规则来变更内容——what is possible,
safe and/or required is highly context dependent。这类操作可能受安全方面的因素所驱动。考虑到支持的不全面，客户端可以获取服务器的
基本的符合性声明来确定服务器不支持哪些特性或取值。


根据出于上面所述的三种理由对资源内容变更的程度，FHIR服务器给它所从属的生态系统所造成的后果是需要管理的。鉴于这样的原因，服务器宜尽可能少的对资源内容进行变更，。
但是由于医疗本身的多样性，FHIR 标准允许服务器在新增、更新时对资源内容进行变更。

类似的，系统实现时有些应用场景需要有一些合并内容、变更内容的特殊规则，这些应用场景的维护成本会很高。


尽管我们说这些规则是针对服务器的，对于客户端而言也有类似的概念——根据与服务器交互的不同客户端不支持同样特性/功能的程度，客户端/服务器被迫要实现一些
定制的业务逻辑以避免信息的丢失或受损。

通过遵循基于版本的更新模式，可以减少一些此类问题，在这种模式中：

*   服务器对于它所支持[update](#update)操作的资源都要支持[read](#read)操作
*   在更新之前，客户端先通过[reads](#read) 操作获取资源最新版本的内容
*   客户端根据自己的需要对自己内容进行变更，保持其他内容完整即可(note the [extension related rules](extensibility.html#exchange) around this)
*   客户端调用[update](#update) 操作,将变更后的内容提及给服务器，客户端要能够处理 409 412的http 响应

如果客户端遵循的是这种模式，对于不能够理解的那些来自其他系统的信息，通过更新操作就可以维护起来.

要注意服务器也可能选择维护那些可能会丢失的信息，但服务器没有明确的方法来确定客户端到底是因为不支持此类信息而省略了相应内容还是说客户端想要删除此类信息。


#####  2.1.0.18.1  Conformance

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
