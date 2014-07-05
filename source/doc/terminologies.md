title: 
date: 
categories: doc
---

  [首页](../home/index.html) >[文档](documentation.html) > **总结**	
# <span class="sectioncount">1.14.0<a name="1.14.0"> </a></span> Using Codes in Resources

<a name="bindings"> </a>

Many elements in the FHIR resources have a **coded value**: some fixed string 
(a sequence of characters) assigned elsewhere that identifies some defined &quot;concept&quot;. The 
sequence of characters and it's meaning may be defined in one of several places:

*   As one of a set of fixed values defined in this specification
*   In an internet RFC (e.g. mime type, language)
*   An HL7 defined source (v3 code system, or v2 table)
*   Some external terminology or ontology such as [LOINC](http://loinc.org), [SNOMED CT](http://www.ihtsdo.org)
*   A locally maintained dictionary, look up table or enumeration in an application

All of these kinds of ways of defining codes are collectively called &quot;code systems&quot;.
This list is far from complete; there are many ways to define code systems, and they
vary widely in sophistication and size. 

Throughout this specification, coded values are always treated as a pair 
composed of &quot;system&quot; and &quot;code&quot;, where the system is a URL that identifies the 
code system that defines the codes. 

The FHIR framework for using coded values is based on the fundamental framework defined in section 5 of the  
[HL7 v3 Core Principles](http://www.hl7.org/documentcenter/public/standards/V3/core_principles/infrastructure/coreprinciples/v3modelcoreprinciples.html) document.

When codes are carried in resources, one of 
3 different data types is used:

<table class="grid">
 <tr><td>[code](datatypes.html#code)</td><td>The instance represents the _code_ only. The _system_ is defined as part of the definition of the element, and not carried in the instance. </td></tr>
 <tr><td>[Coding](datatypes.html#Coding)</td><td>A data type that has a _code_ and a _system_ element that identifies where the definition of the code comes from</td></tr>
 <tr><td>[CodeableConcept](datatypes.html#CodeableConcept)</td><td>A type that represents a concept by plain text and/or one or more _Codings_</td></tr>
</table>

## <span class="sectioncount">1.14.0.1<a name="1.14.0.1"> </a></span> Controlling the use of Coded Values

The set of coded values that is allowed to be used in an element of one of these
3 data types is known as a &quot;value set&quot;. Anywhere these data types are used, the
specification &quot;binds&quot; a value set to the element. How this is done is different for 
the simple [code](datatypes.html#code) data type and the complex 
data types ([Coding](datatypes.html#Coding)/[CodeableConcept](datatypes.html#CodeableConcept)).

<a name="simple"> </a>
<a name="code"> </a>

### <span class="sectioncount">1.14.0.1.1<a name="1.14.0.1.1"> </a></span> Simple Code Data Type

Simple elements with type [code](datatypes.html#code) are either bound to a 
value set that contains a list of distinct codes with a specified system (and version, where required), 
or the element is bound to some external standard that defines the set of valid codes that can be 
used (typical examples of references are [Mime Types](http://www.rfc-editor.org/bcp/bcp13.txt), 
[Language Codes](http://tools.ietf.org/html/bcp47), [UCUM](http://unitsofmeasure.org), etc.).

In all cases, the value of the element SHALL be one of the codes defined by value set or the referenced specification. 

Note the following additional rules about these codes:

*   Where the value set is defined by FHIR, the list of allowed codes will be fixed in the XML schema
*   Comparison between codes is always case sensitive for codes unless the codes are defined by reference, and the referenced specification clearly states otherwise
*   The list of codes that can be used can only be extended in subsequent releases of the FHIR specification
*   [Profiles](profile.html) that define how a resource is used in some context may state rules on which codes can be used, but cannot define new or additional codes for these elements

<a name="complex"> </a>
<a name="codeable"> </a>

### <span class="sectioncount">1.14.0.1.2<a name="1.14.0.1.2"> </a></span> Complex Coded Data Types

Elements with type [CodeableConcept](datatypes.html#CodeableConcept) or [Coding](datatypes.html#Coding) 
are bound to a value set that defines a list of coded values that can be used. Because of the size and complexity of 
these value sets, schemas are not used to enforce the correct use of valid coded values. Instead, 
formal definitions of the value sets are provided using the [Value Set](valueset.html) resource, and a cascading set of 
rules is used to control how tightly the actual coded values are controlled by the value set.
In the base FHIR specification, the binding may be called &quot;incomplete&quot; or &quot;example&quot;. 

<a name="incomplete"> </a>

#### <span class="sectioncount">1.14.0.1.2.1<a name="1.14.0.1.2.1"> </a></span> Incomplete Bindings

Incomplete bindings are used when there is consensus at the specification level about the coded values 
that should be used. For these bindings:

*   **Coding**: the _system_/_code_ values SHOULD be one of the codes in the value set.*   **CodeableConcept**: one of the _coding_ elements SHOULD contain a _system_/_code_ that is in the value set.

When none of the coded values in the value set is correct, some other coded value MAY be used, or (for 
a CodeableConcept), a text alternative MAY be provided. Implementers are able to choose other codes 
than those specified in recognition of the fact that:

*   Licensing and Legal policy may dictate that particular coded values must or cannot be used
*   Even when the specified value set can be used, the specification cannot account for all known use cases in advance

<a name="example"> </a>

#### <span class="sectioncount">1.14.0.1.2.2<a name="1.14.0.1.2.2"> </a></span> Example Bindings

Example bindings are used when an element has a very broad meaning (such as [List](list.html).code), 
or there is no consensus over the correct codes to be used. For these bindings:

*   **Coding**: the _system_/_code_ values MAY be one of the codes in the value set.*   **CodeableConcept**: one of the _coding_ elements MAY  contain a _system_/_code_ that is in the value set.

Some other coded value MAY be used, or (for a CodeableConcept), a text alternative MAY be provided. 
Example value sets are provided to assist implementers to understand the correct use of an element.
Value sets based on code systems such as SNOMED CT that have restrictive license terms will only be used as example bindings.

#### <span class="sectioncount">1.14.0.1.2.3<a name="1.14.0.1.2.3"> </a></span> Implementation Details

Irrespective of whether the binding is an incomplete or example binding, when a 
[Profile](profile.html) is used to describe local usage, it can 
bind the element to a different value set. When a profile redefines a 
binding, it can redefine the binding and is able to be much more precise about
exactly which coded values can be used for these elements (see [Binding 
Control](profile.html#binding) for more detail).

Generally it is expected that jurisdictions, projects and vendors 
will work together to choose actual working value sets. Subsequent
versions of FHIR may replace example value sets with full bindings
if enough consensus emerges. 

_System_ values are always case sensitive. Different code systems make their own
rules as to whether the codes they define are case sensitive or not. Note that all the 
codes defined by FHIR itself are case sensitive and SHALL be used in the provided case 
(usually, but not always, lowercase).

Bindings to value sets provided as part of the specification are always specific
to the version of the value set published with the specification. The value set 
may be sealed by defining a simple list of enumerated codes, or it may include 
codes by their properties, along with a non-version specific reference to an 
underlying code system, in which case the list of valid concepts may grow
or change over time.

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
               [Compare to DSTU](http://services.w3.org/htmldiff?doc1=http%3A%2F%2Fhl7.org%2Fimplement%2Fstandards%2Ffhir%2Fterminologies.html&amp;doc2=http%3A%2F%2Fhl7.org%2Fimplement%2Fstandards%2FFHIR-Develop%2Fterminologies.html) | 
               [License](license.html) | 
               [Propose a change](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemAdd&amp;tracker_id=677)   
        </span>

			</div>  <!-- /inner-wrapper -->
		</div>  <!-- /container -->
	</div>  <!-- /segment-footer -->
  <!-- disqus thread -->
  <!-- disqus -->
  <!-- end disqus -->        

	<div id="segment-post-footer" class="segment hidden">  <!-- segment-post-footer -->
		<div class="container">  <!-- container -->
		</div>  <!-- /container -->
	</div>  <!-- /segment-post-footer -->

    