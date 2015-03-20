title: 
date: 
categories: doc
---

[首页](../home/index.html) >[文档](documentation.html) >[BackboneElement](BackboneElement.html) >**正规定义**       


 <!-- no repeating primitives in datatypes? No id's on primitives in datatypes...No dar on primitives in datatypes. It would be worthwhile to document that and the reason for it. -->

*   [Element](#)
*   [Detailed Descriptions](element-definitions.html)

# <span class="sectioncount">?.?<a name="?.?"> </a></span> BackboneElement

The base definition for elements defined as part of a resource. [Data Type](datatypes.html) elements do not use this type.

<a name="definition"/>

## <span class="sectioncount">?.?.1<a name="?.?.1"> </a></span> 
Content

<div id="tabs-BackboneElement">

*   [Structure](#tabs-BackboneElement-struc)
*   [UML](#tabs-BackboneElement-uml)
*   [XML](#tabs-BackboneElement-xml)
*   [JSON](#tabs-BackboneElement-json)
*   [All](#tabs-BackboneElement-all)
 <div id="tabs-BackboneElement-struc">
  <div id="tbl">

**Structure**

   <div id="tbl-inner">
    <table style="border: 0px; font-size: 11px; font-family: verdana; vertical-align: top;" cellpadding="0" border="0" cellspacing="0"><tr style="border: 1px #F0F0F0 solid; font-size: 11px; font-family: verdana; vertical-align: top;"><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Name</th><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Flags</th><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Card.</th><th style="width: 100px" class="heirarchy">Type</th><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Description &amp; Constraints<span style="float: right">[![doco](help16.png)](formats.html#table "Legend for this format")</span></th></tr><tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck1.png)" class="heirarchy">![.](tbl_spacer.png)![.](icon_element.gif "Element") [BackboneElement](backboneelement-definitions.html#BackboneElement "Base definition for all elements that are defined inside a resource - but not those in a data type.")<a name="BackboneElement"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy"/><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">1..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[Element](element.html)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Base for elements defined inside a resource</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck00.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin_end.png)![.](icon_extension_simple.png "Extension") [modifierExtension](backboneelement-definitions.html#BackboneElement.modifierExtension "May be used to represent additional information that is not part of the basic definition of the element, and that modifies the understanding of the element that contains it. Usually modifier elements provide negation or qualification. In order to make the use of extensions safe and manageable, there is a strict set of governance applied to the definition and use of extensions. Though any implementer is allowed to define an extension, there is a set of requirements that SHALL be met as part of the definition of the extension. Applications processing a resource are required to check for modifier extensions.")<a name="BackboneElement.modifierExtension"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy"/><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..*</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[Extension](extensibility.html#Extension)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Extensions that cannot be ignored</td></tr>
</table>
   </div>
  </div>
 </div>

 <div id="tabs-BackboneElement-uml">
  <div id="uml">

**UML Diagram**

   <div id="uml-inner">

to do

   </div>
  </div>
 </div>

 <div id="tabs-BackboneElement-xml">
  <div id="xml">

**XML Template**

   <div id="xml-inner">
    <pre class="spec">
&lt;[**BackboneElement**](backboneelement-definitions.html#BackboneElement "Base definition for all elements that are defined inside a resource - but not those in a data type.") xmlns=&quot;http://hl7.org/fhir&quot;&gt; <span style="float: right">[![doco](help.png)](formats.html "Documentation for this format")</span>
 &lt;!-- from [Resource](resource.html): [id](resource.html#id), [meta](resource.html#meta), [implicitRules](resource.html#implicitRules), and [language](resource.html#language) --&gt;
 &lt;[**modifierExtension**](backboneelement-definitions.html#BackboneElement.modifierExtension "May be used to represent additional information that is not part of the basic definition of the element, and that modifies the understanding of the element that contains it. Usually modifier elements provide negation or qualification. In order to make the use of extensions safe and manageable, there is a strict set of governance applied to the definition and use of extensions. Though any implementer is allowed to define an extension, there is a set of requirements that SHALL be met as part of the definition of the extension. Applications processing a resource are required to check for modifier extensions.")&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..***</span> <span style="color: darkgreen">[Extension](extensibility.html#Extension)</span> <span style="color: navy">Extensions that cannot be ignored</span><span style="color: Gray"> --&gt;</span>&lt;/modifierExtension&gt;
&lt;/BackboneElement&gt;
</pre>

   </div>
  </div>
 </div>

 <div id="tabs-BackboneElement-json">
  <div id="json">

**JSON Template**

   <div id="xml-inner">

todo

   </div>
  </div>
 </div>

 <div id="tabs-BackboneElement-all">
  <div id="tbla">
   <a name="tbl"> </a>

**Structure**

   <div id="tbl-inner">
    <table style="border: 0px; font-size: 11px; font-family: verdana; vertical-align: top;" cellpadding="0" border="0" cellspacing="0"><tr style="border: 1px #F0F0F0 solid; font-size: 11px; font-family: verdana; vertical-align: top;"><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Name</th><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Flags</th><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Card.</th><th style="width: 100px" class="heirarchy">Type</th><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Description &amp; Constraints<span style="float: right">[![doco](help16.png)](formats.html#table "Legend for this format")</span></th></tr><tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck1.png)" class="heirarchy">![.](tbl_spacer.png)![.](icon_element.gif "Element") [BackboneElement](backboneelement-definitions.html#BackboneElement "Base definition for all elements that are defined inside a resource - but not those in a data type.")<a name="BackboneElement"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy"/><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">1..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[Element](element.html)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Base for elements defined inside a resource</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck00.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin_end.png)![.](icon_extension_simple.png "Extension") [modifierExtension](backboneelement-definitions.html#BackboneElement.modifierExtension "May be used to represent additional information that is not part of the basic definition of the element, and that modifies the understanding of the element that contains it. Usually modifier elements provide negation or qualification. In order to make the use of extensions safe and manageable, there is a strict set of governance applied to the definition and use of extensions. Though any implementer is allowed to define an extension, there is a set of requirements that SHALL be met as part of the definition of the extension. Applications processing a resource are required to check for modifier extensions.")<a name="BackboneElement.modifierExtension"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy"/><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..*</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[Extension](extensibility.html#Extension)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Extensions that cannot be ignored</td></tr>
</table>
   </div>
  </div>

  <div id="umla">
   <a name="uml"> </a>

**UML Diagram**

   <div id="uml-inner">

todo

   </div>
  </div>

  <div id="xmla">
   <a name="xml"> </a>

**XML Template**

   <div id="xml-inner">
     <pre class="spec">
&lt;[**BackboneElement**](backboneelement-definitions.html#BackboneElement "Base definition for all elements that are defined inside a resource - but not those in a data type.") xmlns=&quot;http://hl7.org/fhir&quot;&gt; <span style="float: right">[![doco](help.png)](formats.html "Documentation for this format")</span>
 &lt;!-- from [Resource](resource.html): [id](resource.html#id), [meta](resource.html#meta), [implicitRules](resource.html#implicitRules), and [language](resource.html#language) --&gt;
 &lt;[**modifierExtension**](backboneelement-definitions.html#BackboneElement.modifierExtension "May be used to represent additional information that is not part of the basic definition of the element, and that modifies the understanding of the element that contains it. Usually modifier elements provide negation or qualification. In order to make the use of extensions safe and manageable, there is a strict set of governance applied to the definition and use of extensions. Though any implementer is allowed to define an extension, there is a set of requirements that SHALL be met as part of the definition of the extension. Applications processing a resource are required to check for modifier extensions.")&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..***</span> <span style="color: darkgreen">[Extension](extensibility.html#Extension)</span> <span style="color: navy">Extensions that cannot be ignored</span><span style="color: Gray"> --&gt;</span>&lt;/modifierExtension&gt;
&lt;/BackboneElement&gt;
</pre>

   </div>
  </div>

  <div id="jsona">
   <a name="json"> </a>

**JSON Template**

   <div id="xml-inner">

to do

   </div>
  </div>
 </div>
</div>

</div>


  <!-- end disqus -->        