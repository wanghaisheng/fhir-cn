title: 
date: 
categories: doc
---

[首页](../home/index.html) >[文档](documentation.html) >[资源定义](resources.html) >[资源格式](formats.html) > **XML**       


#### 1.12.5.1   XML            

XML语法与[XML notation](formats.html)非常接近:     

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
*    资源和元素名称都是大小写敏感的.      
*   在基础标准如[ATOM](#atom) 中所定义的特性才被表示成属性,用在bundle的XML表达,也用在表示基本数据类型的属性.            
*   FHIR元素总是属于 [http://hl7.org/fhir](http://hl7.org/fhir)命名空间, 该命名空间常常是根元素的默认命名空间.当明确地将外部内容模型引入到资源的内容模型当中的时候,才会使用的其他命名空间.比如, [每个资源里都有XHTML](narrative.html)
*   任意XML元素都可以有一个id属性,用作[内部引用定位](references.html#idref). 在这个格式中并没有显示id属性.      
*   FHIR元素绝不能为空. 如果资源中出现了某个元素,它要么必须包含一个value属性,子元素,作为[叙述性文本](narrative.html#narrative)的[关联对象](references.html#idref)的id属性,要么必须有1到多个[扩展](extensibility.html)                     
*   属性绝不能为空.要么不出现,出现就必须包含至少一个字符的非空格内容.     
*   XML 批注,处理指南和格式并不属于资源内容的一部分.      
*   利用 &lt;?xml encoding=&quot;&quot; ?&gt; 指定字节编码,处理指南是可选的,但推荐要有.其他处理指南不宜包括,为了能够正确理解和或准确的展现资源的叙述性文本 也不应作要求.在处理资源内容时,应用程序可以保留这些内容,但不作要求. 注意 数字签名可能会对有所依赖(取决于所使用的canonicalization方法)         

当表示成XML时,资源可以通过schema和schematron的方式来校验,但是对于系统不作此类要求.

######  1.12.5.1.2.1 Atom Bundle表达

在XML中 [bundles](extras.html#bundle)是用 Atom格式 ([http://tools.ietf.org/html/rfc4287](http://tools.ietf.org/html/rfc4287))来表示的,如下:        
```
<feed xmlns="http://www.w3.org/2005/Atom"> 
  <title><!-- 1..1 string Text statement of purpose --></title>
  <id><!-- 1..1 uri Unique URI for this bundle --></id>
  <link rel="self" href="[building application url (Service base on REST)]"/><!-- 0..1 -->
  <link rel="first" href="[paging: url for first page of result]"/><!-- 0..1 -->
  <link rel="previous" href="[paging: url for previous page of result]"/><!-- 0..1 -->
  <link rel="next" href="[paging: url for next page of result]"/><!-- 0..1 -->
  <link rel="last" href="[paging: url for last page of result]"/><!-- 0..1 -->
  <link rel="fhir-base" href="[base path to resolve local urls in this bundle]"/><!-- 0..1 -->
  <os:totalResults xmlns:os="http://a9.com/-/spec/opensearch/1.1/"><!-- 0..1 integer 
              Paging: the total number of results --></os:totalResults>
  <updated><!-- 1..1 instant When the bundle was built --></updated>
  <author><!-- 0..1 Who created resource? -->
      <name><!-- 1..1 string Name of Human or Device that authored the resource --></name>
      <uri><!-- 0..1 uri Link to the resource for the author --></uri>
  </author>
  <category term="[Tag Term]" label="[Tag Label]" scheme="[Tag Scheme]"/> <!-- 0..* -->
  <entry><!-- Zero+ -->
    <title><!-- 1..1 string Text summary of resource content --></title>
    <id><!-- 1..1 uri Logical Id (URI) for this resource --></id>
    <link rel="self" href="Version Specific reference to Resource"><!-- 0..1 --></link>
    <updated><!-- 1..1 instant Last Updated for resource --></updated>
    <published><!-- 0..1 instant Time resource copied into the feed --></published>
    <author><!-- 0..1 Who created resource? -->
      <name><!-- 1..1 string Name of Human or Device that authored the resource --></name>
      <uri><!-- 0..1 uri Link to the resource for the author --></uri>
    </author>    
    <!-- Tags affixed to the resource (0..*):   --> 
  <category term="[Tag Term]" label="[Tag Label]" scheme="[Tag Scheme]"/> <!-- 0..* -->
    <content type="text/xml"><!-- 0..1 -->
      <[ResourceName] xmlns="http://hl7.org/fhir">
        <!-- Content for the resource -->
      </[ResourceName]>
    </content>
    <summary type="xhtml"><!-- 0..1 -->
      <div xmlns="http://www.w3.org/1999/xhtml"><!-- Narrative from resource --></div>
    </summary>
  </entry>
  <Signature xmlns="http://www.w3.org/2000/09/xmldsig#">
    <!-- 0..1 Enveloped Digital Signature (see Atom section 5.1) -->
  </Signature>
</feed>

```

###### 1.12.5.1.1.1 注意事项     

*   逻辑上,bundle就是准备好发送给某处使用的资源集合-就是一个"feed"      
*   atom feed中元素的顺序无关紧要,entry的顺序是很重要的,可能会存在一些含义. 上面提到的atom命名空间中的元素顺序不必遵守,尽管在FHIR参考实现中是这样做的.       
*   feed的title和entry都可以是任意的人可读的内容,entry的title宜从资源自身的内容衍生而得到.系统可能会忽略title中存在的内容.    
*   每个bundle都应包含一个惟一的id,id应包含一个有效的绝对[uri](datatypes.html#uri). 推荐使用UUIDs (urn:uuid:...)
*   entry元素包含了  [三块资源元数据](resources.html#metadata): Id (.id), Version Id (.link), Last Updated (.updated)
*   每个entry的category元素中也包含了附加在资源上的各种tag标签,  category元素也可以用作它用.   
*    entry.i应该是一个绝对URL,尾部则是资源的逻辑id.id是与版本无关的     
*    entry.link是与版本相关的对资源的引用,       
*   当在[RESTful implementation](http.html)中使用时,  entry.link 和 entry.id是系统中资源的URL. 通过atom bundle的[updates operation](http.html#history), 特定版本的link可以用做发布/订阅系统的同步.在其他场景下,如果有的话,link的值宜是对上某个服务器的字面上的引用        
*   注意 atom包含了标准要求每个entry都要有一个已知的作者.如果在基础的feed元素中包含了author元素,后续每个entry就不必指定.          
*   在FHIR资源模型中资源的作者是不明确的. 相反的,把这个问题留给了基础架构.name就是人或机器的名称.uri是与author的链接(可能是一个Practitioner资源)      
*   xml:base 元素不宜使用,开发中也不必支持.      
*    entry.content是可选的,但总是应该出现,除非是事务响应的特殊情况.        
*   如atom标准所述,整个bundle可以使用一个数字签名     
*    feed.link为&quot;self&quot; 并没有什么特殊含义,除了查询操作的情况,但可以用以引用feed源.      
*    feed.link为 &quot;first&quot;, &quot;last&quot;, &quot;previous&quot; 和 &quot;next&quot;用于在RESTFUL接口中实现分页功能,  使得客户端能够浏览多页的结果.参考 [search/query](search.html)     
*   feed.link 为 &quot;fhir-base&quot;用于解析bundle中的相对URL.参考 [相对引用](references.html#atom-rel)


###### 1.12.5.1.1.2  Bundling versions - deletion                       


当返回一些资源集合或一个资源的多个版本时,某条entry可能会指出entry已经被删除了. 在atom feed中表示已删除的资源请按照  [rfc6721.txt](http://www.rfc-editor.org/rfc/rfc6721.txt)的定义:     

```
<feed xmlns="http://www.w3.org/2005/Atom">  
  ... feed elements and other entries ...
  <at:deleted-entry xmlns:at="http://purl.org/atompub/tombstones/1.0"
      ref="[Logical Id for deleted resource]" when="instant [when deleted]">
    <link rel="self" href="[Version Specific reference to Resource]"><!-- 0..1 --></link>
  </at:deleted-entry>
  ... other entries ...
  ```
如果通过Restful接口调用该资源,服务器返回410无法找到的错误信息         

##### 1.12.5.1.2 开发实现/注意事项               

*   Atom Feed可使用atom标准中提到的规则来签名。对文档进行签名的后果之一是URL，标识符和内部引用都被锁定，无法更改。这可能是一个我们期望的特性，但也会给封闭式的生态系统带来互操作性的障碍，因为常常会发生重新 标识的情况.                  鉴于此，推荐仅对所有相关资源都能够在bundle中找到的Document Bundle进行签名。                         

*    FHIR资源将id属性作为内部引用的目标。 这些id属性是唯一的，在单个资源的语境中是能够解析的。当资源整合成bundle时，不同的资源可能会存在重复的id，因此，在声明id属性时限制id属性能够解析的范围是很重要的。         


######  1.12.5.1.2.1 Binary Resources                   

当在atom feed中以XML格式表示 [binary resource](extras.html#binary)时，它是以base64编码的内容，也有一个content-type，也就是HTTP中指定的mime-type：                            
```      
 <Binary xmlns="http://hl7.org/fhir" contentType="[mime type]">  
   [Base64 Content]
 </Binary>
```                         
Binary resources 也可以嵌套成 [内嵌资源](references.html#contained).  如果需要收集binary对象的元数据，可以使用资源类型如[DocumentReference](documentreference.html) or [Media](media.html).                          

#####   1.12.5.1.3 XML Schema and Schematron                      

该标准中包含了所有内容模型的schema定义。根schema叫做 &quot;[fhir-base.xsd](fhir-base.xsd)&quot;其中定义了所有的数据类型，和这部分所描述的基本的基础架构。另外，每个资源都有一个schema和包含所有资源的一个通用schema [fhir-all.xsd](../material/fhir-all.xsd) 
. 定制的 atom schema [fhir-atom.xsd](../material/fhir-atom.xsd)
用以校验 [bundles](#atom).

除了w3c schema 文件,标准中也包括了schematron文件， 包含了对数据类型和资源的其他很多约束。每个资源对应一个，也有一个fhir-atom.sch整合了所有资源的规则      

交换时XML必须通过 w3c schema and Schematron的校验，尽管通过了 schema 和 Schematron的校验不足以说明是一个 conformant instance: 
标准中包含了一些无法通过这些机制检测的规则。
所交换的内容不应规定schema或者在资源内部规定schema实例的命名空间 。     


 &copy; HL7.org 2011 - 2014. FHIR DSTU (v0.2.1-2606)构建于2014  7月2号 16:29+0800 星期三 . 
链接：[试行版是什么](http://hl7.org/implement/standards/fhir/dstu.html) |[版本更新情况](http://hl7.org/implement/standards/fhir/history.html) | [许可协议](http://hl7.org/implement/standards/fhir/license.html) |[提交变更建议](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemAdd&tracker_id=677)      