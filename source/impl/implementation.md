title: implementation
date: 2014-05-20 15:13:12
categories: impl
---


## <span class="sectioncount">2.0<a name="2.0"> </a></span> Implementation

<table width="100%">
 <tr>
 <td>

**Exchange Frameworks**

Define how Resources are exchanged.

*   [**RESTful API (HTTP)**](http.html)
*   [Search / Query](search.html)
*   [Documents](documents.html)
*   [Messaging](messaging.html)
*   [Services (SOA)](services.html)
</td><td style="border-left: 1px solid #eeeeee">

**Support**

Implementation Support.

*   [Downloads - Schemas, Code, Tools](downloads.html)
*   [Managing Resource Identity](managing.html)
*   [Push vs Pull](pushpull.html)
*   [Support Links](support.html)
</td><td style="border-left: 1px solid #eeeeee">

**Using FHIR**

Making use of FHIR.

*   [Common Use Cases](usecases.html)
*   [Profiles Defined as part of FHIR](profilelist.html)
*   [Security](security.html) &amp;  [Security Labels](security-labels.html)
*   [Integrated Examples](integrated-examples.html)
</td></tr></table>

### <span class="sectioncount">2.0.1<a name="2.0.1"> </a></span> Implementers Safety Check List

FHIR is as simple to implement as we know how to make it. However, due to the nature of 
healthcare, and healthcare processes, and cultural concerns, there are a number of features in
FHIR that implementers are obliged to consider in order to implement safe systems.

This section is a check list to help implementers be sure that they've considered all the parts
of FHIR that impact on their system design with regard to safety. 

1.  <input type="checkbox"/> Production exchange of patient or other sensitive data will always use some form of [encryption on the wire](security.html#http)
2.  <input type="checkbox"/> For each resource that my system handles, I've reviewed the [Modifier elements](conformance-rules.html#isModifier)
3.  <input type="checkbox"/> My system checks for [modifierExtension](extensibility.html#modifierExtension) elements
4.  <input type="checkbox"/> My system supports [elements labelled as &quot;must-support&quot;](conformance-rules.html#mustSupport) in the [Profiles](profile.html) that apply to my system
5.  <input type="checkbox"/> My system can [render narratives properly](narrative.html#css) (if/when they are used)
6.  <input type="checkbox"/> My system has documented how [distributed resource identification](managing.html#distributed) works in it's relevant contexts of use
7.  <input type="checkbox"/> My system uses the right [security labels](security-labels.html#core) where appropriate
8.  <input type="checkbox"/> When other systems [return http errors from the RESTful API](http.html#summary) or from the [Mailbox](messaging.html#mailbox) (perhaps using [Operation Outcome](operationoutcome.html)), my system checks for them and handles them appropriately
9.  <input type="checkbox"/> My system publishes a [conformance statement](conformance.html) so other implementers know what it does 

Obviously this list is only a small part of the overall safety check list for an application, which will have checks regarding jurisdictionally mandated policies, internal integrity, etc.

</div>

				</div>  <!-- /inner-wrapper -->
            </div>  <!-- /row -->
        </div>  <!-- /container -->

    </div>  <!-- /segment-content -->