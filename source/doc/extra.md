title: extra
date: 2014-05-20 15:13:12
categories: doc
---		


## 标签、组合和逻辑类型Tags, Bundles, Compartments <span class="sectioncount">1.10.1<a name="1.10.1"> </a></span>

<a name="root"> </a>
<a name="tags"> </a>

### 标签Tags <span class="sectioncount">1.10.1.1<a name="1.10.1.1"> </a></span>

除了资源的基本内容和元数据之外，每个资源都会有0到多个"标签"。这些标签能够用来将操作信息与资源关联起来，包括定义在访问控制策略、工作流和其他场景中的安全标签，这些标签是资源的一部分 与资源一起进行交换。标签从未用来保存那些在解释资源内容时所需的信息。它们的作用仅限于寻找和控制对资源的访问。In addition to the basic contents of Resources, and their metadata, each resource can be labelled
with one or more &quot;Tags&quot;. These tags can be used to associate additional operational information 
with the Resources, including defining security labels used in access control policies, workflow
management, and other uses. Tags are attached to resources, and exchanged with their resource.
Tags are never used to keep information that needs to be understood when interpreting the content
of a resource; their function is limited to finding and controlling access to the resource.

每个标签都有2个属性：Each tag has two properties:

<table class="grid">
 <tr><td>URI : uri</td><td>定义标签含义的术语A term that defines the meaning of the tag</td></tr>
 <tr><td>Label : string</td><td>(可选的)在面向用户的终端应用程序中给标签一个人可读的标记(Optional) A human-readable label for the tag for use when displaying in end-user applications</td></tr>
</table>

URI可以引用某个医疗健康领域的词汇，包括在该标准中定义的一些 如 [基础安全标签集](security.htm#labels)，或者是那些在HL7 V2/V3 /CDA 或SNOMED-CT中定义的词汇。另外，URI可能是在本地实现中定义的某一种。对标签描述的文字引用通常优于符号引用，但并不是必须这样做。
</br>The URI may be a reference to a healthcare vocabulary, including ones defined in this specification,
such as the basic [security label set](security.htm#labels), or vocabularies such as 
those defined by HL7 (v2 and v3/CDA), LOINC, or SNOMED-CT. Alternatively, the URI may be one
defined by the implementation in the local context. Literal references that refer directly 
to a description of the tag (typically just an HTML page) are preferred over symbolic references 
but this is not required.

如果面向用户的应用程序能够为用户提供给任意资源贴上自己的文本标签的功能，通过在基础URL后面添上MIME编码的标签，&quot;http://hl7.org/fhir/tags/text/&quot;. 应用程序就可以自动的构建URI。当处理资源的应用程序发现这样的URL，很自然地它们知道这只是一个纯文本的标签，不具任何含义。
</br>
If the end user application provides functionality to the user that allows the user to 
affix arbitrary text tags to the resource for their own purpose, the application can 
automatically construct a URI by appending the mime encoding of the Label to the base
URL &quot;http://hl7.org/fhir/tags/text/&quot;. When applications processing resources see this
base URL, they can automatically know that this is a pure text label with no formal
meaning.

<a name="compartments"> </a>
<a name="compartment"> </a>

### 逻辑类型Compartments <span class="sectioncount">1.10.1.2<a name="1.10.1.2"> </a></span>

每个资源可能属于一到多个逻辑compartments。一个compartment 也就是拥有共同属性的资源的一种逻辑分类。compartment有2种主要的角色：

</br>Each resource may belong to one or more logical compartments. A compartment is a logical 
grouping of resources which share a common property. Compartments have two principal roles:

*   提供快速查找一些相关联的资源的访问机制的功能Function as an access mechanism for finding a set of related resources quickly
*   为将访问控制快速应用到资源中提供定义的基础Provide a definitional basis for applying access control to resources quickly

Compartments定义了Compartment的实例如何定义和确定，系统如何知道资源是否归属于Compartments。如下是该标准中的一些Compartment列表：
</br>Compartments define how particular instances of the compartment are defined and identified,
and how systems know whether resources are in the compartment or not. Here is a list of 
the compartments defined by this specification:

<table class="grid">
 <tr><td>**名称Name**</td><td>**标题Title**</td><td>**描述Description**</td><td>**标识Identity**</td><td>**成员Membership**</td></tr>
 <tr><td>[patient](compartment-patient.htm)</td><td>Patient</td><td>与某个患者相关的资源集合The set of resources associated with a particular patient</td><td>每个患者资源有一个patient compartment的实例，compartment的标识与患者是一样的。当一个患者与另一个关联起来的时候，所有与被关联的患者相关的记录都归属于关联对象的compartment。There is an instance of the patient compartment for each patient resource, and the identity of the compartment is the same as the patient. When a patient is linked to another patient, all the records associated with the linked patient are in the compartment associated with the target of the link.</td><td>patient compartment包含了资源中对象是患者的任意资源和那些在患者compartment中直接关联起来的资源。The patient compartment includes any resources where the subject of 
the resource is the patient, and some other resources that are directly linked 
to resources in the patient compartment</td></tr>
</table>

compartment使用的例子：使用如下URL来获取病人病情的列表： 
</br>As an example of compartment usage, to retrieve a list of a patient's conditions, use the URL:

<pre>
  GET [baseurl]/patient/@[id]/condition
</pre>

更多详细信息参见 [查询操作](http.htm#search).

可能会像这样，很明确的使用compartment，也可能是隐式的。比如 如果FHIR服务器提供病人记录的视图，授权使用FHIR Restful API的用户可能会受限于访问那些从与之身份标识相关的compartment实例中的记录。
</br>Compartments may be used explicitly, like this, but can also be used implicitly. For instance,
if a FHIR server is providing a patient view of a record, the authorised user associated
with use of the FHIR RESTful api may be limited to accessing records from the
compartment instance(s) logically associated with their identity.

注意资源可能包含多种逻辑类型，或多种逻辑类型之间互相关联。如[诊断学报告](diagnosticreport.htm)中存在一个对象，但它所引用的 [观察](observation.htm)针对的是另一个对象，或者它所引用的[列表项](list.htm)针对的是多个不同对象。这样的一些交叉关联可能是由多种原因引起的，如：
</br>
Note that resources may cross between compartments, or interlink them. Examples of 
this would be where a [Diagnostic Report](diagnosticreport.htm) identifies  
a subject, but an [Observation](observation.htm) it references identifies
a different subject, or where a [List](list.htm) resource references
items that identify different subjects. Such cross-linking may arise for 
many valid reasons, including:

*   对象的记录是互相关联的-器官移植、产期护理、家庭治疗等等情况
*   工作列表中涉及多个病人/医务人员的工作流管理

*   Cases where subject records are inter-linked - Transplants, Perinatal care, family therapy etc.
*   Workflow management where action lists link multiple patients and/or practitioners

鉴于FHIR应用场景的多样性，逻辑分类中并没有定义如何来处理之间的相互关联。系统可能会拒绝资源，移除所有的逻辑分类，或将其置于其中，或者以其他方式来处理。
Given the wide variety of use cases and contexts in which FHIR is used, compartments 
do not define how cross-linking is handled. Systems may reject resources, remove them 
from both compartments, or place them in both, or act in some other fashion.

* * *

<a name="bundles"/> 
<a name="bundle"/> 

### 资源组合/Resource Bundles <span class="sectioncount">1.10.1.3<a name="1.10.1.3"> </a></span>

对资源的一个常见操作就是将多个资源整合成一个单独的实例。在FHIR中把这称之为资源的组合。资源组合并不只是对一些资源的引用，而是包含它们的整个内容。资源组合适用于多种情境，如：One common operation performed with resources is to gather a collection of resources into a single instance.
In FHIR this is referred to as &quot;bundling&quot; the resources together. The resource bundle is not just a list of 
references to resources, but includes their whole content. These resource bundles are useful for a variety of 
different reasons, including:

*   返回满足某个服务器操作一部分的某些条件的资源集合Returning a set of resources that meet some criteria as part of a server operation
*   返回作为某个服务器history操作一部分的资源版本集合Returning a set of versions of resources as part of the history operation on a server
*   存储资源集合Storing a collection of resources
*   消息事务中交换资源集合Exchanging a set of resources as part of a message transaction
*   得到一个自包含的资源集合作为交换和持久化的单位来满足临床上的完整性如临床文档Grouping a self-contained set of resources to act as an exchangeable and persistable group with clinical integrity (i.e. a clinical document)

从概念上讲，资源组合拥有一个url标识符、一个更新日期和 资源列表。对于列表中每个资源，包含了资源内容和上述的一些元数据。组合中的每条都包含了他们最初的标识符。也就是说读取资源组合的应用程序应该能够通过资源组合中的标识，在试图利用资源自身的url访问资源之前来查找资源(在将)Conceptually, a bundle has an identifier (url) and a date updated, and a list of resources. 
For each resource in the list, the bundle has the resource and also its metadata as listed above.
Each entry in the bundle retains its original identifier. This means that applications reading
the bundle should always look for a resource by its identity (after converting relative URLs
absolute URL) in the bundle first before trying to access it by its URL.

</div>
<div class="col-3"><div class="itoc">

On This Page:

[Resource Definitions](#root)

[Resource Content](#content)

[Bundles](#bundles)

[Conformance](#conformance)

[Resource References](#references)

[Contained Resources](#contained)

[Versioning](#version)