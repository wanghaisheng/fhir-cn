title: 
date: 
categories: doc
---

  [首页](../home/index.html) >[文档](documentation.html) >[比较](comparison.html) > **其他标准**	


 [比较](comparison.html) >[V2消息](comparison-v2.html)> [V3](comparison-v3.html)>[CDA](comparison-cda.html) >**其他** 
###  1.10.4 其他HL7标准  

HL7发行了大量与上述所列与FHIR不存在重叠的其他标准，主要是因为它们不仅仅关注的是信息的交换。然而，我们大体上提一下： 

####   1.10.4.1 EHR功能模型(EHR-FM)    

这份标准为电子健康档案系统的功能富IFA你。FHIR是一种信息交换的标准，可以满足其中一些系统功能。如何在EHR-FM中使用FHIR [见此](ehr-fm.html)    

####   1.10.4.2 语境管理标准Context Management Specifications (CCOW)     

CCOW 是一种在单个工作站上独立的系统间同步语境的标准，为工作站的用户提供了一种无缝接口(比如，确保统一的用户认证，同一病人的展示，同一医嘱的展示等)。理论上，FHIR资源可以替代CCOW实现技术，然而这样做的业务场景并不明确。CCOW规范包含了与V2的映射。在建立CCOW与基于FHIR的系统间的链接时，这些映射可以用来确定相对应的FHIR数据元素。 

#### 1.10.4.3 Arden Syntax    

Arden Syntax是定义临床决策支持规则的一种语言。这些规则根据临床决策过程中所用的一部分数据元素来做推理，然而，标准本身并没有定义这些数据元素如何标识。FHIR元素和扩展标识符能改为标识相关数据元素提供一种机制。   

####  1.10.4.4  虚拟医疗记录/Virtual Medical Record

 Virtual Medical Record是由HL7还在开发的一种标准草案，也是围绕着临床决策支持领域。它定义了临床决策支持规则所对应的逻辑医疗记录。目前，这个模型是由VMR构建的一种自定义模型。然而，决策支持工作组正在评估在后续版本中使用FHIR作为数据结构的可能性。        
 

&copy; HL7.org 2011+. FHIR DSTU (v0.4.0-3900) 构建于2014  12月20号 2014 22:38+0000 星期六 . 
  链接：[试行版是什么](http://hl7.org/implement/standards/fhir/dstu.html) |[版本更新情况](http://hl7.org/implement/standards/fhir/history.html) | [许可协议](http://hl7.org/implement/standards/fhir/license.html) |[提交变更建议](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemAdd&tracker_id=677)