title: 
date: 
categories: doc
---

[首页](../home/index.html) >[文档](documentation.html) >**数据类型**        


本页内容:

  

*   [数据类型](datatypes.html)
*   [示例](datatypes-examples.html)
*   [详细描述](datatypes-definitions.html)
*   [映射](datatypes-mappings.html)
### 1.17.1  数据类型的示例
这一部分包含了如下数据类型的示例
![](../material/datatypes.png)

#### 1.17.1 基本数据类型

布尔值：

```
<active value="true" />
```
  
负整数：  


```
<score value="-14" />
```

高精度的小数：


```
<pi value="3.14159265358979323846264338327950288419716939937510" />
```

base64编码的字节流：


```
<data value="/9j/4...KAP//Z" /> <!-- covers many lines -->
```

unicode编码的字符串：


```
<caption value="Noodles are called ?? in Chinese" />
```

A uri that points to a website:
<pre class="xml" fragment="uri">&lt;reference value=&quot;http://hl7.org/fhir&quot; /&gt;</pre>

A uri that is a urn:
<pre class="xml" fragment="uri">&lt;id value=&quot;urn:isbn:0451450523&quot; /&gt;</pre>

A date of birth:
<pre class="xml" fragment="date">&lt;date value=&quot;1951-06-04&quot; /&gt;</pre>

An approximate date of birth:
<pre class="xml" fragment="date">&lt;date value=&quot;1951-06&quot; /&gt;</pre>

The instant a document was created, including time zone:
<pre class="xml" fragment="instant">&lt;instant value=&quot;2013-06-08T10:57:34+01:00&quot; /&gt;</pre>

The instant a document was created, expressed in UTC, with milliseconds:
<pre class="xml" fragment="instant">&lt;instant value=&quot;2013-06-08T09:57:34.2112Z&quot; /&gt;</pre>

2:35pm in the afternoon:
<pre class="xml" fragment="time">&lt;time value=&quot;14:35&quot; /&gt;</pre>
</div>

<a name="strings"/>


### <span class="sectioncount">1.17.1.2<a name="1.17.1.2"> </a></span> String Patterns

<div class="example">

A uri that is the root oid of HL7:
<pre class="xml" fragment="oid">&lt;root value=&quot;urn:oid:2.16.840.1.113883&quot; /&gt;</pre>

A uri that is a uuid:
<pre class="xml" fragment="uuid">&lt;id value=&quot;urn:uuid:a5afddf4-e880-459b-876e-e4591b0acc11&quot; /&gt;</pre>

A code:
<pre class="xml" fragment="code">&lt;code value=&quot;acq4+acq5&quot; /&gt;</pre>

A code with single internal space:
<pre class="xml" fragment="code">&lt;code value=&quot;Question 4b&quot; /&gt;</pre>

A numeric id:
<pre class="xml" fragment="code">&lt;id value=&quot;314&quot; /&gt;</pre>

An alphanumeric id:
<pre class="xml" fragment="code">&lt;id value=&quot;alpha-gamma-14&quot; /&gt;</pre>
</div>

<a name="Attachment"/>
<a name="attachment"/>

### <span class="sectioncount">1.17.1.3<a name="1.17.1.3"> </a></span> 
Attachment

See also [Base Definition](datatypes.html#Attachment), [Detailed Descriptions](datatypes-definitions.html#Attachment) and [Mappings](datatypes-mappings.html#Attachment).

<div class="example">

A PDF document:

<pre class="xml" fragment="Attachment">
  &lt;document&gt;
    &lt;contentType value=&quot;application/pdf&quot; /&gt;
    &lt;language value=&quot;en&quot; /&gt;
    &lt;data value=&quot;/9j/4...KAP//Z&quot; /&gt; &lt;!-- covers many lines --&gt;
    &lt;title value=&quot;Definition of Procedure&quot; /&gt;
  &lt;/document&gt;
</pre>
<pre class="json">
  document : {
    contentType :  { value : &quot;application/pdf&quot; },
    language : { value : &quot;en&quot; },
    data :  { value : &quot;/9j/4...KAP//Z&quot;},
    title :  { value : &quot;Definition of Procedure&quot; }
  }
</pre>

Since the JSON examples have the same structure as the XML, only XML is shown for the rest of the examples.

A reference to a DICOM image via WADO:

<pre class="xml" fragment="Attachment">
  &lt;image&gt;
    &lt;contentType value=&quot;application/dicom&quot; /&gt;
    &lt;url value=&quot;http://10.1.2.3:1000/wado?requestType=WADO&amp;amp;wado_details...&quot; /&gt;
    &lt;hash value=&quot;EQH/..AgME&quot; /&gt;
  &lt;/image&gt;
</pre>
</div>

<a name="Identifier"/>
<a name="identifier"/>

### <span class="sectioncount">1.17.1.4<a name="1.17.1.4"> </a></span> 
Identifier

See also [Base Definition](datatypes.html#Identifier), [Detailed Descriptions](datatypes-definitions.html#Identifier) and [Mappings](datatypes-mappings.html#Identifier).

<div class="example">

**Examples**

A primary key from an application table (an OID in the space allocated by HL7
to some organization to further sub-allocate):

<pre class="xml" fragment="Identifier">
  &lt;identifier&gt;
    &lt;use value=&quot;official&quot; /&gt;
    &lt;system value=&quot;urn:oid:2.16.840.1.113883.16.4.3.2.5&quot; /&gt;
    &lt;value value=&quot;123&quot; /&gt;
  &lt;/identifier&gt;
</pre>

A patient identifier defined by a hospital:

<pre class="xml" fragment="Identifier">
  &lt;identifier&gt;
    &lt;use value=&quot;official&quot; /&gt;
    &lt;system value=&quot;http://www.acmehosp.com/patients&quot; /&gt;
    &lt;value value=&quot;44552&quot; /&gt;
    &lt;period&gt;
      &lt;start value=&quot;2003-05-03&quot; /&gt;
    &lt;/period&gt;
  &lt;/identifier&gt;
</pre>

In this case, the period is used to track when the identifier was first assigned to the patient.

An identifier that refers to a patient FHIR resource on a particular system:

<pre class="xml" fragment="Identifier">
  &lt;identifier&gt;
   &lt;system value=&quot;urn:ietf:rfc:3986&quot; /&gt;
   &lt;value value=&quot;http://pas-server/xxx/Patient/443556&quot; /&gt;
  &lt;/identifier&gt;
</pre>

This is not a resource reference - it's a logical reference by the patient identifier.

A UUID:

<pre class="xml" fragment="Identifier">
  &lt;identifier&gt;
    &lt;use value=&quot;temp&quot; /&gt;
    &lt;system value=&quot;urn:ietf:rfc:3986&quot; /&gt;
    &lt;value value=&quot;urn:uuid:a76d9bbf-f293-4fb7-ad4c-2851cac77162&quot; /&gt;
  &lt;/identifier&gt;
</pre>

UUIDs are often used for temporary identifiers, though this is not necessary.

A US SSN:

<pre class="xml" fragment="Identifier">
  &lt;identifier&gt;
    &lt;use value=&quot;usual&quot; /&gt;
    &lt;label value=&quot;SSN&quot; /&gt;
    &lt;system value=&quot;http://hl7.org/fhir/sid/us-ssn&quot; /&gt;
    &lt;value value=&quot;000111111&quot; /&gt;
  &lt;/identifier&gt;
</pre>

Notes:

*   US SSNs are often presented like this: 000-11-1111, the dashes are for presentation and should be removed, as specified in the [definition of ssn-us](terminologies-systems.html#identifiersystems)
*   The use of &quot;usual&quot; means that this institution prefers to use SSN when identifying the patient

A medical record number assigned on 5-July 2009:

<pre class="xml" fragment="Identifier">
  &lt;identifier&gt;
    &lt;use value=&quot;usual&quot; /&gt;
    &lt;label value=&quot;MRN&quot; /&gt;
    &lt;system value=&quot;urn:oid:0.1.2.3.4.5.6.7&quot; /&gt;
    &lt;value value=&quot;2356&quot; /&gt;
    &lt;period&gt;
      &lt;start value=&quot;2009-07-05&quot; /&gt;
    &lt;/period&gt;
  &lt;/identifier&gt;
</pre>
</div>

<a name="Coding"/>
<a name="coding"/>

### <span class="sectioncount">1.17.1.5<a name="1.17.1.5"> </a></span> Coding

See also [Base Definition](datatypes.html#Coding), [Detailed Descriptions](datatypes-definitions.html#Coding) and [Mappings](datatypes-mappings.html#Coding).

<div class="example">

**Examples**

A simple code for headache, in ICD-10:

<pre class="xml" fragment="Coding">
  &lt;code&gt;
    &lt;system value=&quot;http://hl7.org/fhir/sid/icd-10&quot; /&gt;
    &lt;code value=&quot;G44.1&quot; /&gt;
  &lt;/code&gt;
</pre>

A SNOMED CT expression:

<pre class="xml" fragment="Coding">
  &lt;problem&gt;
    &lt;system value=&quot;http://snomed.info/sct&quot; /&gt;
    &lt;code value=&quot;128045006:{363698007=56459004}&quot; /&gt;
  &lt;/problem&gt;
</pre>
</div>

<a name="CodeableConcept"/>
<a name="codeableconcept"/>

### <span class="sectioncount">1.17.1.6<a name="1.17.1.6"> </a></span> 
CodeableConcept

See also [Base Definition](datatypes.html#CodeableConcept), [Detailed Descriptions](datatypes-definitions.html#CodeableConcept) and [Mappings](datatypes-mappings.html#CodeableConcept).

<div class="example">

**Examples**

A simple code for headache initially coded in SNOMED CT (by picking the SNOMED CT code from a pick-list), and then translated to ICD-10:

<pre class="xml" fragment="CodeableConcept">
  &lt;concept&gt;
    &lt;coding&gt;
      &lt;system value=&quot;http://hl7.org/fhir/sid/icd-10&quot; /&gt;
      &lt;code value=&quot;R51&quot; /&gt;
    &lt;/coding&gt;
    &lt;coding&gt;
      &lt;system value=&quot;http://snomed.info/sct&quot; /&gt;
      &lt;code value=&quot;25064002&quot; /&gt;
      &lt;display value=&quot;Headache&quot; /&gt;
      &lt;primary value=&quot;true&quot; /&gt;
    &lt;/coding&gt;
    &lt;text value=&quot;general headache&quot; /&gt;
  &lt;/concept&gt;
</pre>

A concept represented in an institution's local coding systems for unit for which no UCUM equivalent exists:

<pre class="xml" fragment="CodeableConcept">
  &lt;unit&gt;
    &lt;coding&gt;
      &lt;system value=&quot;urn:oid:2.16.840.1.113883.19.5.2&quot; /&gt;
      &lt;code value=&quot;tab&quot; /&gt;
      &lt;display value=&quot;Tablet&quot; /&gt;
    &lt;/coding&gt;
    &lt;coding&gt;
      &lt;system value=&quot;http://unitsofmeasure.org&quot; /&gt;
    &lt;/coding&gt;
  &lt;/unit&gt;
</pre>

A SNOMED CT expression:

<pre class="xml" fragment="CodeableConcept">
  &lt;diagnosis&gt;
    &lt;coding&gt;
      &lt;system value=&quot;http://snomed.info/sct&quot; /&gt;
      &lt;code value=&quot;128045006:{363698007=56459004}&quot; /&gt;
    &lt;/coding&gt;
    &lt;text value=&quot;Cellulitis of the foot&quot; /&gt;
  &lt;/diagnosis&gt;
</pre>

In this case, there is no display element, because no display is defined for SNOMED CT expressions.

Using the valueset:

The results on a urinalysis strip:

<pre class="xml" fragment="Coding">
  &lt;valueCoding&gt;
    &lt;system value=&quot;http://example.org/codes/simple-grades&quot; /&gt;
    &lt;code value=&quot;+&quot; /&gt;
    &lt;valueSet&gt;
      &lt;reference url=&quot;ValueSet/simple-grades&quot; /&gt;
    &lt;/valueSet&gt;
  &lt;/valueCoding&gt;
</pre>

And where the value set would be something like this:

<pre>
  &lt;ValueSet xmlns=&quot;http://hl7.org/fhir&quot;&gt;
    &lt;text&gt;
      &lt;status value=&quot;generated&quot;/&gt;
      &lt;div xmlns=&quot;http://www.w3.org/1999/xhtml&quot;&gt;
        &lt;p&gt;Possible Clinistix codes: neg, trace, +, ++, and +++&lt;/p&gt;
      &lt;/div&gt;
    &lt;/text&gt;
    &lt;identifier value=&quot;http://hl7.org/fhir/vs/clinistix&quot;/&gt;
    &lt;name value=&quot;Codes for Clinistix&quot;/&gt;
    &lt;publisher value=&quot;HL7&quot;/&gt;
    &lt;telecom&gt;
      &lt;system value=&quot;url&quot;/&gt;
      &lt;value value=&quot;http://hl7.org/fhir&quot;/&gt;
    &lt;/telecom&gt;
    &lt;description value=&quot;Clinistix Codes&quot;/&gt;
    &lt;status value=&quot;draft&quot;/&gt;
    &lt;experimental value=&quot;true&quot;/&gt;
    &lt;date value=&quot;2013-10-01&quot;/&gt;
    &lt;define&gt;
      &lt;system value=&quot;http://hl7.org/fhir/clinistix&quot;/&gt;
      &lt;caseSensitive value=&quot;false&quot;/&gt;
      &lt;concept&gt;
        &lt;code value=&quot;neg&quot;/&gt;
      &lt;/concept&gt;
      &lt;concept&gt;
        &lt;code value=&quot;trace&quot;/&gt;
      &lt;/concept&gt;
      &lt;concept&gt;
        &lt;code value=&quot;+&quot;/&gt;
      &lt;/concept&gt;
      &lt;concept&gt;
        &lt;code value=&quot;+&quot;/&gt;
      &lt;/concept&gt;
      &lt;concept&gt;
        &lt;code value=&quot;++&quot;/&gt;
      &lt;/concept&gt;
      &lt;concept&gt;
        &lt;code value=&quot;+++&quot;/&gt;
      &lt;/concept&gt;
    &lt;/define&gt;
  &lt;/ValueSet&gt;
</pre>
</div>
<a name="Quantity"/>
<a name="quantity"/>
<a name="age"/>
<a name="distance"/>
<a name="duration"/>
<a name="count"/>
<a name="money"/>

### <span class="sectioncount">1.17.1.7<a name="1.17.1.7"> </a></span> 
Quantity

See also [Base Definition](datatypes.html#Quantity), [Detailed Descriptions](datatypes-definitions.html#Quantity) and [Mappings](datatypes-mappings.html#Quantity).

<div class="example">

**Examples**

A duration:

<pre class="xml" fragment="Quantity">
  &lt;time&gt;
    &lt;value value=&quot;25&quot; /&gt;
    &lt;units value=&quot;sec&quot; /&gt;
    &lt;system value=&quot;http://unitsofmeasure.org&quot; /&gt;
    &lt;code value=&quot;s&quot; /&gt;
  &lt;/time&gt;
</pre>

A concentration where the value was out of range:

<pre class="xml" fragment="Quantity">
  &lt;result&gt;
    &lt;value value=&quot;40000&quot; /&gt;
    &lt;comparator value=&quot;&amp;gt;&quot; /&gt;
    &lt;units value=&quot;mcg/L&quot; /&gt;
    &lt;system value=&quot;http://unitsofmeasure.org&quot; /&gt;
    &lt;code value=&quot;ug&quot; /&gt;
  &lt;/result&gt;
</pre>

An amount of prescribed medication:

<pre class="xml" fragment="Quantity">
  &lt;dose&gt;
    &lt;value value=&quot;3&quot; /&gt;
    &lt;units value=&quot;capsules&quot; /&gt;
    &lt;system value=&quot;http://snomed.info/sct&quot; /&gt;
    &lt;code value=&quot;385049006&quot; /&gt;
  &lt;/dose&gt;
</pre>

A price (coded using currency codes defined in ISO 4217):

<pre class="xml" fragment="Quantity">
  &lt;cost&gt;
    &lt;value value=&quot;25.45&quot; /&gt;
    &lt;units value=&quot;US$&quot; /&gt;
    &lt;system value=&quot;urn:std:iso:4217&quot; /&gt;
    &lt;code value=&quot;USD&quot; /&gt;
  &lt;/cost&gt;
</pre>
</div>

<a name="Range"/>
<a name="range"/>

### <span class="sectioncount">1.17.1.8<a name="1.17.1.8"> </a></span> 
Range

See also [Base Definition](datatypes.html#Range), [Detailed Descriptions](datatypes-definitions.html#Range) and [Mappings](datatypes-mappings.html#Range).

<div class="example">

**Examples**

Range of Quantity (distance):

<pre class="xml" fragment="Range">
  &lt;estimate&gt;
   &lt;low&gt;
     &lt;value value=&quot;1.6&quot; /&gt;
     &lt;units value=&quot;m&quot; /&gt;
   &lt;/low&gt;
   &lt;high&gt;
     &lt;value value=&quot;1.9&quot; /&gt;
     &lt;units value=&quot;m&quot; /&gt;
   &lt;/high&gt;
  &lt;/estimate&gt;
</pre>
</div>
<a name="Ratio"/>
<a name="ratio"/>

### <span class="sectioncount">1.17.1.9<a name="1.17.1.9"> </a></span> 
Ratio

See also [Base Definition](datatypes.html#Ratio), [Detailed Descriptions](datatypes-definitions.html#Ratio) and [Mappings](datatypes-mappings.html#Ratio).

<div class="example">

**Examples**

Titer (Ratio of integer:integer)

<pre class="xml" fragment="Ratio">
  &lt;result&gt;
   &lt;numerator&gt;
     &lt;value value=&quot;1&quot; /&gt;
   &lt;/numerator&gt;
   &lt;denominator&gt;
     &lt;value value=&quot;128&quot; /&gt;
   &lt;/denominator&gt;
  &lt;/result&gt;
</pre>

Unit cost (Ratio of
Money:Quantity):

<pre class="xml" fragment="Ratio">
  &lt;charge&gt;
   &lt;numerator&gt;
     &lt;value value=&quot;103.50&quot; /&gt;
     &lt;units value=&quot;US$&quot; /&gt;
     &lt;code value=&quot;USD&quot; /&gt;
     &lt;system value=&quot;urn:std:iso:4217&quot; /&gt;
   &lt;/numerator&gt;
   &lt;denominator&gt;
     &lt;value value=&quot;1&quot; /&gt;
     &lt;units value=&quot;day&quot; /&gt;
     &lt;code value=&quot;day&quot; /&gt;
     &lt;system value=&quot;http://unitsofmeasure.org&quot; /&gt;
   &lt;/denominator&gt;
  &lt;/charge&gt;
</pre>
</div>
<a name="Period"/>
<a name="period"/>

### <span class="sectioncount">1.17.1.10<a name="1.17.1.10"> </a></span> 
Period

See also [Base Definition](datatypes.html#Period), [Detailed Descriptions](datatypes-definitions.html#Period) and [Mappings](datatypes-mappings.html#Period).

<div class="example">

**Examples**

23rd May 2011 to 27th May, including 27th May:

<pre class="xml" fragment="Period">
  &lt;coverage&gt;
   &lt;start value=&quot;2011-05-23&quot; /&gt;
   &lt;end value=&quot;2011-05-27&quot; /&gt;
  &lt;/coverage&gt;
</pre>
</div>

<a name="SampledData"/>
<a name="sampleddata"/>

### <span class="sectioncount">1.17.1.11<a name="1.17.1.11"> </a></span> 
SampledData

See also [Base Definition](datatypes.html#SampledData), [Detailed Descriptions](datatypes-definitions.html#SampledData) and [Mappings](datatypes-mappings.html#SampledData).

<div class="example">

**Example**

The output from an EKG device:

<pre class="xml" fragment="SampledData">
 &lt;sampledData&gt;
  &lt;origin&gt;
   &lt;value value=&quot;0&quot;/&gt;
   &lt;units value=&quot;μV&quot;/&gt;
   &lt;system value=&quot;http://unitsofmeasure.org&quot;/&gt;
   &lt;code value=&quot;uV&quot;/&gt;
  &lt;/origin&gt;
  &lt;period value=&quot;2&quot;/&gt;
  &lt;factor value=&quot;2.5&quot;/&gt;
  &lt;dimensions value=&quot;1&quot;/&gt;
  &lt;data value=&quot;-4 -13 -18 -18 -18 -17 -16 -16 -16 -16 -16 -17 -18 -18 -18 ....&quot;/&gt;
 &lt;/sampledData&gt;
</pre>
</div>
<a name="HumanName"/>
<a name="humanname"/>

### <span class="sectioncount">1.17.1.12<a name="1.17.1.12"> </a></span> 
HumanName

See also [Base Definition](datatypes.html#HumanName), [Detailed Descriptions](datatypes-definitions.html#HumanName) and [Mappings](datatypes-mappings.html#HumanName).

<div class="example">

A Simple example

<pre class="xml" fragment="HumanName">
&lt;name&gt;
  &lt;family value=&quot;Everyman&quot; /&gt;
  &lt;given value=&quot;Adam&quot; /&gt;
  &lt;given value=&quot;A.&quot; /&gt;
&lt;/name&gt;
</pre>

Composite names

<pre class="xml" fragment="HumanName">
&lt;name&gt;
  &lt;family value=&quot;Contrata&quot; /&gt;
  &lt;given value=&quot;Mary Jane&quot; /&gt;
&lt;/name&gt;
</pre>

These cases can be quite ambiguous - is &quot;Mary Jane&quot; one name, or two? Different systems,
and data enterers may treat this differently, and the person themselves may not know.
Parts are allowed to contain spaces, but systems should consider how to treat
these cases. Composite names separated by &quot;-&quot; should be treated as a single name part.

A common pattern: a person is called by a name other than that expected from their official name (first given name in most cultures).

<pre class="xml" fragment="HumanName">
&lt;name&gt;
  &lt;use value=&quot;official&quot; /&gt;
  &lt;family value=&quot;Chalmers&quot; /&gt;
  &lt;given value=&quot;Peter&quot; /&gt;
  &lt;given value=&quot;James&quot; /&gt;
&lt;/name&gt;
&lt;name&gt;
  &lt;use value=&quot;usual&quot; /&gt;
  &lt;given value=&quot;Jim&quot; /&gt;
&lt;/name&gt;
</pre>

This same pattern is often encountered with immigrants, who retain their real name for official use, but adopt a localized name for everyday use:

<pre class="xml" fragment="HumanName">
&lt;name&gt;
  &lt;use value=&quot;official&quot; /&gt;
  &lt;family value=&quot;Sczypinski&quot; /&gt;
  &lt;given value=&quot;Piotr&quot; /&gt;
  &lt;given value=&quot;Andre&quot; /&gt;
&lt;/name&gt;
&lt;name&gt;
  &lt;use value=&quot;usual&quot; /&gt;
  &lt;family value=&quot;Skipper&quot; /&gt;
  &lt;given value=&quot;Jim&quot; /&gt;
&lt;/name&gt;
</pre>
</div>

<div class="example">

Karen van Hentenryck is of Dutch origin, and the &quot;van&quot; is a voorvoegsel.

<pre class="xml" fragment="HumanName">
&lt;name&gt;
  &lt;use value=&quot;official&quot; /&gt;
  &lt;family value=&quot;van&quot;&gt;
    &lt;extension url=&quot;http://hl7.org/fhir/StructureDefinition/iso21090-EN-qualifier&quot; &gt;
	   &lt;valueCode value=&quot;VV&quot; /&gt;
    &lt;/extension&gt;
  &lt;/family&gt;
  &lt;family value=&quot;Hentenryck&quot; /&gt;
  &lt;given value=&quot;Karen&quot; /&gt;
&lt;/name&gt;
</pre>

See [the Extensibility Example for more information](extensibility-examples.html).
Note that this name has multiple family name parts. Systems that do not support as many name parts
as are provided in an instance they are processing may wish to append parts together using spaces,
so that this becomes &quot;van Hentenryck&quot;.

</div>

<div class="example">

Complex example from Germany: Dr.phil. Regina Johanna Maria Gräfin Hochheim-Weilenfels, NCFSA. This example shows extensive use of
multiple given names, prefixes, suffixes, for academic degrees, nobility titles, and professional designations.

<pre class="xml" fragment="HumanName">
&lt;name&gt;
  &lt;use value=&quot;official&quot; /&gt;
  &lt;family value=&quot;Hochheim-Weilenfels&quot; /&gt;
  &lt;given value=&quot;Regina&quot; /&gt;
  &lt;given value=&quot;Johanna&quot; /&gt;
  &lt;given value=&quot;Maria&quot; /&gt;
  &lt;prefix value=&quot;Gräfin&quot;&gt;
    &lt;extension url=&quot;http://hl7.org/fhir/StructureDefinition/iso21090-EN-qualifier&quot; &gt;
      &lt;valueCode value=&quot;NB&quot; /&gt;
    &lt;/extension&gt;
  &lt;/prefix&gt;
  &lt;prefix value=&quot;Dr. phil.&quot;&gt;
    &lt;extension url=&quot;http://hl7.org/fhir/StructureDefinition/iso21090-EN-qualifier&quot; &gt;
      &lt;valueCode value=&quot;AC&quot; /&gt;
    &lt;/extension&gt;
  &lt;/prefix&gt;
  &lt;suffix value=&quot;NCFSA&quot; /&gt;
&lt;/name&gt;
&lt;name&gt;
  &lt;use value=&quot;maiden&quot; /&gt;
  &lt;family value=&quot;Hochheim&quot; /&gt;
&lt;/name&gt;
</pre>

This example makes use of the ISO 21090 extensions to carry the rare ISO 21090 qualifier attributes &quot;AC&quot; and &quot;NB&quot;.

</div>

<div class="example">

Japanese example in the three forms: ideographic (Kanji), syllabic (Hiragana) and alphabetic (Romaji).

<pre class="xml" fragment="HumanName">
&lt;name&gt;
  &lt;family value=&quot;??&quot; /&gt;
  &lt;given value=&quot;??&quot; /&gt;
  &lt;/name&gt;
&lt;name&gt;
 &lt;family value=&quot;???&quot; /&gt;
 &lt;given value=&quot;???&quot; /&gt;
&lt;/name&gt;
&lt;name&gt;
  &lt;family value=&quot;KIMURA&quot; /&gt;
  &lt;given value=&quot;MICHIO&quot; /&gt;
&lt;/name&gt;
</pre>

The three forms are differentiated by the character subset each contains.

</div>

<div class="example">

Russian example in the two forms: cyrillic, and latin:

<pre class="xml" fragment="HumanName">
&lt;name&gt;
  &lt;family value=&quot;??????&quot; /&gt;
  &lt;given value=&quot;????&quot; /&gt;
  &lt;given value=&quot;????????????&quot; /&gt;
&lt;/name&gt;
&lt;name&gt;
  &lt;family value=&quot;EMELIN&quot; /&gt;
  &lt;given value=&quot;IVAN&quot; /&gt;
  &lt;given value=&quot;VLADIMIROVICH&quot; /&gt;
&lt;/name&gt;
</pre>

In  Russian  usage, these names are known as
the domestic and foreign names respectively. The two forms are differentiated by the character subset each contains.

</div>

<div class="example">

Scandinavian example: Erikson is the family name. Jan Erik are the given names, and Östlund the family name of the mother, which is taken as a Mellannamn.

<pre class="xml" fragment="HumanName">
&lt;name&gt;
  &lt;use value=&quot;official&quot; /&gt;
  &lt;family value=&quot;Erikson&quot; /&gt;
  &lt;given value=&quot;Jan&quot; /&gt;
  &lt;given value=&quot;Erik&quot; /&gt;
  &lt;given value=&quot;Östlund&quot;&gt;
    &lt;extension url=&quot;http://hl7.org/fhir/StructureDefinitioniso-20190#name-qualifier&quot; &gt;
      &lt;valueCoding&gt;
         &lt;code value=&quot;MID&quot; /&gt;
         &lt;system value=&quot;http://hl7.org/fhir/v3/EntityNamePartQualifier2&quot; /&gt;
      &lt;/valueCoding&gt;
    &lt;/extension&gt;
  &lt;/given&gt;
&lt;/name&gt;
</pre>

This example makes use of the ISO 21090 extension to carry the culture specific ISO 21090 qualifier attribute &quot;MID&quot; for the Mellannamn.

Then Jan Erikson has a daughter, Karin, with his wife Margrete Hansen. The first communications of the new born
name is &quot;Margrete Jente&quot; (Margrete's Girl) and the mother's family name, not the given name (Karin). The
father's Family name is  not used at all. This is a known temporary name assigned directly after the birth of
the child.

<pre class="xml" fragment="HumanName">
&lt;name&gt;
  &lt;use value=&quot;temp&quot; /&gt;
  &lt;!-- use could be OR+OLD, depends how record keeping is done --&gt;
  &lt;family value=&quot;Hansen&quot; /&gt;
  &lt;given value=&quot;Margrete Jente&quot; /&gt;
&lt;/name&gt;
</pre>

The baby's name is subsequently changed to the fathers' family name, and to use the mother's name as
mellomnamn.

<pre class="xml" fragment="HumanName">
&lt;name&gt;
  &lt;use value=&quot;official&quot; /&gt;
  &lt;family value=&quot;Erikson&quot; /&gt;
  &lt;given value=&quot;Karin&quot; /&gt;
  &lt;given value=&quot;Hansen&quot;&gt;
    &lt;extension url=&quot;http://hl7.org/fhir/StructureDefinitioniso-20190#name-qualifier&quot; &gt;
      &lt;valueCoding&gt;
         &lt;code value=&quot;MID&quot; /&gt;
         &lt;system value=&quot;http://hl7.org/fhir/v3/EntityNamePartQualifier2&quot; /&gt;
      &lt;/valueCoding&gt;
    &lt;/extension&gt;
  &lt;/given&gt;
&lt;/name&gt;
</pre>

Later, Karin gets married to Per Berg, and decides to adopts Berg as her family name, and also decides to use
Erikson as the mellom navn. (Note: Karin could have chosen to use another mellom navn, e.g. the family name of
her mother, her father or other family names as specified by naming laws of the country in question).

<pre class="xml" fragment="HumanName">
&lt;name&gt;
  &lt;use value=&quot;old&quot; /&gt;
  &lt;family value=&quot;Erikson&quot; /&gt;
  &lt;given value=&quot;Karin&quot; /&gt;
  &lt;given value=&quot;Hansen&quot;&gt;
    &lt;extension url=&quot;http://hl7.org/fhir/StructureDefinitioniso-20190#name-qualifier&quot; &gt;
      &lt;valueCoding&gt;
        &lt;code value=&quot;MID&quot; /&gt;
        &lt;system value=&quot;http://hl7.org/fhir/v3/EntityNamePartQualifier2&quot; /&gt;
      &lt;/valueCoding&gt;
    &lt;/extension&gt;
  &lt;/given&gt;
&lt;/name&gt;
&lt;name&gt;
  &lt;use value=&quot;official&quot; /&gt;
  &lt;family value=&quot;Berg&quot; /&gt;
  &lt;given value=&quot;Karin&quot; /&gt;
  &lt;given value=&quot;Erikson&quot;&gt;
    &lt;extension url=&quot;http://hl7.org/fhir/StructureDefinitioniso-20190#name-qualifier&quot; &gt;
      &lt;valueCoding&gt;
        &lt;code value=&quot;MID&quot; /&gt;
        &lt;system value=&quot;http://hl7.org/fhir/v3/EntityNamePartQualifier2&quot; /&gt;
      &lt;/valueCoding&gt;
    &lt;/extension&gt;
  &lt;/given&gt;
&lt;/name&gt;
&lt;name&gt;
  &lt;use value=&quot;usual&quot; /&gt;
  &lt;family value=&quot;Berg&quot; /&gt;
  &lt;given value=&quot;Karin&quot; /&gt;
&lt;/name&gt;
</pre>
</div>

#### <span class="sectioncount">1.17.1.12.1<a name="1.17.1.12.1"> </a></span> W3C International Examples

These examples are taken from the [W3C International Examples](http://www.w3.org/International/questions/qa-personal-names),
which should be consulted for further information.

A patronymic is &quot;The part of a name that links to the genealogy&quot;:

<pre class="xml" fragment="HumanName">
&lt;name&gt;
  &lt;text value=&quot;Björk Guðmundsdóttir&quot;/&gt;
  &lt;family value=&quot;Guðmundsdóttir&quot;/&gt;
  &lt;given value=&quot;Björk&quot;/&gt;
&lt;/name&gt;
</pre>

A patronymic with a &quot;son/daughter of&quot; appellation:

<pre class="xml" fragment="HumanName">
&lt;name&gt;
  &lt;text value=&quot;Isa bin Osman&quot;/&gt;
  &lt;family value=&quot;bin Osman&quot;/&gt;
  &lt;given value=&quot;Isa&quot;/&gt;
&lt;/name&gt;
</pre>

Note: The family name may also be given as two different family names.

A Chinese name with a generational name:

<pre class="xml" fragment="HumanName">
&lt;name&gt;
  &lt;text value=&quot;???&quot;/&gt; &lt;!-- left to right --&gt;
  &lt;family value=&quot;?&quot;/&gt;
  &lt;given value=&quot;?&quot;/&gt;
  &lt;given value=&quot;?&quot;/&gt;
&lt;/name&gt;
&lt;name&gt;
  &lt;text value=&quot;Mao Ze Dong&quot;/&gt; &lt;!-- left to right --&gt;
  &lt;family value=&quot;Mao&quot;/&gt;
  &lt;given value=&quot;Ze&quot;/&gt;
  &lt;given value=&quot;Dong&quot;/&gt;
&lt;/name&gt;
</pre>

_Todo: is there a need to identify the given name that is the generational name_.

Additional Western name (see also example above):

<pre class="xml" fragment="HumanName">
&lt;name&gt;
  &lt;use value=&quot;official&quot; /&gt;
  &lt;family value=&quot;Yao&quot; /&gt;
  &lt;given value=&quot;Ming&quot; /&gt;
&lt;/name&gt;
&lt;name&gt;
  &lt;use value=&quot;usual&quot; /&gt;
  &lt;given value=&quot;Fred&quot; /&gt;
&lt;/name&gt;
</pre>

Multiple Family names:

<pre class="xml" fragment="HumanName">
&lt;name&gt;
  &lt;family value=&quot;Carreño&quot; /&gt;
  &lt;family value=&quot;Quiñones&quot; /&gt;
  &lt;given value=&quot;María-Jose&quot; /&gt;
&lt;/name&gt;
</pre>

Brazilian Example:

<pre class="xml" fragment="HumanName">
&lt;name&gt;
  &lt;family value=&quot;Eduardo&quot; /&gt;
  &lt;family value=&quot;Santos&quot; /&gt;
  &lt;family value=&quot;Tavares&quot; /&gt;
  &lt;family value=&quot;Melo&quot; /&gt;
  &lt;family value=&quot;Silva&quot; /&gt;
  &lt;given value=&quot;José&quot; /&gt;
&lt;/name&gt;
</pre>

Russian Examples (using Cyrillic):

<pre class="xml" fragment="HumanName">
&lt;name&gt;
  &lt;family value=&quot;??????????&quot; /&gt;
  &lt;family value=&quot;??????&quot; /&gt;
  &lt;given value=&quot;?????&quot; /&gt;
&lt;/name&gt;
&lt;name&gt;
  &lt;family value=&quot;?????????&quot; /&gt;
  &lt;family value=&quot;???????&quot; /&gt;
  &lt;given value=&quot;?????&quot; /&gt;
&lt;/name&gt;
</pre>

Example with Initial:

<pre class="xml" fragment="HumanName">
&lt;name&gt;
  &lt;family value=&quot;Public&quot; /&gt;
  &lt;given value=&quot;John&quot; /&gt;
  &lt;given value=&quot;Q.&quot; /&gt;
&lt;/name&gt;
</pre>

Other Examples:

<pre class="xml" fragment="HumanName">
&lt;name&gt;
  &lt;text value=&quot;Velikkakathu Sankaran Achuthanandan&quot;/&gt;
  &lt;family value=&quot;Velikkakathu&quot; /&gt;
  &lt;given value=&quot;Sankaran&quot; /&gt;
  &lt;given value=&quot;Achuthanandan&quot; /&gt;
&lt;/name&gt;
&lt;name&gt;
  &lt;text value=&quot;Kogaddu Birappa Timappa Nair&quot;/&gt;
  &lt;family value=&quot;Nair&quot; /&gt;
  &lt;given value=&quot;Birappa&quot; /&gt;
  &lt;given value=&quot;Timappa&quot; /&gt;
  &lt;prefix value=&quot;Kogaddu&quot; /&gt;
&lt;/name&gt;
&lt;name&gt;
  &lt;text value=&quot;Aditya Pratap Singh Chauhan&quot;/&gt;
  &lt;family value=&quot;Singh&quot; /&gt;
  &lt;given value=&quot;Aditya&quot; /&gt;
  &lt;given value=&quot;Pratap&quot; /&gt;
  &lt;suffix value=&quot;Chauhan&quot; /&gt;
&lt;/name&gt;
&lt;name&gt;
  &lt;text value=&quot;Madurai Mani Iyer&quot;/&gt;
  &lt;given value=&quot;Mani&quot; /&gt;
  &lt;prefix value=&quot;Madurai&quot; /&gt;
  &lt;suffix value=&quot;Iyer&quot; /&gt;
&lt;/name&gt;
&lt;name&gt;
  &lt;text value=&quot;Abu Karim Muhammad al-Jamil ibn Nidal ibn Abdulaziz al-Filistini&quot;/&gt;
  &lt;family value=&quot;ibn Nidal&quot; /&gt;
  &lt;family value=&quot;ibn Abdulaziz&quot; /&gt;
  &lt;given value=&quot;Muhammad&quot; /&gt;
  &lt;given value=&quot;al-Jamil&quot; /&gt;
  &lt;prefix value=&quot;Abu Karim&quot; /&gt;
  &lt;suffix value=&quot;al-Filistini&quot; /&gt;
&lt;/name&gt;
</pre>

_Todo: need to discuss this with Indian / Arabic implementers_.
Note that collecting and storing the _text_ element makes the
primary purpose of the structured parts for index/searching, and
fidelity of the name parts is not critical.

<a name="Address"/>
<a name="address"/>

### <span class="sectioncount">1.17.1.13<a name="1.17.1.13"> </a></span> 
Address

See also [Base Definition](datatypes.html#Address), [Detailed Descriptions](datatypes-definitions.html#Address) and [Mappings](datatypes-mappings.html#Address).

<div class="example">

**Example**

HL7 office's address.

<pre class="xml" fragment="Address">
  &lt;address&gt;
   &lt;use value=&quot;work&quot; /&gt;
   &lt;text value=&quot;1050 W Wishard Blvd
RG
         5th floor
Indianapolis, IN 46240&quot; /&gt;
   &lt;line value=&quot;1050 W Wishard Blvd&quot; /&gt;
   &lt;line value=&quot;RG 5th floor&quot; /&gt;
   &lt;city value=&quot;Indianapolis&quot; /&gt;
   &lt;state value=&quot;IN&quot; /&gt;
   &lt;postalCode value=&quot;46240&quot; /&gt;
  &lt;/address&gt;
</pre>

A UK example address.

<pre class="xml" fragment="Address">
  &lt;address&gt;
    &lt;extension url=&quot;http://hl7.org/fhir/StructureDefinition/iso21090-ADXP-county&quot; &gt; &lt;!-- todo: review this --&gt;
      &lt;valueString value=&quot;HUDDERSFIELD&quot;/&gt;
    &lt;/extension&gt;
    &lt;text value=&quot;1 Back Lane&amp;#13;&amp;#10;Holmfirth&amp;#13;&amp;#10;HUDDERSFIELD&amp;#13;&amp;#10;HD7 1HQ&quot;/&gt;
    &lt;line value=&quot;1 Back Lane&quot;/&gt;
    &lt;city value=&quot;Holmfirth&quot;/&gt;
    &lt;postalCode value=&quot;HD7 1HQ&quot;/&gt;
  &lt;/address&gt;
</pre>

A Postal address - i.e. an address that it doesn't make sense to try and visit.

<pre class="xml" fragment="Address">
  &lt;address&gt;
    &lt;extension url=&quot;http://hl7.org/fhir/StructureDefinition/iso21090-AD-use&quot;&gt; &lt;!-- todo: review this --&gt;
      &lt;valueCode value=&quot;PST&quot;/&gt;
    &lt;/extension&gt;
    &lt;line value=&quot;PO Box 31445&quot;/&gt;
    &lt;city value=&quot;Erewhon&quot;/&gt;
    &lt;postalCode value=&quot;0001&quot;/&gt;
  &lt;/address&gt;
</pre>
</div>

<a name="ContactPoint"/>
<a name="contactpoint"/>

### <span class="sectioncount">1.17.1.14<a name="1.17.1.14"> </a></span> 
ContactPoint

See also [Base Definition](datatypes.html#ContactPoint), [Detailed Descriptions](datatypes-definitions.html#ContactPoint) and [Mappings](datatypes-mappings.html#ContactPoint).

<div class="example">

**Example**

Home phone number:

<pre class="xml" fragment="ContactPoint">
  &lt;telecom&gt;
   &lt;system value=&quot;phone&quot; /&gt;
   &lt;value value=&quot;+15556755745&quot; /&gt;
   &lt;use value=&quot;home&quot; /&gt;
  &lt;/telecom&gt;
</pre>
</div>

<a name="Timing"/>
<a name="timing"/>

### <span class="sectioncount">1.17.1.15<a name="1.17.1.15"> </a></span> 
Timing

See also [Base Definition](datatypes.html#Timing), [Detailed Descriptions](datatypes-definitions.html#Timing) and [Mappings](datatypes-mappings.html#Timing).

<div class="example">

**Example**

A series of appointments for radiotherapy:

<pre class="xml" fragment="Timing">
  &lt;schedule&gt;
    &lt;event&gt;
      &lt;start value=&quot;2012-01-07T09:00:00+10:00&quot; /&gt;
      &lt;end value=&quot;2012-01-07T13:00:00+10:00&quot; /&gt;
    &lt;/event&gt;
    &lt;event&gt;
      &lt;start value=&quot;2012-01-14T09:00:00+10:00&quot; /&gt;
      &lt;end value=&quot;2012-01-14T13:00:00+10:00&quot; /&gt;
    &lt;/event&gt;
    &lt;event&gt;
      &lt;start value=&quot;2012-01-22T11:00:00+10:00&quot; /&gt;
      &lt;end value=&quot;2012-01-22T15:00:00+10:00&quot; /&gt;
    &lt;/event&gt;
  &lt;/schedule&gt;
</pre>

BID (twice a day) (no start or end specified):

<pre class="xml" fragment="Timing">
  &lt;schedule&gt;
   &lt;repeat&gt;
     &lt;frequency value=&quot;2&quot; /&gt;
     &lt;duration value=&quot;1&quot; /&gt;
     &lt;units value=&quot;d&quot; /&gt;
   &lt;/repeat&gt;
  &lt;/schedule&gt;
</pre>

1/2 an hour before breakfast for 10 days from 23-Dec 2011:

<pre class="xml" fragment="Timing">
  &lt;schedule&gt;
    &lt;event&gt;
      &lt;start value=&quot;2011-12-23&quot; /&gt;
    &lt;/event&gt;
    &lt;repeat&gt;
      &lt;when value=&quot;ACM&quot; /&gt;
      &lt;duration value=&quot;30&quot; /&gt;
      &lt;units value=&quot;min&quot; /&gt;
      &lt;end value=&quot;2012-01-02&quot; /&gt;
    &lt;/repeat&gt;
  &lt;/schedule&gt;
</pre>

Note that the end date is inclusive like the high date of a Period.

</div>

<a name="Signature"/>
<a name="timing"/>

### <span class="sectioncount">1.17.1.16<a name="1.17.1.16"> </a></span> 
Signature

See also [Base Definition](datatypes.html#Signature), [Detailed Descriptions](datatypes-definitions.html#Signature) and [Mappings](datatypes-mappings.html#Signature).

<div class="example">

**Example**

todo

<pre class="xml" fragment="Signature">
  &lt;signature&gt;
    &lt;!-- todo --&gt;
  &lt;/signature&gt;
</pre>

</div>

</div>
  
&copy; HL7.org 2011+. FHIR DSTU (v0.4.0-3900) 构建于2014  12月20号 2014 22:38+0000 星期六 . 
链接：[试行版是什么](http://hl7.org/implement/standards/fhir/dstu.html) |[版本更新情况](http://hl7.org/implement/standards/fhir/history.html) | [许可协议](http://hl7.org/implement/standards/fhir/license.html) |[提交变更建议](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemAdd&tracker_id=677) 	  