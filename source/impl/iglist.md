title:  
date:  
categories: impl
---


*   [Home](index.html)
*   [Implementation](implementation.html)
*   **Implementation Guides**	
		</div>  <!-- /container -->
	</div>  <!-- /segment-breadcrumb -->

	<div id="segment-content" class="segment">  <!-- segment-content -->
	<div class="container">  <!-- container -->
            <div class="row">
            	<div class="inner-wrapper">
  <!-- CONTENT CONTENT -->

<div class="col-9">

## <span class="sectioncount">2.14.0<a name="2.14.0"> </a></span> Implementation Guides defined as part of FHIR

An Implementation Guide is a collection of [Profiles](profile.html), [Conformance](conformance.html)
requirements, [ValueSets](valueset.html) and other resources, together with textual guidance, that provides instruction
on how to make use of FHIR in a particular problem space.  Implementation guides may be developed and published as part of
a FHIR release or as separate specifications.  Additional support and tooling for implementation guides is being developed, so
the content provided here should be considered &quot;preliminary&quot; from a publication perspective.

At present, implementation guides are published in conjunction with the FHIR specification because tooling that supports
straightforward independent publication is not yet developed.  However, the intention is that in the future implementation guides
will be published separately from the core FHIR specification and can be subject to separate approval processes.

The predominance of US implementation guides in this specification is a result of the fact that the US doesn't have an independent
affiliate body to support balloting and publishing of US realm-specific content.  It should in no way be interpreted as suggesting
that FHIR is a US-centric specification.

<table class="grid">
  <tr>
    <td>**Name**</td>
    <td>**Usage**</td>
  </tr>
  <tr>
    <td>[Argonaut Project](argonauts.html)</td>
    <td>A joint task force of the HIT Standards and Policy Committees: a first-generation FHIR-based API and Core Data Services specification</td>
  </tr>
  <tr>
    <td>[Data Access Framework](daf.html)</td>
    <td>A U.S. Realm guide for making use of FHIR resources to support queries between systems within an enterprise and across enterprises.</td>
  </tr>
  <tr>
    <td>[EHRS Functional model - Record Lifecycle Events](ehrs-rle.html)</td>
    <td>Describes the use of the [Provenance](provenance.html) and [SecurityEvent](securityevent.html)
    resources to support meeting the needs of the EHRS functional model requirements for tracking record lifecycle.</td>
  </tr>
  <tr>
    <td>[Structured Data Capture](sdc.html)</td>
    <td>A U.S. Realm guide for making use of [Data Elements](dataelement.html), 
      [Questionnaires](questionnaire.html) and [QuestionnaireAnswers](questionnaireanswers.html) to
      support pre-population and auto-population of forms.</td>
  </tr>
  <tr>
    <td>[Structured Data Capture - Data Element Exchange](sdc-de.html)</td>
    <td>A U.S. Realm guide for supporting the exchange and maintenance of [Data Elements](dataelement.html) by
      and between data element registries.</td>
  </tr>
  <tr>
    <td>[US Laboratory Order](uslaborder.html)

    </td>
    <td>A US Realm guide making use of [Diagnostic Order](diagnosticorder.html) and FHIR resources referenced by them to support ordering of laboratory tests in ambulatory care.
 </td>
  </tr>
    <tr>
    <td>[US Laboratory Report](uslabreport.html)

    </td>
    <td>A US Realm guide making use of [Diagnostic Report](diagnosticreport.html), and FHIR resources referenced by them to support reporting of laboratory tests in ambulatory care.</td>
  </tr>

  <tr>
    <td>[US Laboratory Report to Public Health](uslabphreport.html)

    </td>
    <td>A US Realm guide making use of [Diagnostic Report](diagnosticreport.html), and FHIR resources referenced by them to support reporting of reportable lab tests to Public Health jurisdictions.</td>
  </tr>

</table>

<