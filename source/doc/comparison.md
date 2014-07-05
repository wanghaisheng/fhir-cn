title: 
date: 
categories: doc
---

  [首页](../home/index.html) >[文档](documentation.html) > **总结**	

<a name="root"> </a>

# <span class="sectioncount">1.9.0<a name="1.9.0"> </a></span> Appendix: The Relationship between FHIR and other HL7 Standards

[Health Level Seven (HL7)](http://www.hl7.org) has been developing healthcare 
information exchange and related standards since 1987.  In that time, the organization has 
produced a number of standards families - many  used throughout the world to automate healthcare 
data sharing and improve patient care.  FHIR has been written to be implementable without 
any knowledge of these other specifications.  However, FHIR does leverage this prior experience, 
both in terms of applying best practices learned from experience and attempting to avoid 
some of the pitfalls of earlier work.

This appendix describes the relationship of FHIR to some of HL7's other standard families. 
It may be of interest to those coming to FHIR with previous experience with other HL7 
standards as well as those who may need to support interoperability between FHIR 
solutions and implementations of other HL7 standards.

In this appendix:

*   [Version 2.x](comparison-v2.html)
*   [V3 (RIM / messaging)](comparison-v3.html)
*   [CDA &amp; CCDA etc](comparison-cda.html)
*   [Other HL7 standards](comparison-other.html)

**Notes:**

*   In addition to the major standards families identified below, HL7 produces numerous    implementation guides, some of which have earned as much prominence as a standard    family themselves.  The general guidance given below for each standard family should    hold for all implementation guides based on that standard.  For example, the guidance    listed for [CDA](comparison-cda.html) would apply to Consolidated CDA (CCDA), Continuity    of Care Document (CCD) and other CDA profiles.
*   While this appendix focuses on the relationship between FHIR and other HL7 standards,  relationships also exist to non-HL7 standards.  Some resources provide direct implementation  of functionality from other standards including [DICOM](http://medical.nema.org)  (see the [ImagingStudy](imagingstudy.html) resource) and [IHE](http://www.ihe.net/)  (e.g. the [SecurityEvent](securityevent.html) and [DocumentReference](documentreference.html) resources).*   Many FHIR resources draw requirements from or provide mappings to other standards. Some resources also  provide additional guidance on how to use them with external specifications as part of their implementation notes.    As well, a wiki page to capture additional guidance on the use of FHIR with other specifications can be found    [here](http://wiki.hl7.org/index.php?title=FHIR_and_Other_Specifications "FHIR_and_Other_Specifications")
*   FHIR can satisfy the needs covered by all of the previous primary HL7 interoperability standards (V2, V3 and  CDA).  In many cases, it also provides additional benefits in terms of ease of interoperability.  Therefore, the  possibility exists that FHIR could gradually replace some or all of these standards.  However it is unclear how  rapidly (or even if) the market will make such a migration.  It is likely that most of these standards will exist  in parallel for quite some time.  HL7 has committed to ongoing maintenance of existing standards for as long as  the HL7 membership requires.

</div>
 