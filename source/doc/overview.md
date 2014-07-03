title: overview
date: 2014-05-20 15:13:12
categories: doc
---		


<a name="root"> </a>

## 概述 <span class="sectioncount">1.7<a name="1.7"> </a></span>

FHIR定义了在医疗卫生过程中为了进行信息交换所用到的资源
Resources是:

*   原子的-操作的最小单元 自己有自己的事务的范围。
*   互联的-资源引用其他资源 保证了信息的模块化复用
*   独立的-无需获取所引用的资源即可对资源的内容进行处理
*   简单的-每个资源定义易于理解 易于实现，无需特殊工具或基础架构
*   RESTful - 可以在restful交换语境下使用资源
*   灵活的-也可在非restful语境下使用资源，诸如消息或SOA架构，可以很方便的从RESTFUL的方式转换
*   可扩展的-在不影响互操作性的前提下可以根据本地需求对资源进行扩展
*   面向web的-在合适的场合，使用开放的互联网标准来表达数据
*   免费使用-FHIR标准本身是开放的-任何人都可以实现FHIR或者在不受任何知识产权限制的情况下衍生出相关标准

除了一些最基础的资源以外，FHIR也定义了一个可以支撑在Restful环境、传统消息交换、以人为核心的临床文档和企业级SOA架构中使用这些资源的轻量级的实现框架。每种方法都有各自的优势-FHIR所提供的基础实现使得可以灵活选择其中一种，企业可以按照自己的方式 无需放弃与其他方式之间的互操作性 .

尽管资源很简单  也易于理解，它们是通过完善的、全面的需求整理和正式的建模过程得到的，这样就保证了资源需求的内容的可靠性和稳定性。资源内容使用机器可处理的语言对应到严谨的基础本体和模型中，保证了可以使用计算机分析和转换资源定义和内容。

同样的FHIR也提供了一个基础符合性框架和工具以保证不同的实现语境和企业能够用一种统一的计算机可处理的方式来描述他们的语境和用到的资源，使用符合性框架和定义框架来提高计算机间的互操作性 。

资源和3种支撑层(实现框架、完整性定义和符合性工具)的组合 同时完全免费使用，使得FHIR可以在需要的地方得到使用(跨医院的系统、移动医疗应用、云存储和国家级的卫生信息仓库、研究型数据库等等)，无需在整个过程中经过格式和语义的互相转换。

<a name="roadmap"> </a>

### 该标准的路线图 <span class="sectioncount">1.7.1<a name="1.7.1"> </a></span>

该标准分为三部分: 背景性文档,实现相关知识和资源的定义. 

#### 文档 <span class="sectioncount">1.7.1.1<a name="1.7.1.1"> </a></span>

 [文档](documentation.htm) 这部分提供了使用和理解资源所需的基础材料：

*   证书、授权、版本历史和重要的问题列表
*   一般入门指导信息(包括本网页)
*   如何定义资源以及相关的信息
*   所有资源中使用到的通用数据类型的定义
*   如何使用编码和字典以及编码注册的信息

#### 实现 <span class="sectioncount">1.7.1.2<a name="1.7.1.2"> </a></span>

 [实现](implementation.htm) 这部分解释了如何在各种语境下使用资源：

*   交换框架：REST API、消息和文档交换
*   查询/搜索基础架构：最重要的搜索/查询结构
*   实现相关材料的下载：schema、代码、实例
*   实现相关信息：包括通用的业务场景
*   安全相关备注

#### Resources <span class="sectioncount">1.7.1.3<a name="1.7.1.3"> </a></span>

 [resources 这部分](resourcelist.htm) 枚举和描述了这些资源
为了导航方便起见，总共分为3类资源:

*   [临床资源Clinical resources](clinical.htm): 集中在记录了病人相关信息的临床记录Clinical Record keeping focused on patient related information
*   [管理资源Administrative resources](administration.htm): 医疗卫生中涉及的实体：患者、医务人员、设备和工作流信息包括随访和医嘱管理*   [基础架构资源Infrastructural resources](infrastructure.htm):包括支持交换、审计和一致性管理的资源

每种资源都有如下界面：

*   **内容**: 介绍资源的上下文(语境)，利用XML格式来定义它的内容，提供一些额外的描述。也提供了诸如W3C Schema和其他方式的正规定义。同时也描述了与该资源相关的查询条件和事件。
*   **范例**: 提供一或多个范例来展示如何使用资源。
*   **正规定义**:资源中每个元素的完整的正规定义的表格，也有与其他标准和本体的对应。

  <!--*   **Design Notes**: Explanations of some of the less obvious aspects of the resource and explanation of why the resource is structured in a particular way. Not all resources have design notes and implementers do not need to read them
 -->*   **规范Profiles**: 作为标准的一部分，提供了资源的规范列表。提供规范可能是为了阐述某方面使用资源的问题或者某个资源的某种特定用途是需要一个标准化的规范的。
