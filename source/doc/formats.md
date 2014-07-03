title: formats
date: 2014-05-20 15:13:12
categories: doc
---		


<a name="root"> </a>
<h1>资源格式 <span class="sectioncount">1.10.4.0<a name="1.10.4.0"> </a></span></h1>
<p>
该页记录了资源内容如何描述。实际交换中，资源可以用如下格式来表示：This page documents how the content of the resources are described. 
In actual exchange, resources can be represented in the following
formats: <a href="xml.htm">XML</a>and <a href="json.htm">JSON</a>. 
</p>

<h2>资源定义 <span class="sectioncount">1.10.4.0.1<a name="1.10.4.0.1"> </a></span></h2>
<p>
资源以2种不同的方式来描述：UML图 概述其内容，伪XML语法提供一种直观方式，最终XML格式的资源实例是长什么样的。记住尽管资源的描述是基于XML方式的，诸如JSON等其他格式也是等效的。The resources are described in two different ways: a UML diagram that summarises the content, and 
an pseudo-XML syntax that provides a visual sense of what the end resource instances will look like in XML. 
Note that although the description of the resources is based on their XML representation, other representations
such as JSON are equally valid.
</p>
<a name="syntax"> </a>
<h3>XML <span class="sectioncount">1.10.4.0.1.1<a name="1.10.4.0.1.1"> </a></span></h3>
<p>
XML语法使用如下标记：The XML syntax uses the following notation:
</p>
<pre class="spec">
 &lt;<b>name</b> xmlns=&quot;http://hl7.org/fhir&quot; (attrA=&quot;value&quot;)&gt; 
   &lt;<u><b title="Formal Definition (must be supported or understood)">nameA</b></u>&gt;<font color="Gray">&lt;!-- </font><font color="brown">1..1</font> <font color="Darkgreen">type</font> <font color="Navy">description of content</font> <font color="Gray"> --&gt;</font>&lt;nameA&gt;
   &lt;<b title="Formal Definition">nameB[x]</b>&gt;<font color="Gray">&lt;!-- </font><font title="Condition" color="deeppink">0..1</font> <font color="darkgreen">type1</font>|<font color="darkgreen">type1</font> <font color="Navy">description</font> <font color="Gray"> --&gt;</font>&lt;/nameB&gt;
   &lt;<b>nameC</b>&gt; <font color="Brown"><font color="Gray">&lt;!-- </font> <b>1..*</b> --&gt;</font>
     &lt;<b>nameD</b> &gt;<font color="Gray">&lt;!-- </font><font color="brown">1..1</font> <font color="darkgreen">type</font>&gt;<font color="navy">Relevant records</font> <font color="Gray"> --&gt;</font>&lt;/nameD&gt;
   &lt;/nameC&gt;
 &lt;name&gt;
</pre>
<p>
注意:
</p>
<ul>
 <li>资源和元素名称是大小写敏感的()Resource and Element names are case-sensitive (though duplicates that differ only in case are never defined)</li>
 <li>拥有<a href="datatypes.htm#primitive">primitive type</a>的任意元素都有一个value属性，包含该元素的实际值。Any elements that have a <a href="datatypes.htm#primitive">primitive type</a> will have a value attribute to contain the actual value of the element</li>
 <li>会给元素分配一个基数，用来确定该元素可或必须出现的次数。如果基数的颜色是粉色，也就是说有其他条件会影响该基数，要么鼠标移上去会显示文字 要么是在正式定义中。Elements are assigned a cardinality that specifies how many times the element may or must appear. If the cardinality is shown in 
    <font color="deeppink">Pink</font> then there is an additional condition that impacts on the allowed cardinality. This is available as a mouse-over text, or in the formal definitions</li>
 <li>元素有一或多种类型。所有类型都在<a href="datatypes.htm">数据类型</a> 中定义好了(除了&quot;Resource&quot; and &quot;Narrative&quot;)。类型名称是超链接。The elements are assigned one or more types. All of the types are defined in <a href="datatypes.htm">the data types</a> except for &quot;Resource&quot; and &quot;Narrative&quot; that are documented below. The type names are hyperlinked</li>
 <li>当元素可能是不止一种类型时，名称的格式为nnn[x]。&quot;nnn&quot;这部分是固定不变的，而[x]则用类型实际私用的名称来替代。允许 的类型之间用&quot;|&quot; 来分隔。当其中一种类型为Resource时，元素名称中的类型名称就直接是&quot;Resource&quot;。When a logical element can have more than one type, its name takes the form nnn[x]. The &quot;nnn&quot; part of the name is constant, and 
   the [x] is replaced with the title-cased name of the type that is actually used. The types that are allowed are listed with a &quot;|&quot; used to separate them. 
   When one of the types is Resource([X]), the type name in the element name is simply &quot;Resource&quot;</li>
 <li>伪语法中的每个元素名称都超链接到基础交换格式的数据字典中元素的正式定义。Each element name in the pseudo-syntax is also a hyperlink to the formal definition of the element in the data dictionary that underlies the exchange formats. </li>
 <li>如果元素名称带下划线，应用程序必须<a href="resources.htm#mustSupport">支持</a> 和或<a href="resources.htm#isModifier">理解</a>该元素。If the element name is underlined, then applications are required to <a href="resources.htm#mustSupport">support</a> and/or <a href="resources.htm#isModifier">understand</a> it</li>
 <li>资源的字符集总是Unicode，UTF-8编码。The character set for a resource is always Unicode, encoded in UTF-8.</li>
 <li>任一元素都可有id属性，在 <a href="references.htm#idref">指向内部引用时使用</a>.id属性在这种格式中未显示。Any of the elements may have an id attribute to serve as <a href="references.htm#idref">the target of an internal reference</a>. The id attribute is not shown in this format</li>
 <li>FHIR元素不能为空。如果资源中出现了某个元素，它必须要么有一个value属性，要么有一个子元素或者是id属性为<a href="narrative.htm#narrative">叙述性文本</a>中<a href="references.htm#idref">关联的目标</a> ，又或者是1到多个<a href="extensibility.htm">extensions</a>。FHIR elements are never empty. If an element is present in the resource, it must have either a value attribute, child elements as defined for its type, an id attribute that is the <a href="references.htm#idref">link target</a> of <a href="narrative.htm#narrative">narrative</a>, or 1 or more <a href="extensibility.htm">extensions</a></li>
 <li>属性不能为空。要么不存在，要么包含至少一个非空字符。Attributes can never be empty. Either they are absent, or they are present with at least one character of non-whitespace content</li>
 <li>除了描述性语法，也有一些其他定义形式，包括W3C schema和schematron。In addition to this descriptive syntax, other definitional forms are available, including W3C schema and Schematron</li>
</ul>

<h3>UML <span class="sectioncount">1.10.4.0.1.2<a name="1.10.4.0.1.2"> </a></span></h3>
<p>
UML图用一些类来表示资源的元素。The UML diagrams represent the same content as a series of classes that represent
the elements of a resource. 
</p>
<p style="text-alignment: left">
  <!-- ?xml version="1.0" encoding="UTF-8"? -->

<svg height="90.0" width="360.0" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns="http://www.w3.org/2000/svg" version="1.1">  <defs>
    <filter id="shadow" height="200%" width="200%" y="0" x="0">
      <feOffset result="offOut" dx="3" dy="3" in="SourceGraphic"/>
      <feColorMatrix result="matrixOut" values="0.2 0 0 0 0 0 0.2 0 0 0 0 0 0.2 0 0 0 0 0 1 0" type="matrix" in="offOut"/>
      <feGaussianBlur result="blurOut" stdDeviation="2" in="matrixOut"/>
      <feBlend in2="blurOut" in="SourceGraphic" mode="normal"/>
    </filter>
  </defs>
  <rect height="76.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="160.0" filter="url(#shadow)" rx="4" y="0.0" ry="4" x="0.0"/>
  <line style="stroke:dimgrey;stroke-width:1" y1="20.0" y2="20.0" x2="160.0" x1="0.0"/>
  <text style="font-size: 14; text-anchor: middle; font-family: sans-serif; font-weight: bold" fill="black" y="16.0" x="50.0">Name</text>
  <text style="font-size: 10; text-anchor: left; font-family: sans-serif" fill="black" y="36.0" x="4.0">attrA : string 0..1</text>
  <text style="font-size: 10; text-anchor: left; font-family: sans-serif" fill="black" y="50.0" x="4.0">nameA : type 1..1</text>
  <text style="font-size: 10; text-anchor: left; font-family: sans-serif" fill="black" y="64.0" x="4.0">nameB[x] : type1 | type2 0..1</text>

  <rect height="60.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="100.0" filter="url(#shadow)" rx="4" y="10" ry="4" x="240.0"/>
  <line style="stroke:dimgrey;stroke-width:1" y1="30.0" y2="30.0" x2="340.0" x1="240.0"/>
  <text style="font-size: 14; text-anchor: middle; font-family: sans-serif" fill="black" y="26.0" x="270.0">NameC</text>
  <text style="font-size: 10; text-anchor: left; font-family: sans-serif" fill="black" y="46.0" x="244.0">nameD : type 1..*</text>

  <line style="stroke:navy;stroke-width:1" y1="40.0" y2="40.0" x2="240.0" x1="160.0"/>
  <polygon style="fill:navy;stroke:navy;stroke-width:1" points="160.0,40.0 166.0,44.0 172.0,40.0 166.0,36.0 160.0,40.0"/>
  <rect height="18.0" style="fill:white;stroke:black;stroke-width:0" width="50.0" y="30.0" x="175.0"/>
  <text style="font-size: 10; text-anchor: middle; font-family: sans-serif; opacity: 1" fill="black" y="42.0" x="200.0">software</text>
  <text style="font-size: 10; text-anchor: middle; font-family: sans-serif; opacity: 1" fill="black" y="36.0" x="230.0">0..1</text>

</svg>
</p>
<p>
当元素的数据类型为可选时，使用上述XML语法中一样的方式来表示可选项。考虑到UML的原理，元素设计的顺序不是由图来确定的，也无法确定该元素是属性还是元素。元素和类型链接到正式定义中。UML图也能显示绑定，超链接到详细的绑定信息。Where an element can have a choice of data types, these are represented in the 
choice using the same syntax as the xml syntax described above. Due to way UML works, the actual 
order of the elements cannot be determined from the diagram, nor is it visible 
whether a property is an element or an attribute. The elements and types are
links to the formal definitions of the parts. The UML diagrams also show the 
bindings, and these are hyperlinks to the details of the binding.
</p>
<p>
这些UML图旨在将资源内容展示给人看。图的另一种形式更适合于代码生成，它是<a href="downloads.htm#refimpl">UML
参考平台</a>的一部分. These UML diagrams are intended to communicate the contents of the resource
to a human. An alternate set of diagrams that is more suited to code 
generation is available as part of the <a href="downloads.htm#refimpl">UML
reference platform</a>. 
</p>




