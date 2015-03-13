title: 
date: 
categories: home
---

**首页**	
# 0  欢迎来到 FHIR&reg;的世界       
翻译之前，倍感忐忑，英语中总是有一些术语、词汇无法准确理解,其中一部分也没有办法和现有的中文概念对应起来，这里我整理了一份列表，希望能够通过不断完善，形成一份 `FHIR` 标准中涉及的词汇的约定俗成的叫法[常见术语的汉译](../doc/common-terms-in-Chinese.html)，翻译过程中并非按照原文逐字逐句，适当的做了增删改，但均文中做出了说明。中文的排版参考了[中文文案排版指北](https://github.com/sparanoid/chinese-copywriting-guidelines)            
初次接触 `FHIR` 的话? 先读一读 [总结](../doc/summary.html)， [开发者指南](../doc/overview-dev.html)，或者临床应用简介(todo)，然后读一读[概述](../doc/overview.html)。 也可以读一下 `FHIR` 的 [许可协议](../doc/license.html)
> This ballot is a “For comment” draft of the material that will be part of the scope of the second DSTU release (currently slated for ballot in April/May 2015). It is not a fully polished release and not all content should be considered at the “ready to implement” level. The purpose of this ballot is to give the implementer community a sense of the content that will be included in the second DSTU. This includes revisions to DSTU content (some of them significant) as well as additions to functionality and new resources.

> This release should be considered “feature complete” in that it is unlikely that any significant new capabilities or resources will be introduced between this publication and the DSTU ballot. However, additional changes are very likely as work groups continue to clear the backlog of change requests and continue their review and polishing of content. While any sort of feedback is welcomed, balloters are encouraged to focus on substantive concerns with the specification rather than spending too much energy on reporting spelling, grammatical or other similar issues. These will be addressed as part of the quality process leading up to the DSTU ballot in May.

> This draft content will serve as the basis for FHIR Connectathons in Jan-Feb 2015, including FHIR Connectathon 8.


##	**主要章节:**
<table class="bare"> <tr> <td align="middle"><a href="../doc/documentation.html"><img height="128" width="128" src="../images/icon-documentation.png"><br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[基础文档](../doc/documentation.html)</td>
  <td align="middle"><a href="../impl/implementation.html"><img height="128" width="128" src="../images/icon-implementation.png"><br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[实现与 &amp; 交换](../impl/implementation.html)</td>
  <td align="middle"><a href="../clin/clinical.html"><img height="128" width="128" src="../images/icon-clinical.png"><br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[临床类资源](../clin/clinical.html)</td>
  <td align="middle"><a href="../admin/administration.html"><img height="128" width="128" src="../images/icon-administration.png"><br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[管理类资源](../admin/administration.html)</td>
  <td align="middle"><a href="../infra/infrastructure.html"><img height="128" width="128" src="../images/icon-infrastructure.png"><br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[基础架构类资源](../infra/infrastructure.html)</td></tr></table>
##	**快速链接:**  
###  文档	
*   [资源列表Resource List](../res/resourcelist.html)	  
*   [XML](../doc/xml.html) &amp; [JSON](../doc/json.html)	
*   [REST API](../impl/http.html) &amp; [Search](../impl/search.html)		
*   [数据类型Data Types](../doc/datatypes.html)		
*   [术语的使用Codes / Terminologies](../doc/terminologies.html)	
*   [扩展Extensions](../doc/extensibility.html)	
*   [完整内容Full table of contents](../doc/toc.html)	
###  代码实现  
*   [下载](../impl/downloads.html)	
*   [FHIR 本地化](../impl/profiling.html)	
*   [实施指南](../impl/iglist.html)	
*   [FHIR Schemas &amp; Schematrons](../material/fhir-all-xsd.zip)	
*   示例: [XML](../material/examples.zip), [JSON](../material/examples-json.zip)	
*   代码: [Java](../material/fhir-0.2.1-Java-0.81.zip), [C#](http://www.nuget.org/packages/Hl7.Fhir), [Pascal](../material/fhir-0.2.1-Pascal-0.80.zip), [iOS](../material/fhir-0.2.1-Java-0.81.zip), [JS](../material/fhir-0.2.1-JavaScript-0.1.zip), [XML](../material/fhir-0.2.1-XML Tools-0.01.zip)   
*   [常见应用场景和规范](../impl/usecases.html)	
*   [安全Security](../impl/security.html)			
*   [更多帮助](../impl/support.html)			
###  外部链接   
*   [Stack Overflow](http://stackoverflow.com/questions/tagged/hl7_fhir) ([何时使用](http://meta.stackoverflow.com/questions/3966/is-it-okay-to-use-stack-overflow-as-the-support-forum-for-a-product-or-project))		
*   [公开可用的测试服务器 &amp; 软件](http://wiki.hl7.org/index.php?title=Publicly_Available_FHIR_Servers_for_testing "Publicly_Available_FHIR_Servers_for_testing")	
*   [FHIR Wiki](http://wiki.hl7.org/index.php?title=FHIR "FHIR")	 
* [HIMSS研讨会：互操作性的明天](https://live.blueskybroadcast.com/bsb/client/CL_DEFAULT.asp?Client=556675&PCAT=8341&CAT=8341&Review=true)	  
*   [FHIR 相关博客博文](http://wiki.hl7.org/index.php?title=FHIR_Blogs)	
*   其他语言版本: [日语](https://sites.google.com/site/fhirjp/)  [英语](http://hl7-fhir.github.io/index.html) [俄语](http://fhir-ru.github.io)


注意: FHIR要用兼容SVG的浏览器(Microsoft Internet Explorer 10+, Firefox 3.0+, Chrome, or Safari)打开。	

&copy; HL7.org 2011+. FHIR DSTU (v0.4.0-3900) 构建于2014  12月20号 2014 22:38+0000 星期六 . 
链接：[试行版是什么](http://hl7.org/implement/standards/fhir/dstu.html) |[版本更新情况](http://hl7.org/implement/standards/fhir/history.html) | [许可协议](http://hl7.org/implement/standards/fhir/license.html) |[提交变更建议](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemAdd&tracker_id=677) 	
