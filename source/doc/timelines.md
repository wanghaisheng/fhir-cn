title: 
date: 
categories: doc
---


## <span class="sectioncount">1.4<a name="1.4"> </a></span> FHIR Timelines

FHIR is a standard.  In order to be useful, standards need to evolve.  At the same time, the evolution of standards
needs to be predictable and manageable for the implementation community.  This section provides forward-looking
statements about the expected pattern of FHIR releases as well as the degree of stability and change implementers
should expect from the standard as it continues to evolve.

<a name="levels"/>

### <span class="sectioncount">1.4.1<a name="1.4.1"> </a></span> Standard Levels

FHIR has three descriptive terms that describe the level of stability and implementation readiness associated with
different aspects of the specification.  They are as follows:

<table>
  <tbody>
    <tr>
      <th>Standard Level</th>
      <th>Description</th>
    </tr>
    <tr>
      <th>Draft</th>
      <td>This portion of the specification is not considered to be complete enough or sufficiently reviewed to be
      safe for implementation.  It may have known issues or still in the &quot;in development&quot; stages.  It is included
      in the publication as a place-holder, to solicit feedback from the implementation community and/or to give
      implementers some insight as to functionality likely to be included in future versions of the specification.
      Content at this level should only be implemented by the brave or desparate and is very much &quot;use at your own
      risk&quot;.</td>
    </tr>
    <tr>
      <th>Draft Standard for Trial Use (DSTU)</th>
      <td>This content has been well reviewed and is considered by the authors to be ready for use in production
      systems.  It has been subjected to ballot and approved as an official standard.  However, it has not yet
      seen widespread use in production across the full spectrum of environments it is intended to be used in.  In
      some cases, there may be documented known issues that require implementation experience to determine appropriate
      resolutions for.
      For these reasons, DSTU content is not subject to FHIR [Inter-version Compatibility Rules](compatibility.html).
      Future versions of FHIR may make significant changes to DSTU-level content that are not compatible with
      previously published content.  See [DSTU suggestions](#dstu) for implementation strategies to
      help manage the risk of non-compatible future changes.</td>
    </tr>
    <tr>
      <th>Normative</th>
      <td>This content has been subject to review and production implementation in a wide variety of environments.
      The content is consdiered to be stable and has been 'locked', subjecting it to FHIR 
      [Inter-version Compatibility Rules](compatibility.html).  While changes are possible, they are
      expected to be infrequent and are tightly constrained.</td>
    </tr>
  </tbody>
</table>

The above statuses can apply to both the standard overall as well as to individual components of the FHIR specification.
Specification components cannot ever have a &quot;higher&quot; standard level than the overall specification, but they can have
lower levels.  For example, at DSTU, FHIR can include draft content.  When it reaches Normative, FHIR may include
some content that remains at DSTU or draft levels if that content has not yet reached the criteria for normative.
All content that is at a different ballot level than the overall specification will be clearly identified.

### <span class="sectioncount">1.4.2<a name="1.4.2"> </a></span> FHIR timeline

New versions of FHIR will be published on a release cycle of aproximately 18-24 months.  This frequency is based on
the timelines necessary to develop, implement and review new content as well as the time necessary to undertake the
formal balloting and reconciliation processes required for ANSI-approved standards.  This release cycle also ensures
an opportunity to incorporate implementer feedback from earlier versions of the specification into subsequent versions.

This release (DSTU 2) is hoped to be the final publication of the specification at the DSTU level.  The subsequent
publication of the specification (targeted for 2017) should take the core aspects of the specification and many
of the most broadly used resources to Normative level.  Whether this timeline will be met will be dependent on
uptake and feedback from implementers.  This feedback will also govern exactly which resources, profiles and other content become
normative.  Only content that has been successfully implemented in a wide variety of implementation environments with
minimal divergence from the DSTU specification will be candidates for normative.

Once FHIR has reached normative status, subsequent publications will continue on the 18-24 month schedule with subsequent releases
introducing additional resources, capabilities and other content as well as migrating existing content from draft to DSTU and
DSTU to normative, based on the level of implementation.

<a name="dstu"/>

### <span class="sectioncount">1.4.3<a name="1.4.3"> </a></span> DSTU Suggestions

The FHIR specification is &quot;draft&quot;.  It has been subject to significant review through ballot and other HL7 processes and many aspects of it have been 
implemented and subjected to interoperability testing through Connectathons and early adoption.  However, the degree of testing has varied.  Some resources 
have been well tested in a variety of environments.  Others have received relatively little real-world exercise.  In general, the infrastructure should be 
considered to be more stable than the resources themselves.  In some cases, there are issues on which input is specifically requested during the DSTU period
(see the [Outstanding Issue List](todo.html), and known issues will arise after publication (refer to the 
[FHIR Change Request](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemBrowse&amp;tracker_id=677) tracker for details.)
Guidance from early implementation will help address these areas.

Regardless of the degree of prior implementation, all aspects of the FHIR specification are potentially subject to change.  These changes may be minor 
(clarifications of definitions, etc.) or major (refactoring of resources, changes to serialization rules, eliminating or adding data types, etc.)  There is no 
commitment to backward or forward compatibility during the DSTU process.  Changes will not be made without cause, however the interests of long-term 
implementability will generally trump the impact on early adopters when determining what changes should be made.

This specification has been promoted to DSTU because it is felt that the specification, as is, is implementable and that more value can be gleaned from 
implementer experience than from subsequent review as part of the ballot process.  Implementers who are willing to accept the risk of change (perhaps 
for the benefit of early implementation experience, first mover advantage and the ability to leverage FHIR's intrinsic benefits) are encouraged to implement 
FHIR in real-world systems.  However, those implementers should be aware that local adaptations may be necessary to meet real-world requirements.  Furthermore, 
such implementers should architect their solutions to be tolerant of changes to the specification and, where necessary, to manage interoperability with systems 
that may be using different versions of the specification or different local adaptations.

During the DSTU period, requests for change may be submitted using the HL7 gForge tracker which can be found  
[here](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemBrowse&amp;tracker_id=677).  Where possible, updates to the 
&quot;development&quot; version of the specification will be made in a timely fashion.  A list of these proposed changes will be published 
as a continuously updated supplement to the official DSTU publication.  Implementers should be aware that the changes are not considered &quot;official&quot; until such 
time as they are balloted and approved as part of a subsequent DSTU or Normative publication.  Change requests might be fixes to allow implementation, 
clarifications or enhancements.  In addition, HL7 will be developing and introducing additional resources and profiles as part of the FHIR specification.

SDOs and regulatory bodies that are interested in making use of the FHIR specification should feel free to do so, but should consider and plan for the possibility 
that the specification will evolve and change prior to becoming normative. 

A key objective of the DSTU process is gaining feedback from implementers making use of the specification.  As well, the HL7 has a need to
monitor which portions of FHIR are being implemented in what sorts of environments so as to make an informed decision on when the specification is ready to
proceed to Normative status.  For this reason, all FHIR implementers are asked to complete a short survey which can be found 
[here](https://www.surveymonkey.com/s/PXZTY7Z).

This survey will capture contact and other information that will allow the FMG to perform appropriate monitoring of FHIR DSTU usage.  Survey information will
be kept confidential unless the participant authorizes inclusion of their project in an HL7-maintained wiki page of early implementers.  Confidential submissions
will be reported in aggregate only.

While implementation of the this DSTU release is occurring, development will be progressing on the next (hopefully Normative) release.  This next release will include 
additional resources, profiles and quality enhancements over the current release.  It will also incorporate fixes for issues raised with the 
[FHIR change tracker](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemBrowse&amp;tracker_id=677).  It may be useful for implementers
of the DSTU to browse the development release to get a sense of what changes are likely coming and perhaps to find more robust definitions and guidance than
are available in the first release.  The FHIR development release can be found at [hl7.org/fhir-develop](http://hl7.org/fhir-develop).  Some implementers
who are dependent on content that exists in a draft release may choose to implement based on a particular snapshot of the development release, though in doing so, they
will limit their potential communication partners and would not be considered to be completely FHIR conformant.

</div>

				</div>  <!-- /inner-wrapper -->
            </div>  <!-- /row -->
        </div>  <!-- /container -->

    </div>  <!-- /segment-content -->

	<div id="segment-footer" class="segment">  <!-- segment-footer -->
		<div class="container">  <!-- container -->
			<div class="inner-wrapper">

        © HL7.org 2011+. FHIR DSTU (v0.4.0-3900) generated on Sat, Dec 20, 2014 22:38+0000.   <!-- [QA Report](qa.html) -->   <!-- achive note -->

        <span style="color: #FFFF77">
        Links: [What's a DSTU?](timelines.html) | 
               [Version History](history.html) | 
               [Compare to DSTU](http://services.w3.org/htmldiff?doc1=http%3A%2F%2Fhl7.org%2Fimplement%2Fstandards%2Ffhir%2Ftimelines.html&amp;doc2=http%3A%2F%2Fhl7-fhir.github.io%2F%2Ftimelines.html) | 
               [![CC0](cc0.png)](license.html) | 
               [Propose a change](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemAdd&amp;tracker_id=677)   
        </span>

			</div>  <!-- /inner-wrapper -->
		</div>  <!-- /container -->
	</div>  <!-- /segment-footer -->
  <!-- disqus thread -->
  <!-- disqus -->
  <!-- end disqus -->        