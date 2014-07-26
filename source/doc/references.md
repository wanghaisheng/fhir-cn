title: 
date: 
categories: doc
---		

[首页](../home/index.html) >[文档](documentation.html) >[资源定义](resources.html) > **引用**

### 1.12.3 资源的引用     

资源包含2种类型的引用:
*  **内部引用**-一个资源内的不同元素间的引用     
*  **外部引用**一个资源与其他资源组件的引用    
#### 1.12.3.1 内部引用    
资源内元素间相互引用有3种情况:

**ResrouceReference和内嵌资源组件的引用**
ResrouceReference引用的元素指的是内嵌资源的id,一个相对于该资源的不完整id.示例参考下面"内嵌资源" 
**叙述性文本数据元素与结构化数据元素组件的引用**    
通过基于id/idref的方法来实现,表示源数据元素与目的数据元素内容一致.xhtml元素与必须理解的数据元素之间的引用建立了一种"衍生自derived from"的关系,而所衍生出的内容指的是源数据元素的内容.注意这意味着有些引用可能是前向推理(对于这些元素的引用是随后在实例中定义的)    
```
<Patient xmlns="http://hl7.org/fhir">
  <text>
    <status value="generated"/>
    <div xmlns="http://www.w3.org/1999/xhtml">
      <p>xxx <span idref="dob"/>30-11-1972</span>
    </div>
  </text>
  <birthDate id="dob" value="1972-11-30" />
```   
**叙述性文本中的图片的引用**    
图片源可能是资源内可以找到的图片(比如一个内嵌的[Media](../infra/media.html)或[Binary](extras.html#binary)资源)
```
<Patient xmlns="http://hl7.org/fhir">
  <text>
    <status value="generated"/>
    <div xmlns="http://www.w3.org/1999/xhtml">
      <p>xxx <img src="#pic1"/>. xxx.</p>
    </div>
  </text>
  <contained>
    <Binary id="pic1" contentType="image/gif">MEKHxxx.SD/Z</Binary>
  </contained>
```     

在这三种情况下,目标元素都有一个"id"属性,与资源内其他的id属性相较,应保持唯一值.这些id引用的为一些和范围只是在包含它们的资源内部.如果多个资源整合成一个单独的XML片段,诸如[atom feed](xml.html#atom),资源间可能会出现重复值.这应该由读取资源的应用程序负责管理."id"属性不属于任何命名空间.引用中的源数据元素应指向同一个资源内的某个属性.       


#### 1.12.3.2 资源间的引用    

资源内部的许多已定义的元素都会引用其他资源.通过这些引用,这些资源能够整合成医疗保健的信息网络.  
总是单向定义和标识引用-从源资源到目标资源.引用通过URL来标识,可能是绝对地址,也可能是相对地址.后面会继续讨论引用的解析.  

逆向关系逻辑上也存在从目标资源到源资源的逆向关系,但是在资源中没有明确表示.浏览这些逆向关系需要一些外部的架构来追踪资源间的关系([REST API](../impl/http.html)提供了这样的一种架构,通过对引用搜索变量的命名来[搜索](../impl/http.html#search)逆向关系)

由于资源是单独处理的,不能认为资源间的关系是具有传递性的. 比如,[Conidition](../clin/condition.html)资源引用了一个[patient](../admin/patient.html)作为对象,关联了一个[procedure](../clin/procedure.html)作为原因,并没有自动化规则或者说言外之意procedure的对象也是这patient. 反而,procedure的对象必须在procedure资源内明确指出. 另外一种方式是对象的语境并没有继承,也不会随着与procedure的关系而传递.这里仅有的例外在于是内嵌资源的情况.注意,在实践当中,关系必须要描述一个合乎逻辑和条理分明的记录。,在condition和procedure的案例中,常常要求对象是同一个病人,

在资源中，引用是用reference和文字描述来表示的。引用最关键的属性是 reference_——资源是通过URL来标识和寻址的。实际的引用长得像如下：
<pre class="spec">
&lt;<a title="A reference from one resource to another." class="dict" href="base-definitions.html#ResourceReference"><b>[name]</b></a> xmlns="http://hl7.org/fhir"&gt; 
 &lt;!-- from Element: <a href="extensibility.html">extension</a> --&gt;
 &lt;<a title="A reference to a location at which the other resource is found. The reference may a relative reference, in which case it is relative to the service base URL, or an absolute URL that resolves to the location where the resource is found. The reference may be version specific or not. If the reference is not to a FHIR RESTful server, then it should be assumed to be version specific. Internal fragment references (start with '#') refer to contained resources." class="dict" href="base-definitions.html#ResourceReference.reference"><b>reference</b></a> value="[<span style="color: darkgreen"><a href="datatypes.html#string">string</a></span>]"/&gt;<span style="color: Gray">&lt;!--</span>   <span style="color: brown"><b>0..1</b></span><span style="color: red">Relative, internal or absolute URL reference</span><span style="color: Gray"> --&gt;</span>
 &lt;<a title="Plain text narrative that identifies the resource in addition to the resource reference." class="dict" href="base-definitions.html#ResourceReference.display"><b>display</b></a> value="[<span style="color: darkgreen"><a href="datatypes.html#string">string</a></span>]"/&gt;<span style="color: html">&lt;!--</span> <span style="color: brown"><b>0..1</b></span> <span style="color: red">Text alternative for the resource</span><span style="color: Gray"> --&gt;</span>
&lt;/[name]&gt;
</pre>

![](../material/resourceReference.png)
另一种定义:资源规范([XML](ResourceReference.profile.xml.html),[JSON](ResourceReference.profile.json.html))    
注意:   
*  reference元素包含一个url,这个url可以是
      *  绝对的URL    
      *  相对的URL,相对于[根服务地址](../impl/http.html#root),或者是在bundle中相对于[bundle的语境](references.html#atom-refs)    
*  使用绝对URL是一种稳定的 可扩展的方式,适合于云端/web应用,而使用相对URL/逻辑引用是一种灵活的方式,适合于封闭式的系统间互相交换的情况     
*   尽管是首选方案,绝对URL不需要指向[ FHIR RESTful server](../impl/http.html).无论引用是否指向Restful的FHIR服务器,引用都应指向该标准中定义的某个资源.   
*   URL总是大小写敏感的.   
*   如果存在的话,display一般上和所引用资源的Resource.text的内容是不等同的.它的目的在于确定引用的是什么,而非完整的描述它.    


>约束  
>              
>*  **INV-1**:如果资源是內联的(xpath: not(starts-with(f:reference/@value, '#')) or exists(ancestor::a:content/f:*/f:contained/f:*[@id=substring-after(current()/f:reference/@value, '#')]|/f:*/f:contained/f:*[@id=substring-after(current()/f:reference/@value, '#')])),则必须有一个局部引用    


在一个restful FHIR服务器上通过"context"元素对病人"034AB16"的相对引用:
```
  <context>
    <reference value="Patient/034AB16" />
  </context>
```
通过"profile"元素对资源规范的绝对引用:
```
  <profile>
    <reference value="http://fhir.hl7.org/svc/Profilec8973a22-2b5b-4e76-9c66-00639c99e61b" />
  </profile>
```
注意 目前HL7还没有一个规范注册库,也没有一个确定的url.   
display元素中可以提供一个供人可读的资源标识    
```
  <custodian>
    <reference value="Organization/123" />
    <display value="HL7, Inc" />
  </custodian>
```
当系统无法解析对应的资源时,系统可以利用这些文字描述.         

####  1.12.3.3 内嵌资源        
在一些情况下,资源引用的内容并不是能够脱离资源本身而独立存在的-它不能够被单独的标识,也不可能有它独立的事务范围.一般而言,这种情况是由于原始数据的二手用户对资源进行了组装,比如中间件引擎.如果在构建资源时没有包含记录主键或者绝对标识信息,那么就不可能得到一个准确标识的资源,即使将其与任意的标识关联起来,这个资源也永远不能脱离引用它的资源的语境而成为某个事务的对象。 　　　　　　　
比如,当某个接口引擎要通过一条V2消息构建某个病人的一条[condition](../clin/condition.html)记录时,外科手术相关的仅有信息为她的姓名,如果没有可控的从业人员目录的话,就不足以创建一个可标识的[Practioner](../clin/practitioner.html)资源 -同名同姓的医务人员可能不止一个。 
在这样的情况下,资源是直接內联在资源内的.**当内容能够准确标识时就不必这么做 因为一旦标识信息丢失以后,是极难再次恢复的**                
An example of a contained resource:                     
```      
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
```                   　
The same example in JSON:            
```
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
```     
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
 #### 1.12.3.4 解析bundle中的资源引用       
 在处理bundle时,当遇到一个[资源引用](references.html#Resource),应用程序宜总是先在bundle中检索资源.          
 ##### 1.12.3.4.1 绝对引用       
 ```     
   <institution>
    <reference value="http://example.org/Organization/23" />
  </institution>
  <institution>
    <reference value="http://example.org/Organization/ex/history/2" />
  </institution>
  ```     
  这样应用程序宜查找bundle中的每个entry,看看entry.id或者entry.link与reference url匹配:      
  ```     
     .. feed ..
  <entry>
    .. 
    <id>http://example.org/Organization/23<id>
    .. 

    <content type="text/xml">
      <Organization xmlns="http://hl7.org/fhir">
         <!-- Content for the resource -->
      </Organization>
    </content>

  <entry>
    .. 
    <link rel="self" href="http://example.org/Organization/ex/history/2<"/>
    .. 

    <content type="text/xml">
      <Organization xmlns="http://hl7.org/fhir">
         <!-- Content for the resource -->
      </Organization>
    </content>
    xxx feed xxx

```     
在第二种情况下,匹配到资源的一个特定版本.应用程序宜核对entry.id和entry.link两项-只有其中之一能改匹配.如果资源引用不能够解析到bundle内部,应用程序宜能够通过提供的URL直接获取资源.如果不能的话,就必须使用其他方法来找到资源.      

注意 内部引用与其是literal URL,倒不如是URI,典型范例是[cid:URI在事务中的使用](../impl/http.html#transaction)         
##### 1.12.3.4.2 相对引用       
如果资源引用是一个相对URL,使用同样的基本原则:先尝试在bundle内部解析引用,然后再外面找.然而,在这些开始之前,首先要将相对URL转换成绝对URL,要实现这个,必须要指导逻辑上的服务根URL.这个值位于feed本身的叫"fhir-base"的link元素中      
```     
<feed xmlns="http://www.w3.org/2005/Atom">
  <link rel="fhir-base" href="http://example.org"/>
  <entry>
    <id>http://example.org/Organization/23<id>
    .. 
    <content type="text/xml">
      <Organization xmlns="http://hl7.org/fhir">
         <!-- Content for the resource -->
      </Organization>
    </content>
  <entry>
    .. 
    <link rel="self" href="http://example.org/Practitioner/example"/>
    .. 
    <content type="text/xml">
      <Practitioner xmlns="http://hl7.org/fhir">
         <!-- Content for the resource -->
           <institution>
             <reference value="Organization/23" />
           </institution>
         <!-- Content for the resource -->
      </Practitioner>
    </content>
    xxx feed xxx
```     

当应用程序遇到引用"Organization/23"时,首先查找"fhir-base"URL,也就是http://example.org.[根服务URL中结尾处没有斜线](../impl/http.html#root),    这样应用程序在这二者之间添加一个"/",绝对地址也就是 "http://example.org/Organization/23",   这样就可以在bundle中解析了.注意:JSON格式的bundle方法是一样的.      

为了让相对URL能够正确处理,如果bundle中任意资源存在相对引用,bundle link元素中应该有一个"fhir-base"的link.            


注意:应用程序不宜假设服务根地址实际上是可以解析的.一些情况下,它是的.如果执行一个检索或者history操作,从某个服务器上得到一个bundle,那么服务根URL宜与客户端使用的匹配.然而,在其他情况下,bundle自身是从数据源向其他交换时,或者是独立的作为一个实体存储时(例如临床文档), 服务根url就只是在解析资源时bundle内部的一个逻辑构件,脱离了bundle则毫无意义.     

 &copy; HL7.org 2011 - 2014. FHIR DSTU (v0.2.1-2606)构建于2014  7月2号 16:29+0800 星期三 . 
链接：[试行版是什么](http://hl7.org/implement/standards/fhir/dstu.html) |[版本更新情况](http://hl7.org/implement/standards/fhir/history.html) | [许可协议](http://hl7.org/implement/standards/fhir/license.html) |[提交变更建议](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemAdd&tracker_id=677)      