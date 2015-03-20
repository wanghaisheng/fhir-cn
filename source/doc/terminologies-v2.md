title: 
date: 
categories: doc
---

  [首页](../home/index.html) >[文档](documentation.html) > [编码的使用](terminologies.html) > **V2 中的表**	
  
  
  
  *   [Content](terminologies.html)
  *   [ Named Systems List](terminologies-systems.html)
  *   [value sets](terminologies-valuesets.html)
  *   [V2 表格](terminologies-v2.html)
  *   [V3 命名空间](terminologies-v3.html)
  *   [Concept Map字典映射](terminologies-conceptmaps.html)  
  *   [术语服务](terminologies-service.html)




####  1.22.3.0  HL7 Version 2 Table Namespaces

这些系统命名空间是用来定义在FHIR 中使用那些在 V2 表格里定义的编码。如果你要在FHIR 数据实例中表示编码 HL7 v2.3.1 表0001中的 &quot;M&quot;，你应该使用编码系统 &quot;http://hl7.org/fhir/v2/0001&quot;.

要把 V2定义的表格当做 code system 来用，有一些subtle but serious的问题，因此其中一些表的不同版本 我们把它们映射成不同版本的命名空间。需要注意的是，即使将多个版本映射成同一个命名空间，也会存在一些问题，there are different formal code systems for different versions.

随着后续V2 表格评审工作的进行 所有的命名空间都可能会变化。


<table class="grid">
 <tr><td>**URI**</td><td>**ID**</td><td>**Comments**</td></tr>
 <tr><td>[http://hl7.org/fhir/v2/0001](v2/0001/index.html)</td><td>Administrative Sex</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0002](v2/0002/index.html)</td><td>Marital Status</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0003](v2/0003/index.html)</td><td>Event Type</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0004](v2/0004/index.html)</td><td>Patient Class</td><td/></tr>
 <tr><td>http://hl7.org/fhir/v2/0006</td><td>0006</td><td>Religion
Version Dependent. Use one of:

*   [2.1](v2/0006/2.1/index.html)
*   [2.4+](v2/0006/2.4+/index.html)</td></tr>
 <tr><td>[http://hl7.org/fhir/v2/0007](v2/0007/index.html)</td><td>Admission Type</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0027](v2/0027/index.html)</td><td>Priority</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0038](v2/0038/index.html)</td><td>Order status</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0048](v2/0048/index.html)</td><td>What subject filter</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0052](v2/0052/index.html)</td><td>Diagnosis Type</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0061](v2/0061/index.html)</td><td>Check Digit Scheme</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0063](v2/0063/index.html)</td><td>Relationship</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0065](v2/0065/index.html)</td><td>Specimen Action Code</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0074](v2/0074/index.html)</td><td>Diagnostic Service Section ID</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0076](v2/0076/index.html)</td><td>Message Type</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0078](v2/0078/index.html)</td><td>Interpretation Codes</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0100](v2/0100/index.html)</td><td>Invocation event</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0102](v2/0102/index.html)</td><td>Delayed acknowledgment type</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0103](v2/0103/index.html)</td><td>Processing ID</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0104](v2/0104/index.html)</td><td>Version ID</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0105](v2/0105/index.html)</td><td>Source of Comment</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0106](v2/0106/index.html)</td><td>Query/response format code</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0107](v2/0107/index.html)</td><td>Deferred response type</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0108](v2/0108/index.html)</td><td>Query results level</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0109](v2/0109/index.html)</td><td>Report priority</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0119](v2/0119/index.html)</td><td>Order Control Codes</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0121](v2/0121/index.html)</td><td>Response Flag</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0122](v2/0122/index.html)</td><td>Charge Type</td><td/></tr>
 <tr><td>http://hl7.org/fhir/v2/0123</td><td>0123</td><td>Result Status
Version Dependent. Use one of:
*   [2.2-](v2/0123/2.2-/index.html)
*   [2.3+](v2/0123/2.3+/index.html)</td></tr>
 <tr><td>[http://hl7.org/fhir/v2/0124](v2/0124/index.html)</td><td>Transportation Mode</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0126](v2/0126/index.html)</td><td>Quantity Limited Request</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0136](v2/0136/index.html)</td><td>Yes/no Indicator</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0148](v2/0148/index.html)</td><td>Money or Percentage Indicator</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0153](v2/0153/index.html)</td><td>Value Code</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0155](v2/0155/index.html)</td><td>Accept/Application Acknowledgment Conditions</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0156](v2/0156/index.html)</td><td>Which date/time qualifier</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0157](v2/0157/index.html)</td><td>Which date/time status qualifier</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0158](v2/0158/index.html)</td><td>Date/time selection qualifier</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0159](v2/0159/index.html)</td><td>Diet Code Specification Type</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0160](v2/0160/index.html)</td><td>Tray Type</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0161](v2/0161/index.html)</td><td>Allow Substitution</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0162](v2/0162/index.html)</td><td>Route of Administration</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0163](v2/0163/index.html)</td><td>Body Site</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0164](v2/0164/index.html)</td><td>Administration Device</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0165](v2/0165/index.html)</td><td>Administration Method</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0166](v2/0166/index.html)</td><td>RX Component Type</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0167](v2/0167/index.html)</td><td>Substitution Status</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0168](v2/0168/index.html)</td><td>Processing Priority</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0169](v2/0169/index.html)</td><td>Reporting Priority</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0170](v2/0170/index.html)</td><td>Derived Specimen</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0174](v2/0174/index.html)</td><td>Nature of Service/Test/Observation</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0175](v2/0175/index.html)</td><td>Master File Identifier Code</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0178](v2/0178/index.html)</td><td>File Level Event Code</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0179](v2/0179/index.html)</td><td>Response Level</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0180](v2/0180/index.html)</td><td>Record-level Event Code</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0183](v2/0183/index.html)</td><td>Active/Inactive</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0185](v2/0185/index.html)</td><td>Preferred Method of Contact</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0187](v2/0187/index.html)</td><td>Provider Billing</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0190](v2/0190/index.html)</td><td>Address Type</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0191](v2/0191/index.html)</td><td>Type of Referenced Data</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0200](v2/0200/index.html)</td><td>Name Type</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0201](v2/0201/index.html)</td><td>Telecommunication Use Code</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0202](v2/0202/index.html)</td><td>Telecommunication Equipment Type</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0203](v2/0203/index.html)</td><td>Identifier Type</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0205](v2/0205/index.html)</td><td>Price Type</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0206](v2/0206/index.html)</td><td>Segment action code</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0207](v2/0207/index.html)</td><td>Processing Mode</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0210](v2/0210/index.html)</td><td>Relational Conjunction</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0211](v2/0211/index.html)</td><td>Alternate Character Sets</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0227](v2/0227/index.html)</td><td>Manufacturers of Vaccines (code=MVX)</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0234](v2/0234/index.html)</td><td>Report Timing</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0235](v2/0235/index.html)</td><td>Report Source</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0236](v2/0236/index.html)</td><td>Event Reported To</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0237](v2/0237/index.html)</td><td>Event Qualification</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0238](v2/0238/index.html)</td><td>Event Seriousness</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0239](v2/0239/index.html)</td><td>Event Expected</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0240](v2/0240/index.html)</td><td>Event Consequence</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0241](v2/0241/index.html)</td><td>Patient Outcome</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0242](v2/0242/index.html)</td><td>Primary Observer's Qualification</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0243](v2/0243/index.html)</td><td>Identity May Be Divulged</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0247](v2/0247/index.html)</td><td>Status of Evaluation</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0248](v2/0248/index.html)</td><td>Product Source</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0250](v2/0250/index.html)</td><td>Relatedness Assessment</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0251](v2/0251/index.html)</td><td>Action Taken in Response to the Event</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0252](v2/0252/index.html)</td><td>Causality Observations</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0254](v2/0254/index.html)</td><td>Kind of Quantity</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0256](v2/0256/index.html)</td><td>Time Delay Post Challenge</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0267](v2/0267/index.html)</td><td>Days of the Week</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0271](v2/0271/index.html)</td><td>Document Completion Status</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0272](v2/0272/index.html)</td><td>Document Confidentiality Status</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0273](v2/0273/index.html)</td><td>Document Availability Status</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0274](v2/0274/index.html)</td><td>Document Modification Status</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0275](v2/0275/index.html)</td><td>Document Storage Status</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0276](v2/0276/index.html)</td><td>Appointment reason codes</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0279](v2/0279/index.html)</td><td>Allow Substitution Codes</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0280](v2/0280/index.html)</td><td>Referral Priority</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0281](v2/0281/index.html)</td><td>Referral Type</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0282](v2/0282/index.html)</td><td>Referral Disposition</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0283](v2/0283/index.html)</td><td>Referral Status</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0284](v2/0284/index.html)</td><td>Referral Category</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0286](v2/0286/index.html)</td><td>Provider Role</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0287](v2/0287/index.html)</td><td>Problem/Goal Action Code</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0290](v2/0290/index.html)</td><td>MIME base64 encoding characters</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0291](v2/0291/index.html)</td><td>Subtype of Referenced Data</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0292](v2/0292/index.html)</td><td>Vaccines Administered (code = CVX) (parenteral, unless oral is noted)</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0298](v2/0298/index.html)</td><td>CP Range Type</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0299](v2/0299/index.html)</td><td>Encoding</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0316](v2/0316/index.html)</td><td>Organ Donor Code</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0347](v2/0347/index.html)</td><td>State/Province</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0348](v2/0348/index.html)</td><td>Special Program Indicator</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0349](v2/0349/index.html)</td><td>PSRO/UR Approval Indicator</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0350](v2/0350/index.html)</td><td>Occurrence Code</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0351](v2/0351/index.html)</td><td>Occurrence Span</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0353](v2/0353/index.html)</td><td>CWE statuses</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0354](v2/0354/index.html)</td><td>Message Structure</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0371](v2/0371/index.html)</td><td>Additive/Preservative</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0373](v2/0373/index.html)</td><td>Treatment</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0411](v2/0411/index.html)</td><td>Supplemental Service Information Values</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0445](v2/0445/index.html)</td><td>Identity Reliability Code</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0487](v2/0487/index.html)</td><td>Specimen Type</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0488](v2/0488/index.html)</td><td>Specimen Collection Method</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0489](v2/0489/index.html)</td><td>Risk Codes</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0490](v2/0490/index.html)</td><td>Specimen Reject Reason</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0491](v2/0491/index.html)</td><td>Specimen Quality</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0492](v2/0492/index.html)</td><td>Specimen Appropriateness</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0493](v2/0493/index.html)</td><td>Specimen Condition</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0494](v2/0494/index.html)</td><td>Specimen Child Role</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0495](v2/0495/index.html)</td><td>Body Site Modifier</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0496](v2/0496/index.html)</td><td>Consent Type</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0497](v2/0497/index.html)</td><td>Consent Mode</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0498](v2/0498/index.html)</td><td>Consent Status</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0499](v2/0499/index.html)</td><td>Consent Bypass Reason</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0500](v2/0500/index.html)</td><td>Consent Disclosure Level</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0501](v2/0501/index.html)</td><td>Consent Non-Disclosure Reason</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0502](v2/0502/index.html)</td><td>Non-Subject Consenter Reason</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0503](v2/0503/index.html)</td><td>Sequence/Results Flag</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0504](v2/0504/index.html)</td><td>Sequence Condition Code</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0505](v2/0505/index.html)</td><td>Cyclic Entry/Exit Indicator</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0506](v2/0506/index.html)</td><td>Service Request Relationship</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0507](v2/0507/index.html)</td><td>Observation Result Handling</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0508](v2/0508/index.html)</td><td>Blood Product Processing Requirements</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0510](v2/0510/index.html)</td><td>Blood Product Dispense Status</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0511](v2/0511/index.html)</td><td>BP Observation Status Codes Interpretation</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0513](v2/0513/index.html)</td><td>Blood Product Transfusion/Disposition Status</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0514](v2/0514/index.html)</td><td>Transfusion Adverse Reaction</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0516](v2/0516/index.html)</td><td>Error Severity</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0517](v2/0517/index.html)</td><td>Inform Person Code</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0518](v2/0518/index.html)</td><td>Override Type</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0520](v2/0520/index.html)</td><td>Message Waiting Priority</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0634](v2/0634/index.html)</td><td>Item Importance Codes</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0728](v2/0728/index.html)</td><td>CCL Value</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0731](v2/0731/index.html)</td><td>DRG Diagnosis Determination Status</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0734](v2/0734/index.html)</td><td>Grouper Status</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0739](v2/0739/index.html)</td><td>Status Patient</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0742](v2/0742/index.html)</td><td>DRG Status Financial Calculation</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0749](v2/0749/index.html)</td><td>DRG Grouping Status</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0755](v2/0755/index.html)</td><td>Status Weight At Birth</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0757](v2/0757/index.html)</td><td>Status Respiration Minutes</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0759](v2/0759/index.html)</td><td>Status Admission</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0761](v2/0761/index.html)</td><td>DRG Procedure Determination Status</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0763](v2/0763/index.html)</td><td>DRG Procedure Relevance</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0776](v2/0776/index.html)</td><td>Item Status</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0778](v2/0778/index.html)</td><td>Item Type</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0790](v2/0790/index.html)</td><td>Approving Regulatory Agency</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0793](v2/0793/index.html)</td><td>Ruling Act</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0806](v2/0806/index.html)</td><td>Sterilization Type</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0818](v2/0818/index.html)</td><td>Package</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0868](v2/0868/index.html)</td><td>Telecommunication Expiration Reason</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0871](v2/0871/index.html)</td><td>Supply Risk Codes</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0881](v2/0881/index.html)</td><td>Role Executing Physician</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0882](v2/0882/index.html)</td><td>Medical Role Executing Physician</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0894](v2/0894/index.html)</td><td>Side of body</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0895](v2/0895/index.html)</td><td>Present On Admission (POA) Indicator</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0904](v2/0904/index.html)</td><td>Security Check Scheme</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0905](v2/0905/index.html)</td><td>Shipment Status</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0906](v2/0906/index.html)</td><td>ActPriority</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0907](v2/0907/index.html)</td><td>Confidentiality</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0909](v2/0909/index.html)</td><td>Patient Results Release Categorization Scheme</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0910](v2/0910/index.html)</td><td>Acquisition Modality</td><td/></tr>
 <tr><td>[http://hl7.org/fhir/v2/0912](v2/0912/index.html)</td><td>Participation</td><td/></tr>
</table>

