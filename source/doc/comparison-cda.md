title: 
date: 
categories: doc
---

  [首页](../home/index.html) >[文档](documentation.html) >>[比较](comparison.html) > **CDA**	


 [比较](comparison.html) >[V2消息](comparison-v2.html)> [V3](comparison-v3.html)>**CDA** >[其他](comparison-other.html) 

### 1.10.3  Clinical Document Architecture (CDA)



CDA是HL7应用最广泛的V3标准。它提供了一个标准化的头，头中包含了文档相关的元数据， 用不同的章节来表达不同的临床相关内容。文档可以使未编码的，如PDF，也可以是全编码的如V3实例。  需要注意的是：在FHIR中可以用Composition Resource](../infra/composition.html)来构建 [文档](../impl/documents.html) ，也能够用[DocumentReference](../infra/documentreference.html) 来传输传统的CDA R2文档.
 
####  1.10.3.1 与CDA的异同

1、**临床文档的关注点:**  正如它的名称所暗示，临床文档架构仅限于“临床”的场景。CDA模型不支持那些与临床无关的内容的交换，诸如财务信息，所处理的文档也只是和病人相关的哪些。(在一些情况下，诸如HL7结构化产品标签标准——不是针对病人的类似CDA标准，就是为了解决此类局限性的)。FHIR文档在内容上没有限制，对象可以是病人之外的其他。 

2、**人可读的方式:** CDA 和 FHIR都要求内容是可以供人读的，定义了这些文本如何展现的规则。一点细微的差异在于在CDA里面，供人读的部分是为章节所定义的，而FHIR中为章节所归属的资源所定义的。然而，从效果上来看上并没产生什么实际的差异。另外一点不同在于，对于FHIR而言，供人可读的特性不局限于文档—— 是受资源自身影响的，如果一份文档引用了现有的资源，这样可能会导致在渲染方式可能会有那么一些不太灵活。  

3、**临床声明 vs. 资源:** 在CDA中In CDA,  文档 &quot;内容&quot; 是通过一个基于HL7 &quot;临床声明&quot;项目的高度复杂和极其抽象的模型来表达的。它的目的在于使得开发人员能够在任意的粒度和严密性上表达任意的临床概念。(实际上，CDA模型有一些内在的局限性，导致要表达某些临床概念就很困难) 。这个模型很强大，也存在一些挑战。首先需要精通RIM建模才能给够表达任意的临床信息。
 如何非常好的表达像过敏、手术、血压等是不那么明显。要支持互操作性 必须要用到模板。其次就是不同情况下通用的临床概念的模型各异。在FHIR里面，消息中所有临床(非临床)内容都通过引用现有资源定义来处理。这些资源使得FHIR能够很好的表达像过敏、血压等通用结构 , 确保核心内容只有一种唯一的表达方式。然而 它的局限性在于为了共享内容必须定义好一个恰当的资源。在开发FHIR的初级阶段，如果还没有定义好一个合适的资源，[Other](other.html) 资源可能是最好的选择。   

4、**模板和规范 :** 如上所述，为了理解实例的含义，CDA必须依赖于模板的存在。(理论上而言，查看RIM的属性和编码就能确定含义，事实是这通常是不安全的或者不足够的，因此，基本上每个CDA实例里面到处都会包含templateId属性来定义含义)。 在FHIR中，含义是通过资源来定义的。
可以用 [Profiles](../infra/profile.html)来定义扩展，但它永远不能重新定义核心元素的含义。尽管当使用规范来构建一个特殊实例的时候，可以在实例中使用[tags](extras.html#tag).来声明此规范。 但这种声明并不是必须存在的。   

5、**标记语言:** CDA为叙述性文本定义了自己的XML语法，基本上是基于XHTML，某种程度上，XHTML比HTML表达能力要强一些。 FHIR使用了XHTML的一个约束集，它比CDA中的标记语言 FHIR makes u表达能力更强。 从FHIR转换成CDA需要考虑这些约束(或者提供一份完整的已渲染过的文档版本)  

#### 1.10.3.2 基于CDA实现互操作性需要考虑的因素  

CDA是V3标准的一种。因此，所有[V3中的注意事项](comparison-v3.html#V3-interoperability)适用于V3消息的也同样适用于CDA。另外，以下的部分只是针对CDA的实现。   

1、**映射哪些内容:**CDA模型右边的一部分(临床内容)是[上述的一种抽象模型](comparison-v3.html#V3-abstractModels).  尽管CDA头可以对应到FHIR的 [Composition](composition.html) 和相关资源，FHIR与CDA的对应应该是在模板层面上而不是CDA标准自身上。  

2、**人可读部分的粒度:**  对于FHIR而言，叙述性文本只存在于每个章节根部的资源里面，对于CDA而言，叙述性文本存在于每个章节。通常这意味着CDA和FHIR中的叙述性文本是相一致的。 然而，在一些情况下，一个章节会包含一些子章节。CDA中这些嵌套的章节也可以有叙述性文本.在FHIR里面，它们就不能有叙述性文本。 在转换的时候，应用程序需要一些其他的管理办法。     

3、**叙述性文本与特定元素间的关联:**  为了保证语义上的可追踪性，FHIR和CDA都允许在叙述性文本和文档中可编码部分特定的离散元素组件建立关联。如果FHIR与CDA之间进行转换，也需要转换这些链接。然而，这是很复杂的，事实上，两个标准关联的粒度是不同的。 在CDA中，关联只能存在于章节的层面上或者是一组条目的层面上。对于FHIR，关联可以存在于任何层面上，包括单独的数据类型组件或者甚至是扩展的一部分。从CDA到FHIR的转换是单向的，然而，反向转换总会有信息损耗。  


&copy; © HL7.org 2011+. FHIR DSTU (v0.5.0-5149) generated on Fri, Apr 3, 2015 14:36+1100\.  
  链接：[试行版是什么](http://hl7.org/implement/standards/fhir/dstu.html) |[版本更新情况](http://hl7.org/implement/standards/fhir/history.html) | [许可协议](http://hl7.org/implement/standards/fhir/license.html) |[提交变更建议](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemAdd&tracker_id=677)