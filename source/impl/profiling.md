title:  
date:  
categories: impl
---



*   [Profiling FHIR](#)
*   [Examples](profiling-examples.html)

##  2.11.0  Profiling FHIR FHIR的定制与本地化

FHIR标准本身描述了一系列可用于医疗领域多个场景下的基础资源、框架和API。但是不同的生态圈和地区的医学实践、法律和教育程度又存在巨大差异，鉴于此，我们需要根据具体的需求对FHIR标准进一步进行定制和本地化。
一般而言，在定制与本地化过程中需要规定:

*   规定资源中需要那些元素/字段，需要添加哪些额外的仍不存在的字段；
*   规定使用哪些API以及如何使用；
*   规定特定的元素中使用哪些术语字典；
*   描述具体的元素与实际需求(数据库表字段)的对应关系


鉴于医疗自身的特殊性，不同的业务领域、国家、机构或者是供应商、具体的产品、项目的定制与本地化会存在一些重叠的部分。

一般而言，我们在实施规范中定义了如何限制和扩展API，资源以及术语字典。这些约束和限制以及扩展可以通过一些称之为一致性资源来表达。
开发人员能够从这些一致性资源中获得下列信息:

*   确定某些API的调用不适用与某个场景，以及调用API的详细信息Indicate that [some API calls](http.html) are not used for a particular use , and provide additional details about how the API calls are used ([Conformance](conformance.html) Resource)
*  定义了哪些新的操作和查询变量。 Add additional [operations](operations.html) or [search parameters](search.html) not in the base specification   (using the [OperationDefinition](operationdefinition.html) resource or the [SearchParameter](searchparameter.html) Resource
*   确定某个资源中没有用到哪些字段Identify specific elements in resources that are not used ([Profile](profile.html) Resource)
*   描述如何使用资源中已有的字段Describe how existing elements in resources are used (Profile resource)
*   定义在资源或数据类型中用到的新字段Define new elements that are used resources or data types (Profile resource)
*   确定本地术语和标化术语的具体应用Mix custom and standard terminologies and choose which codes from these to use for a particular use (Profile and [Value Set](valueset.html) Resources)
*   本地术语和标化术语的映射 Map between local and standard terminologies or content models ([Concept Map](conceptmap.html) Resource)
*   系统命名空间的注册，术语字典的注册 Register system namespaces for identifiers and terminologies ([NamingSystem](namingsystem.html) Resource)
*   数据字典的描述和注册 Describe and register specific Data Elements that are used across systems in a Data Dictionary ([DataElement](dataelement.html) Resource)

These need to be used following the policies discussed below, and also 
following the basic concepts for extension that are described in [&quot;Extensibility&quot;](extensibility.html). 
For implementer convenience, the specification itself publishes its base definitions using these same resources.

<a name="api"> </a>

###  2.11.0.1  API的扩展和约束 Extending and Restricting the API

一致性资源中罗列了服务器中可用的REST交互(read, update, search增删改查等)，其中，用于查询服务器支持哪些交互的交互接口([Conformance](http.html#conformance))是必须存在的.除此之外，客户端和服务器根据所需选择API实现即可。


除了FHIR已经定义好的操作之外，服务器亦可定义新的操作，只需给自定义的操作名称加上前缀“$”即可，The Conformance resource supports defining what OperationDefinitions make use of particular names on an end point。如果没有使用OperationDefinition来声明已经定义哈的服务，使用较长的名称是比较好的，可用降低服务名称与其他接口冲突的可能性。鉴于FHIR标准中所定义的操作名称中不可能存在"."，我们可以使用“.”来定义自己的名称 诸如"ihe.someService"

建议使用FHIR operations framework来定义操作，也就是说使用OperationDefinition资源来声明所定义的操作，但有些操作可能涉及一些无法这样描述的格式。

我们也可以通过额外的content-type来扩展FHIR的API,使用vCard格式来庚子年或读取appointment资源的数据是很不错的。vCard中定义了自己的mime type。

###  2.11.0.2  约束和扩展资源 Extending and Restricting Resources

可以通过 &quot;StructureDefinition&quot; 资源来约束和扩展某个具体的资源, &quot;StructureDefinition&quot; 中描述了如何使用资源中的字段、元素，在那些地方使用扩展

###  2.11.0.3  Limitations of Use
StructureDefinition 应遵循以下原则:

*   StructureDefinition 不能破坏原始标准的已有规则(比如，某个元素的基数为1..1，则不能改为0..1 或1..*) 
*   StructureDefinition 中不能规定元素的默认值或含义  
*   StructureDefinition 不能为元素规定具体的名称 
*   在不知道StructureDefinition 的前提下应该能够安全的处理资源中的数据 

如果StructureDefinition 中规定某个扩展的动作不能忽略，必须同时使用[modifier extension](extensibility.html#modifiers). 
Another way of saying this is that knowledge must be explicit in
the instance, not implicit in the profile. 

举例说明，如果StructureDefinition中想要描述 [Procedure](procedure.html)资源将被否定(也就是说该手术从未发生)，不能只是在StructureDefinition 中说明，相反，必须在StructureDefinition 规定 该资源要有一个扩展，这个扩展能够表达这样的信息。

也有一种机制可以保证资源在了解和理解了一系列的规则之后才能够安全理解。具体请参考 [Restricted Understanding of Resources](resources.html#ruleset).

###  2.11.0.4  Using Structure Definitions

Structure Definitions 中描述了某个FHIR资源或数据类型的约束、限制。某个Structure Definitions是通过具体的URL来确定的，:

*   限制元素的基数 比如原来是0..* 可以限制成1..2
*   通过将基数的上限设为0来排除某个元素的使用 
*   限制某个元素值为某个固定值
*   对资源内的嵌套元素进行约束(XPath表达式)
*   限制支持多类型的元素的类型 
*   Requiring a typed element or the target of a resource reference to conform to another structure profile (declared in the same profile, or elsewhere)
*   指定其他的术语字典 值集
*   为了描述某个元素在具体场景下的使用提供另外的定义和示例
*   提供具体的映射关系 v2 v3或其他 
*   规定Structure Definitions中必须支持的一到多个元素



A profile contains a linear list of element declarations. The inherent 
nested structure of the elements is derived from the _path_ value of each element. 
For instance, a sequence of the element paths like this:

*   Root
*   Root.childA
*   Root.childA.grandchild1
*   Root.childB

defines the following structure:

<pre class="xml">
 &lt;Root&gt;
   &lt;childA&gt;
     &lt;grandChild/&gt;
   &lt;/childA&gt;
   &lt;childB/&gt;
 &lt;/Root&gt;
</pre>

or its JSON equivalent. The structure is coherent - children are never 
implied, and the path statements are always in order. The element list is 
a linear list rather than being explicitly nested because element definitions
are frequently re-used in multiple places within a single profile, and this re-use
is easier with a flat structure.

<a name="snapshot"> </a>

### <span class="sectioncount">2.11.0.5<a name="2.11.0.5"> </a></span> Differential vs Snapshot

Profiles may contain either a differential statement, a snapshot
statement or both.

Differential statements describe only the differences that they make 
relative to another profile (which is most often the base FHIR resource or data type). 
For example, a profile may make a single element mandatory (cardinality 1..1).
In the case of a differential structure, it will contain a single element 
with the path of the element being made mandatory, and a cardinality statement.
Nothing else is stated - all the rest of the structure is implied (note:
this implies that a differential profile can be sparse, and only 
mention the elements that are changed, without having to list the
full structure).

In order to properly understand a differential structure, it must be 
applied to the profile on which it is based. In order to save
tools from needing to support this operation (which is computationally intensive - and 
impossible if the base structure is not available), a Profile 
can also carry a &quot;snapshot&quot; - a fully calculated form of the
structure that is not dependent on any other structure. The FHIR
project provides tools for the common platforms that can populate
a snapshot from a differential.

Profiles can contain both a differential and a snapshot view. 
In fact, this is the most useful form - the differential 
form serves the authoring process, while the snapshot serves
the implementation tooling. Profile resources used in operational
systems should always have the snapshot view populated.

<a name="slicing"> </a>

### <span class="sectioncount">2.11.0.6<a name="2.11.0.6"> </a></span> Slicing

One common feature of profiles is to take an element that may occur more than once (e.g. in a list),   <!-- What about slicing type choices? -->
and split the list into a series of sublists, each with different restrictions on the elements in the sublist with associated 
additional meaning. In FHIR, this operation is known as &quot;Slicing&quot; a list. It is common to 
“slice” a list into sub-lists containing just one element, effectively putting constraints on each element in the list.

Here is an example to illustrate the process:

![Slicing diagram](slicing.png)

In this example, the base resource defines the &quot;related&quot; element which refers to 
another Observation which is related to the main Observation and which may occur
multiple times. Each &quot;related&quot; element has a &quot;type&quot; element specifying the nature 
of the relationship (component, replacement, derivation etc.), and a &quot;target&quot; element
which identifies the actual observation. In this diagram, for convenience, the contents 
of the target element are shown in the inner box instead of the showing the target 
reference explicitly. Also, to avoid adding clutter to this simplified example, 
the &quot;name&quot; attribute of Observation is shown as just a code not a full CodeableConcept.

The profile for Blood Pressure constrains the related element list into 
2 sublists of one element: a systolic element, and a diastolic element. Each of these
elements has a fixed value for the type element, and the profile also fixes the 
contents of the target observation as well, specifying a fixed LOINC code for
the name and specifying that both have a value of type Quantity. This process
is known as &quot;slicing&quot; and the Systolic and Diastolic elements are called &quot;slices&quot;.

Note that when the resource is exchanged, the wire format that is exchanged is not 
altered by the profile. This means that the item profile names defined in the 
profile (&quot;systolic&quot;, etc. in this example) are never exchanged. A resource 
instance looks like this:

<pre>
 &lt;Observation&gt;
   ...
   &lt;related&gt;
     &lt;type value=&quot;component&quot;/&gt;
     &lt;target ...&gt; &lt;!-- has the name &quot;8480-6&quot; --&gt;
   &lt;/related&gt;
   &lt;related&gt;
     &lt;type value=&quot;component&quot;/&gt;
     &lt;target ...&gt;  &lt;!-- has the name &quot;8462-4&quot; --&gt;
   &lt;/related&gt;
 &lt;/Observation&gt;
</pre>

In order to determine that the first related item corresponds to &quot;Systolic&quot; in 
the profile  to determine to which additional constraints for a sub-list the item conforms, 
the system checks the values of the elements - in this case, the name element
in the resource that target refers to. This element is called the “discriminator”.

<a name="discriminator"> </a>

### <span class="sectioncount">2.11.0.7<a name="2.11.0.7"> </a></span> Discriminator

In the general case, systems processing resources using a profile
that slices a list can determine which profile slice an item in 
the list by checking whether its content meets the rules specified
for the slice. 

This requires for a processor to be able to check all the rules
applied in the slice and to do so speculatively in a depth-first
fashion. Neither of these is appropriate for an operational system,
and particularly not for generated code. For this reason, a slice 
can nominate a set of fields that act as a &quot;discriminator&quot; - they
are used to tell the slices apart. 

When a discriminator is provided, the composite of the values of 
the elements nominated in the discriminator is unique and distinct
for each possible slice and applications can easily determine
which slice an item in a list corresponds to. The intention is that 
this can be done in generated code.

When a profile nominates one or more discriminators, it SHALL 
fix the value of the element for each discriminator for each 
slice, or if the element has a terminology binding, it SHALL be 
associated with a complete binding with a version specific [Value Set](valueset.html) 
reference that enumerates the possible codes in the value set.
The profile SHALL ensure that there is no overlap between the 
set of values and/or codes in the value sets between slices.

It is the composite (combined) values of the discriminators 
that are unique, not each discriminator alone. For example,
a slice on a list of items that are references to other 
resources could nominate fields from different resources, 
where each resource only has one of the nominated elements,
as long as they are distinct across slices. 

A profile is not required to nominate any discriminator at all 
for a slice, but profiles that don't identify discriminators are describing 
content that is very difficult to process, and so this is 
discouraged.

Within a profile, a slice is defined using multiple _element_
entries that share a _path_ but have distinct _name_s. 
These entries together form a &quot;slice group&quot; that is:

1.  **Initiated by a &quot;slicing entry&quot;** That is, the first
		_element_ in a slice group must contain a
		_slicing_ property that defines the
		_discriminator_ for all members of the group.  It also contains the unconstrained definition of the element that is sliced
2.  **Mutually exclusive**. This means that each
		_element_ in a slice group SHALL describe a
		distinct set of  values for the group's
		_discriminators_.  Because of this constraint, an	        element in a resource **instance** will never match more
		than one _element_ in a given slice group. If no discriminators are named,    it SHOULD still be possible to differentiate the slices based    on their properties, though it may be substantially harder to    do so
3.  **Serialized as a group**. The entries in a slice
		group must be **adjacent** in a serialized Profile,
		**or**, if there are any intervening elements, those
		elements must be &quot;compatible with&quot; the group. Concretely, this
		means that any intervening elements must have a
		_path_ that starts with the slice groups's
		_path_.  For example, an _element_ with a
		_path_ of _Observation.name.extension_
		would be compatible with (and thus, would not &quot;break up&quot;) a
		slice group whose path was _Observation.name_

The value of the discriminator element is a path name that identifies
the descendant element using a dotted notation. For references, the path
transitions smoothly across the reference and into the children of the 
root element/object of the resource. For extensions, an extension can be
qualified with the URL of the extensions being referred to.
There are two special names: @type, and @profile. Here are some example discriminators:

<table class="grid">
 <tr>  <td>**Context**</td> <td>**Discriminator**</td> <td>**Interpretation**</td> </tr>
 <tr>  <td>List.entry</td> <td>item.reference.name</td> <td>Entries are differentiated by the name element on the target resource - probably an observation, which could be determined by other information in the profile</td> </tr>
 <tr>  <td>List.entry</td> <td>item.reference.@type</td> <td>Entries are differentiated by the type of the target element that the reference points to</td> </tr>
 <tr>  <td>List.entry</td> <td>item.reference.@profile</td> <td>Entries are differentiated by a profile tag on the target of the reference, as specified by a profile (todo: how to do that?)</td> </tr>
 <tr>  <td>List.entry</td> <td>item.extension[&quot;http://acme.org/extensions/test&quot;].code</td> <td>Entries are differentiated by the value of the code element in the extension with the nominated URL</td> </tr>
 <tr>  <td>List.entry.extension</td> <td>url</td> <td>Extensions are differentiated by the value of their url property (usually how extensions are sliced)</td> </tr>
 <tr>  <td>List.entry</td> <td>item.reference.@type, item.reference.name</td> <td>Extensions are differentiated by the combination of item.reference.name, and, if it has one, the name element. This would be
   appropriate for where a List might be comprised of a Condition, and set of observations, each differentiated by it's name - the condition has no name, so that is evaluated as a null in the discriminator set</td> </tr>
</table>

See also [examples of slicing and discriminators](profiling-examples.html).

<a name="extensions"> </a>

### <span class="sectioncount">2.11.0.8<a name="2.11.0.8"> </a></span> Extension Definitions

An extension definition defines the url that identifies the extension
and which is used to refers to the extension definition when it is used 
in a resource.

The extension definition also defines the context where the extension can be used (usually
a particular path or a data type) and then defines the extension element using the same details used to 
profile the structural elements that are part of resources. This means that a single extension 
can be defined once and used on different Resource and/or datatypes, e.g. one would only have to 
define an extension for “hair color” once, and then specify it can be used on both Patient and Practitioner.

For further discussion of defining and using extensions, along with some examples, 
see [Extensibility](extensibility.html). 

#### <span class="sectioncount">2.11.0.8.1<a name="2.11.0.8.1"> </a></span> Using Extensions in Profiles

Once defined, an extension can be used in an instance of a resource 
without any Profile declaring that it can, should or must be, but 
Profiles can be used to describe how an extension is used.

To actually prescribe the use of an extension in an instance, the extension list 
on the resource needs to be sliced. This is shown in [the extensibility 
examples](extensibility-examples.html#sliceextensions)

Note that the minimum cardinality of an extension SHALL be a valid restriction
on the minimum cardinality in the definition of the extension. if the minimum
cardinality of the extension is 1 when it is defined, it can only be mandatory
when it is added to a profile. This is not recommended - the minimum cardinality
of an extension should usually be 0. 

<a name="binding"> </a>

### <span class="sectioncount">2.11.0.9<a name="2.11.0.9"> </a></span> Binding Definitions

Coded elements have bindings that link from the element to a definition of the 
set of possible codes the element may contain. The binding identifies the 
definition of the set of possible codes and controls how tightly the set of the possible codes is interpreted.

The set of possible codes is either a formal reference to a [ValueSet](valueset.html) 
resource, which may be version specific, or a general reference to some web content that defines a set of 
codes. The second is most appropriate where set of values is defined by 
some external standard (such as mime types). Alternatively, where the binding
is incomplete (e.g. under development) just a text description of the 
possible codes can be provided. 

Bindings have two properties that define how the set of codes is used: _isExtensible_ and _conformance_.

*   **isExtensible**<a name="extensibility"> </a>indicates whether additional codes are allowed beyond those in the defined set of codes.

        <table>
      <tr><td>false</td> <td>No additional codes are to be used beyond the list provided</td> </tr>
      <tr><td>true</td>  <td>Supplemental codes or plain text may be needed (this is common because it is frequently the case that concepts will need to be used which won't be in the defined set of codes)</td></tr>
    </table>
*   **Conformance**<a name="conformance"> </a>indicates the expectations for implementers of the specification.    There are three possible values:

    <table>
      <tr><td>required</td><td>
        <p>Only codes in the specified set are allowed.

        If the strength is 'extensible', other codes may be used for concepts not covered by the        value set but cannot be used for concepts covered by the bound code list, even        if a profile constrains out some of those codes).

          </td></tr>
      <tr><td>preferred</td><td>
        For greater interoperability, implementers are strongly encouraged to use the bound set of
        codes, however alternate codes may be used in profiles if necessary without being considered
        non-conformant.
      </td></tr>
      <tr><td>example</td><td>
        The codes in the set are an example to illustrate the meaning of the field.
        There is no particular preference for the set's use.
      </td></tr>
    </table>

The interplay between the meaning of these is subtle but sometimes important. The following table helps 
define the meanings:

<table>
 <tr><td>**Conformance**</td><td>**isExtensible=false**</td><td>**isExtensible=true**</td></tr>
 <tr><td>**Required**</td><td>Implementers SHALL use a code from the defined set</td><td>Implementers SHALL use a code from the defined set if one is applicable, but otherwise may provide their own code or use text</td></tr>
 <tr><td>**Preferred**</td><td>Implementers SHOULD use a code from the defined set
Using a different code will generate a warning from a validator</td><td>Implementers SHOULD use a code from the defined set if one is applicable, but MAY provide their own code or use text</td></tr>
 <tr><td>**Example**</td><td>Implementers MAY use a code from the defined set, or provide their own code, or use text</td></tr>
</table>

Note: Example binding isExtensible = false is not generally a useful statement. 

<a name="tx"> </a>

### <span class="sectioncount">2.11.0.10<a name="2.11.0.10"> </a></span> Mixing Custom and Standard Terminologies

[Value Set](valueset.html) resources can be used to define local codes (Example) and 
to mix a combination of local codes and standard codes (examples: LOINC, SNOMED), or just
to choose a particular set of standard codes (examples: LOINC, SNOMED, RxNorm). 
Profiles can bind to these value sets instead of the ones defined in the base
specification, following these rules:

<table class="grid">
 <tr> <td>**Binding Type in base specification**</td> <td>**Matching Profile Properties**</td> <td>**Customization Rules in Profiles**</td> </tr>

 <tr> <td>Complete</td> <td>conformance = required, extensible = false</td> <td>The value set can only contain codes contained in the value set specified by the FHIR specification</td> </tr>
 <tr> <td>Incomplete</td> <td>conformance = preferred and extensible = true</td> <td>The value set can contain codes not found in the base value set. These additional codes SHOULD not have the same meaning as existing codes in the base value set</td> </tr>
 <tr> <td>Example</td> <td>conformance = example</td> <td>The value set can contain whatever is appropriate for local use</td> </tr> 
</table> 

<a name="mustSupport"> </a>

### <span class="sectioncount">2.11.0.11<a name="2.11.0.11"> </a></span> Must Support

One property that can be declared on profiles that is not declared on the resource or data type definitions is &quot;Must Support&quot;.
This is a boolean property.  If true, it means that systems claiming to conform to a given profile must &quot;support&quot; the element.
This is distinct from cardinality.  It is possible to have an element with a minimum cardinality of &quot;0&quot;, but still expect systems
to support the element.

The meaning of &quot;support&quot; is left deliberately ambiguous.  Examples might include:

*   The system must be able to store and retrieve the element
*   The system must display the element to the user and/or allow the user to capture the element via the UI
*   The element must appear in an output report
*   The element must be taken into account when performing decision support, calculations or other processing
*   etc.

The specific meaning of &quot;Must Support&quot; for the purposes of a particular profile SHALL be described in the Profile.description or in other documentation for the
implementation guide the profile is part of.

If creating a profile based on another profile, Must Support can be changed from false to true, but cannot be changed from true to false.

<a name="search"> </a>

### <span class="sectioncount">2.11.0.12<a name="2.11.0.12"> </a></span> Search Criteria

The final thing implementations can do is to define search criteria in addition to those defined in the specification itself.  
Search criteria fall into one of four categories:

1.  Enabling search on core elements that don't have standard search criteria defined (e.g. searching Observation by normal range)
2.  Enabling search on elements that already have a standard search criteria defined, but with custom matching rules.  E.g. a sounds-like search on Practitioner name
3.  Enabling search on a particular extension
4.  Enabling search that doesn't correspond to a single element but rather a combination of elements or computation on an element.  E.g. searching for patients by age

Additional Search Parameters can be defined using the [SearchParameter](searchparameter.html) resource.

</div>

				</div>  <!-- /inner-wrapper -->
            </div>  <!-- /row -->
        </div>  <!-- /container -->

    </div>  <!-- /segment-content -->

	<div id="segment-footer" class="segment">  <!-- segment-footer -->
		<div class="container">  <!-- container -->
			<div class="inner-wrapper">
				<p>
        © HL7.org 2011+. FHIR DSTU (v0.4.0-3900) generated on Sat, Dec 20, 2014 22:38+0000.   <!-- [QA Report](qa.html) -->   <!-- achive note -->
        