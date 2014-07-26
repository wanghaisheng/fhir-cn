title: 
date: 
categories: doc
---

[首页](../home/index.html) >[文档](documentation.html) >[资源定义](resources.html) >**扩展**       


#### 1.12.6.0  扩展

同时请参考扩展[示例](extensibility-examples.html).                     

该交换标准是以卫生保健领域普遍认可的通用需求为基础-涵盖多个地区,领域和不同的函数式方法.因此,对于某个特殊的实现而言,会存在一些标准中并没有覆盖的需求,如果将所有这些需求都融合到标准中将会导致标准非常冗长且难于实现.然而,该标准期望在实现中将此类区域性的额外需求视为扩展.            


因此,扩展是该标准设计中的基础部分,资源的每个元素都可能会有extension子元素,用以标识不属于资源基础定义的其他信息.应用程序不应只是因为资源中包含扩展而拒绝它们,尽管可能会由于扩展中的某些特殊内容而拒绝它们.              


需要注意的是,与其他标准不同的是,无论是机构还是地区定义或使用了这些扩展,在任何应用程序,项目或标准中,都不应该对扩展的使用感到困扰.正是由于对扩展的使用才使得对于每个人而言,FHIR标准能够保持它的简单性.                      


为了安全,易管理的使用扩展,对于扩展的定义和使用有严格的治理机制.尽管允许开发人员定义和使用扩展,在定义和使用扩展时也必须满足一系列的要求.           



#####  1.12.6.0.1 扩展的元素

资源或数据类型中的每个元素都有一个可选的可出现任意次数的 &quot;extension&quot; 子元素, &quot;extension&quot; 子元素在所有子元素中第一个出现,优先于其他所有子元素,每个资源中所出现的&quot;extension&quot; 的内容模型如下:                                            

<pre class="spec">&lt;<a title="Optional Extensions Element - found in all resources." class="dict" href="base-definitions.html#Extension"><b>[name]</b></a> xmlns=&quot;http://hl7.org/fhir&quot; url=&quot;<span style="color: navy">identifies the meaning of the extension</span> (<span style="color: darkgreen"><a href="datatypes.html#uri">uri</a></span>)&quot;&gt; <span style="float: right"><a title="Documentation for this format" href="formats.html"></a></span>
 &lt;!-- from Element: <a href="extensibility.html">extension</a> --&gt;
 &lt;<a title="Value of extension - may be a resource or one of a constrained set of the data types (see Extensibility in the spec for list)." class="dict" href="base-definitions.html#Extension.value_x_"><b>value[x]</b></a>&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown"><b>0..1</b></span> <span style="color: darkgreen"><a href="datatypes.html#open">*</a></span> <span style="color: navy">Value of extension</span><span style="color: Gray"> --&gt;</span>&lt;/value[x]&gt;
&lt;/[name]&gt;
</pre>                         

![](../material/extension-content.png)                        

其他定义: 资源规范 ([XML](Extension.profile.xml.html), [JSON](Extension.profile.json.html))                          

注意事项:               

*    url是一个强制性属性,是对定义了扩展内容和含义的[资源规范](profile.html)的标识                   
*   扩展的实际内容要么是value[x]元素,要么是包含其他扩展,每个扩展都有对应的定义它们的URL和各自的内容.                 
*   一个扩展应包含一个value元素或者子扩展.  value[x]元素应包含content和或id属性,id属性是Narrative叙述性文本中引用的目标.              
*   当某个扩展成为内部引用的目标,When an extension is the target of an internal reference, the reference is always to the value of the extension. An extension is only allowed to be the target of a reference when it has no value[x]
*   对于大多数扩展而言,处理资源内容的应用程序无视该扩展的内容应该是安全的.尤其是,对于扩展内容的理解不会改变包含它的元素的含义.更多讨论参考如下内容.                

value[x]元素中的[x]可以用如下的任意一种数据类型替换:

*   [integer](datatypes.html#integer)
*   [decimal](datatypes.html#decimal)
*   [dateTime](datatypes.html#dateTime)
*   [date](datatypes.html#date)
*   [instant](datatypes.html#instant)
*   [string](datatypes.html#string)
*   [uri](datatypes.html#uri)
*   [boolean](datatypes.html#boolean)
*   [code](datatypes.html#code) (only if the extension definition provides a [fixed](terminologies.html#code) binding to a suitable set of codes)
*   [base64Binary](datatypes.html#base64Binary)
*   [Coding](datatypes.html#Coding)
*   [CodeableConcept](datatypes.html#CodeableConcept)
*   [Attachment](datatypes.html#Attachment)
*   [Identifier](datatypes.html#Identifier)
*   [Quantity](datatypes.html#Quantity)
*   [Range](datatypes.html#Range)
*   [Period](datatypes.html#Period)
*   [Ratio](datatypes.html#Ratio)
*   [HumanName](datatypes.html#HumanName)
*   [Address](datatypes.html#Address)
*   [Contact](datatypes.html#Contact)
*   [Schedule](datatypes.html#Schedule)
*   [Resource](references.html#ResourceReference) - a reference to another resource

如果原始的扩展定义了复杂的内容,该扩展会包含其他子扩展,而不是用value来表达.   如果扩展的value本身需要扩展,这些扩展位于value[x]元素的内容当中.               

如下,name包含部落名称的扩展:              
<pre class="xml" fragment="HumanName">
&lt;name&gt;
  &lt;extension url=&quot;http://hl7.org/fhir/Profileiso-21090#name-use&quot; &gt;
    &lt;valueCode value=&quot;I&quot; /&gt;
  &lt;/extension&gt;
  &lt;text value=&quot;Chief Red Cloud&quot;/&gt;
&lt;/name&gt;
</pre>

 JSON格式:

<pre class="json">
&quot;name&quot; : {
  &quot;extension: [
    {
      &quot;url&quot; : &quot;http://hl7.org/fhir/Profileiso-21090#name-use&quot;,
      &quot;valueCode&quot; : &quot;I&quot;
     }]
  &quot;text&quot;: &quot;Chief Red Cloud&quot;/&gt;
}
</pre>

下面讨论如何正确的使用URL值 .          
对patient进行扩展,是否参加clinical trial的状态属性,其中又包含三个字段 : 状态,记录日期.记录人员status, date of recording, and person who recorded:                
<pre class="xml" fragment="Patient">
&lt;Patient&gt;
  &lt;extension url=&quot;http://acme.org/fhir/Profile/main#trial-status&quot; &gt;
    &lt;extension url=&quot;http://acme.org/fhir/Profile/main#trial-status-code&quot; &gt;    
      &lt;valueCode value=&quot;unsure&quot; /&gt;    
    &lt;/extension&gt;
    &lt;extension url=&quot;http://acme.org/fhir/Profile/main#trial-status-date&quot; &gt;    
      &lt;valueDate value=&quot;2009-03-14&quot; /&gt;    
    &lt;/extension&gt;
    &lt;extension url=&quot;http://acme.org/fhir/Profile/main#trial-status-who&quot; &gt;   
      &lt;valueResource&gt;   
        &lt;reference value=&quot;Practitioner/example&quot; /&gt;          
      &lt;/valueResource&gt;    
    &lt;/extension&gt;
  &lt;/extension&gt;
  &lt;!-- other data for patient --&gt;
&lt;/Patient&gt;
</pre>

JSON格式:

<pre class="json">
{
  &quot;resource-type&quot; : &quot;Patient&quot;,
  &quot;extension&quot; : [
    {
      &quot;url&quot; : &quot;http://acme.org/fhir/Profile/main#trial-status&quot;,
      &quot;extension&quot; : [
        {
          &quot;url&quot; : &quot;http://acme.org/fhir/Profile/main#trial-status-code&quot;,
          &quot;valueCode&quot; : &quot;unsure&quot;
        }, 
        {
          &quot;url&quot; : &quot;http://acme.org/fhir/Profile/main#trial-status-date&quot;,
          &quot;valueDate&quot; : &quot;2009-03-14&quot;
        }, 
        {
          &quot;url&quot; : &quot;http://acme.org/fhir/Profile/main#trial-status-who&quot;,
          &quot;valueResource&quot; : {
            &quot;reference&quot; : &quot;Practitioner/example&quot;
          }
        }
     ]
   }
  ], 
  ... other data for patient... 
}
</pre>


#####  1.12.6.0.2 扩展修饰符Modifier Extensions

有一些情况,扩展中的信息会修饰包含它的元素的含义.典型的,这也就是说信息能够否定或证明包含它的元素含义.例如:            
*   给 [Adverse Reaction](adversereaction.html)加一个确定性扩展,值为 &quot;highly doubtful&quot;            
*   给 [value set](valueset.html)中的某个概念新增一个包含关系                  
*   某个反对药物的人:记录一条不用药的指令                 
*   利用 [Condition](condition.html)资源记录断言:病人并没有某个诊断         
*   声明 医务人员并没有参与某个[Procedure](procedure.html)
*   记录并没有提供某个[Supply](supply.html)(i.e. 拒绝配药refusal to fill)

开发人员宜尽可能避免使用扩展修饰符/限定符.任何使用应谨慎考虑可能引发的后果.然而,由于资源使用的业务要求,开发人员常常不得不这么做,因此,该标准中提供了一个处理此类问题的框架.                    
 
如果出现了扩展限定符,除非应用程序知道扩展对于数据使用的用途,否则应用程序无法安全的处理它. 该标准中允许在资源的基础部分或没有数据类型的任意元素中包含修饰符元素(比如资源UML图中类对应的元素),元素名称为&quot;modifierExtension&quot;,内容与extension元素相同.                             

处理资源中数据的实现应该能够理解使用扩展时扩展所带来的影响.如果处理资源内容的应用程序无法识别modifierExtension,且应用程序要处理它所扩展元素的内容,应用程序应该要么拒绝处理数据,要么对数据相关的操作或者是从数据处理中所得到的结果输出发出警示,以告知使用者它并没有充分理解原始信息.             


Implementations are not required to &quot;support&quot; the extension in any meaningful way - they 
may achieve this understanding by rejecting instances that contain this extension. Alternatively,
implementations may be able to be sure, due to their implementation environment, that such extensions
will never occur. However applications SHOULD always check for extensions irrespective of this.

Note that processing the data of a resource typically means
copying or filtering data out of a resource for use in another 
context (display to a human, decision support, exchange in another 
format where not all information is included, or storing it for this kind of use).
Servers and background processes that simply move whole resources around unchanged 
are not &quot;processing the data of the resource&quot;, and therefore these applications 
are not required to check for unknown extensions. 

### <span class="sectioncount">1.12.6.0.2.1<a name="1.12.6.0.2.1"> </a></span> Summary: Conformance Rules for Modifier Extensions

*   A modifierExtension SHALL only modify the element which it contains and/or its children
*   It SHALL always be safe to show the narrative to humans; any modifier extension SHALL be represented in the narrative.
*   Applications SHALL always check for modifierExtensions when processing the data from any element that may carry one. If a modifierExtension they do not understand is found, the application SHALL either refuse to process the resource or affected element, or provide an appropriate warning to its users

### <span class="sectioncount">1.12.6.0.2.2<a name="1.12.6.0.2.2"> </a></span> Example

<div class="example">

Example: Because of a lack of clinical consensus, there's no element on [Procedure](procedure.html) 
for any expression of certainty around the expression of the Allergy/Intolerance. Some systems mark their entries 
as &quot;unlikely&quot; or &quot;probable&quot;. Applications are allowed to extend a resource with data like this: 

<pre class="xml">
&lt;AllergyIntolerance&gt;
  &lt;modifierExtension&gt;
    &lt;url value=&quot;http://example.org/fhir/extensions#certainty&quot; /&gt;
    &lt;valueCoding&gt;
      &lt;system value=&quot;http://example.org/codes/certainty&quot;/&gt;
      &lt;code value=&quot;2&quot;/&gt;
      &lt;display value=&quot;Unlikely&quot;/&gt;
    &lt;/valueCoding&gt;
  &lt;/modifierExtension&gt;
  &lt;!-- .. text etc... --&gt;
&lt;/AllergyIntolerance&gt;
</pre>
</div>

When an application understands this extension, it means that some developer
has provided appropriate instructions for what to do with the data contained 
in it. Note that there is no obligation that the application do anything at
all with the data - it can ignore it if that is safe in its own context,
though this would not usually be the case.

When an application that doesn't understand this extension tries
to process this resource, it is required to either refuse to process 
the resource (or containing element), or provide an appropriate warning to its users. Either
of these courses of action is potentially difficult. One option is to 
download the profile that defines the extension (from the given URL), 
find the name of the extension, and then use the name to display
the extension to the user. An error message could look something like
this:

![](modifier-extension-warning.png)

Note that the narrative of the resource SHALL contain this qualifying 
information, so it is safe to show this to the user as an expression 
of the resource's content. A warning dialog box could be extended to
offer the user the choice to see the original narrative. 

<div class="example">

Here is an example showing a statement that a particular surgeon did
not perform an operation:

<pre class="xml">
&lt;Procedure xmlns=&quot;http://hl7.org/fhir&quot;&gt;
  &lt;text&gt;
    &lt;status value=&quot;generated&quot;/&gt;
    &lt;div xmlns=&quot;http://www.w3.org/1999/xhtml&quot;&gt;Routine appendicectomy for Fred Smith performed By Susan Taylor. Note: This operation was not performed by Dr Lakin&lt;/div&gt;
  &lt;/text&gt;
  &lt;!-- ...data... --&gt;
  &lt;performer&gt;
    &lt;modifierExtension&gt;
      &lt;url value=&quot;http://example.org/fhir/extensions#didNotPerform&quot;/&gt;
      &lt;valueBoolean value=&quot;true&quot;/&gt;
    &lt;/modifierExtension&gt;
    &lt;person&gt;
      &lt;reference value=&quot;Practitioner/example&quot;/&gt;
      &lt;display value=&quot;Dr Lakin&quot;/&gt;
    &lt;/person&gt;
  &lt;/performer&gt;
  &lt;!-- ...data... --&gt;
&lt;/Procedure&gt;
</pre>
</div>

In this case, if an application is not reading the performers of the operation at all,
the fact that one of the performers has a modifierExtension is irrelevant and the 
application is free to ignore it. 

### <span class="sectioncount">1.12.6.0.2.3<a name="1.12.6.0.2.3"> </a></span> Special Case: Missing data

In some cases, implementers may find that they do not have appropriate data for an
element with minimum cardinality = 1. In this case, the element must be present, but 
unless the resource or a profile on it has made the actual value of the primitive 
data type mandatory, it is possible to provide an extension that explains why the 
primitive value is not present:

<pre class="xml">
&lt;uri&gt;
  &lt;extension url=&quot;http://hl7.org/fhir/Profile/general-extensions#data-absent-reason&quot;&gt;
    &lt;valueCode=&quot;unknown&quot;/&gt;
  &lt;/extension&gt;
&lt;/uri&gt;
</pre>

In this example, instead of a value, a [data missing code](general-extensions.html) is provided. Note that 
it is not required that this particular extension be used. This extension 
is **not** a modifier extension, because the primitive data type has no
value. 

It is not valid to create a fictional piece of data for the primitive value,
and then to add an extension indicating that the data has been constructed
to meet the data rules. This would be both a bad idea, and also a modifier
extension, which is not allowed on data types. 

<a name="exchange"> </a>

## <span class="sectioncount">1.12.6.0.3<a name="1.12.6.0.3"> </a></span> Exchanging Extensions

Extensions are a way of allowing local requirements to be reflected in a resource using
a common information based approach so that all systems can confidently process them 
using the same tools. However, when it comes to processing the information, applications
will be constrained in their ability to handle extensions by the degree to which they 
are informed about them. 

While the structured definition of an extension should always be available (see below for 
details), the mere availability of a definition does not automatically mean that applications
know how to handle them correctly - generally, human decisions are required to made around
how the data extensions contain should be handled, along with the implicit obligations 
that around the information. 

For this reason, local requirements that manifest as extensions are an obstacle to 
integration. The more the requirements are shared (i.e. regional or national scale),
the less impact they will have. The consistent representation, definition and registration of 
extensions that this specification defines cannot resolve that problem - it only provides a framework 
within which such local variations can be handled more easily. 

When it comes to deploying applications that support local requirements, situations
will very likely arise where different applications
exchanging information with each other are supporting different sets of extensions.
This specification makes some basic rules that are intended to make management
of these situations easier, but they cannot resolve them.

*   When exchanging resources, systems SHOULD retain unknown extensions when they are capable of doing so (just as they SHOULD retain core elements when they are capable of doing so)
*   If a system modifies a resource it SHOULD remove any extensions that it does not understand from themodified element and its descendants, because it cannot know whether the modifications it has mademight invalidate the value of the unknown extension
*   Systems that drop existing elements are considered to be &quot;processing the resource&quot;
*   A system SHALL not modify a resource or element that contains &quot;modifier&quot; extensions it doesn't understand
*   Applications SHOULD ignore extensions that they do not recognize if they are not &quot;modifier&quot; extensions
*   Systems that do not accept unknown extensions SHALL declare so in their Conformance resource instances

The degree to which a system can retain unknown extensions is a function of the type of system
it is: a general purpose FHIR server, or a middleware engine would be expected to retain 
all extensions, while an application that manages patient registration through a user 
interface can only retain extensions to the degree that the information in them is part of the
set managed by the user. Other applications will fall somewhere between these two extremes.

### <span class="sectioncount">1.12.6.0.3.1<a name="1.12.6.0.3.1"> </a></span> Summary: Handling extensions

Use the following rules as a guideline for handling resources:

*   When writing extensions, make sure they are defined and published
*   When reading, navigating through or searching on elements that can have modifier extensions, check whether there are any
*   When reading elements, ignore other extensions, unless you want to read a particular extension
*   Retain extensions whenever you can 

<a name="define"/>

## <span class="sectioncount">1.12.6.0.4<a name="1.12.6.0.4"> </a></span> Defining Extensions

Extensions may be defined by any project or jurisdiction, up to and including international standards organizations such as HL7 itself.  Extensions are defined and published
as part of a [Resource Profile](profile.html). Extensions are always defined against some particular context - the type of element 
that they may be used to extend. The following are possible contexts for an extension:

<table class="codes">
 <tr><th>Context type</th><th>Context format</th><th>Examples</th></tr>
 <tr><td>A particular element (including the root) in a single resource</td><td>The element path for that element</td><td>Profile.resource.element; Person</td></tr>
 <tr><td>A particular element (including the root) in a particular data type</td><td>The data type name for primitive types or the element path for complex data types</td><td>Address.part.value; string</td></tr>
 <tr><td>A particular context in one of the mapped reference models</td><td>The name of the reference model followed by the mapping path</td><td>RIM: Act[moodCode=&quot;EVN&quot;]</td></tr>
 <tr><td>Another extension</td><td>The profile uri of the extension followed by the extension code</td><td>http://myextensions.org#someExtension</td></tr>
 <tr><td>A set of some combination of the above</td><td>As above, separated by ';'</td><td>Address; Contact</td></tr>
</table>

In addition, an extension definition might apply additional constraints with
regards to particular element values of the target that make its use appropriate.
Extensions SHALL only be used on a target for which they are defined.

Each extension is defined using the following fields:

<table class="codes">
 <tr><td>Field</td><td>Required?</td><td>Path in Profile (from Profile.extensionDefn)</td><td>Description</td></tr>
 <tr><td>Code</td><td>Required</td><td>.code</td><td>The name that is used as a code in a resource to identify this extension - unique in the context of the defining profile</td></tr>
 <tr><td>Context</td><td>Required</td><td>.contextType and .context</td><td>The context of this extension. See above. The context has two parts: a type, and a path which supplies the details</td></tr>
 <tr><td>Short Definition</td><td>Required</td><td>.definition.short</td><td>A brief description of the extension used in the XML descriptions when the extension is referenced in a profile</td></tr>
 <tr><td>Definition</td><td>Required</td><td>.definition.formal</td><td>A formal statement of the meaning of the content of the field</td></tr>
 <tr><td>Requirements</td><td>Optional</td><td>.definition.requirements</td><td>Identifies the reason the extension is needed</td></tr>
 <tr><td>Comments</td><td>Optional</td><td>.definition.comments</td><td>Additional other information about the extension, including information such as use notes</td></tr>
 <tr><td>Cardinality</td><td>Required</td><td>.definition.min / .definition.max</td><td>The cardinality of this extension.
 Specifying a minimum cardinality of 1 means that if the source system declares that it conforms to an extension that declares a type including this extension, this extension must be included in the resource.  Cardinality can be constrained but not loosened in profiles that reference this extension</td></tr>
 <tr><td>Type</td><td>Required</td><td>.definition.type</td><td>The type(s) of the extension. This SHALL be a valid FHIR data type as described above, or empty, if the extension will contain other extensions</td></tr>
 <tr><td>XPaths</td><td>Optional</td><td>.definition.constraint</td><td>One or more XPath statements that SHALL evaluate to true when the extension is used</td></tr>
 <tr><td>Is Modifier</td><td>Required</td><td>.definition.isModifier</td><td>Whether the extension changes the meaning or interpretation of the element containing the extension (or any descendant of that element). Extensions defined as IsModifier=true are always represented in _modifierExtension_ elements, and extensions defined as IsModifier=false are always represented in _Extension_ elements</td></tr>
 <tr><td>RIM Mapping</td><td>Conditional</td><td>.definition.mapping...</td><td>The formal mapping from this extension to the RIM. Required for HL7-defined extensions that apply to resources with RIM mappings, but optional in other contexts</td></tr>
 <tr><td>v2 Mapping</td><td>Optional</td><td>.definition.mapping...</td><td>Mapping to a v2 segment/field/etc., if desired and appropriate. </td></tr>
 <tr><td>Binding</td><td>Conditional</td><td>.definition.binding</td><td>For the types CodeableConcept and Coding. See [Terminologies](terminologies.html)</td></tr>
</table>

Notes:

*   Mappings are not required to be computable (i.e. executable logic). Mappings to other specifications can also be provided.

Whenever resources containing extensions are exchanged, the definitions of the extensions SHALL be available to all the parties that share the resources.
Each extension contains a URI that references the source of the definitions as a Resource Profile. The source SHOULD be a literal reference, such as an
http: url that refers to an end-point that responds with the contents of the definitions - preferably a [FHIR RESTful server](http.html)
supporting the Resources Profile, or a logical reference (e.g. using a urn:) - for instance, to a national published
standard.

<a name="definition"> </a>

## <span class="sectioncount">1.12.6.0.5<a name="1.12.6.0.5"> </a></span> Control of extensions

As well as defining the base element structure for resources, HL7 also publishes extensions. HL7 publishes data definitions
as extensions rather than as part of the base resource structure in order to keep the base
resource structure simple and concise, and to allow implementers not to engage with an entire world's
worth of functionality up front. Note that HL7 does not define &quot;modifier&quot; extensions - if
HL7 publishes an element that modifies the meaning of other elements, it will be part of the resource
content itself, since everyone has to understand the extension anyway.

Before extensions can be used in instances, they SHALL be published. HL7 maintains two
extension registries and users are encouraged to register their extensions there. But
this is not required. All that is required is that the extension is published in a
context that is available for users of the extension. So, for example, if a particular
extension is used within a single institution, the definition of the extension
can be placed on the institution's intranet. However since, by their nature, resources
tend to travel well, it's always better to use the HL7 or other publicly accessible extension registries.

HL7 provides two extension registries. The first is for HL7 approved extensions. These
have been approved by an appropriate part of the HL7 community following a review process,
and have formal standing. The other registry is provided as a service to the community,
and anyone can register an extension on it.

<table class="codes">
 <tr><th>Registry</th><th>Search</th><th>Submit</th></tr>
 <tr><td>HL7 Approved</td><td>[TBD]</td><td>[TBD]</td></tr>
 <tr><td>Community</td><td>[TBD]</td><td>[TBD]</td></tr>
 <tr><td>Interim</td><td>[http://hl7connect.healthintersections.com.au/svc/fhir/profile/search](http://hl7connect.healthintersections.com.au/svc/fhir/profile/search)</td>
 <td>[http://hl7connect.healthintersections.com.au/svc/fhir/profile/upload](http://hl7connect.healthintersections.com.au/svc/fhir/profile/upload)</td></tr>
</table>

HL7 profiles defining extensions may be balloted alongside resource content as part of the FHIR specification or may
be published as part of separate specifications.
When HL7  publishes extensions as part of the FHIR specification, these extensions SHALL
be used for this data whenever the data is represented in instances. Applications SHOULD use other
HL7-defined extensions published to represent equivalent data in the interest of maximum interoperability.
If referencing a profile that defines extensions, implementations declaring conformance with the profile SHALL
use the profile-defined and imported extensions when conveying equivalent data elements.

To minimize complexity for implementers, HL7 will not elevate content defined in an HL7-approved extension to
be content defined in a core resource in future versions of the resource once that resource is normative.

In some cases, an HL7 work group or other body may publish a profile whose sole
purpose is to define extensions expected to be needed by implementers in a particular context.  E.g. extensions needed
to map a particular set of v2 segments or a v3 model.

Implementations are encouraged to share their extensions with HL7 and register them with the HL7 extension registry. The domain committees will work
to elevate the extensions into HL7 published extensions or, if adopted by a broad enough portion of the implementer community, the into the base resource structure itself.

  <!-- Todo: point to actual registry once it's up and running -->

To avoid interoperability issues, extensions SHALL NOT change their definition once published.  (Small clarifications to descriptions
that do not affect interoperability are permitted.)  Rather than modifying an existing extension, a new extension should be introduced.
Revisions to an extension may extend the set of contexts in which the extension apply but may not remove or constrain any context previously listed

  <!-- Todo: Figure out how to manage "deprecating" extensions and pointing at their new versions -->

</div>
<div class="col-3"><div class="itoc">

On This Page:

[Extensibility](#root)

[isModifier](#isModifier)

[Defining Extensions](#definition)

 &copy; HL7.org 2011 - 2014. FHIR DSTU (v0.2.1-2606)构建于2014  7月2号 16:29+0800 星期三 . 
链接：[试行版是什么](http://hl7.org/implement/standards/fhir/dstu.html) |[版本更新情况](http://hl7.org/implement/standards/fhir/history.html) | [许可协议](http://hl7.org/implement/standards/fhir/license.html) |[提交变更建议](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemAdd&tracker_id=677)      