title: 
date:  
categories: impl
---

  [首页](../home/index.html) > **实现**	

##  2.0  实现


### **交换模式/交换框架**

定义资源如何交换.

*   [**RESTful API (HTTP)**](http.html)       
*   [Search](search.html)         
*   [Operations](operations.html)         
*   [Documents](documents.html)       
*   [Messaging](messaging.html)       
*   [Services (SOA)](services.html)      

### **帮助**

实现中的帮助.

*   [Downloads - Schemas, Code, Tools](downloads.html)
*   [Managing Resource Identity](managing.html)
*   [Push vs Pull](pushpull.html)
*   [Create and Update Behavior](updates.html)
*   [Support Links](support.html)
*   [Integrated Examples](integrated-examples.html)
*   [Security](security.html) &amp;  [Security Labels](security-labels.html)

### **FHIR 规范和实施指南Profiles &amp; Implementation Guides**

根据特定用途对FHIR进行本地化.

*   [Profiling FHIR](profiling.html)
*   [Implementation Guides](iglist.html)
*   [Profiles Defined as part of FHIR](profilelist.html)
*   [Common Use Cases](usecases.html)

###  2.0.1  Implementers Safety Check List

FHIR is as simple to implement as we know how to make it. However, due to the nature of 
healthcare, and healthcare processes, and cultural concerns, there are a number of features in
FHIR that implementers are obliged to consider in order to implement safe systems.

This section is a check list to help implementers be sure that they've considered all the parts
of FHIR that impact on their system design with regard to safety. 

1.  <input type="checkbox"/> Production exchange of patient or other sensitive data will always use some form of [encryption on the wire](security.html#http)
2.  <input type="checkbox"/> For each resource that my system handles, I've reviewed the [Modifier elements](conformance-rules.html#isModifier)
3.  <input type="checkbox"/> My system checks for [modifierExtension](extensibility.html#modifierExtension) elements
4.  <input type="checkbox"/> My system supports [elements labelled as &quot;must-support&quot;](conformance-rules.html#mustSupport) in the [Profiles](profiling.html) that apply to my system
5.  <input type="checkbox"/> My system can [render narratives properly](narrative.html#css) (if/when they are used)
6.  <input type="checkbox"/> My system has documented how [distributed resource identification](managing.html#distributed) works in its relevant contexts of use
7.  <input type="checkbox"/> My system uses the right [security labels](security-labels.html#core) where appropriate
8.  <input type="checkbox"/> When other systems [return http errors from the RESTful API](http.html#summary) or from the [Mailbox](messaging.html#mailbox) (perhaps using [Operation Outcome](operationoutcome.html)), my system checks for them and handles them appropriately
9.  <input type="checkbox"/> My system publishes a [conformance statement](conformance.html) so other implementers know what it does 

Obviously this list is only a small part of the overall safety check list for an application, which will have checks regarding jurisdictionally mandated policies, internal integrity, etc.


 &copy; HL7.org 2011 - 2014. FHIR DSTU (v0.2.1-2606)构建于2014  7月2号 16:29+0800 星期三 . 
链接：[试行版是什么](http://hl7.org/implement/standards/fhir/dstu.html) |[版本更新情况](http://hl7.org/implement/standards/fhir/history.html) | [许可协议](http://hl7.org/implement/standards/fhir/license.html) |[提交变更建议](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemAdd&tracker_id=677) 	 		