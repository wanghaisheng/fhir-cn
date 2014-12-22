title: 
date: 
categories: doc
---

*   [Content](#)
*   [Detailed Descriptions](resource-definitions.html)
*   [Operations](resource-operations.html)

# <span class="sectioncount"><a name="null"> </a></span> Base Resource Definitions

<div>

## <span class="sectioncount">null.1<a name="null.1"> </a></span> Scope and Usage

This specification defines a series of different types of resource that can be used to exchange and/or store data 
in order to solve a wide range of healthcare related problems, both clinical and administrative. In addition,
this specification defines several different ways of exchanging the resources.

A resource is an entity that:

*   has a known identity (a url) by which it can be addressed
*   identifies itself as one of the types of resource defined in this specification
*   contains a set of structured data items as described by the definition of the resource type
*   contains a human-readable XHTML representation of the content of the resource
*   has an identified version that changes if the contents of the resource change

Resources have multiple representations. A resource is valid if it meets the above rules, and is represented in 
either [XML](xml.html) or [JSON](json.html) according to the rules defined in this specification. 
Other representations are allowed, but are not described by this specification.

  <!-- 

Basic definitions:

<table class="grid">
 <tr> <td>Resource</td> <td>An instance of data that is stored or exchanged</td> </tr>
 <tr> <td>Resource Definition</td> <td>Defines the data elements that are part of the resource</td> </tr>
 <tr> <td>Profile</td> <td>Additional rules about the data elements for a particular context of use. There's a specific type of resource - the [Profile Resource](profile.html) that is used to represent a profile</td> </tr>
</table> -->

</div>

<div>

## <span class="sectioncount">null.2<a name="null.2"> </a></span> Boundaries and Relationships

All resources have the following optional or mandatory elements and properties:

*   An identity
*   Meta data
*   A base language
*   A reference to &quot;Implicit Rules&quot;

Most resources are derived from [Domain Resources](domainresource.html) - they also contain text, contained resources, extensions,
and data elements specific to the particular domain of the resource. There is a special type of resource called [Bundle](bundle.html) for groups/lists of resources. 

Note: there is documentation for the [Structure](formats.html), [UML](formats.html#uml), [XML](xml.html), and [JSON](json.html) representations. 

</div>

<a name="resource"/>

## <span class="sectioncount">null.3<a name="null.3"> </a></span> 
Resource Content

<a name="def"> </a>
<a name="resource"> </a>
<a name="Resource"> </a>

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
        <table style="border: 0px; font-size: 11px; font-family: verdana; vertical-align: top;" cellpadding="0" border="0" cellspacing="0"><tr style="border: 1px #F0F0F0 solid; font-size: 11px; font-family: verdana; vertical-align: top;"><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Name</th><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Flags</th><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Card.</th><th style="width: 100px" class="heirarchy">Type</th><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Description &amp; Constraints<span style="float: right">[![doco](help16.png)](formats.html#table "Legend for this format")</span></th></tr><tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck1.png)" class="heirarchy">![.](tbl_spacer.png)![.](icon_resource.png "Resource") [Resource](resource-definitions.html#Resource "Base Resource for everything.")<a name="Resource"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy"/><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy"/><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">n/a</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Base Resource</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_primitive.png "Primitive Data Type") [id](resource-definitions.html#Resource.id "The logical id of the resource, as used in the url for the resoure. Once assigned, this value never changes.")<a name="Resource.id"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy"/><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[id](datatypes.html#id)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Logical id of this artefact</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck11.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_element.gif "Element") [meta](resource-definitions.html#Resource.meta "The metadata about the resource. This is content that is maintained by the infrastructure. Changes to the content may not always be associated with version changes to the resource.")<a name="Resource.meta"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy"/><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[Element](element.html)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Metadata about the resource</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck110.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vline.png)![.](tbl_vjoin.png)![.](icon_primitive.png "Primitive Data Type") [versionId](resource-definitions.html#Resource.meta.versionId "The version specific identifier, as it appears in the version portion of the url. This values changes when the resource is created, updated, or deleted.")<a name="Resource.meta.versionId"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy"/><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[id](datatypes.html#id)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Version specific identifier</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck110.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vline.png)![.](tbl_vjoin.png)![.](icon_primitive.png "Primitive Data Type") [lastUpdated](resource-definitions.html#Resource.meta.lastUpdated "When the resource last changed - e.g. when the version changed.")<a name="Resource.meta.lastUpdated"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy"/><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[instant](datatypes.html#instant)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">When the resource version last changed</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck110.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vline.png)![.](tbl_vjoin.png)![.](icon_primitive.png "Primitive Data Type") [profile](resource-definitions.html#Resource.meta.profile "A list of profiles that this resource claims to conform to. The URL is a reference to Profile.url.")<a name="Resource.meta.profile"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy"/><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..*</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[uri](datatypes.html#uri)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Profiles this resource claims to conform to</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck110.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vline.png)![.](tbl_vjoin.png)![.](icon_datatype.gif "Data Type") [security](resource-definitions.html#Resource.meta.security "Security labels applied to this resource. These tags connect specific resources to the overall security policy and infrastructure.")<a name="Resource.meta.security"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy"/><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..*</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[Coding](datatypes.html#Coding)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Security Labels applied to this resource</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck100.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vline.png)![.](tbl_vjoin_end.png)![.](icon_datatype.gif "Data Type") [tag](resource-definitions.html#Resource.meta.tag "Tags applied to this resource. Tags are intended to to be used to identify and relate resources to process and workflow, and applications are not required to consider the tags when interpreting the meaning of a resource.")<a name="Resource.meta.tag"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy"/><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..*</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[Coding](datatypes.html#Coding)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Tags applied</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_primitive.png "Primitive Data Type") [implicitRules](resource-definitions.html#Resource.implicitRules "A reference to a set of rules that were followed when the resource was constructed, and which must be understood when processing the content.")<a name="Resource.implicitRules"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy"><span title="This element is a modifier element">M</span></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[uri](datatypes.html#uri)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">A set of rules under which this content was created</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck00.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin_end.png)![.](icon_primitive.png "Primitive Data Type") [language](resource-definitions.html#Resource.language "The base language in which the resource is written.")<a name="Resource.language"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy"/><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[code](datatypes.html#code)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Language of the resource content
[Language](http://tools.ietf.org/html/bcp47 "A human language") ([Required](terminologies.html#code "One of the the defined codes must be used"))</td></tr>
</table>
      </div>
    </div>
  </div>
  <div id="tabs-uml"> 
    <div id="uml">

**UML Diagram**

      <div id="uml-inner">
        <svg height="126.0" width="512.0" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns="http://www.w3.org/2000/svg" version="1.1">  <defs>
    <filter id="shadow" height="200%" width="200%" y="0" x="0">
      <feOffset result="offOut" dx="3" dy="3" in="SourceGraphic"/>
      <feColorMatrix result="matrixOut" values="0.2 0 0 0 0 0 0.2 0 0 0 0 0 0.2 0 0 0 0 0 1 0" type="matrix" in="offOut"/>
      <feGaussianBlur result="blurOut" stdDeviation="2" in="matrixOut"/>
      <feBlend in2="blurOut" in="SourceGraphic" mode="normal"/>
    </filter>
  </defs><rect height="78.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="140.0" filter="url(#shadow)" rx="4" y="0.0" ry="4" x="0.0"/><line style="stroke:dimgrey;stroke-width:1" y1="28.0" y2="28.0" x2="140.0" x1="0.0"/><text fill="black" class="diagram-class-title  diagram-class-resource" y="20.0" x="70.0">Resource «Resource»</text><text fill="black" class="diagram-class-detail" y="42.0" x="6.0">[<title>The logical id of the resource, as used in the url for the resoure. Once assigned, this value never changes</title>id](resource-definitions.html#Resource.id) : [id](datatypes.html#id) 0..1</text><text fill="black" class="diagram-class-detail" y="56.0" x="6.0">[<title>A reference to a set of rules that were followed when the resource was constructed, and which must be understood when processing the content (this element modifies the meaning of other elements)</title>implicitRules](resource-definitions.html#Resource.implicitRules) : [uri](datatypes.html#uri) 0..1</text><text fill="black" class="diagram-class-detail" y="70.0" x="6.0">[<title>The base language in which the resource is written</title>language](resource-definitions.html#Resource.language) : [code](datatypes.html#code) 0..1 « [<title>A human language</title>Language](http://tools.ietf.org/html/bcp47) »</text><rect height="106.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="112.0" filter="url(#shadow)" rx="4" y="0.0" ry="4" x="200.0"/><line style="stroke:dimgrey;stroke-width:1" y1="28.0" y2="28.0" x2="312.0" x1="200.0"/><text fill="black" class="diagram-class-title" y="20.0" x="256.0">Meta</text><text fill="black" class="diagram-class-detail" y="42.0" x="206.0">[<title>The version specific identifier, as it appears in the version portion of the url. This values changes when the resource is created, updated, or deleted</title>versionId](resource-definitions.html#Resource.meta.versionId) : [id](datatypes.html#id) 0..1</text><text fill="black" class="diagram-class-detail" y="56.0" x="206.0">[<title>When the resource last changed - e.g. when the version changed</title>lastUpdated](resource-definitions.html#Resource.meta.lastUpdated) : [instant](datatypes.html#instant) 0..1</text><text fill="black" class="diagram-class-detail" y="70.0" x="206.0">[<title>A list of profiles that this resource claims to conform to. The URL is a reference to Profile.url</title>profile](resource-definitions.html#Resource.meta.profile) : [uri](datatypes.html#uri) 0..*</text><text fill="black" class="diagram-class-detail" y="84.0" x="206.0">[<title>Security labels applied to this resource. These tags connect specific resources to the overall security policy and infrastructure</title>security](resource-definitions.html#Resource.meta.security) : [Coding](datatypes.html#Coding) 0..*</text><text fill="black" class="diagram-class-detail" y="98.0" x="206.0">[<title>Tags applied to this resource. Tags are intended to to be used to identify and relate resources to process and workflow, and applications are not required to consider the tags when interpreting the meaning of a resource</title>tag](resource-definitions.html#Resource.meta.tag) : [Coding](datatypes.html#Coding) 0..*</text><line style="stroke:navy;stroke-width:1" y1="44.26881720430108" y2="48.78494623655914" x2="200.0" x1="140.0"/><polygon transform="rotate(4.3044689605079824 140.0 44.26881720430108)" style="fill:navy;stroke:navy;stroke-width:1" points="140.0,44.26881720430108 146.0,48.26881720430108 152.0,44.26881720430108 146.0,40.26881720430108 140.0,44.26881720430108"/><rect height="18.0" style="fill:white;stroke:black;stroke-width:0" width="16.0" y="39.0" x="162.0"/><text fill="black" class="diagram-class-linkage" y="49.0" x="170.0">[<title>The metadata about the resource. This is content that is maintained by the infrastructure. Changes to the content may not always be associated with version changes to the resource</title>meta](resource-definitions.html#Resource.meta)</text><text fill="black" class="diagram-class-linkage" y="44.78494623655914" x="180.0">0..1</text></svg>
      </div>
    </div>
  </div>
  <div id="tabs-xml">
    <div id="xml">

**XML Template**

      <div id="xml-inner">
        <pre class="spec">
&lt;[**[name]**](resource-definitions.html#Resource "Base Resource for everything.") xmlns=&quot;http://hl7.org/fhir&quot;&gt; <span style="float: right">[![doco](help.png)](formats.html "Documentation for this format")</span>
 &lt;!-- from Element: [extension](extensibility.html) --&gt;
 &lt;[**id**](resource-definitions.html#Resource.id "The logical id of the resource, as used in the url for the resoure. Once assigned, this value never changes.") value=&quot;[<span style="color: darkgreen">[id](datatypes.html#id)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..1**</span> <span style="color: navy">Logical id of this artefact</span><span style="color: Gray"> --&gt;</span>
 &lt;[**meta**](resource-definitions.html#Resource.meta "The metadata about the resource. This is content that is maintained by the infrastructure. Changes to the content may not always be associated with version changes to the resource.")&gt;  <span style="color: Gray">&lt;!-- <span style="color: brown">**0..1**</span> Metadata about the resource --&gt;</span>
  &lt;[**versionId**](resource-definitions.html#Resource.meta.versionId "The version specific identifier, as it appears in the version portion of the url. This values changes when the resource is created, updated, or deleted.") value=&quot;[<span style="color: darkgreen">[id](datatypes.html#id)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..1**</span> <span style="color: navy">Version specific identifier</span><span style="color: Gray"> --&gt;</span>
  &lt;[**lastUpdated**](resource-definitions.html#Resource.meta.lastUpdated "When the resource last changed - e.g. when the version changed.") value=&quot;[<span style="color: darkgreen">[instant](datatypes.html#instant)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..1**</span> <span style="color: navy">When the resource version last changed</span><span style="color: Gray"> --&gt;</span>
  &lt;[**profile**](resource-definitions.html#Resource.meta.profile "A list of profiles that this resource claims to conform to. The URL is a reference to Profile.url.") value=&quot;[<span style="color: darkgreen">[uri](datatypes.html#uri)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..***</span> <span style="color: navy">Profiles this resource claims to conform to</span><span style="color: Gray"> --&gt;</span>
  &lt;[**security**](resource-definitions.html#Resource.meta.security "Security labels applied to this resource. These tags connect specific resources to the overall security policy and infrastructure.")&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..***</span> <span style="color: darkgreen">[Coding](datatypes.html#Coding)</span> <span style="color: navy">Security Labels applied to this resource</span><span style="color: Gray"> --&gt;</span>&lt;/security&gt;
  &lt;[**tag**](resource-definitions.html#Resource.meta.tag "Tags applied to this resource. Tags are intended to to be used to identify and relate resources to process and workflow, and applications are not required to consider the tags when interpreting the meaning of a resource.")&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..***</span> <span style="color: darkgreen">[Coding](datatypes.html#Coding)</span> <span style="color: navy">Tags applied</span><span style="color: Gray"> --&gt;</span>&lt;/tag&gt;
 &lt;/meta&gt;
 &lt;[<span style="text-decoration: underline">**implicitRules**</span>](resource-definitions.html#Resource.implicitRules "A reference to a set of rules that were followed when the resource was constructed, and which must be understood when processing the content (this element modifies the meaning of other elements)") value=&quot;[<span style="color: darkgreen">[uri](datatypes.html#uri)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..1**</span> <span style="color: navy">A set of rules under which this content was created</span><span style="color: Gray"> --&gt;</span>
 &lt;[**language**](resource-definitions.html#Resource.language "The base language in which the resource is written.") value=&quot;[<span style="color: darkgreen">[code](datatypes.html#code)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..1**</span> <span style="color: navy">[Language of the resource content](http://tools.ietf.org/html/bcp47.html)</span><span style="color: Gray"> --&gt;</span>
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
        <table style="border: 0px; font-size: 11px; font-family: verdana; vertical-align: top;" cellpadding="0" border="0" cellspacing="0"><tr style="border: 1px #F0F0F0 solid; font-size: 11px; font-family: verdana; vertical-align: top;"><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Name</th><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Flags</th><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Card.</th><th style="width: 100px" class="heirarchy">Type</th><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Description &amp; Constraints<span style="float: right">[![doco](help16.png)](formats.html#table "Legend for this format")</span></th></tr><tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck1.png)" class="heirarchy">![.](tbl_spacer.png)![.](icon_resource.png "Resource") [Resource](resource-definitions.html#Resource "Base Resource for everything.")<a name="Resource"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy"/><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy"/><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">n/a</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Base Resource</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_primitive.png "Primitive Data Type") [id](resource-definitions.html#Resource.id "The logical id of the resource, as used in the url for the resoure. Once assigned, this value never changes.")<a name="Resource.id"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy"/><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[id](datatypes.html#id)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Logical id of this artefact</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck11.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_element.gif "Element") [meta](resource-definitions.html#Resource.meta "The metadata about the resource. This is content that is maintained by the infrastructure. Changes to the content may not always be associated with version changes to the resource.")<a name="Resource.meta"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy"/><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[Element](element.html)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Metadata about the resource</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck110.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vline.png)![.](tbl_vjoin.png)![.](icon_primitive.png "Primitive Data Type") [versionId](resource-definitions.html#Resource.meta.versionId "The version specific identifier, as it appears in the version portion of the url. This values changes when the resource is created, updated, or deleted.")<a name="Resource.meta.versionId"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy"/><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[id](datatypes.html#id)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Version specific identifier</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck110.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vline.png)![.](tbl_vjoin.png)![.](icon_primitive.png "Primitive Data Type") [lastUpdated](resource-definitions.html#Resource.meta.lastUpdated "When the resource last changed - e.g. when the version changed.")<a name="Resource.meta.lastUpdated"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy"/><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[instant](datatypes.html#instant)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">When the resource version last changed</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck110.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vline.png)![.](tbl_vjoin.png)![.](icon_primitive.png "Primitive Data Type") [profile](resource-definitions.html#Resource.meta.profile "A list of profiles that this resource claims to conform to. The URL is a reference to Profile.url.")<a name="Resource.meta.profile"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy"/><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..*</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[uri](datatypes.html#uri)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Profiles this resource claims to conform to</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck110.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vline.png)![.](tbl_vjoin.png)![.](icon_datatype.gif "Data Type") [security](resource-definitions.html#Resource.meta.security "Security labels applied to this resource. These tags connect specific resources to the overall security policy and infrastructure.")<a name="Resource.meta.security"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy"/><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..*</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[Coding](datatypes.html#Coding)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Security Labels applied to this resource</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck100.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vline.png)![.](tbl_vjoin_end.png)![.](icon_datatype.gif "Data Type") [tag](resource-definitions.html#Resource.meta.tag "Tags applied to this resource. Tags are intended to to be used to identify and relate resources to process and workflow, and applications are not required to consider the tags when interpreting the meaning of a resource.")<a name="Resource.meta.tag"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy"/><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..*</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[Coding](datatypes.html#Coding)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Tags applied</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_primitive.png "Primitive Data Type") [implicitRules](resource-definitions.html#Resource.implicitRules "A reference to a set of rules that were followed when the resource was constructed, and which must be understood when processing the content.")<a name="Resource.implicitRules"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy"><span title="This element is a modifier element">M</span></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[uri](datatypes.html#uri)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">A set of rules under which this content was created</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck00.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin_end.png)![.](icon_primitive.png "Primitive Data Type") [language](resource-definitions.html#Resource.language "The base language in which the resource is written.")<a name="Resource.language"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy"/><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[code](datatypes.html#code)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Language of the resource content
[Language](http://tools.ietf.org/html/bcp47 "A human language") ([Required](terminologies.html#code "One of the the defined codes must be used"))</td></tr>
</table>
      </div>
    </div>
    <div id="uml">
      <a name="uml"> </a>

**UML Diagram**

      <div id="uml-inner">
        <svg height="126.0" width="512.0" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns="http://www.w3.org/2000/svg" version="1.1">  <defs>
    <filter id="shadow" height="200%" width="200%" y="0" x="0">
      <feOffset result="offOut" dx="3" dy="3" in="SourceGraphic"/>
      <feColorMatrix result="matrixOut" values="0.2 0 0 0 0 0 0.2 0 0 0 0 0 0.2 0 0 0 0 0 1 0" type="matrix" in="offOut"/>
      <feGaussianBlur result="blurOut" stdDeviation="2" in="matrixOut"/>
      <feBlend in2="blurOut" in="SourceGraphic" mode="normal"/>
    </filter>
  </defs><rect height="78.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="140.0" filter="url(#shadow)" rx="4" y="0.0" ry="4" x="0.0"/><line style="stroke:dimgrey;stroke-width:1" y1="28.0" y2="28.0" x2="140.0" x1="0.0"/><text fill="black" class="diagram-class-title  diagram-class-resource" y="20.0" x="70.0">Resource «Resource»</text><text fill="black" class="diagram-class-detail" y="42.0" x="6.0">[<title>The logical id of the resource, as used in the url for the resoure. Once assigned, this value never changes</title>id](resource-definitions.html#Resource.id) : [id](datatypes.html#id) 0..1</text><text fill="black" class="diagram-class-detail" y="56.0" x="6.0">[<title>A reference to a set of rules that were followed when the resource was constructed, and which must be understood when processing the content (this element modifies the meaning of other elements)</title>implicitRules](resource-definitions.html#Resource.implicitRules) : [uri](datatypes.html#uri) 0..1</text><text fill="black" class="diagram-class-detail" y="70.0" x="6.0">[<title>The base language in which the resource is written</title>language](resource-definitions.html#Resource.language) : [code](datatypes.html#code) 0..1 « [<title>A human language</title>Language](http://tools.ietf.org/html/bcp47) »</text><rect height="106.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="112.0" filter="url(#shadow)" rx="4" y="0.0" ry="4" x="200.0"/><line style="stroke:dimgrey;stroke-width:1" y1="28.0" y2="28.0" x2="312.0" x1="200.0"/><text fill="black" class="diagram-class-title" y="20.0" x="256.0">Meta</text><text fill="black" class="diagram-class-detail" y="42.0" x="206.0">[<title>The version specific identifier, as it appears in the version portion of the url. This values changes when the resource is created, updated, or deleted</title>versionId](resource-definitions.html#Resource.meta.versionId) : [id](datatypes.html#id) 0..1</text><text fill="black" class="diagram-class-detail" y="56.0" x="206.0">[<title>When the resource last changed - e.g. when the version changed</title>lastUpdated](resource-definitions.html#Resource.meta.lastUpdated) : [instant](datatypes.html#instant) 0..1</text><text fill="black" class="diagram-class-detail" y="70.0" x="206.0">[<title>A list of profiles that this resource claims to conform to. The URL is a reference to Profile.url</title>profile](resource-definitions.html#Resource.meta.profile) : [uri](datatypes.html#uri) 0..*</text><text fill="black" class="diagram-class-detail" y="84.0" x="206.0">[<title>Security labels applied to this resource. These tags connect specific resources to the overall security policy and infrastructure</title>security](resource-definitions.html#Resource.meta.security) : [Coding](datatypes.html#Coding) 0..*</text><text fill="black" class="diagram-class-detail" y="98.0" x="206.0">[<title>Tags applied to this resource. Tags are intended to to be used to identify and relate resources to process and workflow, and applications are not required to consider the tags when interpreting the meaning of a resource</title>tag](resource-definitions.html#Resource.meta.tag) : [Coding](datatypes.html#Coding) 0..*</text><line style="stroke:navy;stroke-width:1" y1="44.26881720430108" y2="48.78494623655914" x2="200.0" x1="140.0"/><polygon transform="rotate(4.3044689605079824 140.0 44.26881720430108)" style="fill:navy;stroke:navy;stroke-width:1" points="140.0,44.26881720430108 146.0,48.26881720430108 152.0,44.26881720430108 146.0,40.26881720430108 140.0,44.26881720430108"/><rect height="18.0" style="fill:white;stroke:black;stroke-width:0" width="16.0" y="39.0" x="162.0"/><text fill="black" class="diagram-class-linkage" y="49.0" x="170.0">[<title>The metadata about the resource. This is content that is maintained by the infrastructure. Changes to the content may not always be associated with version changes to the resource</title>meta](resource-definitions.html#Resource.meta)</text><text fill="black" class="diagram-class-linkage" y="44.78494623655914" x="180.0">0..1</text></svg>
      </div>
    </div>
    <div id="xml">
      <a name="xml"> </a>

**XML Template**

      <div id="xml-inner">
        <pre class="spec">
&lt;[**[name]**](resource-definitions.html#Resource "Base Resource for everything.") xmlns=&quot;http://hl7.org/fhir&quot;&gt; <span style="float: right">[![doco](help.png)](formats.html "Documentation for this format")</span>
 &lt;!-- from Element: [extension](extensibility.html) --&gt;
 &lt;[**id**](resource-definitions.html#Resource.id "The logical id of the resource, as used in the url for the resoure. Once assigned, this value never changes.") value=&quot;[<span style="color: darkgreen">[id](datatypes.html#id)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..1**</span> <span style="color: navy">Logical id of this artefact</span><span style="color: Gray"> --&gt;</span>
 &lt;[**meta**](resource-definitions.html#Resource.meta "The metadata about the resource. This is content that is maintained by the infrastructure. Changes to the content may not always be associated with version changes to the resource.")&gt;  <span style="color: Gray">&lt;!-- <span style="color: brown">**0..1**</span> Metadata about the resource --&gt;</span>
  &lt;[**versionId**](resource-definitions.html#Resource.meta.versionId "The version specific identifier, as it appears in the version portion of the url. This values changes when the resource is created, updated, or deleted.") value=&quot;[<span style="color: darkgreen">[id](datatypes.html#id)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..1**</span> <span style="color: navy">Version specific identifier</span><span style="color: Gray"> --&gt;</span>
  &lt;[**lastUpdated**](resource-definitions.html#Resource.meta.lastUpdated "When the resource last changed - e.g. when the version changed.") value=&quot;[<span style="color: darkgreen">[instant](datatypes.html#instant)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..1**</span> <span style="color: navy">When the resource version last changed</span><span style="color: Gray"> --&gt;</span>
  &lt;[**profile**](resource-definitions.html#Resource.meta.profile "A list of profiles that this resource claims to conform to. The URL is a reference to Profile.url.") value=&quot;[<span style="color: darkgreen">[uri](datatypes.html#uri)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..***</span> <span style="color: navy">Profiles this resource claims to conform to</span><span style="color: Gray"> --&gt;</span>
  &lt;[**security**](resource-definitions.html#Resource.meta.security "Security labels applied to this resource. These tags connect specific resources to the overall security policy and infrastructure.")&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..***</span> <span style="color: darkgreen">[Coding](datatypes.html#Coding)</span> <span style="color: navy">Security Labels applied to this resource</span><span style="color: Gray"> --&gt;</span>&lt;/security&gt;
  &lt;[**tag**](resource-definitions.html#Resource.meta.tag "Tags applied to this resource. Tags are intended to to be used to identify and relate resources to process and workflow, and applications are not required to consider the tags when interpreting the meaning of a resource.")&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..***</span> <span style="color: darkgreen">[Coding](datatypes.html#Coding)</span> <span style="color: navy">Tags applied</span><span style="color: Gray"> --&gt;</span>&lt;/tag&gt;
 &lt;/meta&gt;
 &lt;[<span style="text-decoration: underline">**implicitRules**</span>](resource-definitions.html#Resource.implicitRules "A reference to a set of rules that were followed when the resource was constructed, and which must be understood when processing the content (this element modifies the meaning of other elements)") value=&quot;[<span style="color: darkgreen">[uri](datatypes.html#uri)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..1**</span> <span style="color: navy">A set of rules under which this content was created</span><span style="color: Gray"> --&gt;</span>
 &lt;[**language**](resource-definitions.html#Resource.language "The base language in which the resource is written.") value=&quot;[<span style="color: darkgreen">[code](datatypes.html#code)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..1**</span> <span style="color: navy">[Language of the resource content](http://tools.ietf.org/html/bcp47.html)</span><span style="color: Gray"> --&gt;</span>
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

### <span class="sectioncount">null.3.1<a name="null.3.1"> </a></span> 
Terminology Bindings

<table class="grid">
 <tr><th>Path</th><th>Definition</th><th>Type</th><th>Reference</th></tr>
 <tr><td title="Language" valign="top">Resource.language </td><td valign="top">A human language</td><td>[Fixed](terminologies.html#code)</td><td valign="top">[IETF language tag](http://tools.ietf.org/html/bcp47)  <!-- g --></td> </tr>
</table>

<a name="id"> </a>

### <span class="sectioncount">null.3.2<a name="null.3.2"> </a></span> Resource Identity

Each resource has an &quot;id&quot; element which contains the logical identity of the resource 
assigned by the server responsible for storing it. Resources always have a known identity
except for the special case when a new resources is being sent to a server to assign
an identity ([create interaction](http.html#create)). 
The logical identity is unique within the space of all resources of the same type on 
the same server. Once assigned, the identity is never changed, though copies of the 
same resource made elsewhere may not retain the same identity.

The full identity of a resource is an absolute URL constructed from the server base address at 
which it is found, the resource type, and the Logical Id, such as http://test.fhir.org/rest/Patient/123 
(where 123 is the Logical Id). Note that implementations SHOULD NOT assume that the identity of a resource 
is always resolvable to a literal server - it may be temporarily unavailable, or not available by policy (e.g. firewalls) or in some 
cases, it may not actually exist (e.g. use of resource outside a RESTful environment). Resources reference each other by their identity. 
These references are allowed to be absolute or relative (see [Resource References](references.html) for further discussion).
Copying or moving resources from one server to another means that resources acquire a new identity. For further details, 
see [Managing Resource Identity](managing.html).

Logical ids are case sensitive. Ids are always opaque, and external systems need not and should not 
attempt to determine their internal structure. An id SHALL always be represented in the same way in 
resource references and URLs. Ids can be up to 36 characters long, and contain any combination of 
upper and lowercase ASCII letters, numerals, &quot;-&quot; and &quot;.&quot;. 

<a name="metadata"> </a>
<a name="meta"> </a>

### <span class="sectioncount">null.3.3<a name="null.3.3"> </a></span> Resource Metadata

Each resource contains a set of meta data that provide technical and workflow 
context to the resource. The metadata items are all optional, though some of all
of them may be required in particular implementations.

<table class="grid">
  <tr>
    <th>Metadata Item</th>
    <th>Type</th>
    <th>Usage</th>
  </tr>
  <tr>
    <td>versionId (0..1)</td>
    <td>[id](datatypes.html#id)</td>
    <td>Changes each time the content of the resource changes. Can be referenced in a [resource reference](references.html#Resource). 
      Can be used to ensure that updates are based on the latest version of the resource. 

The version can be globally unique, or scoped by the Logical Id of the resource. 
     Version identifiers are generally either a serially incrementing id scoped by the logical id, or a uuid, though neither of these approaches 
     is required. Note that servers SHOULD support versions, but some are unable to</td>
  </tr>

  <tr>
   <td>lastUpdated (0..1)</td>
   <td>[instant](datatypes.html#instant)</td>
   <td>If populated, this value changes each time the content of the resource 
    changes. it can be used by a system or a human to judge the currency of the resource content. 
    Note that [version aware updates](http.html#update) do not use this element</td>
  </tr>

  <tr>
   <td>profile (0..*)</td>
   <td>[uri](datatypes.html#uri)</td>
   <td>An assertion that the content conforms to a profile. See [Extending and Restricting Resources](profiling.html#resources) for further discussion. 
    Can be changed as profiles and value sets change or the system rechecks conformance</td>
  </tr>

  <tr>
   <td>security (0..*)</td>
   <td>[Coding](datatypes.html#Coding)</td>
   <td>[Security labels](security-labels.html) applied to this resource. These tags connect resources in specific ways to 
    the overall security policy and infrastructure. Security tags can be updated when the resource changes, or whenever the security sub-system chooses to</td>
  </tr>

  <tr>
   <td>tag (0..*)</td>
   <td>[Coding](datatypes.html#Coding)</td>
   <td>[Tags](extras.html) applied to this resource. Tags are used to relate resources to process and workflow. Applications are not required to consider 
    the tags when interpreting the meaning of a resource.</td>
  </tr>

</table>

The profile, security, and tag elements can be changed by [a meta interaction](http.html#meta) without changing the resource version.

<a name="implicitRules"> </a>

### <span class="sectioncount">null.3.4<a name="null.3.4"> </a></span> Implicit Rules

A reference to a [custom agreement](profiling.html#agreement) about how the resources are used 
that was followed when the resource was constructed, and which must be understood when processing the content.

Asserting this rule set restricts the content to be only understood by a limited set of 
trading partners. This inherently limits the usefulness of the data in the long term,
and should be avoided where possible. However the existing health 
eco-system is highly fractured, and not yet ready to define, collect, and exchange 
data in a generally exchangeable sense. 

Note that resources are almost always constructed following some custom agreement.
Best practice is that such agreements make all knowledge about the content 
of the resource explicit; if custom agreements do this, and declare their extensions
as required, then it is not necessary to understand the agreement when processing the 
resource content.

<a name="lang"> </a>
<a name="language"> </a>

### <span class="sectioncount">null.3.5<a name="null.3.5"> </a></span> Language

Each resource may have a language element that specifies the base language of the content using a [code defined in BCP 47](http://tools.ietf.org/html/bcp47).
The language element is provided to support indexing and accessibility (e.g. text-to-speech use the language tag). 

There is no default language, though one may be inferred from the context of use.
Not all of the content of the resource has to be in the specified language. 

If a language is specified, it should also be specified on the [Narrative Text](narrative.html#Narrative). 
The html language tag in the narrative is used when processing the narrative. The language tag on the resource is provided 
for use to specify the language of alternate presentations generated from the data in the resource

<a name="tags"> </a>
<a name="tag"> </a>

### <span class="sectioncount">null.3.6<a name="null.3.6"> </a></span> Tags, Profiles, and Security Labels

These 3 metadata attributes are part of the resource, but are never used to keep information 
that needs to be understood when interpreting the content of a resource; their 
function is limited to finding and controlling access to the resource, and connecting 
resources to technical or clinical workflow.

#### <span class="sectioncount">null.3.6.1<a name="null.3.6.1"> </a></span> Tags

Tags are used to associate additional operational information with the Resources, including
such as workflow management. A typical use of tagging would be to maintain an informal list
of resources that need review.

In a general tag, the [concept](datatypes.html#coding) may be a reference to a 
healthcare vocabulary, including ones defined in this specification, or vocabularies such 
as those defined by HL7 for other purposes (e.g. v2 and v3/CDA), LOINC, or SNOMED CT. 
Alternatively, the concept may be one defined by the implementation in the local context. 

<a name="profile-tags"> </a>

#### <span class="sectioncount">null.3.6.2<a name="null.3.6.2"> </a></span> Profile Tags

A profile assertion represents a claim that the resource conforms to [the identified profile](profile.html),
which makes sets of rules about what 
content is allowed to be in a resource. In a profile tag, the term
is a URL that references a profile resource.

It's always possible to determine whether a resource conforms to a 
profile simply by testing it against the profile (the [validation tools](downloads.html)
provide the functionality to perform this test in a variety of contexts). 
However there are several circumstances where simply examining whether 
a resource conforms to a particular profile as needed is impractical:

*   A server searching a set of resources for ones that conform to a particular profile
*   A receiver that has many profiles to choose when validating resource

Profile Tags serve these use cases - a client/creator of a resource can tag the 
resource with an assertion that the resource conforms to a profile. The server/receiver
of the resource can choose to take this assertion at face value, or to assist in locating
the profile against which to validate the resource. 

Note: resources can conform to multiple profiles at once. A resource can conform to 
a profile without ever being labelled that it does, or a resource may falsely claim to conform 
to a profile. For this reason, applications processing resources SHOULD always 
depend on the contents of the resource when processing them, and/or check resources
against profiles directly rather than relying the existence of profile tags.
Many trading partner agreements will make rules about what claims can be made 
and when they must be tested, which will make the profile assertion more reliable. 

Profile Tags are provided as a method of finding resources that conform to 
a particular profile, not statements of meaning about the resource.

#### <span class="sectioncount">null.3.6.3<a name="null.3.6.3"> </a></span> Security Labels

A security label is attached to a resource to provide specific security metadata 
about the information in the resource. For further information, see 
[Security Labels](security-labels.html).

### <span class="sectioncount">null.3.7<a name="null.3.7"> </a></span> Further Information

*   [Conformance Rules](conformance-rules.html)
*   [Resource Definitions](resources.html)
*   [References between Resources](references.html)
*   [Narratives](narrative.html)
*   [Formats:](formats.html) [XML](xml.html), [JSON](json.html)*   [Extensibility](extensibility.html) ([Examples](extensibility-examples.html))
*   [Detailed Descriptions](resource-definitions.html)
*   [Inter-version Compatibility](compatibility.html)

<a name="search"> </a>

## <span class="sectioncount">null.4<a name="null.4"> </a></span> Search Parameters

Common search parameters defined by this resource. See [Searching](search.html) for more information about searching in REST, messaging, and services.

<table class="list">
<tr><td>**Name**</td><td>**Type**</td><td>**Description**</td><td>**Paths**</td></tr>
<tr><td>_id</td><td>[token](search.html#token)</td><td>Logical id of this artefact</td><td>Resource.id</td></tr>
<tr><td>_language</td><td>[token](search.html#token)</td><td>Language of the resource content</td><td>Resource.language</td></tr>
<tr><td>_lastUpdated</td><td>[date](search.html#date)</td><td>When the resource version last changed</td><td>Resource.meta.lastUpdated</td></tr>
<tr><td>_profile</td><td>[token](search.html#token)</td><td>Profiles this resource claims to conform to</td><td>Resource.meta.profile</td></tr>
<tr><td>_security</td><td>[token](search.html#token)</td><td>Security Labels applied to this resource</td><td>Resource.meta.security</td></tr>
<tr><td>_tag</td><td>[token](search.html#token)</td><td>Tags applied</td><td>Resource.meta.tag</td></tr>
</table>

</div>