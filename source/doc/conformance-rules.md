title: 
date: 
categories: doc
---		

[首页](../home/index.html) >[文档](documentation.html) >[资源定义](resources.html) > **一致性**
### 1.12.1  一致性 

资源内容和表达它们的格式必须遵循该标准中所描述的规则，标准中叙述性文本中的定义以及如下的一致性属性中的约束。   
注意：该标准使用[RFC2119](http://www.ietf.org/rfc/rfc2119.txt)中定义的一致性动词SHALL应/应该/必须、SHOULD宜、MAY可/可能。  

由于其通用性和应用范围很广泛，一般而言，该标准中的规则是很宽松的。因此，由于不同的应用程序之间使用可选特性的不同，该标准可能会使得不同的应用程序无法进行互操作。为了能够然引用程序能改处理这种清空，FHIR提供了一个一致性层， 开发人员和国家/区域性项目可以用来以一种计算机可处理的方式来声明如何使 用资源和交换模式来解决它们的应用场景。该一致性层自身是通过使用[Conformance](../infra/conformance.htm) 和 [Profile](../infra/profile.htm)资源来实现的。 
<table class="grid"> <tr> <td><a href="../infra/valueset.html">值集</a></td> <td>定义了一些可编码值的集合(参考 &quot;<a href="../infra/terminologies.html">如何使用字典</a>&quot;)</td>  </tr> <tr> <td><a href="../infra/profile.html">Profile</a></td> <td>如何在特定场景中使用资源和其数据项的规则.其中对于资源中的可编码项，规范会引用值集。</td>  </tr> <tr> <td><a href="../infra/conformance.html">一致性</a></td> <td>应用程序所提供的或能够使用的资源的种类和对应的操作。该资源会引用一些资源规范来描述该程序所用到的资源</td>  </tr></table>

该标准也提供了很多工具，技术上能改遵循该标准的一致性：

*   [Schema &amp; Schematron](../material/fhir-all-xsd.zip)    
*   [Validator Package](../material/validation.zip)    
*   [Reference Platforms](../impl/downloads.htm#refimpl)     

注意 所有这些都无法检测对该标准的所有一致性约束。  

资源中定义的数据元和数据类型有3个与一致性直接相关的属性：Cardinality, Is-Modifier, Must-Support。它们相互结合，确定实现中的一致性需求。   



####1.12.1.1  基数    

所有FHIR中定义的元素，基数是在其定义的一部分-必须出现的最小次数和最大次数。该数字规定了在某个类型的资源实例中某个元素可能出现的次数。该标准中只定义了如下几种类型的基数： 0..1, 0..*, 1..1, 和 1..*。描述特殊应用场景的规范可能会在资源所定义的基数限制范围内使用其他的一些值。   

注意：如果出现 元素就不能为空-它们必须要么包含一个value属性 、要么包含一个子元素或者是扩展。   


该标准中鲜有元素的基数中最小出现次数为1.资源可以用在多种场景下，除了那些主要的应用场景， 有时候甚至连基本信息都是不完整的。出于这个原因，基数中最小出现次数为1的是包含在其中的对元素的理解很必要的那些元素。基数中的最小出现次数不应视作在使用资源的任意特殊场合应该出现的指南。 该标准可能会发布一些针对某个场景的规范，其中会定义哪些元素必须出现，或者由某个区域、供应商或项目发布这样的规范。  


对于那些基数&gt;1的元素，它们出现的次序也许是有含义的。除非元素定义(在该标准或扩展)中明确定义了次序的含义，我们认为次序是无意义的，在实现中是允许重新对元素排序的。注意 在规范中,你是不能定义元素出现次序的含义的。当没有定义次序的含义时，在实现中 ，针对某种用途 ，必须依据所重复的元素内容的语义,从元素集合中选择一个元素。规范和实现指南常常可对这个选择的过程作出约束。

####1.12.1.2  Is-modifier    

Is-Modifier是一个布尔型属性，不管是作为该标准中基础资源的一部分还是规范中声明扩展的一部分，当定义了一个元素时，就给它分配一个。如果一个元素所包含的值会改变其他元素的解释 或者改变整个资源的解释时，我们就把它标记为&quot;Is-Modifier = true&quot;典型地，会有这样标记的元素有&quot;status&quot;, &quot;active&quot;, or &quot;certainty&quot;如果在[资源规范](../infra/profile.html)中描述了使用该元素时Is-Modifier的值是否无法更改。一旦某个元素被标记成Is-Modifier，文档中就必须明确说明为什么它是一个修饰符，和/或该元素修饰的是那些元素。
modifier元素的典型实例是 对包含它的元素的否定。例如，如下的元素定义
<pre class="spec">&lt;<a title="Specific reactions to a substance." class="dict" ok="true"><b>AdverseReaction</b></a> xmlns=&quot;http://hl7.org/fhir&quot;&gt;
 &lt;!-- Other information --&gt;
 &lt;<a title="When the exposure occurred." class="dict" ok="true"><b>exposureDate</b></a> value=&quot;[<span style="color: darkgreen"><a ok="true">dateTime</a></span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown"><b>0..1</b></span> <span style="color: navy">When the exposure occurred</span><span style="color: Gray"> --&gt;</span>
 &lt;<a title="Substance(s) that is presumed to have caused the adverse reaction." class="dict" ok="true"><b>substance</b></a>&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown"><b>0..1</b></span> <span style="color: darkgreen"><a ok="true">Resource</a>(<a ok="true">Substance</a>)</span> <span style="color: navy">Presumed to have caused the reaction</span><span style="color: Gray"> --&gt;</span>&lt;/substance&gt;
 &lt;<a title="To say that a reaction to substance did not occur (this element modifies the meaning of other elements)" class="dict" ok="true"><span style="text-decoration: underline"><b>didNotOccurFlag</b></span></a> value=&quot;[<span style="color: darkgreen"><a ok="true">boolean</a></span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown"><b>1..1</b></span> <span style="color: navy">To say that a reaction to substance did not occur</span><span style="color: Gray"> --&gt;</span>
 &lt;!-- Other information --&gt;
&lt;/AdverseReaction&gt;
</pre>

 &quot;didNotOccurFlag&quot;元素影响了整个资源的含义，如果它是true的话，对整个资源的理解就会完全不同，因此对于实现而言，忽略该元素是不安全的。    
一般而言，被标记成&quot;Is-Modifier = true&quot;的元素的基数的最小出现次数也是1，为的是在处理的时候引入确定性。如果在实例中这样一个元素的值是不明确的，或者不能从语境中得知，我们就不能安全准确地理解这个资源。无论基数的最小出现次数，在构建资源的实现中必须确保isModifier元素有恰当的值。isModifier元素必须在资源的叙述性的摘要中表示。


实现在处理资源中数据的时候，应能够理解在使用数据时这些元素产生的影响。不要求实现中以任意方式支持这些元素-通过拒绝那些包含超出它们所支持的值之外的实例，可以达到这样的目的(比如，应用程序可能拒绝接收 reliability != "ok"的observation)。另外，根据它们的实现环境，实现可能要确保这样的值永远不会出现。然而 不论值是什么 ，应用程序总是宜核实它。
注意 对资源的数据进行处理，一般而言意味着将数据从资源中复制出来或过滤出来，用在另外的场景中(展示给用户，决策支持，以其他格式来进行交换或者是存储)。服务器和移动资源的后台处理过程并不是在处理资源中的数据，这些应用程序不必检测那些未知的扩展。   


#### 1.12.1.3 Must-Support     

如果元素标记为Must-Support，意味着使用或生产资源的实现中必须以某种有意义的方式提供对该元素的支持。究竟该怎么来理解 不是FHIR标准的一部分所能描述和阐述清楚的。

鉴于此，标准中并未将任何元素标记成must-support。这在[资源规范](../infra/profile.htm)中完成，其中将一些元素标记为mustSupport=true。当在规范中这样规定了之后，由于它有多种解释，它也要明确说明需要提供那些支持。   

注意拥有IsModifier属性的元素并不是一个核心元素(如使用资源的重要元素之一)，也不是说自然而然地它就是mustSupport-然而对于除了IsModifier元素的其他元素而言 这两样的可能性更大。


 &copy; HL7.org 2011 - 2014. FHIR DSTU (v0.2.1-2606)构建于2014  7月2号 16:29+0800 星期三 . 
链接：[试行版是什么](http://hl7.org/implement/standards/fhir/dstu.html) |[版本更新情况](http://hl7.org/implement/standards/fhir/history.html) | [许可协议](http://hl7.org/implement/standards/fhir/license.html) |[提交变更建议](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemAdd&tracker_id=677) 	 		