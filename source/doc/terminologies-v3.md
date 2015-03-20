title: 
date: 
categories: doc
---

  [首页](../home/index.html) >[文档](documentation.html) > [编码的使用](terminologies.html) > **V3 命名空间**	
  
  
  
  *   [Content](terminologies.html)
  *   [ Named Systems List](terminologies-systems.html)
  *   [value sets](terminologies-valuesets.html)
  *   [V2 表格](terminologies-v2.html)
  *   [V3 命名空间](terminologies-v3.html)
  *   [Concept Map字典映射](terminologies-conceptmaps.html)  
  *   [术语服务](terminologies-service.html)
  
####  1.22.4.0  HL7 Version 3 Namespaces (Code Systems and Value Sets)

These namespaces are defined for use in FHIR. Code Systems are used when representing codes that were defined as part of the v3 code systems. 
So if you are representing the code &quot;M&quot; from the code system AdministrativeGender in a FHIR instance, then you would use 
the system &quot;http://hl7.org/fhir/v3/AdministrativeGender&quot; (note that the namespace is case sensitive).

Value Set namespaces are used as part of the specification itself, or in Profiles or other Value Sets where v3 code systems are used.

All of these namespaces are subject to further change.

**CodeSystems**

See below for value sets.

<table class="grid">
 <tr><td>**Name (URI = http://hl7.org/fhir/v3/...)**</td><td>**Description**</td><td>**OID**</td></tr>
 <tr><td>[AcknowledgementCondition](v3/AcknowledgementCondition/index.html)</td><td> The codes identify the conditions under which accept acknowledgements are required to be returned in response to this message. Note that accept acknowledgement address two different issues at the same time: reliable transport as well as syntactical correctness</td><td>--</td></tr>
 <tr><td>[AcknowledgementDetailCode](v3/AcknowledgementDetailCode/index.html)</td><td>  OpenIssue:
Missing description.</td><td>--</td></tr>
 <tr><td>[AcknowledgementDetailType](v3/AcknowledgementDetailType/index.html)</td><td> A code identifying the specific message to be provided.  Discussion:
A textual value may be specified as the print name, or for non-coded messages, as the original text.  Examples:
'Required attribute xxx is missing', 'System will be unavailable March 19 from 0100 to 0300'</td><td>--</td></tr>
 <tr><td>[AcknowledgementType](v3/AcknowledgementType/index.html)</td><td> This attribute contains an acknowledgement code as described in the HL7 message processing rules.  OpenIssue:
Description was copied from attribute and needs to be improved to be appropriate for a code system.</td><td>--</td></tr>
 <tr><td>[ActClass](v3/ActClass/index.html)</td><td>? not found</td><td>--</td></tr>
 <tr><td>[ActCode](v3/ActCode/index.html)</td><td> A code specifying the particular kind of Act that the Act-instance represents within its class.  Constraints:
The kind of Act (e.g. physical examination, serum potassium, inpatient encounter, charge financial transaction, etc.) is specified with a code from one of several, typically external, coding systems.  The coding system will depend on the class of Act, such as LOINC for observations, etc. Conceptually, the Act.code must be a specialization of the Act.classCode. This is why the structure of ActClass domain should be reflected in the superstructure of the ActCode domain and then individual codes or externally referenced vocabularies subordinated under these domains that reflect the ActClass structure. Act.classCode and Act.code are not modifiers of each other but the Act.code concept should really imply the Act.classCode concept. For a negative example, it is not appropriate to use an Act.code &quot;potassium&quot; together with and Act.classCode for &quot;laboratory observation&quot; to somehow mean &quot;potassium laboratory observation&quot; and then use the same Act.code for &quot;potassium&quot; together with Act.classCode for &quot;medication&quot; to mean &quot;substitution of potassium&quot;. This mutually modifying use of Act.code and Act.classCode is not permitted.</td><td>--</td></tr>
 <tr><td>[ActExposureLevelCode](v3/ActExposureLevelCode/index.html)</td><td> A qualitative measure of the degree of exposure to the causative agent.  This includes concepts such as &quot;low&quot;, &quot;medium&quot; and &quot;high&quot;.  This quantifies how the quantity that was available to be administered to the target differs from typical or background levels of the substance.</td><td>--</td></tr>
 <tr><td>[ActInvoiceElementModifier](v3/ActInvoiceElementModifier/index.html)</td><td> Processing consideration and clarification codes.</td><td>--</td></tr>
 <tr><td>[ActMood](v3/ActMood/index.html)</td><td> OpenIssue:  In Ballot 2009May, a strong Negative vote was lodged against several of the concept definitions in the vocabulary used for Act.moodCode. The vote was found &quot;Persuasive With Mod&quot;, with the understanding that M and M would undertake a detailed review of these concept definitions for a future release of the RIM.</td><td>--</td></tr>
 <tr><td>[ActPriority](v3/ActPriority/index.html)</td><td> A set of codes (e.g., for routine, emergency), specifying the urgency under which the Act happened, can happen, is happening, is intended to happen, or is requested/demanded to happen.</td><td>--</td></tr>
 <tr><td>[ActReason](v3/ActReason/index.html)</td><td> A set of codes specifying the motivation, cause, or rationale of an Act, when such rationale is not reasonably represented as an ActRelationship of type &quot;has reason&quot; linking to another Act.  Examples:
Example reasons that might qualify for being coded in this field might be: &quot;routine requirement&quot;, &quot;infectious disease reporting requirement&quot;, &quot;on patient request&quot;, &quot;required by law&quot;.</td><td>--</td></tr>
 <tr><td>[ActRelationshipCheckpoint](v3/ActRelationshipCheckpoint/index.html)</td><td>? not found</td><td>--</td></tr>
 <tr><td>[ActRelationshipJoin](v3/ActRelationshipJoin/index.html)</td><td>? not found</td><td>--</td></tr>
 <tr><td>[ActRelationshipSplit](v3/ActRelationshipSplit/index.html)</td><td>? not found</td><td>--</td></tr>
 <tr><td>[ActRelationshipSubset](v3/ActRelationshipSubset/index.html)</td><td> &lt;ns1:p&gt;Used to indicate that the target of the relationship will be a filtered subset of the total related set of targets.&lt;/ns1:p&gt;&lt;ns1:p&gt;Used when there is a need to limit the number of components to the first, the last, the next, the total, the average or some other filtered or calculated subset.&lt;/ns1:p&gt;</td><td>--</td></tr>
 <tr><td>[ActRelationshipType](v3/ActRelationshipType/index.html)</td><td> The source is an excerpt from the target.</td><td>--</td></tr>
 <tr><td>[ActSite](v3/ActSite/index.html)</td><td> An anatomical location on an organism which can be the focus of an act.</td><td>--</td></tr>
 <tr><td>[ActStatus](v3/ActStatus/index.html)</td><td> Codes representing the defined possible states of an Act, as defined by the Act class state machine.</td><td>--</td></tr>
 <tr><td>[ActUSPrivacyLaw](v3/ActUSPrivacyLaw/index.html)</td><td>  Description:
A jurisdictional mandate in the US relating to privacy.</td><td>--</td></tr>
 <tr><td>[ActUncertainty](v3/ActUncertainty/index.html)</td><td>  OpenIssue:
Missing Description</td><td>--</td></tr>
 <tr><td>[AddressPartType](v3/AddressPartType/index.html)</td><td>  Description:
Code that specifies whether an address part names the street, city, country, postal code, post box, etc. Discussion: The hierarchical nature of these concepts shows composition.  E.g. &quot;Street Name&quot; is part of &quot;Street Address Line&quot;</td><td>--</td></tr>
 <tr><td>[AddressUse](v3/AddressUse/index.html)</td><td>  Description:
Uses of Addresses.   Lloyd to supply more complete description.</td><td>--</td></tr>
 <tr><td>[AdministrativeGender](v3/AdministrativeGender/index.html)</td><td> The gender of a person used for adminstrative purposes (as opposed to clinical gender)</td><td>--</td></tr>
 <tr><td>[AmericanIndianAlaskaNativeLanguages](v3/AmericanIndianAlaskaNativeLanguages/index.html)</td><td> American Indian and Alaska Native languages currently being used in the United States.</td><td>--</td></tr>
 <tr><td>[Calendar](v3/Calendar/index.html)</td><td>? not found</td><td>--</td></tr>
 <tr><td>[CalendarCycle](v3/CalendarCycle/index.html)</td><td> Calendar cycle identifiers</td><td>--</td></tr>
 <tr><td>[CalendarType](v3/CalendarType/index.html)</td><td>? not found</td><td>--</td></tr>
 <tr><td>[Charset](v3/Charset/index.html)</td><td> Internet Assigned Numbers Authority (IANA) Charset Types</td><td>--</td></tr>
 <tr><td>[CodeSystem](v3/CodeSystem/index.html)</td><td> Code systems used in HL7 standards.</td><td>--</td></tr>
 <tr><td>[CodingRationale](v3/CodingRationale/index.html)</td><td> Identifies how to interpret the instance of the code, codeSystem value in a set of translations.  Since HL7 (or a government body) may mandate that codes from certain code systems be sent in conformant messages, other synonyms that are sent in the translation set need to be distinguished among the originally captured source, the HL7 specified code, or some future role.  When this code is NULL, it indicates that the translation is an undefined type.  When valued, this property must contain one of the following values: SRC - Source (or original) code HL7 - HL7 Specified or Mandated SH - both HL7 mandated and the original code (precoordination) There may be additional values added to this value set as we work through the use of codes in messages and determine other Use Cases requiring special interpretation of the translations.</td><td>--</td></tr>
 <tr><td>[CommunicationFunctionType](v3/CommunicationFunctionType/index.html)</td><td> Describes the type of communication function that the associated entity plays in the associated transmission.</td><td>--</td></tr>
 <tr><td>[CompressionAlgorithm](v3/CompressionAlgorithm/index.html)</td><td>? not found</td><td>--</td></tr>
 <tr><td>[ConceptCodeRelationship](v3/ConceptCodeRelationship/index.html)</td><td>  Deprecation Comment:
Deprecated as per 11/2008 Harmonization cleanup; internal and obsolete HL7 usage, no longer used.</td><td>--</td></tr>
 <tr><td>[ConceptGenerality](v3/ConceptGenerality/index.html)</td><td> Indicates whether the concept that is the target should be interpreted as itself, or whether it should be expanded to include its child concepts, or both when it is included in the source domain/valueset.  Deprecation Comment:
Deprecated as per 11/2008 Harmonization cleanup; internal and obsolete HL7 usage, no longer used.</td><td>--</td></tr>
 <tr><td>[ConceptProperty](v3/ConceptProperty/index.html)</td><td>  Deprecation Comment:
Deprecated as per 11/2008 Harmonization cleanup; internal and obsolete HL7 usage, no longer used.</td><td>--</td></tr>
 <tr><td>[ConceptStatus](v3/ConceptStatus/index.html)</td><td>  Deprecation Comment:
Deprecated as per 11/2008 Harmonization cleanup; internal and obsolete HL7 usage, no longer used.</td><td>--</td></tr>
 <tr><td>[Confidentiality](v3/Confidentiality/index.html)</td><td> A set of codes specifying the security classification of acts and roles in accordance with the definition for concept domain &quot;Confidentiality&quot;.</td><td>--</td></tr>
 <tr><td>[ContainerCap](v3/ContainerCap/index.html)</td><td> The type of cap associated with a container</td><td>--</td></tr>
 <tr><td>[ContainerSeparator](v3/ContainerSeparator/index.html)</td><td> A material in a blood collection container that facilites the separation of of blood cells from serum or plasma</td><td>--</td></tr>
 <tr><td>[ContentProcessingMode](v3/ContentProcessingMode/index.html)</td><td>  Description:
Identifies the order in which content should be processed.</td><td>--</td></tr>
 <tr><td>[ContextControl](v3/ContextControl/index.html)</td><td> A code that specifies how an ActRelationship or Participation contributes to the context of an Act, and whether it may be propagated to descendent Acts whose association allows such propagation (see also attributes Participation.contextControlCode, ActRelationship.contextControlCode, ActRelationship.contextConductionInd).</td><td>--</td></tr>
 <tr><td>[Currency](v3/Currency/index.html)</td><td> The currency unit as defined in ISO 4217. Created prior to ISO ruling on OIDs for ISO code tables defined in ISO standards.  Retired.  Replaced by 1.0.4217 iso4217.</td><td>--</td></tr>
 <tr><td>[DataOperation](v3/DataOperation/index.html)</td><td>? not found</td><td>--</td></tr>
 <tr><td>[DataType](v3/DataType/index.html)</td><td> Code system retired.</td><td>--</td></tr>
 <tr><td>[DeviceAlertLevel](v3/DeviceAlertLevel/index.html)</td><td> Domain values for the Device.Alert_levelCode</td><td>--</td></tr>
 <tr><td>[DocumentCompletion](v3/DocumentCompletion/index.html)</td><td> Identifies the current completion state of a clinical document.</td><td>--</td></tr>
 <tr><td>[DocumentStorage](v3/DocumentStorage/index.html)</td><td> Identifies the storage status of a document.</td><td>--</td></tr>
 <tr><td>[EditStatus](v3/EditStatus/index.html)</td><td> The status of an entry as it pertains to its review and incorporation into the HL7 domain specification database.</td><td>--</td></tr>
 <tr><td>[EducationLevel](v3/EducationLevel/index.html)</td><td> Years of education that a person has completed</td><td>--</td></tr>
 <tr><td>[EmployeeJobClass](v3/EmployeeJobClass/index.html)</td><td>? not found</td><td>--</td></tr>
 <tr><td>[EncounterAccident](v3/EncounterAccident/index.html)</td><td>  Deprecation Comment:
Deprecated as per 11/2008 Harmonization cleanup; internal and obsolete HL7 usage, no longer used.  No content.</td><td>--</td></tr>
 <tr><td>[EncounterAcuity](v3/EncounterAcuity/index.html)</td><td> The level of resource intensiveness of patient care.  Deprecation Comment:
Deprecated as per 11/2008 Harmonization cleanup; internal and obsolete HL7 usage, no longer used.  No content.</td><td>--</td></tr>
 <tr><td>[EncounterAdmissionSource](v3/EncounterAdmissionSource/index.html)</td><td>? not found</td><td>--</td></tr>
 <tr><td>[EncounterReferralSource](v3/EncounterReferralSource/index.html)</td><td> This domain is defined in UB92 and applies to US realm only  Deprecation Comment:
Deprecated as per 11/2008 Harmonization cleanup; internal and obsolete HL7 usage, no longer used.  We've deprecated all of the codes.</td><td>--</td></tr>
 <tr><td>[EncounterSpecialCourtesy](v3/EncounterSpecialCourtesy/index.html)</td><td>? not found</td><td>--</td></tr>
 <tr><td>[EntityClass](v3/EntityClass/index.html)</td><td> Classifies the Entity class and all of its subclasses.  The terminology is hierarchical.  At the top is this  HL7-defined domain of high-level categories (such as represented by the Entity subclasses). Each of these terms must be harmonized and is specializable. The value sets beneath are drawn from multiple, frequently external, domains that reflect much more fine-grained typing.</td><td>--</td></tr>
 <tr><td>[EntityCode](v3/EntityCode/index.html)</td><td>  OpenIssue:
Missing description.</td><td>--</td></tr>
 <tr><td>[EntityDeterminer](v3/EntityDeterminer/index.html)</td><td> EntityDeterminer in natural language grammar is the class of words that comprises articles, demonstrative pronouns, and quantifiers. In the RIM, determiner is a structural code in the Entity class to distinguish whether any given Entity object stands for some, any one, or a specific thing.</td><td>--</td></tr>
 <tr><td>[EntityHandling](v3/EntityHandling/index.html)</td><td>? not found</td><td>--</td></tr>
 <tr><td>[EntityNamePartQualifier](v3/EntityNamePartQualifier/index.html)</td><td>  OpenIssue:
Needs description</td><td>--</td></tr>
 <tr><td>[EntityNamePartQualifierR2](v3/EntityNamePartQualifierR2/index.html)</td><td>  Description:
The qualifier is a set of codes each of which specifies a certain subcategory of the name part in addition to the main name part type. For example, a given name may be flagged as a nickname, a family name may be a pseudonym or a name of public records.</td><td>--</td></tr>
 <tr><td>[EntityNamePartType](v3/EntityNamePartType/index.html)</td><td>? not found</td><td>--</td></tr>
 <tr><td>[EntityNamePartTypeR2](v3/EntityNamePartTypeR2/index.html)</td><td>  Description:
Indicates whether the name part is a given name, family name, prefix, suffix, etc.</td><td>--</td></tr>
 <tr><td>[EntityNameUse](v3/EntityNameUse/index.html)</td><td>? not found</td><td>--</td></tr>
 <tr><td>[EntityNameUseR2](v3/EntityNameUseR2/index.html)</td><td>  Description:
A set of codes advising a system or user which name in a set of names to select for a given purpose.</td><td>--</td></tr>
 <tr><td>[EntityRisk](v3/EntityRisk/index.html)</td><td> Kinds of risks associated with the handling of the material..</td><td>--</td></tr>
 <tr><td>[EntityStatus](v3/EntityStatus/index.html)</td><td> Codes representing the defined possible states of an Entity, as defined by the Entity class state machine.</td><td>--</td></tr>
 <tr><td>[EquipmentAlertLevel](v3/EquipmentAlertLevel/index.html)</td><td>? not found</td><td>--</td></tr>
 <tr><td>[Ethnicity](v3/Ethnicity/index.html)</td><td> In the United States, federal standards for classifying data on ethnicity determine the categories used by federal agencies and exert a strong influence on categorization by state and local agencies and private sector organizations. The federal standards do not conceptually define ethnicity, and they recognize the absence of an anthropological or scientific basis for ethnicity classification.  Instead, the federal standards acknowledge that ethnicity is a social-political construct in which an individual's own identification with a particular ethnicity is preferred to observer identification.  The standards specify two minimum ethnicity categories: Hispanic or Latino, and Not Hispanic or Latino.  The standards define a Hispanic or Latino as a person of &quot;Mexican, Puerto Rican, Cuban, South or Central America, or other Spanish culture or origin, regardless of race.&quot; The standards stipulate that ethnicity data need not be limited to the two minimum categories, but any expansion must be collapsible to those categories.  In addition, the standards stipulate that an individual can be Hispanic or Latino or can be Not Hispanic or Latino, but cannot be both.</td><td>--</td></tr>
 <tr><td>[ExposureMode](v3/ExposureMode/index.html)</td><td> Code for the mechanism by which the exposure agent was exchanged or potentially exchanged by the participants involved in the exposure.</td><td>--</td></tr>
 <tr><td>[GTSAbbreviation](v3/GTSAbbreviation/index.html)</td><td>? not found</td><td>--</td></tr>
 <tr><td>[GenderStatus](v3/GenderStatus/index.html)</td><td>? not found</td><td>--</td></tr>
 <tr><td>[HL7CommitteeIDInRIM](v3/HL7CommitteeIDInRIM/index.html)</td><td> Holds the codes used to identify the committees and SIGS of HL7 in RIM repository tables.  Deprecation Comment:
Deprecated as per 11/2008 Harmonization cleanup; internal and obsolete HL7 usage, no longer used.</td><td>--</td></tr>
 <tr><td>[HL7ConformanceInclusion](v3/HL7ConformanceInclusion/index.html)</td><td> These concepts represent theconformance requirments defined for including or valuing an element of an HL7 message.  The concepts apply equally to conformance profiles  defined for Version 2.x messgaes as defined by the Conformance SIG, and to the conformance columns for Version 3 messages as specified in the HMD.  Deprecation Comment:
Deprecated as per 11/2008 Harmonization cleanup; internal and obsolete HL7 usage, no longer used.</td><td>--</td></tr>
 <tr><td>[HL7DefinedRoseProperty](v3/HL7DefinedRoseProperty/index.html)</td><td> The property Ids that HL7 has defined for customizing Rational Rose.  Deprecation Comment:
Deprecated as per 11/2008 Harmonization cleanup; internal and obsolete HL7 usage, no longer used.</td><td>--</td></tr>
 <tr><td>[HL7UpdateMode](v3/HL7UpdateMode/index.html)</td><td> The possible modes of updating that occur when an attribute is received by a system that already contains values for that attribute.</td><td>--</td></tr>
 <tr><td>[HealthcareProviderTaxonomyHIPAA](v3/HealthcareProviderTaxonomyHIPAA/index.html)</td><td>? not found</td><td>--</td></tr>
 <tr><td>[HtmlLinkType](v3/HtmlLinkType/index.html)</td><td> HtmlLinkType values are drawn from HTML 4.0 and describe the relationship between the current document and the anchor that is the target of the link</td><td>--</td></tr>
 <tr><td>[IdentifierReliability](v3/IdentifierReliability/index.html)</td><td> Specifies the reliability with which the identifier is known. This attribute MAY be used to assist with identifier matching algorithms.</td><td>--</td></tr>
 <tr><td>[IdentifierScope](v3/IdentifierScope/index.html)</td><td>  Description:
Codes to specify the scope in which the identifier applies to the object with which it is associated, and used in the datatype property II.</td><td>--</td></tr>
 <tr><td>[IntegrityCheckAlgorithm](v3/IntegrityCheckAlgorithm/index.html)</td><td>? not found</td><td>--</td></tr>
 <tr><td>[LanguageAbilityMode](v3/LanguageAbilityMode/index.html)</td><td> A value representing the method of expression of the language.  Example:
Expressed spoken, expressed written, expressed signed, received spoken, received written, received signed.  OpenIssue:
Description copied from Concept Domain of same name.  Must be verified.</td><td>--</td></tr>
 <tr><td>[LanguageAbilityProficiency](v3/LanguageAbilityProficiency/index.html)</td><td> A value representing the level of proficiency in a language.  Example:
Excellent, good, fair, poor.  OpenIssue:
Description copied from Concept Domain of same name.  Must be verified.</td><td>--</td></tr>
 <tr><td>[LivingArrangement](v3/LivingArrangement/index.html)</td><td> A code depicting the living arrangements of a person</td><td>--</td></tr>
 <tr><td>[LocalMarkupIgnore](v3/LocalMarkupIgnore/index.html)</td><td> Tells a receiver to ignore just the local markup tags (local_markup, local_header, local_attr) when value=&quot;markup&quot;, or to ignore the local markup tags and all contained content when value=&quot;all&quot;</td><td>--</td></tr>
 <tr><td>[LocalRemoteControlState](v3/LocalRemoteControlState/index.html)</td><td>? not found</td><td>--</td></tr>
 <tr><td>[MDFAttributeType](v3/MDFAttributeType/index.html)</td><td>  Deprecation Comment:
Deprecated as per 11/2008 Harmonization cleanup; internal and obsolete HL7 usage, no longer used.</td><td>--</td></tr>
 <tr><td>[MDFSubjectAreaPrefix](v3/MDFSubjectAreaPrefix/index.html)</td><td> The standard prefixes used in Rose for RIM subject areas that determine the role or function of each subject area.  Deprecation Comment:
Deprecated as per 11/2008 Harmonization cleanup; internal and obsolete HL7 usage, no longer used.</td><td>--</td></tr>
 <tr><td>[ManagedParticipationStatus](v3/ManagedParticipationStatus/index.html)</td><td> Codes representing the defined possible states of a Managed Participation, as defined by the Managed Participation class state machine.</td><td>--</td></tr>
 <tr><td>[MapRelationship](v3/MapRelationship/index.html)</td><td> The closeness or quality of the mapping between the HL7 concept (as represented by the HL7 concept identifier) and the source coding system. The values are patterned after the similar relationships used in the UMLS Metathesaurus. Because the HL7 coding sy</td><td>--</td></tr>
 <tr><td>[MaritalStatus](v3/MaritalStatus/index.html)</td><td> * * * No description supplied * * *  Open Issue:
The specific meanings of these codes can vary somewhat by jurisdiction and implementation so caution should be used when determining equivalency.</td><td>--</td></tr>
 <tr><td>[MaterialForm](v3/MaterialForm/index.html)</td><td> A value representing the state (solid, liquid, gas) and nature of the material. Open Issue:There exist no codes in the repository for this coding system; should it be removed?</td><td>--</td></tr>
 <tr><td>[MaterialType](v3/MaterialType/index.html)</td><td>  Deprecation Comment:
Deprecated as per 11/2008 Harmonization cleanup; internal and obsolete HL7 usage, no longer used.  This is outside the hierarchy and there's already an equivalent domain MaterialEntityClass in the right hierarchy.  The corresponding code system is empty.</td><td>--</td></tr>
 <tr><td>[MdfHmdMetSourceType](v3/MdfHmdMetSourceType/index.html)</td><td> Code to identify the source of a Message Element Type represented in the 'of MET' column of an HMD.  Deprecation Comment:
Deprecated as per 11/2008 Harmonization cleanup; internal and obsolete HL7 usage, no longer used.</td><td>--</td></tr>
 <tr><td>[MdfHmdRowType](v3/MdfHmdRowType/index.html)</td><td> The row type codes for the tabular representation of a Hierarchical Message Description.  Deprecation Comment:
Deprecated as per 11/2008 Harmonization cleanup; internal and obsolete HL7 usage, no longer used.</td><td>--</td></tr>
 <tr><td>[MdfRmimRowType](v3/MdfRmimRowType/index.html)</td><td> The row types for the tabular representation of an R-MIM.  Deprecation Comment:
Deprecated as per 11/2008 Harmonization cleanup; internal and obsolete HL7 usage, no longer used.</td><td>--</td></tr>
 <tr><td>[MessageCondition](v3/MessageCondition/index.html)</td><td>  Deprecation Comment:
Deprecated as per 11/2008 Harmonization cleanup; internal and obsolete HL7 usage, no longer used.This isn't referenced in the RIM and is a copy of old v2 codes.  It's superseded by AcknowledgementDetailCode</td><td>--</td></tr>
 <tr><td>[MessageWaitingPriority](v3/MessageWaitingPriority/index.html)</td><td> Indicates that the receiver has messages for the sender  OpenIssue:
Description does not make sense relative to name of coding system.  Must be reviewed and improved.</td><td>--</td></tr>
 <tr><td>[ModifyIndicator](v3/ModifyIndicator/index.html)</td><td>? not found</td><td>--</td></tr>
 <tr><td>[NullFlavor](v3/NullFlavor/index.html)</td><td> A collection of codes specifying why a valid value is not present.</td><td>--</td></tr>
 <tr><td>[ObservationInterpretation](v3/ObservationInterpretation/index.html)</td><td> One or more codes specifying a rough qualitative interpretation of the observation, such as &quot;normal&quot;, &quot;abnormal&quot;, &quot;below normal&quot;, &quot;change up&quot;, &quot;resistant&quot;, &quot;susceptible&quot;, etc.  OpenIssue:
Description copied from Concept Domain of same name.  Must be verified.  Note also that this might be identical to the V2 code system of interpretation codes (formerly Abnormal Flags in older versions).</td><td>--</td></tr>
 <tr><td>[ObservationMethod](v3/ObservationMethod/index.html)</td><td> A code that provides additional detail about the means or technique used to ascertain the observation.  Examples:
Blood pressure measurement method: arterial puncture vs. sphygmomanometer (Riva-Rocci), sitting vs. supine position, etc.  OpenIssue:
Description copied from Concept Domain of same name.  Must be verified.  Note that the Domain has a full discussion about use of the attribute and constraining that is not appropriate for the code system description.  Needs to be improved.</td><td>--</td></tr>
 <tr><td>[ObservationValue](v3/ObservationValue/index.html)</td><td> This domain is the root domain to which all HL7-recognized value sets for the Observation.value attribute will be linked when Observation.value has a coded data type.  OpenIssue:
Description copied from Concept Domain of same name.  Must be corrected..</td><td>--</td></tr>
 <tr><td>[OrganizationNameType](v3/OrganizationNameType/index.html)</td><td>  Deprecation Comment:
Deprecated as per 11/2008 Harmonization cleanup; internal and obsolete HL7 usage, no longer used.  All of these are maintained under EntityNameType.  This was created in error and should never be used.</td><td>--</td></tr>
 <tr><td>[ParameterizedDataType](v3/ParameterizedDataType/index.html)</td><td>  Deprecation Comment:
Deprecated as per 11/2008 Harmonization cleanup; internal and obsolete HL7 usage, no longer used.</td><td>--</td></tr>
 <tr><td>[ParticipationFunction](v3/ParticipationFunction/index.html)</td><td> This code is used to specify the exact function an actor had in a service in all necessary detail. This domain may include local extensions (CWE).</td><td>--</td></tr>
 <tr><td>[ParticipationMode](v3/ParticipationMode/index.html)</td><td> A set of codes specifying the modality by which the Entity playing the Role is participating in the Act.  Examples:
Physically present, over the telephone, written communication.  Rationale:
Particularly for author (originator) participants this is used to specify whether the information represented by the act was initially provided verbally, (hand-)written, or electronically.  Open Issue:
There needs to be a reexamination of the hierarchies as there seems to be some muddling between ELECTRONIC and other concepts that involve electronic communication that are in other hierarchies.</td><td>--</td></tr>
 <tr><td>[ParticipationSignature](v3/ParticipationSignature/index.html)</td><td> A set of codes specifying whether and how the participant has attested his participation through a signature and or whether such a signature is needed.  Examples:
A surgical Procedure act object (representing a procedure report) requires a signature of the performing and responsible surgeon, and possibly other participants. (See also: Participation.signatureText.)</td><td>--</td></tr>
 <tr><td>[ParticipationType](v3/ParticipationType/index.html)</td><td>? not found</td><td>--</td></tr>
 <tr><td>[PatientImportance](v3/PatientImportance/index.html)</td><td> Patient VIP code</td><td>--</td></tr>
 <tr><td>[PaymentTerms](v3/PaymentTerms/index.html)</td><td> Describes payment terms for a financial transaction, used in an invoice. This is typically expressed as a responsibility of the acceptor or payor of an invoice.</td><td>--</td></tr>
 <tr><td>[PeriodicIntervalOfTimeAbbreviation](v3/PeriodicIntervalOfTimeAbbreviation/index.html)</td><td>? not found</td><td>--</td></tr>
 <tr><td>[PersonDisabilityType](v3/PersonDisabilityType/index.html)</td><td> A code identifying a person's disability.</td><td>--</td></tr>
 <tr><td>[PostalAddressUse](v3/PostalAddressUse/index.html)</td><td>  Deprecation Comment:
This code system was deprecated as of the November 2007 harmonization meeting. The content was folded into AddressUse (2.16.840.1.113883.5.1119), which replaces this code system.</td><td>--</td></tr>
 <tr><td>[ProbabilityDistributionType](v3/ProbabilityDistributionType/index.html)</td><td>? not found</td><td>--</td></tr>
 <tr><td>[ProcedureMethod](v3/ProcedureMethod/index.html)</td><td> Identifies the technique used to perform a procedure.</td><td>--</td></tr>
 <tr><td>[ProcessingID](v3/ProcessingID/index.html)</td><td> Codes used to specify whether a message is part of a production, training, or debugging system.</td><td>--</td></tr>
 <tr><td>[ProcessingMode](v3/ProcessingMode/index.html)</td><td>? not found</td><td>--</td></tr>
 <tr><td>[QueryParameterValue](v3/QueryParameterValue/index.html)</td><td> The domain of coded values used as parameters within QueryByParameter queries.</td><td>--</td></tr>
 <tr><td>[QueryPriority](v3/QueryPriority/index.html)</td><td>? not found</td><td>--</td></tr>
 <tr><td>[QueryQuantityUnit](v3/QueryQuantityUnit/index.html)</td><td> Values in this domain specify the units of a query quantity limited request.  Deprecation Comment:
Deprecated as per 11/2008 Harmonization cleanup; internal and obsolete HL7 usage, no longer used.  This is a holdover.  It is not referenced.  It is superseded by QueryRequestLimit.</td><td>--</td></tr>
 <tr><td>[QueryRequestLimit](v3/QueryRequestLimit/index.html)</td><td>  Definition:
Defines the units associated with the magnitude of the maximum size limit of a query response that can be accepted by the requesting application.</td><td>--</td></tr>
 <tr><td>[QueryResponse](v3/QueryResponse/index.html)</td><td> A code classifying the general nature of the response to a given query. Includes whether or not data was found, or whether an error occurred.</td><td>--</td></tr>
 <tr><td>[QueryStatusCode](v3/QueryStatusCode/index.html)</td><td> A code specifying the state of the Query.</td><td>--</td></tr>
 <tr><td>[Race](v3/Race/index.html)</td><td> In the United States, federal standards for classifying data on race determine the categories used by federal agencies and exert a strong influence on categorization by state and local agencies and private sector organizations.  The federal standards do not conceptually define race, and they recognize the absence of an anthropological or scientific basis for racial classification.  Instead, the federal standards acknowledge that race is a social-political construct in which an individual's own identification with one more race categories is preferred to observer identification. The standards use a variety of features to define five minimum race categories. Among these features are descent from &quot;the original peoples&quot; of a specified region or nation.  The minimum race categories are American Indian or Alaska Native, Asian, Black or African American, Native Hawaiian or Other Pacific Islander, and White.  The federal standards stipulate that race data need not be limited to the five minimum categories, but any expansion must be collapsible to those categories.</td><td>--</td></tr>
 <tr><td>[RelationalOperator](v3/RelationalOperator/index.html)</td><td>? not found</td><td>--</td></tr>
 <tr><td>[RelationshipConjunction](v3/RelationshipConjunction/index.html)</td><td>? not found</td><td>--</td></tr>
 <tr><td>[ReligiousAffiliation](v3/ReligiousAffiliation/index.html)</td><td> Assigment of spiritual faith affiliation</td><td>--</td></tr>
 <tr><td>[ResponseLevel](v3/ResponseLevel/index.html)</td><td> Specifies whether a response is expected from the addressee of this interaction and what level of detail that response should include</td><td>--</td></tr>
 <tr><td>[ResponseModality](v3/ResponseModality/index.html)</td><td> Defines the timing and grouping of the response instances.  OpenIssue:
Description copied from Concept Domain of same name.  Must be verified.</td><td>--</td></tr>
 <tr><td>[ResponseMode](v3/ResponseMode/index.html)</td><td> Specifies the mode, immediate versus deferred or queued, by which a receiver should communicate its receiver responsibilities.</td><td>--</td></tr>
 <tr><td>[RoleClass](v3/RoleClass/index.html)</td><td> Codes for the Role class hierarchy.  The values in this hierarchy, represent a Role which is an association or relationship between two entities - the entity that plays the role and the entity that scopes the role.  Roles names are derived from the name of the playing entity in that role. The role hierarchy stems from three core concepts, or abstract domains:    RoleClassOntological
is an abstract domain that collects roles in which the playing entity is defined or specified by the scoping entity.   RoleClassPartitive
collects roles in which the playing entity is in some sense a &quot;part&quot; of the scoping entity.   RoleClassAssociative
collects all of the remaining forms of association between the playing entity and the scoping entity. This set of roles is further partitioned between:    RoleClassPassive
which are roles in which the playing entity is used, known, treated, handled, built, or destroyed, etc. under the auspices of the scoping entity. The playing entity is passive in these roles in that the role exists without an agreement from the playing entity.   RoleClassMutualRelationship
which are relationships based on mutual behavior of the two entities. The basis of these relationship may be formal agreements or they may bede facto
behavior.  Thus, this sub-domain is further divided into:    RoleClassRelationshipFormal
in which the relationship is formally defined, frequently by a contract or agreement.   Personal relationship
which inks two people in a personal relationship. The hierarchy discussed above is represented In the current vocabulary tables as a set of abstract domains, with the exception of the  &quot;Personal relationship&quot; which is a leaf concept.  OpenIssue:
Description copied from Concept Domain of same name.  Must be verified.</td><td>--</td></tr>
 <tr><td>[RoleCode](v3/RoleCode/index.html)</td><td> A set of codes further specifying the kind of Role; specific classification codes for further qualifying RoleClass codes.</td><td>--</td></tr>
 <tr><td>[RoleLinkStatus](v3/RoleLinkStatus/index.html)</td><td>  Description:
Codes representing possible states of a RoleLink, as defined by the RoleLink class state machine.</td><td>--</td></tr>
 <tr><td>[RoleLinkType](v3/RoleLinkType/index.html)</td><td>? not found</td><td>--</td></tr>
 <tr><td>[RoleStatus](v3/RoleStatus/index.html)</td><td> Codes representing the defined possible states of an Role, as defined by the Role class state machine.</td><td>--</td></tr>
 <tr><td>[RouteOfAdministration](v3/RouteOfAdministration/index.html)</td><td> The path the administered medication takes to get into the body or into contact with the body.</td><td>--</td></tr>
 <tr><td>[Sequencing](v3/Sequencing/index.html)</td><td> Specifies sequence of sort order.</td><td>--</td></tr>
 <tr><td>[SetOperator](v3/SetOperator/index.html)</td><td>? not found</td><td>--</td></tr>
 <tr><td>[SpecialArrangement](v3/SpecialArrangement/index.html)</td><td> A code indicating the type of special arrangements provided for a patient encounter (e.g., wheelchair, stretcher, interpreter, attendant, seeing eye dog). For encounters in intention moods, this information can be used to identify special arrangements that will need to be made for the incoming patient.</td><td>--</td></tr>
 <tr><td>[SpecimenType](v3/SpecimenType/index.html)</td><td>? not found</td><td>--</td></tr>
 <tr><td>[SubstitutionCondition](v3/SubstitutionCondition/index.html)</td><td> Identifies what sort of change is permitted or has occurred between the item that was ordered/requested and the one that was/will be provided.</td><td>--</td></tr>
 <tr><td>[TableCellHorizontalAlign](v3/TableCellHorizontalAlign/index.html)</td><td> These values are defined within the XHTML 4.0 Table Model</td><td>--</td></tr>
 <tr><td>[TableCellScope](v3/TableCellScope/index.html)</td><td> These values are defined within the XHTML 4.0 Table Model</td><td>--</td></tr>
 <tr><td>[TableCellVerticalAlign](v3/TableCellVerticalAlign/index.html)</td><td> These values are defined within the XHTML 4.0 Table Model</td><td>--</td></tr>
 <tr><td>[TableFrame](v3/TableFrame/index.html)</td><td> These values are defined within the XHTML 4.0 Table Model</td><td>--</td></tr>
 <tr><td>[TableRules](v3/TableRules/index.html)</td><td> These values are defined within the XHTML 4.0 Table Model</td><td>--</td></tr>
 <tr><td>[TargetAwareness](v3/TargetAwareness/index.html)</td><td>? not found</td><td>--</td></tr>
 <tr><td>[TelecommunicationAddressUse](v3/TelecommunicationAddressUse/index.html)</td><td>  Deprecation Comment:
This code system was deprecated as of the November 2007 harmonization meeting. The content was folded into AddressUse (2.16.840.1.113883.5.1119), which replaces this code system.</td><td>--</td></tr>
 <tr><td>[TelecommunicationCapabilities](v3/TelecommunicationCapabilities/index.html)</td><td>  Description:
Concepts that define the telecommunication capabilities of a particular device. Used to identify the expected capabilities to be found at a particular telecommunication address.</td><td>--</td></tr>
 <tr><td>[TimingEvent](v3/TimingEvent/index.html)</td><td>? not found</td><td>--</td></tr>
 <tr><td>[TransmissionRelationshipTypeCode](v3/TransmissionRelationshipTypeCode/index.html)</td><td>  Description:
A code specifying the meaning and purpose of every TransmissionRelationship instance. Each of its values implies specific constraints to what kinds of Transmission objects can be related and in which way.</td><td>--</td></tr>
 <tr><td>[TribalEntityUS](v3/TribalEntityUS/index.html)</td><td> INDIAN ENTITIES RECOGNIZED AND ELIGIBLE TO RECEIVE SERVICES FROM THE UNITED STATES BUREAU OF INDIAN AFFAIRS</td><td>--</td></tr>
 <tr><td>[VaccineManufacturer](v3/VaccineManufacturer/index.html)</td><td> The manufacturer of a vaccine.</td><td>--</td></tr>
 <tr><td>[VaccineType](v3/VaccineType/index.html)</td><td> The kind of vaccine.</td><td>--</td></tr>
 <tr><td>[VocabularyDomainQualifier](v3/VocabularyDomainQualifier/index.html)</td><td> Vocabulary domain qualifiers are concepts that are used in domain constraints to specify behavior of the new domain. Code system retired.</td><td>--</td></tr>
 <tr><td>[hl7Realm](v3/hl7Realm/index.html)</td><td>  Description:
Coded concepts representing Binding Realms (used for Context Binding of terminology in HL7 models)  and/or Namespace Realms (used to help ensure unique identification of HL7 artifacts). This code system is partitioned into three sections: Affiliate realms, Binding realms and Namespace realms.  All affiliate realm codes may automatically be used as both binding realms and namespace realms.  Furthermore, affiliate realms are the only realms that have authority over the creation of binding realms.  (Note that 'affiliate' includes the idea of both international affiliates and the HL7 International organization.)  All other codes must be associated with an owning affiliate realm and must appear as a specialization of _BindingRealm or _NamespaceRealm.  For affiliates whose concepts align with nations, the country codes from ISO 3166-1 2-character alpha are used for the code when possible so these codes should not be used for other realm types.  It is recommended that binding realm and namespace codes submitted by affiliates use the realm code as a prefix to avoid possible collisions with ISO codes.  However, tooling does not currently support namepace realm codes greater than 2 characters.  Open Issue:
The name of the concept property &quot;owningAffiliate&quot; should be changed to better reflect that the property value is the human readable name of the organizational entity that manages the Realm identified by the Realm Code.  Open Issue:
In spite of the inability of tooling to process codes longer than 2 characters, there is at least one realm codes ('SOA') that was added that is 3 characters in length.</td><td>--</td></tr>
 <tr><td>[hl7V3Conformance](v3/hl7V3Conformance/index.html)</td><td>  Description:
Identifies allowed codes for HL7aTMs v3 conformance property.</td><td>--</td></tr>
 <tr><td>[orderableDrugForm](v3/orderableDrugForm/index.html)</td><td>  OpenIssue:
Missing description.</td><td>--</td></tr>
 <tr><td>[substanceAdminSubstitution](v3/substanceAdminSubstitution/index.html)</td><td> Identifies what sort of change is permitted or has occurred between the therapy that was ordered and the therapy that was/will be provided.</td><td>--</td></tr>
</table>

**Value Sets**

<table class="grid">
 <tr><td>**Name (URI = http://hl7.org/fhir/v3/vs/...) **</td><td>**Name**</td><td>**OID**</td></tr>
 <tr><td>[ActClassInvestigation](v3/vs/ActClassInvestigation/index.html)</td><td> An formalized inquiry into the circumstances surrounding a particular unplanned event or potential event for the purposes of identifying possible causes and contributing factors for the event. This investigation could be conducted at a local institutional level or at the level of a local or national government. </td><td>2.16.840.1.113883.1.11.20224</td></tr>
 <tr><td>[ActConsentType](v3/vs/ActConsentType/index.html)</td><td>  Definition:
The type of consent directive, e.g., to consent or dissent to collect, access, or use in specific ways within an EHRS or for health information exchange; or to disclose  health information  for purposes such as research. </td><td>2.16.840.1.113883.1.11.19897</td></tr>
 <tr><td>[ActCoverageTypeCode](v3/vs/ActCoverageTypeCode/index.html)</td><td>  Definition:
Set of codes indicating the type of insurance policy or program that pays for the cost of benefits provided to covered parties. </td><td>2.16.840.1.113883.1.11.19855</td></tr>
 <tr><td>[ActPharmacySupplyType](v3/vs/ActPharmacySupplyType/index.html)</td><td> Identifies types of dispensing events </td><td>2.16.840.1.113883.1.11.16208</td></tr>
 <tr><td>[ActSubstanceAdminSubstitutionCode](v3/vs/ActSubstanceAdminSubstitutionCode/index.html)</td><td>?? </td><td>2.16.840.1.113883.1.11.16621</td></tr>
 <tr><td>[Compartment](v3/vs/Compartment/index.html)</td><td> A named tag set for metadata used to populate a security category label field that &quot;segments&quot; an IT resource per policy by indicating that access and use is restricted to members of a defined community or project. (HL7 Healthcare Privacy and Security Classification System)  Usage Note:
This is the healthcare analog to the US Intelligence Community's concept of a Special Access Program.  Compartment codes may be used in as a field value in an initiator's clearance to indicate permission to access and use an IT Resource with a security label having the same compartment value in security category label field. Map: Aligns with ISO 2382-8 definition of Compartment -  &quot;A division of data into isolated blocks with separate security controls for the purpose of reducing risk.&quot; </td><td>2.16.840.1.113883.1.11.20478</td></tr>
 <tr><td>[FamilyMember](v3/vs/FamilyMember/index.html)</td><td> A relationship between two people characterizing their &quot;familial&quot; relationship </td><td>2.16.840.1.113883.1.11.19579</td></tr>
 <tr><td>[GeneralPurposeOfUse](v3/vs/GeneralPurposeOfUse/index.html)</td><td> Supports communication of purpose of use at a general level. </td><td>2.16.840.1.113883.1.11.20449</td></tr>
 <tr><td>[InformationSensitivityPolicy](v3/vs/InformationSensitivityPolicy/index.html)</td><td> Sensitivity codes are not useful for interoperability outside of a policy domain because sensitivity policies are typically localized and vary drastically across policy domains even for the same information category because of differing organizational business rules, security policies, and jurisdictional requirements.  For example, an &quot;employee&quot; sensitivity code would make little sense for use outside of a policy domain.   &quot;Taboo&quot; would rarely be useful outside of a policy domain unless there are jurisdictional requirements requiring that a provider disclose sensitive information to a patient directly. Sensitivity codes may be more appropriate in a legacy system's Master Files in order to notify those who access a patient's orders and observations about the sensitivity policies that apply.  Newer systems may have a security engine that uses a sensitivity policy's criteria directly. The specializable Sensitivity Act.code may be useful in some scenarious if used in combination with a sensitivity identifier and/or Act.title. </td><td>2.16.840.1.113883.1.11.20428</td></tr>
 <tr><td>[MilitaryRoleType](v3/vs/MilitaryRoleType/index.html)</td><td>  Definition:
A person playing the role of program eligible under a program based on military status.  Discussion:
This CoveredPartyRoleType.code is typically used when the CoveredPartyRole class code is either &quot;program eligible&quot; or &quot;subscriber&quot; and the person's status as a member of the military meets jurisdictional or program criteria </td><td>2.16.840.1.113883.1.11.19812</td></tr>
 <tr><td>[ObligationPolicy](v3/vs/ObligationPolicy/index.html)</td><td> Conveys the mandated workflow action that an information custodian, receiver, or user must perform.  Examples:
  encrypt  Usage Note:
Per OASIS XACML, an obligation is an operation specified in a policy or policy that is performed in conjunction with the enforcement of an access control decision. </td><td>2.16.840.1.113883.1.11.20445</td></tr>
 <tr><td>[ObservationType](v3/vs/ObservationType/index.html)</td><td> Identifies the kinds of observations that can be performed </td><td>2.16.840.1.113883.1.11.16226</td></tr>
 <tr><td>[PersonalRelationshipRoleType](v3/vs/PersonalRelationshipRoleType/index.html)</td><td> Types of personal relationships between two living subjects.  Example:
Parent, sibling, unrelated friend, neighbor </td><td>2.16.840.1.113883.1.11.19563</td></tr>
 <tr><td>[PurposeOfUse](v3/vs/PurposeOfUse/index.html)</td><td> Supports communication of purpose of use at a general level. </td><td>2.16.840.1.113883.1.11.20448</td></tr>
 <tr><td>[RefrainPolicy](v3/vs/RefrainPolicy/index.html)</td><td> Conveys prohibited actions which an information custodian, receiver, or user is not permitted to perform unless otherwise authorized or permitted under specified circumstances.  Examples:
  prohibit redisclosure without consent directive </td><td>2.16.840.1.113883.1.11.20446</td></tr>
 <tr><td>[SecurityControlObservationValue](v3/vs/SecurityControlObservationValue/index.html)</td><td> Security observation values used to indicate security control metadata.  V:SecurityControl is the union of V:SecurityPolicy,V:ObligationPolicy, V:RefrainPolicy, V:PurposeOfUse, and V:GeneralPurpose of Use used to populate the SecurityControlObservationValue attribute in order to convey one or more nonhierarchical security control metadata dictating handling caveats, purpose of use, dissemination controls and other refrain policies, and obligations to which a custodian or receiver is required to comply. </td><td>2.16.840.1.113883.1.11.20471</td></tr>
 <tr><td>[SecurityIntegrityObservationValue](v3/vs/SecurityIntegrityObservationValue/index.html)</td><td>?? </td><td>2.16.840.1.113883.1.11.20481</td></tr>
 <tr><td>[SecurityPolicy](v3/vs/SecurityPolicy/index.html)</td><td> Types of security policies that further specify the ActClassPolicy value set.  Examples:
  encrypt prohibit redisclosure without consent directive </td><td>2.16.840.1.113883.1.11.20444</td></tr>
 <tr><td>[ServiceDeliveryLocationRoleType](v3/vs/ServiceDeliveryLocationRoleType/index.html)</td><td> A role of a place that further classifies the setting (e.g., accident site, road side, work site, community location) in which services are delivered. </td><td>2.16.840.1.113883.1.11.17660</td></tr>
 <tr><td>[SeverityObservation](v3/vs/SeverityObservation/index.html)</td><td> Potential values for observations of severity. </td><td>2.16.840.1.113883.1.11.16643</td></tr>
 <tr><td>[SubstanceAdminSubstitutionReason](v3/vs/SubstanceAdminSubstitutionReason/index.html)</td><td>?? </td><td>2.16.840.1.113883.1.11.19377</td></tr>
 <tr><td>[VerificationMethod](v3/vs/VerificationMethod/index.html)</td><td>?? </td><td>2.16.840.1.113883.1.11.19707</td></tr>
 <tr><td>[x_BasicConfidentialityKind](v3/vs/x_BasicConfidentialityKind/index.html)</td><td>  Description:
Used to enumerate the typical confidentiality constraints placed upon a clinical document.  Usage Note:
x_BasicConfidentialityKind is a subset of Confidentiality codes that are used as metadata indicating the receiver responsibility to comply with normally applicable jurisdictional privacy law or disclosure authorization; that the receiver may not disclose this information except as directed by the information custodian, who may be the information subject; or that the receiver may not disclose this information except as directed by the information custodian, who may be the information subject. </td><td>2.16.840.1.113883.1.11.16926</td></tr>
</table>