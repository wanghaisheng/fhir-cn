title: 
date: 
categories: doc
---

  [首页](../home/index.html) >[文档](documentation.html) > **尚待解决的问题**	



<a name="todo"> </a>

## 1.7 Open Issues

在试用期间根据实现的经验教训来说，提出了大量的尚待解决的问题:

*   [Conformance](conformance.html#dstu): 如何在系统中使用profile规范
*   [Order](order.html#dstu): 需要定义一些其他类型的医嘱
*   [Resource Identification](managing.html#dstu): 分布式系统中如何管理资源的标识    
*   [Search](search.html#dstu): 如何标准化对文本的检索?
*   [Search](search.html#dstu-2): _include参数标准化的程度应该是怎么样的?
*   [Security Labels](security-labels.html#dstu): 到底应该确定哪些策略，这些策略对标准本身有哪些影响?
*   [Security](security.html#dstu): 数字签名的应用场景有哪些?
*   [Messaging](messaging.html#dstu): 消息框架并没有在connectathon中演示过，欢迎一切意见

I另外，以后想要添加如下新的资源类型:

*   A notification resource for creating and recording notifications between parties
*   An alarm resource to represent current issues with the patient
*   A person resource to support person registries
*   An appointment resource for making and tracking arrangements around the future of care
*   Payment related resources, and specifically, an Account resource for payment tracking
*   Possibly a way to define particular queries (finer detail than Profile provides)
*   One or more resources for Advance Care Directive / Power of Attorney

Note that other resources beyond these may be anticipated.

In addition to these, further work is planned around tracking and  reporting clinical observations / vital signs, and supporting   remote consultations / telehealth. 


&copy; HL7.org 2011+. FHIR DSTU (v0.4.0-3900) 构建于2014  12月20号 2014 22:38+0000 星期六 . 
  链接：[试行版是什么](http://hl7.org/implement/standards/fhir/dstu.html) |[版本更新情况](http://hl7.org/implement/standards/fhir/history.html) | [许可协议](http://hl7.org/implement/standards/fhir/license.html) |[提交变更建议](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemAdd&tracker_id=677)