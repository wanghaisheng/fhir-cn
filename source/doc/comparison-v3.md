title: 
date: 
categories: doc
---

  [首页](../home/index.html) >[文档](documentation.html) >>[比较](comparison.html) > **V3消息**	


 [比较](comparison.html) >[V2消息](comparison-v2.html)>**V3消息** > [CDA](comparison-cda.html) > [其他](comparison-other.html) 

###  1.26.2  HL7 Version 3 (and ISO 21090)


HL7 V3 (V3)是新一代的HL7消息标准。它引入了一个通用的参考信息模型RIM，数据类型模型和词汇集合以及一个正式的标准开发方法学。另外，它引入了”文档“，作为消息架构的一种补充来实现卫生保健信息的共享
(参考 [与CDA的比较](comparison-cda.html)).  尽管名义上涵盖了这些所有内容，但是“V3”这个词一般用来指代 &quot;V3 消息&quot;. 数据类型是V3的基础，已经被ISO采用，也就是ISO21090. HL7 RIM也已经被采纳为ISO标准。  
很多大型项目中都采用了V3 消息，尤其是在电子健康档案领域，尽管它的市场占有率还是不及HL7 V2.  HL7 RIM 和ISO 21090 数据类型也已经被其他那些没有完全使用V3方法学的SDO和项目采纳。这里所提到的大多数评论和建议也都适用于基于V3的解决方案。   
#### 1.26.2.1  与V3的异同
1、**参考模型:**  HL7 RIM的使用是HL7 V3方法学的核心，也是整个标准和wire format/传输格式的核心。V3实例中的所有数据元素都继承自RIM或者是ISO数据类型。在 FHIR里面, 大多数资源和数据类型元素也是这样，但不尽然。一些资源 ([Profile](../infra/profile.html), [Conformance](../infra/conformance.html), [ValueSet](../infra/valueset.html), etc.) 的内容超出了 RIM的范围.  在很少的一些情况下，FHIR中对那些V3数据类型模型中还不支持的数据类型进行了调整。我们期望在V3数据类型模型的下一个版本会支持这些变更。 FHIR传输格式的主要差异不是因为与RIM的映射。 这样使得实例更加简洁直观，这样就可能导致在完全不了解HL7 RIM情况下也可以实现FHIR.    

2、**编码:**  V3中依赖可编码属性来表达实例的含义。包括classCode、moodCode、determinerCode等。这些属性的允许值受HL7严格管控。FHIR中也有一些属性，其编码受限于FHIR中定义的内容——这些使用 [code](datatypes.html#code) 数据类型. 然而，这些只限于拥有业务含义的属性——   status, contact types等.

FHIR 和 V3 都利用值集来定义在某些特定场景下属性可用的编码集合。然而，在FHIR中，一个  [ValueSet](../infra/valueset.html)仅仅是一种资源，意味着它可以是某个实例的一部分，就跟数据的其他部分一样来传输(T这点和[Profile](../infra/profile.html), [Conformance](conformance.html) 以及其他元资源一样)     

3、**粒度 &amp; 引用:**  HL7 V3 模型分为三大类  - 封装层、消息负载和通用的消息元素类型(CMET), 这些组合起来形成交互，定义了通信的内容。在一些情况下，这些模型的粒度与FHIR资源完全一致，但也不总是这样。 V3模型是按照复用来划分的。FHIR模型是按照其所表达的对象是否能看做“单独的"对象来划分.在HL7 V3中，可以用众多模型来表达卫生保健的同一个基本构件。比如，在HL7国际层面上，有10种不同的CMET来表达 &quot;Patient&quot;的概念.  另外，一些负载模型也会直接表示患者而没有使用CMET。其他的差异也存在于其他HL7成员和开发人员所定义的V3模型.这些不同的CMET每个都有自己的schema，可能会使用不同的元素名称，不同的嵌套层次和不同的约束 . 对于FHIR而言，只有一个 [Patient](patient.html) 资源. 可以根据整个资源创建多种规范，但是它们都会使用同样的schema和同样的传输格式。    

4、**Design by constraint:** V3设计的方法学是  &quot;design by constraint&quot;中的一种。原理在于任何一种卫生保健的通信所需要的所有数据都表达在HL7 RIM之中。 其他所有数据模型只是简单的约束RIM来表达特殊领域的需求。国际层面上是这样，某个国家、项目或者某些开发中又会进一步进行精细化。当模型越来越贴近开发人员，它们就变得更加不那么抽象。这就导致有一种倾向，V3模型在涵盖范围和功能上极为广泛，也有一定的抽象性。They need to be in order to ensure that all possible implementations in the space covered by that model can be proper constraints on it.  同样的，每个模型都会产生自己的schema，大多数情况下，约束后的schema不是那么严格兼容未经约束的模型的schema。   

FHIR中采用了不同的方法。FHIR 资源并没有想要表达某个领域可能会用到的所有数据元素，相反，只有那些会被大多数实现所使用的元素才会被视为核心资源定义的一部分。(这有时候称之为”80法则“- 如果使用这种资源的80%的系统都有整个元素，那么它就是核心元素。).  其他所有数据元素都通过扩展来处理。使用[Profiles](../infra/profile.html)来为某个更细的领域约束资源和定义扩展。某个资源的传输格式的互操作性就能够在所有规范中保持。

5、**语境传递:**  当在人之间传递卫生保健信息时，很多数据可以从语境中推理而出。比如，一份报告的封皮上有一个&quot;author&quot; 签名, 自然而然的会人为报告中每条陈述都是经过此人授权的。当需要计算机分析数据时，不论是查询、决策支持还是其他分析，这种推理就变得极为挑战， 因此，HL7 V3方法论中提供了三种不同的机制来使得数据模型能改定义语境如何在模型间传递， 明确地告诉计算机,人们一般是如何理解的。
FHIR 选择了不同的方法，在FHIR里面，任何语境都不能传递——一切都是明指。如果患者的一份报告包含了针对这个患者的100个观察，每个观察都要包含对整个患者的一条引用。然而，这样也很痛苦，因为引用仅仅是一个id,可能还有一个简短的展示值。这种方法的一个好处在于每个资源的使用都很安全，毋须考虑资源中所传递的语境。每个资源实例的含义都是自包含的。

6、**空值:** 在卫生保健领域，数据不知道、不可用，异常值或者落在正常值范围之外是很常见的。为了处理这种情况，V3引入了"空值"的概念，几乎模型中所有属性和数据类型的属性都有。这些可编码的空值可以代替属性、关联和数据类型的属性的数据或者附加在数据中。例子包括 &quot;Unknown&quot;, &quot;Not asked&quot;, &quot;Positive infinity&quot;, &quot;Trace amount&quot;, &quot;Masked&quot;, &quot;Other&quot;, 等.  除非元素明确标记为&quot;mandatory&quot; - 也就是说不允许任何空值存在，这些空值可以在其他任何地方使用。 

FHIR以完全不同的方式来处理这个问题。只有大多数系统需要的时候才会在核心标准中引入.  需要的话,只需要约束该元素相关的.Where needed, the flavors are constrained to those relevant to that element.     

####  1.26.2.2   基于V3实现互操作性需要考虑的因素


1、**使用 RIM 映射:** 大多数资源元素和数据类型属性包含了与RIM的映射.这些映射有2个目的,它们是用HL7的参考模型来辅助定义FHIR的语义,确保工作组所定义的数据元素能够对其有良好的、一致的理解.同样也能为V3标准的开发人员提供帮助,它们可能会想要迁移或者做V3与FHIR之间的映射.  RIM是一种语言,它能供让同样的想法能够以不同方式、不同表达能力来传输．因此完全有可能一个RIM元素对应到一个FHIR核心元素上，即使它的RIM表达形式与映射中的可能不同 。另外，不是所有V3模型都遵循了良好的建模实践，因此不能良好表示的一些数据元素可能会对应不到FHIR元素上去。因此，RIM映射应看做一个指导，不是绝对的，映射应该针对实际所使用的V3标准。 (同时参见下面的 [抽象模型](#V3-abstractModels) .)

2、**V3 中的扩展:**  尽管V3方法学的核心是 &quot;design by constraint&quot;, 仍然提供了扩展——要么是外部的命名空间，要么是一个特殊的属性。当在V3与FHIR之间转换时，应该考虑这些扩展的使用。   一般来说，大多数V3扩展对应到FHIR扩展，就像V3 design-by-constraint 的设计原则中所推荐的那样，FHIR中的核心部分已经是V3基础标准的一部分。   

3、**抽象模型  :**  如上所述，HL7国际层面上创建的很多V3模型都是很抽象的。因此，这些模型可以用多种不同方式来表达多种场景。这使得这些标准与FHIR之间的映射就会很棘手。对于使用的V3 &lt;-&gt; FHIR 互操作性，需要在消息标准、实现规范或者模板这些更加具体更加贴近开发的层面上进行映射。比如，把CDA模型与FHIR进行映射就很困难，因为CDA模型本身拥有极强的表达能力，然而，CCDA模板与FHIR之间的映射是有可能的。
**语境传递:** 如上所述， HL7 V3 依赖于语境传递——要么是显式的要么是隐式的。当转换成FHIR时，语境需要转移到每个资源中去。 

4、**更新模式:** 在HL7 V3实例中，与FHIR的方法类似，更新一般是通过快照模式来处理的——如果任何信息发生变化，发送整条记录，包括了已经修改的数据元素。然而，V3方法学支持了 引入&quot;updateMode&quot; 来实现只是发送实例的全部和部分。每个用 updateMode 标记的重复元素来标识该元素是否是要新增的、移除的还是更新的等等。另外，updateModes 还能提供除了更新之外的空值，跟前面 [V2 对比](comparison-v2.html#V2-updateMode) 一样,需要开发人员生成每个资源的完整快照或者引入扩展修饰符来提供类似V3的机制。    

5、**额外的考虑因素:**  大多数FHIR与V2之间互操作性要考虑的注意事项适用于FHIR与V3之间。特别是 : [扩展](comparison-v2.html#V2-extensions), [独立 vs. 内嵌资源 resources](comparison-v2.html#V2-contained), [资源标识](comparison-v2.html#V2-identification), [引用和资源的合并](comparison-v2.html#V2-merging) 以及 [生成人可读的内容](comparison-v2.html#V2-humanReadable).

&copy; HL7.org 2011+. FHIR DSTU (v0.5.0-6346) generated on Tue, Aug 18, 2015 03:54+0000\.  
  链接：[试行版是什么](http://hl7.org/implement/standards/fhir/dstu.html) |[版本更新情况](http://hl7.org/implement/standards/fhir/history.html) | [许可协议](http://hl7.org/implement/standards/fhir/license.html) |[提交变更建议](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemAdd&tracker_id=677)

