title: 
date: 
categories: doc
---

[首页](../home/index.html) >[文档](documentation.html) >[资源定义](resources.html) >[扩展](extensibility.html)＞**样例**      


*   [Content](extensibility.html)
*   [示例](extensibility-examples.html)
*   [详细描述](extensibility-definitions.html)
*   [扩展的注册库](extensibility-registry.html)

#### 1.12.6.1 扩展的样例　　

为了使用扩展，要走三个步骤：　　　　

1.  定义扩展　　　
2.  注册扩展　　　　
3.  在实例中使用扩展　　　　　　　　　　　　　

这部分就是对这三个步骤的演示．
#####  1.12.6.1.1 共享病历的病人授权　　　　

基本的patient资源不包含与患者授权相关的信息，和或患者登记时有关授权策略的详细信息．PHR的社交网络供应商可能需要追踪病人与此PHR供应商之间建立起关系的策略，并通过FHIR api与合作伙伴进行共享．如果需要的话，他们可以扩展patient资源来表达患者的使用协议．注意也有其他解决此问题的方法，但这样已经足够用来演示扩展的流程．　　　　　　　　
　

鉴于这个例子的目的，我们假设患者在注册时就已经同意了参与其中的策略，当供应商要更改它们的策略时，它们要征询患者是否同意最新的参与细节．每种参与协议都用一个URI来标识，对于每种不同的策略协定，patient资源中都会包含那些患者同意策略对应的uri．　　　　


#######  1.12.6.1.1.1  定义扩展　　　　　　　　　

对于每个扩展，所要做的第一件事就是完成[扩展的定义属性](extensibility.html#define):      

<table class="codes"> <tr><td>Code</td><td>&quot;参与协议&quot;</td></tr><tr><td>Context</td><td>该扩展用在patient资源之中</td></tr> <tr><td>Short Defn</td><td>用户协议/策略</td></tr> <tr><td>Definition</td><td>患者所同意的用户协议的URI</td></tr> <tr><td>Comments</td><td>URI是对协议文本的字面引用</td></tr> <tr><td>Cardinality</td><td>1..* (患者至少要选择一种协议)</td></tr><tr><td>Type</td><td>uri</td></tr> <tr><td>XPaths</td><td>无</td></tr> <tr><td>is Modifier</td><td>No (用户协议的内容不影响对患者相关数据的解读,尽管可能会影响系统与患者交互的方式)</td></tr> <tr><td>Binding</td><td>(无绑定 - 非可编码值)</td></tr></table>       

######  1.12.6.1.1.2  编写扩展的定义    

通过下表,我们可以得到一个规范.      

This is all then represented formally in a profile. 一些规范不需要包含对资源的约束声明,取而代之的是,它们会包含扩展声明和相应的绑定.这种情况下,一个规范如下所示:    

```
<StructureDefinition xmlns="http://hl7.org/fhir">
  <url value="http://example.org/fhir/StructureDefinition/participation-agreement" />
  <name value="Example Extension Definition" />
  <!-- snip other metadata -->
  <type value="extension" />
  <contextType value="resource" />
  <context value="Patient" />
  <differential>
    <element>
    <path value="Extension.value"/>
    <short value="Agreed agreement/policy" />
    <definition value="A URI that identifies a participation agreement/policy 
      to which the patient has agreed" />
    <comments value="URI is a literal reference to agreement text (html). 
      Systems SHALL conform to the policies as indicated. 
      For further information, see the partnership agreement..." />
    <min value="1" />
    <max value="*" />
    <type>
       <code value="uri" />
    </type>
    <mustSupport value="true" />
    <isModifier value="false" />
    </element>
  </differential>
</StructureDefinition>

````

注意 通常你可能是用一些工具来生成规范的.上面的例子是手工编写的.     
######  1.12.6.1.1.3 注册扩展  

把上面定义扩展的规范放在web中去.首选的话,放置在一个FHIR规范的节点上,最好是放在HL7的规范注册库中(还没有实现)             

在这个例子中,我们假设它已经上传到PHR供应商自己的网站http://example.org/phr/documents/fhir/extensions.上去了.           
######  1.12.6.1.1.4  在实例中使用扩展             

要想在实例中使用扩展,扩展需放在资源的根元素之后.注意扩展的url指向所注册的网址, with the id of the extension as a fragment identifier.
```


<Patient xmlns="http://hl7.org/fhir">
  <extension url="http://example.org/phr/documents/fhir/extensions#participation-agreement" >
    <valueUri value="http://example.org/phr/documents/patient/general/v1" />
  </extension>
    
</Patient>


````

######  1.12.6.1.1.5 将扩展添加到Patient StructureDefinition

上面的规范定义中只是简单的定义了 &quot;参与协议&quot;这个扩展,告诉我们这个扩展可以在patient中使用,但是上面的规范内并没有说服务器实际上是在使用整个扩展.对于PHR供应商而言,通过patientStructureDefinition来声明所有patient资源都在使用这个扩展.    

```
<StructureDefinition xmlns="http://hl7.org/fhir">
  <name value="iso-21090" />
  <!-- snip other metadata, narrative -->
  <differential>

    <!-- first, the patient root element 
      - can be copy/paste from the base patient profile -->    
    <element>
      <path value="Patient"/>
      <!-- snip definition -->
    </element>
    
    <!-- now, the general definition for extensions
      - can be copy/paste from the base patient profile,
      with changes for slicing  -->
    <element>
      <path value="Patient.extension"/>
      <name value="base extension"/>
      <!-- we're going to slice the extension element, and 
        one of the extensions is one we have defined -->
      <slicing>
        <!-- extension is always sliced on url -->
        <discriminator value="url"/> 
        <!-- we don't care what the order of any extensions is -->
        <ordered value="false"/>
        <!-- Other extensions are allowed in addition to this one -->
        <rules value="open"/>
      </slicing>
      <!-- snip definition -->
    </element>
    
    <!-- now, the slice that contains our extension -->    
    <element>
      <path value="Patient.extension"/>
      <!-- clone information from the extension definition. 
        duplicative, but this duplication makes it over all simpler -->
      <short value="Agreed agreement/policy"/>
      <definition value="A URI that identifies a participation agreement/policy 
      to which the patient has agreed"/>
      <!--  min has to be 1, since the extension itself has min = 1 -->
      <min value="1"/>
      <max value="*"/>
      <type>
        <!-- obviously it has to be an extension -->
        <code value="Extension"/>
        <!-- and here is the link to the extension definition:
          this extension has to conform to the rules laid down in its definition -->
        <profile value="http://example.org/phr/documents/fhir/extensions#participation-agreement"/>
      </type>
      <isModifier value="false"/>
    </element>
    
  <!-- snip the rest of the profile -->

  </differential>
</StructureDefinition>
````


注意 - 这一步是可选的 .               

#####   1.12.6.1.2   患者姓名的组成部分

ISO 21090 (Healthcare Data Types)定义一个概念&quot;姓名组成部分修饰符&quot; ,其中包含描述某个姓名组成部分如何使用的信息.在实际应用中,除了极少的场景,很少使用这个字段.按照[FHIR设计原则](extensibility.html),在核心的name数据类型中并没有包含这个字段,可以将其作为扩展.                 

实际应用中,像ISO 21090中类似的这种情况,HL7提供了常用扩展,是在[这里]()定义的.                 

######  1.12.6.1.2.1 定义扩展           

对于每个扩展，所要做的第一件事就是完成[扩展的定义属性](extensibility.html#define):      

<table class="codes"> <tr><td>Code</td><td>&quot;姓名修饰符&quot;</td></tr><tr><td>Context</td><td>该扩展可以用在任何出现HumanName.part的地方 </td></tr> <tr><td>Short Defn</td><td>(可选编码) LS | AC | NB | PR | HON | BR | AD | SP | MID | CL | IN</td></tr> <tr><td>Definition</td><td>除了主要的姓名组成部分之外,每个编码代表姓名组成部分的某个子类.</td></tr> <tr><td>Comments</td><td>用来表达姓名组成部分的额外信息,以及如何使用它们</td></tr> <tr><td>Cardinality</td><td>0..* (该字段总是可选的,如果需要的话可以使用一到多个)</td></tr> <tr><td>Type</td><td>code</td></tr> <tr><td>XPaths</td><td>N/A</td></tr> <tr><td>Is Modifier</td><td>否 (修饰符不会更改姓或者名的内容)</td></tr> <tr><td>RIM Mapping</td><td>ENXP.qualifier</td></tr> <tr><td>v2 Mapping</td><td>N/A</td></tr> <tr><td>Binding</td><td>与 [EntityNamePartQualifierR2 in ISO 21090](http://www.hl7.org/v3ballot/html/infrastructure/vocabulary/EntityNamePartQualifierR2.html) 的子集绑定</td></tr></table>

在这种场景下,并非需要所有的EntityNamePartQualifierR2编码,因为前缀,后缀很明显是姓名的组成部分.与其引用EntityNamePartQualifierR2的OID (2.16.840.1.113883.5.1122), 我们枚举出需要用的编码,只有在规范中定义好了可以使用的编码才允许使用&quot;code&quot; 数据类型.编码如下表 (完整定义请参考[EntityNamePartQualifierR2](http://www.hl7.org/v3ballot/html/infrastructure/vocabulary/EntityNamePartQualifierR2.html)):

<table class="codes"><tr><td>LS</td><td>Legal status </td><td>For organizations a suffix...</td></tr><tr><td>AC</td><td>Academic</td><td>Indicates that a prefix like &quot;D...</td></tr><tr><td>NB</td><td>Nobility</td><td>In Europe and Asia, there are s...</td></tr><tr><td>PR</td><td>Professional</td><td>Primarily in the British Im...</td></tr><tr><td>HON</td><td>Honorific</td><td>An honorific such as 'The Rig...</td></tr><tr><td>BR</td><td>Birth</td><td>A name that a person was given at ...</td></tr><tr><td>AD</td><td>Acquired</td><td>A name part a person acquired. ...</td></tr><tr><td>SP</td><td>Spouse</td><td>The name assumed from the partner...</td></tr><tr><td>MID</td><td>Middle Name</td><td>Indicates that the name par...</td></tr><tr><td>CL</td><td>Call me</td><td>Callme is used to indicate which...</td></tr><tr><td>IN</td><td>Initial</td><td>Indicates that a name part is ju...</td></tr></table>

This is all then represented formally in a profile. 一些规范不需要包含对资源的约束声明,取而代之的是,它们会包含扩展声明和相应的绑定.这种情况下,一个规范如下所示:   
```
<StructureDefinition xmlns="http://hl7.org/fhir">
  <url value="http://hl7.org/fhir/StructureDefinition/iso21090-EN-qualifier" />
  <name value="iso-21090" />
  <!-- snip other metadata, including definition of RIM Mapping -->
  <type value="extension" />
  <contextType value="datatype" />
  <context value="HumanName.given" />
  <context value="HumanName.prefix" />
  <context value="HumanName.family" />
  <context value="HumanName.suffix" />
  <differential>
    <element>
      <path value="Extension.value"/>
      <short value="LS | AC | NB | PR | HON | BR | AD | SP | MID | CL | IN" />
      <definition value="A set of codes each of which specifies a certain subcategory
          of the name part in addition to the main name part type" />
      <comments value="Used to indicate additional information about the
             name part and how it should be used" />
      <min value="0" />
      <max value="*" />
      <type>
         <code value="code" />
      </type>
      <mustSupport value="false" />
      <isModifier value="false" />
      <binding>
        <name value="EntityNamePartQualifier" />
        <strength value="required" />
        <description value="A set of codes each of which specifies a certain subcategory
            of the name part in addition to the main name part type" />
        <referenceReference>
          <reference value="ValueSet/name-part-qualifier" />
        </referenceReference>
      </binding>
      <mapping>
         <identity value="RIM" />
         <map value="ENXP.qualifier" />
      </mapping>
    </element>
  </differential>
</StructureDefinition>

````

注意 通常你可能是用一些工具来生成规范的.上面的例子是手工编写的.        

######   1.12.6.1.2.2  注册扩展    

在这个例子中,在[http://hl7.org/fhir/Profile/iso-21090](http://hl7.org/fhir/Profile/iso-21090?_format=text/html)中注册.用到扩展时,url的值就是这个网址.              
 
######  1.12.6.1.2.3 在实例中使用扩展       

想要使用这个扩展,就要将扩展嵌套在它所想要扩展的属性中.      
注意扩展的URL对应的注册地址,with the id of the extension as a fragment identifier.       

```
<name>
  <use value="official" />
  <given value="Östlund">
     <extension url="http://hl7.org/fhir/StructureDefinition/iso-21090#name-qualifier" >
        <valueCode value="MID" />
     </extension>
  </given>
</name>
````

This particular example is a Scandinavian mellannamn. 
[更多实例请参考](datatypes-examples.html).





 &copy; HL7.org 2011 - 2014. FHIR DSTU (v0.2.1-2606)构建于2014  7月2号 16:29+0800 星期三 . 
链接：[试行版是什么](http://hl7.org/implement/standards/fhir/dstu.html) |[版本更新情况](http://hl7.org/implement/standards/fhir/history.html) | [许可协议](http://hl7.org/implement/standards/fhir/license.html) |[提交变更建议](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemAdd&tracker_id=677)      