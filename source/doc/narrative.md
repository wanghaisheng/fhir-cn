title: narrative
date: 2014-05-20 15:13:12
categories: doc
---		


## 叙述性文本 <span class="sectioncount">1.10.3<a name="1.10.3"> </a></span>

每个资源可包含一个人可读的叙述性文本，其中包含了对资源的总结，可能用作表示资源中给人看的那部分内容。叙述性文本无需全部是结构化数据，但宜包含足够多的细节，人只是读取叙述性文本也能确保临床安全。资源定义可能定义那些内容宜在叙述性文本中表示以确保临床安全。Each resource may include a human readable narrative that contains a summary of the resource, 
and may be used to represent the content of the resource to a human. The narrative need 
not encode all the structured data, but SHOULD contain sufficient detail to make 
it &quot;clinically safe&quot; for a human to just read the narrative. Resource definitions may define 
what content should be represented in the narrative to ensure clinical safety.

资源中的叙述性文本允许包含一些结构化数据中不存在的额外信息，如人可编辑的内容。这样的额外信息必须在资源定义的范围之内，尽管很常见，在叙述性文本中包含从其他引用的资源中抽取额外的描述信息。The narrative for a resource is allowed to contain additional information that is not in 
the structured data, including human-edited content. Such additional information must be 
in the scope of the definition of the resource, though it is common for the narrative to
include additional descriptional information extracted from other referenced resources.

既然资源始终宜包含叙述性文本，为此，在严格管理的交易系统中，所有系统都是一个通用数据模型，不需要额外的文本，甚至是一种临床安全风险，这时叙述性文本可被省略。然而，实现人员在这样做之前宜认真考虑，因为这意味着这些资源只有在有限的交易环境中才能被理解，在它们定义的资源的生命周期中 这样封闭的交易环节很有可能会开放。While resources SHOULD always contain narrative, so that to support human-consumption
as a fall back, in a strictly managed trading systems where all systems share a common 
data model, and additional text is unnecessary or even a clinical safety risk, the 
narrative may be omitted. However implementers should consider carefully before 
doing this, as it will mean that these resources can only be understood in the 
limited trading environment, and closed trading partner environments are very likely 
to open up during the lifetime of the resources they define.

注意[内嵌](references.htm#contained)资源自身不应包含叙述性文本。 Note that [Contained](references.htm#contained) Resources SHALL NOT have a narrative 
of their own.

叙述性文本是一个xhtml的片段，也可包含图片：The narrative is an xhtml fragment that also includes images if appropriate:

<pre class="spec">
&lt;[**[name]**](narrative-definitions.htm#Narrative "A human readable formatted text, including images.") xmlns=&quot;http://hl7.org/fhir&quot;&gt;
 &lt;!-- from Element: [extension](extensibility.htm) --&gt;
 &lt;[**status**](narrative-definitions.htm#Narrative.status "The status of the narrative - whether it") value=&quot;[<span style="color: darkgreen">[code](datatypes.htm#code)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**1..1**</span> <span style="color: navy">[generated | extensions | additional](narrative-status.htm)</span><span style="color: Gray"> --&gt;</span>
 &lt;[**div**](narrative-definitions.htm#Narrative.div "The actual narrative content, a stripped down version of XHTML.") xmlns=&quot;http://www.w3.org/1999/xhtml&quot;&lt; <span style="color: Gray">&lt;!--</span> <span style="color: navy">Limited xhtml content</span><span style="color: Gray">&lt; --&gt;</span> &lt;/div&gt;
&lt;/[name]&gt;
</pre>

### 
Terminology Bindings
 <span class="sectioncount">1.10.3.1<a name="1.10.3.1"> </a></span>

<table class="grid">
 <tr><th>Path</th><th>Definition</th><th>Type</th><th>Reference</th></tr>
 <tr><td title="NarrativeStatus" valign="top">Narrative.status </td><td valign="top">The status of a resource narrative</td><td>[Fixed](terminologies.htm#code)</td><td valign="top">[http://hl7.org/fhir/narrative-status](narrative-status.htm)</td> </tr>
</table>

_div_ 元素的内容是XHTML片段，仅包含HTML4.0标准中第7-11(除了第9章第4部分)章和第15章所介绍的基本html元素：<a> element、image或内部包含的style属性。XHTML内容不应包含head、body元素和外部的stylesheet引用、script、form、base/link/xlink、frame、iframe和object。div元素必须包含一些非空白内容。The contents of the _div_ element are an XHTML fragment containing only the basic html formatting elements described in 
chapters 7-11 (except section 4 of chapter 9) and 15 of the HTML 4.0 standard, &lt;a&gt; elements (either name or href),
images and internally contained style attributes. The XHTML content must not contain
a head, a body element, external stylesheet references, scripts, forms, base/link/xlink, frames, iframes,
and objects. The div element must have some non-whitespace content.
  <!-- Todo: Formally encode these constraints in schematron -->

<div class="example">
<pre class="xml" fragment="Narrative">
  &lt;narrative&gt;
    &lt;div xmlns=&quot;http://www.w3.org/1999/xhtml&quot;&gt;This is a simple 
          example with only plain text&lt;/div&gt;
  &lt;/narrative&gt;

   &lt;narrative&gt;
   &lt;div xmlns=&quot;http://www.w3.org/1999/xhtml&quot;&gt;
     &lt;p&gt;
       This is an &lt;i&gt;example&lt;/i&gt; with some &lt;b&gt;xhtml&lt;/b&gt; formatting.
     &lt;/p&gt;
   &lt;/div&gt;
  &lt;/narrative&gt;
</pre>
</div>

div内容中的inner部分常常用在浏览器中的innerHTML属性中。为了简化处理，叙述性文本应编码，这样子第一个 &quot;&gt;&quot; 和最后一个&quot;&lt;&quot; 之间的内容就是&lt;div&gt;元素的字节内容。
The inner portion of the div content is often used for the innerHTML property in a browser.
In order to simplify processing, the narrative SHALL be encoded so that the character content
between the first &quot;&gt;&quot; and the last &quot;&lt;&quot; characters is the content of the &lt;div&gt; element.

注意:XHTML是嵌在XML中的，因此不支持如_&amp;nbsp;_ or _&amp;copy;_等HTML entity。应该使用Unicode来替代。用_&amp;#160;_ 替换_&amp;nbsp;_。Note that the XHTML is contained in general XML, and so there is no support for HTML entities
like _&amp;nbsp;_ or _&amp;copy;_ etc. Unicode characters should be used instead. Note that 
_&amp;#160;_ substitutes for _&amp;nbsp;_. 

叙述性文本的内容应采用<a href="base-definitions.htm#Resource.language">资源所使用的语言</a>，但并不期望HTML 类型的工具能理解资源中的_language_ 元素。鉴于此，&lt;div&gt; 元素中应使用lang属性(a href="http://www.w3.org/html/wg/drafts/html/master/dom.html#the-lang-and-xml:lang-attributes">参考HTML5标准中使用语言的注意事项)The narrative content should be in the [language of the resource](base-definitions.htm#Resource.language), but 
there is no reason to expect that HTML type tooling would understand the resource _language_ element. For this reason, 
a lang attribute on the &lt;div&gt; should also be used (and see 
[the note in the HTML 5 specification about use of language](http://www.w3.org/html/wg/drafts/html/master/dom.html#the-lang-and-xml:lang-attributes)).

image源引用可能是资源内的一个局部/本地引用：The image source references may be a local reference within the resource:

<pre class="xml">
  &lt;img src=&quot;#a5&quot;/&gt;
</pre>

这是对同一资源中某个元素的id属性的[内部引用](references.htm#idref) 。不管是&quot;[Attachment](datatypes.htm#Attachment)&quot;类型还是内嵌的[Binary](http.htm#binary)资源。This is an [internal reference](references.htm#idref) to an id attribute on an element in the same resource, 
either an element of type &quot;[Attachment](datatypes.htm#Attachment)&quot;, or a contained [Binary](http.htm#binary) resource.

<div class="example">
<pre class="xml">
&lt;Patient xmlns=&quot;http://hl7.org/fhir&quot;&gt;
  &lt;text&gt;
    &lt;status value=&quot;generated&quot;/&gt;
    &lt;div xmlns=&quot;http://www.w3.org/1999/xhtml&quot;&gt;
      &lt;p&gt;... &lt;img src=&quot;#pic1&quot;/&gt;. ....&lt;/p&gt;
    &lt;/div&gt;
  &lt;/text&gt;
  &lt;contained&gt;
    &lt;Binary id=&quot;pic1&quot; contentType=&quot;image/gif&quot;&gt;MEKH....SD/Z&lt;/Binary&gt;
  &lt;/contained&gt;
</pre>
</div>

由于不能保证未内嵌在资源内的图片的可及性，当将资源展现给用户时，图片的来源是叙述性文本必要的一部分，应始终嵌套在attachment或内嵌资源里面。
Since the availability of images that are not contained in the resource is not guaranteed, 
when the resource is presented to a user, the source for any images that are an essential 
part of the narrative should always be embedded in an attachment or a contained resource.

<a name="css"/>

### XHTML样式化Styling the XHTML <span class="sectioncount">1.10.3.2<a name="1.10.3.2"> </a></span>

叙述性文本中的XHTML片段可能使用标准方式的css、类和id以及内嵌的样式元素来样式化。当要将XHTML从资源中提取出来展示给用户时，可以给XHTML应用特定的css样式表来构建使用场景所需的展现形式。作者可能会固定内容的如下风格： XHTML fragment in the narrative may be styled using CSS in the normal fashion, using a mix of classes, ids 
and in-line style elements. Specific CSS stylesheets will be applied to the XHTML when it is extracted from
the resource to be displayed to a human to create the presentation desired in the context of use. Authors
may fix the following styling aspects of the content:

*   bold, italic, underline, strikethrough
*   font color, family, and size
*   background color, text alignment
*   whitespace interpretation
*   ordered list number format (since it may be referred to in text)

使用内置的style属性来规定这些样式属性。如果有类似的html元素存在，如&quot;i&quot;, or &quot;pre&quot; 可能会使用这些，但须注意HTML4中废弃了不少这样的元素，不能在叙述性文本的XHTML中使用(包括&quot;u&quot;, and &quot;font&quot;)。These style properties are specified in-line using the style attribute. If an equivalent 
html element exists, such as &quot;i&quot;, or &quot;pre&quot;, it may be used instead, but note that some of these 
elements are deprecated in HTML 4 and must not be used in Narrative XHTML (including &quot;u&quot;, and &quot;font&quot;).

渲染系统必须遵从在XHTML中规定的这些渲染风格，尽管允许恰当的解读(如在较暗的房间提供低对比度的展示和针对视觉障碍提供高对比度的展示)。Rendering systems are required to respect any of these rendering styles when they are specified in 
the XHTML, though appropriate interpretation is allowed (e.g. a low-contrast display for dark 
room contexts or a high-contrast display for the visually impaired may adjust colors accordingly). 

允许作者规定额外的在CSS标准中定义的样式和样式属性，但这些都是FHIR标准的扩展，渲染系统无需认可。然而要注意的是，有关样式的其他规定也适用于[documents](document.htm#css)中。
Authors are allowed to specify additional styles and style properties as specified in the CSS specification,
but these are extensions to this specification and renderers are not required to honor them. Note, however,
the additional rules around styling that apply in the context of [documents](document.htm#css).

注意：资源中的样式可采用FHIR标准样式表[http://hl7.org/implement/standards/fhir/fhir.css](http://hl7.org/implement/standards/fhir/fhir.css).已经定义的样式。鉴于没有直接提到该样式表，渲染系统可以保存自己的副本。在没有交易双方协议之下，管理系统不应依赖这些样式来正确地渲染临床内容。Note: styles in resources can make use of the styles defined in the standard FHIR stylesheet, which
lives here: [http://hl7.org/implement/standards/fhir/fhir.css](http://hl7.org/implement/standards/fhir/fhir.css).
Since this stylesheet is not referred to directly, rendering systems may take their own copy if they wish. 
Authoring systems should not depend on these styles being supported in order to render clinical content correctly without
trading partner agreement. 

</div>
<div class="col-3"><div class="itoc">

On This Page:

[Resource Definition](#root)

[Narrative](#Narrative)

[Internal References](#idref)

[JSON](#json)

[Atom (Bundle)](#atom)

[JSON (Bundle)](#json-bundles)

[Schema](#schema)

</div></div>