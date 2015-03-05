title: 
date: 
categories: doc
---

[首页](../home/index.html) >[文档](documentation.html) > [资源](resource.html) > **操作**


*   [Content](#)
*   [示例](resource-examples.html)
*   [详细描述](resource-definitions.html)
*   [对应关系](resource-mappings.html)
*   [规范](resource-packages.html)
*   [Operations](resource-operations.html)

## 1.12.1.6  Resource Resource - Operations

每个资源都有3种不同的操作/方法。更多信息请参考 [Operations](operations.html).

###  1.12.1.6.1  资源内容的校验

校验操作检查所提交的内容是否满足通用的要求、满足新建、更新或对已有资源的删除的要求。

具体操作根据mode参数来确定:

*   [missing]: 服务器根据任意的schema、约束规则或其他通用术语规则来校验   
*   create: 服务器校验资源内容，然后校验其是否满足新建操作The server checks the content, and then checks that the content would be acceptable as a create (e.g. that the content would not validate any uniqueness constraints)
*   update: 服务器校验资源内容，然后校验其是否满足对特定资源的更新要求(如服务器不允许变更的字段没有变化，核对版本完整性)
*   delete: 服务器忽略内容本身，核对所牵涉的资源是否允许删除操作(比如核对一些参照完整性规则) (e.g. checking referential integrity rules)

 update 和 delete两种mode只能用于resource层面 .

该操作的返回结果为OperationOutcome

[操作/方法定义](operation-resource-validate.html) (as a [OperationDefinition](operationdefinition.html)).

URL: [base]/Resource/$validate

URL: [base]/Resource/[id]/$validate

|**入参:** |
| -------- | ----------- | --------| -------- | ----------- |  
 |**Name** |   **Cardinality** | **Type** | **StructureDefinition** | **Documentation** | 
 |resource | 0..1 | Resource | |Must be present unles the mode is &quot;delete&quot;|
 |mode | 0..1 | [string](datatypes.html#string) | | Default is 'no action; (e.g. general validation) |
 |profile | 0..1 | [uri](datatypes.html#uri)| |If this is nominated, then the resource is validated against this specific profile. If a profile is nominated, and the server cannot validate agsinst the nominated profile, it SHALL return an error |
 
 | **出参:** |
 | -------- | ----------- | --------| -------- | ----------- |  
 |**Name** | **Cardinality** | **Type** | **StructureDefinition** | **Documentation** | 
 |return | 1..1 | [OperationOutcome](operationoutcome.html) | |If the operation outcome does not list any errors, and a mode was specified, then this is an indication that the operation would be expected to succeed (excepting for transactional integrity issues, see below) Note: as this the only out parameter, it is a resource, and it has the name 'return', the result of this operation is returned directly as a resource |

该操作可用于软件设计和开发过程中的功能验证。也可用于运行时，一种可能的应用是在用户编辑对话框时，客户端向服务器发送请求，确认该更新操作是否合法，将更新错误提醒给用户。该操作也可以作为轻量级的两阶段式提交协议的一部分，但是不能保证服务器在校验完成之后会保留资源内容，或者服务器能够在校验完成之后成功完成实际上的新建、更新或者删除。


### <span class="sectioncount">1.12.1.6.2<a name="1.12.1.6.2"> </a></span> Access a list of profiles, tags, and security labels<a name="meta"> </a>

<p>该操作会获取特定范围内的规范、标签和安全标记的概要，比如：下述每种范围：
	
*   system-wide: 系统中用到的所有规范、标签和安全标记
*   resource-type level: 某种资源类型涉及的所有规范、标签和安全标记
*   individual resource level:某个资源当前版本所涉及的所有规范、标签和安全标记

同时，该操作也可用于资源的历史版本

[Formal Definition](operation-resource-meta.html) (as a [OperationDefinition](operationdefinition.html)).

URL: [base]/$

URL: [base]/Resource/$meta

URL: [base]/Resource/[id]/$meta

 |**Out Parameters:** |
 | -------- | ----------- | --------| -------- | ----------- |   |**Name** | **Cardinality** | **Type** | **StructureDefinition** | **Documentation** | 
 |return | 1..1 | [Meta](resource.html#Meta) | The meta returned by the operation |

在系统和资源类型的层面上，$meta 操作是用于获取系统中在用的所有标签。该操作的原理是支持查询操作，比如 可以检索哪些标签。在这些层面上，meta数据不会包括versionId, lastUpdated 等. Systems are not obligated to implement the operation at this level (and should return a 4xx error if they don't)

在单个资源和单个资源历史版本的层面上，$meta 操作所获取的meta数据和单独访问资源时获取的meta数据一样。这样，系统就能够在不访问单个资源的情况下获取资源的meta-information，比如：处于安全方面的考虑


### <span class="sectioncount">1.12.1.6.3<a name="1.12.1.6.3"> </a></span> Add or delete profiles, tags, and security labels for a resource<a name="meta-change"> </a>

<p>This operation takes a meta, and either adds or deletes the profiles, tags, and security labels found in it to or from the nominated resource.

This operation can also be used on historical entries

[Formal Definition](operation-resource-meta-change.html) (as a [OperationDefinition](operationdefinition.html)).

URL: [base]/Resource/[id]/$meta-change

 |**入参:** |
 | -------- | ----------- | --------| -------- | ----------- |  
 |**Name** | **Cardinality** | **Type** | **StructureDefinition** | **Documentation** | 
 |meta | 1..1 | [Meta](resource.html#Meta)| | Profiles, tags, and security labels to add to or delete from the existing resource. Note that profiles, tags, and security labels are sets, and duplicates are not created. E.g. Profiles are unique by URL, and tags and security labels are unique by system+code | 
 |mode | 0..1 | [code](datatypes.html#code)| |  Whether to add or delete. The default action is add the labels |
 
 | **出参:** |
 | -------- | ----------- | --------| -------- | ----------- |  
 |**Name** | **Cardinality** | **Type** | **StructureDefinition** | **Documentation** | 
 |return | 1..1 | [Meta](resource.html#Meta) |  Resulting meta for the resource |

This operation is special in that executing this operation does not cause a new version of the resource to be created. The meta is updated directly. This is because the content in meta does not affect the meaning of the resource, and the security labels (in particular) are used to apply access rules to existing resources

<p/>

</div>