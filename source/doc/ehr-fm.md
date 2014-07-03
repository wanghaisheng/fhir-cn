title: ehr-fm
date: 2014-05-20 15:13:12
categories: doc
---		


## HL7 EHR Functional Model HL7 EHR功能模型<span class="sectioncount">1.9<a name="1.9"> </a></span>

HL7EHR系统功能模型罗列了在EHR系统(电子病历/电子健康档案系统)中可能存在的功能的参考列表。而FHIR关注的是医疗中的信息交换，这主要发生在EHR之中。该表简要地描述了一种可以如何使用FHIR来满足EHR-FM中描述的需求的方式，旨在帮助读者理解如何使用FHIR。也有很多其他有效的方式来实现EHR-FM，使用FHIR。(The HL7 EHR System Functional Model provides a reference list of functions that may be present in an Electronic Health Record System. 
While FHIR is an implementation focused on exchange of information in healthcare, this often happens in the context of an EHR. 
This table briefly describes one way that FHIR can be used to meet the requirements described in the EHR-FM and is provided to help
readers of the FHIR specification understand how FHIR can be used. There are many other equally valid ways to implement the EHR-FM
and to make use of FHIR. )

<table class="list">
<tr><th colspan="2">EHR功能</th><th>FHIR 实现说明</th></tr>
<tr><td>IN.1</td><td>安全/Security</td><td>FHIR定义了一部分安全架构，把其他部分交给标准的web安全协议框架。(FHIR defines parts of the security infrastructure, and delegates others to standard web based security frameworks)</td></tr>
<tr><td>IN.1.1</td><td>实体认证/Entity Authentication</td><td>FHIR中假设用户是认证过的。OAuth是一种推荐的方法。(FHIR assumes that the users are authenticated. OAuth is the preferred mechanism)</td></tr>
<tr><td>IN.1.2</td><td>实体授权/Entity Authorization</td><td>目前FHIR中并没有描述或管理权限控制的一些资源。一般默认地使用诸如SAML等web框架。参考[安全章节](security.htm#binding)中对FHIR与SAML绑定的讨论 (FHIR doesn't currently provide any resources to describe or manage access-control permissions. 
By default, underlying web frameworks such as SAML would be used. See) [the security section](security.htm#binding) for a discussion of binding between FHIR and SAML</td></tr>
<tr><td>IN.1.3</td><td>实体权限控制/Entity Access Control</td><td>参考上面关于SAML/OAuth的部分(See above about SAML / OAuth)</td></tr>
<tr><td>IN.1.4</td><td>患者访问管理/Patient Access Management</td><td>暂时FHIR中还没有与此相关的功能(FHIR does not - yet? - include functionality related to this requirement)</td></tr>
<tr><td>IN.1.5</td><td>抗抵赖/Non-Repudiation</td><td>[provenance资源](provenance.htm)记录了与资源相关的时间戳、系统角色和数字签名(The [provenance resource](provenance.htm) tracks the timestamps, actors, digital signatures associated with resources)</td></tr>
<tr><td>IN.1.6</td><td>安全的数据交换/Secure Data Exchange</td><td>应当在所有生产环境下的数据交换中使用TLS(https:).所有遵循FHIR Restful风格的实现必须能够使用https。(TLS (https:) should be used for all production exchange of data. All conformant FHIR RESTful implementations must be able to use https)</td></tr>
<tr><td>IN.1.7</td><td>安全的数据路由/Secure Data Routing</td><td>FHIR支持代理和其他能够保证消息目的地和传输的形式。参考下面的IN.2.2(FHIR allows for brokers and various forms of messaging that support assured destinations and delivery (also see IN.2.2 below))</td></tr>
<tr><td>IN.1.8</td><td>信息认证/Information Attestation</td><td>参考[provenance资源](provenance.htm)</td></tr>
<tr><td>IN.1.9</td><td>病人隐私和保密性/Patient Privacy and Confidentiality</td><td>FHIR中并未包含此类需求相关的功能，当然可以在具体实现中提供此类功能(FHIR does not include functionality related to this requirement, though implementations would be expected to provide this)</td></tr>
<tr><td>IN.2</td><td>健康档案信息和管理/Health Record Information and Management</td><td>这是FHIR标准的核心(This is the core focus of the FHIR specification)</td></tr>
<tr><td>IN.2.1</td><td>数据的保留、可及性和销毁/Data Retention, Availability and Destruction</td><td>Restful的FHIR服务器按照所有在一致性声明中的明确描述来提供对资源精确的细粒度的保留和可及性以及对资源的销毁。(A FHIR RESTful server gives precise and fine-grained control of retention, availability and destruction of resources, all clearly described by the conformance statement)</td></tr>
<tr><td>IN.2.2</td><td>审计记录/Auditable Records</td><td>FHIR 中的[SecurityEvent](securityevent.htm) 资源，可供审计记录使用</td></tr>
<tr><td>IN.2.3</td><td>同步/Synchronization</td><td>FHIR通过[Bundles](extras.htm#bundle) 使用标准的web发布/订阅的方法来支撑同步。基于Atom的发布/订阅可能是推模式 也可能是拉模式，可以包含某种类型的所有资源或者资源的特定子集。另外成组的资源可以用bundle来交换，保证了相关资源的同步性。(FHIR supports synchronization using standard web publication/subscription methods via [Bundles](extras.htm#bundle) (i.e. Atom feeds). Atom-based pub/sub may be push or pull based, and can include all resources of a particular type, or selected subsets of the resources. In addition, groups of resources can be exchanged in bundles, keeping a set of related resources in synchronization)</td></tr>
<tr><td>IN.2.4</td><td>健康档案信息的抽取/Extraction of Health Record Information</td><td>FHIR暂时未提供报表格式，但是有检索和获取功能来帮助构建这样的一些报表(FHIR does not provide report formats (yet?), but does provide extensive search and retrieval functions to assist with building such reports)s</td></tr>
<tr><td>IN.2.5</td><td>存储和管理健康档案信息/Store and Manage Health Record Information</td><td>Restful的FHIR服务器能够永久地存储和管理健康信息-更多信息参考下面内容(A FHIR RESTful server can store and manage health information persistently - see below for further information.) </td></tr>
<tr><td>IN.2.5.1/2</td><td>管理结构化和非结构化的健康档案信息/Manage Structured and Unstructured Health Record Information</td><td>FHIR资源的结构化数据和XHTML文本描述 双重内容能够无缝地支持结构化和非结构化信息的处理。(The dual contents of FHIR resources - structured data and XHTML narrative - provide seamless support for dealingsh  with a mix of structured and unstructured information)</td></tr>
<tr><td>IN.3</td><td>注册和目录服务/Registry and Directory Services</td><td> FHIR [管理资源 ](resourcelist.htm#administrative) 提供一种基于注册的对患者、医务人员等信息的访问(provide a registry based access to patients, providers, etc.)</td></tr>
<tr><td>IN.4</td><td>标准术语和术语服务/Standard Terminologies and Terminology Services</td><td>FHIR提倡尽可能的使用标准术语，通过多种术语相关的[数据类型](datatypes.htm)支持术语的使用。FHIR并未定义术语架构或者术语服务的架构，但是定义了[规范/Profile](profile.htm) 和 [值集/ValueSet](valueset.htm)来描述如何在FHIR中使用术语。 (encourages the use of standard terminologies wherever possible, and provides full support for their use through a variety of terminology related [data types](datatypes.htm). FHIR does not define a terminology infrastructure or service, but does define the [Profile](profile.htm) and [ValueSet](valueset.htm) resources to describe how terminology is used in a FHIR context)</td></tr>
<tr><td>IN.5</td><td>基于标准的互操作性/Standards-based Interoperability</td><td>FHIR是对基础互操作性标准的定义(FHIR is a definition of a standard on which to base interoperability)</td></tr>
<tr><td>IN.5.1</td><td>交换标准/Interchange Standards</td><td>这是FHIR的核心。参考下面交互模式的讨论。This is the core focus of FHIR. See below for discussion of interaction modes</td></tr>
<tr><td>IN.5.2</td><td>交换标准版本控制和维护/Interchange Standards Versioning and Maintenance </td><td>在[此描述了](resources.htm#version)FHIR的版本维护（FHIR version maintenance is [described here](resources.htm#version))</td></tr>
<tr><td>IN.5.3</td><td>基于标准的应用集成/Standards-based Application Integration</td><td>FHIR以一种易于理解、使用和调试的基于web的架构来实现简单的集成。在EHR使用同样的架构也能提供一种简单的方式实现信息交换。(FHIR enables simple integration through use of an easy to understand, use and debug web based infrastructure. The same framework used within an EHR for persistence can also offer a simple way to implement exchange)</td></tr>
<tr><td>IN.5.4</td><td>交换协议/Interchange Agreements</td><td>FHIR一致性声明和资源规范资源为单个的和基于社区的交易双方之间的协议提供了一种基于注册的架构(The FHIR Conformance Statement and Resource Profile resources provide a registry based infrastructure for individual trading partner agreements, as well as for community based ones)</td></tr>
<tr><td>IN.6</td><td>业务规则管理/Business Rules Management</td><td>目前FHIR中并未解决此类需求。FHIR does not address this requirement at this time</td></tr>
<tr><td>IN.7</td><td>工作流管理/Workflow Management</td><td>目前FHIR并未解决此类需求，尽管存在一些资源和服务支撑此功能。</td></tr>
</table>

EHR功能模型描述了很多系统间交互的模式。其中每一种都可以用FHIR以不同的方式实现。(The EHR functional model describes several modes for interaction between systems. Each of these can be implemented in several different ways using FHIR)

<table class="list">
<tr><th>交互模式</th><th>FHIR中的可选项</th></tr>
<tr><td>Unsolicited Notifications
如患者前来预约e.g. a patient has arrived for a clinic appointment </td><td>

*   通过http创建/更新一个新资源create/update new resource via http
*   使用atom推送资源push resources using atom
*   发送FHIR消息(Send FHIR [Message](message.htm) (if appropriate event is defined)</td></tr>
<tr><td>查询/响应Query/Response
e如系统中有没有Adam Everyman这人？有，MRN号码是12345678.</td><td>

*   使用变量搜索search with parameters
*   查询消息(暂未定义)A query message (though not defined yet)</td></tr>
<tr><td>服务申请和反馈/Service Request and Response
如空腹血糖实验室检验医嘱和检验结果的反馈e.g., Laboratory Order for Fasting Blood Sugar and a response containing the results of the test.  </td><td>消息和SOA都可以支持。Could be supported either through Messaging or SOA solutions.  Request/Response support is not yet defined</td></tr> 
<tr><td>机构间的信息交换如区域平台或国家平台Information Interchange between organizations (e.g. in a RHIO, or in a National Health System)  </td><td>

*   使用atom(push模式或pull模式)的发布/订阅pub/sub using atom (push or pull)
*   RESTful 接口
*   FHIR 消息</td></tr>
<tr><td>结构化/非结构化临床文档Structured / Unstructured clinical document, 如听写的手术记录e.g., dictated surgical note </td><td>参见[Documents](document.htm)</td></tr>
</table>

结合适当的安全和管理性的FHIR服务器 在使用 [SecurityEvent](securityevent.htm) and [Provenance](provenance.htm) 资源之后可以保证满足EHR-FM中定义的话核心的记录管理功能。

*   全生命周期记录，包括对来源、起源和作者信息以及视图和交换的记录。Lifespan/Lifecycle tracking, including capturing source, origination and authorship information, along with tracking of views and exchanges
*   信息完整性、准确性和数字签名的保障Attestation for accuracy and completeness, along with digital signature
*   所保留内容的完整的版本历史A full version history with content retention
*   数据保留和持久化Retention and persistence

其他如抗抵赖、权限控制和授权追踪相关的功能暂未在FHIR中定义。
Additional functionality not defined (yet?) in FHIR is required to ensure non-repudiation, access control, and consent tracking.

