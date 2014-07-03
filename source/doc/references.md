title: references
date: 2014-05-20 15:13:12
categories: doc
---		


## 内部引用Internal References <span class="sectioncount">1.10.2<a name="1.10.2"> </a></span>

资源内部的元素间相互引用有4种情况There are 4 cases where elements inside a resource reference each other:

*   [在CodeableConcept数据类型内部来表示主要编码](datatypes.htm#CodeableConcept)</Inside a [CodeableConcept data type to identify the primary encoding](datatypes.htm#CodeableConcept)
*   叙述性文本中&lt;img src=&quot;&quot;/&gt; 的引用，引用资源中的一个图片。An &lt;img src=&quot;&quot;/&gt; reference in the narrative, referring to an image found in the resource
*   结构化数据元与叙述性文本中的数据元之间Between elements in the narrative and structured data elements
*   在ResourceReference和[contained resource](references.htm#contained)之间Between a ResourceReference and an [contained resource](references.htm#contained)

这些引用是使用id/idref的方式来实现的，表示源数据元和目标数据元的内容一样。目标数据元有一个&quot;id&quot;属性，它的值在整个资源中必须是唯一的。&quot;id&quot;属性没有命名空间。源数据元引用必须指向同一个资源的属性(或者是同一数据类型 如CodeableConcept)
These references are done using an id/idref based approach, where a source element indicates that it 
has the same content as the target element. The target element has an attribute &quot;id&quot; which must 
have a unique value within the resource with regard to any other id attributes. The &quot;id&quot; attribute is not in any namespace.
The source element reference must refer to an attribute in the same resource (or, for a CodeableConcept, inside the
same datatype). 

<div class="example">
<pre class="xml">
  &lt;example&gt;
    &lt;target id=&quot;a1&quot;&gt;
      &lt;child&gt;...&lt;/child&gt;
    &lt;/target&gt;
    &lt;-- other stuff --&gt;
    &lt;source idref=&quot;a1&quot;&gt;
  &lt;/example&gt;
</pre>
</div>

在一个单独的资源中，这和xml：id/idref原理一样，但不同之处在于：id引用的范围和唯一性只存在于包含他们的资源内部。如果多个资源被整合成一个XML，如[atom feed](xml.htm#atom)，资源间可能会存在重复值。这时候就要靠读取资源的应用程序来管理。In a single resource, this works like xml:id/idref, but there is an important difference: the 
uniqueness and resolution scope of these id references is within the resource that contains them. If multiple
resources are combined into a single piece of XML, such as an [atom feed](xml.htm#atom), duplicate 
values may occur between resources. This must be managed by applications reading the resources.

注意所有xhtml元素和数据元之间的引用要建立一种&quot;derived from&quot; 的关系，衍生出的内容(无论是text还是数据)都指向源内容。注意这意味着一些引用可能是向前引用(指向一些可能在以后才会在实例中定义的元素)
Note that all references between the xhtml elements and the data elements must be understood to 
establish a &quot;derived from&quot; relationship, where the derived content (whether text or data) refers 
to the source content.  Note that this means some references may be forward references (references to 
elements defined later in the instance).

<a name="ResourceReference"> </a>
<a name="Resource"> </a>
<a name="references"> </a>
<a name="Identification"> </a>

## 资源间的引用References between resources <span class="sectioncount">1.10.2<a name="1.10.2"> </a></span>

资源中定义的元素包含了很多对其他资源的引用。这些资源共同构成了医疗信息。The defined elements in a resource includes many references to other resources. 
The resources combine to build a web of information about healthcare. 

引用总是单向定义的——从源资源到目标资源。在逻辑上存在从目标资源到源资源的反向关系，但在资源中并没有明确的表示。浏览这些反向关系需要一些外部机制来记录资源间的关系。
References are always defined in one particular direction - from one resource (source) to another (target).
The corresponding reverse relationship from the target to the source exists in a logical sense, but is 
not represented explicitly in the resource. Navigating these reverse relationships requires some 
external infrastructure to track the relationship between resources.

由于资源是单独处理的，我们认为关系是不能够传递的。比如 [Condition](condition.htm)资源引用了一个[Patient](patient.htm)资源作为它的对象，作为病因，又与[Procedure](procedure.htm)资源关联起来，没有自动化的规则和明确方式说明手术的对象也是这个病人。反之，必须在procedure中确定对象。另外一种方式是声明对象的语境是不继承的，也没有顺延到与procedure的关系中。这种情况下唯一的另外就是contained resource。注意实际中，关系必须要描述一个合乎逻辑和条理分明的记录。
Because resources are processed independently, relationships are not considered to be transitive. 
For example, if a [Condition](condition.htm) resource references a particular 
[Patient](patient.htm) as its subject, and it links to a [Procedure](procedure.htm)
resource as its cause, there is no automatic rule or implication that the procedure 
has the same patient as its subject. Instead, the subject of the procedure must be established 
directly in the procedure itself. Another way to state this is that the context of the subject
is not &quot;inherited&quot; and it does not &quot;conduct&quot; along the relationship to procedure. 
The only exception to this in the case of contained resources (see below). Note that in
practice, the relationships do need to describe a logical and coherent record.

在资源中，引用是用类型type、引用reference和文字描述textdescription来表示的。引用最关键的属性是_reference_——资源是通过URL来标识和寻址的。实际的引用长得像如下：
In a resource, 
references are represented with a type, a reference, and a text description.
The key property of the reference is the _reference_ - resources are identified and addressed by their URL.
The actual reference looks like this (see [&quot;XML Format&quot;](formats.htm#syntax)
for details of the way resource contents are described):

<pre class="spec">
&lt;[**[name]**](references-definitions.htm#ResourceReference "A reference from one resource to another.") xmlns=&quot;http://hl7.org/fhir&quot;&gt;
 &lt;!-- from Element: [extension](extensibility.htm) --&gt;
 &lt;[**type**](references-definitions.htm#ResourceReference.type "The name of one of the resource types defined in this specification to identify the type of the resource being referenced.") value=&quot;[<span style="color: darkgreen">[code](datatypes.htm#code)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span title="Inv-1: Must have a type if a reference is provided" style="color: deeppink">**0..1**</span> <span style="color: navy">[Resource Type](resource-types.htm)</span><span style="color: Gray"> --&gt;</span>
 &lt;[**reference**](references-definitions.htm#ResourceReference.reference "A reference to a location at which the other resource is found. The reference may a relative reference, in which case it is relative to the service base URL, or an absolute URL that resolves to the location where the resource is found. The reference may be version specific or not. If the reference is not to a FHIR RESTful server, then it should be assumed to be version specific. Internal fragment references (start with ") value=&quot;[<span style="color: darkgreen">[string](datatypes.htm#string)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span title="Inv-1: Must have a type if a reference is provided" style="color: deeppink">**0..1**</span> <span style="color: navy">Relative, internal or absolute URL reference</span><span style="color: Gray"> --&gt;</span>
 &lt;[**display**](references-definitions.htm#ResourceReference.display "Plain text narrative that identifies the resource in addition to the resource reference.") value=&quot;[<span style="color: darkgreen">[string](datatypes.htm#string)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..1**</span> <span style="color: navy">Text alternative for the resource</span><span style="color: Gray"> --&gt;</span>
&lt;/[name]&gt;
</pre>

### 
术语绑定Terminology Bindings
 <span class="sectioncount">1.10.2.1<a name="1.10.2.1"> </a></span>

<table class="grid">
 <tr><th>Path</th><th>Definition</th><th>Type</th><th>Reference</th></tr>
 <tr><td title="ResourceType" valign="top">ResourceReference.type </td><td valign="top">One of the resource types defined as part of FHIR</td><td>[Incomplete](terminologies.htm#codeable)</td><td valign="top">[http://hl7.org/fhir/resource-types](resource-types.htm)</td> </tr>
</table>

&nbsp;

注意:

*   无论资源定义中元素的资源引用类型是否固定，_type_ 中都必须明确资源类型。The _type_ must specify the resource type, whether or not the type of the resource reference is fixed for the element in the resource definition
*   _reference_ 元素要么包含一个绝对的URL，要么是一个相对与 [服务基础URLService Base URL](http.htm#root)的相对URL，要么是一个内部片段引用。The _reference_ element contains a url that is either an absolute URL, or a relative URL that is relative to the [Service Base URL](http.htm#root), or an internal fragment reference (see below)
*   绝对URL提供了一种稳定可扩展的方式，适合与云/web环境，而相对/逻辑引用为封闭的系统边界间进行交互时提供了一种灵活方式。Using absolute URLs provides a stable scalable approach suitable for a cloud/web context, while using relative/logical references provides a   flexible approach suitable for use when trading across closed ecosystem boundaries. (see [implementation issues for further discussion](use.htm#identity))
*   尽管是首选方法，绝对URL却无需指向[FHIR RESTful server](http.htm)。如果url的后面满足&quot;/[type]/@[id]&quot; or &quot;/[type]/@[id]/history/@[id]&quot; 结构，应被视为引用是指向[FHIR RESTful server](http.htm).无论引用是否指向[FHIR RESTful server](http.htm)，引用必须指向某种资源。Absolute URLs do not need to point to a [FHIR RESTful server](http.htm), though this is the preferred approach. If the tail of the url   conforms to the structure &quot;/[type]/@[id]&quot; or &quot;/[type]/@[id]/history/@[id]&quot; then it should be assumed that the reference is to a [FHIR RESTful server](http.htm).   Whether or not the reference is to a FHIR RESTful server, the reference must point to a Resource as defined by this specification
*   URL综述大小写敏感的，首选小写字母。URLs are always considered to be case-sensitive and lowercase is preferred
*   一般而言，_display_ 和引用资源的Resource.text内容不一样，它的目的在于确定被引用的是什么，而非完整的描述它。The _display_ is generally not the same content as the Resource.text of the referenced resource.  The purpose is to   identify what's being referenced, not to more fully describe it

<div class="use">

**约束Constraints**

*   **Inv-1**: 如果reference存在，必须要有一个type。Must have a type if a reference is provided (xpath: <span style="font-family: Courier New, monospace">exists(f:type) or not(exists(f:reference))</span>)
*   **Inv-2**:如果资源以内置方式提供，必须包含一个本地引用。 Must have a local reference if the resource is provided inline (xpath: <span style="font-family: Courier New, monospace">not(starts-with(f:reference/@value, '#')) or exists(ancestor::a:content/f:*/f:contained/f:*[local-name(.)=current()/f:type/@value and @id=substring-after(current()/f:reference/@value, '#')]|/f:*/f:contained/f:*[local-name(.)=current()/f:type/@value and @id=substring-after(current()/f:reference/@value, '#')])</span>)

</div>

<div class="example">

在&quot;context&quot;元素中对某个FHIR Restful服务器上 [patient](patient.htm) &quot;034AB16&quot; 的相对引用：A relative reference to the [patient](patient.htm) &quot;034AB16&quot; in an element named &quot;context&quot; on a FHIR RESTful server:

<pre class="xml" fragment="ResourceReference">
  &lt;context&gt;
    &lt;type value=&quot;Patient&quot; /&gt;
    &lt;reference value=&quot;patient/@034AB16&quot; /&gt;
  &lt;/context&gt;
</pre>

在&quot;profile&quot;元素中对 [resource profile](profile.htm)的绝对引用：An absolute reference to a [resource profile](profile.htm) in an element named &quot;profile&quot;:

<pre class="xml" fragment="ResourceReference">
  &lt;profile&gt;
    &lt;type value=&quot;Profile&quot; /&gt;
    &lt;reference value=&quot;http://fhir.hl7.org/svc/profile/@c8973a22-2b5b-4e76-9c66-00639c99e61b&quot; /&gt;
  &lt;/profile&gt;
</pre>

_注意HL7还未创建一个profile注册库，也没有决定使用URL。Note that HL7 has not yet actually created a profile registry, nor decided on a URL for it_.

简单的display文本提供了人可读的信息：A short display text that provides a human readable identification of the resource may be provided:

<pre class="xml" fragment="ResourceReference">
  &lt;custodian&gt;
    &lt;type value=&quot;Organization&quot; /&gt;
    &lt;reference value=&quot;organization/@123&quot; /&gt;
    &lt;display value=&quot;HL7, Inc&quot; /&gt;
  &lt;/custodian&gt;
</pre>

当系统无法解析实际的资源时，可以使用该文本。This text can be used by a system that is unable to resolve the reference to an actual resource.

</div>

<a name="contained"> </a>

### 内嵌资源Contained Resources <span class="sectioncount">1.10.2.2<a name="1.10.2.2"> </a></span>

在某些情况下，资源引用中指向的内容不能脱离包含它的资源而独立存在，既不能单独的被标识，也不能拥有独立的事务范围。一般而言，这样的情况是由于源数据的二次用户组装该资源，如中间件引擎。如果知道当资源构建时未包含记录主键或绝对的标识信息，就不能将该资源组装起来，即使有一些任意标识与之关联，该资源永远不能脱离引用它的资源的语境而成为某事务的对象。In some circumstances, the content referred to in the resource reference does not have an independent 
existence apart from the resource that contains it - it cannot be identified independently, and nor 
can it have its own independent transaction scope. Typically, such circumstances arise where the resource
is being assembled by a secondary user of the source data, such as a middleware engine. If the data available
when the resource is constructed does not include record keys or absolute identification information, then
a properly identified resource cannot be assembled, and even if an arbitrary identification was associated
with it, the resource could never be the subject of a transaction outside the context of the resource that
refers to it.

在这些情况下，资源被置于引用的内部。In these circumstances, the resource is placed directly in line in the reference. **当内容能够正确标识时决不能这样子做，因为一旦丢失标识信息，想要恢复就极其困难。This should never be 
done when the content can be identified properly, as once identification is lost, it is extremely difficult 
(and context dependent) to restore it again.**

<div class="example">

内嵌资源的实例：An example of a contained resource:

<pre class="xml">   <!-- Can't fragment test this - too incomplete -->
 &lt;Document xmlns=&quot;http://hl7.org/fhir&quot;&gt;
  &lt;extension&gt;...&lt;/extension&gt;
  &lt;text&gt;...&lt;/text&gt;
  &lt;contained&gt;
    &lt;Organization id=&quot;org1&quot;&gt;
      &lt;!-- whatever information is available --&gt;
    &lt;/Organization&gt;
  &lt;/contained&gt;
  &lt;information&gt;
    &lt;!-- other attributes --&gt;
    &lt;custodian&gt;
      &lt;type value=&quot;Organization&quot; /&gt;
      &lt;reference value=&quot;#org1&quot; /&gt;
    &lt;/custodian&gt;
    &lt;!-- other attributes --&gt;
  &lt;information&gt;
 &lt;/Document&gt;
</pre>

The same example in JSON:

<pre class="json"> 
{ &quot;Document&quot; : {
  &quot;extension&quot; : { ... },
  &quot;text&quot; : { .. },
  &quot;contained: [
    {&quot;Organization&quot; : {
      &quot;_id&quot; : &quot;org1&quot;,
      .. whatever information is available ...
	}}
  ]
  &quot;information: {
    ... other attributes ...
    &quot;custodian&quot; : {
      &quot;type&quot; : { &quot;value&quot; : &quot;Organization&quot; },
      &quot;url&quot; : { &quot;value&quot; : &quot;#org1&quot; }
	}
    ... other attributes ...
  }
}}
</pre>
</div>

type and url是必须的，即使有时候略显重复，这是为了确保只能用一种方式来解决资源引用——分析URL，获取资源。The type and url are always required, even though somewhat redundant in this case, to ensure that a
single approach to resolving resource references can be used - simply by resolving the URL, and accessing
accordingly.

一些使用和解释内嵌资源的注意事项：Some notes about use and interpretation of contained resources:

*   内嵌资源和父资源共有同样的内部id分辨空间。Contained resources share the same internal id resolution space as the parent resource
*   内嵌资源不会包含其他内嵌资源。Contained resources do not contain additional contained resources
*   内嵌资源也继承了父资源的语境。比如，如果父资源包含一个&quot;subject&quot;,被内嵌的资源也包含一个subject元素，但是没有指明任何subject，处理程序可能推断出subject 是一样的。记住，这样的推断是针对某个特殊场景的。比如，没有规则说父资源和内嵌资源的subject的含义就是一样的。 Resources that are contained inline also &quot;inherit&quot; context from their parent resource. For instance, if    the parent resource contains a &quot;subject&quot;, and the contained resource also has a subject element defined,    but does not specify any subject, a processing application may infer that the subject is the same. Note,
    however, that such inferences are specific to a particular circumstance. There is no rule, for instance,	that the meaning of the &quot;subject&quot; element is the same in both parent and contained resources
*   内嵌资源不需要包含任何叙述性文本。Contained resources do not need to contain any narrative

<a name="atom-refs"> </a>

#### 解决资源引用Resolving references to Resources <span class="sectioncount">1.10.2.2.1<a name="1.10.2.2.1"> </a></span>

当碰到一个[resource reference](#Resource)，资源组合的读者总是要在atom feed中去查找资源。资源引用可能会包含资源类型，相对url，也就是目标的id，如下：Readers of the resources bundles should always look through the resources in the 
atom feed when a [resource reference](#Resource) is encountered. 
The resource reference may have the resource type and a relative url, 
which is the id of the target, like this:

<div class="example">
<pre class="xml" fragment="ResourceReference">
  &lt;institution&gt;
    &lt;type value=&quot;Organization&quot; /&gt;
    &lt;reference value=&quot;organization/@23&quot; /&gt;
  &lt;/institution&gt;
</pre>
</div>

读者要找到_institution_ 元素所确定的资源总是要先在atom feed中去查找一个个条目，而不是现在其他地方去找。如果如上的资源的feed.id包含链接http://example.org/,绝对URL就是http://example.org/organization/@23.如果feed中包含organization，则应如下所示： A reader trying to find the resource this _institution_ element identifies 
should always look through the entries in the atom feed prior to looking 
anywhere else for the institution. If the feed.id for the resource that contains
the link above is http://example.org/, then the absolute 
URL is http://example.org/organization/@23. If that organization is in the feed, 
it would look like this:

<div class="example">
<pre class="xml">
   .. feed ..
  &lt;entry&gt;
    .. 
    &lt;id&gt;http://example.org/organization/@23&lt;id&gt;
    .. 

    &lt;content type=&quot;text/xml&quot;&gt;
      &lt;Organization xmlns=&quot;http://hl7.org/fhir&quot;&gt;
         &lt;!-- Content for the resource --&gt;
      &lt;/Organization&gt;
    &lt;/content&gt;
  ... feed ...
</pre>
</div>

当然也可以通过相对url来定位资源。这时候， _id_元素包含对资源位置的直接引用：It would also be possible to locate the resource by an absolute url. In this case, 
the _id_ element contains a direct reference to the location of the resource:

<div class="example">
<pre class="xml" fragment="ResourceReference">
  &lt;institution&gt;
    &lt;type value=&quot;Organization&quot; /&gt;
    &lt;reference value=&quot;http://example.org/organization/@23&quot; /&gt;
  &lt;/institution&gt;
</pre>
</div>

如果在atom feed中找不到正确的URL对应的资源，应用程序可尝试直接访问该URL或者使用其他方法来搞定如何找到该资源。
If there is no resource in the atom feed with an appropriate URL, then 
the application may try accessing the provided URL directly or use some 
other implementation-specific method for resolving how to find the resource.