title: 
date: 
categories: clin
---
<div class="col-9">

*   [Content](#)
*   [Examples](diagnosticreport-examples.html)
*   [Formal Definitions](diagnosticreport-definitions.html)
*   [Mappings](diagnosticreport-mappings.html)
*   [Profiles](diagnosticreport-profiles.html)

# <span class="sectioncount">4.16<a name="4.16"> </a></span> Resource DiagnosticReport - Content

  <!-- 

Status: null
 -->

The findings and interpretation of diagnostic  tests performed on patients, groups of patients, devices, and locations, and/or specimens derived from these. The report includes clinical context such as requesting and provider information, and some mix of atomic results, images, textual and coded interpretation, and formatted representation of diagnostic reports. 

<div>

## <span class="sectioncount">4.16.1<a name="4.16.1"> </a></span> Scope and Usage

A diagnostic report is the set of information that is typically provided by a diagnostic service 
when investigations are complete. The information includes a mix of atomic results, text reports, images,
and codes. The mix varies depending on the nature of the diagnostic procedure, and sometimes on the nature
of the outcomes for a particular investigation. 

The Diagnostic Report Resource is suitable for the following kinds of Diagnostic Reports:

*   Laboratory (Clinical Chemistry, Hematology, Microbiology, etc.)
*   Pathology / Histopathology / related disciplines
*   Imaging Investigations (x-ray, CT, MRI etc.)
*   Other diagnostics - Cardiology, Gastroenterology etc.

The Diagnostic Report resource is not intended to support cumulative result presentation (tabular presentation of past and present results in the resource). 
The Diagnostic Report resource does not yet provide full support for detailed structured reports of sequencing; this is planned for a future release.

</div>

<div>

## <span class="sectioncount">4.16.2<a name="4.16.2"> </a></span> Background and Context

The Diagnostic Report resource has the following aspects:

*   status, issued, identifier, performer, serviceCategory: information about the diagnostic report itself
*   subject, diagnostic[x]: information about the subject of the report
*   requestDetails.*: A set of request information to allow the report to connected to clinical work flows
*   results: a reference to 0 or more [Observation resources](observation.html) which provide    a hierarchical tree of groups of results
*   specimen details: the specimens on which the report is based
*   conclusion, codedDiagnosis: support for structured reporting
*   images, representation: image and media representations of the report and supporting images

### <span class="sectioncount">4.16.2.1<a name="4.16.2.1"> </a></span> Diagnostic Report Names

The words &quot;tests&quot;, &quot;results&quot;, &quot;observations&quot;, &quot;panels&quot; and &quot;batteries&quot; are often used interchangeably when describing 
the various parts of a diagnostic report. This leads to much confusion. The naming confusion is 
worsened because of the wide variety of forms that the result of a diagnostic investigation can take, 
as described above. Languages other than English have their own variations on this theme.

This resource uses one particular set of terms. A practitioner &quot;requests&quot; a set of &quot;tests&quot;. The
diagnostic service returns a &quot;report&quot; which may contain a &quot;narrative&quot; - a written summary of the 
outcomes, and/or &quot;results&quot; - the individual pieces of atomic data which each are &quot;observations&quot;. 
The results are assembled in &quot;groups&quot; which are nested structures of Observations that can be used to 
represent relationships between the individual data items.

</div>

This resource is referenced by [[Procedure]](procedure.html)

<a name="resource"/>

## <span class="sectioncount">4.16.3<a name="4.16.3"> </a></span> 
Resource Content

<a name="def"> </a>
<a name="diagnosticreport"> </a>
<a name="DiagnosticReport"> </a>

<div id="uml">
<a name="uml"> </a>

**UML Diagram**

 <div id="uml-inner">
 <svg height="256.0" width="676.0" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns="http://www.w3.org/2000/svg" version="1.1">  <defs>
    <filter id="shadow" height="200%" width="200%" y="0" x="0">
      <feOffset result="offOut" dx="3" dy="3" in="SourceGraphic"/>
      <feColorMatrix result="matrixOut" values="0.2 0 0 0 0 0 0.2 0 0 0 0 0 0.2 0 0 0 0 0 1 0" type="matrix" in="offOut"/>
      <feGaussianBlur result="blurOut" stdDeviation="2" in="matrixOut"/>
      <feBlend in2="blurOut" in="SourceGraphic" mode="normal"/>
    </filter>
  </defs><rect height="246.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="284.0" filter="url(#shadow)" rx="4" y="0.0" ry="4" x="0.0"/><line style="stroke:dimgrey;stroke-width:1" y1="28.0" y2="28.0" x2="284.0" x1="0.0"/><text fill="black" class="diagram-class-title  diagram-class-resource" y="20.0" x="142.0">DiagnosticReport<tspan class="diagram-class-title-link"> ([Resource](resources.html))</tspan></text><text fill="black" class="diagram-class-detail" y="42.0" x="6.0">[<title>A code or name that describes this diagnostic report</title>name](diagnosticreport-definitions.html#DiagnosticReport.name) : [CodeableConcept](datatypes.html#CodeableConcept) 1..1 芦 [<title>Codes that describe Diagnostic Reports</title>DiagnosticReportNames](valueset-report-names.html)+ 禄</text><text fill="black" class="diagram-class-detail" y="56.0" x="6.0">[<title>The status of the diagnostic report as a whole (this element modifies the meaning of other elements)</title>status](diagnosticreport-definitions.html#DiagnosticReport.status) : [code](datatypes.html#code) 1..1 芦 [<title>The status of the diagnostic report as a whole</title>DiagnosticReportStatus](diagnostic-report-status.html) 禄</text><text fill="black" class="diagram-class-detail" y="70.0" x="6.0">[<title>The date and/or time that this version of the report was released from the source diagnostic service</title>issued](diagnosticreport-definitions.html#DiagnosticReport.issued) : [dateTime](datatypes.html#dateTime) 1..1</text><text fill="black" class="diagram-class-detail" y="84.0" x="6.0">[<title>The subject of the report. Usually, but not always, this is a patient. However diagnostic services also perform analyses on specimens collected from a variety of other sources</title>subject](diagnosticreport-definitions.html#DiagnosticReport.subject) : [Resource](references.html#Resource)([Patient](patient.html#Patient)|[Group](group.html#Group)|[Device](device.html#Device)|[Location](location.html#Location)) 1..1</text><text fill="black" class="diagram-class-detail" y="98.0" x="6.0">[<title>The diagnostic service that is responsible for issuing the report</title>performer](diagnosticreport-definitions.html#DiagnosticReport.performer) : [Resource](references.html#Resource)([Practitioner](practitioner.html#Practitioner)|[Organization](organization.html#Organization)) 1..1</text><text fill="black" class="diagram-class-detail" y="112.0" x="6.0">[<title>The local ID assigned to the report by the order filler, usually by the Information System of the diagnostic service provider</title>identifier](diagnosticreport-definitions.html#DiagnosticReport.identifier) : [Identifier](datatypes.html#Identifier) 0..1</text><text fill="black" class="diagram-class-detail" y="126.0" x="6.0">[<title>Details concerning a test requested</title>requestDetail](diagnosticreport-definitions.html#DiagnosticReport.requestDetail) : [Resource](references.html#Resource)([DiagnosticOrder](diagnosticorder.html#DiagnosticOrder)) 0..*</text><text fill="black" class="diagram-class-detail" y="140.0" x="6.0">[<title>The section of the diagnostic service that performs the examination e.g. biochemistry, hematology, MRI</title>serviceCategory](diagnosticreport-definitions.html#DiagnosticReport.serviceCategory) : [CodeableConcept](datatypes.html#CodeableConcept) 0..1 芦 ([<title>Codes for diagnostic service sections</title>DiagnosticServiceSection](valueset-diagnostic-service-sections.html)) 禄</text><text fill="black" class="diagram-class-detail" y="154.0" x="6.0">[<title>The time or time-period the observed values are related to. This is usually either the time of the procedure or of specimen collection(s), but very often the source of the date/time is not known, only the date/time itself</title>diagnostic[x]](diagnosticreport-definitions.html#DiagnosticReport.diagnostic_x_) : [dateTime](datatypes.html#dateTime)|[Period](datatypes.html#Period) 1..1</text><text fill="black" class="diagram-class-detail" y="168.0" x="6.0">[<title>Details about the specimens on which this Disagnostic report is based</title>specimen](diagnosticreport-definitions.html#DiagnosticReport.specimen) : [Resource](references.html#Resource)([Specimen](specimen.html#Specimen)) 0..*</text><text fill="black" class="diagram-class-detail" y="182.0" x="6.0">[<title>Observations that are part of this diagnostic report. Observations can be simple name/value pairs (e.g. &quot;atomic&quot; results), or they can be grouping observations that include references to other members of the group (e.g. &quot;panels&quot;)</title>result](diagnosticreport-definitions.html#DiagnosticReport.result) : [Resource](references.html#Resource)([Observation](observation.html#Observation)) 0..*</text><text fill="black" class="diagram-class-detail" y="196.0" x="6.0">[<title>One or more links to full details of any imaging performed during the diagnostic investigation. Typically, this is imaging performed by DICOM enabled modalities, but this is not required. A fully enabled PACS viewer can use this information to provide views of the source images</title>imagingStudy](diagnosticreport-definitions.html#DiagnosticReport.imagingStudy) : [Resource](references.html#Resource)([ImagingStudy](imagingstudy.html#ImagingStudy)) 0..*</text><text fill="black" class="diagram-class-detail" y="210.0" x="6.0">[<title>Concise and clinically contextualized narrative interpretation of the diagnostic report</title>conclusion](diagnosticreport-definitions.html#DiagnosticReport.conclusion) : [string](datatypes.html#string) 0..1</text><text fill="black" class="diagram-class-detail" y="224.0" x="6.0">[<title>Codes for the conclusion</title>codedDiagnosis](diagnosticreport-definitions.html#DiagnosticReport.codedDiagnosis) : [CodeableConcept](datatypes.html#CodeableConcept) 0..* 芦 ([<title>Diagnoses codes provided as adjuncts to the report</title>AdjunctDiagnosis](valueset-clinical-findings.html)) 禄</text><text fill="black" class="diagram-class-detail" y="238.0" x="6.0">[<title>Rich text representation of the entire result as issued by the diagnostic service. Multiple formats are allowed but they SHALL be semantically equivalent</title>presentedForm](diagnosticreport-definitions.html#DiagnosticReport.presentedForm) : [Attachment](datatypes.html#Attachment) 0..*</text><rect height="64.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="116.0" filter="url(#shadow)" rx="4" y="125.0" ry="4" x="360.0"/><line style="stroke:dimgrey;stroke-width:1" y1="153.0" y2="153.0" x2="476.0" x1="360.0"/><text fill="black" class="diagram-class-title" y="145.0" x="418.0">Image</text><text fill="black" class="diagram-class-detail" y="167.0" x="366.0">[<title>A comment about the image. Typically, this is used to provide an explanation for why the image is included, or to draw the viewer's attention to important features</title>comment](diagnosticreport-definitions.html#DiagnosticReport.image.comment) : [string](datatypes.html#string) 0..1</text><text fill="black" class="diagram-class-detail" y="181.0" x="366.0">[<title>Reference to the image source</title>link](diagnosticreport-definitions.html#DiagnosticReport.image.link) : [Resource](references.html#Resource)([Media](media.html#Media)) 1..1</text><line style="stroke:navy;stroke-width:1" y1="140.4927536231884" y2="149.85507246376812" x2="360.0" x1="284.0"/><polygon transform="rotate(7.022793835573206 284.0 140.4927536231884)" style="fill:navy;stroke:navy;stroke-width:1" points="284.0,140.4927536231884 290.0,144.4927536231884 296.0,140.4927536231884 290.0,136.4927536231884 284.0,140.4927536231884"/><rect height="18.0" style="fill:white;stroke:black;stroke-width:0" width="20.0" y="138.0" x="312.0"/><text fill="black" class="diagram-class-linkage" y="148.0" x="322.0">[<title>A list of key images associated with this report. The images are generally created during the diagnostic process, and may be directly of the patient, or of treated specimens (i.e. slides of interest)</title>image](diagnosticreport-definitions.html#DiagnosticReport.image)</text><text fill="black" class="diagram-class-linkage" y="145.85507246376812" x="340.0">0..*</text></svg>
 </div>
</div>

<div id="tbl">
<a name="tbl"> </a>

**Structure**

 <div id="tbl-inner">
  <table style="border: 0px; font-size: 11px; font-family: verdana; vertical-align: top;" cellpadding="0" border="0" cellspacing="0"><tr style="border: 1px #F0F0F0 solid; font-size: 11px; font-family: verdana; vertical-align: top;"><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Name</th><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Card.</th><th style="width: 100px" class="heirarchy">Type</th><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Description &amp; Constraints</th></tr><tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck1.png)" class="heirarchy">![.](tbl_spacer.png)![.](icon_resource.png) <span title="The findings and interpretation of diagnostic  tests performed on patients, groups of patients, devices, and locations, and/or specimens derived from these. The report includes clinical context such as requesting and provider information, and some mix of atomic results, images, textual and coded interpretation, and formatted representation of diagnostic reports.">DiagnosticReport</span><a name="DiagnosticReport"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy"/><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[Resource](resources.html)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">A Diagnostic report - a combination of request information, atomic results, images, interpretation, as well as formatted reports</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_datatype.gif) <span title="A code or name that describes this diagnostic report.">name</span><a name="DiagnosticReport.name"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">1..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[CodeableConcept](datatypes.html#CodeableConcept)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Name/Code for this diagnostic report
[DiagnosticReportNames](valueset-report-names.html "Codes that describe Diagnostic Reports") ([Incomplete](terminologies.html#incomplete "If one of the defined codes is appropriate, it must be used, or some other code may be used"))</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_primitive.png) <span title="The status of the diagnostic report as a whole.">status</span><a name="DiagnosticReport.status"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">1..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[code](datatypes.html#code)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">registered | partial | final | corrected +
[DiagnosticReportStatus](diagnostic-report-status.html "The status of the diagnostic report as a whole") ([Required](terminologies.html#code "One of the the defined codes must be used"))</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_primitive.png) <span title="The date and/or time that this version of the report was released from the source diagnostic service.">issued</span><a name="DiagnosticReport.issued"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">1..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[dateTime](datatypes.html#dateTime)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Date this version was released</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_reference.png) <span title="The subject of the report. Usually, but not always, this is a patient. However diagnostic services also perform analyses on specimens collected from a variety of other sources.">subject</span><a name="DiagnosticReport.subject"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">1..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[Patient](patient.html) | [Group](group.html) | [Device](device.html) | [Location](location.html)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">The subject of the report, usually, but not always, the patient</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_reference.png) <span title="The diagnostic service that is responsible for issuing the report.">performer</span><a name="DiagnosticReport.performer"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">1..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[Practitioner](practitioner.html) | [Organization](organization.html)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Responsible Diagnostic Service</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_datatype.gif) <span title="The local ID assigned to the report by the order filler, usually by the Information System of the diagnostic service provider.">identifier</span><a name="DiagnosticReport.identifier"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[Identifier](datatypes.html#Identifier)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Id for external references to this report</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_reference.png) <span title="Details concerning a test requested.">requestDetail</span><a name="DiagnosticReport.requestDetail"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..*</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[DiagnosticOrder](diagnosticorder.html)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">What was requested</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_datatype.gif) <span title="The section of the diagnostic service that performs the examination e.g. biochemistry, hematology, MRI.">serviceCategory</span><a name="DiagnosticReport.serviceCategory"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[CodeableConcept](datatypes.html#CodeableConcept)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Biochemistry, Hematology etc.
[DiagnosticServiceSection](valueset-diagnostic-service-sections.html "Codes for diagnostic service sections") ([Example](terminologies.html#example "These codes are an example of the type of codes that may be used"))</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck11.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_choice.gif) <span title="The time or time-period the observed values are related to. This is usually either the time of the procedure or of specimen collection(s), but very often the source of the date/time is not known, only the date/time itself.">diagnostic[x]</span><a name="DiagnosticReport.diagnostic_x_"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy"/><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy"/><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Physiologically Relevant time/time-period for report</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck110.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vline.png)![.](tbl_vjoin.png)![.](icon_primitive.png) <span title="A date, date-time or partial date (e.g. just year or year + month).  If hours and minutes are specified, a time zone SHALL be populated. The format is a union of the schema types gYear, gYearMonth, date and dateTime. Seconds may be provided but may also be ignored.  Dates SHALL be valid dates.">diagnosticDateTime</span></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">1..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[dateTime](datatypes.html#dateTime)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy"/></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck100.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vline.png)![.](tbl_vjoin_end.png)![.](icon_datatype.gif) <span title="A time period defined by a start and end date and optionally time.">diagnosticPeriod</span></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">1..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[Period](datatypes.html#Period)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy"/></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_reference.png) <span title="Details about the specimens on which this Disagnostic report is based.">specimen</span><a name="DiagnosticReport.specimen"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..*</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[Specimen](specimen.html)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Specimens this report is based on</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_reference.png) <span title="Observations that are part of this diagnostic report. Observations can be simple name/value pairs (e.g. &quot;atomic&quot; results), or they can be grouping observations that include references to other members of the group (e.g. &quot;panels&quot;).">result</span><a name="DiagnosticReport.result"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..*</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[Observation](observation.html)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Observations - simple, or complex nested groups</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_reference.png) <span title="One or more links to full details of any imaging performed during the diagnostic investigation. Typically, this is imaging performed by DICOM enabled modalities, but this is not required. A fully enabled PACS viewer can use this information to provide views of the source images.">imagingStudy</span><a name="DiagnosticReport.imagingStudy"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..*</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[ImagingStudy](imagingstudy.html)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Reference to full details of imaging associated with the diagnostic report</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck11.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_element.gif) <span title="A list of key images associated with this report. The images are generally created during the diagnostic process, and may be directly of the patient, or of treated specimens (i.e. slides of interest).">image</span><a name="DiagnosticReport.image"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy"/><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Element</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Key images associated with this report</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck110.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vline.png)![.](tbl_vjoin.png)![.](icon_primitive.png) <span title="A comment about the image. Typically, this is used to provide an explanation for why the image is included, or to draw the viewer's attention to important features.">comment</span><a name="DiagnosticReport.image.comment"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[string](datatypes.html#string)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Comment about the image (e.g. explanation)</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck100.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vline.png)![.](tbl_vjoin_end.png)![.](icon_reference.png) <span title="Reference to the image source.">link</span><a name="DiagnosticReport.image.link"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">1..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[Media](media.html)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Reference to the image source</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_primitive.png) <span title="Concise and clinically contextualized narrative interpretation of the diagnostic report.">conclusion</span><a name="DiagnosticReport.conclusion"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[string](datatypes.html#string)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Clinical Interpretation of test results</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_datatype.gif) <span title="Codes for the conclusion.">codedDiagnosis</span><a name="DiagnosticReport.codedDiagnosis"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..*</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[CodeableConcept](datatypes.html#CodeableConcept)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Codes for the conclusion
[AdjunctDiagnosis](valueset-clinical-findings.html "Diagnoses codes provided as adjuncts to the report") ([Example](terminologies.html#example "These codes are an example of the type of codes that may be used"))</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck00.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin_end.png)![.](icon_datatype.gif) <span title="Rich text representation of the entire result as issued by the diagnostic service. Multiple formats are allowed but they SHALL be semantically equivalent.">presentedForm</span><a name="DiagnosticReport.presentedForm"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..*</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[Attachment](datatypes.html#Attachment)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Entire Report as issued</td></tr>
</table>
 </div>
</div>

<div id="xml">
<a name="xml"> </a>

**XML Template**

 <div id="xml-inner">
  <pre class="spec">
&lt;[**DiagnosticReport**](diagnosticreport-definitions.html#DiagnosticReport "The findings and interpretation of diagnostic  tests performed on patients, groups of patients, devices, and locations, and/or specimens derived from these. The report includes clinical context such as requesting and provider information, and some mix of atomic results, images, textual and coded interpretation, and formatted representation of diagnostic reports.") xmlns=&quot;http://hl7.org/fhir&quot;&gt; <span style="float: right">[![doco](help.png)](formats.html "Documentation for this format")</span>
 &lt;!-- from [Resource](resources.html): [extension](extensibility.html), [modifierExtension](extensibility.html#modifierExtension), language, [text](narrative.html#Narrative), and [contained](references.html#contained) --&gt;
 &lt;[**name**](diagnosticreport-definitions.html#DiagnosticReport.name "A code or name that describes this diagnostic report.")&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**1..1**</span> <span style="color: darkgreen">[CodeableConcept](datatypes.html#CodeableConcept)</span> <span style="color: navy">[Name/Code for this diagnostic report](valueset-report-names.html)</span><span style="color: Gray"> --&gt;</span>&lt;/name&gt;
 &lt;[<span style="text-decoration: underline">**status**</span>](diagnosticreport-definitions.html#DiagnosticReport.status "The status of the diagnostic report as a whole (this element modifies the meaning of other elements)") value=&quot;[<span style="color: darkgreen">[code](datatypes.html#code)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**1..1**</span> <span style="color: navy">[registered | partial | final | corrected +<span title="This element is included in a summary view (See Search/Query)" style="color: Navy"> &sect;</span>](diagnostic-report-status.html)</span><span style="color: Gray"> --&gt;</span>
 &lt;[**issued**](diagnosticreport-definitions.html#DiagnosticReport.issued "The date and/or time that this version of the report was released from the source diagnostic service.") value=&quot;[<span style="color: darkgreen">[dateTime](datatypes.html#dateTime)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**1..1**</span> <span style="color: navy">Date this version was released<span title="This element is included in a summary view (See Search/Query)" style="color: Navy"> &sect;</span></span><span style="color: Gray"> --&gt;</span>
 &lt;[**subject**](diagnosticreport-definitions.html#DiagnosticReport.subject "The subject of the report. Usually, but not always, this is a patient. However diagnostic services also perform analyses on specimens collected from a variety of other sources.")&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**1..1**</span> <span style="color: darkgreen">[Resource](references.html#Resource)([Patient](patient.html#Patient)|[Group](group.html#Group)|[Device](device.html#Device)|[Location](location.html#Location))</span> <span style="color: navy">
     The subject of the report, usually, but not always, the patient<span title="This element is included in a summary view (See Search/Query)" style="color: Navy"> &sect;</span></span><span style="color: Gray"> --&gt;</span>&lt;/subject&gt;
 &lt;[**performer**](diagnosticreport-definitions.html#DiagnosticReport.performer "The diagnostic service that is responsible for issuing the report.")&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**1..1**</span> <span style="color: darkgreen">[Resource](references.html#Resource)([Practitioner](practitioner.html#Practitioner)|[Organization](organization.html#Organization))</span> <span style="color: navy">Responsible Diagnostic Service<span title="This element is included in a summary view (See Search/Query)" style="color: Navy"> &sect;</span></span><span style="color: Gray"> --&gt;</span>&lt;/performer&gt;
 &lt;[**identifier**](diagnosticreport-definitions.html#DiagnosticReport.identifier "The local ID assigned to the report by the order filler, usually by the Information System of the diagnostic service provider.")&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..1**</span> <span style="color: darkgreen">[Identifier](datatypes.html#Identifier)</span> <span style="color: navy">Id for external references to this report<span title="This element is included in a summary view (See Search/Query)" style="color: Navy"> &sect;</span></span><span style="color: Gray"> --&gt;</span>&lt;/identifier&gt;
 &lt;[**requestDetail**](diagnosticreport-definitions.html#DiagnosticReport.requestDetail "Details concerning a test requested.")&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..***</span> <span style="color: darkgreen">[Resource](references.html#Resource)([DiagnosticOrder](diagnosticorder.html#DiagnosticOrder))</span> <span style="color: navy">What was requested</span><span style="color: Gray"> --&gt;</span>&lt;/requestDetail&gt;
 &lt;[**serviceCategory**](diagnosticreport-definitions.html#DiagnosticReport.serviceCategory "The section of the diagnostic service that performs the examination e.g. biochemistry, hematology, MRI.")&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..1**</span> <span style="color: darkgreen">[CodeableConcept](datatypes.html#CodeableConcept)</span> <span style="color: navy">[Biochemistry, Hematology etc.<span title="This element is included in a summary view (See Search/Query)" style="color: Navy"> &sect;</span>](valueset-diagnostic-service-sections.html)</span><span style="color: Gray"> --&gt;</span>&lt;/serviceCategory&gt;
 &lt;[**diagnostic[x]**](diagnosticreport-definitions.html#DiagnosticReport.diagnostic_x_ "The time or time-period the observed values are related to. This is usually either the time of the procedure or of specimen collection(s), but very often the source of the date/time is not known, only the date/time itself.")&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**1..1**</span> <span style="color: darkgreen">[dateTime](datatypes.html#dateTime)|[Period](datatypes.html#Period)</span> <span style="color: navy">
     Physiologically Relevant time/time-period for report<span title="This element is included in a summary view (See Search/Query)" style="color: Navy"> &sect;</span></span><span style="color: Gray"> --&gt;</span>&lt;/diagnostic[x]&gt;
 &lt;[**specimen**](diagnosticreport-definitions.html#DiagnosticReport.specimen "Details about the specimens on which this Disagnostic report is based.")&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..***</span> <span style="color: darkgreen">[Resource](references.html#Resource)([Specimen](specimen.html#Specimen))</span> <span style="color: navy">Specimens this report is based on</span><span style="color: Gray"> --&gt;</span>&lt;/specimen&gt;
 &lt;[**result**](diagnosticreport-definitions.html#DiagnosticReport.result "Observations that are part of this diagnostic report. Observations can be simple name/value pairs (e.g. &quot;atomic&quot; results), or they can be grouping observations that include references to other members of the group (e.g. &quot;panels&quot;).")&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..***</span> <span style="color: darkgreen">[Resource](references.html#Resource)([Observation](observation.html#Observation))</span> <span style="color: navy">Observations - simple, or complex nested groups</span><span style="color: Gray"> --&gt;</span>&lt;/result&gt;
 &lt;[**imagingStudy**](diagnosticreport-definitions.html#DiagnosticReport.imagingStudy "One or more links to full details of any imaging performed during the diagnostic investigation. Typically, this is imaging performed by DICOM enabled modalities, but this is not required. A fully enabled PACS viewer can use this information to provide views of the source images.")&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..***</span> <span style="color: darkgreen">[Resource](references.html#Resource)([ImagingStudy](imagingstudy.html#ImagingStudy))</span> <span style="color: navy">
     Reference to full details of imaging associated with the diagnostic report</span><span style="color: Gray"> --&gt;</span>&lt;/imagingStudy&gt;
 &lt;[**image**](diagnosticreport-definitions.html#DiagnosticReport.image "A list of key images associated with this report. The images are generally created during the diagnostic process, and may be directly of the patient, or of treated specimens (i.e. slides of interest).")&gt;  <span style="color: Gray">&lt;!-- <span style="color: brown">**0..***</span> Key images associated with this report<span title="This element is included in a summary view (See Search/Query)" style="color: Navy"> &sect;</span> --&gt;</span>
  &lt;[**comment**](diagnosticreport-definitions.html#DiagnosticReport.image.comment "A comment about the image. Typically, this is used to provide an explanation for why the image is included, or to draw the viewer") value=&quot;[<span style="color: darkgreen">[string](datatypes.html#string)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..1**</span> <span style="color: navy">Comment about the image (e.g. explanation)</span><span style="color: Gray"> --&gt;</span>
  &lt;[**link**](diagnosticreport-definitions.html#DiagnosticReport.image.link "Reference to the image source.")&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**1..1**</span> <span style="color: darkgreen">[Resource](references.html#Resource)([Media](media.html#Media))</span> <span style="color: navy">Reference to the image source<span title="This element is included in a summary view (See Search/Query)" style="color: Navy"> &sect;</span></span><span style="color: Gray"> --&gt;</span>&lt;/link&gt;
 &lt;/image&gt;
 &lt;[**conclusion**](diagnosticreport-definitions.html#DiagnosticReport.conclusion "Concise and clinically contextualized narrative interpretation of the diagnostic report.") value=&quot;[<span style="color: darkgreen">[string](datatypes.html#string)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..1**</span> <span style="color: navy">Clinical Interpretation of test results</span><span style="color: Gray"> --&gt;</span>
 &lt;[**codedDiagnosis**](diagnosticreport-definitions.html#DiagnosticReport.codedDiagnosis "Codes for the conclusion.")&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..***</span> <span style="color: darkgreen">[CodeableConcept](datatypes.html#CodeableConcept)</span> <span style="color: navy">[Codes for the conclusion](valueset-clinical-findings.html)</span><span style="color: Gray"> --&gt;</span>&lt;/codedDiagnosis&gt;
 &lt;[**presentedForm**](diagnosticreport-definitions.html#DiagnosticReport.presentedForm "Rich text representation of the entire result as issued by the diagnostic service. Multiple formats are allowed but they SHALL be semantically equivalent.")&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..***</span> <span style="color: darkgreen">[Attachment](datatypes.html#Attachment)</span> <span style="color: navy">Entire Report as issued</span><span style="color: Gray"> --&gt;</span>&lt;/presentedForm&gt;
&lt;/DiagnosticReport&gt;
</pre>

 </div>
</div>

Alternate definitions: [Schema](diagnosticreport.xsd)/[Schematron](diagnosticreport.sch), 
Resource Profile ([XML](diagnosticreport.profile.xml.html), [JSON](diagnosticreport.profile.json.html))

<a name="tx"> </a>

### <span class="sectioncount">4.16.3.1<a name="4.16.3.1"> </a></span> 
Terminology Bindings

<table class="grid">
 <tr><th>Path</th><th>Definition</th><th>Type</th><th>Reference</th></tr>
 <tr><td title="DiagnosticReportNames" valign="top">DiagnosticReport.name </td><td valign="top">Codes that describe Diagnostic Reports</td><td>[Incomplete](terminologies.html#incomplete)</td><td valign="top">[http://hl7.org/fhir/vs/report-names](valueset-report-names.html)</td> </tr>
 <tr><td title="DiagnosticReportStatus" valign="top">DiagnosticReport.status </td><td valign="top">The status of the diagnostic report as a whole</td><td>[Fixed](terminologies.html#code)</td><td valign="top">[http://hl7.org/fhir/diagnostic-report-status](diagnostic-report-status.html)</td> </tr>
 <tr><td title="DiagnosticServiceSection" valign="top">DiagnosticReport.serviceCategory </td><td valign="top">Codes for diagnostic service sections</td><td>[Example](terminologies.html#example)</td><td valign="top">[http://hl7.org/fhir/vs/diagnostic-service-sections](valueset-diagnostic-service-sections.html)</td> </tr>
 <tr><td title="AdjunctDiagnosis" valign="top">DiagnosticReport.codedDiagnosis </td><td valign="top">Diagnoses codes provided as adjuncts to the report</td><td>[Example](terminologies.html#example)</td><td valign="top">[http://hl7.org/fhir/vs/clinical-findings](valueset-clinical-findings.html)</td> </tr>
</table>

Examples of nested report groups: the antibodyhepatitis order panel code for a goup of hepatitis antibody related tests, or the organism code for a group of antibiotic isolate/sensitivities, or a set of perinatal measurements on a single fetus.

## <span class="sectioncount">4.16.4<a name="4.16.4"> </a></span> 
Notes:

*   If the diagnostic procedure was performed on the patient directly, _diagnostic[x]_ is a dateTime, the time it was performed.If specimens were taken, the diagnostically relevant time can be derived from the specimen collection times, butsince detailed specimen information is not always available, and nor is the diagnostically relevant time always exactly the specimen collection time (e.g. complex timed tests), the
reports SHALL always include a _diagnostic[x]_ element. Note that v2 messages often carry a diagnostically relevant time without carrying any specimen information.

*   A report always contains the name of the report itself. The report can also contain a set of observations, which can themselves be simple observations (e.g. atomic results) or can themselves be groups/panels of other observations.The Observation.name is a code that indicates the nature of the observation or panel (e.g. individual measure, organism isolate/sensitivity or antibody functional testing).  When relevant, the observation can specify a particular
specimen from which the result comes.

*   There is rarely a need for more than two levels of nesting in the Observation tree. One known use is for organism sensitivities - see [this example](diagnosticreport-micro1.html).

*   Applications consuming diagnostic reports must take careful note of updated reports, and ensure that retracted reports are appropriately handled.
*   For applications providing diagnostic reports, a report should not be final until all the individual data items
reported with it are final or amended. If a report is retracted, all the results should be retracted by replacingevery result value with the Concept &quot;withdrawn&quot; in the internal terminology [&quot;Special values&quot;](special-values.html)(url = &quot;http://hl7.org/fhir/special-values&quot;), and setting the conclusion (if provided) and the text narrative to sometext like &quot;This report has been withdrawn&quot; in the appropriate language. A reason for retraction may be provided in thenarrative.

### <span class="sectioncount">4.16.4.1<a name="4.16.4.1"> </a></span> Report Content

This resource provides for 3 different ways of presenting the Diagnostic Report:

*   As atomic data items: a hierarchical set of nested references to Observation resources, one or more images, and possibly with a conclusion and/or one or more coded diagnoses
*   As narrative: an XHTML presentation in the standard resource narrative
*   As a &quot;presented form&quot;: A rich text representation of the report - typically a PDF

Note that the conclusion and the coded diagnoses are part of the atomic data, and SHOULD be duplicated in the narrative and in the presented form if the latter is present. 
The narrative and the presented form serve the same function: a representation of the report for a human. The presented form is included since diagnostic service reports 
often contain presentation features that are not easy to reproduce in the HTML narrative. Whether or not the presented form is included, the narrative must be a 
clinically safe view of the diagnostic report; at a minimum, this could be fulfilled by a note indicating that the narrative is not proper representation of 
the report, and that the presented form must be used, or a generated view from the atomic data. However consumers of the report will best be served if the 
narrative contains clinically relevant data from the form. Commonly, the following patterns are used:

*   Simple Laboratory Reports: A single set of atomic observations, and a tabular presentation in narrative. Typically this is encountered in high volume areas such as Biochemistry and Hematology
*   Histopathology Report: A document report in a presented form and the narrative. Possibly a few key images, and some coded diagnoses for registries. If the service is creating a structured report, some atomic data may be included
*   imaging Report; A document report in a presented form and the narrative, with an imaging study reference and possibly some key images. Some imaging reports such as a Bone Density Scan may include some atomic data

Note that the nature of reports from the various disciplines that provide diagnostic reports are changing quickly, 
as expert systems provide improved narrative reporting in high volume reports, structured reporting brings additional 
data to areas that have classically been narrative based, and the nature of the imaging and laboratory procedures are 
merging. As a consequence the patterns described above are only examples of how a diagnostic report can be used.

<a name="search"> </a>

## <span class="sectioncount">4.16.5<a name="4.16.5"> </a></span> Search Parameters

Search parameters for this resource. The standard parameters also apply. See [Searching](search.html) for more information about searching in REST, messaging, and services.

<table class="list">
<tr><td>**Name**</td><td>**Type**</td><td>**Description**</td><td>**Paths**</td></tr>
<tr><td>_id</td><td>[token](search.html#token)</td><td>The logical resource id associated with the resource (must be supported by all servers)</td><td/></tr>
<tr><td>_language</td><td>[token](search.html#token)</td><td>The stated language of the resource</td><td/></tr>
<tr><td>date</td><td>[date](search.html#date)</td><td>The clinically relevant time of the report</td><td>DiagnosticReport.diagnostic[x]</td></tr>
<tr><td>diagnosis</td><td>[token](search.html#token)</td><td>A coded diagnosis on the report</td><td>DiagnosticReport.codedDiagnosis</td></tr>
<tr><td>identifier</td><td>[token](search.html#token)</td><td>An identifier for the report</td><td>DiagnosticReport.identifier</td></tr>
<tr><td>image</td><td>[reference](search.html#reference)</td><td>Reference to the image source</td><td>DiagnosticReport.image.link
([Media](media.html))</td></tr>
<tr><td>issued</td><td>[date](search.html#date)</td><td>When the report was issued</td><td>DiagnosticReport.issued</td></tr>
<tr><td>name</td><td>[token](search.html#token)</td><td>The name of the report (e.g. the code for the report as a whole, as opposed to codes for the atomic results, which are the names on the observation resource referred to from the result)</td><td>DiagnosticReport.name</td></tr>
<tr><td>performer</td><td>[reference](search.html#reference)</td><td>Who was the source of the report (organization)</td><td>DiagnosticReport.performer
([Organization](organization.html), [Practitioner](practitioner.html))</td></tr>
<tr><td>request</td><td>[reference](search.html#reference)</td><td>What was requested</td><td>DiagnosticReport.requestDetail
([DiagnosticOrder](diagnosticorder.html))</td></tr>
<tr><td>result</td><td>[reference](search.html#reference)</td><td>Link to an atomic result (observation resource)</td><td>DiagnosticReport.result
([Observation](observation.html))</td></tr>
<tr><td>service</td><td>[token](search.html#token)</td><td>Which diagnostic discipline/department created the report</td><td>DiagnosticReport.serviceCategory</td></tr>
<tr><td>specimen</td><td>[reference](search.html#reference)</td><td>The specimen details</td><td>DiagnosticReport.specimen
([Specimen](specimen.html))</td></tr>
<tr><td>status</td><td>[token](search.html#token)</td><td>The status of the report</td><td>DiagnosticReport.status</td></tr>
<tr><td>subject</td><td>[reference](search.html#reference)</td><td>The subject of the report</td><td>DiagnosticReport.subject
([Device](device.html), [Location](location.html), [Patient](patient.html), [Group](group.html))</td></tr>
</table>

</div>

				</div>  <!-- /inner-wrapper -->
            </div>  <!-- /row -->
        </div>  <!-- /container -->

    </div>  <!-- /segment-content -->

	<div id="segment-footer" class="segment">  <!-- segment-footer -->
		<div class="container">  <!-- container -->
			<div class="inner-wrapper">

        &copy; HL7.org 2011 - 2014. FHIR DSTU (v0.2.1-2606) generated on Wed, Jul 2, 2014 16:27+0800.   <!-- [QA Report](qa.html) -->   <!-- achive note -->

        <span style="color: #FFFF77">
        Links: [What's a DSTU?](dstu.html) | 
               [Version History](history.html) | 
               [Compare to DSTU](http://services.w3.org/htmldiff?doc1=http%3A%2F%2Fhl7.org%2Fimplement%2Fstandards%2Ffhir%2Fdiagnosticreport.html&amp;doc2=http%3A%2F%2Fhl7.org%2Fimplement%2Fstandards%2FFHIR-Develop%2Fdiagnosticreport.html) | 
               [License](license.html) | 
               [Propose a change](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemAdd&amp;tracker_id=677)   
        </span>

 