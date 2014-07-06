title: 
date: 
categories: doc
---

  [首页](../home/index.html) >[文档](documentation.html) >>[比较](comparison.html) > **V2消息**	


 [比较](comparison.html) **V2消息** >[V3消息](comparison-v3.html) > [CDA](comparison-cda.html) > [其他](comparison-other.html) 

###1.9.1  HL7 Version 2


HL7 version 2 (V2) 是HL7第一部信息交换标准，也是其中应用最广，在住院部最出名的一部，尽管也有用在其他一些场合。 HL7 V2 使用由可复用的区段构建的消息来实现收发系统的信息通信和触发特定的行(转诊/转科、实验室检验申请等)。同时也支持通过通知实现单向通信以支持查询和其他工作流。  

####1.9.1.1 V2 异同  

**事件驱动:** FHIR和V2一样支持事件驱动的消息模式(与V2不同的在于FHIR还支持其他诸如文档、REST和其他服务模型)。参考[Message Header](../infra/messageheader.html) 资源.

**粒度:** HL7 V2中的 &quot;Segment&quot; 结构与FHIR中的[resources](resources.html)类似，都是可复用的数据块.  然而，V2的区段无法单独操作。另外，不是所有的区段都有FHIR资源独立标识的特征。由于在扩展上范围和方法的差异，V2区段和数据类型常常和数据元混杂在一起，大多数开发中都无法重用和理解。  

Segments/区段可以组合成 可重复的/或者可选的集合，称之为"组"，来表达所有的业务对象。例如， OMP (药房/治疗医嘱消息)中的 &quot;医嘱&quot;部分包含:   

*    ORC区段，针对的是医嘱相关的工作流方面的数据   
*    RXO 区段，针对的是医嘱相关的药房方面的数据    
*   可选的TQ1 和 TQ2 区块 描述医嘱的时间   
*   可选的 NTE 区段，针对的是医嘱的渲染和其他额外信息    
*   可选的 RXR 区块描述路径信息
*   等等.  

 V2中针对粒度的方法强调的是对&quot;信息模式&quot;的复用 .比如，时间和路径信息单独没有意义，但是在很多时候是有价值的。由于三层嵌套的限制，也需要单独的区块，否则嵌套的层次就太深了。FHIR针对复用性采用了不同的方法，关注的是可以独立维护管理的对象。 [MedicationPrescription](../clin/medicationprescription.html) 资源 中包含了上述的所有方面，除了ORC中一些针对工作流的内容，则是由 [Order](..clin/order.html) 资源来处理.   [MedicationPrescription](../clin/medicationprescription.html) 资源本身很复杂，包含了用法和配发的嵌套结构等等，这些本身就不是简单的数据类型。  
 
**扩展性:** HL7 V2 中扩展机制是通过使用&quot;Z-segments&quot;实现的.    
在没有发送方事先的人为解释之前这些扩展的含义是不透明的。扩展本应是仅限于那些不会影响标准区段含义的数据项。 
另一方面，FHIR中的 [扩展](extensibility.html)上可以出现在任意的层次上(包括数据类型内部)。  [ModifierExtensions](extensibility.html#modifierExtension) 可能用在扩展会改变其他元素数据含义的情况下 (比如  引入记录的逆指标).  最后，FHIR扩展的含义是通过定义扩展的URI来确定 .  这种URI的方式也确保了不同系统定义的扩展不会冲突(Z-区段就存在这类问题)    

**版本内的兼容性:** 对于维护向前向后的兼容性，HL7 version 2有严格的流程。只有在现有字段、组件的末尾才能新增内容。应用程序应忽略意外内容或重复。FHIR中也有类似的兼容性规则。一个元素在FHIR实例中的路径在以后的版本中将不会变化，在试行版过程中会开发针对新增元素的一些特殊规则(如忽略，核对是否有“必须理解”的标记)

**人可读性:** 一般而言，HL7 V2实例不提供交换内容的人可读的版本。而一些系统可能会使用NTE区段来提供人可读的整个消息或部分消息内容，这些规则因机构而异。FHIR要每个资源都要有人可读的部分。  

**更新机制:** HL7 V2数据一般是以 &quot;snapshot&quot; 模式来交换的——通过传输一份完整的赋值后的数据实例来实现更新，然而，V2中的一些区段和消息支持更复杂的交换，只有当已经发送了交换的消息之后，用一些编码或特殊值来标识这类交换已经发生了(诸如添加地址、移除姓名)。FHIR中只支持snapshot模式，而 [ModifierExtensions](extensibility.html#modifierExtension) 的使用可能会引入与V2类似的内容，这样做会带来互操作性的问题，会使得资源脱离了消息的范式难以利用    

**可选性 &amp; 规范:**  在国际标准的层面上，HL7 V2 和 FHIR都提供了相同程度上的灵活度 ，大多数数据元素是可选的，然而有两点不同。
FHIR资源中对于哪些元素要包含在核心表中有更多限制——只有大多数系统支持的这类数据元。HL7 V2倾向于包含哪些旨在很少场景下会用到的数据元。FHIR 利用扩展来处理这些情况。V2和FHIR都提供了正式的机制来定义规范，也就是如何来使用标准的建议。 然而 V2的机制并没有得到广泛应用 .  FHIR [规范](../infra/profile.html)是方法论的一个基本组件，内置在工具包里，提高了应用的可能性。  

#### 1.9.1.2  V2 Interoperability Considerations

**Mapping:** One of the biggest challenges with HL7 V2 interoperability is the variation of implementation.  
Even when identical scenarios are being handled in similar business environments, the data elements supported 
can vary and even the place where a given data element is placed in an instance can vary.  As a result, defining 
consistent mapping rules between V2 and FHIR at an international or even regional level is not terribly realistic.  
The FHIR mappings provided give a starting point for consideration, but mappings will generally need to be done 
on an implementation by implementation basis.

**Extensions:**<a name="V2-extensions"> </a>While some V2 elements will map to FHIR core, a large percentage 
will not.  Where a V2 element is not supported by core, an extension will be needed to share the information.  
Where there is interest, HL7 may choose to publish and maintain extensions for V2 elements that are not supported 
as part of the core FHIR specification.  The FHIR extension registry   <!-- Todo: Link --> should be searched prior 
to defining local extensions.  If time permits, the relevant HL7 WG should be contacted with a request to define 
additional V2 extensions if needed ones are not present.  If time does not permit, applications can define their 
own extensions, but should have a migration plan for if/when HL7 defines it later.  For Z-segments, URIs should 
be defined to be specific to the system/environment that defined the Z-segment (e.g. http://acme.org/fhir/extensions/consent), 
not based on the name of the Z-segment itself (given that Z-segments with the same name but different meaning may 
exist) (e.g. http://hl7.org/ZAC).

**Resource identification:**<a name="V2-identification"> </a>V2 messages will often reference objects that 
have already been referred to in previous messages.  When converting the messages to FHIR, these references 
will need to point to the same resource URI.  Given that not all V2 message objects have identifiers in the 
message, this can be somewhat problematic.  An approach to handling this issue exists for FHIR [transactions](http.html#transaction).  
However, the ramifications of using this approach in a messaging environment have not yet been resolved.  
Implementers will need to explore their own strategies as part of early adoption.

**Merging references and resources:**<a name="V2-merging"> </a> V2 message instances may well reference the 
same &quot;object&quot; numerous times.  For example, a message containing a patient's medication history is likely to 
include references to the same clinicians and clinics/hospitals many times.  While in some cases, the data 
captured for a given object might be identical in all uses, in other cases the information might vary.  For 
example, the sending system might convey historical phone numbers for old records and current phone numbers 
for newer records.  Alternatively, the message design might allow expression of different amounts of detail 
in different portions of the message or the sending application might simply be designed to convey different 
amounts of detail in different portions of the message (e.g. conveying phone number for an ordering clinician, 
but not for a data-entry clinician).  When converting to FHIR, all references to the same &quot;object&quot; will generally 
have a single resource identifier and be referenced only once in the instance - with the complete set of 
information needed/available.  This creates two challenges:

1.  _How does the conversion software recognize when two portions of a message are referencing the same  object?_  While some references may have unique identifiers or names that are sufficient to confirm &quot;same object&quot;,  others may not - though some other combination of attributes may be sufficient.  The specific rules will need to  be determined by the implementer performing the conversion
2.  _If multiple versions of data are present, what set of data should be used - or should multiple versions  be sent with distinct history ids?  (And if the latter, what is the 'order' of the versions?_  If the order  of the versions can be determined by data in the message (e.g. assuming older order dates have &quot;older&quot;  demographics), dates can be specified on the entry _updated_ element to indicate relative ordering.  If the ordering can't be determined, it will be difficult to merge the data into a single resource or  represent it using multiple resources.

**Identified vs. Contained resources:**<a name="V2-contained"> </a> Each HL7 V2 message will map to 
multiple resource instances - often 10s or even 100s of resource instances.  To maintain consistency 
with the V2 messaging paradigm, all resource data will typically be sent over the wire as part of the 
FHIR message rather than being sent by reference as would be typical in a RESTful implementation.  
However, FHIR provides two different ways of communicating the resources as part of the message [bundle](extras.html#bundle): 
they can either be sent as &quot;fully identified&quot; resources (direct entries in the atom feed with their 
own identity, and able to be the subject of independent transactions), or they can be sent as [contained](references.html#contained) 
resources, meaning they are only identified relative to another resources and cannot be retrieved or 
otherwise manipulated on their own.  A V2 to FHIR conversion process will need to make the determination 
of what data elements are or must be present, for a resource to be fully identified.  In some cases, the 
determination will be done at the time of mapping.  In other cases, it may depend on the content of a 
particular instance. As an example, an XCN containing just a name (`|^Smith^John|`) doesn't 
contain enough information to identify the physician from any other John Smith, so will need to be 
contained resource, whereas an XCN of `|12345^Smith^John|` generally does, though the conversion 
process will need to be aware of the scope and management processes around the identifier.

**Generating human-readable content:**<a name="V2-humanReadable"> </a> FHIR requires that every 
resource have a human readable [narrative](narrative.html) that contains all information 
relevant to human decision-making.  When converting from V2, developers (likely with guidance from 
clinicians) will need to determine what information from the message should be rendered and how
to generate this content.

**Nulls and update modes:**<a name="V2-updateMode"> </a>In HL7 V2, &quot;action&quot; codes can determine 
whether particular segments represent information to be added, updated or deleted.  Fields can be 
populated with &quot;null&quot; (two consecutive double-quotes with no other characters) to note a field is 
to be deleted.  An omitted element or repetition is generally interpreted as &quot;retain existing data 
unchanged&quot;.  This contrasts with the FHIR approach of requiring all data to be present as a snapshot.  
Systems will either need to build in logic to generate a full snapshot of each resource or will need 
to introduce modifier extensions to allow similar behavior to V2.

</div>

 &copy; HL7.org 2011 - 2014. FHIR DSTU (v0.2.1-2606)构建于2014  7月2号 16:29+0800 星期三 . 
链接：[试行版是什么](http://hl7.org/implement/standards/fhir/dstu.htmll) |[版本更新情况](http://hl7.org/implement/standards/fhir/history.htmll) | [许可协议](http://hl7.org/implement/standards/fhir/license.htmll) |[提交变更建议](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemAdd&tracker_id=677) 	 		