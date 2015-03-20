title: 
date: 
categories: doc
---

  [首页](../home/index.html) >[文档](documentation.html) > **编码的使用**	
  
  
  *   [Content](terminologies.html)
  *   [ Named Systems List](terminologies-systems.html)
  *   [value sets](terminologies-valuesets.html)
  *   [V2 表格](terminologies-v2.html)
  *   [V3 命名空间](terminologies-v3.html)
  *   [Concept Map字典映射](terminologies-conceptmaps.html)  
  *   [术语服务](terminologies-service.html)
  
### 1.14.0 资源中编码的使用

<a name="bindings"> </a>

FHIR 资源中很多字段都是**可编码值**: 在别处所分配的表达特定“概念”的字符串. 定义字符串及其含义的地方有:

*   标准中所定义的固定值之一     
*   在某个RFC之中(如mime type, language)       
*   HL7中所定义的(V3的code system或V2的table表格)         
*   诸如[LOINC](http://loinc.org), [SNOMED CT](http://www.ihtsdo.org)等其他的外部术语
*   本地字典、应用程序中的枚举类型或供查找的表格

所有这些方式所定义的编码统称为“code system编码系统”。定义编码系统的方式多种多样，且规模和复杂度各异。

在该规范中，可编码值总是由 &quot;system&quot; and &quot;code&quot;组合而成,system中就是表示定义编码的编码系统的URL


FHIR中编码使用的框架是基于HL7第五部分中的基本框架[HL7 v3 Core Principles](http://www.hl7.org/documentcenter/public/standards/V3/core_principles/infrastructure/coreprinciples/v3modelcoreprinciples.html) document.

如果要在资源中使用编码，可以使用如下三种数据类型：

<table class="grid">
 <tr><td>[code](datatypes.html#code)</td><td>数据实例中只有编码，system是隐含信息，作为数据元素定义的一部分，在数据实例中并不体现. </td></tr>
 <tr><td>[Coding](datatypes.html#Coding)</td><td>同时拥有code和system两个字段的数据类型，system中描述了编码的定义从何而来</td></tr>
 <tr><td>[CodeableConcept](datatypes.html#CodeableConcept)</td><td>要么是由自由文本描述的概念，要么是一到多个Coding类型表示的概念</td></tr>
 <tr><td>[Quantity](datatypes.html#Quantity)</td><td>特例：system和code元素来表示所涉及到的单位的类型</td></tr>
</table>

备注：system字段值总是大小写敏感的。不同的编码系统中编码是否大小写敏感的规则是具体由编码系统所规定的。FHIR自己所定义的所有编码都是大小写敏感的。

####  1.14.0.1 对编码值应用的管理   

在上述三类数据类型的某个元素中可供使用的编码值我们称之为“value set”。只要是用到了这三种类型，标准中都会指定一个value set给某个特定的元素/字段。

code system和value set的区别常常被开发人员所忽视，是由于在系统设计阶段就忽视了这种重要的区别。比如，某个系统表中会混有一些来自LOINC的编码，也包含了一些自定义的编码。大多数情况下两类编码并无显著区别，only the fact that a code happens to look like a LOINC code betrays its origin. 。

在数据交换时，跟踪编码的来源是很重要的。为了达到这样的目的，每个编码系统都有一个URL，能够标识它自己，其中所有的编码事实上都是一个编码对，也就是编码加上一个命名空间。因此，在上面提到的混合式编码列表中，事实上存在两个编码系统：LOINC (http://loinc.org) 和自定义的 (假设URL为: http://example.com/codesystems/additional-test-codes)。混合而成的表格我们认为是一个单独的value set，囊括了来自上述两个命名空间的编码。该value set会有一个URL作为标识，比方说，是"http://example.com/fhir/ValueSet/test-codes)"，在实际的编码对中，或者数据实例中永远不会使用这个URL，这个命名空间。在FHIR 中，除了code数据类型(system是固定在schema之中，没有显式的表示出来)以外，其他的编码值都是用code和system两个字段表示的编码对。

按照上面的描述，FHIR中system元素值中的URL始终指向的是某个code system，而非value set。

当要把某个value set绑定到某个元素上时，这个绑定会存在如下属性：
<table class="grid">
 <tr><td>Name</td><td>该绑定相关的描述信息. </td></tr>
 <tr><td>Strength</td><td>如何理解绑定的程度</td></tr>
 <tr><td>Reference</td><td>定义该value set的URL。通常，它直接指向具体的ValueSet资源，也可以是间接地址</td></tr>
 <tr><td>Description</td><td>如何使用编码的文本描述。如果没有reference的话，必须给该项复制。如果有reference的话，该项可以用来记录一些该value set使用和实施过程中的特殊说明</td></tr>
</table>

在FHIR 的数据类型中，绑定是通过[ElementDefinition,binding](elementdefinition-definitions.html#ElementDefinition.binding)来表示的。


<a name="simple"> </a>
<a name="code"> </a>

####  1.22.0.2 绑定的强度 

几乎所有的可编码数据类型的元素都回绑定一个value set。绑定的灵活程度有如下几种：
	<table class="grid">
	 <tr><td>required</td><td>要满足这种，该元素的值必须从特定的value set中选取其中一个编码</td></tr>
	 <tr><td>extensible</td><td>要满足这种，如果value set中的某个编码能够表达某个概念，该元素的值必须从value set中取值，不然的话，可以使用额外的编码(数据类型或文本).</td></tr>
	 <tr><td>preferred</td><td>出于互操作性的目的鼓励该元素的值从规定的编码中取值，但不强制要求</td></tr>
	 <tr><td>example</td><td>value set中的值仅仅是对要表达的概念的示范。无需从该value set中取值</td></tr>
	</table>

在使用[StructureDefinition](structuredefinition.html)进行本地化的时候，可以给某个元素指定更为具体的value set(这个value set必须是原来的value set的子集)来限制其范围，可以强化绑定的强度。具体的规则参考下面。一般而言，由不同的地区、项目或者供应商来共同确定选择合适的value set. 

<a name="required"> </a>
<a name="simple"> </a>
<a name="code"> </a>

####  1.22.0.2.1  Required

要满足这种，该元素的值必须从特定的value set中选取其中一个编码。

这种情况适用于那些元素的值需要严格管控的情况，大家都能够对其的理解形成一致。一般而言，适用于数据类型为[code](datatypes.html#code)的元素/字段: 

*   元素所绑定的value set中所包含的编码是来自某一个编码系统的一些编码(如果需要的话 可以规定编码系统的版本) 
*   元素所绑定的是外部标准所定义的允许编码的列表(例如[Mime Types](http://www.rfc-editor.org/bcp/bcp13.txt),
[Language Codes](http://tools.ietf.org/html/bcp47), [UCUM](http://unitsofmeasure.org), etc.) 

其他可能的应用场景有：在[对资源进行规范时profiling resources](profiling.html),会对特定场景下只能使用某些编码达成一致。这时候，数据类型必须包含该值集中的某个编码。如果数据类型恰恰是[CodeableConcept](datatypes.html#CodeableConcept), 其中某个coding的值必须取自规定的值集。也可以提供text字段，也推荐这样来做，但是text字段不能替代必须存在的编码。


注意：当数据类型为 [code](datatypes.html#code)的元素绑定为required时应遵循如下额外的规则：

*   如果该值集是FHIR所定义的，可允许编码的列表应固定在XML schema中
*   除非编码是由外部引用所定义的，且所引用的标准中存在明确声明，编码之间的比较常常都是大小写敏感的，
*   可使用编码的集合只有在随后的FHIR标准的版本中才能够进行扩展

如果一个元素跟一个value set的绑定程度/强度是required， [衍生出的规范 derived profiles](profiling.html) 
可声明编码使用的规则，但不能添加额外的编码。

<a name="extensible"> </a>

####  1.22.0.2.2 Extensible

要满足这种，如果value set中的某个编码能够表达某个概念，该元素的值必须从value set中取值，不然的话，可以使用额外的编码(数据类型或文本)

如果元素的数据类型为[CodeableConcept](datatypes.html#CodeableConcept),如果value set中的某个编码能够表达某个概念，coding的某个值必须取自规定的value，不然的话，可以使用text。

此种类型的绑定适用于在标准或规范层面对于使用可编码值能够达成一致，但是无法穷举出涵盖所有应用场景的编码集合的情况。



如果一个元素跟一个value set的绑定程度/强度是 extensible， 
When an element is bound to an extensible value set, [derived profiles](profiling.html) 
may state rules on which codes can be used, but cannot define new or additional codes for these elements
unless they are not found in the base value set.

<a name="preferred"> </a>

####  1.22.0.2.3  Preferred

出于互操作性的目的鼓励该元素的值从规定的编码中取值，但不强制要求。

如果元素的数据类型为[CodeableConcept](datatypes.html#CodeableConcept),如果value set中的某个编码能够表达某个概念，coding的某个值 宜 取自规定的value set，但是也可使用其他code或和text来取代。

此种类型的绑定适用于在标准或规范层面 这些可编码值是最佳选择，但由于种种原因某些实现中是不能使用这些推荐的编码的。系统或应用程序应极可能采用preferred的value set，因为这些value set能够在以后最大程度的满足服务器互操作性的要求。


如果一个元素跟一个value set的绑定程度/强度是 preferred，  [衍生出的规范 derived profiles](profiling.html) 
可以将该元素和任何它们认为适合value set绑定.

<a name="example"> </a>

#### 1.22.0.2.3.1 Example Bindings

数据实例中不要求也不鼓励从规定的value set中取值
value set中的值仅仅是对应包含哪些概念做个示范。

当某个元素的含义范围很广([List](list.html).code)时，或者对应该使用的编码没有达成共识时使用这种类型的绑定：

*   **Coding**:  system/code的值可能取自规定的value set中之一
*   **CodeableConcept**: 某个coding 可能包含取自value set的system/code

可以使用其他的编码值，也可使用text来代替。此类value set仅供开发人员参考，帮助理解以正确使用该元素。基于类如SNOMED CT这样的授权条款很严格的编码系统的value set在 FHIR 只能作为此类 example 绑定来使用，尽管在针对某个地区的具体的实施指南中可能会采用需要授权的value set。

如果一个元素跟一个value set的绑定程度/强度是 example，  [衍生出的规范 derived profiles](profiling.html) 

可以将该元素和任何它们认为适合value set绑定.

####  1.22.0.3  Other notes

*   如果能形成共识的话，后续版本的 FHIR 中可能会将example类型的绑定替换成preferred类型的。
*   标准中所提供的针对某个value set的绑定总是针对标准中所发布的某个具体的版本。value set可以只是一些简单的枚举值，也可以是来自某个没有规定特殊版本号的code system的编码，这种情况下，有效的可用的概念集合可能会随着时间而变化


