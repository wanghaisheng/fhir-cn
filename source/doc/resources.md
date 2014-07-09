title: 
date: 
categories: doc
---		

[首页](../home/index.htmll) >[文档](documentation.htmll) > **资源定义**
### 1.12.0 资源定义   
该标准中定义了一系列不同类型的资源，可以用来交换或存储数据，以此来解决很多卫生保健领域相关的问题，不论是行政管理上的还是临床上的．另外，该标准还定义了很多交换资源的不同方法．

一个资源，也就是一个实体　拥有如下特点：

*   拥有一个可寻址的标识　　
*   自身是该标准中所定义的某种资源类型　　
*   包含诸多在资源定义中所描述的结构化数据项　　
*   包含一种供人可读的对资源内容的XHTML的表达形式　
*   可能随着时间而发生变化　　

资源有多种表达形式。如果能满足上述条件，依据标准中定义的规则，不管是XML还是JSON ，我们都认为是一个有效的资源，也允许其他的表达形式 ，但该标准中并未描述。　　

##### 1.12.0.0.1 定义　　
<table class="grid"><tr> <td>资源</td> <td>存储或交换的数据实例</td> </tr><tr> <td>资源定义</td> <td>定义资源所包含的数据项</td> </tr> <tr> <td>规范</td> <td>本身可以关于某个应用场景的对数据项的额外描述，用一种特殊的资源[规范](../infra/profile.html)来表达．</td> </tr></table>   

####1.12.0.1 资源的内容   
所有资源都拥有如下数据项和属性，可能是可选的　也可能是强制存在的:

*   针对某个类型的一些定义好的基础数据元。　　
*   [Extensibility](extensibility.htm))——实现中会另外添加的一些数据元　　　
*   [人可读的资源内容的文本描述](narrative.htm#Narrative)　　
*   [内嵌资源](references.htm#contained) - 作为该资源标识和事务相关范围一部分的其他资源　　
*   [元数据](resources.html#metadata)——不是资源内容模型的一部分 但是是资源的一些重要信息。　
*   [标签](extras.html#tags)——可能用来定义 如安全性、工作流等额外动作的资源标签   
每个资源都是从公用数据项开始的(对于这种格式的相关文档，参考[资源定义格式](formats.html))     

<pre class="spec">
&lt;<a title="A Resource Definition for FHIR" class="dict" href="#content"><b>[Name]</b></a> xmlns=&quot;http://hl7.org/fhir&quot;&gt;  
 &lt;<a title="See Extensions" class="dict" href="extensibility.html"><b>extension</b></a>&gt;<font color="Gray">&lt;!-- <font color="brown"><b>0..*</b></font> </font> <font color="darkgreen"><a href="extensibility.html">Extension</a></font>   <a href="extensibility.html"><font color="navy">See Extensions</font></a> <font color="Gray"> --&gt;</font>&lt;/extension&gt;
 &lt;<a title="See Extensions" class="dict" href="extensibility.html"><b>modifierExtension</b></a>&gt;<font color="Gray">&lt;!-- <font color="brown"><b>0..*</b></font> </font> <font color="darkgreen"><a href="extensibility.html">Extension</a></font>   <a href="extensibility.html"><font color="navy">See Extensions</font></a> <font color="Gray"> --&gt;</font>&lt;/modifierExtension&gt;
 &lt;<a title="The base human language of the resource content. The value can be any valid value following BCP 47" class="dict" href="base-definitions.html#Resource.language"><b>language</b></a> value=&quot;[<span style="color: darkgreen"><a href="datatypes.html#code">code</a></span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown"><b>0..1</b></span> <span style="color: navy">Human language of the content (BCP-47)</span><span style="color: Gray"> --&gt;</span>
 &lt;<a title="Text summary of resource content, for human interpretation" class="dict" href="narrative.html#Narrative"><b>text</b></a>&gt;<font color="Gray">&lt;!--</font> <font color="brown"><b>0..1</b></font> <font color="darkgreen"><a href="narrative.html#Narrative">Narrative</a></font> <font color="navy">Text summary of resource content, for human interpretation</font><font color="Gray"> --&gt;</font>&lt;/text&gt;
 &lt;<a title="See Contained Resources" class="dict" href="references.html#contained"><b>contained</b></a>&gt;<font color="Gray">&lt;!-- <font color="brown"><b>0..*</b></font> </font> <font color="darkgreen"><a href="references.html#contained">Resource</a></font>   <a href="references.html#contained"><font color="navy">Contained Resources</font></a> <font color="Gray"> --&gt;</font>&lt;/contained&gt;
 <font color="Gray">&lt;!-- Defined Data Elements for Resource --&gt;</font>
&lt;/[Name]&gt;
</pre>

这些元素的出现顺序必须是这样子的。为了保证schema和UML衍生的代码定义的一致性，首先要考虑到的是所有资源都共同拥有的这些元素。  

可选的language元素规定了资源所使用的语言，使用[BCP 47中定义的编码](http://tools.ietf.org/html/bcp47)。注意：并非资源的全部内容都必须使用这种语言。如果规定了使用的语言，在[叙述性文本Narrative Text](narrative.htm#Narrative)中也应该规定。   

language元素是用来支持索引和访问的(如文本-语音中使用了language标签)．当处理叙述性文本的时候，会用到叙述性文本中的html language标签。资源中的language标签是用来规定从资源中的数据中所生成的其他表达方式应使用的语言。

#### 1.12.0.2 资源的元数据　　　



The metadata properties are key aspects of a resource and how it behaves　出于实现的考虑，它们表达在资源之外。　

<table class="grid"> <tr><th>元数据项</th><th>类型</th><th>用途</th></tr><tr><td>逻辑ID</td> <td>[id](datatypes.htm#id)</td> <td>字符串形式的资源逻辑标识符。在同一个服务器的同样类型的所有资源中，它是唯一的．在这个服务器上该资源的整个生命周期中都是固定不变的</td></tr><tr><td>版本ID</td><td>[id](datatypes.htm#id)</td><td>随着资源内容变化而改变。可在[resource reference](references.htm#Resource)中进行引用。用作保证每次更新都是基于最新的版本。版本号可以是全球唯一的，也可以是逻辑ID的范围内唯一。它们常常是一个逻辑ID范围内的渐增ID，要么是UUID，尽管并未对这些方法作出要求</td></tr><tr><td>最后更新日期</td><td>[instant](datatypes.htm#instant)</td><td>随资源内容变化而改变。某个系统或人可以用其来判断资源内容是否为最新</td></tr></table>

逻辑标识符和版本标识符都是大小写敏感的．Id总是不透明的，任何系统都不应该也不需要去确定它的内部结构．在资源引用里，ID的表达方式应该总是一样的．Id最长可以是３６位，可以包含任意组合的ASCII字符、数字、 &quot;-&quot; 和 &quot;.&quot;
注意:这些数据元不包含在资源里面是因为:
*   在传输内容的封装层,它们几乎总是显式存在的,特别是在http和atom的头部
*   当对资源管理、移动或复制时,甚至内容本身没有变化时(尽管改变了资源的逻辑标识符,对应引用它的其他资源的内容可能需要改变),它们都会发生变化.   

一个资源完整标识是一个绝对的URL,由服务器负责构建,表明可以在何处找到它、资源类型、逻辑标识符,比如http://test.fhir.org/rest/Patient/123 (123 就是逻辑标识符).注意实现中不应假设资源的标识总是可以指向某个服务器-可能暂时不可用,或者由于政策不可访问(GFW防火墙)或者是其他一些原因,也可能实际上就不存在(比如脱离了RESTFUL环境来使用资源).资源间通过标识来互相引用.则些引用可以是绝对地址或者相对地址(更多信息参考[资源引用](references.html)).从一个服务器向另一个服务器复制或移动资源意味着资源需要一个新的标识.更多详细信息请参考[资源标识的管理](../impl/managing.html)


只要资源发生变化 版本id和最后更新日期都会变化。由于相关的日期时间固有的不准确性和精度限制,版本id对于管理并发问题和特殊版本引用问是很有用的。最后更新日期对于人确定资源中的信息是否最新而言是有帮助的。  

在任何使用资源的场景中，都需要解决如何表达这样的一些元数据的技术细节。更多信息请参考[在服务中使用资源](../impl/services.html))


####1.12.0.3 版本内的兼容性    
> 一旦该标准完全成为正式标准,以下规则就都适用。这些规则保证了是用来不同版本FHIR的应用程序间交换数据时，不同的实现可以安全的处理资源的内容。然而，在该标准试运行阶段，HL7可能会对除了这里所描述的缺陷作出更改以响应发现的问题。应用程序可能会使用[资源标签](extras.html#tags)来辅助管理     

资源内容里没有显式的版本记号。一旦成为正式版标准，该标准的随后版本可能会在资源内容的某个部分引入一些新的元素或内容，但是已有资源的含义和路径不会发生变化。任意的值集和编码集可能会被修订以包含额外的编码。  

与某个值集或编码系统的绑定表示值集是否会随着新代码的定义而自动增长，是否在以后版本的标准中集合会被扩展，或者在以后的版本里该集合永远不会发生变化。   

一致性层([Conformance](../infra/conformance.html)和[Profile](../infra/profile.html))里包含了强制性存在的属性，其中声明了对应的FHIR标准的版本，可以用以确定开发所使用的FHIR版本。   

在典型的场景中，可能会出现多个版本并存，因此，除了modifierExtensions，应用程序应忽略那些它们所无法识别的元素。然而，在医疗场景中，由于临床安全和技术局限性的原因，很多应用程序供应商不乐意考虑这种方法。对于应用程序是否忽略未知元素不做要求，但是应道在它们的[一致性声明](../infra/conformance.html)事先声明。  
更多有关版本间兼容性问题的讨论请参考：http://wiki.hl7.org/index.php?title=FHIR_interversion_compatibility   

##### 1.12.0.3.1 额外信息

*   [一致性声明规则](conformance-rules.html)    
*   [资源定义](resources.html)     
*   [标签, Bundles, Compartments](extras.html)   
*   [资源间的引用](references.html)    
*   [叙述性文本](narrative.html)    
*   [格式:](formats.html) [XML](xml.html), [JSON](json.html)     
*   [扩展](extensibility.html)    
*   [实例](extensibility-examples.html)    
*   [正式定义](base-definitions.html)     

 &copy; HL7.org 2011 - 2014. FHIR DSTU (v0.2.1-2606)构建于2014  7月2号 16:29+0800 星期三 . 
链接：[试行版是什么](http://hl7.org/implement/standards/fhir/dstu.htmll) |[版本更新情况](http://hl7.org/implement/standards/fhir/history.htmll) | [许可协议](http://hl7.org/implement/standards/fhir/license.htmll) |[提交变更建议](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemAdd&tracker_id=677) 	 		