title: 
date: 
categories: doc
---

  [首页](../home/index.html) >[文档](documentation.html) > **版本更新记录**	

See [below](#history) for version history details.

<a name="history"> </a>

## 1.5 Version History

This is the developmental version of FHIR. The only changes tracked here are 
changes from after the publication of the DSTU. For changes from before this, 
see the [DSTU Version History](http://hl7.org/implement/standards/fhir/history.html).
Note that a full archive history of everything is available 
[through the HL7 gForge SVN archives](http://wiki.hl7.org/index.php?title=FHIR "FHIR").

<a name="rules"> </a>

### 1.5.1 How FHIR Versioning works

_This section is draft_

The FHIR version policy is based on [Semantic versioning](http://semver.org/), but with 
some differences due to fact that FHIR is a specification, not a software API.

There is a single development version of FHIR. This undergoes cycles of development as 
managed by HL7. Each major cycle of development is concluded by a formal ballot, and then 
a new specification is published. In version control terms, each published specification is a 
branch off the development trunk, which may then itself undergo further change as 
HL7 maintains the published specification. 

The following kinds of changes may be made to the specification:

*   Non-substantiative changes do not cause changes in any conformant application. For example, section renumbering,   broken links, style corrections, typos, and clarifications that do not change the meaning. Some corrections may   be judged not to create any expectation of change to a conformant application
*   Substantiative changes that are not breaking. These introduce new functionality - changes to the specification that create new capabilities, but would not render existing applications non-conformant if they do not change
*   Breaking changes would mean that previously conformant applications are not longer conformant

Note that the following are, by definition, considered non-breaking changes, even though some implementations (including the reference implementations) may not be able to handle these changes without error:

*   creation of new resources
*   adding new elements in an existing resource
*   defining new datatypes
*   Adding new API operations

Also, the examples are never substantiative - every effort is made to ensure that they are correct, but changes to the examples in the specification are not considered substantiative.

Each FHIR version is identified by a string composed from 4 parts: publication.major.minor.revision. 

<table class="lines">
  <tr>
   <td valign="top">publication</td>
   <td>

*   Incremented when HL7 publishes FHIR as an updated specification, e.g. a DSTU or normative version of FHIR
*   HL7 plans to do this every 1 to 2 years
*   The first DSTU was version 0
   </td>
  </tr>
  <tr>
   <td valign="top">major</td>
   <td>

*   Increments every time a breaking change is made
*   When a new publication is made, this is reset to 0 in the publication, and 1 in the development branch
*   Since HL7 does not make breaking changes as technical corrections to a published specification, these versions of FHIR always have a version number X.0.n.r
*   Because the development version is the subject of ongoing analysis, debate, ballot and repeated alterations, breaking changes are to be expected
   </td>
  </tr>
  <tr>
   <td valign="top">minor</td>
   <td>

*   Increments every time a substantive change is made
*   Resets to 0 any time the major version changes
   </td>
  </tr>
  <tr>
   <td valign="top">revision</td>
   <td>

*   Incremented any time a change is made to the specification
*   At present, this is the SVN version number (this allows anyone to reconstruct the source from which the version was built from)
   </td>
  </tr>
</table>

Additional notes:

*   Changes to a formally published specification (except for minor publishing corrections, such as correcting broken links) are only made via announced technical corrections
*   The reference implementations have 2 versions - the version of the specification that they implement, and their own version. Consult the reference implementation documentation for policy regarding this version number
*   The specification published by the continuous integration service ([http://hl7-fhir.github.io/](http://hl7-fhir.github.io/)) build may not conform to this version policy,   but the versions published on the HL7 web site will (Current published specification at [http://hl7.org/implement/standards/FHIR/](http://hl7.org/implement/standards/FHIR/))     and current development version at [http://hl7.org/implement/standards/FHIR-Develop/](http://hl7.org/implement/standards/FHIR-Develop/))
*   The first DSTU was published prior to these rules being agreed as v0.80-2286. This has been updated to 0.0.81.2382 as a technical correction to align with this policy on 9-May 2014

<a name="history"> </a>

### <span class="sectioncount">1.5.2<a name="1.5.2"> </a></span> Version History since DSTU #1

This table lists substantiative changes only.

<table class="grid"> 
 <tr>
   <td>**Version**</td>
   <td>**Changes**</td>
 </tr>
  <!-- template:
 <tr>
   <td>0.major.minor</td>
   <td>

*
   </td>
 </tr>

notes: do not list revision in the version --> 

	<tr>
		<td>0.4.0</td>
		<td>

**Draft For Comment, January 2015 Ballot**

Breaking Changes (full list):

*   Replace atom and taglist with a native [Bundle](bundle.html) format ([3728](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemEdit&amp;tracker_item_id=3728), [3558](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemEdit&amp;tracker_item_id=3558), [2889](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemEdit&amp;tracker_item_id=2889)) (and also [Binary](binary.html))
*   JSON: change how extensions are represented ([3471](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemEdit&amp;tracker_item_id=3471))
*   RESTful API: change how version specific upgrades work ([3451](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemEdit&amp;tracker_item_id=3451))
*   DataTypes:          <li>Rename Schedule to [Timing](datatypes.html#Timing) ([3536](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemEdit&amp;tracker_item_id=3536), [3236](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemEdit&amp;tracker_item_id=3236))*   Rename Contact to [ContactPoint](datatypes.html#ContactPoint) ([3533](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemEdit&amp;tracker_item_id=3533)) and swap order of elements ([3108](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemEdit&amp;tracker_item_id=3108)))
*   [Address](datatypes.html#Address) - change zip to postCode ([2888](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemEdit&amp;tracker_item_id=2888))
*   [Quantity](datatypes.html#Quantity): Correct schema spelling for &quot;QuantityCompararator&quot; ([3531](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemEdit&amp;tracker_item_id=3531))
*   Change allowable values for the [id](datatypes.html#id) type to include capital letters, and allow up to 64 chars ([3750](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemEdit&amp;tracker_item_id=3750))

*   Restructure [Profile](profile.html) - only one structure, and pull [ExtensionDefinition](extensiondefinition.html) out of Profile (3647, 3498), and pull [SearchParameter](searchparameter.html) out ([3626](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemEdit&amp;tracker_item_id=3626))
*   [Profile](profile.html): allow 0..* discriminator ([3131](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemEdit&amp;tracker_item_id=3131)), and change the way discriminators work across resource boundaries ([3124](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemEdit&amp;tracker_item_id=3124)) + generate multiple types properly ([2856](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemEdit&amp;tracker_item_id=2856))
*   remove _validate interaction, and replace with $validate operation ([3686](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemEdit&amp;tracker_item_id=3686))
*   [Patient](patient.html): separate birth time from birthDate ([3731](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemEdit&amp;tracker_item_id=3731)), Change Administrative Gender from a CodableConcept to a Code. Also fixed the values as male|female|other|unknown with mappings to v2 and v3 ([3070](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemEdit&amp;tracker_item_id=3070))
*   [Supply](supply.html): Change Name of supply.kind binding ([3412](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemEdit&amp;tracker_item_id=3412))
*   [DocumentReference](documentreference.html): change encoding of Hash to Base64 ([3291](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemEdit&amp;tracker_item_id=3291))
*   [Group](group.html): rename header to title ([3126](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemEdit&amp;tracker_item_id=3126))
*   [Condition](condition.html): split relatedItem into two ([3111](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemEdit&amp;tracker_item_id=3111))
*   [Questionnaire](questionnaire.html): drop questionnaire.group.question.remarks ([3255](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemEdit&amp;tracker_item_id=3255)) and move omitReason from extension to base resource ([3260](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemEdit&amp;tracker_item_id=3260))
*   [QuestionnaireAnswers](questionnaireanswers.html): allow multiple answers ([3146](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemEdit&amp;tracker_item_id=3146))*   [ValueSet](valueset.html): replace  ValueSet.compose.include.code with ValueSet.compose.include.concept ([3258](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemEdit&amp;tracker_item_id=3258)), added new rules about expansion content ([3138](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemEdit&amp;tracker_item_id=3138))
*   [Media](media.html): Rename element 'dateTime' to 'created' ([3174](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemEdit&amp;tracker_item_id=3174)) and length to duration ([2866](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemEdit&amp;tracker_item_id=2866))
*   Remove DeviceObservationReport and Query
*   Collapse AdverseReaction into [AllergyIntolerance](allergyintolerance.html)
*   [Appointment](appointment.html) changes - individual field renamed to actor, and added mappings to v2 and v3

New Resources:

*   [Appointment](appointment.html)
*   [AppointmentResponse](appointmentresponse.html)
*   [Basic](basic.html)
*   [CarePlan2](careplan2.html)*   [ClaimResponse](claimresponse.html)
*   [ClinicalAssessment](clinicalassessment.html)
*   [Communication](communication.html)
*   [CommunicationRequest](communicationrequest.html)
*   [Contract](contract.html)
*   [Contraindication](contraindication.html)
*   [Coverage](coverage.html)
*   [DataElement](dataelement.html)
*   [DeviceComponent](devicecomponent.html)
*   [DeviceMetric](devicemetric.html)
*   [DeviceObservationReport](deviceobservationreport.html)
*   [DeviceUseRequest](deviceuserequest.html)*   [DeviceUseStatement](deviceusestatement.html)
*   [EligibilityRequest](eligibilityrequest.html)
*   [EligibilityResponse](eligibilityresponse.html)
*   [EnrollmentRequest](enrollmentrequest.html)
*   [EnrollmentResponse](enrollmentresponse.html)
*   [EpisodeOfCare](episodeofcare.html)
*   [ExplanationOfBenefit](explanationofbenefit.html)
*   [ExtensionDefinition](extensiondefinition.html)
*   [Goal](goal.html)*   [HealthcareService](healthcareservice.html)
*   [ImagingObjectSelection](imagingobjectselection.html)
*   [InstitutionalClaim](institutionalclaim.html)
*   [NamingSystem](namingsystem.html)
*   [NutritionOrder](nutritionorder.html)
*   [OperationDefinition](operationdefinition.html)
*   [OralHealthClaim](oralhealthclaim.html)
*   [PaymentNotice](paymentnotice.html)
*   [PaymentReconciliation](paymentreconciliation.html)
*   [PendedRequest](pendedrequest.html)
*   [Person](person.html)
*   [PharmacyClaim](pharmacyclaim.html)
*   [ProcedureRequest](procedurerequest.html)*   [ProfessionalClaim](professionalclaim.html)
*   [QuestionnaireAnswers](questionnaireanswers.html)
*   [Readjudicate](readjudicate.html)
*   [ReferralRequest](referralrequest.html)
*   [Reversal](reversal.html)
*   [RiskAssessment](riskassessment.html)
*   [SearchParameter](searchparameter.html)
*   [Schedule](schedule.html)
*   [Slot](slot.html)
*   [StatusRequest](statusrequest.html)
*   [StatusResponse](statusresponse.html)
*   [Subscription](subscription.html)
*   [SupportingDocumentation](supportingdocumentation.html)
*   [VisionClaim](visionclaim.html)
*   [VisionPrescription](visionprescription.html)

New Implementation Guides

*   [Argonaut Project](argonauts.html)
*   [Data Access Framework](daf.html)
*   [Structured Data Capture](sdc.html) &amp; [Structured Data Capture - Data Element Exchange](sdc-de.html)
*   US Laboratory [Order](uslaborder.html), [Report](uslabreport.html) &amp; [Report to Public Health](uslabphreport.html)
*   [EHRS Functional model - Record Lifecycle Events](ehrs-rle.html)
		</td>
	</tr> <tr>
   <td>0.3.0</td>
   <td>

*   Renamed Namespace to NamingSystem
*   Split [QuestionnaireAnswers](questionnaireanswers.html) from [Questionnaire](questionnaire.html) and significantly revamped the       [Questionnaire](questionnaire.html) in response to feedback from the Connectathon.
*   Added [DataElement](dataelement.html) resource (has been previously discussed as ObservationDefinition)
*   Defined [Subscription](subscription.html) resource for evaluation
*   Add [time](datatypes.html#time) data type
*   Define RPC-type [operations](operations.html) on the RESTful interface, and add [Operation Definition](operationdefinition.html)
*   Defined operations on several resources including [ConceptMap](conceptmap.html), [Questionnaire](questionnaire.html) and [ValueSet](valueset.html)
*   [Conformance](conformance.html): Change Conformance.rest.operation to Conformance.rest.interaction and Conformance.rest.resource.operation to Conformance.rest.resource.interaction, and add Conformance.rest.operation to point to [Operation Definition](operationdefinition.html)
*   [Profile](profile.html): add Profile.url, Profile.structure.snapshot and Profile.structure.differential, and remove query definition (now in OperationDefinition)
*   Add pages for [LOINC](loinc.html), [RxNorm](rxnorm.html), and [SNOMED CT](snomedct.html)
*   Significant rework for [ConceptMap](conceptmap.html) so it can be used to map between structures as well as value sets
*   Add [Contraindication](contraindication.html) and [Risk Assessment](riskassessment.html) and added examples to other resources in support of these
*   Add [Referral Request](referralrequest.html)
*   Add supportingInformation to [DiagnosticOrder](diagnosticorder.html)
*   Add fulfills to [Encounter](encounter.html)
*   Add date and age[x] to [FamilyHistory](familyhistory.html)
*   Change cardinality of [Location](location.html).identifier to 0..*
*   Change cardinality of [Practitioner](practitioner.html).address to 0..*
*   Add [Observation](observation.html).encounter to 0..*
*   Temporarily added content for the [Structured Data Capture implementation guide](sdc.html), including profiles on several resources, conformance instances, etc.
       This content will be moved to an external specification once the necessary tooling is in place to support that form of publication.
   </td>
 </tr>
 <tr>
   <td>0.2.1</td>
   <td>

*   Minor new optional elements on value set for metadata, new extensions for all the rest of the VSD project metadata, formal profile to express basic minimum metadata for value set
   </td>
 </tr>
 <tr>
   <td>**0.2.0**</td>
   <td>

*   Namespace:  adjustments based on Grahame's feedback
   </td>
 </tr>
 <tr>
   <td>0.1.0</td>
   <td>

*   Add [Appointment](appointment.html), [Appointment Response](appointmentresponse.html), [Schedule](schedule.html) and [Slot](slot.html)
*   Add [Namespace](namespace.html)
   </td>
 </tr>
</table>

Note: a useful tool for displaying the differences between pages is the [W3C HTML Diff engine](http://services.w3.org/htmldiff).

&copy; HL7.org 2011+. FHIR DSTU (v0.4.0-3900) 构建于2014  12月20号 2014 22:38+0000 星期六 . 
链接：[试行版是什么](http://hl7.org/implement/standards/fhir/dstu.htmll) |[版本更新情况](http://hl7.org/implement/standards/fhir/history.htmll) | [许可协议](http://hl7.org/implement/standards/fhir/license.htmll) |[提交变更建议](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemAdd&tracker_id=677) 	