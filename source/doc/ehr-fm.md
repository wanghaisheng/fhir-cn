title: 
date: 2014-05-20 15:13:12
categories: doc
---		

[首页](../home/index.html) >[文档](documentation.html) > **FHIR与EHR功能模型对应表**	
## 1.12　附录: FHIR与EHR功能模型对应表
HL7 EHR系统功能模型罗列了在EHR系统(电子病历/电子健康档案系统)中可能存在的功能的参考列表。而FHIR的实现关注的是卫生保健中的信息交换，这主要发生在EHR之中。下表简要地以一种方式描述了可以如何使用FHIR来满足EHR-FM中描述的需求，旨在帮助读者理解如何使用FHIR。也有很多其他有效的方式使用FHIR来实现EHR-FM。
<table class="list"><thead><tr><th colspan="2">EHR功能</th><th>FHIR 实现说明</th></tr></thead><tr><td>IN.1</td><td>安全</td><td>FHIR定义了一部分安全架构，把其他部分交给标准的web安全协议框架</td></tr><tr><td>IN.1.1</td><td>实体认证</td><td>FHIR中假设用户是认证过的。OAuth是一种推荐的方法</td></tr><tr><td>IN.1.2</td><td>实体授权</td><td>目前FHIR中并没有描述或管理访问权限控制的一些资源。一般默认地使用诸如SAML等web框架。参考[安全章节](../infra/security.html#binding)中对FHIR与SAML绑定的讨论</td></tr><tr><td>IN.1.3</td><td>实体访问控制</td><td>参考上面关于SAML/OAuth的部分</td></tr><tr><td>IN.1.4</td><td>患者访问管理</td><td>参考[安全标签](../infra/security-labels.htmll)</td></tr><tr><td>IN.1.5</td><td>抗抵赖</td><td>[provenance资源](../infra/provenance.html)记录了与资源相关的时间戳、系统角色和数字签名</td></tr><tr><td>IN.1.6</td><td>安全的数据交换</td><td>应当在所有生产环境下的数据交换中使用TLS(https:).所有遵循FHIR Restful风格的实现必须能够使用https</td></tr><tr><td>IN.1.7</td><td>安全的数据路由</td><td>FHIR支持代理和其他能够保证消息目的地和传输的形式。参考下面的IN.2.2</td></tr><tr><td>IN.1.8</td><td>信息认证</td><td>参考[provenance资源](../infra/provenance.html)</td></tr><tr><td>IN.1.9</td><td>病人隐私和保密性</td><td>FHIR中并未包含此类需求相关的功能，当然可以在具体实现中提供此类功能</td></tr><tr><td>IN.2</td><td>健康档案信息和管理</td><td>这是FHIR标准的核心</td></tr><tr><td>IN.2.1</td><td>数据的保留、可及性和销毁</td><td>Restful式的FHIR服务器按照所有在一致性声明中的明确描述来提供对资源精确的细粒度的保留和可及性以及对资源的销毁</td></tr><tr><td>IN.2.2</td><td>审计记录</td><td>FHIR 中的[SecurityEvent](../infra/securityevent.html) 资源，可供审计记录使用</td></tr><tr><td>IN.2.3</td><td>同步</td><td>FHIR通过[Bundles](extras.html#bundle) 使用标准的web发布/订阅的方法来支持同步。基于Atom的发布/订阅可能是推送模式 也可能是拉取模式，可以包含某种类型的所有资源或者资源的特定子集。另外成组的资源可以用bundle来交换，保证了相关资源的同步性</td></tr><tr><td>IN.2.4</td><td>健康档案信息的抽取</td><td>FHIR暂时未提供报表格式，但是有检索和获取功能来帮助构建这样的一些报表</td></tr>
<tr><td>IN.2.5</td><td>存储和管理健康档案信息</td><td>Restful式的FHIR服务器能够永久地存储和管理健康信息-更多信息参考下面内容</td></tr><tr><td>IN.2.5.1/2</td><td>管理结构化和非结构化的健康档案信息</td><td>FHIR资源的两种类型的内容--结构化数据和XhtmlL文本描述,能够无缝地支持结构化和非结构化信息的处理</td></tr><tr><td>IN.3</td><td>注册和目录服务 </td><td> FHIR [行政管理类管理资源 ](../res/resourcelist.html#administrative)提供一种注册,可以访问患者、医务人员等的信息</td></tr><tr><td>IN.4</td><td>标准化术语和术语服务</td><td>FHIR鼓励尽可能的使用标准化术语，通过术语相关的多种[数据类型](datatypes.html)全方位支持术语的使用。FHIR中并未定义术语架构或者术语服务的架构，但是定义了[规范](../infra/profile.html) 和 [值集/ValueSet](../infra/valueset.html)来描述如何在FHIR中使用术语</td></tr><tr><td>IN.5</td><td>基于标准的互操作性</td><td>FHIR是对基础互操作性标准的定义</td></tr><tr><td>IN.5.1</td><td>交换标准</td><td>这是FHIR的核心。参考下面交互模型的讨论</td></tr><tr><td>IN.5.2</td><td>交换标准版本控制和维护</td><td>在[此描述了](resources.html#version)FHIR的版本维护</td></tr><tr><td>IN.5.3</td><td>基于标准的应用集成</td><td>FHIR以一种易于理解、使用和调试的基于web的架构来实现简单的集成。在EHR中使用同样的架构也能提供一种简单的方式实现信息交换</td></tr><tr><td>IN.5.4</td><td>交换协议</td><td>FHIR一致性声明和资源规范资源为单个的和基于社区的交易双方之间的协议提供了一种基于注册的架构</td></tr><tr><td>IN.6</td><td>业务规则管理</td><td>目前FHIR中并未解决此类需求</td></tr><tr><td>IN.7</td><td>工作流管理</td><td>目前FHIR并未解决此类需求，尽管存在一些资源和服务支撑此功能。</td></tr></table>
EHR功能模型描述了很多系统间交互的模式。其中每一种都可以用FHIR以不同的方式实现．
<table class="list">
<tr><th>交互模式</th><th>FHIR中的可选项</th></tr>
<tr><td>Unsolicited Notifications如患者前来预约</td><td>*   通过http创建/更新一个新资源　　*   使用atom推送资源　　*   发送FHIR[消息](../impl/message.html)(如果事件已经定义好了)</td></tr><tr><td>查询/响应　比如系统中有没有Adam Everyman这人？有，MRN号码是12345678.</td><td>*   根据变量搜索　　
*   查询消息(暂未定义)</td></tr><tr><td>服务请求和响应　比如空腹血糖实验室检验医嘱和检验结果的响应</td><td>消息和SOA都可以支持，暂不支持请求／响应</td></tr> <tr><td>机构间的信息交换如区域平台或国家平台</td><td>*   使用atom(push模式或pull模式)的发布/订阅　
*   RESTful 接口　　
*   FHIR 消息</td></tr><tr><td>结构化/非结构化临床文档, 如听写的手术记录</td><td>参见[文档](../impl/document.html)</td></tr>
</table>

结合一定程度上安全的和可管理的FHIR服务器， 再加上使用 [SecurityEvent](../infra/securityevent.html) 和 [Provenance](../infra/provenance.html) 资源之后就可以保证满足EHR-FM中定义的话核心记录的管理功能。　　
*   全生命周期记录，包括对来源、起源和作者信息以及视图和交换的记录　　
*   信息完整性、准确性和数字签名的保障　　
*   所保留内容的完整的版本历史记录　　　　
*   数据保留和持久化　　
其他如抗抵赖、访问控制和知情同意/授权追踪相关的功能暂未在FHIR中定义。　　


&copy; HL7.org 2011+. FHIR DSTU (v0.4.0-3900) 构建于2014  12月20号 2014 22:38+0000 星期六 . 
  链接：[试行版是什么](http://hl7.org/implement/standards/fhir/dstu.htmll) |[版本更新情况](http://hl7.org/implement/standards/fhir/history.htmll) | [许可协议](http://hl7.org/implement/standards/fhir/license.htmll) |[提交变更建议](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemAdd&tracker_id=677)	