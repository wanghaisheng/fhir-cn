title: 
date: 
categories: doc
---

[首页](../home/index.html) >[文档](documentation.html) >[资源定义](resources.html) > **JSON**

####  1.18.2 用JSON格式表示资源 　　　

尽管在描述FHIR资源时使用的XML语言，但是该标准也定义了资源的JSON表达方式．
JSON格式与标准XML格式很相近，互相转换很容易，因此Xpath的查询可以很容易的映射到对JSON结构的查询，这种格式的正式的mime-type是 application/json+fhir.           

允许客户端自由选择是实现XML还是JSON格式。服务器应该支持XML，可以选择是否支持JSON。注意如果支持的话应该在 [Conformance Statement](conformance.html)中声明它们所支持的格式有哪些.                    
JSON表达方式与XML表达方式的关系：        
*   JSON对象元素的名称和XML的元素属性名称是一样的，包括可以重复的元素。元素的名称是大小写敏感的。         
*   如同XML一样，JSON 属性永远不能为空值，如果为空则必须省略该元素。      
*   JSON中空格并不是资源内容的一部分。应用程序处理资源时可能会保留空格，但对比不作要求。注意数字签名可以会依赖于空格。      
二者之间的差异在于：     
*   JSON格式中没有命名空间一说。       
*   JSON中资源类型的表达完全不一样。      
*   JSON中属性的顺序不是那么重要，尽管必须维护数组中元素的顺序。        
*   JSON中没有属性VS元素的标记，因此属性是以完全不同的方式来处理的  (xml:id, value)     
*   JSON中有数组array，可以用来表示重复元素。注意当某个项可能会重复时使用array数组，即使在某个数据实例中并没有重复出现。        
*  [Narrative](narrative.html)数据类型中的 XHTML &lt;div&gt; 元素用XHTML的 单个转移字符串来表示，这样做是为了避免JSON中混合内容的问题等等，XHTML 仍然遵循 [the Narrative](narrative.html)中所描述的规则。       
*	There is no inherent support in JSON for a comment syntax. As a convention, content that would be comments in an XML representation is represented in a property with the name "fhir_comments", which is an array of strings, which can appear on any JSON object. This is heavily used in example instances, e.g. in this specification, but not usually used in production systems (and production systems may choose to reject resources with comments in them)

这些差异，尤其是重复元素的整个，都是不可避免的，也就是说通用的XML到JSON的转换不能正确的处理这些。 [reference platforms](downloads.html#refimpl)中提供了 XML &lt;--&gt; JSON的转换功能，其中整合了一些FHIR相关的特性。       
 The formal mime type for this format is application/json+fhir. 
#####   1.18.2.1重复元素的JSON表达方式       
一个元素的最大基数为x..*,则该元素在实例中可能会出现不止一次。在XML中只需要重复XML元素多次即可。JSON中，我们是通过array数组来实现的。注意：             
*   数组的名称是单一的——这点和XML一样。      
*   即使没有重复，可能会重复的一个项目也是用array来表示的，这样不管怎样，处理该元素的方式总是不变，      
<pre class="xml">
 &lt;<b>coding</b>&gt;
      &lt;<b>system</b> value=&quot;http://snomed.info/sct&quot;/&gt;
      &lt;<b>code</b> value=&quot;104934005&quot;/&gt;
 &lt;/<b>coding</b>/&gt;
 &lt;<b>coding</b>&gt;
      &lt;<b>system</b> value=&quot;http://loinc.org&quot;/&gt;
      &lt;<b>code</b> value=&quot;2947-0&quot;/&gt;
 &lt;/<b>coding</b>/&gt;
</pre>

对应的JSON格式：    
<pre class="json">
 &quot;coding&quot;: [
   {
     &quot;system&quot; : &quot;http://snomed.info/sct&quot;,
     &quot;code&quot; : &quot;104934005&quot;
   },
   {
     &quot;system&quot; : &quot;http://loinc.org&quot;,
     &quot;code&quot; : &quot;2947-0&quot;
   }
 ]
</pre>

#####   1.18.2.2 基本数据类型元素的JSON表达     

FHIR元素值为基本数据类型的表达分为两类：      

*   元素名称为 JSON属性名称，数据类型是JSON的number、boolean和string类型。        
*   JSON属性名称是元素名称前加上  &quot;_&quot; 表示它包含的是xml:id和或扩展的值。    

FHIR  [integer](datatypes.html#integer) 和 [decimal](datatypes.html#decimal) 数据类型对应成JSON的number，   FHIR  [boolean](datatypes.html#boolean)
对应成JSON的 boolean,其他所有数据类型都被看作JSON string。一般而言空格是很重要的
(i.e.非字符串类型不存在前置后置空格 ).    


<pre class="xml">
 &lt;<b>code</b> value=&quot;abc&quot;/&gt; &lt;!-- code --&gt;
 &lt;<b>date</b> value=&quot;1972-11-30&quot;/&gt; &lt;!-- dateTime --&gt;
 &lt;<b>deceased</b> value=&quot;false&quot; /&gt; &lt;!-- boolean --&gt;
 &lt;<b>count</b> value=&quot;23&quot; /&gt;  &lt;!-- integer --&gt;
</pre>

对应的JSON格式：    
<pre class="json">
 &quot;code&quot; : &quot;abc&quot;,
 &quot;date&quot; : &quot;1972-11-30&quot;,
 &quot;deceased&quot; : false,
 &quot;count&quot; : 23
</pre>

> 当在实现中使用  JavaScript 的JSON.parse() 时的解析其和，牢记一点，JavaScript本来只支持一种数字型数据类型——浮点数
> 这会使得FHIR number的精度下降，你可能会需要使用定制解析其和big number库
> (比如. 可以考虑[https://github.com/jtobey/javascript-bignum](https://github.com/jtobey/javascript-bignum))

如果值存在id属性或者扩展，该采用如下的表达方式：      

<pre class="xml">
 &lt;**dob** id=&quot;314159&quot; value=&quot;1970-03-30&quot; &gt;
   &lt;extension url=&quot;http://example.org/fhir/extensions#text&quot;&gt;
     &lt;valueString value=&quot;Easter 1970&quot;/&gt;     
   &lt;/extension&gt;
 &lt;/**dob**&gt;
</pre>

对应的JSON格式为：    
<pre class="json">
 &quot;dob&quot;: &quot;1972-11-30&quot;,
 &quot;_dob&quot;: { 
   &quot;id&quot;: &quot;314159&quot;, 
   &quot;extension&quot;: [{
      &quot;url&quot; : &quot;http://example.org/fhir/extensions#text&quot;,
      &quot;valueString&quot; : &quot;Easter 1970&quot;
   }]
 }
</pre>

注意: 如果基本数据类型只有id属性或扩展，但是没有value，只需要渲染带 &quot;_&quot;的属性即可。     
当基本数据类型元素可能会重复时，使用两个数组来表达。JSON null值用来保证id和或扩展与第一个数组的对应值一致,如下例所示：      

<pre class="xml">
 &lt;<b>code</b> value=&quot;au&quot;/&gt;
 &lt;<b>code</b> value=&quot;nz&quot;&gt;
   &lt;extension url=&quot;http://hl7.org/fhir/Profile/tools-extensions#display&quot;&gt;
     &lt;valueString value=&quot;New Zealand a.k.a Kiwiland&quot;/&gt;     
   &lt;/extension&gt;
 &lt;/<b>code</b>&gt;
</pre>

对应的JSON格式为： 
    
<pre class="json">
 &quot;code&quot;: [ &quot;au&quot;, &quot;nz&quot; ],
 &quot;_code&quot;: [ 
   null, 
   { &quot;extension&quot;: [{
      &quot;url&quot; : &quot;http://example.org/fhir/extensions#text&quot;,
      &quot;valueString&quot; : &quot;New Zealand a.k.a Kiwiland&quot;
   }] }
  ]
 }
</pre>

注意: 当某个重复元素没有value时，在第一个数组中用null来表示。当一个元素有value，但是没有id或扩展时，第二个数组的该元素位置为null。     
> 设计上的考虑: 基本数据类型的表达被这样分为两类是为了简化没有id和扩展的简单基本数据类型的表达。这样做使得id属性和扩展的表达显得特别丑陋，但这两种情况在基本数据类型中其实是很少用到的。          


#####  1.18.2.3 元素、复杂数据类型的JSON表达      

用JSON对象来表示元素和[复杂的数据类型](datatypes.html) ，包含了不同数据类型的每个元素的member。composite有id属性，将其以处理基础数据类型中所描述的方式转换为JSON的member值。如下：     

 <pre class="xml">
&lt;person&gt;
  &lt;text&gt;
    &lt;status value=&quot;generated&quot; /&gt;
    &lt;div xmlns=&quot;http://www.w3.org/1999/xhtml&quot;&gt;&lt;p&gt;...&lt;/p&gt;&lt;/div&gt;
  &lt;/text&gt;
  &lt;name&gt;
    &lt;use value=&quot;official&quot; /&gt;  
    &lt;given value=&quot;Karen&quot; /&gt;
    &lt;family id=&quot;a2&quot; value=&quot;Van&quot; /&gt;
  &lt;/name&gt;
&lt;/person&gt;
</pre>

对应的JSON格式为：    
<pre class="json">
{
  &quot;person&quot; : {
    &quot;name&quot; : [{
      &quot;use&quot; : &quot;official&quot; ,
      &quot;given&quot; : [ &quot;Karen&quot; ],
      &quot;family&quot; : [ &quot;Van&quot; ]
      &quot;_family&quot; : [ {&quot;id&quot; : &quot;a2&quot;} ]
     }],
    &quot;text&quot; : {
      &quot;status&quot; : &quot;generated&quot; ,
      &quot;div&quot; : &quot;&lt;div xmlns=\&quot;http://www.w3.org/1999/xhtml\&quot;&gt;&lt;p&gt;...&lt;/p&gt;&lt;/div&gt;&quot;
    }
}
</pre>

需要注意的是：    
*    given 和 family都是可重复的XML元素，因此它们被当作数组处理，无论它们有没有重复。    
*   在'name'的family部分中,  如上所述，在_family表达了'id'      
*    'div' 元素中的XHTML内容，也就是Narrative  'text' 元素，是在value属性中用转义字符来表示的。 xhtml根元素必须是xhtml命名空间的 &lt;div&gt;   

#####   1.18.2.4  资源的JSON表达      

资源就是一个JSON对象，其中&quot;resourceType&quot; 属性告诉解析器该资源的类型：     
<pre class="json">
{
  &quot;resourceType&quot; : &quot;Patient&quot;,
  &quot;text&quot; : {
    &quot;status&quot; : &quot;generated&quot; ,
    &quot;div&quot; : &quot;&lt;div xmlns=\&quot;http://www.w3.org/1999/xhtml\&quot;&gt;&lt;p&gt;...&lt;/p&gt;&lt;/div&gt;&quot;
  }
  etc...
}
</pre>

注意解析器不能认为resourceType总是第一个出现。     
> **设计时的考虑**: 对于很多JSON-&gt;对象序列化工具 都存在这个问题，设定resourceType总是第一个出现，包括了 [Json.NET](http://james.newtonking.com/json). 然而，一些JSON生成器并不能让编辑应用程序控制属性值的顺序，因此这些实现就不能互相操作，鉴于此，JSON中指出属性值是一组无序的name/value对，标准中也不能对属性的出现次序作出要求，尽管开发任意可能会选择固定属性的顺序，如果能够实现的话。

这里有一个 [示例文件](json-edge-cases.json) ，包含了多种边缘情况，用以测试JSON解析器。           

######  1.18.2.5.3 签名

todo


 &copy; HL7.org 2011 - 2014. FHIR DSTU (v0.2.1-2606)构建于2014  7月2号 16:29+0800 星期三 . 
链接：[试行版是什么](http://hl7.org/implement/standards/fhir/dstu.html) |[版本更新情况](http://hl7.org/implement/standards/fhir/history.html) | [许可协议](http://hl7.org/implement/standards/fhir/license.html) |[提交变更建议](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemAdd&tracker_id=677)      