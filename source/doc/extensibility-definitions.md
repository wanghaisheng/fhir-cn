title: 
date: 
categories: doc
---

[首页](../home/index.html) >[文档](documentation.html) >[资源定义](resources.html) >[扩展](extensibility.html)＞**详细描述**      


*   [Content](extensibility.html)
*   [示例](extensibility-examples.html)
*   [详细描述](extensibility-definitions.html)
*   [扩展的注册库](extensibility-registry.html)

#### 1.12.6.1 扩展的详细描述　　



<table class="dict">
  <tr><td colspan="2" class="structure"><a name="Extension"> </a><b>Extension</b></td></tr>
  <tr><td>Definition</td><td><p>Optional Extensions Element - found in all resources.</p>
</td></tr>
  <tr><td><a href="conformance-rules.html#conformance">Control</a></td><td>1..1</td></tr>
  <tr><td>Requirements</td><td><p>The ability to add extensions in a structured way is what keeps FHIR resources simple.</p>
</td></tr>
  <tr><td colspan="2" class="structure"><a name="Extension.url"> </a><b>Extension.url</b></td></tr>
  <tr><td>Definition</td><td><p>Source of the definition for the extension code - a logical name or a URL.</p>
</td></tr>
  <tr><td><a href="conformance-rules.html#conformance">Control</a></td><td>1..1</td></tr>
  <tr><td><a href="datatypes.html">Type</a></td><td><a href="datatypes.html#uri">uri</a></td></tr>
  <tr><td>Comments</td><td><p>The definition may point directly to a computable or human-readable definition of the extensibility codes, or it may be a logical URI as declared in some other specification. The definition should be version specific.  This will ideally be the URI for the Resource Profile defining the extension, with the code for the extension after a #.</p>
</td></tr>
  <tr><td colspan="2" class="structure"><a name="Extension.value_x_"> </a><b>Extension.value[x]</b></td></tr>
  <tr><td>Definition</td><td><p>Value of extension - may be a resource or one of a constrained set of the data types (see Extensibility in the spec for list).</p>
</td></tr>
  <tr><td><a href="conformance-rules.html#conformance">Control</a></td><td>0..1</td></tr>
  <tr><td><a href="datatypes.html">Type</a></td><td><a href="datatypes.html#open">*</a></td></tr>
</table>



 &copy; HL7.org 2011 - 2014. FHIR DSTU (v0.2.1-2606)构建于2014  7月2号 16:29+0800 星期三 . 
链接：[试行版是什么](http://hl7.org/implement/standards/fhir/dstu.html) |[版本更新情况](http://hl7.org/implement/standards/fhir/history.html) | [许可协议](http://hl7.org/implement/standards/fhir/license.html) |[提交变更建议](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemAdd&tracker_id=677)      