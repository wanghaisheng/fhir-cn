title: 
date: 
categories: doc
---

[首页](../home/index.html) >[文档](documentation.html) >[资源定义](resources.html) >[资源格式](formats.html) > **XML**       


#### 1.18.1   XML            

资源的XML表达格式如下所示:     

```
 <name xmlns="http://hl7.org/fhir" (attrA="value")>   
   <nameA><!-- 1..1 type description of content  --><nameA>
   <nameB[x]><!-- 0..1 type1|type1 description  --></nameB>
   <nameC> <!--  1..* -->
     <nameD><!-- 1..1 type>Relevant records  --></nameD>
   </nameC>
 <name>
```      

注意:

*   为了构建一个有效的XML资源实例,只需要根据每个元素中对基数数据类型和内容描述,用有效内容替换元素和属性的内容即可.    
*   资源和元素名称都是大小写敏感的.      
*   元素的顺序必须按照排列
*   一些属性是作为attribute的: 基本数据类型的值是在value属性中，扩展的url是在url属性中，以及id属性primitive values in the "value" attribute, extension URLs in the "url" attribute on an extension, and the "id" property            
*   FHIR元素总是属于 [http://hl7.org/fhir](http://hl7.org/fhir)命名空间, 该命名空间常常是根元素的默认命名空间.当明确地将外部内容模型引入到资源的内容模型当中的时候,才会使用的其他命名空间.比如, [每个资源里都有XHTML](narrative.html)
*   任意XML元素都可以有一个id属性,用作[内部引用定位](references.html#idref). 在这个格式中并没有显示id属性.      
*   XML表示方式中并没有显示基础架构类元素。这些元素的出现顺序必须在其他所定义的子元素之前：
	*  首先是基础资源base resource中定义的元素按照顺序排列
	*  然后是领域资源domain resource中定义的元素按照顺序排列
*   FHIR元素绝不能为空. 如果资源中出现了某个元素,它要么必须包含一个value属性,要么包含子元素,要么必须有1到多个[扩展](extensibility.html)         
*   属性绝不能为空.要么不出现,出现就必须包含至少一个字符的非空格内容. 
*   图标![](../material/lock.png)表示该元素受其他规则的影响.     
*   XML 批注,处理指南和格式并不属于资源内容的一部分.      
*   利用 &lt;?xml encoding=&quot;&quot; ?&gt; 指定字节编码,处理指南是可选的,但推荐要有.其他处理指南不宜包括,为了能够正确理解和或准确的展现资源的叙述性文本 也不应作要求.在处理资源内容时,应用程序可以保留这些内容,但不作要求. 注意 数字签名可能会对有所依赖(取决于所使用的canonicalization方法)         
*   Other processing Instructions SHOULD not be included, except and SHALL not be required in order to properly understand and/or present the data or narrative of the resource. Applications MAY preserve these when handling resources, but are not required to do so
*   The MIME-type for this format is application/xml+fhir.      


               

####   1.18.1.1 XML Schema and Schematron                      

该标准中包含了所有内容模型的schema定义。根schema叫做 &quot;[fhir-base.xsd](fhir-base.xsd)&quot;其中定义了所有的数据类型，和这部分所描述的基本的基础架构。另外，每个资源都有一个schema和包含所有资源的一个通用schema [fhir-all.xsd](../material/fhir-all.xsd) 
. 定制的 atom schema [fhir-atom.xsd](../material/fhir-atom.xsd)
用以校验 [bundles](#atom).

除了w3c schema 文件,标准中也包括了schematron文件， 包含了对数据类型和资源的其他很多约束。每个资源对应一个，也有一个fhir-atom.sch整合了所有资源的规则      

交换时XML必须通过 w3c schema and Schematron的校验，尽管通过了 schema 和 Schematron的校验不足以说明是一个 conformant instance: 
标准中包含了一些无法通过这些机制检测的规则。
所交换的内容不应规定schema或者在资源内部规定schema实例的命名空间 。     


#### 1.18.1.2 数字签名


Resources and/or Bundles may be digitally signed (ref to be provided). One consequence of signing the document is that URLs, identifiers and internal references are frozen and cannot be changed. This might be a desired feature, but it may also cripple interoperability between closed ecosystems where re-identification frequently occurs. For this reason, it is recommended that only Document Bundles are signed and then only when all the related resources are found in the bundle.

todo: canonical XML 




 &copy; HL7.org 2011 - 2014. FHIR DSTU (v0.2.1-2606)构建于2014  7月2号 16:29+0800 星期三 . 
链接：[试行版是什么](http://hl7.org/implement/standards/fhir/dstu.html) |[版本更新情况](http://hl7.org/implement/standards/fhir/history.html) | [许可协议](http://hl7.org/implement/standards/fhir/license.html) |[提交变更建议](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemAdd&tracker_id=677)      