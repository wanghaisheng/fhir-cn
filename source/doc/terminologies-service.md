title: 
date: 
categories: doc
---

  [首页](../home/index.html) >[文档](documentation.html) > [编码的使用](terminologies.html) > **术语服务**	
  
  
  *   [Content](terminologies.html)
  *   [ Named Systems List](terminologies-systems.html)
  *   [value sets](terminologies-valuesets.html)
  *   [V2 表格](terminologies-v2.html)
  *   [V3 命名空间](terminologies-v3.html)
  *   [Concept Map字典映射](terminologies-conceptmaps.html)  
  *   [术语服务](terminologies-service.html)



####  1.22.6  Terminology Service

This specification includes support for the provision of a consumer level terminology service - that is, a
service that lets healthcare applications make use of codes and value sets without having to become
experts in the fine details of the value set resource, and the underlying code systems.
A server that supports all the functionality described here can be described as a &quot;FHIR Terminology Service&quot;,
and SHALL conform to this conformance statement: [link to be provided].

### <span class="sectioncount">1.22.6.1<a name="1.22.6.1"> </a></span> Open issues to be addressed

*   improve the definitions of mapping equivalence, and change &quot;inexact&quot; map to &quot;overlap&quot;

### <span class="sectioncount">1.22.6.2<a name="1.22.6.2"> </a></span> Security

Generally, SSL SHOULD be used for all production health care data exchange.
Even though terminology servers do not directly handle patient information,
hackers may still be able to infer information about patients by observing
the codes and concepts that the terminology service is asked about, so
encryption is still recommended.

A terminology server may choose not to authenticate the clients/users in any fashion,
but can do so in order to limit or account for usage.
For a value set maintenance server that allows terminologies to be edited,
some form of [authorization and/or authentication would be appropriate](security.html).
This specification does not require any particular approach to security.

_Note to reviewers/implementers: can we? it would increase interoperability if we could bind
to a particular approach. If we said, for the operations, SSL+server certs
mandatory, use client certificates if you want to authenticate the clients,
and to use Smart on FHIR for editing value sets and concept maps, is there
any problems with that?_

### <span class="sectioncount">1.22.6.3<a name="1.22.6.3"> </a></span> Basic Concepts

A FHIR terminology service is a simply a set of functions built on the definitions
provided by a set of [ValueSet](valueset.html) and
[ConceptMap](conceptmap.html) resources, with additional inherently known terminologies providing support.

The terminology service builds on the basic principles for using terminologies
in FHIR. Implementers should be familiar with:

*   [Using codes in FHIR](terminologies.html)
*   The [ValueSet](valueset.html) resource
*   The [ConceptMap](conceptmap.html) resource

In addition, implementers should be familiar with the [operations
framework](operations.html). Further useful information may be found in:

*   Underlying Principles: [V3 Core Principles](http://www.hl7.org/documentcenter/public/standards/V3/core_principles/infrastructure/coreprinciples/v3modelcoreprinciples.html)
*   SNOMED CT [technical documentation](http://ihtsdo.org/fileadmin/user_upload/doc/). Note; &quot;namespace&quot; is used differentyl here from the way it is used by IHTSDO

#### <span class="sectioncount">1.22.6.3.1<a name="1.22.6.3.1"> </a></span> External Code Systems

In order to be used with a value set, a code must be defined somewhere. They can be defined as part of
an [inline code system definition](valueset.html#define), or they can be defined elsewhere,
and then used in a value set by quoting the correct namespace. The FHIR specification defines a [set of
namespaces](terminologies-systems.html) for commonly encountered code systems, and defines how some work with FHIR (e.g.
[SNOMED-CT](snomedct.html), [LOINC](loinc.html), [RxNorm](rxnorm.html)).
These code systems are often large, and have many internally defined properties that are part of their
formal definitions. Inline code systems in Value Set resources are not an appropriate way to define
these code systems; FHIR does not provide a formal representation at all. Instead, these terminologies
provide their own distribution formats, and it is assumed that they are externally known to the
terminology server.

Most useful terminology servers will make one or more of these external code systems available for use
within the value sets that they manage. The list of additional terminologies that a terminology server supports
beyond those defined in its value sets is published to clients by (still to figure out how this works).

A server SHOULD publish the additional code systems that it supports through intrinsic knowledge
using the [http://hl7.org/fhir/StructureDefinition/conformance-common-supported-system extension:](extension-conformance-common-supported-system.html)

<pre class="json">
{
 &quot;resourceType&quot; : &quot;Conformance&quot;,
 &quot;extension&quot; : [
   { 
     &quot;url&quot; : &quot;http://hl7.org/fhir/StructureDefinition/supported-system&quot;,
     &quot;valueUri&quot; : &quot;http://loinc.org&quot; 
   }]  
}
</pre>

This extension is added to the root [Conformance Statement](conformance.html).

#### <span class="sectioncount">1.22.6.3.2<a name="1.22.6.3.2"> </a></span> Implementation Note

When a terminology server exposes an external code system, it makes a set of services available
internally that serve the operational interfaces below. The internal server depends on the following
logical information for a terminology:

*   its URL (namespace, and how versioning works)
*   what codes are valid*   what properties can be used to select codes*   what implicit value sets exist

The FHIR specification itself defines these things for common terminologies (including
[SNOMED-CT](snomedct.html), [LOINC](loinc.html), [RxNorm](rxnorm.html)),
and provides the Value Set infrastructure for supporting typical relatively simple small code systems.

_Implementers Note: Implementers interested in working with existing published terminologies for
which the Value Set infrastructure is not suitable should discuss their needs with HL7 to get the
list above extended._

Note: A terminology service may choose to expose additional external code system specific
related functionality such as exploration, or structured search, but these services are
outside the scope of the FHIR terminology service.

#### <span class="sectioncount">1.22.6.3.3<a name="1.22.6.3.3"> </a></span> Terminology Maintenance

The terminology service uses the value set resources defined on the system - both
the implicit ones associated with the external code systems and those explicitly
available at the /ValueSet endpoint - to serve the operational interface defined below.
As value sets are created, updated or deleted, the outcomes of the operational services
change. A terminology server should validate incoming resources, and ensure integrity
of the terminology services. Typically, servers would provide a test and production
environment, but there is no explicit notion of this in the interface itself.

### <span class="sectioncount">1.22.6.4<a name="1.22.6.4"> </a></span> Value Set Expansion

A value set describes a set of rules for what codes or concepts are considered to be in the value set.
These rules might be simple (e.g. a direct list of codes from a specified version of a code system), or
they might be quite complex (e.g. all codes with a particular property from an unspecified version of
a code system).

A FHIR enabled application can simply ask the server to figure out all the details, and return it a list
of the current codes in the value set. This is known as [&quot;expanding&quot; the valueset](valueset-operations.html#expand).
As a summary, the client passes the server the following information:

*   the value set (either by its URL on the RESTful interface, by its logical identifier [(ValueSet.url)](valueset-definitions.html#ValueSet.url), or directly as a parameter to the call)
*   (Optionally) a text filter to use to restrict the codes that are returned (e.g. user input text). It is left to server discretion to choose how to apply the text filter
*   (Optionally) a date at which the expansion should be evaluated (usually, this is the current date/time, but there are circumstances where that is not appropriate)

The server returns a value set that contains the current list of codes that meet the filter criteria (or an
[OperationOutcome](operationoutcome.html) with an error if the expansion fails).
Note that some value sets expand to many thousands of codes, or even an infinite number,
and for these, the server SHOULD return an [error code
_too-costly_](issue-type.html#too-costly). In these cases the client can try again with a more specific text filter
to reduce the number of codes returned.

For further information, consult the [definition of the operation](valueset-operations.html#expand).
_Note to reviewers/implementers: Open Issue for connectathons: is paging support required for the iterating through an expansion?_

Some example uses for the expansion operation:

*   get a list of codes to display in a User interface (e.g. a drop down interface)
*   a variation on this is to offer the user a text box to type in. As the user types, call the expand operation to provide the user with a list of matching codes/concepts (like a browser search)*   fetch a list of codes to use when generating software programming instructions
*   get a list of codes so that software can check whether a code is valid or not in a particular context

<div class="example">

**Examples**

Expanding a value set that is already registered on the server as &quot;23&quot;, with a text filter of &quot;abdo&quot; :

<pre class="http">
GET [base]/ValueSet/23/$expand?filter=abdo
</pre>

Expanding a value set that is specififed by the client (using JSON):

<pre class="http">
POST [base]/ValueSet/23/$expand
[other headers]

{
  &quot;resourceType&quot; : &quot;Parameters&quot;,
  &quot;parameter&quot; : [
     {
     &quot;name&quot; : &quot;valueSet&quot;,
     &quot;resource&quot; : {
       &quot;resourceType&quot; : &quot;ValueSet&quot;,
     [value set details]
     }
   }
  ]
}
</pre>

The server responds with a value set (this example in XML):

<pre class="http">
HTTP/1.1 200 OK
[other headers]

&lt;ValueSet xmlns=&quot;http://hl7.org/fhir&quot;&gt;
  &lt;!-- the server SHOULD populate the id with a newly created UUID
    so clients can easily track a particular expansion  --&gt;
  &lt;id value=&quot;43770626-f685-4ba8-8d66-fb63e674c467&quot;/&gt;
  &lt;!-- no need for meta, though it is allowed for security labels, profiles --&gt;

  &lt;!-- other value set details --&gt;
  &lt;expansion&gt;
    &lt;!-- when expanded --&gt;
    &lt;timestamp value=&quot;20141203T08:50:00+11:00&quot;/&gt;
  &lt;contains&gt;
    &lt;!-- expansion contents --&gt;
  &lt;/contains&gt;
  &lt;/expansion&gt;
&lt;/ValueSet&gt;
</pre>
</div>

### <span class="sectioncount">1.22.6.5<a name="1.22.6.5"> </a></span> Concept Lookup

A system can ask a terminology server to return a set of information about a particular system/code
combination using [the lookup operation](valueset-operations.html#lookup). The server returns information for both display and processing
purposes. The client passes the server the following information:

*   the code value (either a code+system, or a Coding data type
*   (Optionally) a date at which the code information should be returned (usually, this is the current date/time, but there are circumstances where that is not appropriate)

The server returns the following information:

*   A human description of the system
*   A recommended display for the code*   Whether the code is abstract or not
*   Other designations for the code (a value, optionally with language and/or a use code)

The recommended display to the code is a text representation of the code
that the terminology server recommends as the default choice to show
to the user, though a  client may choose out of the other designations if it has reason to.

<div class="example">

**Examples**

Looking up a code/system :

<pre class="http">
GET [base]/ValueSet/$lookup?system=http://loinc.org&amp;code=1963-8
</pre>

Lookup using a Coding (this example in XML):

<pre class="http">
POST [base]/ValueSet/$lookup
[other headers]

&lt;Parameters xmlns=&quot;http://hl7.org/fhir&quot;&gt;
  &lt;parameter&gt;
    &lt;name value=&quot;coding&quot;/&gt;
  &lt;valueCoding&gt;
    &lt;system value=&quot;http://loinc.org&quot;/&gt;
    &lt;code value=&quot;1963-8&quot;/&gt;
  &lt;/valueCoding&gt;
  &lt;/parameter&gt;
&lt;/Parameters&gt;
</pre>

The server responds with a set of information (JSON this time):

<pre class="http">
HTTP/1.1 200 OK
[other headers]

{
  &quot;resourceType&quot; : &quot;Parameters&quot;,
  &quot;parameter&quot; : [
    {
    &quot;name&quot; : &quot;name&quot;,
    &quot;valueString&quot; : &quot;LOINC&quot;
  },
  {
    &quot;name&quot; : &quot;version&quot;,
    &quot;valueString&quot; : &quot;2.48&quot;
  },
  {
    &quot;name&quot; : &quot;designation&quot;,
    &quot;valueString&quot; : &quot;Bicarbonate [Moles/volume] in Serum&quot;
  },
  {
    &quot;name&quot; : &quot;abstract&quot;,
    &quot;valueString&quot; : &quot;false&quot;
  },
  {
      &quot;name&quot; : &quot;designation&quot;,
    &quot;part&quot; : [
    {
      &quot;name&quot; : &quot;value&quot;,
      &quot;valueString&quot; : &quot;Bicarbonate [Moles/volume] in Serum &quot;
    }
    ]
  }
  ]
}
</pre>
</div>

### <span class="sectioncount">1.22.6.6<a name="1.22.6.6"> </a></span> Value Set Validation

One of the ways to determine whether a code is in a value set is to expand the value set
(as described above), and then look at the returned codes to see if the code is in the expansion.
However this is not an efficient way to test whether a code is valid, and for some value sets
(e.g. with infinite number of members), it cannot work. Instead, a FHIR terminology server
provides [a &quot;validate&quot; operation](valueset-operations.html#validate). The client passes the server the following information:

*   the value set (either by its URL on the RESTful interface, by its logical identifier [(ValueSet.url)](valueset-definitions.html#ValueSet.url), or directly as a parameter to the call)
*   the code value (either a code+system, a Coding data type, or a CodeableConcept
*   (Optionally) a date at which the expansion should be evaluated (usually, this is the current date/time, but there are circumstances where that is not appropriate)

The server returns a true/false indicating whether the code/concept is valid, and a list
of errors and warnings associated with it. The server should also return an appropriate
display for the concept for use in a UI context.

Note that if the server is passed a CodeableConcept, the server is able to check
whether any of the codes are valid against the value set, and also check whether
multiple codings are allowed and/or the codings provided are consistent with each other.

Every code system has an implicit value set that is &quot;all the concepts defined
in the code system&quot;. For some code systems, these value set URIs are defined
in advance (e.g. for [LOINC](loinc.html), it's `http://loinc.org/vs`).
However for some code systems, they are not known. Clients can refer to these implicit
value sets by providing the URI for the code system itself.

<div class="example">

**Examples**

Simple validation of a code/system against a known value set:

<pre class="http">
GET [base]/ValueSet/23/$validate?system=http://loinc.org&amp;code=1963-8&amp;display=test
</pre>

Validate a CodeableConcept against a client specified value set (this example in JSON):

<pre class="http">
POST [base]/ValueSet/$validate
[other headers]

{
  &quot;ResourceType&quot; : &quot;Parameters&quot;,
  &quot;parameter&quot; : [
    {
    &quot;name&quot; : &quot;coding&quot;,
    &quot;valueCodeableConcept&quot; : {
      &quot;coding&quot; : {
        &quot;system&quot; : &quot;http://loinc.org&quot;,
          &quot;code&quot; : &quot;1963-8&quot;,
      &quot;display&quot; : &quot;test&quot;
      }
    }
  },
  {
    &quot;name&quot; : &quot;valueSet&quot;,
    &quot;resource&quot;: {
      &quot;resourceType&quot; : &quot;ValueSet&quot;,
    [etc]
    }
  }
  ]
}
</pre>

The server responds with validation information (JSON this time):

<pre class="http">
HTTP/1.1 200 OK
[other headers]

{
  &quot;resourceType&quot; : &quot;Parameters&quot;,
  &quot;parameter&quot; : [
    {
    &quot;name&quot; : &quot;result&quot;,
    &quot;valueBoolean&quot; : &quot;false&quot;
  },
  {
    &quot;name&quot; : &quot;message&quot;,
    &quot;valueString&quot; : &quot;The display \&quot;test\&quot; is incorrect&quot;
  },
  {
    &quot;name&quot; : &quot;display&quot;,
    &quot;valueString&quot; : &quot;Bicarbonate [Moles/volume] in Serum&quot;
  }
  ]
}
</pre>
</div>

### <span class="sectioncount">1.22.6.7<a name="1.22.6.7"> </a></span> Subsumption testing

The Expand and Validate operations can be used to perform subsumption testing. To test whether
_code A_ subsumes _code B_, perform a validate specifying a value set built of all the
codes that are subsumed by _code A_, and test whether _code B_ is subsumed by it.
Note that a server is allowed (and SHOULD, but is not required to) consider concept maps when
doing subsumption testing. E.g. if A is a LOINC code, and it has a precise mapping to a
SNOMED CT code that subsumes B, with an appropriate scope, then the server can indicate
that this it is true that LOINC code A subsumes SNOMED CT code B.

In order to make it convenient to perform this subsumption testing, code systems that define
subsumption hierarchies should define simple URLs to express a value set that includes all the
codes subsumed by a code.

<div class="example">

**Examples**

Test whether a Snomed Concept 399211009 (History of myocardial infarction) is subsumed by 22298006 (Myocardial infarction):

<pre class="http">
GET [base]/ValueSet/$validate?system=http://snomed.info/sct&amp;code=X&amp;uri=http://hl7.org/fhir/ValueSet/snomedct?base=Y
</pre>

Server response:

<pre class="http">
HTTP/1.1 200 OK
[other headers]

{
  &quot;resourceType&quot; : &quot;Parameters&quot;,
  &quot;parameter&quot; : [
    {
    &quot;name&quot; : &quot;result&quot;,
    &quot;valueBoolean&quot; : &quot;false&quot;
  },
  ]
}
</pre>
</div>

### <span class="sectioncount">1.22.6.8<a name="1.22.6.8"> </a></span> Batch Validation

It's also possible to validate a set of concepts against their relevant value
sets in [a single batch operation](valueset-operations.html#batch), to support high-volume process and reduce network
latency effects. In this case, the client passes the server the following information:

*   a series of pairs of parameters, where each pair contains
*   a CodeableConcept containing the concept to be validated
*   a uri referring to the value set against which the code should be validated
*   (Optionally) a date at which the expansion should be evaluated (usually, this is the current date/time, but there are circumstances where that is not appropriate)

Code system URIs may be used to refer to the implicit value set that includes
all the codes in the code system  (as described for the validation operation).

The server returns a series of parameters, one for each submitted item, each of
which has a result, a message, and a display (same as for the $validate operation).

This operation could be used, for instance, to validate a set of codes in a
CDA document, by converting from the CDA CD data type to CodeableConcepts.

<div class="example">

**Examples**

A request to validate 2 concepts from a CDA document, with OIDs for value set identifiers:

<pre class="http">
POST [base]/ValueSet/$batch
[other headers]

{
  &quot;ResourceType&quot; : &quot;Parameters&quot;,
  &quot;parameter&quot; : [
    {
    &quot;name&quot; : &quot;item&quot;,
    &quot;part&quot; : [
      {
      &quot;name&quot; : &quot;concept&quot;,
      &quot;valueCodeableConcept&quot; : {
        &quot;system&quot; : &quot;http://loinc.org&quot;,
        &quot;code&quot; : &quot;2324-4&quot;
      },
    }
      &quot;name&quot; : &quot;uri&quot;,
      &quot;valueUri&quot; : &quot;urn:oid:1.2.3.4.6&quot;
    ]
  },
  {
    &quot;name&quot; : &quot;item&quot;,
    &quot;part&quot; : [
      {
      &quot;name&quot; : &quot;concept&quot;,
      &quot;valueCodeableConcept&quot; : {
        &quot;system&quot; : &quot;http://snomed.info/sct&quot;,
        &quot;code&quot; : &quot;22298006&quot;
      },
    }
      &quot;name&quot; : &quot;uri&quot;,
      &quot;valueUri&quot; : &quot;urn:oid:1.2.3.4.7&quot;
    ]
  }
  ]
}
</pre>

The server responds with a series of validation outcomes (JSON this time):

<pre class="http">
HTTP/1.1 200 OK
[other headers]

{
  &quot;resourceType&quot; : &quot;Parameters&quot;,
  &quot;parameter&quot; : [
    {
      &quot;name&quot; : &quot;item&quot;,
      &quot;part&quot; : [
        {
        &quot;name&quot; : &quot;result&quot;,
        &quot;valueBoolean&quot; : &quot;false&quot;
      },
      {
        &quot;name&quot; : &quot;message&quot;,
        &quot;valueString&quot; : &quot;'2324-4' is not a valid LOINC code&quot;
      }
    ]
  },
  {
      &quot;name&quot; : &quot;item&quot;,
      &quot;part&quot; : [
        {
        &quot;name&quot; : &quot;result&quot;,
        &quot;valueBoolean&quot; : &quot;false&quot;
      },
      {
        &quot;name&quot; : &quot;message&quot;,
        &quot;valueString&quot; : &quot;The concept is not in the specified value set (\&quot;Organisms\&quot;)&quot;
      },
      {
        &quot;name&quot; : &quot;display&quot;,
        &quot;valueString&quot; : &quot;Myocardial infarction&quot;
      }
    ]
  }]
}
</pre>
</div>

### <span class="sectioncount">1.22.6.9<a name="1.22.6.9"> </a></span> Translations

A client can ask a server to translate a concept from one value set to another. Typically, this
is used to translate between code systems (e.g. from LOINC to SNOMED CT, or from a v3 code to
a v2 code). The client calls [the translate operation](conceptmap-operations.html#translate) and passes the following parameters:

*   A code+system, Coding, or CodeableConcept
*   A Concept Map to use for the translation
*   The value set for the context of the source*   The value set for the destination

The client passes either a concept map, or the value sets for the source and destination context.
If there is no concept map, then the server may determine the appropriate map to use from
context provided in the value sets.
If there is no particular context, the appropriate value sets would be the value sets for the
entire coding system at question (e.g. from http://snomed.info/sct to http://loinc.org/vs).
The server performs the translation as it is able based on the concept maps that it knows about.
If no single mapping can be determined then the
server returns an error. Some servers may require a concept map to use for the translation.

<div class="example">

**Example**

Translate from FHIR Composition status to V3 Act Status (based on
[this defined concept map](composition-status-map-v3.html):

<pre class="http">
GET [base]/ConceptMap/$validate?system=http://hl7.org/fhir/composition-status
  &amp;code=preliminary&amp;valueSet= http://hl7.org/fhir/vs/composition-status
  &amp;target=http://hl7.org/fhir/v3/vs/ActStatus
</pre>

The server responds with validation information:

<pre class="http">
HTTP/1.1 200 OK
[other headers]

{
  &quot;resourceType&quot; : &quot;Parameters&quot;,
  &quot;parameter&quot; : [
    {
    &quot;name&quot; : &quot;result&quot;,
    &quot;valueBoolean&quot; : &quot;true&quot;
    },
    {
      &quot;name&quot; : &quot;outcome&quot;,
      &quot;valueCoding&quot; : {
        &quot;system&quot; : &quot;http://hl7.org/fhir/v3/ActStatus&quot;,
        &quot;code&quot; : &quot;active&quot;,
      }
    }
  ]
}
</pre>
</div>

### <span class="sectioncount">1.22.6.10<a name="1.22.6.10"> </a></span> Batch Translation

It's also possible to translate a set of concepts in [a single batch operation](conceptmap-operations.html#batch), to support high-volume process and reduce network
latency effects. In this case, the client passes the server the following information:

*   a series of parameter tuples, where each pair contains
*   a CodeableConcept containing the concept to be translated
*   a uri that identifies the target value set into which to translate the concept
*   (optiona) A reference to a particular map to use for the translation

The server returns a series of parameters, one for each submitted item, each of
which has a result, a message, and an outcome (same as for the $translate operation).

<div class="example">

**Examples**

A request to translate 2 concepts from a CDA document, with OIDs for value set identifiers:

<pre class="http">
POST [base]/ConceptMap/$batch
[other headers]

{
  &quot;ResourceType&quot; : &quot;Parameters&quot;,
  &quot;parameter&quot; : [
    {
    &quot;name&quot; : &quot;item&quot;,
    &quot;part&quot; : [
      {
      &quot;name&quot; : &quot;concept&quot;,
      &quot;valueCodeableConcept&quot; : {
        &quot;system&quot; : &quot;http://loinc.org&quot;,
        &quot;code&quot; : &quot;2324-4&quot;
      },
    }
      &quot;name&quot; : &quot;target&quot;,
      &quot;valueUri&quot; : &quot;urn:oid:1.2.3.4.6&quot;
    ]
  },
  {
    &quot;name&quot; : &quot;item&quot;,
    &quot;part&quot; : [
      {
      &quot;name&quot; : &quot;concept&quot;,
      &quot;valueCodeableConcept&quot; : {
        &quot;system&quot; : &quot;http://snomed.info/sct&quot;,
        &quot;code&quot; : &quot;22298006&quot;
      },
    }
      &quot;name&quot; : &quot;target&quot;,
      &quot;valueUri&quot; : &quot;urn:oid:1.2.3.4.7&quot;
    ]
  }
  ]
}
</pre>

The server responds with a series of validation outcomes:

<pre class="http">
HTTP/1.1 200 OK
[other headers]

{
  &quot;resourceType&quot; : &quot;Parameters&quot;,
  &quot;parameter&quot; : [
    {
      &quot;name&quot; : &quot;item&quot;,
      &quot;part&quot; : [
        {
        &quot;name&quot; : &quot;result&quot;,
        &quot;valueBoolean&quot; : &quot;false&quot;
      },
      {
        &quot;name&quot; : &quot;message&quot;,
        &quot;valueString&quot; : &quot;'2324-4' is not a valid LOINC code&quot;
      }
    ]
  },
  {
      &quot;name&quot; : &quot;item&quot;,
      &quot;part&quot; : [
        {
        &quot;name&quot; : &quot;result&quot;,
        &quot;valueBoolean&quot; : &quot;false&quot;
      },
      {
        &quot;name&quot; : &quot;outcome&quot;,
        &quot;valueCodeableConcept&quot; : {
          &quot;coding&quot; : {
            &quot;system&quot; : &quot;http://example.com/codesystems/example&quot;,
            &quot;code&quot; : &quot;xxxx&quot;
          }
        }
      }
    ]
  }]
}
</pre>
</div>

<a name="closure"> </a>

### <span class="sectioncount">1.22.6.11<a name="1.22.6.11"> </a></span> Maintaining a Closure Table

The 4 operations Expand, Lookup, Validate, and Translate account for most operational requirements
associated with terminology use. However there is one difficult but important use case that
they do not address, which is integrating terminologically based logic into application search.

A typical example of this is a user that wants to find any observations for male patients over
the age of 50 who attended a particular clinic within a particular 2 week period, with a
diagnosis of gout, and who had an elevated serum creatinine.

In this case, both &quot;diagnosis of gout&quot; and &quot;serum creatinine&quot; involve valueset and/or subsumption queries
(e.g. against SNOMED CT and LOINC respectively). This search has to be executed by some
logical processing engine that knows how to find this data in a given persistence store.
Often, this is some kind of SQL query, though many other technological choices are available.
However this is done, the challenge with an operation like this is to integrate the
terminological knowledge with search execution based on the other relationships the criteria is expressed.

On approach to this problem would be to using the expand operation above, so that the system executing
the search could generate expansions, and then search for these expansions. This has a couple of problems:

*   the list of subsumed codes could be very long, and the search operation becomes correspondingly inefficient
*   the expansion of the subsumption might not be closed, and so the search operation can't be correct

An alternative approach is to generate a subsumption [closure table](http://karwin.blogspot.com.au/2010/03/rendering-trees-with-closure-tables.html),
which lists all the possible relationships, and allows for rapid execution of these kind of queries. However this has other problems:

*   the subsumption table can be very large (&gt;500000 records for SNOMED CT), even though very few of the codes are used
*   subsumption tables are generally built up front, and don't deal with new codes as they are encountered very well
*   they still don't offer a solution for non-closed expansions

This is the main reason why most systems don't support post-coordination or other forms
of coded expressions.

In FHIR, this problem is solved by building a closure table on the fly, as new codes are seen.
This technique leaves the FHIR terminology server responsible for the terminological reasoning,
and the client responsible for the closure table maintenance. To the client, it doesn't matter
whether the concept is post-coordinated or not. Here's a description of how the process works:

1.  The client defines a name associated with a particular context in which it wishes to maintain a subsumption based closure table.
2.  The client registers this name with the FHIR Terminology server using the $closure operation (described below), with only one parameter, the name of the context
3.  any time the client system encounters a new Coding that isn't entered in the closure table, it calls the $closure operation with the context name, and the Coding value it has encountered
4.  the server returns a ConceptMap resource with a list of new entries (code : system -&gt; code : system) that the client should add to its closure table

        *   the server can indicate that entries should be removed from the table by providing a (code : system -&gt; code : system) with equivalence &quot;unmatched&quot; (though it's not known why that would be needed)
5.  The client makes these entries into its closure table6.  to facilitate the initialization process, a server can call $closure with multiple Coding values

The [$closure operation](conceptmap-operations.html#closure) takes 2 parameters:

*   Closure table context name
*   Coding to enter into the table (0 or more - 0 codings is a request to (re-)initialise the table)

The operation returns a concept map which has a list of mappings that represent new entries to make in the closure table.

The closure table can be resynchronized by passing an additional &quot;version&quot; parameter, which is a value taken from the
version in one of the delta responses. This is a request to replay all the mapping changes since that delta was sent.

<div class="example">

**Example**

The client sees a new SNOMED CT concept &quot;22298006&quot; in a data element it is tracking as &quot;patient-problems&quot;:

<pre class="http">
POST [base]/$closure

{
  &quot;resourceType&quot; : &quot;Parameters&quot;,
  &quot;parameter&quot; : [
    {
      &quot;name&quot; : &quot;name&quot;,
      &quot;valueId : &quot;patient-problems&quot;
    },
    {
      &quot;name&quot; : &quot;concept&quot;,
      &quot;valueCoding&quot; : {
        &quot;system&quot; : &quot;http://snomed.info/sct&quot;,
        &quot;code&quot; : &quot;22298006&quot;,
      }
    }
  ]
}

</pre>

The server responds with a set of new entries to add to the concept map.
It provides one important piece of metadata - the version, which the client
can use to resynchronize the closure table:

<pre class="http">
HTTP/1.1 200 OK
[other headers]

{
  &quot;resourceType&quot;: &quot;ConceptMap&quot;,
  &quot;identifier&quot;: &quot;49088976-d54d-4d19-b868-3d4c18cebabb&quot;,
  &quot;version&quot;: &quot;8&quot;,
  &quot;status&quot;: &quot;active&quot;,
  &quot;experimental&quot;: true,
  &quot;date&quot;: &quot;2012-06-13&quot;,
  &quot;element&quot;: [
    {
      &quot;codeSystem&quot;: &quot;http://snomed.info/sct&quot;,
      &quot;code&quot;: &quot;22298006&quot;,
      &quot;map&quot;: [
        {
          &quot;codeSystem&quot;: &quot;http://snomed.info/sct&quot;,
          &quot;code&quot;: &quot;128599005&quot;,
          &quot;equivalence&quot;: &quot;narrower&quot;
        }
      ]
    },
  ]
}
</pre>
</div>

Notes:

*   In this simple example, the addition of a single new SNOMED CT concept created one existing subsumption relationship. In general clinical use, more than one relationship would be expected
*   For the purposes of the closure table, the relationships are considered to be bi-directional; e.g. if A subsumes B, then B is subsumed by A
*   As well as entering codes that are actually used, the client also enters search terms into the closure table
*   The combination of the system and code is the key to the closure table; if the server encounters two different codes that have the same meaning (e.g. syntactical variation), it should create an &quot;equals&quot; relationship between them

### <span class="sectioncount">1.22.6.12<a name="1.22.6.12"> </a></span>  Functional Operations 

In order to support terminology operations in FHIR a minimal set of terminology operations would be necessary.  These operations are a sub set of the available terminology service operations defined in the [http://www.omg.org/spec/CTS2/1.0/ Common Terminology Services - Release 2 (CTS2) specification] and can be categorized as:

*   Administrative Operations
*   Search/Query Operations
*   Authoring/Maintenance Operations

Functional operations within these categories support the access and management of terminology objects such as Code Systems, Concepts, Value Sets and Concept Mappings. The functional operations necessary to support a FHIR terminology service are outlined here.

#### <span class="sectioncount">1.22.6.12.1<a name="1.22.6.12.1"> </a></span>  Administrative Operations 

*   Be able to load a standard or local code system

#### <span class="sectioncount">1.22.6.12.2<a name="1.22.6.12.2"> </a></span>  Search/Query Operations 

 Concepts 

*   Retrieve the concept details (display name, qualifiers, associations, etc.) for a given code/code system
*   Return possible concept matches  based on search criteria*   Validate whether a code is valid within a given code system (content)
*   Retrieve a list of codes (for example, to populate a user interface)
*   Return the decedents of a given concept

 Code System 

*   Retrieve the metadata for a code system

 Value Set 

*   Retrieve the metadata for a value set
*   Return a value set based on search criteria
*   Determine if a code is valid in a value set
*   Generate the Value set Expansion from the Value Set Definition.

 Mapping 

*   Retrieve the metadata for map set
*   Retrieve a translation (mapping) of concept(s) from a given source code system to target concept(s) from a target code system

#### <span class="sectioncount">1.22.6.12.3<a name="1.22.6.12.3"> </a></span>  Authoring/Maintenance Operations 

Concepts

*   Maintain a closure table

 Value Set 

*   Create/editing a value set

 Mapping 

*   Translate (map) from a source code system to a target code system

</div>