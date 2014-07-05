title:  
date:  
categories: impl
---
<div class="col-9">

# <span class="sectioncount">2.3<a name="2.3"> </a></span> Messaging using FHIR Resources

FHIR Resources can be used in a traditional messaging context, much like HL7 v2. 
Applications asserting conformance to this framework claim to be conformant to &quot;FHIR messaging&quot;. 

In FHIR messaging, a &quot;request message&quot; is sent from a source application to a destination
application when an event happens. Events mostly correspond to things that happen in the 
real world. The request message consists of a [bundle](extras.html#bundle)
[identified by the tag](extras.html#tags) &quot;http://hl7.org/fhir/tag/message&quot;, 
with the first resource in the bundle being a [MessageHeader](messageheader.html) 
resource. The MessageHeader resource has a code - the message event - that identifies the 
nature of the request message, and it also carries additional request metadata. 
The other resources in the bundle depend on the type of the request.

The events supported in FHIR, along with the resources that are included in them, are defined below. 

The destination application processes the request and returns one or more response messages 
which are also a [bundle](extras.html#bundle) of resources
[identified by the tag](extras.html#tags) &quot;http://hl7.org/fhir/tag/message&quot;, with the first 
resource in the bundle being a [MessageHeader](messageheader.html) resource with a response
section that reports the outcome of processing the message and any additional response 
resources required. 

## <span class="sectioncount">2.3.1<a name="2.3.1"> </a></span> Basic Messaging Assumptions

This specification assumes that content will be delivered from one application
to another by some delivery mechanism, and then a response will be returned 
to the source application. The exact mechanism of transfer is irrelevant to
this specification, but may include file transfer, http based transfer, MLLP
(HL7 minimal lower layer protocol), MQ series messaging or anything else. 
The only requirement for the transfer layer is that requests are sent to 
a known location and responses are returned to the source of the request. 
This specification considers the source and destination applications as logical
entities, and the mapping from logical source and destination to implementation
specific addresses is outside the scope of this specification, though this 
specification does provide a direct delivery mechanism below.

This specification assumes that content will be delivered from one application to 
another by some delivery mechanism, and then one or more responses will be returned 
to the source application. The agreements around the content of the messages and
the behavior of the two applications form the &quot;contract&quot; that describes the exchange.
The contract will add regional and local agreements to the rules defined in this 
specification.

This specification ignores the existence of interface engines and message 
transfer agents that exist between the _source_ and _destination_. 
Either they are transparent to the message/transaction content and irrelevant 
to this specification, or they are actively involved in manipulating the message 
content (in particular, the source and destination headers are often changed). 
If these middleware agents are modifying the message content, then they become
responsible for honoring the contract that applies (including applicable profiles) 
in both directions.

A key aspect of a message is the impact of it's content:

  <!-- <table class="grid">
 <tr> <td>Consequence</td> <td>The message represents/requests a change that should not be processed more than once. E.g. Making a booking for an appointment</td> </tr>
 <tr> <td>Currency</td> <td>The message represents a response to query for current information. Retrospective processing is wrong and/or wasteful</td> </tr>
 <tr> <td>Notification</td> <td>The content is not necessarily intended to be current, and it can be reprocessed, though there may be version issues created by processing old notifications</td> </tr>
</table> -->
<table class="codes">
 <tr><td>Consequence</td><td>The message represents/requests a change that should not be processed more than once. E.g. Making a booking for an appointment.</td></tr>
 <tr><td>Currency</td><td>The message represents a response to query for current information. Retrospective processing is wrong and/or wasteful.</td></tr>
 <tr><td>Notification</td><td>The content is not necessarily intended to be current, and it can be reprocessed, though there may be version issues created by processing old notifications.</td></tr>
</table>

Some Events defined by FHIR are assigned to one of these categories, 
but others are not able to be categorized in advance, and the category
must be determined by the content, or the context.

<a name="synchronous"> </a>
<a name="patterns"> </a>

### <span class="sectioncount">2.3.1.1<a name="2.3.1.1"> </a></span> Message Exchange Patterns

Each FHIR request message has one or more response messages. There must be at least 
one response message so that the sender can know that the message was properly
received. Multiple response SHALL not be returned for messages of consequence,
and SHOULD not be returned for notifications. 

In principle, source applications are not required to wait for a response to 
a transaction before issuing a new transaction. However in many cases, the 
messages in a given stream are dependent on each other, and must be sent and 
processed in order. In addition, some transfer methods may require sequential 
delivery of messages.

For this reason, a synchronous exchange pattern - where the sender sends a 
message, and waits on the same channel for a single response, and then 
sends the next message - are the easiest to understand and manage. The 
[Mailbox](#mailbox) described below works in this fashion.

However synchronous message exchange does not cater for multiple response 
messages, which may arise when processing queries, and also imposes 
through-put limitations which may become relevant at high volumes. 
Because of this, other complex message patterns are allowed, though 
none are described in detail in this specification.

### <span class="sectioncount">2.3.1.2<a name="2.3.1.2"> </a></span> Message Identifiers

An incoming message contains two identifiers: the envelope id 
([feed](extras.html#bundles).id) and the [message](messageheader.html).identifier. 
Each time a new message is created, it SHALL be assigned an identifier that is 
unique within that message stream. Note that since message streams are often 
merged with other streams, it is recommended that the identifier should be globally 
unique. This can be achieved by using a UUID or an OID or appropriately 
chosen URI with a serially incrementing number. Each time a message is sent, 
the bundle identifier (feed.id) should be changed to a new value. 

When a receiver receives and processes the message, it responds with a 
new message with a new identifier, wrapped in a bundle which also has a new id. 
The response message also quotes the request message identifier so that the source
system can relate the response to its request.

<a name="reliable"> </a>

### <span class="sectioncount">2.3.1.3<a name="2.3.1.3"> </a></span> Absence of Reliable Messaging

Some of the message delivery mechanisms mentioned above are reliable delivery
systems - the message is always delivered, or an appropriate error is returned
to the source. However most implementations use methods which do not provide
reliable messaging, and either the request or the response can get lost in transit.
FHIR messaging describes a simple approach that receivers SHOULD conform to in 
order to handle the absence of reliable messaging that maintains predictable 
functionality. 

If the sender of the message implements reliable messaging, it SHALL do 
the following when it receives no response to a message within a 
configured timeout period:

<table class="grid">
 <tr><td>Consequence</td><td>Resend the same message (including with the same identifier) with the same envelope id</td></tr>
 <tr><td>Currency</td><td>Resend the same message (including with the same identifier) with a different envelope id</td></tr>
 <tr><td>Notification</td><td>Resend the same message (including with the same identifier) with a different envelope id</td></tr>
</table>

When a receiver implements reliable messaging, it SHALL check the incoming envelope 
id and message identifier against a cache of previously received messages. The 
correct action to take depends on what is received:

<table class="grid">
 <tr><td>Both the envelope id and message identifier have not been received</td><td>This is the normal case, and the message should be processed</td></tr>
 <tr><td>Both envelope and message already received</td><td>The original response has been lost (failed to return to the request issuer), and the original response SHALL be resent</td></tr>
 <tr><td>The message identifier has already been received, but the envelope id is new</td><td>A previously seen message has been resubmitted for processing again. The server may either reprocess the message, or reject the message</td></tr>
 <tr><td>The envelope id has already been received, but the message identifier is new</td><td>This is an error - envelope ids should never be reused</td></tr>
</table>

The duration period for caching does generally not need to be very long. At a minimum, it 
could be 1 minute longer than the timeout of the sending system, though it may need to 
be longer depending on the re-sending policies of the sending system. 

Applications that implement reliable messaging declare their reliable cache 
period in their [conformance statement](conformance.html).

#### <span class="sectioncount">2.3.1.3.1<a name="2.3.1.3.1"> </a></span> Example: Consequence

In the first example, a Clinical EHR issues an order for a particular imaging examination 
to be performed on a patient. This is considered to be a message of **Consequence**: multiple
orders should not be created (in practice there are usually human review processes that 
catch multiple orders, but repeat orders create entropy in the system that is harmful). 
The EHR sends a message where the envelope id (feed.id) is UUID 1 (urn:uuid:72edc4e0-6708-42ab-9734-f56721882c10), 
with a Message Header that contains a message id of UUID 2 (urn:uuid:dad53a57-dcb4-4f18-b066-7239eb4b5229).

The EHR system never receives a response to the message; it does not know whether the request
message got lost, or the imaging management systems was unable to process the request, or whether
it successfully processed the message and the response was lost. In this case, the EHR system
resends the message with same two identifiers. 

In this case, the imaging system successfully received the message, and processed it. Because
it receives the resent order after 1 minute (which is within it's 15 minute cache time), 
and the two UUIDs 1 and 2 match a message it has already processed, it knows that it already 
processed the order, and simply returns the previous response. In the case of additional resent
queries, the application keeps sending the original response, though it may also alert system
administrators that the same original message keeps being resent, since lost messages should be 
a rare occurrence.

When the EHR system finally receives the message, it knows how the imaging management system 
responded; it can be sure because the message id from the original request is echoed in the 
response portion of the returned message.

#### <span class="sectioncount">2.3.1.3.2<a name="2.3.1.3.2"> </a></span> Example: Currency

In this second example, a Clinical EHR needs to know what appointment slots are available
for a particular imaging procedure. This is a message of **Currency**: available slots are 
ever disappearing, and ordering a slot that has become unavailable is a waste of time for 
the humans and systems involved. The EHR sends a message where the envelope id (feed.id) is 
UUID 3 (urn:uuid:4c7f5cb2-5964-4d42-b719-e0227461818c), with a Message Header that contains 
a message id of UUID 4 (urn:uuid:63ED7D68-B2CC-421D-BA1C-A6C7785581F2).

The EHR system never receives a response to the message; it does not know whether the request
message got lost, or the imaging management systems was unable to process the request, or whether
it successfully processed the message and the response was lost. In this case, the EHR system
resends the message with same message id (UUID 4), but creates a new envelope id (feed.id):
(urn:uuid:c7c17fe4-9560-49c7-b2ae-42636476fb86).

In this case, the imaging system successfully received the message, and processed it. When 
it receives the resent order after 1 minute (which is within it's 15 minute cache time), it 
sees that although the message id is the same, the envelope id has changed, and it reprocesses
the message again, and sends a new response.

When the EHR system finally receives the message, it knows the current slot availability 
on the imaging management system responded. 

Note that the existence of active intermediaries (or &quot;middleware&quot;) creates the need
for this protocol - the original sender matches the response to the request based on the 
message id, and so an active intermediary that choose the re-initiate a query that
it previously relayed cannot change the message id. This protocol avoids the need for
the message id to change, and only requires change to the envelope id which is never
the basis for context linking outside the immediate message exchange protocol described
here.

## <span class="sectioncount">2.3.2<a name="2.3.2"> </a></span> Conformance Statement

Applications may only assert conformance to &quot;FHIR messaging&quot; if they 
publish a conformance statement so the claim may be verified. A 
conformance statement lists all the message events supported (either 
as sender or receiver) and for each event, a 
profile that states which resources are bundled (sender), or 
are required to be bundled (receiver), and any rules about the 
information content of the individual resources. The conformance 
statement is a [resource with the name 
&quot;Conformance&quot;](conformance.html). 

<a name="mailbox"/>

## <span class="sectioncount">2.3.3<a name="2.3.3"> </a></span> Mailbox

The mailbox is the standard name for a service hosted on a [RESTful server](http.html) that accepts 
messages and processes 
them as transactions and returns a message response appropriate for the message received. The server is under
no obligation to do anything particular with the resources except as required by the semantics of the event code in
the message resource. A server may choose to retain the resources and make them available on a RESTful interface, but 
is not required to do so.

### <span class="sectioncount">2.3.3.1<a name="2.3.3.1"> </a></span> Submitting query messages and documents

The mailbox can also be used to accept queries or documents. In the case of documents, the document is &quot;accepted&quot; 
(the server takes responsibility for custody of the received document) 
or an HTTP error is returned. The server is under no obligation to perform any particular processing of the document
except as 
specific trading partner agreements dictate. In the case of queries, the server receives a bundle containing 
a query and a set of other related resources, processes the query, and returns a bundle with a query which is a response,
and any additional resources that are part of the query response.

### <span class="sectioncount">2.3.3.2<a name="2.3.3.2"> </a></span> Result of submission

Depending on the semantics of the event code or processing done on the query or document, a server may return 
a status code 200 OK, 201 Created, 202 Accepted or 204 No Content. If the server returns 200 OK, it SHALL return a 
bundle with the outcome of the event or document processing. In case of errors, the client SHALL interpret a 
4xx response to indicate that there is no point resubmitting the message or document, and a 5xx response to indicate 
an unexpected error on the part of the server, which means that it is worth resubmitting 
(and doing so should not result in a duplicate message response).  Repeated failures indicate either a
fatal problem with the submission or a problem with the receiving application.

The following rules apply to the mailbox:

*   The mailbox only accepts POST transactions - any other HTTP method will result in an HTTP error
*   The request content type submitted is always [a bundle](extras.html#bundle) containing a message or document resource as the first resource
*   The response content type returned is always an HTTP error, [a bundle](extras.html#bundle) containing a message as the first resource, or empty (if a document was received)
*   If the response is an error, the body SHOULD be an [Errors &amp; Warning](operationoutcome.html) resource with full details
*   The URL never takes any parameters
*   The mailbox may be authenticated using standard HTTP authentication methods, including OAuth

This simple mailbox profile can be used by any HTTP end point that accepts FHIR messages or documents, not just 
FHIR RESTful servers.

In order to ensure consistency of processing, the [logical rules regarding processing of envelope id and 
message id described above](#reliable) SHALL be followed when messages are processed using the mailbox. No such rules apply regarding
documents - if the client receives no response, it should continue to submit the document until it does. Servers SHALL 
accept multiple document submissions and process them correctly.

<a name="endpoints"/>

## <span class="sectioncount">2.3.4<a name="2.3.4"> </a></span> Relationship between Messaging and REST

As well as this messaging framework documented here, FHIR also defines a 
[RESTful API](http.html). The messaging and RESTful frameworks
are related in that both share the same set of resources on which they operate.
In fact, the basic [MessageHeader](messageheader.html) resource 
that the messaging framework is implemented is itself a resource that can treated in a RESTful approach. 

The kinds of functionality that the RESTful API and the messaging framework
offer are very similar; their primary difference is architectural in nature. 

For instance, the messaging framework defines an event for notifying that
a administration resource has been created or updated, as does the REST API.
On the other hand, there are differences in the capabilities offered - while
a patient merge can be implemented as a series of RESTful operations performed
by the client that update all resources linked to the patient, when a message 
command to merge patient records is processed, the server will do all
the work, and is also able to merge in areas not exposed on the RESTful API.
The REST API, however, provides a set of basic operations on all resources
that would need special definitions in the messaging framework - definitions that
are not provided.

There is no expectation that RESTful systems will need to offer messaging
support, or vice versa, though systems may find it useful to support both 
sets of functionality in order to satisfy a wider range of implementers. 

As a resource that can be used with the RESTful framework, the MessageHeader
resource has the normal resource end-point (/MessageHeader), which is
used to manage a set of static message resources. This could be used to 
make an archive of past messages available. **Creating or updating MessageHeader resources
in this fashion does not represent the actual occurrence of any event, nor can it trigger
any logic associated with the actual event.** It is just for managing a set of message resources.

In, addition, as described above, this specification defines the /Mailbox end-point
so that RESTful servers can offer both messaging and RESTful services at once.
Alternatively, messages can be transported between systems using any other method by which 
a stream of bytes (the message bundle) can be moved from one place to 
another. There is no requirement to use HTTP.

<a name="Events"/>
<a name="events"/>

## <span class="sectioncount">2.3.5<a name="2.3.5"> </a></span> Event List

The _message.code_ element carries a [Coding](datatypes.html#Coding) that identifies the event that the message conveys. 
This table lists the message event codes defined in this specification (the system value for these is &quot;http://hl7.org/fhir/message-type&quot;):

<table class="grid">
 <tr><th>Code</th><th>Category</th><th>Description</th><th>Request</th><th>Response</th><th>Notes</th></tr>
 <tr><td>MedicationAdministration-Complete<a name="MedicationAdministration-Complete"> </a></td><td>Consequence</td><td>Change the status of a Medication Administration to show that it is complete.</td><td>MedicationAdministration</td><td>MedicationAdministration</td><td/></tr>
 <tr><td>MedicationAdministration-Nullification<a name="MedicationAdministration-Nullification"> </a></td><td>Consequence</td><td>Someone wishes to record that the record of administration of a medication is in error and should be ignored.</td><td>MedicationAdministration</td><td>MedicationAdministration</td><td/></tr>
 <tr><td>MedicationAdministration-Recording<a name="MedicationAdministration-Recording"> </a></td><td>Consequence</td><td>Indicates that a medication has been recorded against the patient's record.</td><td>MedicationAdministration</td><td>MedicationAdministration</td><td/></tr>
 <tr><td>MedicationAdministration-Update<a name="MedicationAdministration-Update"> </a></td><td>Consequence</td><td>Update a Medication Administration record.</td><td>MedicationAdministration</td><td>MedicationAdministration</td><td/></tr>
 <tr><td rowspan="8">admin-notify</td><td rowspan="8">Notification that a patient or other administrative resource as been created or updated.</td><td>Device</td><td><font color="silver">--</font></td><td/></tr>
 <tr><td>Device</td><td><font color="silver">--</font></td><td/></tr>
 <tr><td>Group</td><td><font color="silver">--</font></td><td/></tr>
 <tr><td>Location</td><td><font color="silver">--</font></td><td/></tr>
 <tr><td><font color="silver">--</font></td><td>Organization</td><td>(see Patient)</td></tr>
 <tr><td>Patient</td><td><font color="silver">--</font></td><td/></tr>
 <tr><td>Practitioner</td><td><font color="silver">--</font></td><td/></tr>
 <tr><td><font color="silver">--</font></td><td>RelatedPerson</td><td/></tr>
 <tr><td>diagnosticreport-provide<a name="diagnosticreport-provide"> </a></td><td>Notification</td><td>Provide a diagnostic report, or update a previously provided diagnostic report.</td><td>DiagnosticReport
&nbsp;DiagnosticReport.patient
&nbsp;DiagnosticReport.perfomer
&nbsp;DiagnosticReport.results.specimen
&nbsp;DiagnosticReport.results.result
&nbsp;DiagnosticReport.image</td><td><font color="silver">--</font></td><td/></tr>
 <tr><td>observation-provide<a name="observation-provide"> </a></td><td>Notification</td><td>Provide a simple observation or update a previously provided simple observation.</td><td>Observation
&nbsp;Observation.subjectPatient
&nbsp;Observation.subjectPatient.person
&nbsp;Observation.subjectGroup
&nbsp;Observation.subjectDevice
&nbsp;Observation.subjectAnimal
&nbsp;Observation.performerAgent
&nbsp;Observation.performerAgent.person
&nbsp;Observation.performerPatient
&nbsp;Observation.performerPerson</td><td><font color="silver">--</font></td><td/></tr>
 <tr><td>patient-link<a name="patient-link"> </a></td><td>Notification</td><td>Notification that two patient records actually identify the same patient.</td><td>Patient,Patient</td><td><font color="silver">--</font></td><td>Follow ups: patient-unlink?</td></tr>
 <tr><td>patient-unlink<a name="patient-unlink"> </a></td><td>Notification</td><td>Notification that previous advice that two patient records concern the same patient is now considered incorrect.</td><td>Patient,Patient</td><td><font color="silver">--</font></td><td/></tr>
 <tr><td>query<a name="query"> </a></td><td>??</td><td>Request to perform a query according to the attached query resource.</td><td>query</td><td>query</td><td/></tr>
 <tr><td>query-response<a name="query-response"> </a></td><td>??</td><td>Response with the result of processing the query.</td><td>query</td><td><font color="silver">--</font></td><td>Used when queries are performed asynchronously</td></tr>
</table>

<a name="dstu"> </a>

In this table, the request and response columns list the focus resource for the event, along with other resources that should also be carried in the message directly (if they exist).
Additional events may be defined elsewhere, though this specification does not yet define how. DSTU: Input on this is sought during the trial use period.

</div> 