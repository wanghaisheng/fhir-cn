title: 
date: 
categories: doc
---

  [首页](../home/index.html) >[文档](documentation.html) > **总结**	

<a name="root"> </a>

## <span class="sectioncount">1.12.5.1<a name="1.12.5.1"> </a></span> XML

The XML syntax is closely based on the [XML notation](formats.html):

<pre class="spec">
 &lt;**name** xmlns=&quot;http://hl7.org/fhir&quot; (attrA=&quot;value&quot;)&gt;   <span style="float: right">[![doco](help.png)](formats.html "Documentation for this format")</span>
   &lt;<u>**nameA**</u>&gt;<font color="Gray">&lt;!-- </font><font color="brown">1..1</font> <font color="Darkgreen">type</font> <font color="Navy">description of content</font> <font color="Gray"> --&gt;</font>&lt;nameA&gt;
   &lt;**nameB[x]**&gt;<font color="Gray">&lt;!-- </font><font title="Condition" color="deeppink">0..1</font> <font color="darkgreen">type1</font>|<font color="darkgreen">type1</font> <font color="Navy">description</font> <font color="Gray"> --&gt;</font>&lt;/nameB&gt;
   &lt;**nameC**&gt; <font color="Brown"><font color="Gray">&lt;!-- </font> **1..*** --&gt;</font>
     &lt;**nameD**&gt;<font color="Gray">&lt;!-- </font><font color="brown">1..1</font> <font color="darkgreen">type</font>&gt;<font color="navy">Relevant records</font> <font color="Gray"> --&gt;</font>&lt;/nameD&gt;
   &lt;/nameC&gt;
 &lt;name&gt;
</pre>

Notes:

*   To build a valid XML instance of a resource, simply replace the contents of the elements and attributes with valid content as described by the cardinality, type rules and content description found in the comment in each element
*   Resource and Element names are case-sensitive (though duplicates that differ only in case are never defined)
*   Note that the only properties that are represented as attributes are those defined in underlying specifications such as [Atom (see below)](#atom), which is used as the XML representation for bundles, and attributes are also used for primitive values
*   FHIR elements are always in the namespace [http://hl7.org/fhir](http://hl7.org/fhir).  This is usually specified as the default namespace on the root element.   The only other namespaces that occur in FHIR resources are where some external content model is explicitly introduced into the resource content model. For example, [XHTML is found in every resource](narrative.html)
*   Any of the XML elements may have an id attribute to serve as [the target of an internal reference](references.html#idref). The id attribute is not shown in this format
*   FHIR elements are never empty. If an element is present in the resource, it SHALL have either a value attribute, child elements as defined for its type, an id attribute that is the [link target](references.html#idref) of [narrative](narrative.html#narrative), or 1 or more [extensions](extensibility.html)
*   Attributes can never be empty. Either they are absent, or they are present with at least one character of non-whitespace content
*   XML comments, processing instructions and formatting are not part of the contents of a resource.
*   Specifying the character encoding using a &lt;?xml encoding=&quot;&quot; ?&gt; processing instruction is optional but recommended. Other processing Instructions  SHOULD not be included, except and SHALL not be required in order to properly understand and/or present the data or narrative of the resource.  Applications MAY preserve these when handling resources, but are not required to do so.  Note that digital signatures may depend on them (depending on the canonicalization method used)

When represented as XML, resources may be validated by schema and schematron (see below), but 
operational systems are not required to do so (though the XML SHALL always be 
valid against this specification and the schema and Schematron).

<a name="bundle"> </a>
<a name="atom"> </a>

### <span class="sectioncount">1.12.5.1.1<a name="1.12.5.1.1"> </a></span> Atom Bundle Representation

In XML [bundles](extras.html#bundle) are represented using an Atom format ([http://tools.ietf.org/html/rfc4287](http://tools.ietf.org/html/rfc4287)), following this template:

<pre class="spec">
&lt;feed xmlns=&quot;http://www.w3.org/2005/Atom&quot;&gt;  <span style="float: right">[![doco](help.png)](formats.html "Documentation for this format")</span>
  &lt;title&gt;<span style="color:Gray;">&lt;!-- </span><span style="color: brown;">**1..1**</span> <span style="color:darkgreen;">[string](datatypes.html#string)</span> <span style="color:navy;">Text statement of purpose</span><span style="color: Gray"> --&gt;</span>&lt;/title&gt;
  &lt;id&gt;<span style="color:Gray;">&lt;!-- </span><span style="color: brown;">**1..1**</span> <span style="color:darkgreen;">[uri](datatypes.html#uri)</span> <span style="color:navy;">Unique URI for this bundle</span><span style="color: Gray"> --&gt;</span>&lt;/id&gt;
  &lt;link rel=&quot;self&quot; href=&quot;<span style="color:navy;">[building application url (Service base on REST)]</span>&quot;/&gt;<span style="color:Gray;">&lt;!-- </span><span style="color: brown;">0..1</span><span style="color: Gray"> --&gt;</span>
  &lt;link rel=&quot;first&quot; href=&quot;<span style="color:navy;">[paging: url for first page of result]</span>&quot;/&gt;<span style="color:Gray;">&lt;!-- </span><span style="color: brown;">0..1</span><span style="color: Gray"> --&gt;</span>
  &lt;link rel=&quot;previous&quot; href=&quot;<span style="color:navy;">[paging: url for previous page of result]</span>&quot;/&gt;<span style="color:Gray;">&lt;!-- </span><span style="color: brown;">0..1</span><span style="color: Gray"> --&gt;</span>
  &lt;link rel=&quot;next&quot; href=&quot;<span style="color:navy;">[paging: url for next page of result]</span>&quot;/&gt;<span style="color:Gray;">&lt;!-- </span><span style="color: brown;">0..1</span><span style="color: Gray"> --&gt;</span>
  &lt;link rel=&quot;last&quot; href=&quot;<span style="color:navy;">[paging: url for last page of result]</span>&quot;/&gt;<span style="color:Gray;">&lt;!-- </span><span style="color: brown;">0..1</span><span style="color: Gray"> --&gt;</span>
  &lt;link rel=&quot;fhir-base&quot; href=&quot;<span style="color:navy;">[base path to resolve local urls in this bundle]</span>&quot;/&gt;<span style="color:Gray;">&lt;!-- </span><span style="color: brown;">0..1</span><span style="color: Gray"> --&gt;</span>
  &lt;os:totalResults xmlns:os=&quot;http://a9.com/-/spec/opensearch/1.1/&quot;&gt;<span style="color:Gray;">&lt;!-- </span><span style="color: brown;">**0..1**</span> <span style="color:darkgreen;">[integer](datatypes.html#primitive)</span> <span style="color:navy;">
              Paging: the total number of results</span><span style="color: Gray"> --&gt;</span>&lt;/os:totalResults&gt;
  &lt;updated&gt;<span style="color:Gray;">&lt;!-- </span><span style="color: brown;">**1..1**</span> <span style="color:darkgreen;">[instant](datatypes.html#instant)</span> <span style="color:navy;">When the bundle was built</span><span style="color: Gray"> --&gt;</span>&lt;/updated&gt;
  &lt;author&gt;<span style="color:Gray;">&lt;!-- 0..1 Who created resource? --&gt;</span>
      &lt;name&gt;<span style="color:Gray;">&lt;!-- </span><span style="color: brown;">**1..1**</span> <span style="color:darkgreen;">[string](datatypes.html#string)</span> <span style="color:navy;">Name of Human or Device that authored the resource</span><span style="color: Gray"> --&gt;</span>&lt;/name&gt;
      &lt;uri&gt;<span style="color:Gray;">&lt;!-- </span><span style="color: brown;">0..1</span> <span style="color:darkgreen;">[uri](datatypes.html#uri)</span> <span style="color:navy;">Link to the resource for the author</span><span style="color: Gray"> --&gt;</span>&lt;/uri&gt;
  &lt;/author&gt;
 <a name="tags"> </a>&lt;category term=&quot;<span style="color:navy;">[Tag Term]</span>&quot; label=&quot;<span style="color:navy;">[Tag Label]</span>&quot; scheme=&quot;<span style="color:navy;">[Tag Scheme]</span>&quot;/&gt; <span style="color:Gray;">&lt;!-- </span><span style="color: brown;">0..*</span><span style="color: Gray"> --&gt;</span>
  &lt;entry&gt;<span style="color:Gray;">&lt;!-- Zero+ --&gt;</span>
    &lt;title&gt;<span style="color:Gray;">&lt;!-- </span><span style="color: brown;">**1..1**</span> <span style="color:darkgreen;">[string](datatypes.html#string)</span> <span style="color:navy;">Text summary of resource content</span><span style="color: Gray"> --&gt;</span>&lt;/title&gt;
    &lt;id&gt;<span style="color:Gray;">&lt;!-- </span><span style="color: brown;">**1..1**</span> <span style="color:darkgreen;">[uri](datatypes.html#uri)</span> <span style="color:navy;">Logical Id (URI) for this resource</span><span style="color: Gray"> --&gt;</span>&lt;/id&gt;
    &lt;link rel=&quot;self&quot; href=&quot;<span style="color:navy;">Version Specific reference to Resource</span>&quot;&gt;<span style="color:Gray;">&lt;!-- </span><span style="color: brown;">0..1</span><span style="color: Gray"> --&gt;</span>&lt;/link&gt;
    &lt;updated&gt;<span style="color:Gray;">&lt;!-- </span><span style="color: brown;">**1..1**</span> <span style="color:darkgreen;">[instant](datatypes.html#instant)</span> <span style="color:navy;">Last Updated for resource</span><span style="color: Gray"> --&gt;</span>&lt;/updated&gt;
    &lt;published&gt;<span style="color:Gray;">&lt;!-- </span><span style="color: brown;">0..1</span> <span style="color:darkgreen;">[instant](datatypes.html#instant)</span> <span style="color:navy;">Time resource copied into the feed</span><span style="color: Gray"> --&gt;</span>&lt;/published&gt;
    &lt;author&gt;<span style="color:Gray;">&lt;!-- 0..1 Who created resource? --&gt;</span>
      &lt;name&gt;<span style="color:Gray;">&lt;!-- </span><span style="color: brown;">**1..1**</span> <span style="color:darkgreen;">[string](datatypes.html#string)</span> <span style="color:navy;">Name of Human or Device that authored the resource</span><span style="color: Gray"> --&gt;</span>&lt;/name&gt;
      &lt;uri&gt;<span style="color:Gray;">&lt;!-- </span><span style="color: brown;">0..1</span> <span style="color:darkgreen;">[uri](datatypes.html#uri)</span> <span style="color:navy;">Link to the resource for the author</span><span style="color: Gray"> --&gt;</span>&lt;/uri&gt;
    &lt;/author&gt;    <!-- &lt;category term="<span style="color:navy;">[Resource Type]</span>" scheme="http://hl7.org/fhir/resource-types"&gt;<span style="color:Gray;">&lt;!-- </span><span style="color: brown;">**1..1**</span><span style="color: Gray"> --&gt;</span>&lt;/category&gt; -->
    <span style="color:Gray;">&lt;!-- </span><span style="color:navy;">Tags affixed to the resource (<span style="color: brown;">**0..***</span>): </span> <span style="color: Gray"> --&gt; </span>
	&lt;category term=&quot;<span style="color:navy;">[Tag Term]</span>&quot; label=&quot;<span style="color:navy;">[Tag Label]</span>&quot; scheme=&quot;<span style="color:navy;">[Tag Scheme]</span>&quot;/&gt; <span style="color:Gray;">&lt;!-- </span><span style="color: brown;">0..*</span><span style="color: Gray"> --&gt;</span>
    &lt;content type=&quot;text/xml&quot;&gt;<span style="color:Gray;">&lt;!-- </span><span style="color: brown;">**0..1**</span><span style="color: Gray"> --&gt;</span>
      &lt;<span style="color:navy;">[ResourceName]</span> xmlns=&quot;http://hl7.org/fhir&quot;&gt;
        <span style="color: Gray">&lt;!-- </span><span style="color: navy">Content for the resource</span><span style="color: Gray"> --&gt;</span>
      &lt;/<span style="color:navy;">[ResourceName]</span>&gt;
    &lt;/content&gt;
    &lt;summary type=&quot;xhtml&quot;&gt;<span style="color:Gray;">&lt;!-- </span><span style="color: brown;">0..1</span><span style="color: Gray"> --&gt;</span>
      &lt;div xmlns=&quot;http://www.w3.org/1999/xhtml&quot;&gt;<span style="color:Gray;">&lt;!-- </span><span style="color:navy;">Narrative from resource</span><span style="color:Gray;"> --&gt;</span>&lt;/div&gt;
    &lt;/summary&gt;
  &lt;/entry&gt;
  &lt;Signature xmlns=&quot;http://www.w3.org/2000/09/xmldsig#&quot;&gt;
    <span style="color:Gray;">&lt;!-- </span><span style="color: brown;">0..1</span> <span style="color:navy;">Enveloped Digital Signature (see Atom section 5.1)</span><span style="color:Gray;"> --&gt;</span>
  &lt;/Signature&gt;
&lt;/feed&gt;
</pre>
<a name="atom-notes"> </a>

#### <span class="sectioncount">1.12.5.1.1.1<a name="1.12.5.1.1.1"> </a></span> Notes

*   Logically, a bundle is a set of resources that are prepared to be sent somewhere for consumption - a &quot;feed&quot;
*   The order of elements does not matter in an atom feed (but not entries: the order of the entries is important and may have some meaning associated with it). The order of elements in the atom namespace as documented above does not need to be followed, though it is followed by the FHIR reference platforms
*   The title for the feed and the entry are arbitrary human-readable content. The title of the entry SHOULD be derived from information present in the resource itself.   Systems may ignore content present in the title
*   Every bundle SHALL have a unique id and that id SHALL be a valid absolute [uri](datatypes.html#uri). UUIDs are recommended (urn:uuid:...)
*   The entry element carries the [three pieces of resource metadata](resources.html#metadata): Id (.id), Version Id (.link), Last Updated (.updated)
*   Each entry also carries all the Tags affixed to the resource in the category element. The category element can be used in other ways too
*   The entry.id SHALL be an absolute URL, the tail element of which is the logical id of the resource. The id is a version independent reference
*   The entry.link to self is a version specific reference to the resource.
*   When used in a [RESTful implementation](http.html), the entry.link and entry.id are the URLs of the resource on the system; the version specific link can be used as the basis synchronizing pub/sub systems using the atom bundle with the [updates operation](http.html#history). In other contexts, the values should be literal references to a server if one is available
*   Note that the atom specification requires a known author for every entry. If an author is provided in the base feed element, a specific author is not needed on each entry
*   The author of a resource is not explicit in the FHIR resource model; instead it is delegated to the infrastructure. The name is the name of a human author or a device. The uri is a link to the author (possibly a Practitioner resource)
*   xml:base elements SHOULD NOT be used and implementations do not need to support it
*   The entry.content is optional, but SHALL always be present except in the special case of a transaction response
*   The entire bundle can be signed with a single Enveloped Digital Signature as described in the Atom specification (section 5.1)
*   The feed.link element with relationship &quot;self&quot; is assigned no particular meaning the FHIR specification, except in the case of a search operation, but may be used to provide a reference to the source of the feed
*   The feed.link elements with relationship &quot;first&quot;, &quot;last&quot;, &quot;previous&quot; and &quot;next&quot; are used to implement paging in the RESTful interface and allow a client to browse through a multi-page result. See [search/query](search.html)
*   The feed.link element &quot;fhir-base&quot; is used to resolve relative urls in a bundle, see [relative references](references.html#atom-rel)

<a name="atom-deleted"> </a>

#### <span class="sectioncount">1.12.5.1.1.2<a name="1.12.5.1.1.2"> </a></span> Bundling versions - deletion

When returning a set of resources or versions of a resource, an entry might indicate that the entry has been _deleted_. Deleted resources are represented
in an atom feed as defined by [rfc6721.txt](http://www.rfc-editor.org/rfc/rfc6721.txt): 

<pre class="spec">
&lt;feed xmlns=&quot;http://www.w3.org/2005/Atom&quot;&gt;  <span style="float: right">[![doco](help.png)](formats.html "Documentation for this format")</span>
  <span style="color:Gray;">... feed elements and other entries ...</span>
  &lt;at:deleted-entry xmlns:at=&quot;http://purl.org/atompub/tombstones/1.0&quot;
      ref=&quot;<span style="color:navy;">[Logical Id for deleted resource]</span>&quot; when=&quot;<span style="color:navy;"><span style="color:darkgreen;">[instant](datatypes.html#instant)</span> [when deleted]</span>&quot;&gt;
    &lt;link rel=&quot;self&quot; href=&quot;<span style="color:navy;">[Version Specific reference to Resource]</span>&quot;&gt;<span style="color:Gray;">&lt;!-- </span><span style="color: brown;">0..1</span><span style="color:Gray;"> --&gt;</span>&lt;/link&gt;
  &lt;/at:deleted-entry&gt;
  <span style="color:Gray;">... other entries ...</span>
</pre>

A deleted resource returns a 410 Gone error if it is accessed through the RESTful interface. 

<a name="atom-impl"> </a>

### <span class="sectioncount">1.12.5.1.2<a name="1.12.5.1.2"> </a></span> Implementation Notes

<a name="digsig"> </a>

*   Atom Feeds may be signed following the rules described in the Atom specification. One consequence ofsigning the document is that URLs, identifiers and internal references are frozen and cannot be changed.
This might be a desired feature, but it may also cripple interoperability between closed ecosystems where
[re-identification](use.html#identity) frequently occurs. For this reason, it is recommended that only Document Bundles
are signed and then only when all the related resources are found in the bundle.
*   <a name="Ids"/>
FHIR resources make use of id attributes as targets for <a href="references.html#idref">internal references with resources</a>.These id attributes are unique and resolved within the context of a single resource. When resources arecombined into a bundle, different resources may contain duplicate id attributes. Thus it is important to limit
the scope of resolution of an id attribute to the resource in which the _id_ attribute is declared.

<a name="binary"> </a>

#### <span class="sectioncount">1.12.5.1.2.1<a name="1.12.5.1.2.1"> </a></span> Binary Resources

When a [binary resource](extras.html#binary) is represented as XML in an atom feed, 
it is represented as base64 encoded content along with a content-type, which is the mime-type 
as it would be specified in HTTP:

<pre class="spec">
 &lt;Binary xmlns=&quot;http://hl7.org/fhir&quot; contentType=&quot;<span style="color:navy;">[mime type]</span>&quot;&gt;  <span style="float: right">[![doco](help.png)](formats.html "Documentation for this format")</span>
   <span style="color:navy;">[Base64 Content]</span>
 &lt;/Binary&gt;
</pre>

Binary resources can also be embedded as [contained resources](references.html#contained).  
If there is a desire to capture metadata about a binary object, an appropriate resource type must be used such as
[DocumentReference](documentreference.html) or [Media](media.html).

<a name="schema"> </a>

### <span class="sectioncount">1.12.5.1.3<a name="1.12.5.1.3"> </a></span> XML Schema and Schematron

This specification provides schema definitions for all of the content models described here. 
The base schema is called &quot;[fhir-base.xsd](fhir-base.xsd)&quot; and defines all of the 
datatypes and also the base infrastructure types described on this page. In addition, there 
is a schema for each resource and a common schema [fhir-all.xsd](fhir-all.xsd) 
that includes all the resource schemas.  A customized atom schema [fhir-atom.xsd](fhir-atom.xsd)
is provided for validating [bundles](#atom).

In addition to the w3c schema files, this specification also provides Schematron files that
enforce the various constraints defined for the datatypes and resources.  These are packaged
as files for each resource as well as a combined fhir-atom.sch file
that incorporates the rules for all resources.

XML that is exchanged SHALL be valid against the w3c schema and Schematron, though being 
valid against the schema and Schematron is not sufficient to be a conformant instance: 
this specification makes several rules that cannot be checked by either mechanism. 
Exchanged content SHALL not specify the schema or even the schema instance namespace in 
the resource itself. 

  <!-- Todo: Relax NG, RDF, eCore -->

</div>

				</div>  <!-- /inner-wrapper -->
            </div>  <!-- /row -->
        </div>  <!-- /container -->

    </div>  <!-- /segment-content -->

	<div id="segment-footer" class="segment">  <!-- segment-footer -->
		<div class="container">  <!-- container -->
			<div class="inner-wrapper">

        &copy; HL7.org 2011 - 2014. FHIR DSTU (v0.2.1-2606) generated on Wed, Jul 2, 2014 16:29+0800.   <!-- [QA Report](qa.html) -->   <!-- achive note -->

        <span style="color: #FFFF77">
        Links: [What's a DSTU?](dstu.html) | 
               [Version History](history.html) | 
               [Compare to DSTU](http://services.w3.org/htmldiff?doc1=http%3A%2F%2Fhl7.org%2Fimplement%2Fstandards%2Ffhir%2Fxml.html&amp;doc2=http%3A%2F%2Fhl7.org%2Fimplement%2Fstandards%2FFHIR-Develop%2Fxml.html) | 
               [License](license.html) | 
               [Propose a change](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemAdd&amp;tracker_id=677)   
        </span>

			</div>  <!-- /inner-wrapper -->
		</div>  <!-- /container -->
	</div>  <!-- /segment-footer -->
  <!-- disqus thread -->
  <!-- disqus -->
  <!-- end disqus -->        