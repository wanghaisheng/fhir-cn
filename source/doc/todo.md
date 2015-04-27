title: 
date: 
categories: doc
---

  [首页](../home/index.html) >[文档](documentation.html) > **尚待解决的问题**	



<a name="todo"> </a>

## 1.5 Open Issues

在试用期间根据实现的经验教训来说，提出了大量的尚待解决的问题:

*   [Immunization](): 到底应该拆分成一个独立的[资源](immunization.html)还是看做对[用药的profile](medicationadministration-immunization.html)
*   [Conformance](profiling.html#dstu): 系统中该如何使用profile
*   [Resource Identification](managing.html#dstu): 分布式系统中如何管理资源的标识    
*   [Search](search.html#dstu): 如何标准化对文本的检索?
*   [Search](search.html#dstu-2): _include参数标准化的程度应该是怎么样的?
*   [Security Labels](security-labels.html#dstu): 到底应该确定哪些策略，这些策略对标准本身有哪些影响?
*   [Security](security.html#dstu): 数字签名的应用场景有哪些?
*   [ClinicalImpression](clinicalimpression.html):与之相关的内容和工作里粗粗的问题     
*   [Care Team](careplan.html#dstu):与之相关的内容和工作里粗粗的问题     
*   [Data Element](dataelement.html):  specificity相关的问题   
*   [Risk Assessment](riskassessment.html):     
*   [Messaging](messaging.html#dstu): 消息框架并没有[](medicationadministration-immunization.html)在connectathon中演示过，欢迎一切意见
*   [BodySite](bodysite.html#dstu):到底是单独作为一个资源还是作为一个可复用的类型       

另外， 还有很多与申请/执行(医嘱及医嘱的反馈，与申请相关的工作流程、状态等)问题没有解决。

### 1.5.1  留待后续版本解决的问题
*   不良反应的上报       
*	alarm资源用于表示患者当前存在的问题      
*	Concern Tracking     
*	Clinical Studies and Protocols         
*	Aggregated Data Reporting including Public Health Reporting        
*	Payment related resources, and specifically, an Account resource for payment tracking      
*	One or more resources for Advance Care Directive / Power of Attorney      
*	Use of RDF       
*	A full server side query framework       

&copy; © HL7.org 2011+. FHIR DSTU (v0.5.0-5149) generated on Fri, Apr 3, 2015 14:36+1100\.  
  链接：[试行版是什么](http://hl7.org/implement/standards/fhir/dstu.html) |[版本更新情况](http://hl7.org/implement/standards/fhir/history.html) | [许可协议](http://hl7.org/implement/standards/fhir/license.html) |[提交变更建议](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemAdd&tracker_id=677)