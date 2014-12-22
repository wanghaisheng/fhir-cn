 DomainResource Resource

## <span class="sectioncount">null.1<a name="null.1"> </a></span> Scope and Usage

This resource is defined to add text, contained resources, and extension support
to the base [resource](resource.html). As an abstract resource, this 
resource never exists directly, only one of it's descendent resources ([list](resourcelist.html)).

For further information:

*   _text_: see [Human Narrative in resources](narrative.html)
*   _contained_: see [Contained Resources](references.html#contained)
*   _extension_ and _modifierExtension_: See [Extensibility](extensibility.html)

</div>

<div>

## <span class="sectioncount">null.2<a name="null.2"> </a></span> Boundaries and Relationships

This resource is extends [resource](resource.html). All of the [listed](resourcelist.html)
resources except [Bundle](bundle.html) and [Binary](binary.html) extend
this resource.

</div>

<a name="resource"/>

## <span class="sectioncount">null.3<a name="null.3"> </a></span> 
Resource Content

<a name="def"> </a>
<a name="domainresource"> </a>
<a name="DomainResource"> </a>

<div id="tabs">

*   [Structure](#tabs-struc)
*   [UML](#tabs-uml)
*   [XML](#tabs-xml)
*   [JSON](#tabs-json)
*   [All](#tabs-all)
  <div id="tabs-struc">
    <div id="tbl">

**Structure**

      <div id="tbl-inner">
        <table style="border: 0px; font-size: 11px; font-family: verdana; vertical-align: top;" cellpadding="0" border="0" cellspacing="0"><tr style="border: 1px #F0F0F0 solid; font-size: 11px; font-family: verdana; vertical-align: top;"><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Name</th><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Flags</th><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Card.</th><th style="width: 100px" class="heirarchy">Type</th><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Description &amp; Constraints<span style="float: right">[![doco](help16.png)](formats.html#table "Legend for this format")</span></th></tr><tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck1.png)" class="heirarchy">![.](tbl_spacer.png)![.](icon_resource.png "Resource") [DomainResource](domainresource-definitions.html#DomainResource)<a name="DomainResource"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy"><span title="This element has or is affected by some invariants">I</span></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy"/><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[Resource](resource.html)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">
<span title="3" style="font-style: italic">If the resource is contained in another resource, it SHALL be referred to from elsewhere in the resource</span>
<span title="2" style="font-style: italic">If the resource is contained in another resource, it SHALL not contain nested Resources</span>
<span title="1" style="font-style: italic">If the resource is contained in another resource, it SHALL not contain any narrative</span></td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_datatype.gif "Data Type") [text](domainresource-definitions.html#DomainResource.text "A human-readable narrative that contains a summary of the resource, and may be used to represent the content of the resource to a human. The narrative need not encode all the structured data, but is required to contain sufficient detail to make it &quot;clinically safe&quot; for a human to just read the narrative. Resource definitions may define what content should be represented in the narrative to ensure clinical safety.")<a name="DomainResource.text"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy"><span title="This element has or is affected by some invariants">I</span></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[Narrative](narrative.html#Narrative)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Text summary of the resource, for human interpretation</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_datatype.gif "Data Type") [contained](domainresource-definitions.html#DomainResource.contained "These resources do not have an independent existence apart from the resource that contains them - they cannot be identified independently, and nor can they have their own independent transaction scope.")<a name="DomainResource.contained"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy"/><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..*</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[Resource](resource.html#Resource)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Contained, inline Resources</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_extension_simple.png "Extension") [extension](domainresource-definitions.html#DomainResource.extension "May be used to represent additional information that is not part of the basic definition of the resource. In order to make the use of extensions safe and manageable, there is a strict set of governance  applied to the definition and use of extensions. Though any implementer is allowed to define an extension, there is a set of requirements that SHALL be met as part of the definition of the extension.")<a name="DomainResource.extension"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy"/><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..*</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[Extension](extensibility.html#Extension)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Additional Content defined by implementations</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck00.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin_end.png)![.](icon_extension_simple.png "Extension") [modifierExtension](domainresource-definitions.html#DomainResource.modifierExtension "May be used to represent additional information that is not part of the basic definition of the resource, and that modifies the understanding of the element that contains it. Usually modifier elements provide negation or qualification. In order to make the use of extensions safe and manageable, there is a strict set of governance applied to the definition and use of extensions. Though any implementer is allowed to define an extension, there is a set of requirements that SHALL be met as part of the definition of the extension. Applications processing a resource are required to check for modifier extensions.")<a name="DomainResource.modifierExtension"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy"/><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..*</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[Extension](extensibility.html#Extension)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Extensions that cannot be ignored</td></tr>
</table>
      </div>
    </div>
  </div>
  <div id="tabs-uml"> 
    <div id="uml">

**UML Diagram**

      <div id="uml-inner">
        <svg height="102.0" width="244.8" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns="http://www.w3.org/2000/svg" version="1.1">  <defs>
    <filter id="shadow" height="200%" width="200%" y="0" x="0">
      <feOffset result="offOut" dx="3" dy="3" in="SourceGraphic"/>
      <feColorMatrix result="matrixOut" values="0.2 0 0 0 0 0 0.2 0 0 0 0 0 0.2 0 0 0 0 0 1 0" type="matrix" in="offOut"/>
      <feGaussianBlur result="blurOut" stdDeviation="2" in="matrixOut"/>
      <feBlend in2="blurOut" in="SourceGraphic" mode="normal"/>
    </filter>
  </defs><rect height="92.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="144.8" filter="url(#shadow)" rx="4" y="0.0" ry="4" x="0.0"/><line style="stroke:dimgrey;stroke-width:1" y1="28.0" y2="28.0" x2="144.8" x1="0.0"/><text fill="black" class="diagram-class-title  diagram-class-resource" y="20.0" x="72.4">DomainResource<tspan class="diagram-class-title-link"> ([Resource](resource.html))</tspan></text><text fill="black" class="diagram-class-detail" y="42.0" x="6.0">[<title>A human-readable narrative that contains a summary of the resource, and may be used to represent the content of the resource to a human. The narrative need not encode all the structured data, but is required to contain sufficient detail to make it &quot;clinically safe&quot; for a human to just read the narrative. Resource definitions may define what content should be represented in the narrative to ensure clinical safety</title>text](domainresource-definitions.html#DomainResource.text) : [Narrative](narrative.html#Narrative) 0..1</text><text fill="black" class="diagram-class-detail" y="56.0" x="6.0">[<title>These resources do not have an independent existence apart from the resource that contains them - they cannot be identified independently, and nor can they have their own independent transaction scope</title>contained](domainresource-definitions.html#DomainResource.contained) : [Resource](resource.html#Resource) 0..*</text><text fill="black" class="diagram-class-detail" y="70.0" x="6.0">[<title>May be used to represent additional information that is not part of the basic definition of the resource. In order to make the use of extensions safe and manageable, there is a strict set of governance  applied to the definition and use of extensions. Though any implementer is allowed to define an extension, there is a set of requirements that SHALL be met as part of the definition of the extension</title>extension](domainresource-definitions.html#DomainResource.extension) : [Extension](extensibility.html#Extension) 0..*</text><text fill="black" class="diagram-class-detail" y="84.0" x="6.0">[<title>May be used to represent additional information that is not part of the basic definition of the resource, and that modifies the understanding of the element that contains it. Usually modifier elements provide negation or qualification. In order to make the use of extensions safe and manageable, there is a strict set of governance applied to the definition and use of extensions. Though any implementer is allowed to define an extension, there is a set of requirements that SHALL be met as part of the definition of the extension. Applications processing a resource are required to check for modifier extensions</title>modifierExtension](domainresource-definitions.html#DomainResource.modifierExtension) : [Extension](extensibility.html#Extension) 0..*</text></svg>
      </div>
    </div>
  </div>
  <div id="tabs-xml">
    <div id="xml">

**XML Template**

      <div id="xml-inner">
        <pre class="spec">
&lt;[**[name]**](domainresource-definitions.html#DomainResource "null") xmlns=&quot;http://hl7.org/fhir&quot;&gt; <span style="float: right">[![doco](help.png)](formats.html "Documentation for this format")</span>
 &lt;!-- from Element: [extension](extensibility.html) --&gt;
 &lt;[**text**](domainresource-definitions.html#DomainResource.text "A human-readable narrative that contains a summary of the resource, and may be used to represent the content of the resource to a human. The narrative need not encode all the structured data, but is required to contain sufficient detail to make it &quot;clinically safe&quot; for a human to just read the narrative. Resource definitions may define what content should be represented in the narrative to ensure clinical safety.")&gt;<span style="color: Gray">&lt;!--</span> <span title="Inv-1: If the resource is contained in another resource, it SHALL not contain any narrative" style="color: brown">**![??](lock.png) 0..1**</span> <span style="color: darkgreen">[Narrative](narrative.html#Narrative)</span> <span style="color: navy">Text summary of the resource, for human interpretation</span><span style="color: Gray"> --&gt;</span>&lt;/text&gt;
 &lt;[**contained**](domainresource-definitions.html#DomainResource.contained "These resources do not have an independent existence apart from the resource that contains them - they cannot be identified independently, and nor can they have their own independent transaction scope.")&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..***</span> <span style="color: darkgreen">[Resource](resource.html#Resource)</span> <span style="color: navy">Contained, inline Resources</span><span style="color: Gray"> --&gt;</span>&lt;/contained&gt;
 &lt;[**extension**](domainresource-definitions.html#DomainResource.extension "May be used to represent additional information that is not part of the basic definition of the resource. In order to make the use of extensions safe and manageable, there is a strict set of governance  applied to the definition and use of extensions. Though any implementer is allowed to define an extension, there is a set of requirements that SHALL be met as part of the definition of the extension.")&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..***</span> <span style="color: darkgreen">[Extension](extensibility.html#Extension)</span> <span style="color: navy">Additional Content defined by implementations</span><span style="color: Gray"> --&gt;</span>&lt;/extension&gt;
 &lt;[**modifierExtension**](domainresource-definitions.html#DomainResource.modifierExtension "May be used to represent additional information that is not part of the basic definition of the resource, and that modifies the understanding of the element that contains it. Usually modifier elements provide negation or qualification. In order to make the use of extensions safe and manageable, there is a strict set of governance applied to the definition and use of extensions. Though any implementer is allowed to define an extension, there is a set of requirements that SHALL be met as part of the definition of the extension. Applications processing a resource are required to check for modifier extensions.")&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..***</span> <span style="color: darkgreen">[Extension](extensibility.html#Extension)</span> <span style="color: navy">Extensions that cannot be ignored</span><span style="color: Gray"> --&gt;</span>&lt;/modifierExtension&gt;
&lt;/[name]&gt;
</pre>

      </div>
    </div>
  </div>
  <div id="tabs-json">
    <div id="json">

**JSON Template**

      <div id="xml-inner">

todo

      </div>
    </div>
  </div>
  <div id="tabs-all">
    <div id="tbl">
      <a name="tbl"> </a>

**Structure**

      <div id="tbl-inner">
        <table style="border: 0px; font-size: 11px; font-family: verdana; vertical-align: top;" cellpadding="0" border="0" cellspacing="0"><tr style="border: 1px #F0F0F0 solid; font-size: 11px; font-family: verdana; vertical-align: top;"><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Name</th><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Flags</th><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Card.</th><th style="width: 100px" class="heirarchy">Type</th><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Description &amp; Constraints<span style="float: right">[![doco](help16.png)](formats.html#table "Legend for this format")</span></th></tr><tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck1.png)" class="heirarchy">![.](tbl_spacer.png)![.](icon_resource.png "Resource") [DomainResource](domainresource-definitions.html#DomainResource)<a name="DomainResource"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy"><span title="This element has or is affected by some invariants">I</span></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy"/><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[Resource](resource.html)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">
<span title="3" style="font-style: italic">If the resource is contained in another resource, it SHALL be referred to from elsewhere in the resource</span>
<span title="2" style="font-style: italic">If the resource is contained in another resource, it SHALL not contain nested Resources</span>
<span title="1" style="font-style: italic">If the resource is contained in another resource, it SHALL not contain any narrative</span></td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_datatype.gif "Data Type") [text](domainresource-definitions.html#DomainResource.text "A human-readable narrative that contains a summary of the resource, and may be used to represent the content of the resource to a human. The narrative need not encode all the structured data, but is required to contain sufficient detail to make it &quot;clinically safe&quot; for a human to just read the narrative. Resource definitions may define what content should be represented in the narrative to ensure clinical safety.")<a name="DomainResource.text"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy"><span title="This element has or is affected by some invariants">I</span></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[Narrative](narrative.html#Narrative)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Text summary of the resource, for human interpretation</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_datatype.gif "Data Type") [contained](domainresource-definitions.html#DomainResource.contained "These resources do not have an independent existence apart from the resource that contains them - they cannot be identified independently, and nor can they have their own independent transaction scope.")<a name="DomainResource.contained"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy"/><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..*</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[Resource](resource.html#Resource)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Contained, inline Resources</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_extension_simple.png "Extension") [extension](domainresource-definitions.html#DomainResource.extension "May be used to represent additional information that is not part of the basic definition of the resource. In order to make the use of extensions safe and manageable, there is a strict set of governance  applied to the definition and use of extensions. Though any implementer is allowed to define an extension, there is a set of requirements that SHALL be met as part of the definition of the extension.")<a name="DomainResource.extension"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy"/><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..*</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[Extension](extensibility.html#Extension)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Additional Content defined by implementations</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck00.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin_end.png)![.](icon_extension_simple.png "Extension") [modifierExtension](domainresource-definitions.html#DomainResource.modifierExtension "May be used to represent additional information that is not part of the basic definition of the resource, and that modifies the understanding of the element that contains it. Usually modifier elements provide negation or qualification. In order to make the use of extensions safe and manageable, there is a strict set of governance applied to the definition and use of extensions. Though any implementer is allowed to define an extension, there is a set of requirements that SHALL be met as part of the definition of the extension. Applications processing a resource are required to check for modifier extensions.")<a name="DomainResource.modifierExtension"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy"/><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..*</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[Extension](extensibility.html#Extension)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Extensions that cannot be ignored</td></tr>
</table>
      </div>
    </div>
    <div id="uml">
      <a name="uml"> </a>

**UML Diagram**

      <div id="uml-inner">
        <svg height="102.0" width="244.8" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns="http://www.w3.org/2000/svg" version="1.1">  <defs>
    <filter id="shadow" height="200%" width="200%" y="0" x="0">
      <feOffset result="offOut" dx="3" dy="3" in="SourceGraphic"/>
      <feColorMatrix result="matrixOut" values="0.2 0 0 0 0 0 0.2 0 0 0 0 0 0.2 0 0 0 0 0 1 0" type="matrix" in="offOut"/>
      <feGaussianBlur result="blurOut" stdDeviation="2" in="matrixOut"/>
      <feBlend in2="blurOut" in="SourceGraphic" mode="normal"/>
    </filter>
  </defs><rect height="92.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="144.8" filter="url(#shadow)" rx="4" y="0.0" ry="4" x="0.0"/><line style="stroke:dimgrey;stroke-width:1" y1="28.0" y2="28.0" x2="144.8" x1="0.0"/><text fill="black" class="diagram-class-title  diagram-class-resource" y="20.0" x="72.4">DomainResource<tspan class="diagram-class-title-link"> ([Resource](resource.html))</tspan></text><text fill="black" class="diagram-class-detail" y="42.0" x="6.0">[<title>A human-readable narrative that contains a summary of the resource, and may be used to represent the content of the resource to a human. The narrative need not encode all the structured data, but is required to contain sufficient detail to make it &quot;clinically safe&quot; for a human to just read the narrative. Resource definitions may define what content should be represented in the narrative to ensure clinical safety</title>text](domainresource-definitions.html#DomainResource.text) : [Narrative](narrative.html#Narrative) 0..1</text><text fill="black" class="diagram-class-detail" y="56.0" x="6.0">[<title>These resources do not have an independent existence apart from the resource that contains them - they cannot be identified independently, and nor can they have their own independent transaction scope</title>contained](domainresource-definitions.html#DomainResource.contained) : [Resource](resource.html#Resource) 0..*</text><text fill="black" class="diagram-class-detail" y="70.0" x="6.0">[<title>May be used to represent additional information that is not part of the basic definition of the resource. In order to make the use of extensions safe and manageable, there is a strict set of governance  applied to the definition and use of extensions. Though any implementer is allowed to define an extension, there is a set of requirements that SHALL be met as part of the definition of the extension</title>extension](domainresource-definitions.html#DomainResource.extension) : [Extension](extensibility.html#Extension) 0..*</text><text fill="black" class="diagram-class-detail" y="84.0" x="6.0">[<title>May be used to represent additional information that is not part of the basic definition of the resource, and that modifies the understanding of the element that contains it. Usually modifier elements provide negation or qualification. In order to make the use of extensions safe and manageable, there is a strict set of governance applied to the definition and use of extensions. Though any implementer is allowed to define an extension, there is a set of requirements that SHALL be met as part of the definition of the extension. Applications processing a resource are required to check for modifier extensions</title>modifierExtension](domainresource-definitions.html#DomainResource.modifierExtension) : [Extension](extensibility.html#Extension) 0..*</text></svg>
      </div>
    </div>
    <div id="xml">
      <a name="xml"> </a>

**XML Template**

      <div id="xml-inner">
        <pre class="spec">
&lt;[**[name]**](domainresource-definitions.html#DomainResource "null") xmlns=&quot;http://hl7.org/fhir&quot;&gt; <span style="float: right">[![doco](help.png)](formats.html "Documentation for this format")</span>
 &lt;!-- from Element: [extension](extensibility.html) --&gt;
 &lt;[**text**](domainresource-definitions.html#DomainResource.text "A human-readable narrative that contains a summary of the resource, and may be used to represent the content of the resource to a human. The narrative need not encode all the structured data, but is required to contain sufficient detail to make it &quot;clinically safe&quot; for a human to just read the narrative. Resource definitions may define what content should be represented in the narrative to ensure clinical safety.")&gt;<span style="color: Gray">&lt;!--</span> <span title="Inv-1: If the resource is contained in another resource, it SHALL not contain any narrative" style="color: brown">**![??](lock.png) 0..1**</span> <span style="color: darkgreen">[Narrative](narrative.html#Narrative)</span> <span style="color: navy">Text summary of the resource, for human interpretation</span><span style="color: Gray"> --&gt;</span>&lt;/text&gt;
 &lt;[**contained**](domainresource-definitions.html#DomainResource.contained "These resources do not have an independent existence apart from the resource that contains them - they cannot be identified independently, and nor can they have their own independent transaction scope.")&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..***</span> <span style="color: darkgreen">[Resource](resource.html#Resource)</span> <span style="color: navy">Contained, inline Resources</span><span style="color: Gray"> --&gt;</span>&lt;/contained&gt;
 &lt;[**extension**](domainresource-definitions.html#DomainResource.extension "May be used to represent additional information that is not part of the basic definition of the resource. In order to make the use of extensions safe and manageable, there is a strict set of governance  applied to the definition and use of extensions. Though any implementer is allowed to define an extension, there is a set of requirements that SHALL be met as part of the definition of the extension.")&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..***</span> <span style="color: darkgreen">[Extension](extensibility.html#Extension)</span> <span style="color: navy">Additional Content defined by implementations</span><span style="color: Gray"> --&gt;</span>&lt;/extension&gt;
 &lt;[**modifierExtension**](domainresource-definitions.html#DomainResource.modifierExtension "May be used to represent additional information that is not part of the basic definition of the resource, and that modifies the understanding of the element that contains it. Usually modifier elements provide negation or qualification. In order to make the use of extensions safe and manageable, there is a strict set of governance applied to the definition and use of extensions. Though any implementer is allowed to define an extension, there is a set of requirements that SHALL be met as part of the definition of the extension. Applications processing a resource are required to check for modifier extensions.")&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..***</span> <span style="color: darkgreen">[Extension](extensibility.html#Extension)</span> <span style="color: navy">Extensions that cannot be ignored</span><span style="color: Gray"> --&gt;</span>&lt;/modifierExtension&gt;
&lt;/[name]&gt;
</pre>

      </div>
    </div>
    <div id="json">
      <a name="json"> </a>

**JSON Template**

      <div id="xml-inner">

to do

      </div>
    </div>  
  </div>
</div>

<a name="tx"> </a>

### <span class="sectioncount">null.3.1<a name="null.3.1"> </a></span> Constraints

*   **Inv-1**: If the resource is contained in another resource, it SHALL not contain any narrative (xpath: <span style="font-family: Courier New, monospace">not(parent::f:contained and f:text)</span>)
*   **Inv-2**: If the resource is contained in another resource, it SHALL not contain nested Resources (xpath: <span style="font-family: Courier New, monospace">not(parent::f:contained and f:contained)</span>)
*   **Inv-3**: If the resource is contained in another resource, it SHALL be referred to from elsewhere in the resource (xpath: <span style="font-family: Courier New, monospace">exists(for $id in f:contained/*/@id return $id[not(ancestor::f:contained/parent::*/descendant::f:reference/@value=concat('#', $id))])</span>)

<a name="search"> </a>

## <span class="sectioncount">null.4<a name="null.4"> </a></span> Search Parameters

This resource doesn't define any common [Search parameters](search.html)

To search for extensions, define a search parameter for the extension. 
All other search parameters are named aliases for existing content in
the resource. In some cases, though not all, the search parameter name
is the same as the element that it searches, but this is not required. 
Searching for extensions is the same - define a name that identifies 
the value extension by it's URL, and then searches can filter based on
the value of the extension.

<a name="search"> </a>

</div>

				</div>  <!-- /inner-wrapper -->
            </div>  <!-- /row -->
        </div>  <!-- /container -->

    </div>  <!-- /segment-content -->

	<div id="segment-footer" class="segment">  <!-- segment-footer -->
		<div class="container">  <!-- container -->
			<div class="inner-wrapper">

        © HL7.org 2011+. FHIR DSTU (v0.4.0-3900) generated on Sat, Dec 20, 2014 22:28+0000.   <!-- [QA Report](qa.html) -->   <!-- achive note -->

        <span style="color: #FFFF77">
        Links: [What's a DSTU?](timelines.html) | 
               [Version History](history.html) | 
               [Compare to DSTU](http://services.w3.org/htmldiff?doc1=http%3A%2F%2Fhl7.org%2Fimplement%2Fstandards%2Ffhir%2Fdomainresource.html&amp;doc2=http%3A%2F%2Fhl7-fhir.github.io%2F%2Fdomainresource.html) | 
               [![CC0](cc0.png)](license.html) | 
               [Propose a change](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemAdd&amp;tracker_id=677)   
        </span>

			</div>  <!-- /inner-wrapper -->
		</div>  <!-- /container -->
	</div>  <!-- /segment-footer -->
  <!-- disqus thread -->
  <!-- disqus -->
  <!-- end disqus -->        