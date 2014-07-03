title: 一页纸总结
date: 2014-05-20 15:13:12
categories: doc
---

*   [首页](index.htm)
*   [文档](documentation.htm)
*   **总结**	
		</div>  <!-- /container -->
	</div>  <!-- /segment-breadcrumb -->

	<div id="segment-content" class="segment">  <!-- segment-content -->
	<div class="container">  <!-- container -->
            <div class="row">
            	<div class="inner-wrapper">
  <!-- CONTENT CONTENT -->

<div class="col-9">

<a name="glossy"> </a>

#  HL7 FHIR简介 <span class="sectioncount">1.6<a name="1.6"> </a></span>

[获取PDF格式的该文档](fhir-summary.pdf)

FHIR&reg; – Fast Health Interoperable Resources (hl7.org/fhir) – 是由HL7创建的新一代标准框架.FHIR整合了HL7 V2,V3 和CDA的优点,同时利用了最新的Web标准,紧紧围绕着implementability可实现性.

FHIR 解决方案是基于一些称之为“Resources”资源的模块化组件的.  这些资源可以很容易的组装进生产系统中,以已有方案的一小部分成本来解决实际的临床和管理问题.
FHIR适用于多种场景– 移动电话的社交媒体、云平台通信、基于EHR的数据共享、大型医疗机构的服务器通信和其他。

## 为什么 FHIR 比较好 <span class="sectioncount">1.6.1<a name="1.6.1"> </a></span>

FHIR在现有标准基础上做了很多改进:

*   主要关注在implementation方面 – 易于且快速实现(很多开发人员在单个工作日记就能完成一些简单的接口)
*   多种实现的库,有很多示例可以帮助开发
*   标准免费使用 无额外限制
*   即开即用的互操作性– 基础的资源可以直接用，也可以根据本地实际需求来改动
*   从HL7 V2 CDA演化而来 – 这些标准可以共存 相互使用
*   依赖Web标准– XML, JSON, HTTP, Atom, OAuth等等.
*   支持RESTful架构，同时支持使用消息或文档进行无缝地信息交换
*   简练、易于理解的标准

*   提供一种开发人员易于使用的人可读的格式wire format
*   基于本体的扎实分析 并提供一个对应以保证正确性

## Flexibility <span class="sectioncount">1.6.2<a name="1.6.2"> </a></span>

健康卫生标准的一个核心挑战在于说如何处理不同的卫生流程造成的多样性。过去的日子里，在规范中添加更多的字段和可选性，最终增加了实现的复杂度和成本。另外的就是依赖本地扩展的方式，但这样实现中也会产生诸多问题。

FHIR通过定义一个扩展和改造已有资源的简单框架来解决这一挑战。不管是如何开发的 所有系统都能很容易地解读这些扩展，使用同一框架可以像获取其他资源一样来获取扩展的定义。

另外，每种资源都会有一个人可读的文本表示 用HTML来表达，作为保证临床安全的一种选择。对于很多采用基于简单文本或文档方式的诸多系统中复杂的临床信息 这点尤为重要。

##  资源示例: Patient <span class="sectioncount">1.6.3<a name="1.6.3"> </a></span>

该示例展示了一个资源的关键部分: 一个本地扩展，一个人可读的HTML的表示和标准化定义的数据内容.

![](shot.png)

FHIR 中有诸如病人、医务人员、医疗机构和设备的管理性概念的资源，也有很多涵盖了疾病、用药、诊断、治疗计划和财务等临床概念的资源

## The FHIR 开发过程 <span class="sectioncount">1.6.4<a name="1.6.4"> </a></span>

FHIR 是HL7一个正在开发之中的标准。到2013年年底，FHIR会变成试行版。 在一段时间的试用期之后，极可能在2015年左右 将正式发布为最终版标准。

由于FHIR提供的诸多优点，使用已经在进行之中. 

[http://www.hl7.org/fhir](http://www.hl7.org/fhir). Follow us on Twitter using [#FHIR](https://twitter.com/search?q=%23FHIR)


  <!-- Analytics Below
================================================== -->

</body>
</html>