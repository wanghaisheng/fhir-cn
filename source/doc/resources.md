title: 
date: 
categories: doc
---		

[首页](../home/index.htmll) >[文档](documentation.htmll) > **资源定义**
### 1.12.0 资源定义   
该标准中定义了一系列不同类型的资源，可以用来交换或存储数据，以此来解决很多卫生保健领域相关的问题，不论是行政管理上的还是临床上的．另外，该标准还定义了很多交换资源的不同方法．

一个资源，也就是一个实体　拥有如下特点：

*   拥有一个可寻址的标识　　
*   自身是该标准中所定义的某种资源类型　　
*   包含诸多在资源定义中所描述的结构化数据项　　
*   包含一种供人可读的对资源内容的XHTML的表达形式　
*   可能随着时间而发生变化　　

资源有多种表达形式。如果能满足上述条件，依据标准中定义的规则，不管是XML还是JSON ，我们都认为是一个有效的资源，也允许其他的表达形式 ，但该标准中并未描述。　　

##### 1.12.0.0.1 定义　　
<table class="grid"><tr> <td>资源</td> <td>存储或交换的数据实例</td> </tr><tr> <td>资源定义</td> <td>定义资源所包含的数据项</td> </tr> <tr> <td>规范</td> <td>本身可以关于某个应用场景的对数据项的额外描述，用一种特殊的资源[规范](../infra/profile.html)来表达．</td> </tr></table>   

####1.12.0.1 资源的内容   
所有资源都拥有如下数据项和属性，可能是可选的　也可能是强制存在的:

*   针对某个类型的一些定义好的基础数据元。　　
*   [Extensibility](extensibility.htm))——实现中会另外添加的一些数据元　　　
*   [人可读的资源内容的文本描述](narrative.htm#Narrative)　　
*   [内嵌资源](references.htm#contained) - 作为该资源标识和事务相关范围一部分的其他资源　　
*   [元数据](resources.html#metadata)——不是资源内容模型的一部分 但是是资源的一些重要信息。　
*   [标签](extras.html#tags)——可能用来定义 如安全性、工作流等额外动作的资源标签   
每个资源都是从公用数据项开始的(对于这种格式的相关文档，参考[资源定义格式](formats.html))     
<pre class="spec">&lt;<a title="A Resource Definition for FHIR" class="dict" href="#content"><b>[Name]</b></a> xmlns=&quot;http://hl7.org/fhir&quot;&gt;  
 &lt;<a title="See Extensions" class="dict" href="extensibility.html"><b>extension</b></a>&gt;<font color="Gray">&lt;!-- <font color="brown"><b>0..*</b></font> </font> <font color="darkgreen"><a href="extensibility.html">Extension</a></font>   <a href="extensibility.html"><font color="navy">See Extensions</font></a> <font color="Gray"> --&gt;</font>&lt;/extension&gt;
 &lt;<a title="See Extensions" class="dict" href="extensibility.html"><b>modifierExtension</b></a>&gt;<font color="Gray">&lt;!-- <font color="brown"><b>0..*</b></font> </font> <font color="darkgreen"><a href="extensibility.html">Extension</a></font>   <a href="extensibility.html"><font color="navy">See Extensions</font></a> <font color="Gray"> --&gt;</font>&lt;/modifierExtension&gt;
 &lt;<a title="The base human language of the resource content. The value can be any valid value following BCP 47" class="dict" href="base-definitions.html#Resource.language"><b>language</b></a> value=&quot;[<span style="color: darkgreen"><a href="datatypes.html#code">code</a></span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown"><b>0..1</b></span> <span style="color: navy">Human language of the content (BCP-47)</span><span style="color: Gray"> --&gt;</span>
 &lt;<a title="Text summary of resource content, for human interpretation" class="dict" href="narrative.html#Narrative"><b>text</b></a>&gt;<font color="Gray">&lt;!--</font> <font color="brown"><b>0..1</b></font> <font color="darkgreen"><a href="narrative.html#Narrative">Narrative</a></font> <font color="navy">Text summary of resource content, for human interpretation</font><font color="Gray"> --&gt;</font>&lt;/text&gt;
 &lt;<a title="See Contained Resources" class="dict" href="references.html#contained"><b>contained</b></a>&gt;<font color="Gray">&lt;!-- <font color="brown"><b>0..*</b></font> </font> <font color="darkgreen"><a href="references.html#contained">Resource</a></font>   <a href="references.html#contained"><font color="navy">Contained Resources</font></a> <font color="Gray"> --&gt;</font>&lt;/contained&gt;
 <font color="Gray">&lt;!-- Defined Data Elements for Resource --&gt;</font>
&lt;/[Name]&gt;
</pre>
<p>
<pre class="spec">
&lt;[**[Name]**](#content "A Resource Definition for FHIR") xmlns=&quot;http://hl7.org/fhir&quot;&gt;
 &lt;[**extension**](extensibility.htm "See Extensions")&gt;<font color="Gray">&lt;!-- <font color="brown">**0..***</font> </font> <font color="darkgreen">[Extensibility](extensibility.htm)</font>   [<font color="navy">参考扩展</font>](extensibility.htm) <font color="Gray"> --&gt;</font>&lt;/extension&gt;
 &lt;[**language**](base-definitions.htm#Resource.language "The base human language of the resource content. The value can be any valid value following BCP 47") value=&quot;[<span style="color: darkgreen">[code](datatypes.htm#code)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..1**</span> <span style="color: navy">内容所使用的语言文字 (BCP-47)</span><span style="color: Gray"> --&gt;</span>
 &lt;[**text**](narrative.htm#Narrative "Text summary of resource content, for human interpretation")&gt;<font color="Gray">&lt;!--</font> <font color="brown">**1..1**</font> <font color="darkgreen">[Narrative](narrative.htm#Narrative)</font> <font color="navy">资源内容的文字描述 用以人类对内容的解读Text summary of resource content, for human interpretation</font><font color="Gray"> --&gt;</font>&lt;/text&gt;
 &lt;[**contained**](references.htm#contained "See Contained Resources")&gt;<font color="Gray">&lt;!-- <font color="brown">**0..***</font> </font> <font color="darkgreen">[Resource](references.htm#contained)</font>   [<font color="navy">所包含的资源</font>](references.htm#contained) <font color="Gray"> --&gt;</font>&lt;/contained&gt;
 <font color="Gray">&lt;!-- 资源中定义的数据元Defined Data Elements for Resource --&gt;</font>
&lt;/[Name]&gt;
</pre>
```
这些元素的出现顺序必须是这样子的。为了保证schema和UML衍生的代码定义的一致性，首先要考虑到的是所有资源都共同拥有的这些元素。 
These elements must always appear in this order. These basic elements shared by all resources come first
in order to support consistent definitions for schema and UML derived code. 

可选的language元素规定了资源所使用的语言，使用[BCP 47中定义的编码](http://tools.ietf.org/html/bcp47)。注意：并非资源的全部内容都必须使用这种语言。如果规定了使用的语言，在[叙述性文本Narrative Text](narrative.htm#Narrative)中也应该规定。
The optional language element specifies the base language of the resource using the [codes defined in BCP 47](http://tools.ietf.org/html/bcp47).
Note that not all the content of the resource has to be in the language. 
If a language is specified, it should also be specified on the [Narrative Text](narrative.htm#Narrative).

language元素是用来支持索引和可及性的(如文本-语言中使用了language标签)当处理叙述性文本的时候，会用到叙述性文本中的html language标签。资源中的language标签是用来规定从资源中的数据中所得到的其他表达方式应使用的语言。
The language element is provided to support indexing and accessibility (e.g. text-to-speech use the language tag). 
The html language tag in the narrative is used when processing the narrative. The language tag on the resource is provided 
for use to specify the language of alternate presentations generated from the data in the resource

<a name="metadata"> </a>

## 资源的元数据Resource Metadata <span class="sectioncount">1.10.0.2<a name="1.10.0.2"> </a></span>

元数据是资源及其如何使用的重要特征。出于实现的考虑，它们在资源之外表达。The metadata properties are key aspects of the resource and how it behaves. For implementation reasons, these are represented outside the resource:

<table class="grid">
  <tr><th>元数据项Metadata Item</th><th>类型Type</th><th>用途Usage</th></tr>

  <tr><td>逻辑ID Logical Id</td> <td>[id](datatypes.htm#id)</td> <td>资源的标识。资源总是有一个标识，而且在资源的整个生命周期中都是固定不变的。资源标识的讨论见 [此](references.htm#Identification) 。The identity of the resource. 
    Resources always have a known identity and it is constant for the entire lifetime of the resource. Resource identification is [discussed elsewhere](references.htm#Identification)</td></tr>

  <tr><td>版本ID Version Id</td><td>[id](datatypes.htm#id)</td><td>每当资源内容发生改变时就改变。可在[resource reference](references.htm#Resource)中进行引用。用作保证每次更新都是基于最新的版本。版本号可以是全球唯一的，也可以是逻辑ID之下唯一的。鉴于在一个资源中版本ID必须是唯一的，它们常常是一个逻辑ID范围内的渐增ID 要么是UUID，尽管并未对这些方法作出要求。Changes each time the content of the resource changes. 
    Can be referenced in a [resource reference](references.htm#Resource). Can be used to ensure that updates are based on the latest version of the resource. 

The version can be globally unique, or scoped by the Logical Id. Since version ids must be unique within the scope of a single resource, they are generally either a serially incrementing id 
     scoped by the logical id, or a uuid, though neither of these approaches is required</td></tr>

  <tr><td>最后更新日期Last Modified Date</td><td>[instant](datatypes.htm#instant)</td><td>每当资源内容发生改变时间改变。某个系统或人可以用来判断资源内容是否为最新。Changes each time the content of the resource 
    changes. Can be used by a system or a human to judge the currency of the resource content.   </td></tr>

</table>

注意只要资源发生变化 版本id就会发生变化，最后更新日期也是。版本id对于管理并发问题和特殊版本引用问题是很有用的  是因为与之相关的日期时间固有的不准确性和精度限制。最后更新日期对于人确定资源中的信息是最新的而言是有用的。Note that the version id changes any time the resource changes, and so does the last modified date. The Version Id is more useful for managing
concurrency issues and version specific references because of the inherent uncertainties and precision limits associated with date times. The Last Modified Date 
is useful for a human to ascertain the logical currency of the information in the resource.

在任何使用资源的场景中，都需要解决如何表达这样的一些元数据的技术细节。更多信息请参考[实现细节Implementation 
Details](implementation.htm)，同时也包含了如何维护资源标识的讨论。In any environment where the resources are used, the technical details of how these metadata elements 
are represented will need to be resolved. For further details, see [Implementation 
Details](implementation.htm), which also contains a discussion of how resource identity is maintained.

资源的ID是大小写敏感的。ID通常都是难懂的，系统不需要也不应该尝试去确定它们的内部结构。不管ID是怎么表示的，在资源引用和URL总是要保持一致。ID可以是36位长的字符串，包含任意的ASCII字母、数字 &quot;-&quot; and &quot;.&quot;。Resource ids are case sensitive. Ids are always opaque, and systems need not and should not attempt to determine their internal structure. 
However the id is represented, it must always be represented in the same way in resource references and URLs. Ids can be up to 36 characters 
long, and contain any combination of ASCII letters, numerals, &quot;-&quot; and &quot;.&quot;.

* * *

<a name="conformance"> </a>

## 一致性Conformance <span class="sectioncount">1.10.0.3<a name="1.10.0.3"> </a></span>

资源内容和表达它们的格式必须遵循该标准中所描述的规则。由于其通用性和综合特征，该标准中的规则一般而言 与适用于某种特殊场景下的规则相比 是很松散的。该标准提供了一个一致性层 实现人员和国家/区域性项目可以用来以一种计算机可处理的方式来声明如何使用资源和交换模式来解决它们的应用场景。该一致性层是通过使用[Conformance](conformance.htm) and [Profile](profile.htm)资源来实现的。 The contents of the resource and the formats used to represent it must conform to the rules described in this specification.
Because of its general nature and wide applicability, the rules made in this specification are generally loose compared 
to the rules suitable for particular use cases. This specification provides a conformance layer that implementers and 
national/regional programs can use to provide a computable statement about how the resources and their exchange 
paradigms are used to solve particular use cases. This conformance layer is delivered through use of the 
[Conformance](conformance.htm) and [Profile](profile.htm) resources.

该标准也提供了大量的技术方面的资源 用以辅助对该标准的一致性的遵循。The specification also provides a number of technical resources that can assist with enforcing conformance 
to this base specification:

*   [Schema &amp; Schematron](fhir-all-xsd.zip)
*   [Validator Package](validation.zip)
*   [Reference Platforms](downloads.htm#refimpl) 

注意 所有这些都无法检测对该标准的所有一致性约束。
Note that none of these are able to check complete conformance to this specification.

资源中定义的数据元和数据类型有3个与一致性直接相关的属性：Cardinality, Is-Modifier, Must-Support。它们相互影响，给实现提出一致性的需求。
The data elements defined resources and data types have 3 properties that are 
directly related to conformance: Cardinality, Is-Modifier, Must-Support.
These interact to place conformance requirements on implementations. 

<a name="cardinality"> </a>

### 基数/Cardinality <span class="sectioncount">1.10.0.3.1<a name="1.10.0.3.1"> </a></span>

所有FHIR中定义的元素 在其定义中都有一个基数-最小出现次数和最大出现次数。该数字规定了在某个类型的资源实例中某个元素可能出现的次数。该标准中只定义了如下几种类型的基数： 0..1, 0..*, 1..1, and 1..*。描述特殊应用场景的规范profile可能在资源所定义的基数限制范围内使用其他的一些值。All elements defined in FHIR have a cardinality as part of their definition - a minimum number 
of required appearances, and a maximum number. This number specifies the number of times
the element may appear in any instance of the resource type. This specification
only defines the following cardinalities: 0..1, 0..*, 1..1, and 1..*. Profiles 
that describe specific use cases may use other values for cardinality within the limits 
of the cardinality defined by the resource. 

注意 如果出现 元素就不能为空-它们必须要么包含一个value属性 要么包含一个子元素或者是扩展。
Note that when present, elements cannot be empty - they must have either a value attribute, child elements, or extensions. 

该标准中鲜有元素的基数中最小出现次数为1.资源可以用在多种场景下，除了那些主要的应用场景， 有时候甚至连基本信息都是不完整的。出于这个原因，基数中最小出现次数为1的是包含在其中的对元素的理解很必要的那些元素。基数中的最小出现次数不应视作在使用资源的任意特殊场合应该出现的指南。In this specification, very few elements have a minimum cardinality of 1. 
Resources are used in many contexts, often quite removed from their primary
use case, and sometimes even basic information is sometimes very incomplete. For this reason,
the only elements that have a minimum cardinality of 1 are those where they
are necessary to any understanding of the element that contains them. 
The minimum cardinalities should not be taken as a guide to which elements
are expected to be present in any particular use of the resource.

对于那些基数>1的元素，它们出现的次序也许是有含义的。除非元素定义(在该标准或扩展)中明确定义了次序的含义，我们认为次序是无意义的，在实现中是允许重新对元素排序的。注意 在规范中profile 你是不能定义元素出现次序的含义的。当没有定义次序的含义时，在实现中 为了某种用途 需要从元素集合中选择一个元素时，必须依据所重复的元素内容的语义。规范和实现指南常常可对这个选择的过程作出约束。For elements that have cardinality &gt; 1, the order in which they appear may have meaning.
Unless the element definition (either in this specification or the extension) defines a meaning 
to the order explicitly, the meaning of the order is not defined, and implementations are allowed 
to reorder the elements. Note that you cannot define a meaning for the order of the elements in 
a profile. When there is no definition of the meaning of the order, implementations that need 
to choose a single element from a list of elements for some use must do so based on the semantics 
of the content of the elements that repeats. Profiles and Implementation guides may often make 
rules about this selection process.

<a name="mustUnderstand"> </a>
<a name="ismodifier"> </a>
<a name="isModifier"> </a>

### Is-modifier <span class="sectioncount">1.10.0.3.2<a name="1.10.0.3.2"> </a></span>

Is-Modifier是一个布尔型属性，当定义了一个元素 就给它分配一个，不管是作为该标准中基础资源的一部分还是规范中声明扩展的一部分。如果一个元素所包含的值会改变其他元素的解释 或者改变整个资源的解释时 我们就把它标记为&quot;Is-Modifier = true&quot;典型地，会有这样标记的元素有&quot;status&quot;, &quot;active&quot;, or &quot;certainty&quot;如果在[资源规范Resource Profile](profile.htm)中描述了元素用途，Is-Modifier的值则无法更改。一旦某个元素被标记成Is-Modifier，文档中就必须明确说明为什么它是一个修饰符，和/或该元素修饰的是那些元素。
Is-Modifier is a boolean property that is assigned when an element is defined, either as part of 
the base resource contents in this specification, or when profiles declare extensions. 
An element is labelled &quot;Is-Modifier = true&quot; if the value it contains may change the 
interpretation of other elements or the resource as a whole. Typical examples of 
elements that are labelled &quot;Is-Modifier&quot; are elements such as &quot;status&quot;, &quot;active&quot;, or &quot;certainty&quot;. 
The value of Is-Modifier cannot be changed when element usage is described in a 
[Resource Profile](profile.htm).
When an element is labelled as Is-Modifier, the documentation  must be clear about why 
it is a modifier, and/or which elements the element may modify.

一般而言，被标记成&quot;Is-Modifier = true&quot;的元素的基数的最小出现次数也是1 为的是在处理的时候引入确定性。如果在实例中这样一个元素的值是不明确的，或者不能从语境中得知，我们就不能安全准确地理解这个资源。无论基数的最小出现次数，在构建资源的实现中必须确保isModifier元素有恰当的值。isModifier元素必须在资源的叙述性的摘要中表示。
Generally, elements labelled &quot;Is-Modifier = true&quot; also have a minimum cardinality of 1, to introduce
certainty in their handling. If the value of such an element is not explicit in the instance, or known 
by the context, the resource cannot be safely understood. Irrespective of the minimum cardinality, 
implementations producing resources SHALL ensure that appropriate values for isModifier 
elements are provided. Is-Modifier elements SHALL be represented in the narrative summary 
of the resource.

处理资源的实现在它们处理资源的时候，应能够理解这些元素产生的影响。实现中不要求以任意方式支持这些元素-可以通过拒绝那些包含它们所支持的值之外的实例来达到这样的目的(比如，应用程序可能拒绝接收 reliability != "ok"的observation)。另外，根据它们的实现环境，实现可能要确保这样的值永远不会出现。然而 不论值是什么 ，应用程序总是宜核实它。Implementations processing resources SHALL understand the impact of the element when they process 
the resource. Implementations are not required to &quot;support&quot; the elem1ent in any meaningful way - they 
may achieve this by rejecting instances that contain values outside those they support (for instance,
an application may refuse to accept observations with a reliability != &quot;ok&quot;). Alternatively,
implementations may be able to be sure, due to their implementation environment, that such values 
will never occur. However applications SHOULD always check the value irrespective of this.

服务器和移动资源的后台处理过程并不是在处理资源中的数据，这些应用程序不必检测那些未知的扩展。任意为了在其他语境中使用资源而 从资源中复制数据的过程(展示为人，决策支持，另外一种不支持扩展的交换格式)则是对数据的处理。
Servers and background processes that move resources around are not &quot;processing the data
of the resource&quot;, and these applications are not required to check for unknown extensions. Any
process that copies data out of a resource for use in another context (display to a human,
decision support, exchange in another format that doesn't support extensions) is processing
the data.

<a name="mustSupport"> </a>

### Must-Support <span class="sectioncount">1.10.0.3.3<a name="1.10.0.3.3"> </a></span>

元素标记为Must-Support意味着使用或生产资源的实现中必须以某种有意义的方式提供对该元素的支持。究竟该怎么来理解 不是FHIR标准的一部分所能描述和阐述清楚的。Labelling an element Must-Support means that implementations that produce or consume resources must 
provide &quot;support&quot; for the element in some meaningful way. Exactly what this means is impossible
to describe or clarify as part of the FHIR specification.

鉴于此，标准中并未将任何元素标记成must-support。这在[Resource Profiles](profile.htm)中完成，其中将一些元素标记为mustSupport=true。当一个规范中这样规定了之后，由于这有多种解释，它也要具体明确应提供那些支持。For this reason, the specification itself never labels any elements as must-support. 
This is done in [Resource Profiles](profile.htm), where the profile 
labels an element as mustSupport=true. When a profile does this, it must also make clear
exactly what kind of &quot;support&quot; is required, as this can mean many things.

注意拥有IsModifier属性的元素并不是一个重要元素(如使用资源的重要元素之一)，也不是说它自动地就是mustSupport-然而对于除了IsModifier元素的其他元素而言 这两样的可能性更大。Note that an element that has the property IsModifier is not necessarily a &quot;key&quot; element (e.g. one of 
the important elements to make use of the resource), nor is it automatically mustSupport - however both 
of these things are more likely to be true for IsModifier elements than for other elements.

<a name="version"> </a>

## 版本间的兼容性/Inter-version Compatibility <span class="sectioncount">1.10.0.4<a name="1.10.0.4"> </a></span>

> 一旦标准完全变成正式标准 将适用如下规则。这些规则保证了实现中可能安全的处理资源内容，同时保证了使用不同版本的FHIR在应用程序间交换数据。然而，除了这里描述的局限性之外，在标准的试用期间，HL7会针对标准中发现的问题作出修改。应用程序在标准试用期间可能会用到 [资源标签resource tags](extras.htm#tags)来帮助管理。
> The following rules will apply once the specification becomes a full normative 
> specification. These rules ensure that implementations may process the content 
> of the resources safely while exchanging data between applications using different
> versions of FHIR. However during the period of trial use of the specification, HL7
> may make changes outside the limitations described here in response to discovered 
> issues in the specification. Applications may wish to use [resource tags](extras.htm#tags) to help
> manage this during the period of trial use.

资源内容中并不存在明确的版本标记。一旦成为正式版，该标准随后的版本可能会在资源内容任意部位引入新的元素和/或内容，但是已有数据元的路径和含义不会发生改变。任意值集或代码集都可能重新修订，囊括一些其他的值。There is no explicit version marker in the resource content. Once normative, subsequent versions of 
this specification may introduce new elements and/or content at any point in the 
resource contents, but the path and meaning of existing data elements will not be changed. Any value
set or code list may be revised to include additional cods

与一个值集或字典的绑定意味着 不论值集是自动增长的 或者在未来版本的标准中会对值集进行扩展，抑或是在以后的版本中值集永远不会发生变化。Each binding to a value set or code system indicates whether the value list automatically 
grows as new codes are defined, whether the list may be extended
in future versions of the specification, or whether the list cannot be changed at all in future versions.

一致性层([Conformance](conformance.htm) and [Profile](profile.htm))有声明FHIR标准版本的强制性属性，这些可能用作来确定实现中使用的是哪个版本的FHIR。
The conformance layer ([Conformance](conformance.htm) and [Profile](profile.htm))
have mandatory properties declaring the FHIR specification version, and these may be used to determine
which version of FHIR an implementation is using. 

在典型的场景中，可能是多个版本共存，因此应用程序宜忽略那些不认识的元素，除非它们是isModifier值为true的扩展。然而，在医疗领域中，很多应用程序供应商不乐意考虑这种方法，是因为考虑到存在的临床风险或它们软件技术上的局限性。并不要求应用程序一定要忽略未知元素，但必须使用一致性声明中的acceptUnkown元素来声明它们是不是这样来处理的。
In a typical scenario, mixed versions may need to exist, so applications SHOULD ignore elements 
that they do not recognize unless they are extensions with a isModifier element with value=&quot;true&quot;. 
However, in a healthcare context, many application vendors are unwilling to 
consider this approach because of concerns about clinical risk or 
technical limitations in their software (i.e. schema based processing). 
Applications are not required to ignore unknown elements, but must
declare whether they will do so in their conformance statements using the _acceptUnknown_ element.

其他有关版本间一致性问题的讨论可以在这里找到
[http://wiki.hl7.org/index.php?title=FHIR_interversion_compatibility](http://wiki.hl7.org/index.php?title=FHIR_interversion_compatibility "FHIR_interversion_compatibility").
 Additional discussion on interversioning issues can be found here: 
[http://wiki.hl7.org/index.php?title=FHIR_interversion_compatibility](http://wiki.hl7.org/index.php?title=FHIR_interversion_compatibility "FHIR_interversion_compatibility").

### 其他信息Further Information <span class="sectioncount">1.10.0.4.1<a name="1.10.0.4.1"> </a></span>

其他文档Additional documentation.

*   [资源定义/Resource Definitions](resources.htm)
*   [标签、组合、分隔符Tags, Bundles, Compartments](extras.htm)
*   [资源间的引用/References between Resources](references.htm)
*   [叙述性文本/Narratives](narrative.htm)
*   [格式：Formats:](formats.htm) [XML](xml.htm), [JSON](json.htm)*   [扩展Extensibility](extensibility.htm) ([Examples](extensibility-examples.htm))
*   [正规定义Formal Definitions](base-definitions.htm)

 &copy; HL7.org 2011 - 2014. FHIR DSTU (v0.2.1-2606)构建于2014  7月2号 16:29+0800 星期三 . 
链接：[试行版是什么](http://hl7.org/implement/standards/fhir/dstu.htmll) |[版本更新情况](http://hl7.org/implement/standards/fhir/history.htmll) | [许可协议](http://hl7.org/implement/standards/fhir/license.htmll) |[提交变更建议](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemAdd&tracker_id=677) 	 		