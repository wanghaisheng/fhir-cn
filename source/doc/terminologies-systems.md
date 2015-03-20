title: 
date: 
categories: doc
---

  [首页](../home/index.html) >[文档](documentation.html) > [编码的使用](terminologies.html) > **Named Systems List**	
  
  
  *   [Content](terminologies.html)
  *   [ Named Systems List](terminologies-systems.html)
  *   [value sets](terminologies-valuesets.html)
  *   [V2 表格](terminologies-v2.html)
  *   [V3 命名空间](terminologies-v3.html)
  *   [Concept Map字典映射](terminologies-conceptmaps.html)  
  *   [术语服务](terminologies-service.html)

####  1.22.1.0  Named Systems List

该页中定义的URI都是一个个value set，有XML和JSON两种表达格式。

##### 1.22.1.0.1 已知的编码系统 Known Code Systems

下表中的URI可能会用在[Coding](datatypes.html#Coding)数据类型的system字段中.如果下表中已经规定了某个URI，应该优先使用该URI而非其他标识机制。如果某个编码系统不在下表之内，应该通过如下流程来确定合适的URI，顺序依次为：
If a URI is defined here, it SHALL be used in preference to any other identifying mechanisms. If a code system is not listed
here, the correct URI may be determined by working through the following list, in order:

*	[HL7 OID注册库]()
*	和字典/编码系统有关的文档
*	咨询代码系统的所有者
*	在HL7词汇邮件列表中提问

<table class="grid">
 <tr>
   <th width="150">URI</th>
   <th>Source</th>
   <th>Comment</th>
 </tr>

 <tr>
   <td>http://snomed.info/sct <a name="http://snomed.info/sct"> </a></td>
   <td>SNOMED CT ([IHTSDO](http://ihtsdo.org)) Concept IDs, Expressions and SNOMED Legacy codes (e.g. SCTV3 codes)</td>
   <td>

See [Using SNOMED CT with FHIR](snomedct.html)

OID=2.16.840.1.113883.6.96
</td>
 </tr>
 <tr>
   <td>http://www.nlm.nih.gov/research/umls/rxnorm<a name=" http://www.nlm.nih.gov/research/umls/rxnorm"> </a></td>
   <td>RxNorm ([US NLM](http://www.nlm.nih.gov/))</td>
   <td>

See [Using RxNorm with FHIR](rxnorm.html)

OID=2.16.840.1.113883.6.88

   </td>
 </tr>
 <tr>
   <td>http://loinc.org <a name="http://loinc.org"> </a></td>
   <td>LOINC ([LOINC.org](http://loinc.org))</td>
   <td>

See [Using LOINC with FHIR](loinc.html)

OID=2.16.840.1.113883.6.1

   </td>
 </tr>
 <tr>
   <td>http://unitsofmeasure.org <a name="http://unitsofmeasure.org"> </a></td>
   <td>UCUM: ([UnitsOfMeasure.org](http://unitsofmeasure.org)) Case Sensitive Codes</td>
   <td>

See [Using UCUM with FHIR](ucum.html)

OID=2.16.840.1.113883.6.8
</td>
 </tr>
 <tr>
   <td>http://ncimeta.nci.nih.gov <a name="http://ncimeta.nci.nih.gov"> </a></td>
   <td>[NCI Metathesaurus](http://ncimeta.nci.nih.gov)</td>
   <td>

See [Using NCI Metathesaurus with FHIR](ncimeta.html)

OID=2.16.840.1.113883.3.26.1.2
</td>

 </tr>
 <tr>
   <td>http://www.ama-assn.org/go/cpt <a name="http://www.ama-assn.org/go/cpt"> </a></td>
   <td>[AMA CPT codes](http://www.ama-assn.org/go/cpt)</td>
   <td>

See [Using CPT with FHIR](cpt.html)

OID=2.16.840.1.113883.6.12
</td>

 </tr>
 <tr>
   <td>http://hl7.org/fhir/ndfrt <a name="http://hl7.org/fhir/ndfrt"> </a></td>
   <td>[NDF-RT (National Drug File – Reference Terminology)](http://hl7.org/fhir/ndfrt)</td>
   <td>

See [Using NDF-RT with FHIR](ndfrt.html)

OID=2.16.840.1.113883.6.209 (?)
</td>
 </tr>
 <tr>
   <td>http://fdasis.nlm.nih.gov <a name="http://fdasis.nlm.nih.gov"> </a></td>
   <td>[Unique Ingredient Identifier (UNII)](http://fdasis.nlm.nih.gov)</td>
   <td>

See [Using UNII with FHIR](unii.html)

OID=2.16.840.1.113883.4.9
</td>
 </tr>
 <tr>
   <td>http://www2a.cdc.gov/vaccines/iis/iisstandards/vaccines.asp?rpt=cvx <a name="http://www2a.cdc.gov/vaccines/iis/iisstandards/vaccines.asp?rpt=cvx"> </a></td>
   <td>[CVX (Vaccine Admnistered)](http://www2a.cdc.gov/vaccines/iis/iisstandards/vaccines.asp?rpt=cvx)</td>
   <td>

See [Using CVX with FHIR](cvx.html)

OID=2.16.840.1.113883.12.292
</td>
 </tr>
 <tr>
   <td>urn:iso:std:iso:3166 <a name="urn:iso:std:iso:3166"> </a></td>
   <td>[ISO 2 letter Country Codes](http://www.iso.org/iso/country_codes.htm)</td>
   <td>

Note: a few country codes have been reused (e.g. CS). If a version is needed, simply use the year of publication e.g. 1998

OID=1.0.3166.1.2.2
</td>
 </tr>

 <tr>
   <td>http://www.radlex.org/ <a name="http://www.radlex.org/"> </a></td>
   <td>[RadLex](http://www.radlex.org/)</td>
   <td>
OID=2.16.840.1.113883.6.256 </td>
 </tr>
 <tr>
   <td>http://hl7.org/fhir/sid/icd-10 <a name="http://hl7.org/fhir/sid/icd-10"> </a></td>
   <td>ICD-10 International ([WHO](http://www.who.int/classifications/icd/en/))</td>
   <td>
OID=2.16.840.1.113883.6.3 </td>
 </tr>
 <tr>
   <td>http://hl7.org/fhir/sid/icd-9 <a name="http://hl7.org/fhir/sid/icd-9"> </a></td>
   <td>ICD-9 USA ([CDC](http://www.cdc.gov/nchs/icd/icd9.htm))</td>
   <td>
OID=2.16.840.1.113883.6.42 </td>
 </tr>
 <tr>
   <td>http://hl7.org/fhir/v2/[X](/v) <a name="http://hl7.org/fhir/v2/[X](/v"> </a></td>
   <td>Version 2 table code</td>
   <td>[X] is the 4 digit identifier for a table. e.g. http://hl7.org/fhir/v2/0203

     Only [some tables](terminologies-v2.html) may be treated in this fashion.
     For some tables, the meaning of the code is version dependent, and so additional information 
     must be included in the namespace, e.g. http://hl7.org/fhir/v2/0123/2.3+, as defined in the [v2 table namespace list](terminologies-v2.html).
     Version 2 codes are case sensitive.

OID=2.16.840.1.113883.12.[X] (note that this is the table OID, which is not the same as the codeSystem OID)

Note: This namespace may be revised in the future</td>
 </tr>
 <tr>
   <td>http://hl7.org/fhir/v3/[X] <a name="http://hl7.org/fhir/v3/[X"> </a></td>
   <td>A Version 3 code system, from [the list of code systems defined here](terminologies-v3.html)</td>
   <td>[X] is the code system name. e.g. http://hl7.org/fhir/v3/GenderStatus
OID=[as specified by the [index](terminologies-v3.html)]. Version 3 code systems are case sensitive.

Note: This namespace may be revised in the future </td>
 </tr>
 <tr>
   <td>http://www.whocc.no/atc <a name="http://www.whocc.no/atc"> </a></td>
   <td>Anatomical Therapeutic Chemical Classification System ([WHO](http://www.whocc.no/atc/structure_and_principles/))</td>
   <td>
OID=2.16.840.1.113883.6.73</td>
 </tr> 
 <tr>
   <td>urn:std:iso:11073:10101 <a name="urn:std:iso:11073:10101"> </a></td>
   <td>Medical Device Codes defined in ISO 11073-10101 (see [RTM Management service](http://hit-testing.nist.gov:13110/rtmms/index.html#rosetta))

     The ISO/IEEE 11073-10201 Terminology Code is used in the _code_ element, and the Terminology Reference ID is 
     used in the _display_ element (CODE10 and REFID in the reference)</td>
   <td>
OID=2.16.840.1.113883.6.24</td>
 </tr> 
 <tr>
   <td>[http://nema.org/dicom/dicm](valueset-dicom-dcim.html) <a name="http://nema.org/dicom/dicm"> </a></td>
   <td>DICOM Code Definitions (DCM)

   the meanings of codes defined in DICOM, either explicitly or by reference to another part of DICOM or an external reference document or standard</td>
   <td>
v2/DICOM code=&quot;DCM&quot;. OID=1.2.840.10008.2.16.4</td>
 </tr> 

 <tr>
   <td><a name="http://www.genenames.org">http://www.genenames.org</a></td>
   <td>HGNC: Human Gene Nomenclature Committee</td>
   <td>OID=2.16.840.1.113883.6.281</td>
 </tr>
 <tr>
   <td><a name="http://www.hgvs.org/mutnomen">http://www.hgvs.org/mutnomen</a></td>
   <td>HGVS : Human Genome Variation Society </td>
   <td>OID=2.16.840.1.113883.6.282</td>
 </tr>
 <tr>
   <td><a name="http://www.ncbi.nlm.nih.gov/projects/SNP">http://www.ncbi.nlm.nih.gov/projects/SNP</a></td>
   <td>DBSNP : Single Nucleotide Polymorphism database</td>
   <td>OID=2.16.840.1.113883.6.284</td>
 </tr>
 <tr>
   <td><a name="http://cancer.sanger.ac.uk/cancergenome/projects/cosmic">http://cancer.sanger.ac.uk/cancergenome/projects/cosmic</a></td>
   <td>COSMIC : Catalogue Of Somatic Mutations In Cancer</td>
   <td>OID=2.16.840.1.113883.3.912</td>
 </tr>
 <tr>
   <td><a name="http://www.ncbi.nlm.nih.gov/nuccore">http://www.ncbi.nlm.nih.gov/nuccore</a></td>
   <td>REFSEQ : National Center for Biotechnology Information (NCBI) Reference Sequences</td>
   <td>OID=2.16.840.1.113883.6.280</td>
 </tr>
 <tr>
   <td><a name="http://www.lrg-sequence.org">http://www.lrg-sequence.org</a></td>
   <td>LRG : Locus Reference Genomic Sequences</td>
   <td>OID=2.16.840.1.113883.6.283</td>
 </tr>
 <tr>
   <td><a name="http://www.omim.org">http://www.omim.org</a></td>
   <td>OMIM : Online Mendelian Inheritance in Man</td>
   <td>OID=2.16.840.1.113883.6.174</td>
 </tr>
 <tr>
   <td><a name="null">http://www.ncbi.nlm.nih.gov/pubmed</a></td>
   <td>PubMed </td>
   <td>OID=2.16.840.1.113883.13.191</td>
 </tr>
 <tr>
   <td><a name="http://www.pharmgkb.org">http://www.pharmgkb.org</a></td>
   <td>PHARMGKB : Pharmacogenomic Knowledge Base</td>
   <td>OID=2.16.840.1.113883.3.913</td>
 </tr>
 <tr>
   <td><a name="http://clinicaltrials.gov">http://clinicaltrials.gov</a></td>
   <td>ClinicalTrials.gov</td>
   <td>OID=2.16.840.1.113883.3.1077</td>
 </tr>

</table>

<a name="identifiersystems"> </a> 

#####  1.22.1.0.2 已知的标识系统 Known Identifier Systems


下表中的URI可能会用在[Identifier](datatypes.html#Identifier)数据类型的system字段中.如果下表中已经规定了某个URI，应该优先使用该URI而非其他标识机制。如果某个标识系统不在下表之内，应该通过如下流程来确定合适的URI，顺序依次为：

*	[HL7 OID注册库]()
*	和identifier有关的文档
*	咨询identifier的所有者
*	在HL7词汇邮件列表中提问


<table class="grid">
 <tr>
   <th>identifier</th>
   <th width="150">URI</th>
   <th>Comment</th>
 </tr>

 <tr>
   <td>URIs ([W3C](http://www.w3.org)): when the identifier is a URI</td>
   <td>urn:ietf:rfc:3986 <a name="rn:ietf:rfc:3986"> </a></td>
   <td>As defined by [RFC 3986](http://www.ietf.org/rfc/rfc3986.txt) (with many schemes defined in many RFCs). 
   OIDs and UUIDs are represented in their URN form ([urn:oid:](http://www.ietf.org/rfc/rfc3001.txt) and [urn:uuid:](http://www.ietf.org/rfc/rfc4122.txt) 
   - plain [oid:](http://tools.ietf.org/id/draft-larmouth-oid-iri-04.txt) and uuid: are not used). Note that UUIDs are always lowercase in a IRI
No OID</td>
 </tr>
 <tr>
   <td>SSN ([US Government](http://www.ssa.gov/ssnumber/))</td>
   <td>http://hl7.org/fhir/sid/us-ssn <a name="ttp://hl7.org/fhir/sid/us-ssn"> </a></td>
   <td>US SSN. Represented with dashes removed
OID=2.16.840.1.113883.4.1</td>
 </tr>
 <tr>
   <td>Driver's License</td>
   <td>
**USA**

AK: urn:oid:2.16.840.1.113883.4.3.2	  <!-- Alaska --> 

AL: urn:oid:2.16.840.1.113883.4.3.1	  <!-- Alabama --> 

AR: urn:oid:2.16.840.1.113883.4.3.5	  <!-- Arkansas --> 

AZ: urn:oid:2.16.840.1.113883.4.3.4	  <!-- Arizona --> 

CA: urn:oid:2.16.840.1.113883.4.3.6	  <!-- California --> 

CO: urn:oid:2.16.840.1.113883.4.3.8	  <!-- Colorado --> 

CT: urn:oid:2.16.840.1.113883.4.3.9	  <!-- Connecticut --> 

DC: urn:oid:2.16.840.1.113883.4.3.11	  <!-- DC --> 

DE: urn:oid:2.16.840.1.113883.4.3.10	  <!-- Delaware --> 

FL: urn:oid:2.16.840.1.113883.4.3.12	  <!-- Florida --> 

GA: urn:oid:2.16.840.1.113883.4.3.13	  <!-- Georgia --> 

HI: urn:oid:2.16.840.1.113883.4.3.15	  <!-- Hawaii --> 

IA: urn:oid:2.16.840.1.113883.4.3.19	  <!-- Iowa --> 

ID: urn:oid:2.16.840.1.113883.4.3.16	  <!-- Idaho --> 

IL: urn:oid:2.16.840.1.113883.4.3.17	  <!-- Illinois --> 

KS: urn:oid:2.16.840.1.113883.4.3.20	  <!-- Kansas --> 

KY: urn:oid:2.16.840.1.113883.4.3.21	  <!-- Kentucky --> 

LA: urn:oid:2.16.840.1.113883.4.3.22	  <!-- Louisiana --> 

MA: urn:oid:2.16.840.1.113883.4.3.25	  <!-- Massachusetts --> 

MD: urn:oid:2.16.840.1.113883.4.3.24	  <!-- Maryland --> 

ME: urn:oid:2.16.840.1.113883.4.3.23	  <!-- Maine --> 

MI: urn:oid:2.16.840.1.113883.4.3.26	  <!-- Michigan --> 

MN: urn:oid:2.16.840.1.113883.4.3.27	  <!-- Minnesota --> 

MO: urn:oid:2.16.840.1.113883.4.3.29	  <!-- Missouri --> 

MS: urn:oid:2.16.840.1.113883.4.3.28	  <!-- Mississippi --> 

MT: urn:oid:2.16.840.1.113883.4.3.30	  <!-- Montana --> 

MY: urn:oid:2.16.840.1.113883.4.3.36	  <!-- NewYork --> 

NC: urn:oid:2.16.840.1.113883.4.3.37	  <!-- NorthCarolina --> 

ND: urn:oid:2.16.840.1.113883.4.3.38	  <!-- NorthDakota --> 

NE: urn:oid:2.16.840.1.113883.4.3.31	  <!-- Nebraska --> 

NH: urn:oid:2.16.840.1.113883.4.3.33	  <!-- NewHampshire --> 

NJ: urn:oid:2.16.840.1.113883.4.3.34	  <!-- NewJersey --> 

NM: urn:oid:2.16.840.1.113883.4.3.35	  <!-- NewMexico --> 

NV: urn:oid:2.16.840.1.113883.4.3.32	  <!-- Nevada --> 

OH: urn:oid:2.16.840.1.113883.4.3.39	  <!-- Ohio --> 

OK: urn:oid:2.16.840.1.113883.4.3.40	  <!-- Oklahoma --> 

OR: urn:oid:2.16.840.1.113883.4.3.41	  <!-- Oregon --> 

PA: urn:oid:2.16.840.1.113883.4.3.42	  <!-- Pennsylvania --> 

RI: urn:oid:2.16.840.1.113883.4.3.44	  <!-- RhodeIsland --> 

SC: urn:oid:2.16.840.1.113883.4.3.45	  <!-- SouthCarolina --> 

SD: urn:oid:2.16.840.1.113883.4.3.46	  <!-- SouthDakota --> 

TN: urn:oid:2.16.840.1.113883.4.3.47	  <!-- Tennessee --> 

TX: urn:oid:2.16.840.1.113883.4.3.48	  <!-- Texas --> 

UT: urn:oid:2.16.840.1.113883.4.3.49	  <!-- Utah --> 

VA: urn:oid:2.16.840.1.113883.4.3.51	  <!-- Virginia --> 

VT: urn:oid:2.16.840.1.113883.4.3.50	  <!-- Vermont --> 

WA: urn:oid:2.16.840.1.113883.4.3.53	  <!-- Washington --> 

WI: urn:oid:2.16.840.1.113883.4.3.55	  <!-- Wisconsin --> 

WV: urn:oid:2.16.840.1.113883.4.3.54	  <!-- WestVirginia --> 

WY: urn:oid:2.16.840.1.113883.4.3.56	  <!-- Wyoming --> 

   </td>
   <td>Driver's licenses are often recorded without recording which authority issued the license. In these cases, use the general identifier http://hl7.org/fhir/drivers-license</td>
 </tr>

</table>

**注意:**  名称列表是不全的且会变化的.随着HL7 委员会对词汇中URI的正式流程之后 可能会移除一些值，添加另外一些。


表格中的一些URI遵循 [RFC 5141](http://tools.ietf.org/html/rfc5141) for referring to 
standards published by ISO, such as urn:std:iso:11073:10101. Where ISO standards define codes with meanings, and there is no entry in the list above,
and they are not registered in the HL7 OID registry, the default URN for the code system is that defined by the RFC 5141.

