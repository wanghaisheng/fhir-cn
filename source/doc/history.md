title: 
date: 
categories: doc
---

  [首页](../home/index.html) >[文档](documentation.html) > **版本更新记录**	

See [below](#history) for version history details.

<a name="history"> </a>

## 1.4 Version History        
This is the developmental version of FHIR. The only changes tracked here are changes from after the publication of the DSTU. For changes from before this, see the[DSTU #1 Version History](http://hl7.org/fhir/history.html). Note that a full archive history of everything is available[through the HL7 gForge SVN archives](http://wiki.hl7.org/index.php?title=FHIR).

###  1.4.1 How FHIR Versioning works       
_This section is draft_

The FHIR version policy is based on[Semantic versioning](http://semver.org/), but with some differences due to fact that FHIR is a specification, not a software API.

There is a single development version of FHIR. This undergoes cycles of development as managed by HL7\. Each major cycle of development is concluded by a formal ballot, and then a new specification is published. In version control terms, each published specification is a branch off the development trunk, which may then itself undergo further change as HL7 maintains the published specification.

The following kinds of changes may be made to the specification:

*   Non-substantiative changes do not cause changes in any conformant application. For example, section renumbering, broken links, style corrections, typos, and clarifications that do not change the meaning. Some corrections may be judged not to create any expectation of change to a conformant application
*   Substantiative changes that are not breaking. These introduce new functionality - changes to the specification that create new capabilities, but would not render existing applications non-conformant if they do not change
*   Breaking changes would mean that previously conformant applications are not longer conformant

Note that the following are, by definition, considered non-breaking changes, even though some implementations (including the reference implementations) may not be able to handle these changes without error:

*   creation of new resources
*   adding new elements in an existing resource
*   defining new datatypes
*   Adding new API operations

Also, the examples are never substantiative - every effort is made to ensure that they are correct, but changes to the examples in the specification are not considered substantiative.

Each FHIR version is identified by a string composed from 4 parts: publication.major.minor.revision.

<table class="lines"><tbody><tr><td valign="top">publication</td><td>
*   Incremented when HL7 publishes FHIR as an updated specification, e.g. a DSTU or normative version of FHIR
*   HL7 plans to do this every 1 to 2 years
*   The first DSTU was version 0

</td></tr><tr><td valign="top">major</td><td>
*   Increments every time a breaking change is made
*   When a new publication is made, this is reset to 0 in the publication, and 1 in the development branch
*   Since HL7 does not make breaking changes as technical corrections to a published specification, these versions of FHIR always have a version number X.0.n.r
*   Because the development version is the subject of ongoing analysis, debate, ballot and repeated alterations, breaking changes are to be expected

</td></tr><tr><td valign="top">minor</td><td>
*   Increments every time a substantive change is made
*   Resets to 0 any time the major version changes

</td></tr><tr><td valign="top">revision</td><td>
*   Incremented any time a change is made to the specification
*   At present, this is the SVN version number (this allows anyone to reconstruct the source from which the version was built from)

</td></tr></tbody></table>

Additional notes:

*   Changes to a formally published specification (except for minor publishing corrections, such as correcting broken links) are only made via announced technical corrections
*   The reference implementations have 2 versions - the version of the specification that they implement, and their own version. Consult the reference implementation documentation for policy regarding this version number
*   The specification published by the continuous integration service ([http://hl7-fhir.github.io/](http://hl7-fhir.github.io/)) build may not conform to this version policy, but the versions published on the HL7 web site will (see[Directory of published versions](http://hl7.org/fhir/directory.html))
*   The first DSTU was published prior to these rules being agreed as v0.80-2286\. This has been updated to 0.0.81.2382 as a technical correction to align with this policy on 9-May 2014

### <span class="sectioncount">1.4.2</span> Version History since DSTU #
This table lists substantiative changes only.

<table class="grid"><tbody><tr><td>**Version**</td><td>**Changes**</td></tr><tr><td>0.5.0</td><td>

**DSTU Ballot, May 2015**

This version had extensive change as a result of the January Draft ballot, ongoing testing, and the open change proposals (over 800 gForge tasks). List here is a summary of the major changes to resource content, but this is only a small amount of the overall changes.

**Enumerations**

*   All spaces removed
*   Extensive content changes not noted here

**New Data Types**

*   [unsignedInt](datatypes.html#unsignedInt)
*   [positiveInt](datatypes.html#positiveInt)
*   [Signature](datatypes.html#Signature)
*   [Meta](resource.html#Meta)

**Changed Data Types**

*   [Coding](datatypes.html#Coding) - remove valueSet
*   [Attachment](datatypes.html#Attachment) - add creation
*   [Identifier](datatypes.html#Identifier) - replace label with type
*   [Timing](datatypes.html#Timing) - major rework of content
*   [ElementDefinition](elementdefinition.html) - add label, code, rename 'formal' to definition, rename synonym to alias, add language to mapping, remove conformance and isExtensible and replace with strength

**New Resources**

*   [BodySite](bodysite.html)
*   [Claim](claim.html)
*   [ProcessRequest](processrequest.html)
*   [ProcessResponse](processresponse.html)

**Removed Resources**

*   CarePlan2 -> collapsed into CarePlan
*   FamilyHistory -> broken up into FamilyMemberHistory
*   InstitutionalClaim, OralHealthClaim, PharmacyClaim, ProfessionalClaim, VisionClaim -> collapsed into Claim
*   Other - use Basic instead
*   PendedRequest,Readjudicate, Reversal, StatusRequest, StatusResponse - use ProcessRequest/Response instead
*   SupportingDocumentation - use DocumentManifest instead

**Renamed Resources**

*   Alert -> Flag: 'alert' made people think it was an action like an alarm
*   SecurityEvent -> AuditEvent: it wasn't just for security purposes
*   ClinicalAssessment -> ClinicalImpression: people got confused with 'assessment' tools like APGAR score
*   Profile -> StructureDefinition: 'Profile' is the process, a package of statements

**Changes Inside Resources**

*   [Parameters](parameters.html) - allow parameter.part to contain a resource
*   [AllergyIntolerance](allergyintolerance.html) - rename subject to patient
*   [Appointment](appointment.html) - remove lastModifiedBy/lastModified, add location
*   [AppointmentResponse](appointmentresponse.html) - remove lastModifiedBy/lastModified, add rename individual to actor
*   [AuditEvent](auditevent.html) - add .event.purposeOfEvent, participant.location, .policy, and .purposeOfUse
*   [Bundle](bundle.html) - major reorganization
*   [CarePlan](careplan.html) - pull goal out + other reorganization
*   [ClinicalImpression](clinicalimpression.html) - add status, replace careplan & referral with trigger, rename diagnosis to finding, make plan 0..*,
*   [Composition](composition.html) - change .section.content to refer to List only, not any
*   [ConceptMap](conceptmap.html) - change identifier to url, add useContext, change telecom to contact,
*   [Condition](condition.html) - rename subject to patient, rename status to clinicalStatus, change to bodySite = code or Reference(BodySite), rename .codeableConcept to .code
*   [Conformance](conformance.html) - change identifier to url, add useContext, change telecom to contact, add requirements and copyright, add support for conditional operations,
*   [Contract](contract.html) - extensive rewrite
*   [Coverage](coverage.html) - add bin, subscriberId
*   [DataElement](dataelement.html) - total rewrite to use ElementDefinition
*   [Device](device.html) - add status, manufactureDate
*   [DeviceMetric](devicemetric.html) - rename operationalState to operationalStatus, add measurementMode, rename calibrationInfo to calibration, change color to an enumerations
*   [DeviceUseRequest](deviceuserequest.html)/[DeviceUseStatement](deviceusestatement.html) - change to bodySite = code or Reference(BodySite)
*   [DiagnosticOrder](diagnosticorder.html) - change to bodySite = code or Reference(BodySite)
*   [DiagnosticReport](diagnosticreport.html) - add encounter
*   [DocumentManifest](documentmanifest.html) - add options for how content is referred to
*   [DocumentReference](documentreference.html) - add format, remove policyManager, make content : Attachment, and remove several related attributes, remove service reference and add context.practiceSetting, sourcePatientInfo, and related
*   [Encounter](encounter.html) - add incomingReferralRequest, allow reason to repeat, rename diet to dietPreference
*   [EpisodeOfCare](episodeofcare.html) - rename currentStatus to status, allow referralRequest to repeat,
*   [Flag](flag.html) - rename subject to patient, change from note to code
*   [Goal](goal.html) - add targetDate, statusDate, author, priority
*   [HealthcareService](healthcareservice.html) - extensive rewrite
*   [ImagingObjectSelection](imagingobjectselection.html) - remove retrieveAETitle, rename retrieveUrl to url, add frames
*   [ImagingStudy](imagingstudy.html) - add laterality, change url to attachment
*   [Immunization](immunization.html) - add encounter, rename subject to patient, rename refusedIndicator to wasNotGiven, rename refusalReason to reasonNotGiven
*   [ImmunizationRecommendation](immunizationrecommendation.html) - rename subject to patient
*   [List](list.html) - add title, status, change ordered to orderedBy, add note
*   [Location](location.html) - remove status
*   [Media](media.html) - remove created (-> Attachment)
*   [Medication](medication.html) - add batch
*   [MedicationAdministration](medicationadministration.html) - add reasonGiven, note, text. remove timing & maxDosePerPeriod
*   [MedicationDispense](medicationdispense.html) - collapse to a single dispense, add daysSupply, note and substitution, change quantity to allow range
*   [MedicationPrescription](medicationprescription.html) - add note, change quantity to allow range,
*   [MedicationStatement](medicationstatement.html) - add informationSource, status, dateAsserted, replace whenGiven with effective[x], remove device, add dosage.text
*   [NamingSystem](namingsystem.html) - add date, publisher,
*   [NutritionOrder](nutritionorder.html) - extensive rewrite
*   [Observation](observation.html) - change name to code, allow more types of value[x], change type of dataAbsentReason, change to bodySite = code or Reference(BodySite), allow identifier to repeat, add device,
*   [OperationDefinition](operationdefinition.html) - change identifier to url, add useContext, change telecom to contact, change name to title, add reuqirements, idempotent,
*   [OperationOutcome](operationoutcome.html) - change type of .issue.type
*   [OrderResponse](orderresponse.html) - rename code to orderStatus
*   [Organization](organization.html) - remove location and contact.gender
*   [Patient](patient.html) - communication to allow 'preferred'
*   [Person](person.html) - rename other to target
*   [Practitioner](practitioner.html) - change type of birthDate, allow multiple roles per practitioner
*   [Procedure](procedure.html) - add status and category, change to bodySite = code or Reference(BodySite), allow date to be period too, add location, change followUp to code 0..*, add device tracking
*   [ProcedureRequest](procedurerequest.html) - change to bodySite = code or Reference(BodySite)
*   [Provenance](provenance.html) - change integritySignature to signature & make it a type, allow reference by Reference as well as URI
*   [Questionnaire](questionnaire.html) - add telecom
*   [Schedule](schedule.html) - move lastModified
*   [SearchParameter](searchparameter.html) - change telecom to contact, add status, experimental, date,
*   [Slot](slot.html) - move lastModified
*   [Specimen](specimen.html) - change source to parent, change to bodySite = code or Reference(BodySite)
*   [StructureDefinition](structuredefinition.html) - complete rewrite
*   [Subscription](subscription.html) - change type of tag, reanme url to endPoint,
*   [Supply](supply.html) - change type of whenHandedOver
*   [ValueSet](valueset.html) - change identifier to url, add useContext, change telecom to contact, replace purpose with useContext, add requirements, rename stableDate to lockedDate, change type of expansion.identifier, add expansion parameters

</td></tr><tr><td>0.4.0</td><td>

**Draft For Comment, January 2015 Ballot**

Breaking Changes (full list):

*   Replace atom and taglist with a native[Bundle](bundle.html) format ([3728](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemEdit&tracker_item_id=3728),[3558](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemEdit&tracker_item_id=3558),[2889](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemEdit&tracker_item_id=2889)) (and also[Binary](binary.html))
*   JSON: change how extensions are represented ([3471](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemEdit&tracker_item_id=3471))
*   RESTful API: change how version specific upgrades work ([3451](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemEdit&tracker_item_id=3451))
*   DataTypes:
*   Rename Schedule to[Timing](datatypes.html#Timing) ([3536](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemEdit&tracker_item_id=3536),[3236](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemEdit&tracker_item_id=3236))
*   Rename Contact to[ContactPoint](datatypes.html#ContactPoint) ([3533](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemEdit&tracker_item_id=3533)) and swap order of elements ([3108](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemEdit&tracker_item_id=3108)))
*   [Address](datatypes.html#Address) - change zip to postCode ([2888](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemEdit&tracker_item_id=2888))
*   [Quantity](datatypes.html#Quantity): Correct schema spelling for "QuantityCompararator" ([3531](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemEdit&tracker_item_id=3531))
*   Change allowable values for the[id](datatypes.html#id) type to include capital letters, and allow up to 64 chars ([3750](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemEdit&tracker_item_id=3750))
*   Restructure[Profile](profile.html) - only one structure, and pull[ExtensionDefinition](structuredefinition.html) out of Profile (3647, 3498), and pull[SearchParameter](searchparameter.html) out ([3626](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemEdit&tracker_item_id=3626))
*   [Profile](profile.html): allow 0..* discriminator ([3131](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemEdit&tracker_item_id=3131)), and change the way discriminators work across resource boundaries ([3124](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemEdit&tracker_item_id=3124)) + generate multiple types properly ([2856](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemEdit&tracker_item_id=2856))
*   remove _validate interaction, and replace with $validate operation ([3686](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemEdit&tracker_item_id=3686))
*   [Patient](patient.html): separate birth time from birthDate ([3731](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemEdit&tracker_item_id=3731)), Change Administrative Gender from a CodableConcept to a Code. Also fixed the values as male|female|other|unknown with mappings to v2 and v3 ([3070](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemEdit&tracker_item_id=3070))
*   [Supply](supply.html): Change Name of supply.kind binding ([3412](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemEdit&tracker_item_id=3412))
*   [DocumentReference](documentreference.html): change encoding of Hash to Base64 ([3291](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemEdit&tracker_item_id=3291))
*   [Group](group.html): rename header to title ([3126](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemEdit&tracker_item_id=3126))
*   [Condition](condition.html): split relatedItem into two ([3111](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemEdit&tracker_item_id=3111))
*   [Questionnaire](questionnaire.html): drop questionnaire.group.question.remarks ([3255](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemEdit&tracker_item_id=3255)) and move omitReason from extension to base resource ([3260](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemEdit&tracker_item_id=3260))
*   [QuestionnaireAnswers](questionnaireanswers.html): allow multiple answers ([3146](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemEdit&tracker_item_id=3146))
*   [ValueSet](valueset.html): replace ValueSet.compose.include.code with ValueSet.compose.include.concept ([3258](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemEdit&tracker_item_id=3258)), added new rules about expansion content ([3138](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemEdit&tracker_item_id=3138))
*   [Media](media.html): Rename element 'dateTime' to 'created' ([3174](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemEdit&tracker_item_id=3174)) and length to duration ([2866](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemEdit&tracker_item_id=2866))
*   Remove DeviceObservationReport and Query
*   Collapse AdverseReaction into[AllergyIntolerance](allergyintolerance.html)
*   [Appointment](appointment.html) changes - individual field renamed to actor, and added mappings to v2 and v3
*   [FamilyMemberHistory](familymemberhistory.html) combined with[List](list.html) replaces FamilyHistory (with corresponding updates to related profiles)
*   [Flag](flag.html) replaces Alert including improved clarification of how it is used and replacement of "note" with "code"
*   [CarePlan](careplan.html) significantly refactored including splitting Goal out as a distinct resource, moving elements between activity and detail, introduction of several new elements and supported relationship types

New Resources:

*   [Appointment](appointment.html)
*   [AppointmentResponse](appointmentresponse.html)
*   [Basic](basic.html)
*   [ClaimResponse](claimresponse.html)
*   [ClinicalImpression](clinicalimpression.html)
*   [Communication](communication.html)
*   [CommunicationRequest](communicationrequest.html)
*   [Contract](contract.html)
*   [Contraindication](contraindication.html)
*   [Coverage](coverage.html)
*   [DataElement](dataelement.html)
*   [DeviceComponent](devicecomponent.html)
*   [DeviceMetric](devicemetric.html)
*   [DeviceUseRequest](deviceuserequest.html)
*   [DeviceUseStatement](deviceusestatement.html)
*   [EligibilityRequest](eligibilityrequest.html)
*   [EligibilityResponse](eligibilityresponse.html)
*   [EnrollmentRequest](enrollmentrequest.html)
*   [EnrollmentResponse](enrollmentresponse.html)
*   [EpisodeOfCare](episodeofcare.html)
*   [ExplanationOfBenefit](explanationofbenefit.html)
*   [StructureDefinition](structuredefinition.html)
*   [Goal](goal.html)
*   [HealthcareService](healthcareservice.html)
*   [ImagingObjectSelection](imagingobjectselection.html)
*   [InstitutionalClaim](claim.html)
*   [NamingSystem](namingsystem.html)
*   [NutritionOrder](nutritionorder.html)
*   [OperationDefinition](operationdefinition.html)
*   [OralHealthClaim](claim.html)
*   [PaymentNotice](paymentnotice.html)
*   [PaymentReconciliation](paymentreconciliation.html)
*   [Person](person.html)
*   [PharmacyClaim](claim.html)
*   [ProcedureRequest](procedurerequest.html)
*   [ProfessionalClaim](claim.html)
*   [QuestionnaireAnswers](questionnaireanswers.html)
*   [ReferralRequest](referralrequest.html)
*   [RiskAssessment](riskassessment.html)
*   [SearchParameter](searchparameter.html)
*   [Schedule](schedule.html)
*   [Slot](slot.html)
*   [Subscription](subscription.html)
*   SupportingDocumentation
*   [VisionClaim](claim.html)
*   [VisionPrescription](visionprescription.html)

New Implementation Guides (see[discussion of status](iglist.html))

*   [Argonaut Project](argonauts.html)
*   [Data Access Framework](daf.html)
*   [Structured Data Capture](sdc.html) &[Structured Data Capture - Data Element Exchange](sdc-de.html)
*   US Laboratory[Order](uslaborder.html),[Report](uslabreport.html) &[Report to Public Health](uslabphreport.html)
*   [EHRS Functional model - Record Lifecycle Events](ehrs-rle.html)

</td></tr><tr><td>0.3.0</td><td>
*   Renamed Namespace to NamingSystem
*   Split[QuestionnaireAnswers](questionnaireanswers.html) from[Questionnaire](questionnaire.html) and significantly revamped the[Questionnaire](questionnaire.html) in response to feedback from the Connectathon.
*   Added[DataElement](dataelement.html) resource (has been previously discussed as ObservationDefinition)
*   Defined[Subscription](subscription.html) resource for evaluation
*   Add[time](datatypes.html#time) data type
*   Define RPC-type[operations](operations.html) on the RESTful interface, and add[Operation Definition](operationdefinition.html)
*   Defined operations on several resources including[ConceptMap](conceptmap.html),[Questionnaire](questionnaire.html) and[ValueSet](valueset.html)
*   [Conformance](conformance.html): Change Conformance.rest.operation to Conformance.rest.interaction and Conformance.rest.resource.operation to Conformance.rest.resource.interaction, and add Conformance.rest.operation to point to[Operation Definition](operationdefinition.html)
*   [Profile](profile.html): add Profile.url, Profile.structure.snapshot and Profile.structure.differential, and remove query definition (now in OperationDefinition)
*   Add pages for[LOINC](loinc.html),[RxNorm](rxnorm.html), and[SNOMED CT](snomedct.html)
*   Significant rework for[ConceptMap](conceptmap.html) so it can be used to map between structures as well as value sets
*   Add[Contraindication](contraindication.html) and[Risk Assessment](riskassessment.html) and added examples to other resources in support of these
*   Add[Referral Request](referralrequest.html)
*   Add supportingInformation to[DiagnosticOrder](diagnosticorder.html)
*   Add fulfills to[Encounter](encounter.html)
*   Add date and age[x] to[FamilyHistory](familymemberhistory.html)
*   Change cardinality of[Location](location.html).identifier to 0..*
*   Change cardinality of[Practitioner](practitioner.html).address to 0..*
*   Add[Observation](observation.html).encounter to 0..*
*   Temporarily added content for the[Structured Data Capture implementation guide](sdc.html), including profiles on several resources, conformance instances, etc. This content will be moved to an external specification once the necessary tooling is in place to support that form of publication.

</td></tr><tr><td>0.2.1</td><td>
*   Minor new optional elements on value set for metadata, new extensions for all the rest of the VSD project metadata, formal profile to express basic minimum metadata for value set

</td></tr><tr><td>**0.2.0**</td><td>
*   Namespace: adjustments based on Grahame's feedback

</td></tr><tr><td>0.1.0</td><td>
*   Add[Appointment](appointment.html),[Appointment Response](appointmentresponse.html),[Schedule](schedule.html) and[Slot](slot.html)
*   Add_Namespace_

</td></tr></tbody></table>

Note: a useful tool for displaying the differences between pages is the[W3C HTML Diff engine](http://services.w3.org/htmldiff).


