
####  1.12.3.3 内嵌资源        

在一些情况下,资源引用的内容并不是能够脱离资源本身而独立存在的-它不能够被单独的标识,也不可能有它独立的事务范围.一般而言,这种情况是由于原始数据的二手用户对资源进行了组装,比如中间件引擎.如果在构建资源时没有包含记录主键或者绝对标识信息,那么就不可能得到一个准确标识的资源,即使将其与任意的标识关联起来,这个资源也永远不能脱离引用它的资源的语境而成为某个事务的对象。         
比如,当某个接口引擎要通过一条V2消息构建某个病人的一条[condition](../clin/condition.html)记录时,外科手术相关的仅有信息为她的姓名,如果没有可控的从业人员目录的话,就不足以创建一个可标识的[Practioner](../clin/practitioner.html)资源 -同名同姓的医务人员可能不止一个。  

在这样的情况下,资源是直接內联在资源内的.**当内容能够准确标识时就不必这么做 因为一旦标识信息丢失以后,是极难再次恢复的**                

An example of a contained resource:                     
<pre class="xml">   <!-- Can't fragment test this - too incomplete -->                    
 &lt;Document xmlns=&quot;http://hl7.org/fhir&quot;&gt;
  &lt;extension&gt;...&lt;/extension&gt;
  &lt;text&gt;...&lt;/text&gt;
  &lt;contained&gt;
    &lt;Organization id=&quot;org1&quot;&gt;
      &lt;!-- whatever information is available --&gt;
    &lt;/Organization&gt;
  &lt;/contained&gt;
  &lt;information&gt;
    &lt;!-- other attributes --&gt;
    &lt;custodian&gt;
      &lt;reference value=&quot;#org1&quot; /&gt;
    &lt;/custodian&gt;
    &lt;!-- other attributes --&gt;
  &lt;information&gt;
 &lt;/Document&gt;
</pre>                 　
The same example in JSON:            
<pre class="json"> 　　　
{ &quot;resourceType&quot; : &quot;Document&quot;,
  &quot;extension&quot; : { ... },
  &quot;text&quot; : { .. },
  &quot;contained: [
    { &quot;resourceType&quot; : &quot;Organization&quot;,
      &quot;id&quot; : &quot;org1&quot;,
      .. whatever information is available ...
  }  ]
  &quot;information: {
    ... other attributes ...
    &quot;custodian&quot; : {
      &quot;reference&quot; : &quot;#org1&quot;
  }
    ... other attributes ...
  }
}
</pre>                 

 备注:内嵌资源仍然是一个引用,而不是直接对所引用元素的內联(比如上面的"custodian"),这样做是为了能够保证采用单一的方式来解析资源引用.尽管直接包含似乎会更简单些,当同样的内嵌资源引用不止一次时仍然会需要支持内在引用.最终,这样做会导致语法上的可选项.对于使用XPath处理资源的用户而言,如下的XPath能够解析内在引用:       
 ```       
 ancestor::f:*[not(parent::f:*)]/f:contained/*[@id=substring-after(current()/f:reference/@value, '#')]      
 ```          

 对于内嵌资源的使用和解释要注意以下几点:       
*  　内嵌资源和父资源拥有同样的内部id解析空间           
* 　 内嵌资源不应包含另外的内嵌资源         
*  　内嵌资源不宜包含任何叙述性文本         
* 　 內联资源同样继承了父资源的语境.比如,如果父资源包含一个"subject",        
 内嵌资源也同样拥有一个subject元素,但是并没有指明任何subject,处理程序可能会推理出二个subject是一样的.注意,然而,这些推理只是针对特定的场合.比如,并没有规则说明subject元素的含义在父资源和子资源中是一致的.          
 