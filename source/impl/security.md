title:  
date:  
categories: impl
---
<div class="col-9">

# <span class="sectioncount">2.13.0<a name="2.13.0"> </a></span> FHIR Security

Fast Healthcare Interoperability Resources (FHIR) is not a security protocol, nor does it define any security
related functionality. However FHIR does define exchange protocols and content models that need to be used
with various security protocols defined elsewhere. This section gathers all information about security
in one section. A summary:

*   Communications Security - all exchange of production data should be secured using TLS/SSL (e.g. https)
*   Authentication - Users/Clients may be authenticated in any way desired. For web-centric use, OAuth is recommended
*   Authorization/Access Control - FHIR defines a Security Label infrastructure to support access control management. FHIR may also define a set of resources to administer access control management, but does not define any at present
*   Audit - FHIR defines [provenance](provenance.html) and [security event](securityevent.html) resources suitable for tracking the origins, authorship, history, status and access of resources
*   Digital Signatures - FHIR includes several specifically reserved locations for digital signatures
*   Attachments - FHIR allows for binary resources and attachments. These have their own concerns
*   [Labels](security-labels.html) - FHIR allows for set of security related tags that affect that way resources are handled
*   Data Management Policies - FHIR defines a set of capabilities to support data exchange.
     Not all the capabilities that FHIR enables may be appropriate or legal for use in some combinations of context and jurisdiction (e.g. HIPAA for exchange between institutions).     It is the responsibility of implementers to ensure that relevant regulations and other requirements are met
*   Narrative - Care must be taken when displaying the narrative from FHIR resources

Time critical concerns regarding security flaws in the FHIR specification should be addressed to 
the [FHIR email 
list](http://wiki.hl7.org/index.php?title=FHIR_email_list_subscription_instructions "FHIR_email_list_subscription_instructions") for prompt consideration. Alternatively, issues can be raised through the 
[community input](http://wiki.hl7.org/index.php?title=FHIR_Security_Page "FHIR_Security_Page") mechanism.

Implementers should track the developing IHE IUA Profile for additional security considerations.

A production FHIR system will need some kind of security sub-system that administers 
users, user authentication and user-authorization. Where this sub-system fits into the 
deployment architecture is a matter for system design:

<table class="dense">
 <tr>
  <td valign="center">
 ![](security-layout.png)
</td>
<td>&nbsp;&nbsp;&nbsp;</td>
<td style="border-left: 1px solid grey" valign="center">
<table class="dense">
 <tr><td>![](security-icon-user.png)</td><td>The consumer that is using a healthcare related system</td></tr>
 <tr><td>![](security-icon-app.png)</td><td>The client application the user is using (application, mobile app, website, etc.)</td></tr>
 <tr><td>![](security-icon-sec.png)</td><td>The security system (authentication and access control)</td></tr>
 <tr><td>![](security-icon-fhir.png)</td><td>The clinical/healthcare repository</td></tr>
</table>
</td></tr></table>

In this diagram, the red lines represent FHIR interfaces. From the perspective of the FHIR API, 
the client (consumer of FHIR services) may either interact with a security system that manifests
as a FHIR server, and which depends on a subsequent FHIR interface to provide the actual storage,
or either the client or server interacts with the security system independently. In each of these
3 scenarios, the different components may be assembled into applications or network components
differently, but the same logical layout applies. The FHIR specification assumes that a security 
system exists, and that it may be deployed in front of or behind the FHIR API. 

<a name="access-control"> </a>

The security system includes the following subsystems:

*   Authentication: Identifies and Authenticates the user
*   Access Control decision engine: decides whether FHIR operations are allowed
*   Audit Log: records actions to allow for subsequent review and detection of intrusion or inappropriate usage

Because there are a plethora of standards relating to 
the administration and functionality of the security system, FHIR does not provide user,
profile, or other such administration resources. Instead, the FHIR resources are the targets
of the policies expressed in these other approaches. What FHIR does specify is a way to apply
[security labels](security-labels.html) to resources so that a security system may use these (along with the contents
of the resources if appropriate) to determine whether a user is authorized to perform a 
particular FHIR operation or not.

  <!-- These HTTP calls may be authenticated against a single user account (including 
using [OAuth](http://www.oauth.org)), but this arrangement doesn't cater for common transaction metadata such as multiple users, 
responsible party, reasons, consents, etc. that are commonly encountered in healthcare. Instead, 
use of this RESTful implementation assumes that appropriate security and logs are managed by the client (perhaps 
through using [ATNA](http://wiki.ihe.net/index.php?title=Audit_Trail_and_Node_Authentication "Audit_Trail_and_Node_Authentication")), and 
that the server trusts the client to maintain these. One implication is that this RESTful framework is 
only suitable for use where such trust relationships exist (e.g. in a single institution) and is not 
suitable where such trust does not exist (e.g. state &amp; national EHR systems and health record 
systems that support disparate systems). Similarly, this simple RESTful interface has no support for 
explicit archiving and similar functions. Use-cases where these kind of features are required should 
consider a [messaging](messaging.html) or [SOA-based approach](implementation.html#SOA) or 
some other kind of profiled REST interface. -->

<a name="http"> </a>

## <span class="sectioncount">2.13.0.1<a name="2.13.0.1"> </a></span> 
Communications

For the [RESTful API](http.html), normal HTTP security rules apply. 
The [Service Root URL](http.html#root) will specify whether SSL is required. 
Client authentication may be required by the server, possibly including the requirement for 
client certificates.

SSL SHOULD be used for all production data exchange.

To support browser-based client applications, recommend that servers SHOULD implement [cross-origin resource sharing](http://enable-cors.org/) for the [REST operations](http.html).  

<a name="authentication"> </a>

## <span class="sectioncount">2.13.0.2<a name="2.13.0.2"> </a></span> Authentication

Other than testing systems, FHIR servers should authenticate the clients. 
The server may choose to authenticate the client system and trust it, or to authenticate
the individual user by a variety of techniques. For web-centric use, 
[OAuth](http://oauth.net/) may be used to authenticate and/or authorize 
the users. 

  <!-- note about using OAuth and delegating user authority -->

<a name="binding"> </a>

## <span class="sectioncount">2.13.0.3<a name="2.13.0.3"> </a></span> 
Authorization/Access Control

Correctly identifying people, devices, locations and organizations is one of the foundations that any security system is built on. 
Most applications of security protocols, whether authentication, access control, digital signatures, etc. rely on the correct mapping between
the relevant resources and the underlying systems. Note that this isn't necessary: there is nothing in FHIR that requires or relies 
on any security being in place, or any particular implementation. But real world usage will generally require this. 

A holder of data should not allow the data to be communicated unless there is assurances that the 
other party is authorized to receive it. This is true for a Client creating a resource through a PUT/POST, 
as much as it is true for a Server returning resources on a GET. The presumption is that without 
proper authorization, to the satisfaction of the data holder, the data does not get communicated.

The rules behind the Access Control decision are often very complex, and potentially depends on information sourced from:

*   Client, such as User Identity, User Role, Location, level of assurance
*   Resource, such as confidentiality, sensitivity, type of data, date ranges covered by the data, author of the data
*   Patient, such as the patient identity, patient relationship to the user, patient consent policies
*   Context of the transaction, system identity, time-of-day, purpose of use, workflow state, and transport security
  <!-- HL7 has papers on this topic. -->

For one source of further information, see the 
[IHE Access Control white paper](http://www.ihe.net/Technical_Framework/upload/IHE_ITI_TF_WhitePaper_AccessControl_2009-09-28.pdf)

<a name="audit"> </a>

## <span class="sectioncount">2.13.0.4<a name="2.13.0.4"> </a></span> Audit Logging

FHIR provides a [SecurityEvent](securityevent.html) resource suitable for use by 
FHIR clients and servers to record when a security or privacy relevant event has occurred. 
This form of audit logging records as much detail as reasonable at the time the event happened. 

The SecurityEvent when used to record security and privacy relevant events can then be 
used by properly authorized applications to support audit reporting, alerting, filtering, 
and forwarding. This model has been developed and used in healthcare for a decade as 
[IHE-ATNA profile](http://wiki.ihe.net/index.php?title=Audit_Trail_and_Node_Authentication "Audit_Trail_and_Node_Authentication"). 
ATNA log events can be automatically converted to SecurityEvent resources, and from there,
client applications are able to search the security events, or subscribe to them.

<a name="signatures"> </a>

## <span class="sectioncount">2.13.0.5<a name="2.13.0.5"> </a></span> 
Digital Signatures

This specification recommends the use of [W3C Digital Signatures](http://www.w3.org/TR/xmldsig-core/) for signatures.

Resources can be signed using the [Provenance](provenance.html) resource to carry a 
[detached digital signature](http://www.w3.org/TR/xmldsig-core/#def-SignatureDetached) 
for the purpose of detecting subsequent changes to the resource. This signature is not
suitable for non-repudiation purposes. 

In addition, [documents may be signed](documents.html#signatures) using an 
[enveloped](http://www.w3.org/TR/xmldsig-core/#def-SignatureEnveloped) 
signature. 

Neither of these definitions prohibits the use of other ways of using digital signatures.

<a name="dstu"> </a>
> DSTU Note: Additional work is anticipated in this area, including alignment with the [IHE DSG profile](http://wiki.ihe.net/index.php?title=Document_Digital_Signature "Document_Digital_Signature").

<a name="attachments"> </a>

## <span class="sectioncount">2.13.0.6<a name="2.13.0.6"> </a></span> Attachments

Several FHIR resources include attachments. Attachments can either be references to content found elsewhere, or included inline encoded in base64.
Attachments represent security risks in a way that FHIR resources do not, since some attachments contain executable code. Implementers should 
always use caution when handling resources.

<a name="labels"> </a>

## <span class="sectioncount">2.13.0.7<a name="2.13.0.7"> </a></span> Security Labels

See [Security Labels](security-labels.html).

<a name="narrative"> </a>

## <span class="sectioncount">2.13.0.8<a name="2.13.0.8"> </a></span> Narrative

FHIR resources include an XHTML narrative, so that applications can display the contents of the resource to users
without having to fully and correctly process the data in the resource. However displaying HTML is associated 
with several known security issues that have been observed in production systems in other contexts (e.g. 
[with CDA](http://smartplatforms.org/2014/04/security-vulnerabilities-in-ccda-display/)). For
this reason, the [FHIR narrative is not allowed to contain active content](narrative.html#security).
However, care is still needed when displaying the narrative:

*   Validate the narrative (the standard FHIR schemas do not allow active content, and the reference implementations won't handle it). Note, though, that external references could still be included in CSS, and these are outside the scope of schemas and reference implementations.
*   Ensure that any external references to images or anchors (e.g. outside the resource) do not cause the display software to [leak sensitive information in headers](http://smartplatforms.org/2014/04/security-vulnerabilities-in-ccda-display/)
*   Do not allow external links to run in a privileged context such as the EHR unless you are sure they can be trusted

Also note that the inclusion of an external reference to an image can allow the server that hosts the image to track 
when the resource is displayed. This may be a feature or a problem depending on the context.

</div>