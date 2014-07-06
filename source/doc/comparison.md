title: 
date: 
categories: doc
---

  [首页](../home/index.html) >[文档](documentation.html) > **比较**	


 **比较**  >[V2消息](comparison-v2.html) >[V3消息](comparison-v3.html) > [CDA](comparison-cda.html) > [其他](comparison-other.html) 

#1.9.0  附录: FHIR与其他HL7标准的关系

自1987年开始[Health Level Seven (HL7)](http://www.hl7.org) 就一直在开发卫生保健信息交换和相关的一些标准。在这些时间里，该组织已经开发了很多标准系列——很多在全球范围内用以实现卫生保健数据共享的自动化和改善病人的健康。FHIR是在毋须了解任何这些标准的背景下而开发的。然而，FHIR中继承了之前的一些经验，不论是对以往最佳实践的应用还是避免陷入之前的一些坑。   
这部分介绍了FHIR与HL7其他一些标准系列的关系。之前有过HL7标准相关经验的和那些可能需要实现FHIR解决方案与其他HL7标准互操作性的人可能对此比较感兴趣。  

这部分中：
*   [Version 2.x](comparison-v2.html)
*   [V3 (RIM / messaging)](comparison-v3.html)
*   [CDA &amp; CCDA etc](comparison-cda.html)
*   [其他HL7标准](comparison-other.html)

**注意事项:**

*   除了一下所列的主流标准，HL7也有很多实施规范，其中一些被视作和标准本身一样重要。以下的一些指导意见适用于每个标准系列以及它所衍生出的实施规范。比如CDA中所罗列的指导意见适用于CCDA，CCD和其他CDA规范。    
*   尽管这部分关注点在于FHIR与其他HL7标准的关系，也包含一些与非HL7标准的关系。一些资源中包含了诸如 [DICOM](http://medical.nema.org)  (参考[ImagingStudy](../clin/imagingstudy.html) resource) 和 [IHE](http://www.ihe.net/)  (如 [SecurityEvent](../infra/securityevent.html) and [DocumentReference](../infra/documentreference.html) resources)中功能的实现。   
*   很多FHIR资源吸纳了其他标准的需求，或者提供了与其他标准的映射关系。一些资源中也提供了如何与其他外部标准一起使用的指导意见。同样，可以在wiki[页面](http://wiki.hl7.org/index.php?title=FHIR_and_Other_Specifications)上找到关于FHIR如何与其他标准一起使用的建议。   
*   FHIR能够满足之前的HL7互操作性标准(V2, V3 和CDA)的所有需求。在很多案例中，它还有易于实现互操作性的优势。因此，未来FHIR可能会逐步替代其中一些或所有标准。然而，至于市场作出这样的转变时间上有多快还不是很明朗。 极有可能的是在很长的一段时间内这些标准将共存。HL7承诺只要HL7会员需要现有的标准，它们就会一直维护下去。
 

 &copy; HL7.org 2011 - 2014. FHIR DSTU (v0.2.1-2606)构建于2014  7月2号 16:29+0800 星期三 . 
链接：[试行版是什么](http://hl7.org/implement/standards/fhir/dstu.htmll) |[版本更新情况](http://hl7.org/implement/standards/fhir/history.htmll) | [许可协议](http://hl7.org/implement/standards/fhir/license.htmll) |[提交变更建议](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemAdd&tracker_id=677) 	 		