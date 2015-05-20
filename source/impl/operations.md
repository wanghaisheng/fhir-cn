title:
date:  
categories: impl
---

  [首页](../home/index.html) > [实现](implementation.html) >**方法定义框架 operation**



###   2.2.0 扩展方法 Extended Operations on the RESTful API

RESTful API 中定义了某些资源类型的一些常见的交互/接口(增删改查)。这些交互/接口遵循 Restful范式，通过增删改查CRUD操作来管理资源的状态。尽管这些接口能解决大多数的问题，但仍然有一些特殊的功能
只有使用一种类似RPC的范式才能更加高效的解决，也就是我们所说的根据输入来进行输出的operation 方法。这部分介绍了轻量级的operation 框架来无缝的扩展原有的
RESTful API。

Operations 拥有如下的特性:

* 每个 Operation 都有名称
* 每个 Operation 都有入参和出参
* 入参出参中参数可以是资源、数据类型或查询参数
* Operation和 RESTful API 的安全相关的处理一致
* Operation 的URI节点是基于现有的 RESTful API的寻址方案的。
* Operation 可以利用现有的资源
* Operation 可以是针对某个资源，或是某种资源类型或者是整个服务器而言

#### 2.2.0.1 FHIR中定义好的 Operation FHIR defined Operations
FHIR标准中定义了一些 Operation:

|operation 名称| 节点|
| ----- | ------ |
| 资源内容的校验 | [base]/[Resource]/$validate | [base]/[Resource]/[id]/$validate |
| 获取资源的profiles, tags, and security 标签 | [base]/$meta | [base]/[Resource]/$meta | [base]/[Resource]/[id]/$meta |
| 给资源添加profiles, tags, and security 标签 | [base]/[Resource]/[id]/$meta-add |
| 删除资源的profiles, tags, and security 标签  | [base]/[Resource]/[id]/$meta-delete |
| 生成文档 | [base]/Composition/$document |
| 字典项的转换 | [base]/ConceptMap/$translate | [base]/ConceptMap/[id]/$translate |
| 批量转换字典 | [base]/ConceptMap/$batch |
| Closure Table Maintenance | [base]/$closure |
| 获取就诊记录 | [base]/Encounter/[id]/$everything |
| 获取患者的所有病历 | [base]/Patient/$everything | [base]/Patient/[id]/$everything |
| Populate Questionnaire | [base]/Questionnaire/$populate | [base]/Questionnaire/[id]/$populate |
| 生成调查问卷Build Questionnaire | [base]/StructureDefinition/$questionnaire | [base]/StructureDefinition/[id]/$questionnaire |
| 扩展值集内容Value Set Expansion | [base]/ValueSet/$expand | [base]/ValueSet/[id]/$expand |
| 字典项查询 | [base]/ValueSet/$lookup |
| 验证编码是否存在于某值集 | [base]/ValueSet/$validate-code | [base]/ValueSet/[id]/$validate-code |
| 批量验证 | [base]/ValueSet/$batch |

备注:

* 针对元数据的 operation 同样作用于既往的资源版本

#### 2.2.0.2 自定义方法 Implementations Defined Operations

除了上述的operation，系统开发实现时可以定义自己的operation方法。通过使用 conformance statement符合性声明来解决不同的系统中自定义的
operation 之间存在的命名冲突。

除此之外，这些 operation或额外的运行时operation并不会影响独立于或没有和 Restful API整合在一起的operation的使用，前提是它们的寻址方案不会
与这里的寻址方案发生冲突。

#### 2.2.0.3 operation方法的定义 Defining an Operation
每个Operation是通过如下内容来定义的:

* 该operation的语境/应用场景——使用的系统、资源类型或资源实例
* 该operation的名称
* 定义好的参数

要定义一个参数，需要如下信息:

* 参数名称，出于开发实现的考虑，名称应该是有效的字符串token
* 用途——入参 | 出参 |两者都是
* 参数类型——数据类型或资源类型
* Profile规范——表示资源中的额外约束的规范
* 文档——描述参数的使用

有一种叫“Tuple”的参数类型，其中会有一些额外的部分part。每个部分和参数拥有一样的信息
There is a special parameter type called "Tuple" which is a parameter type that has additional parts. Each part has the same information as a parameter, except for use, which is taken from the parameter it is part of.

The resource Operation Definition is used to provide a computable definition of the operation.

#### 2.2.0.4 operation的扩展 Extending an Operation

开发实现时可以通过定义新的参数来扩展operation。使用[Operation Definition](operationdefinition.html)可以自行发布你扩
展后的定义，其中 OperationDefinition.base指向原始的定义即可

注意：FHIR标准不会定义任何的以“x-”开头命名的参数。

#### 2.2.0.5 同步执行 operation方法 Executing an Operation Synchronously
大多数情况下，operation 方法是同步执行的——客户端发送入参请求给服务器，服务器返回出参给客户端。

operation节点的URL 取决于具体的使用场景：

* 系统层面：url形如[base]/$[name]
* 资源类型层面：url形如[base]/[type]/$[name]
* 资源实例层面：url形如[base]/[type]/[id]/$[name]

##### 2.2.0.5.1 Operation请求 Operation Request

一般情况下，通过POST来调用operation节点。提交内容的格式是Parameters资源格式，也就是一些入参。请参考值集扩展的请求范例。
其中Content type的使用和RESTful  API 一样。

如果operation没有复杂类型的入参，称该operation是幂等的，也就是说该operation可以使用GET方法来调用，所有参数附加在URL的后面，
以查询参数的形式出现，跟在?的后面。服务器应支持此类调用。

服务器也可支持multi-part form方法提交参数，对于测试使用HTML form的operation是很有帮助的。


##### 2.2.0.5.2 Operation 响应 Operation Response

如果Operation成功，HTTP 状态码应该是200 OK。如果是4xx或5xx的状态码则表示出错了，也可以返回OperationOutcome。
User agent应注意的是在收到客户端的operation请求时，服务器可能会要求客户端重定向来验证客户端。

一般情况下,当出参是一到多个的时候，响应中使用统一的Parameter资源格式。

如果出参只有一个，而且是一个资源的话，返回值的根元素为"return"，不会使用参数格式，响应中就只是资源内容本身

operation方法返回的资源可能会被保存下来，这样服务器中就可以查找该资源内容。这种情况下，返回的资源内容中会包括服务器分配的资源标识。如果响应中返回的
资源内容并没有持久化在服务器中，那么资源内容中就不会存在id字段

#### 2.2.0.6 异步执行Operation Executing an Operation Asynchronously
Operation也可以异步执行。这种情况下，请求端发送待执行的operation请求的消息，接收端随后返回operation的处理结果。

鉴于异步操作的复杂性，开发实现也会变得很复杂。异步operation的执行步骤总结如下:

* 请求端构建消息(a bundle with type = message)
* 消息头中的event.system 值为 http://blame-Lloyd.com/operations
* 消息头中的event.code为operation定义的URL
* 消息头的data字段指的是Parameters资源，其中的内容是operation的入参。如果没有入参的话，data字段也就不存在
* 接收端收到消息
* 待operation处理完成之后，处理端返回一到多条消息。
* 每条消息都是一个bundle，bundle.type = message，其中 MessageHeader.response.identifier的值为初始
请求中的id
* 如果operation处理失败，MessageHeader.response.code必须标明 失败信息，且应返回OperationOutcome资源
* 如果只有一个出参的话，而且是一个资源，根元素为"return"不会使用参数格式，MessageHeader.data中就只是资源内容本身
* 除了上面一条的其他情况下，MessageHeader.data里面是一个Parameters资源，包括的是operation的出参。如果没有出参，
MessageHeader.data应该不存在
