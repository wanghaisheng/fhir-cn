title: 
date: 
categories: doc
---

  [首页](../home/index.html) >[文档](documentation.html) > **总结**	

<a name="json"> </a>

## <span class="sectioncount">1.12.5.2<a name="1.12.5.2"> </a></span> Representing Resources in JSON

Though the FHIR resources are described using a representation based on XML, this 
specification also defines a JSON representation of the resources. The JSON format 
for the resources follows the standard XML format very closely to make interconversion 
easy, and so that XPath queries can easily be mapped to query the JSON structures. 
The formal mime type for this format is application/json+fhir.

Clients are free to choose whether to implement in XML or JSON. Servers SHALL support XML, and can 
choose to support JSON. Note that systems SHALL declare which format(s) they 
support in their [Conformance Statement](conformance.html). 

The JSON representation is described relative to the XML representation:

*   The names for the JSON object members are the same as the names of the elements and attributes in XML, including elements that may repeat. Property names are case sensitive
*   Just as in XML, JSON property attributes never have empty values; omit a value if it is empty
*   JSON whitespace is not part of the contents of a resource. Applications MAY preserve the whitespace when handling resources, but are not required to do so. Note that digital signatures may depend on the whitespace

There are differences too:

*   There are no namespaces in the JSON representation
*   The type of the resource is represented differently in JSON
*   The order of properties of an object is not significant in the JSON representation, though order within an array SHALL be maintained
*   JSON does not have a notion of attributes versus elements, so attributes (xml:id, value) are handled differently
*   JSON has a notation for arrays, which are used to represent repeating elements. Note that arrays are used when the item might repeat, even if it does not repeat in a specific instance
*   The XHTML &lt;div&gt; element in the [Narrative](narrative.html) datatype is represented as a single escaped string of XHTML. This is to avoid problems in JSON with mixed content, etc. The XHTML S still conform to the rules described for [the Narrative](narrative.html)

These differences - particularly the repeating element one, which cannot be avoided - mean that generic XML --&gt; JSON converters are not 
able to perform correctly. The [reference platforms](downloads.html#refimpl) provide XML &lt;--&gt; JSON conversion functionality that accommodates these FHIR-specific characteristics.

### <span class="sectioncount">1.12.5.2.1<a name="1.12.5.2.1"> </a></span> JSON Representation for repeating elements

An element that has a maximum cardinality of x..* may occur more than once in the instance.
In XML, this is simply done by repeating the XML element multiple times. In JSON, this is
done by using an array type. Note that:

*   The name of the array is singular - the same as the XML element
*   An item that may repeat is represented as an array even in the case that it doesn't repeat so that the process of parsing the resource is the same either way
<pre class="xml">
 &lt;**coding**&gt;
   &lt;**system** value=&quot;http://snomed.info/sct&quot;/&gt;
   &lt;**code** value=&quot;104934005&quot;/&gt;
 &lt;/**coding**/&gt;
 &lt;**coding**&gt;
   &lt;**system** value=&quot;http://loinc.org&quot;/&gt;
   &lt;**code** value=&quot;2947-0&quot;/&gt;
 &lt;/**coding**/&gt;
</pre>

is represented in JSON like this:

<pre class="json">
 &quot;coding&quot;: [
   {
     &quot;system&quot; : &quot;http://snomed.info/sct&quot;,
     &quot;code&quot; : &quot;104934005&quot;
   },
   {
     &quot;system&quot; : &quot;http://loinc.org&quot;,
     &quot;code&quot; : &quot;2947-0&quot;
   }
 ]
</pre>

### <span class="sectioncount">1.12.5.2.2<a name="1.12.5.2.2"> </a></span> JSON representation of primitive elements

FHIR elements with primitive values are represented in two parts:

*   A JSON property with the name of the element, which has a JSON type of number, boolean, or string
*   a JSON property with &quot;_&quot; prepended to the name of the element, which, if present, contains the value's xml:id and/or extensions

The FHIR types [integer](datatypes.html#integer) and [decimal](datatypes.html#decimal) are represented as a JSON number, the FHIR type [boolean](datatypes.html#boolean)
as a JSON boolean, and all other types are represented as a JSON string which has the same content as that specified for the relevant data type. Whitespace is always significant 
(i.e. no leading and trailing spaces for non-strings).

<pre class="xml">
 &lt;**code** value=&quot;abc&quot;/&gt; &lt;!-- code --&gt;
 &lt;**date** value=&quot;1972-11-30&quot;/&gt; &lt;!-- dateTime --&gt;
 &lt;**deceased** value=&quot;false&quot; /&gt; &lt;!-- boolean --&gt;
 &lt;**count** value=&quot;23&quot; /&gt;  &lt;!-- integer --&gt;
</pre>

is represented in JSON as

<pre class="json">
 &quot;code&quot; : &quot;abc&quot;,
 &quot;date&quot; : &quot;1972-11-30&quot;,
 &quot;deceased&quot; : false,
 &quot;count&quot; : 23
</pre>
> When using a JavaScript JSON.parse() implementation, keep in mind that JavaScript natively supports only one numeric datatype, which is a floating point number. 
> This can cause loss of precision for FHIR numbers. You may want to use a custom parser and big number library 
> (e.g. [https://github.com/jtobey/javascript-bignum](https://github.com/jtobey/javascript-bignum)) if this is a concern.

If the value has an id attribute, or extensions, then this is represented as follows:

<pre class="xml">
 &lt;**dob** id=&quot;314159&quot; value=&quot;1970-03-30&quot; &gt;
   &lt;extension url=&quot;http://example.org/fhir/extensions#text&quot;&gt;
     &lt;valueString value=&quot;Easter 1970&quot;/&gt;     
   &lt;/extension&gt;
 &lt;/**dob**&gt;
</pre>

is represented in JSON as:

<pre class="json">
 &quot;dob&quot;: &quot;1972-11-30&quot;,
 &quot;_dob&quot;: { 
   &quot;id&quot;: &quot;314159&quot;, 
   &quot;extension&quot;: [{
      &quot;url&quot; : &quot;http://example.org/fhir/extensions#text&quot;,
      &quot;valueString&quot; : &quot;Easter 1970&quot;
   }]
 }
</pre>

Note: If the primitive has an id attribute or extension, but no value, only the property with the &quot;_&quot; is rendered.

In the case where the primitive element may repeat, it is represented 
in two arrays. JSON null values are used to fill out both arrays so 
that the id and/or extension are aligned with the matching value in 
the first array, as demonstrated in this example:

<pre class="xml">
 &lt;**code** value=&quot;au&quot;/&gt;
 &lt;**code** value=&quot;nz&quot;&gt;
   &lt;extension url=&quot;http://hl7.org/fhir/Profile/tools-extensions#display&quot;&gt;
     &lt;valueString value=&quot;New Zealand a.k.a Kiwiland&quot;/&gt;     
   &lt;/extension&gt;
 &lt;/**code**&gt;
</pre>

is represented in JSON as:

<pre class="json">
 &quot;code&quot;: [ &quot;au&quot;, &quot;nz&quot; ],
 &quot;_code&quot;: [ 
   null, 
   { &quot;extension&quot;: [{
      &quot;url&quot; : &quot;http://example.org/fhir/extensions#text&quot;,
      &quot;valueString&quot; : &quot;New Zealand a.k.a Kiwiland&quot;
   }] }
  ]
 }
</pre>

Note: when one of the repeating elements has no value, it is represented in the first array using a null. When
an element has a value but no extension/id, the second array will have a null at the position of that element.

> Design Note: The representation of primitive data types has been 
> split into two parts like this in order to simplify the representation 
> of simple primitive values without id or extensions. This does have the cost of making the 
> representation of the id attribute and extensions more ungainly, but these are both 
> rarely used with primitive data types.

### <span class="sectioncount">1.12.5.2.3<a name="1.12.5.2.3"> </a></span> JSON representation of Elements, and Complex Data types

Elements, and complex [datatypes](datatypes.html) (types that contain named elements of other types) are represented using 
a JSON object, containing a member for each element in the datatype. Composites can have id attributes, which are 
converted to JSON member values, in the same manner as described for primitives. For example:

 <pre class="xml">
&lt;person&gt;
  &lt;text&gt;
    &lt;status value=&quot;generated&quot; /&gt;
    &lt;div xmlns=&quot;http://www.w3.org/1999/xhtml&quot;&gt;&lt;p&gt;...&lt;/p&gt;&lt;/div&gt;
  &lt;/text&gt;
  &lt;name&gt;
    &lt;use value=&quot;official&quot; /&gt;  
    &lt;given value=&quot;Karen&quot; /&gt;
    &lt;family id=&quot;a2&quot; value=&quot;Van&quot; /&gt;
  &lt;/name&gt;
&lt;/person&gt;
</pre>

is represented in JSON as:

<pre class="json">
{
  &quot;person&quot; : {
    &quot;name&quot; : [{
      &quot;use&quot; : &quot;official&quot; ,
      &quot;given&quot; : [ &quot;Karen&quot; ],
      &quot;family&quot; : [ &quot;Van&quot; ]
      &quot;_family&quot; : [ {&quot;id&quot; : &quot;a2&quot;} ]
     }],
    &quot;text&quot; : {
      &quot;status&quot; : &quot;generated&quot; ,
      &quot;div&quot; : &quot;&lt;div xmlns=\&quot;http://www.w3.org/1999/xhtml\&quot;&gt;&lt;p&gt;...&lt;/p&gt;&lt;/div&gt;&quot;
    }
}
</pre>

Things to note here are:

*   Both given and family are repeating XML elements, so they are serialised as an Array whether or not they repeat in this instance
*   In the family part of 'name', the 'id' is added represented in _family as described above
*   The XHTML content in the 'div' element which is in the Narrative element 'text' is represented  as an escaped string in the value property in JSON. The xhtml's root element needs to be a &lt;div&gt; in the xhtml namespace

### <span class="sectioncount">1.12.5.2.4<a name="1.12.5.2.4"> </a></span> JSON representation of Resources

A resource is a JSON object with a property &quot;resourceType&quot; which informs the 
parser which resource type this is:

<pre class="json">
{
  &quot;resourceType&quot; : &quot;Patient&quot;,
  &quot;text&quot; : {
    &quot;status&quot; : &quot;generated&quot; ,
    &quot;div&quot; : &quot;&lt;div xmlns=\&quot;http://www.w3.org/1999/xhtml\&quot;&gt;&lt;p&gt;...&lt;/p&gt;&lt;/div&gt;&quot;
  }
  etc...
}
</pre>

Note that parsers cannot assume that the resourceType property will come first. 

> **Design Note**: This is a problem for several JSON -&gt; Object serialisers that assume that the 
> resourceType property does come first, including [Json.NET](http://james.newtonking.com/json). 
> However some JSON generators do not give the authoring application control of the order of the 
> property values, and so these implementations cannot inter-operate with implementations that make
> assumptions about order. Given that JSON says that the property values are an unordered map of name/value
> pairs, this specification cannot require that properties come in any particular order, though implementers
> may choose to fix the property order if they are able (and the reference platforms provided with this 
> specification do so).

There is [a sample file](json-edge-cases.json) with many edge cases to help test JSON parsers.

<a name="bundle"> </a>
<a name="atom"> </a>
<a name="json-bundles"/>

### <span class="sectioncount">1.12.5.2.5<a name="1.12.5.2.5"> </a></span> JSON Bundle Representation

In JSON [bundles](extras.html#bundle) are represented using a JSON format that is tailored to the specific needs for bundles. 
Each element in the XML feed definition has a JSON corresponding JSON object member with the same name. For convenience, a bundle has a 
&quot;resourceType&quot; property with the value of &quot;Bundle&quot; (&quot;resourceType&quot; is used for consistency with resources, even though a bundle is 
not a resource, but a container of resources). Here is an example feed returning search results for a person query:

<pre class="json">
{
  &quot;resourceType&quot; : &quot;Bundle&quot;,
  &quot;title&quot; : &quot;Search result&quot;,
  &quot;updated&quot; : &quot;2012-09-20T12:04:45.6787909+00:00&quot;,
  &quot;id&quot; : &quot;urn:uuid:50ea3e5e-b6a7-4f55-956c-caef491bbc08&quot;,
  &quot;link&quot; : [{
    &quot;rel&quot; : &quot;self&quot;,
  &quot;href&quot; : &quot;http://ip-0a7a5abe:16287/fhir/person?format=json&quot;
  }],
 <a name="tags"> </a>&quot;category&quot; : [{
    &quot;term&quot; : &quot;[Tag Term]&quot;,
    &quot;label&quot; : &quot;[Tag Label]&quot;,
    &quot;scheme&quot; : &quot;[Tag Scheme]&quot;
  }],
  &quot;totalResults&quot; : 12,
  &quot;entry&quot; : [{
    &quot;title&quot; : &quot;Resource of type Person, with id = 1 and version = 1&quot;,
    &quot;link&quot; : [{
      &quot;rel&quot; : &quot;self&quot;,
      &quot;href&quot; : &quot;http://fhir.furore.com/fhir/person/@1/history/1&quot;
    }],
    &quot;id&quot; : &quot;http://fhir.furore.com/fhir/person/@1&quot;,
    &quot;updated&quot; : &quot;2012-05-29T23:45:32+00:00&quot;,
    &quot;published&quot; : &quot;2012-09-20T12:04:47.3012429+00:00&quot;,
    &quot;author&quot; : [{
      &quot;name&quot; : &quot;Grahame Grieve / HL7 publishing committee&quot;
    }],
    &quot;category&quot; : [{
      &quot;term&quot; : &quot;[Tag Uri]&quot;,
      &quot;label&quot; : &quot;[Tag Label]&quot;,
      &quot;scheme&quot; : &quot;[Tag Type]&quot;
    }],
    &quot;content&quot; : {
      &quot;resourceType&quot; : &quot;Patient&quot;,
      ...other Patient elements...
    },
    &quot;summary&quot; : &quot;&lt;div xmlns=\&quot;http://www.w3.org/1999/xhtml\&quot;&gt;(text summary)&lt;/div&gt;&quot;,
  },
  ... other entries ....
  ],
  &quot;signature&quot; : &quot;&lt;signature xmlns=\&quot;http://www.w3.org/2000/09/xmldsig\&quot;&gt;...&lt;/signature&gt;&quot;
}
</pre>

Note that property names for elements that can repeat are not pluralized for consistency of overall approach (as described above). 
The mime type for a JSON bundle is also application/json+fhir.

<a name="json-bundle-delete"> </a>

#### <span class="sectioncount">1.12.5.2.5.1<a name="1.12.5.2.5.1"> </a></span> Bundling versions - deletion

When returning a set of versions for a resource, a version might indicate a deletion. 
While the XML format follows [RFC 6721](http://www.rfc-editor.org/rfc/rfc6721.txt),
the JSON format needs to use an entry item to retain the logical order of entries:

<pre class="json">
   .. feed ..
   &quot;entry&quot; : [
    ... other entries ....,    
    {
      &quot;deleted&quot; : &quot;2012-05-29T23:45:32+00:00&quot;,
      &quot;id&quot; : &quot;http://fhir.furore.com/fhir/person/@1&quot;,
      &quot;link&quot; : [{
          &quot;rel&quot; : &quot;self&quot;,
          &quot;href&quot; : &quot;http://fhir.furore.com/fhir/person/@1/history/1&quot;
        }],
    }, ... other entries ....
  ]
  ... feed ...
</pre>

The entry is known to be deleted because a date of deletion is given. An id SHALL be provided, and a link may be provided.

<a name="binary"> </a>

#### <span class="sectioncount">1.12.5.2.5.2<a name="1.12.5.2.5.2"> </a></span> Binary Resources

When a [binary resource](extras.html#binary) is represented in a JSON bundle, 
it is represented as base64 encoded content along with a content-type, which is the mime-type 
as it would be specified in HTTP, like this:

<pre class="json">
{
  &quot;resourceType&quot; : &quot;Binary&quot;,
  &quot;contentType&quot; : &quot;[mime type]&quot;,
  &quot;content&quot; : &quot;[base64 of data]&quot;
}
</pre>

<a name="sig"> </a>

#### <span class="sectioncount">1.12.5.2.5.3<a name="1.12.5.2.5.3"> </a></span> Signatures

If a bundle has a signature, the signature has a JSON property &quot;signature&quot;, 
whose property value is an XML string that is a valid
[XML signature](http://www.w3.org/TR/2002/REC-xmldsig-core-20020212/#sec-Signature)
element.

<pre class="json">
{
  &quot;resourceType&quot; : &quot;Bundle&quot;,
  ... metadata and entries as described above....
  &quot;signature&quot; : &quot;&lt;signature xmlns=\&quot;http://www.w3.org/2000/09/xmldsig\&quot;&gt;...&lt;/signature&gt;&quot;
}
</pre>

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
               [Compare to DSTU](http://services.w3.org/htmldiff?doc1=http%3A%2F%2Fhl7.org%2Fimplement%2Fstandards%2Ffhir%2Fjson.html&amp;doc2=http%3A%2F%2Fhl7.org%2Fimplement%2Fstandards%2FFHIR-Develop%2Fjson.html) | 
               [License](license.html) | 
               [Propose a change](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemAdd&amp;tracker_id=677)   
        </span>

			</div>  <!-- /inner-wrapper -->
		</div>  <!-- /container -->
	</div>  <!-- /segment-footer -->
  <!-- disqus thread -->
  <!-- disqus -->
  <!-- end disqus -->        