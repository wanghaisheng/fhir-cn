title: 
date: 
categories: doc
---

[首页](../home/index.html) >[文档](documentation.html) > [资源](resource.html) > **详细描述**


*   [Content](#)
*   [示例](resource-examples.html)
*   [详细描述](resource-definitions.html)
*   [对应关系](resource-mappings.html)
*   [规范](resource-packages.html)
*   [Operations](resource-operations.html)


##  1.12.1.5 Resource - 详细描述

基础资源定义中字段的详细介绍

| | |      
| ------ | ------- |     
| **Resource** |
  | Definition | Base Resource for everything |
  | [Control](conformance-rules.html#conformance) | 1..1 |
| **Resource.id** |
  | Definition | The logical id of the resource, as used in the url for the resoure. Once assigned, this value never changes. |
  | [Control](conformance-rules.html#conformance) | 0..1 |
  | [Type](datatypes.html) | [id](datatypes.html#id) |
  | Comments | The only time that a resource does not have an id is when it is being submitted to the server using a create operation. Bundles always have an id, though it is usually a generated UUID. |
  | **Resource.meta** |
  | Definition | The metadata about the resource. This is content that is maintained by the infrastructure. Changes to the content may not always be associated with version changes to the resource.|
  | [Control](conformance-rules.html#conformance) | 0..1 |
  | [Type](datatypes.html) | [Meta](resource.html#Meta) |
  | **Resource.implicitRules** |
  | Definition | A reference to a set of rules that were followed when the resource was constructed, and which must be understood when processing the content. |
  | [Control](conformance-rules.html#conformance) | 0..1 |
  | [Type](datatypes.html) | [uri](datatypes.html#uri) |
  | [Is Modifier](conformance-rules.html#ismodifier) | true |
  | Comments | Asserting this rule set restricts the content to be only understood by a limited set of trading partners. This inherently limits the usefulness of the data in the long term. However the existing health eco-system is highly fractured, and not yet ready to define, collect, and exchange data in a generally computable sense. Wherever possible, implementers and/or specification writers should avoid using this element as much as possible. |
  | **Resource.language** |
  | Definition | The base language in which the resource is written. |
  | [Control](conformance-rules.html#conformance) | 0..1 |
  | [Binding](terminologies.html) | Language: Required: [IETF language tag](http://tools.ietf.org/html/bcp47) (A human language) |
  | [Type](datatypes.html) | [code](datatypes.html#code) |
  | Comments | Language is provided to support indexing and accessibility (typically, services such as text to speech use the language tag). The html language tag in the narrative applies  to the narrative. The language tag on the resource may be used to specify the language of other presentations generated from the data in the resource  Not all the content has to be in the base language. The Resource.language should not be assumed to apply to the narrative automatically. If a language is specified, it should it also be specified on the div element in the html (see rules in HTML5 for information about the relationship between xml:lang and the html lang attribute). |


| | |      
| ------ | ------- |     
  | **Meta** |
  | Definition | The metadata about a resource. This is content in the resource that is maintained by the infrastructure. Changes to the content may not always be associated with version changes to the resource. |
  | [Control](conformance-rules.html#conformance) | 1..1 |
  | **Meta.versionId** |
  | Definition | The version specific identifier, as it appears in the version portion of the url. This values changes when the resource is created, updated, or deleted. |
  | [Control](conformance-rules.html#conformance) | 0..1 |
  | [Type](datatypes.html) | [id](datatypes.html#id) |
  | Comments | The server assigns this value, and ignores what the client specifies, except in the case that the server is imposing version integrity on updates/deletes. |
  | **Meta.lastUpdated** |
  | Definition | When the resource last changed - e.g. when the version changed. |
  | [Control](conformance-rules.html#conformance) | 0..1 |
  | [Type](datatypes.html) | [instant](datatypes.html#instant) |
  | Comments | This value is always populated except when the resource is first being created. The server / resource manager sets this value; what a client provides is irrelevant. |
  | **Meta.deleted** |
  | Definition | Set to 'true' if the resource is deleted. Deleted resources can not be fetched via the RESTful API, but may appear in bundles for various reasons. |
  | [Control](conformance-rules.html#conformance) | 0..1 |
  | [Type](datatypes.html) | [boolean](datatypes.html#boolean) |
  | Default Value | false |
  | Meaning if Missing | Not deleted |
  | **Meta.profile** |
  | Definition | A list of profiles [StructureDefinition](structuredefinition.html)s that this resource claims to conform to. The URL is a reference to [StructureDefinition.url](null). |
  | [Control](conformance-rules.html#conformance) | 0..* |
  | [Type](datatypes.html) | [uri](datatypes.html#uri) |
  | Comments | It is up to the server and/or other infrastructure of policy to determine whether/how these claims are verified and/or updated over tiem. |
  | **Meta.security** |
  | Definition | Security labels applied to this resource. These tags connect specific resources to the overall security policy and infrastructure. |
  | [Control](conformance-rules.html#conformance) | 0..* |
  | [Type](datatypes.html) | [Coding](datatypes.html#Coding) |
  | Comments | The security labels can be updated without changing the stated version of the resource. |
  | **Meta.tag** |
  | Definition | Tags applied to this resource. Tags are intended to to be used to identify and relate resources to process and workflow, and applications are not required to consider the tags when interpreting the meaning of a resource. |
  | [Control](conformance-rules.html#conformance) | 0..* |
  | [Type](datatypes.html) | [Coding](datatypes.html#Coding) |
  | Comments | The tags can be updated without changing the stated version of the resource. |
