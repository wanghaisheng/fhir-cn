title: 
date: 
categories: doc
---		

  [首页](../home/index.html) >[文档](documentation.html) > **简介**	
##1.8  FHIR概述

欢迎使用FHIR标准，它是卫生保健信息电子化交换的一种标准。这部分是对标准的概述，为初次接触的读者能改更快上手，提供了一个road map   
###1.8.1  背景  
医疗保健记录越来越多的被数字化。当病人在整个医疗系统中转诊的时候，要求他们的病历能够可及、可发现和可理解。更深层次的，能够支撑自动化地临床决策支持呢其他机器处理，要求数据是结构化的 并且是标准化的。(参考[卫生保健所面临的数字化挑战](change.html))

[HL7](http://hl7.org/)在过去20多年里，一直致力于构建卫生保健数据交换和信息模型标准来解决这些难题。FHIR是一种新标准，采用了新兴的行业方法，但是借鉴了在定义和实现HL7V2，V3,RIM和CDA标准过程中所获得成功、失败的教训。FHIR可以单独作为数据交换标准来使用，也可以和其他广泛应用的标准一起来使用(参考[FHIR与其他HL7标准的比较](comparison.html))   

FHIR旨在不牺牲信息完整性的前提下简化实现。它利用了现有的逻辑和理论模型，为不同的应用程序间交换数据提供了一种一致的、易于实现的、健壮的机制。FHIR的内在机制使得其能够追溯到HL7 RIM和其他内容模型，这就保证了与HL7之前定义的模式，最佳实践间的保持一致，毋须开发人员充分了解RIM和HL7 V3的其他衍生制品。(参考[FHIR与其他HL7标准的比较](comparison.html))    

###1.8.2  组件  
FHIR中最基本的组件是[资源](resources.html)  .所有可交换的内容都被定义成一个个资源。所有资源都拥有如下特征：  
* 同一种[定义](resources.html)、[表达](formats.html)它们以及从[数据类型](datatypes.html)(最基本的可重用元素)构建它们的方式    
* 同样的[元数据](resources.html#metadata)集合   
* [供人可读的部分](narrative.html)   
###1.8.3  方法   
####1.8.3.1  信息建模的方法   
FHIR的理念在于定义一个资源的基础集合，要么利用它们，要么相互结合来满足大多数常见的应用场景的需求。FHIR资源旨在定义绝大多数实现中通用的核心信息集合的信息内容和结构。如果需要的话，有内在的[扩展机制](extensibility.html)来满足剩下的需求。  
FHIR的建模采用了一种组合的方式。相比而言，HL7 V3建模是基于“model by constranit”(参考[FHIR与其他HL7标准的比较](comparison.html)) 。对于FHIR，特殊的应用场景通常是通过利用[资源引用](references.html)整合资源来实现的。尽管对于一个特定场景，单独一个资源可能是存在价值的，更多的是资源互相整合来满足特定的需求。用来描述资源如何整合使用的两类特殊资源：  
* [一致性声明](../infra/conformance.html)——描述一种实现中所暴露的交换数据的接口
* [规范profile](../infra/profile.html)——描述该实现中所使用的资源中定义的用以约束基数、可选性、术语、数据泪下和扩展的其他规则。

####1.8.4 标准
基本上，FHIR标准分为三大块：  
* 基本[文档](documentation.html)部分——描述了[资源是如何定义](resources.html)的，[数据类型](datatypes.html)、[编码](terminologies.html)的定义和[XML](xml.html) 、[JSON](json.html)格式的相关背景信息。  
* [实现部分](../impl/implementation)——描述在[REST](../impl/http.html) 、[消息](../impl/messaging.html)、[文档](../impl/documents.html)和[SOA](../impl/services.html)中使用资源。 
* [资源列表](resourcelist.html)——resourcelist.htmlFHIR中定义的所有资源的列表。其中又分为[临床](../clin/clinical.html)、 [行政管理](../admin/administration.html) 和[基础架构](../infra/infrastructure.html)三大类。 

资源有多种用途，从最基本的[诊疗方案](../clin/careplan.html)和[诊断报告](../clin/diagnosticreport.html)等临床内容到如[消息头](../infra/messageheader.html)、[一致性声明](../infra/conformance.html)等基础架构。虽然它们具有共同的技术特性，但却以完全不同的方式来使用。注意毋须为了使用资源而必须使用REST。 

###1.8.5 如何入门
最好是快速阅读一下 [资源列表](resourcelist.html)，对已经有了哪些资源有个感性认识，然后看一下[患者](../clin/patient.html)的定义来看看资源的定义是什么样的，接着读一下以下介绍背景信息的章节：
*  [资源](resources.html)——资源是如何定义的  
*  所有资源都有的[叙述性文本](narrative.html)，以及[资源之间如何互相引用](references.html)   
*  [格式](formats.html)：[XML](xml.html) 、[JSON](json.html)
*  [扩展相关](extensibility.html)——标准能够保持简单的关键
*  如果你之前了解HL7标准(V2 V3 CDA)的话，[FHIR与其他HL7标准的比较](comparison.html)也值得一看。 
#### 1.8.5.1 顶部标签
整个标准中都会看到这些标签，很多读者可能会遗漏：

![](../material/header-tabs.png)  
[资源](resources.html)和[数据类型](datatypes.html)都是以一种类似XML的 易于阅读的方式来呈现的，它们也有详细描述内容的正规定义。另外，大多数资源映射到很多不同的格式，如HL7V2，HL7V3 RIM ，CDA，DICOM等。同时，所有资源至少包含一个实例(有时候会有更多)，适当的时候，也会有描述它们如何在特殊情况下使用的profile规范。最后，一些资源包含了 帮助开发人员理解它们背后的设计原理的小贴士/备注。  
### 1.8.6 Style conventions
文档中使用了一些风格约定：
>This document uses some simple style conventions: this content represents information that may go over the wire this is the name of a data element    

### 1.8.7 寻求额外信息和提供反馈   
为了能够让更多读者看懂的同时，FHIR标准是面向开发人员社区的——这些真正利用标准编写程序的人。为了满足开发人员社区的需求，编辑人员力求标准行文精确，减少在编写程序之前的阅读时间(然而这份标准并不如我们所想的那么简明扼要，有时候是医疗保健和现实世界的复杂度所致)。鉴于此，在开发过程中并不必要的信息，诸如原理、备选方案、一些争论点和将来的计划等并没有包含在标准里面。同样，开发人员时不时会发遇到标准不明晰或者不完整的清空。最终，会有一些情况，标准可能是错的，或者是对其进行修订以更好的满足开发人员的需求。  
因此HL7提供了多种方法，通过这些方法可以维护和获取一些额外的FHIR相关信息，能够提供一些帮助，响应一些变更请求。  

####1.8.7.1 评论  
在每页地步，都包含一个评论的章节，可以就特定章节进行提问和讨论。评论由FHIRBb编辑人员和HL7工作组来监管，每个问题都会在一定的时间内给予答复。This content will occasionally be currated to ensure ongoing relevance, particularly if the specification is subsequently updated to eliminate confusion that may have spawned an initial comment.   
####1.8.7.2  FHIR Wiki  
FHIR项目团队维护着一个[wiki](http://wiki.hl7.org/index.php?title=FHIR)，记录了开发过程、方法学和设计决策。开发人员和其他人员也可以参与到wiki中来，提供一些暂未出现在标准中的指导和补充信息。注意 FHIR wiki上的内容不具有权威性，与FHIR标准的一致性无关。同样，一些内容可能也没有和最近的FHIR版本保持一致。 
FHIR标准中的每个页面在wiki中都有一页内容。用以记录原理、决策点和其他与开发人员无关的信息。额外的页面包括[FHIR方法论](http://wiki.hl7.org/index.php?title=FHIR_Development_Process)、[FHIR设计工具的使用](http://wiki.hl7.org/index.php?title=FHIR_Guide_to_Authoring_Resources)等。要研究wiki的话，建议从[根页面](http://wiki.hl7.org/index.php?title=FHIR)开始.   

####1.8.7.3 正式变更请求   

正式请求可以在[这里]()提交。对应的工作组会审核这些请求，并作出是否将其纳入到标准中的决策，其中包括了纳入到那个版本。 
####1.8.7.3 源码/参与机制的额外信息   
除了上述机制，HL7提供了一个 Stack Overflow 的标签，邮件列表和skype聊天频道来提供对开发人员各个层面的全方位的支持。如何使用这些请参考[指令](http://wiki.hl7.org/index.php?title=FHIR#More_help_and_Asking_Questions)

&copy; HL7.org 2011 - 2014. FHIR DSTU (v0.2.1-2606)构建于2014  7月2号 16:29+0800 星期三 . 
链接：[试行版是什么](http://hl7.org/implement/standards/fhir/dstu.htmll) |[版本更新情况](http://hl7.org/implement/standards/fhir/history.htmll) | [许可协议](http://hl7.org/implement/standards/fhir/license.htmll) |[提交变更建议](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemAdd&tracker_id=677) 	