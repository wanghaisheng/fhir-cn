title: 
date:   
categories: doc
---		


[首页](../home/index.html) >[文档](documentation.html) >[资源定义](resources.html) > **标签、bunlde和Compartments**
#### 1.12.2.0  标签、bunlde和Compartments     

##### 1.12.2.0.1 标签  
除了资源的基本内容和元数据之外，每个资源都会有0到多个"标签"。这些标签能够用来将额外的操作信息与资源关联起来，包括确定bundle，工作流管理和声称遵循某个[规范](../infra/profile.html)的资源 . 标签是资源的一部分 与资源一起进行交换。标签从未用来保存那些在解释资源内容时所需的信息。它们的作用仅限于寻找资源、控制对资源的访问和将资源与技术上的/临床上的工作流程联系起来    

每个标签都有3个属性：   
 http://hl7.org/fhir/tag   
<table class="grid"> <tr><td>Scheme : uri</td><td>确定标签类型的uri</td></tr> <tr><td>Term : uri</td><td>定义标签含义的绝对地址uri</td></tr> <tr><td>Label : string</td><td>(可选的)在面向用户的终端应用程序中给标签一个供人可读的标记</td></tr></table>

定义了的tag scheme如下：    
<table class="grid"> <tr><td>http://hl7.org/fhir/tag</td><td>通用型标签</td></tr> <tr><td>http://hl7.org/fhir/tag/profile</td><td>规范型标签-表明该资源遵循这个规范 </td></tr> <tr><td>http://hl7.org/fhir/tag/security</td><td><a href="../impl/security.html#labels">安全型标签</a></td></tr></table>     

###### 1.12.2.0.1.1    通用型标签

在一个通用型标签中，Term可能是引用某个卫生保健词汇，包括该标准中定义的一些，也包括诸如像HL7 V2/V3/CDA LONIC SNOMED CT等术语。或者，term可能是由本地实现所定义的。直接指向标签描述的字面引用(尤其是HTML页面里)要比字符引用要好一些，但并不是必须这样做。
如果终端用户应用程序能够提供给用户根据自己的目的任意向资源添加文本标签的功能，应用程序能够通过给根URL&quot;http://hl7.org/fhir/tag/text/&quot;后加上URL编码的标签来自动构建一个term。当处理资源的应用程序发现这样的URL，很自然地它们知道这只是一个纯文本的标签，不具任何含义。   

**  已知的通用型标签 **  
下表总结了标准中已经定义了的这类标签：
<table class="grid"> <tr> <td><b>Term/术语</b></td> <td><b>语境</b></td> <td><b>描述</b></td></tr> <tr> <td>http://hl7.org/fhir/tag/document</td> <td>A bundle (feed.category)</td> <td>这个bundle <a href="../impl/documents.html">表示一份文档</a></td></tr> <tr> <td>http://hl7.org/fhir/tag/message</td> <td>A bundle (feed.category)</td> <td>这个bundle 表示<a href="../impl/messaging.html">一条消息</a></td></tr></table>


###### 1.12.2.0.1.2 规范型标签   
一个规范型标签标识一个资源遵循某个[规范](../infra/profile.html),也就是资源中允许出现什么内容的规则集合。 在一个规范型标签里面，term就是引用规范资源的URL。  

简单的通过对规范的测试就可以确定资源是否遵循某个规范([校验工具](../impl/downloads.html)提供了多种测试功能).然而，在一些情况下 要想简单的校验资源是否遵循一个规范是不现实的：
*   服务器检索资源集合，试图找到那些遵循某个规范的资源   
*   在校验资源时 有可个规范可供选择   
另外，校验根据需要客户端以一种方式告知它想根据哪个规范来校验资源。   

规范型标签可以用于多个应用场景——客户端/资源构建器可以给资源打上标签，表明其遵循某个规范。资源的服务器/接收方可以选择相信这个断言，亦或是定位规范来校验整个资源。  
注意：一个资源可以同时遵循多个规范。一个没有标签的资源可以遵循一个规范，当然，也可以谎称自己遵循某个规范。鉴于此，处理资源的应用程序在处理资源时，总是应该根据资源的内容，要么直接相信规范型标签，要么对其进行校验。规范型标签提供了一种找到资源所遵循规范的方法，而不是资源内容的声明。   
标签在该标准中其他部分的引用：    
*   Tags 用作 [安全型标签](../impl/security-labels.html)
*    [XML](xml.html#tags) 和 [JSON](json.html#tags)格式的Bundle/Feed
*  在 [HTTP interface](../impl/http.html#tags), 和 [tag operations](../impl/http.html#tag-ops), 和 the [Validation operation](../impl/http.html#validation)    
*   [通过标签寻找资源 ](../impl/search.html#tags)
*   规范中的声明 [Conformance Statements](../infra/conformance.html#tags)
*   [安全型标签](../impl/security.html#labels)

##### 1.12.2.0.2 Compartments 

每个资源可能属于一到多个逻辑compartments。一个compartment 也就是拥有共同属性的资源的一种逻辑分类。compartment有2种主要的作用：    
*   提供快速查找一些相关联的资源的获取机制的功能
*   为将访问控制快速应用到资源中提供定义的基础        

Compartments定义了中描述了Compartment的实例如何命名和确定，系统如何知道资源是否归属于Compartments。如下是该标准中的一些Compartment列表：

<table class="grid"> <tr><td>**名称**</td><td>**标题**</td><td>**描述**</td><td>**标识**</td><td>**成员**</td></tr> <tr><td>[patient](compartment-patient.htm)</td><td>Patient</td><td>与某个患者相关的资源集合</td><td>每个患者资源有一个patient compartment的实例，compartment的标识与患者是一样的。当一个患者与另一个关联起来的时候，所有与被关联的患者相关的记录都归属于关联对象的compartment.</td><td>patient compartment包含了所有资源中对象是某个患者的资源和那些在患者compartment中直接关联起来的资源</td></tr></table>

使用compartment的例子：使用如下URL来获取病人病情的列表： 
```
  GET [baseurl]/patient/@[id]/condition
```

更多详细信息参见 [查询操作](http.htm#search).作为一个检索相关的操作，分配给compartment的资源仅是哪些基于已经目前版本中涉及到的任意资源。
注意：内嵌资源不能用来单独形成一个病人compartment。   

可能会像这样，很明确的使用compartment，也可能是隐式的。比如 如果FHIR服务器提供病人记录的视图，获得授权的用户授权使用FHIR Restful API可能只能访问那些与之身份标识逻辑上相关联的compartment实例中的记录。 无论是显式还是隐式的使用compartment，服务器都需要做一些安排，保证客户端能够访问的病人资源没有直接关联到一些资源(比如用药)      
注意资源可能横跨多种逻辑类型，或多种逻辑类型之间互相关联。如[诊断学报告](../clin/diagnosticreport.html)中存在一个对象，但它所引用的 [观察](../clin/observation.html)针对的是另一个对象，或者它所引用的[列表项](../infra/list.html)针对的是多个不同对象。这样的一些交叉关联可能是由多种原因引起的，如：

*   对象的记录是互相关联的-器官移植、产期护理、家庭治疗等等情况
*   工作列表中涉及多个病人/医务人员的工作流管理


鉴于FHIR应用场景的多样性，compartment中并没有定义如何来处理之间的相互关联。系统可能会拒绝资源，从多个compartments中移除资源，，或将资源都置于每个compartments中，或者以其他方式来处理   

#####  1.12.2.0.3 Resource Bundles     
对资源的一个常见操作就是收集多个资源，将其整合成一个单独的实例，赋予一定的语境。在FHIR中把这称之为资源bundling。大多数情况下，资源Bundles并不只是对一些资源的引用和一些元数据，而是包含它们的整个内容。资源Bundles适用于多种情境，如：    
*   返回满足服务器某个操作某些条件的资源集合(参考[RESTFUL 查询](../impl/http.html#search))       
*   返回作为某个服务器history操作的资源版本集合 (参考[版本历史](../impl/http.html#history))      
*   消息事务中将资源及和作为消息的一部分来交换(参考[消息](../impl/messaging.html))   
*   得到一个自包含的资源集合作为交换和持久化的单位来满足临床上的完整性如临床文档(参考[文档](../impl/documents.html))    
*   存储资源集合  
bundled 资源的内容应该包括标识符(url)和更新日期，资源集合，每个资源都要有上述的一些元数据。同时，bundle和每个资源都要有一些有名称的链接，可能会有表示该bundle用途的额外的[标签](extras.html#tags) 
读取资源bundle的应用程序应该能够通过资源bundle中的标识，在通过[利用资源自身的url访问资源之前](references.html#atom-refs)，应该给总是通过标识先查找资源(在将相对URL转换为绝对URL之后).

在XML中，是用[atom feed](xml.html#atom)来标识bundle的 在JSON中，定义了一种[自定义格式](json.html#bundle)   

##### 1.12.2.0.4 Binary resources 二进制资源   
There are situations where it is useful or required to handle pure binary content using the same framework as other resources. Typically, this is when the binary content is referred to from other FHIR Resources. Using the same framework means that the existing servers, security arrangements, code libraries etc. can handle additional related content. Typically, Binary resources are used for handling content such as:   
*  CDA 文档如XDS
*  PDF文档
*  图像(优先使用Media资源来处理图片,如果内容已经是binary就不能这么做)

binary资源可以包含任意内容,文本\图片\pdf zip压缩包等等.在REST接口中,可以使用这些资源的原始格式,也可以用XML/JSON格式来标识,比如当把这些资源包含进一个bundle里面时(直接包含进feed要比引用来的方便)

参考文献:

*  [RESTful HTTP End-Point](../impl/http.html#binary)    
*  [XML Bundle Representation](xml.html#binary)      
*  [JSON Bundle Representation](json.html#binary)      
