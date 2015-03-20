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

表示网站地址的uri:

```

<reference value="http://hl7.org/fhir" />

```

urn格式的uri:

```

<id value="urn:isbn:0451450523" />

```

出生日期:

```

<date value="1951-06-04" />
```

出生年月:

```

<date value="1951-06" />

```

临床文档创建的时间，包括时区:

```

<instant value="2013-06-08T10:57:34+01:00" />

```

精确到毫秒的UTC格式的临床文档创建时间:

```

<instant value="2013-06-08T09:57:34.2112Z" />

```

下午2点35分:

```

<time value="14:35" />

```

#### 1.17.1.2  String Patterns

表示HL7的根oid的uri：

```
<root value="urn:oid:2.16.840.1.113883" />
```
uuid格式的uri:

```

<id value="urn:uuid:a5afddf4-e880-459b-876e-e4591b0acc11" />

```

A code:
```

<code value="acq4+acq5" />
```
带单空格的code:
```

<code value="Question 4b" />
```
数字型id:
```

<id value="314" />
```
字母型id:
```

<id value="alpha-gamma-14" />
```


#### 1.17.1.3 Attachment

See also [Base Definition](datatypes.html#Attachment), [Detailed Descriptions](datatypes-definitions.html#Attachment) and [Mappings](datatypes-mappings.html#Attachment).

PDF文档:

```
  <document>
    <contentType value="application/pdf" />
    <language value="en" />
    <data value="/9j/4...KAP//Z" /> <!-- covers many lines -->
    <title value="Definition of Procedure" />
  </document>

```

```

  document : {
    contentType :  { value : "application/pdf" },
    language : { value : "en" },
    data :  { value : "/9j/4...KAP//Z"},
    title :  { value : "Definition of Procedure" }
  }

```

WADO协议的DICOM图像:

```
  <image>
    <contentType value="application/dicom" />
    <url value="http://10.1.2.3:1000/wado?requestType=WADO&amp;wado_details..." />
    <hash value="EQH/..AgME" />
  </image>
```

<a name="Identifier"/>
<a name="identifier"/>

#### 1.17.1.4 Identifier

See also [Base Definition](datatypes.html#Identifier), [Detailed Descriptions](datatypes-definitions.html#Identifier) and [Mappings](datatypes-mappings.html#Identifier).


**Examples**

系统主键:

```
  <identifier>
    <use value="official" />
    <system value="urn:oid:2.16.840.1.113883.16.4.3.2.5" />
    <value value="123" />
  </identifier>
````

院内的病人编号:

```
  <identifier>
    <use value="official" />
    <system value="http://www.acmehosp.com/patients" />
    <value value="44552" />
    <period>
      <start value="2003-05-03" />
    </period>
  </identifier>
````

In this case, the period is used to track when the identifier was first assigned to the patient.

FHIR服务器中的患者标识:

```
  <identifier>
   <system value="urn:ietf:rfc:3986" />
   <value value="http://pas-server/xxx/Patient/443556" />
  </identifier>
```
This is not a resource reference - it's a logical reference by the patient identifier.

A UUID:

```
  <identifier>
    <use value="temp" />
    <system value="urn:ietf:rfc:3986" />
    <value value="urn:uuid:a76d9bbf-f293-4fb7-ad4c-2851cac77162" />
  </identifier>
````

UUIDs are often used for temporary identifiers, though this is not necessary.

A US SSN:

```
  <identifier>
    <use value="usual" />
    <label value="SSN" />
    <system value="http://hl7.org/fhir/sid/us-ssn" />
    <value value="000111111" />
  </identifier>
````

Notes:

*   US SSNs are often presented like this: 000-11-1111, the dashes are for presentation and should be removed, as specified in the [definition of ssn-us](terminologies-systems.html#identifiersystems)
*   The use of &quot;usual&quot; means that this institution prefers to use SSN when identifying the patient
(如果医院使用身份证号来标识患者 是否也是usual;如果院内有自己唯一的主索引，身份证号是用usual还是official)

表单编号或病案号:

```
  <identifier>
    <use value="usual" />
    <label value="MRN" />
    <system value="urn:oid:0.1.2.3.4.5.6.7" />
    <value value="2356" />
    <period>
      <start value="2009-07-05" />
    </period>
  </identifier>

````
<a name="Coding"/>
<a name="coding"/>

#### 1.17.1.5 Coding

See also [Base Definition](datatypes.html#Coding), [Detailed Descriptions](datatypes-definitions.html#Coding) and [Mappings](datatypes-mappings.html#Coding).


**Examples**

头痛的ICD-10编码:

```
  <code>
    <system value="http://hl7.org/fhir/sid/icd-10" />
    <code value="G44.1" />
  </code>

````

A SNOMED CT expression:

````
  <problem>
    <system value="http://snomed.info/sct" />
    <code value="128045006:{363698007=56459004}" />
  </problem>

````
<a name="CodeableConcept"/>
<a name="codeableconcept"/>

#### 1.17.1.6 CodeableConcept

See also [Base Definition](datatypes.html#CodeableConcept), [Detailed Descriptions](datatypes-definitions.html#CodeableConcept) and [Mappings](datatypes-mappings.html#CodeableConcept).


**Examples**

SNOMED-CT编码的头痛，转换成ICD-10编码:

```
  <concept>
    <coding>
      <system value="http://hl7.org/fhir/sid/icd-10" />
      <code value="R51" />
    </coding>
    <coding>
      <system value="http://snomed.info/sct" />
      <code value="25064002" />
      <display value="Headache" />
      <primary value="true" />
    </coding>
    <text value="general headache" />
  </concept>
````

本地编码的剂型单位，UCUM中找不到对应编码:

```
  <unit>
    <coding>
      <system value="urn:oid:2.16.840.1.113883.19.5.2" />
      <code value="tab" />
      <display value="Tablet" />
    </coding>
    <coding>
      <system value="http://unitsofmeasure.org" />
    </coding>
  </unit>

```


A SNOMED CT expression(由于该SNOMED-CT表达式不存在display，所以没有display元素):

```
  <diagnosis>
    <coding>
      <system value="http://snomed.info/sct" />
      <code value="128045006:{363698007=56459004}" />
    </coding>
    <text value="Cellulitis of the foot" />
  </diagnosis>

````


Using the valueset:

The results on a urinalysis strip:

```
  <valueCoding>
    <system value="http://example.org/codes/simple-grades" />
    <code value="+" />
    <valueSet>
      <reference url="ValueSet/simple-grades" />
    </valueSet>
  </valueCoding>

````

具体定义编码的value set如下所示:

```
  <ValueSet xmlns="http://hl7.org/fhir">
    <text>
      <status value="generated"/>
      <div xmlns="http://www.w3.org/1999/xhtml">
        <p>Possible Clinistix codes: neg, trace, +, ++, and +++</p>
      </div>
    </text>
    <identifier value="http://hl7.org/fhir/vs/clinistix"/>
    <name value="Codes for Clinistix"/>
    <publisher value="HL7"/>
    <telecom>
      <system value="url"/>
      <value value="http://hl7.org/fhir"/>
    </telecom>
    <description value="Clinistix Codes"/>
    <status value="draft"/>
    <experimental value="true"/>
    <date value="2013-10-01"/>
    <define>
      <system value="http://hl7.org/fhir/clinistix"/>
      <caseSensitive value="false"/>
      <concept>
        <code value="neg"/>
      </concept>
      <concept>
        <code value="trace"/>
      </concept>
      <concept>
        <code value="+"/>
      </concept>
      <concept>
        <code value="+"/>
      </concept>
      <concept>
        <code value="++"/>
      </concept>
      <concept>
        <code value="+++"/>
      </concept>
    </define>
  </ValueSet>
```
<a name="Quantity"/>
<a name="quantity"/>
<a name="age"/>
<a name="distance"/>
<a name="duration"/>
<a name="count"/>
<a name="money"/>

#### 1.17.1.7 Quantity

See also [Base Definition](datatypes.html#Quantity), [Detailed Descriptions](datatypes-definitions.html#Quantity) and [Mappings](datatypes-mappings.html#Quantity).


**Examples**

A duration:

```
  <time>
    <value value="25" />
    <units value="sec" />
    <system value="http://unitsofmeasure.org" />
    <code value="s" />
  </time>
````

浓度超出范围:

```
  <result>
    <value value="40000" />
    <comparator value="&gt;" />
    <units value="mcg/L" />
    <system value="http://unitsofmeasure.org" />
    <code value="ug" />
  </result>
````

处方药的数量:

```
  <dose>
    <value value="3" />
    <units value="capsules" />
    <system value="http://snomed.info/sct" />
    <code value="385049006" />
  </dose>

````
A price (coded using currency codes defined in ISO 4217):

```
  <cost>
    <value value="25.45" />
    <units value="US$" />
    <system value="urn:std:iso:4217" />
    <code value="USD" />
  </cost>

````

<a name="Range"/>
<a name="range"/>

#### 1.17.1.8 Range

See also [Base Definition](datatypes.html#Range), [Detailed Descriptions](datatypes-definitions.html#Range) and [Mappings](datatypes-mappings.html#Range).


**Examples**

Range of Quantity (distance):

```
  <estimate>
   <low>
     <value value="1.6" />
     <units value="m" />
   </low>
   <high>
     <value value="1.9" />
     <units value="m" />
   </high>
  </estimate>
````
<a name="Ratio"/>
<a name="ratio"/>

#### 1.17.1.9  Ratio

See also [Base Definition](datatypes.html#Ratio), [Detailed Descriptions](datatypes-definitions.html#Ratio) and [Mappings](datatypes-mappings.html#Ratio).



**Examples**

滴速 (Ratio of integer:integer)

```
  <result>
   <numerator>
     <value value="1" />
   </numerator>
   <denominator>
     <value value="128" />
   </denominator>
  </result>

````

单位成本(Ratio of
Money:Quantity):

```


  <charge>
   <numerator>
     <value value="103.50" />
     <units value="US$" />
     <code value="USD" />
     <system value="urn:std:iso:4217" />
   </numerator>
   <denominator>
     <value value="1" />
     <units value="day" />
     <code value="day" />
     <system value="http://unitsofmeasure.org" />
   </denominator>
  </charge>

````
<a name="Period"/>
<a name="period"/>

#### 1.17.1.10 Period

See also [Base Definition](datatypes.html#Period), [Detailed Descriptions](datatypes-definitions.html#Period) and [Mappings](datatypes-mappings.html#Period).



**Examples**

2011年5月23到27 包括27号:

```
  <coverage>
   <start value="2011-05-23" />
   <end value="2011-05-27" />
  </coverage>

````

<a name="SampledData"/>
<a name="sampleddata"/>

#### 1.17.1.11 SampledData

See also [Base Definition](datatypes.html#SampledData), [Detailed Descriptions](datatypes-definitions.html#SampledData) and [Mappings](datatypes-mappings.html#SampledData).



**Example**

EKG设备的输出:

```
 <sampledData>
  <origin>
   <value value="0"/>
   <units value="μV"/>
   <system value="http://unitsofmeasure.org"/>
   <code value="uV"/>
  </origin>
  <period value="2"/>
  <factor value="2.5"/>
  <dimensions value="1"/>
  <data value="-4 -13 -18 -18 -18 -17 -16 -16 -16 -16 -16 -17 -18 -18 -18 ...."/>
 </sampledData>
````
<a name="HumanName"/>
<a name="humanname"/>

#### 1.17.1.12 HumanName

See also [Base Definition](datatypes.html#HumanName), [Detailed Descriptions](datatypes-definitions.html#HumanName) and [Mappings](datatypes-mappings.html#HumanName).



A Simple example

```
<name>
  <family value="Everyman" />
  <given value="Adam" />
  <given value="A." />
</name>

````

Composite names

```
<name>
  <family value="Contrata" />
  <given value="Mary Jane" />
</name>

````

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

#### 1.17.1.14 ContactPoint

See also [Base Definition](datatypes.html#ContactPoint), [Detailed Descriptions](datatypes-definitions.html#ContactPoint) and [Mappings](datatypes-mappings.html#ContactPoint).



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

如果是微信二维码的话，如何标识：
<a name="Timing"/>
<a name="timing"/>

#### 1.17.1.15  Timing

See also [Base Definition](datatypes.html#Timing), [Detailed Descriptions](datatypes-definitions.html#Timing) and [Mappings](datatypes-mappings.html#Timing).



**Example**

预约了一个疗程的放疗？:

```
  <schedule>
    <event>
      <start value="2012-01-07T09:00:00+10:00" />
      <end value="2012-01-07T13:00:00+10:00" />
    </event>
    <event>
      <start value="2012-01-14T09:00:00+10:00" />
      <end value="2012-01-14T13:00:00+10:00" />
    </event>
    <event>
      <start value="2012-01-22T11:00:00+10:00" />
      <end value="2012-01-22T15:00:00+10:00" />
    </event>
  </schedule>
````

一天两次BID (twice a day) (no start or end specified):

```
  <schedule>
   <repeat>
     <frequency value="2" />
     <duration value="1" />
     <units value="d" />
   </repeat>
  </schedule>

````

早饭前半小时，从2011年12月23开始连续十天
1/2 an hour before breakfast for 10 days from 23-Dec 2011:

```
  <schedule>
    <event>
      <start value="2011-12-23" />
    </event>
    <repeat>
      <when value="ACM" />
      <duration value="30" />
      <units value="min" />
      <end value="2012-01-02" />
    </repeat>
  </schedule>
````

Note that the end date is inclusive like the high date of a Period.

</div>

<a name="Signature"/>
<a name="timing"/>

### <span class="sectioncount">1.17.1.16<a name="1.17.1.16"> </a></span> 
Signature

See also [Base Definition](datatypes.html#Signature), [Detailed Descriptions](datatypes-definitions.html#Signature) and [Mappings](datatypes-mappings.html#Signature).



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