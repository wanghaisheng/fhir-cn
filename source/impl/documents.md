title:  
date:  
categories: impl
---

<div class="col-9">

# <span class="sectioncount">2.4<a name="2.4"> </a></span> FHIR Documents

FHIR resources can be used to build documents that represent a composition:
a set of coherent information that is a statement of healthcare information, 
particularly including clinical observations and services. 

A document is an immutable set of resources with a fixed presentation 
that is authored and/or attested by humans, organizations and devices. 

Documents built in this fashion may be exchanged between systems and also 
persisted in document storage and management systems, including systems such as IHE 
XDS. 

Applications claiming conformance to this framework claim to be conformant to 
&quot;FHIR documents&quot;. 

FHIR documents may be 'clinical' (focused on patient healthcare information) but
may also serve non-clinical purposes (e.g. practice guidelines, patient handouts, etc.)
HL7 will develop profiles in the future giving additional guidance on appropriate 
representation of clinical documents in general as well as specific types of clinical 
documents (e.g. Consolidated CDA).

Note that FHIR defines both this document format and also a [document reference resource](documentreference.html). 
FHIR documents are for documents that are authored and assembled in FHIR, while the document reference resource is for 
general references to other documents. 

## <span class="sectioncount">2.4.1<a name="2.4.1"> </a></span> Document Content

All documents have the same structure: a [bundle](extras.html#bundle) 
[of resources identified by the tag](extras.html#tags) &quot;http://hl7.org/fhir/tag/document&quot; 
that has a [Composition](composition.html) resource as the first resource 
in the bundle, followed by a series of other resources referenced from the _Composition_ 
resource that provides guidance on how they fit together. The bundle gathers all the content
of the document into a single XML document which may be signed and managed as required. The 
resources include both human readable and computer processable portions. In addition, the bundle 
may include [CSS stylesheets](http://www.w3.org/Style/CSS/Overview.en.html) 
[provenance](provenance.html) statements, and a signature.

The composition resource is the foundation of the clinical document. It:

*   provides identity and its purpose, sets the context of the document
*   carries key information such as the subject and author, and who attests to the document
*   divides the document up into a series of sections that contain other resources identified in this specification that carry the content 

Any resource referenced directly in the Composition SHALL be included in the bundle when the document 
is assembled. Other resources that these referenced resources refer to may also be included in the 
bundle if the document construction system chooses to so do. Including these additional resources will
make the document bigger, but will save applications from needing to retrieve the linked resources
if they need them while processing the document. Thus, whether these linked resources should be included or 
not depends on the implementation environment.

The document bundle SHALL NOT include any resources not on this list:

1.  The Composition resource, and any resources directly or indirectly (i.e. recursively) referenced from it
2.  A Binary resource containing a stylesheet (as described below)
3.  Provenance Resources that have a target which is a resource included in item #1

There are two key identifiers on the document:

*   The document identifier (mandatory). This is found in _feed.id_ and is unique for this instance of the document, and is never re-used
*   The Composition identifier (optional). This is found in _Composition.identifier_, and is the same for all documents that are derived from this composition

The document has several dates in it:

*   The document date (mandatory). This is found in _feed.updated_ and identifies when the document bundle was assembled from the underlying resources
*   The Composition date (mandatory). This is found in _Composition.instant_, which is when the author wrote the document logically
*   The Attestation dates (optional). This is found in _Composition.attester.time_ and is when the document was witnessed by the attesters. This would usually be at the same time as the composition date or afterwards
*   The Composition last modified time (mandatory per Atom). This is found in _entry.updated_ for the composition, and is the last date of change of the composition. This must be &gt;= the composition date

Document Bundles may be signed using digital signatures following the rules laid out in 
the [Atom specification](http://tools.ietf.org/html/rfc4287). 
The signature SHOULD be provided by a listed attester of the document and the signature 
SHOULD contain a [KeyInfo 
element](http://www.w3.org/TR/xmldsig-core/#sec-KeyInfo) that contains a KeyName element whose value is a URI that matches the Atom _link_ 
element value for the matching attester resource.

Once assembled into a bundle, the document is immutable - its content can never be changed,
and the document id can never be reused. Note that the document may be represented in either
XML or JSON, and interconverted between these or have its character encoding changed, all
the while remaining the same document. However the content (the set of attested resources,
and their order) and the presentation of the document cannot change. Any additional 
documents derived from the same composition SHALL have a different document id. 

<a name="presentation"> </a> 

### <span class="sectioncount">2.4.1.1<a name="2.4.1.1"> </a></span> Document Presentation

When the document is presented for human consumption, applications must present the 
collated narrative portions of the following resources in order:

1.  The Composition resource
2.  The Subject resource
3.  Resources referenced in the _section.content_

The Composition resource narrative should summarize the important parts of the document header that are required 
to establish clinical context for the document (other than the subject, which is displayed in its own 
right). To actually build the combined narrative, simply append all the narrative &lt;div&gt; fragments
together.

The attested content of the document is the composition, the subject, and the resources
referenced in the sections. Additional resources can be included in the bundle, but 
these are not attested content. Specifically, the attester attests to the presented 
form of the document.

The [XML Tools reference implementation](downloads.html#refimpl) includes a 
transform that converts a document into browser-ready XHTML.

<a name="css"/>

In addition to the <a href="narrative.html#css">basic style rules about Narratives</a>, which 
must be followed, a document can reference or contain one or more stylesheets that contains additional styles that 
apply to the collated narrative. This is done by asserting stylesheet links on the feed:

<pre class="xml">
&lt;feed xmlns=&quot;http://www.w3.org/2005/Atom&quot;&gt;  
  &lt;title&gt;FHIR Document&lt;/title&gt;
  &lt;id&gt;urn:uuid:e1db84d2-a524-40a3-827b-076a277ef7df&lt;/id&gt;
  &lt;link rel=&quot;stylesheet&quot; href=&quot;[uri]&quot;/&gt;
</pre>

The uri can be an absolute reference to a CSS stylesheet or
a relative reference to a Binary resource that carries a 
CSS stylesheet. Stylesheet references can only refer to 
a CSS stylesheet - other forms of stylesheet are not acceptable. 

Relative (internal) references SHOULD be used if the document is not 
safe to view without applying the specified stylesheet, as another location
might not be available to the viewer due to technical problems or policy decisions.

Unless otherwise agreed in local trading partner agreements, applications 
displaying the collated narrative SHOULD use the stylesheets specified by the 
document. Parties entering into a trading agreement to do otherwise should 
consider the implications this action will have on their long term scope for document 
exchange very carefully. If the parties agree to use stylesheets that are 
not contained in the document, then it may be that they will never be able 
to share their documents safely in a more general context, such as a regional 
or national EHR or a global personal health record.

## <span class="sectioncount">2.4.2<a name="2.4.2"> </a></span> Document Profiles

[Document profiles](profile.html) are used to describe documents for a particular
purpose. Document profiles may make rules about:

*   The content of the Composition resource, including
*   The structure of the sections in the composition
*   Which resources are to be included in the bundle along with the resources that are directly referenced in the Document resource 

Applications should consider publishing [conformance 
statements](conformance.html) that identify particular documents they support. Documents can 
identify a profile that they conform to by placing a profile tag in a _feed.category_ 
element - see [Profile Tags](extras.html#profile-tags) for a discussion of the utility 
of this.

## <span class="sectioncount">2.4.3<a name="2.4.3"> </a></span> Document Handling Obligations

The authors/constructors and processors of Clinical Documents, whether human or software, have 
obligations that they must satisfy. 

### <span class="sectioncount">2.4.3.1<a name="2.4.3.1"> </a></span> Author/Constructor Obligations

A document constructor is an application that creates a document. An author 
is a human, organization or device that uses the constructor to create a 
document. Between them, the constructor and the author may create new 
content resources and/or assemble already existing content resources while performing their tasks. 
They also have the following responsibilities:

*   To assure that the document SHALL contain valid composition that conforms to the rules described here and that only links to other valid resources
*   To assure that the content of document SHALL conform to any declared [Profiles](profile.html) (see below).
*   Ensure that the attesters are properly aware of the presentation of the document to which they are attesting

### <span class="sectioncount">2.4.3.2<a name="2.4.3.2"> </a></span> Processor Obligations

A document processor is an application and/or human user that receives documents, and extracts data from them, 
or makes decisions because of them. The documents may be received directly from a document constructor, accessed 
via a document management system or forwarded by a third party. The document processor is responsible for 
ensuring that received documents are processed and/or rendered in accordance to this specification. A 
document processor has the obligation to assure that the following rules are followed:

*   When storing/transmitting a document, any method may be used as long as the bundled document can be   (re-)assembled with sufficient integrity to validate a digital signature
*   When presenting the narrative of the document, the rules described above SHALL be followed
*   Resources or data from the document may be extracted for additional uses, but such data is no longer considered to be attested by the document author
*   Wherever the data from the document is displayed to a user, there SHOULD always be a way for the user to access a presentation of the original document

In addition to these obligations, document receivers SHOULD carefully track the source of 
documents for new documents that supersede existing documents, particularly when the documents
represent compositions that have been retracted. When documents have been replaced,
they SHOULD either withdraw data extracted from superseded documents or warn users when 
they view the document or data taken from it.

<a name="signatures"> </a>

## <span class="sectioncount">2.4.4<a name="2.4.4"> </a></span> Signing Documents

Documents may have either an [enveloped](http://www.w3.org/TR/xmldsig-core/#def-SignatureEnveloped) 
or a [detached](http://www.w3.org/TR/xmldsig-core/#def-SignatureDetached) signature. 

Enveloped signatures are included in the document using the technique described for 
[Atom signatures](http://tools.ietf.org/html/rfc4287#section-5.1). 
There is a single signature that signs the entire feed (e.g. on atom:feed). 
The obligations described in the Atom specification apply, with the proviso 
that atom:source has no use for Documents, and therefore there is no need 
to create the atom:source elements. 

Whether documents are signed with an enveloped or a detached signature, applications
processing documents need to relate the document to an existing document participant.
For this reasons, the keyName in the signature SHOULD contain a uri that points 
directly to one of the document participants (person, device or organization)
by the resource identity.

If the document is represented in [JSON](json.html), the same signature
rules apply, and the signature is represented described for [JSON](json.html#sig).

<a name="bundle"> </a>

## <span class="sectioncount">2.4.5<a name="2.4.5"> </a></span> Document End-Points

There are several different RESTful end-points used when working with documents. 
The use of the various end-points can be best be described by considering the consequences 
of posting to them:

<table class="grid">
 <tr> <td>**End-Point**</td> <td>**Type of Content**</td> <td>**Description**</td> </tr>
 <tr> <td>[baseurl]/Document</td> <td>Document Bundle</td> <td>This works like a normal end point 
   for managing a type of resource, but it works with whole document bundles - i.e. a read operation returns a bundle, an update gets a bundle and a search returns a bundle of bundles. The search parameters
   exposed by this end-point are those of the composition resource from the document bundle</td> </tr>

 <tr> <td>[baseurl]/Composition</td> <td>Composition Resource</td> <td>The normal end point for managing
   composition resources. This can be used while building a document or after breaking a document up into 
   its constituent resources or when using compositions separately from documents</td> </tr>

 <tr> <td>[[baseurl]/Binary](extras.html#binary)</td> <td>Document Bundle</td> <td>Just store the entire document as 
   a sequence of bytes and return exactly that sequence when requested. There is no way to find content in the /Binary end-point,
   so usually this would be associated with a [Document Reference](documentreference.html) so that applications
   can find and process the document, though this is not required</td> </tr>

 <tr> <td>[[baseurl]](http.html#transaction) (e.g. a transaction)</td> <td>Document Bundle</td> <td>Ignore the 
   fact that the bundle is a document and process all of the resources that it contains as individual resources. Clients SHOULD
   not expect that a server that receives a document submitted using this method will be able to reassemble the document exactly. (Even if the
   server can reassemble the document (see below), the result cannot be expected to be in the same order, etc.  Thus a document signature will
   very likely be invalid.)</td> </tr>

 <tr> <td>[[baseurl]/Mailbox](messaging.html#mailbox)</td> <td>Document Bundle</td> <td>Submit the 
 document to the server for processing. The exact processing the server performs is at the discretion of the
 server. It MAY perform one or more of these actions:

*   Resend the document elsewhere
*   Break it up into individually accessible resources and make them available on a RESTful interface
*   Retain the document in its binary form and make it available on /Binary and perhaps also create a DocumentReference
  The server is not obliged to process the document in any particular fashion. The client does not know what action
  the server will take, only that the server has accepted responsibility for the document. 

  Implementation Profiles should be careful when making rules about what happens when a document is submitted to the 
  mailbox, as it would be easy to make rules such that a server cannot conform to more than one profile at a time.
  </td> </tr>
</table>

Note: While these end-points are defined for use with document resources and document bundles, 
it is not necessary to use them. Documents may be transferred between systems using any method desired. 

### <span class="sectioncount">2.4.5.1<a name="2.4.5.1"> </a></span> Generating a Document

A client can ask a server to generate a fully bundled document from a composition resource.
The server takes the composition resource, locates all the referenced resources and other
additional resources as configured or requested and either returns a full document bundle,
or returns an error. Note that since this is a search operation, the document bundle is 
wrapped inside the search bundle.

If some of the resources are located on other servers, it is at the discretion of the 
server whether to retrieve them or return an error. If the correct version of the document 
that would be generated already exists, then the server can return the existing one.

The operation is initiated by a named query, using _query=generate on the /Document
end point:

<pre>
  GET [service-url]/Document/?_query=generate&amp;id=:url&amp;...
</pre>

The &quot;id&quot; parameter is a relative or absolute reference to composition resource (e.g.
Composition/1234). The format of the document is specified using the accept: header or 
a [_format parameter](http.html#mime-type). Other parameters may be supplied:

<table class="grid">
  <tr> <td>**Name**</td> <td>**Meaning**</td> </tr>
  <tr> <td>persist</td> <td>Whether to store the document at the document end-point (/Document) or not once it is generated. Value = true or false (default is for the server to decide)</td> </tr>
  <tr> <td>cert</td> <td>Certificate URL to use to sign the document with</td> </tr>
  <tr> <td>pword</td> <td>Password if certificate requires one and the server doesn't know it by some other means. Putting the password in the URL has obvious security implications to consider. An alternative is for the client to sign the document</td> </tr>
</table>

</div>
 