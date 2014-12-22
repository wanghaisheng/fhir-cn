title: 
date: 
categories: infra
---

*   [Content](#)
*   [Examples](binary-examples.html)
*   [Detailed Descriptions](binary-definitions.html)
*   [Mappings](binary-mappings.html)
*   [Conformance Packages](binary-packages.html)

# <span class="sectioncount">6.7<a name="6.7"> </a></span> Resource Binary - Content

  <!-- 

Status: null
 -->

This resource cultivated by the [FHIR Management Group](http://www.hl7.org/Special/committees/fhirmg/index.cfm) Work Group

A binary resource can contain any content, whether text, image, pdf, zip archive, etc. 

<div>

## <span class="sectioncount">6.7.1<a name="6.7.1"> </a></span> Scope and Usage

There are situations where it is useful or required to handle pure binary content using the same framework as other 
resources. Typically, this is when the binary content is referred to from other FHIR Resources. 
Using the same framework means that the existing servers, security arrangements, code libraries etc. 
can handle additional related content. Typically, Binary resources are used for handling content such as:

*   CDA Documents (i.e. with XDS)
*   PDF Documents
*   Images (the Media resource is preferred for handling images, but not possible when the content is already binary - XDS)

A binary resource can contain any content, whether text, image, pdf, zip archive, etc. These 
resources are served in their native form on the rest interface, but can also be represented in XML or JSON, 
such as when including these resources in a bundle (used when it is convenient to include these in the 
feed directly rather than leaving them by reference).

</div>

<div>

## <span class="sectioncount">6.7.2<a name="6.7.2"> </a></span> Boundaries and Relationships

This resource is generally used as the target of a [Document Reference](documentreference.html) or an [Attachment](datatypes.html#Attachment), when a FHIR server finds it convenient to manage the content within the same overall REST framework as the other resources.

</div>

This resource is referenced by [[DocumentManifest]](documentmanifest.html)

<a name="resource"/>

## <span class="sectioncount">6.7.3<a name="6.7.3"> </a></span> 
Resource Content

<a name="def"> </a>
<a name="binary"> </a>
<a name="Binary"> </a>

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
  <table style="border: 0px; font-size: 11px; font-family: verdana; vertical-align: top;" cellpadding="0" border="0" cellspacing="0"><tr style="border: 1px #F0F0F0 solid; font-size: 11px; font-family: verdana; vertical-align: top;"><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Name</th><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Flags</th><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Card.</th><th style="width: 100px" class="heirarchy">Type</th><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Description &amp; Constraints<span style="float: right">[![doco](help16.png)](formats.html#table "Legend for this format")</span></th></tr><tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck1.png)" class="heirarchy">![.](tbl_spacer.png)![.](icon_resource.png "Resource") [Binary](binary-definitions.html#Binary "A binary resource can contain any content, whether text, image, pdf, zip archive, etc.")<a name="Binary"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy"/><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy"/><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[Resource](resource.html)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Pure binary content defined by sime other format than FHIR</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_primitive.png "Primitive Data Type") [contentType](binary-definitions.html#Binary.contentType "MimeType of the binary content represented as a standard MimeType (BCP 13).")<a name="Binary.contentType"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy"/><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">1..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[code](datatypes.html#code)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">MimeType of the binary content
[MimeType](http://www.rfc-editor.org/bcp/bcp13.txt "The mime type of an attachment") ([Required](terminologies.html#code "One of the the defined codes must be used"))</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck00.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin_end.png)![.](icon_primitive.png "Primitive Data Type") [content](binary-definitions.html#Binary.content "The actual content, base64 encoded.")<a name="Binary.content"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy"/><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">1..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[base64Binary](datatypes.html#base64Binary)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">The actual content</td></tr>
</table>
 </div>
</div>

  </div>
  <div id="tabs-uml">

<div id="uml">

**UML Diagram**

 <div id="uml-inner">
 <svg height="74.0" width="252.0" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns="http://www.w3.org/2000/svg" version="1.1">  <defs>
    <filter id="shadow" height="200%" width="200%" y="0" x="0">
      <feOffset result="offOut" dx="3" dy="3" in="SourceGraphic"/>
      <feColorMatrix result="matrixOut" values="0.2 0 0 0 0 0 0.2 0 0 0 0 0 0.2 0 0 0 0 0 1 0" type="matrix" in="offOut"/>
      <feGaussianBlur result="blurOut" stdDeviation="2" in="matrixOut"/>
      <feBlend in2="blurOut" in="SourceGraphic" mode="normal"/>
    </filter>
  </defs><rect height="64.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="152.0" filter="url(#shadow)" rx="4" y="0.0" ry="4" x="0.0"/><line style="stroke:dimgrey;stroke-width:1" y1="28.0" y2="28.0" x2="152.0" x1="0.0"/><text fill="black" class="diagram-class-title  diagram-class-resource" y="20.0" x="76.0">Binary<tspan class="diagram-class-title-link"> ([Resource](resource.html))</tspan></text><text fill="black" class="diagram-class-detail" y="42.0" x="6.0">[<title>MimeType of the binary content represented as a standard MimeType (BCP 13)</title>contentType](binary-definitions.html#Binary.contentType) : [code](datatypes.html#code) 1..1 « [<title>The mime type of an attachment</title>MimeType](http://www.rfc-editor.org/bcp/bcp13.txt) »</text><text fill="black" class="diagram-class-detail" y="56.0" x="6.0">[<title>The actual content, base64 encoded</title>content](binary-definitions.html#Binary.content) : [base64Binary](datatypes.html#base64Binary) 1..1</text></svg>
 </div>
</div>

  </div>
  <div id="tabs-xml">

<div id="xml">

**XML Template**

 <div id="xml-inner">
  <pre class="spec">
&lt;[**Binary**](binary-definitions.html#Binary "A binary resource can contain any content, whether text, image, pdf, zip archive, etc.") xmlns=&quot;http://hl7.org/fhir&quot;&gt; <span style="float: right">[![doco](help.png)](formats.html "Documentation for this format")</span>
 &lt;!-- from [Resource](resource.html): [id](resource.html#id), [meta](resource.html#meta), [implicitRules](resource.html#implicitRules), and [language](resource.html#language) --&gt;
 &lt;[**contentType**](binary-definitions.html#Binary.contentType "MimeType of the binary content represented as a standard MimeType (BCP 13).") value=&quot;[<span style="color: darkgreen">[code](datatypes.html#code)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**1..1**</span> <span style="color: navy">[MimeType of the binary content](http://www.rfc-editor.org/bcp/bcp13.txt.html)</span><span style="color: Gray"> --&gt;</span>
 &lt;[**content**](binary-definitions.html#Binary.content "The actual content, base64 encoded.") value=&quot;[<span style="color: darkgreen">[base64Binary](datatypes.html#base64Binary)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**1..1**</span> <span style="color: navy">The actual content</span><span style="color: Gray"> --&gt;</span>
&lt;/Binary&gt;
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
  <table style="border: 0px; font-size: 11px; font-family: verdana; vertical-align: top;" cellpadding="0" border="0" cellspacing="0"><tr style="border: 1px #F0F0F0 solid; font-size: 11px; font-family: verdana; vertical-align: top;"><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Name</th><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Flags</th><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Card.</th><th style="width: 100px" class="heirarchy">Type</th><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Description &amp; Constraints<span style="float: right">[![doco](help16.png)](formats.html#table "Legend for this format")</span></th></tr><tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck1.png)" class="heirarchy">![.](tbl_spacer.png)![.](icon_resource.png "Resource") [Binary](binary-definitions.html#Binary "A binary resource can contain any content, whether text, image, pdf, zip archive, etc.")<a name="Binary"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy"/><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy"/><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[Resource](resource.html)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Pure binary content defined by sime other format than FHIR</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_primitive.png "Primitive Data Type") [contentType](binary-definitions.html#Binary.contentType "MimeType of the binary content represented as a standard MimeType (BCP 13).")<a name="Binary.contentType"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy"/><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">1..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[code](datatypes.html#code)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">MimeType of the binary content
[MimeType](http://www.rfc-editor.org/bcp/bcp13.txt "The mime type of an attachment") ([Required](terminologies.html#code "One of the the defined codes must be used"))</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck00.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin_end.png)![.](icon_primitive.png "Primitive Data Type") [content](binary-definitions.html#Binary.content "The actual content, base64 encoded.")<a name="Binary.content"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy"/><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">1..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[base64Binary](datatypes.html#base64Binary)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">The actual content</td></tr>
</table>
 </div>
</div>

<div id="uml">
<a name="uml"> </a>

**UML Diagram**

 <div id="uml-inner">
 <svg height="74.0" width="252.0" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns="http://www.w3.org/2000/svg" version="1.1">  <defs>
    <filter id="shadow" height="200%" width="200%" y="0" x="0">
      <feOffset result="offOut" dx="3" dy="3" in="SourceGraphic"/>
      <feColorMatrix result="matrixOut" values="0.2 0 0 0 0 0 0.2 0 0 0 0 0 0.2 0 0 0 0 0 1 0" type="matrix" in="offOut"/>
      <feGaussianBlur result="blurOut" stdDeviation="2" in="matrixOut"/>
      <feBlend in2="blurOut" in="SourceGraphic" mode="normal"/>
    </filter>
  </defs><rect height="64.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="152.0" filter="url(#shadow)" rx="4" y="0.0" ry="4" x="0.0"/><line style="stroke:dimgrey;stroke-width:1" y1="28.0" y2="28.0" x2="152.0" x1="0.0"/><text fill="black" class="diagram-class-title  diagram-class-resource" y="20.0" x="76.0">Binary<tspan class="diagram-class-title-link"> ([Resource](resource.html))</tspan></text><text fill="black" class="diagram-class-detail" y="42.0" x="6.0">[<title>MimeType of the binary content represented as a standard MimeType (BCP 13)</title>contentType](binary-definitions.html#Binary.contentType) : [code](datatypes.html#code) 1..1 « [<title>The mime type of an attachment</title>MimeType](http://www.rfc-editor.org/bcp/bcp13.txt) »</text><text fill="black" class="diagram-class-detail" y="56.0" x="6.0">[<title>The actual content, base64 encoded</title>content](binary-definitions.html#Binary.content) : [base64Binary](datatypes.html#base64Binary) 1..1</text></svg>
 </div>
</div>

<div id="xml">
<a name="xml"> </a>

**XML Template**

 <div id="xml-inner">
  <pre class="spec">
&lt;[**Binary**](binary-definitions.html#Binary "A binary resource can contain any content, whether text, image, pdf, zip archive, etc.") xmlns=&quot;http://hl7.org/fhir&quot;&gt; <span style="float: right">[![doco](help.png)](formats.html "Documentation for this format")</span>
 &lt;!-- from [Resource](resource.html): [id](resource.html#id), [meta](resource.html#meta), [implicitRules](resource.html#implicitRules), and [language](resource.html#language) --&gt;
 &lt;[**contentType**](binary-definitions.html#Binary.contentType "MimeType of the binary content represented as a standard MimeType (BCP 13).") value=&quot;[<span style="color: darkgreen">[code](datatypes.html#code)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**1..1**</span> <span style="color: navy">[MimeType of the binary content](http://www.rfc-editor.org/bcp/bcp13.txt.html)</span><span style="color: Gray"> --&gt;</span>
 &lt;[**content**](binary-definitions.html#Binary.content "The actual content, base64 encoded.") value=&quot;[<span style="color: darkgreen">[base64Binary](datatypes.html#base64Binary)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**1..1**</span> <span style="color: navy">The actual content</span><span style="color: Gray"> --&gt;</span>
&lt;/Binary&gt;
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

Alternate definitions: [Schema](binary.xsd)/[Schematron](binary.sch), 
Resource Profile ([XML](binary.profile.xml.html), [JSON](binary.profile.json.html)), 
[Questionnaire](binary.questionnaire.html)

<a name="tx"> </a>

### <span class="sectioncount">6.7.3.1<a name="6.7.3.1"> </a></span> 
Terminology Bindings

<table class="grid">
 <tr><th>Path</th><th>Definition</th><th>Type</th><th>Reference</th></tr>
 <tr><td title="MimeType" valign="top">Binary.contentType </td><td valign="top">The mime type of an attachment</td><td>[Fixed](terminologies.html#code)</td><td valign="top">[BCP 13 (RFCs 2045, 2046, 2047, 4288, 4289 and 2049)](http://www.rfc-editor.org/bcp/bcp13.txt)  <!-- g --></td> </tr>
</table>

<a name="rest"> </a>

### <span class="sectioncount">6.7.3.2<a name="6.7.3.2"> </a></span> Serving Binary Resources using the RESTful API

The Binary resources behaves slightly differently to all other resources on the RESTful API.
specifically, when a read request is made for the binary resource that doesn't explicitly
specify the FHIR content types &quot;application/xml+fhir&quot; or &quot;application/json+fhir&quot;, then 
the content should be returned using the content type stated in the resource. 
e.g. if the content type in the resource is &quot;application/pdf&quot;, then the content should
be returned as a PDF directly. 

Note that due to the way the web infrastructure works, it is not possible to make blanket
rules about the relationship between the &quot;Accept&quot; field in the http request, and the 
return type, which is why there is no hard rule about this. However the intent is that
unless specifically requested, the FHIR XML/JSON representation is not returned. 

Note that in the native binary representation, the metadata is not available directly,
though some of it is replicated in the HTTP response headers.

  <!-- <a name="binary"> </a>

### Binary Support

FHIR servers can choose to support [Binary Resources](extras.html#binary)
at the end point [base]/Binary. The binary end-point accepts
any kind of content, such as images and other media, documents (CDA, 
PDF, Word etc.), plain text, XML or anything else, and stores the 
content as is, along with the content type provided by the HTTP headers. 

Binary resources function with the same interactions as described
above. The _format  parameter has no meaning when used with binary 
resources: they are always represented using their original content type.

Note that on GET, POST, and PUT operations, the http content-type
header is the mime type of the binary resource, and the HTTP body is
the resource in its binary form. (The [XML](xml.html#binary) 
and [JSON](json.html#binary) Bundle Representations for binary 
resources are only used in bundles). 

<div class="example">

Here is the request and response to a read operation on a CDA document:

<pre>
GET /[path]/Binary/4 HTTP/1.1
Host: [server]
Accept: */*

HTTP/1.1 200 OK
Content-Type: text/xml
Access-Control-Allow-Origin: *
Last-Modified: Thu, 24 Oct 2013 00:41:55 +0000
ETag: 1
Content-Location: http://[server]/[path]/Binary/4/_history/1

&lt;ClinicalDocument xmlns:xsi=&quot;http://www.w3.org/2001/XMLSchema-instance&quot; 
  xmlns=&quot;urn:hl7-org:v3&quot;xmlns:cda=&quot;urn:hl7-org:v3&quot;&gt;
...  [snip] ...
&lt;/ClinicalDocument&gt;
</pre>
</div>

Searching Binary resources may use the following parameters:

<table class="list">
<tbody><tr><td>**Name**</td><td>**Type**</td><td>**Description**</td></tr>
<tr><td>_id</td><td>[token](search.html#token)</td><td>The logical resource id associated with the resource (must be supported by all servers)</td></tr>
<tr><td>size</td><td>[number](search.html#number)</td><td>Size of the resource in bytes</td></tr>
<tr><td>contenttype</td><td>[token](search.html#token)</td><td>Content Type of the resource</td></tr>
</tbody></table> -->

<a name="search"> </a>

## <span class="sectioncount">6.7.4<a name="6.7.4"> </a></span> Search Parameters

Search parameters for this resource. The [common parameters](search.html#all) also apply. See [Searching](search.html) for more information about searching in REST, messaging, and services.

<table class="list">
<tr><td>**Name**</td><td>**Type**</td><td>**Description**</td><td>**Paths**</td></tr>
<tr><td>contenttype</td><td>[token](search.html#token)</td><td>MimeType of the binary content</td><td>Binary.contentType</td></tr>
</table>

</div>