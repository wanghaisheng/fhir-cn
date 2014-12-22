title: 
date: 
categories: doc
---


 <!-- no repeating primitives in datatypes? No id's on primitives in datatypes...No dar on primitives in datatypes. It would be worthwhile to document that and the reason for it. -->

*   [Element](#)
*   [Detailed Descriptions](element-definitions.html)

# <span class="sectioncount">?.?<a name="?.?"> </a></span> Element

The base definition for all elements contained inside a resource. All elements, whether defined as a [Data Type](datatypes.html)
or as part of a resource structure, have this base content:

<a name="definition"/>

## <span class="sectioncount">?.?.1<a name="?.?.1"> </a></span> 
Content

<div id="tabs-Element">

*   [Structure](#tabs-Element-struc)
*   [UML](#tabs-Element-uml)
*   [XML](#tabs-Element-xml)
*   [JSON](#tabs-Element-json)
*   [All](#tabs-Element-all)
 <div id="tabs-Element-struc">
  <div id="tbl">

**Structure**

   <div id="tbl-inner">
    <table style="border: 0px; font-size: 11px; font-family: verdana; vertical-align: top;" cellpadding="0" border="0" cellspacing="0"><tr style="border: 1px #F0F0F0 solid; font-size: 11px; font-family: verdana; vertical-align: top;"><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Name</th><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Flags</th><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Card.</th><th style="width: 100px" class="heirarchy">Type</th><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Description &amp; Constraints<span style="float: right">[![doco](help16.png)](formats.html#table "Legend for this format")</span></th></tr><tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck1.png)" class="heirarchy">![.](tbl_spacer.png)![.](icon_element.gif "Element") [Element](element-definitions.html#Element "Base definition for all elements in a resource.")<a name="Element"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy"/><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">1..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[Element](element.html)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Base for all elements</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_primitive.png "Primitive Data Type") [id](element-definitions.html#Element.id "unique id for the element within a resource (for internal references).")<a name="Element.id"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy"/><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[id](datatypes.html#id)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">xml:id (or equivalent in JSON)</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck00.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin_end.png)![.](icon_extension_simple.png "Extension") [extension](element-definitions.html#Element.extension "May be used to represent additional information that is not part of the basic definition of the element. In order to make the use of extensions safe and manageable, there is a strict set of governance  applied to the definition and use of extensions. Though any implementer is allowed to define an extension, there is a set of requirements that SHALL be met as part of the definition of the extension.")<a name="Element.extension"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy"/><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..*</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[Extension](extensibility.html#Extension)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Additional Content defined by implementations</td></tr>
</table>
   </div>
  </div>
 </div>

 <div id="tabs-Element-uml">
  <div id="uml">

**UML Diagram**

   <div id="uml-inner">

to do

   </div>
  </div>
 </div>

 <div id="tabs-Element-xml">
  <div id="xml">

**XML Template**

   <div id="xml-inner">
    <pre class="spec">
&lt;[**Element**](element-definitions.html#Element "Base definition for all elements in a resource.") xmlns=&quot;http://hl7.org/fhir&quot; id=&quot;<span style="color: navy">xml:id (or equivalent in JSON)</span> (<span style="color: darkgreen">[id](datatypes.html#id)</span>)&quot;&gt; <span style="float: right">[![doco](help.png)](formats.html "Documentation for this format")</span>
 &lt;[**extension**](element-definitions.html#Element.extension "May be used to represent additional information that is not part of the basic definition of the element. In order to make the use of extensions safe and manageable, there is a strict set of governance  applied to the definition and use of extensions. Though any implementer is allowed to define an extension, there is a set of requirements that SHALL be met as part of the definition of the extension.")&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..***</span> <span style="color: darkgreen">[Extension](extensibility.html#Extension)</span> <span style="color: navy">Additional Content defined by implementations</span><span style="color: Gray"> --&gt;</span>&lt;/extension&gt;
&lt;/Element&gt;
</pre>

   </div>
  </div>
 </div>

 <div id="tabs-Element-json">
  <div id="json">

**JSON Template**

   <div id="xml-inner">

todo

   </div>
  </div>
 </div>

 <div id="tabs-Element-all">
  <div id="tbla">
   <a name="tbl"> </a>

**Structure**

   <div id="tbl-inner">
    <table style="border: 0px; font-size: 11px; font-family: verdana; vertical-align: top;" cellpadding="0" border="0" cellspacing="0"><tr style="border: 1px #F0F0F0 solid; font-size: 11px; font-family: verdana; vertical-align: top;"><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Name</th><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Flags</th><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Card.</th><th style="width: 100px" class="heirarchy">Type</th><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Description &amp; Constraints<span style="float: right">[![doco](help16.png)](formats.html#table "Legend for this format")</span></th></tr><tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck1.png)" class="heirarchy">![.](tbl_spacer.png)![.](icon_element.gif "Element") [Element](element-definitions.html#Element "Base definition for all elements in a resource.")<a name="Element"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy"/><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">1..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[Element](element.html)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Base for all elements</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_primitive.png "Primitive Data Type") [id](element-definitions.html#Element.id "unique id for the element within a resource (for internal references).")<a name="Element.id"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy"/><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[id](datatypes.html#id)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">xml:id (or equivalent in JSON)</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck00.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin_end.png)![.](icon_extension_simple.png "Extension") [extension](element-definitions.html#Element.extension "May be used to represent additional information that is not part of the basic definition of the element. In order to make the use of extensions safe and manageable, there is a strict set of governance  applied to the definition and use of extensions. Though any implementer is allowed to define an extension, there is a set of requirements that SHALL be met as part of the definition of the extension.")<a name="Element.extension"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy"/><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..*</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[Extension](extensibility.html#Extension)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Additional Content defined by implementations</td></tr>
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
&lt;[**Element**](element-definitions.html#Element "Base definition for all elements in a resource.") xmlns=&quot;http://hl7.org/fhir&quot; id=&quot;<span style="color: navy">xml:id (or equivalent in JSON)</span> (<span style="color: darkgreen">[id](datatypes.html#id)</span>)&quot;&gt; <span style="float: right">[![doco](help.png)](formats.html "Documentation for this format")</span>
 &lt;[**extension**](element-definitions.html#Element.extension "May be used to represent additional information that is not part of the basic definition of the element. In order to make the use of extensions safe and manageable, there is a strict set of governance  applied to the definition and use of extensions. Though any implementer is allowed to define an extension, there is a set of requirements that SHALL be met as part of the definition of the extension.")&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..***</span> <span style="color: darkgreen">[Extension](extensibility.html#Extension)</span> <span style="color: navy">Additional Content defined by implementations</span><span style="color: Gray"> --&gt;</span>&lt;/extension&gt;
&lt;/Element&gt;
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

				</div>  <!-- /inner-wrapper -->
            </div>  <!-- /row -->
        </div>  <!-- /container -->

    </div>  <!-- /segment-content -->

	<div id="segment-footer" class="segment">  <!-- segment-footer -->
		<div class="container">  <!-- container -->
			<div class="inner-wrapper">

        © HL7.org 2011+. FHIR DSTU (v0.4.0-3900) generated on Sat, Dec 20, 2014 22:38+0000.   <!-- [QA Report](qa.html) -->   <!-- achive note -->

        <span style="color: #FFFF77">
        Links: [What's a DSTU?](timelines.html) | 
               [Version History](history.html) | 
               [Compare to DSTU](http://services.w3.org/htmldiff?doc1=http%3A%2F%2Fhl7.org%2Fimplement%2Fstandards%2Ffhir%2Felement.html&amp;doc2=http%3A%2F%2Fhl7-fhir.github.io%2F%2Felement.html) | 
               [![CC0](cc0.png)](license.html) | 
               [Propose a change](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemAdd&amp;tracker_id=677)   
        </span>

			</div>  <!-- /inner-wrapper -->
		</div>  <!-- /container -->
	</div>  <!-- /segment-footer -->
  <!-- disqus thread -->
  <!-- disqus -->