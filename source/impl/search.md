title:  
date:  
categories: impl
---
<a name="base"> </a>

## <span class="sectioncount">2.2<a name="2.2"> </a></span> Search / Query

One operation that is fundamental to the way FHIR works is to search (or query).
Search/Query operations search through an existing set of resources by a set 
of search criteria supplied as parameters to the search. This page documents 
the FHIR search framework, starting with the simple cases, and working through 
to the full complexity. Implementations need only implement the amount of 
complexity that they require.

In the simplest case, a search is executed by performing a GET operation
in the RESTful framework:

<pre>
 GET [base-url]/[resourcetype](?parameters)
</pre>

For this RESTful search, the parameters are a series 
of name=[value] pairs encoded in the URL or as an 
application/x-www-form-urlencoded submission for a POST.  
The server returns the results in the HTTP response as a bundle (in XML, an atom feed) 
which includes the resources that are the results of the query. The server can also
include additional resources in the result set, such as [OperationOutcome](operationoutcome.html) 
resources. Clients should ignore resources that don't have the expected type. 
A HTTP status code of 403 signifies that the server refused to perform the query, 
while some other 4xx or 5xx code signifies that some error occurred. 

Search operations are executed in one of 3 defined contexts that control which set of resources are being searched:

*   A specified resource type
*   A specified [compartment](extras.html#compartments), perhaps with a specified resource type in that compartment
*   All resources

Search/Query operations can also be initiated by other more complex and flexible
methods described below, which change both the way the search/query is initiated, and 
the results that are returned. 

<a name="standard"> </a>

## <span class="sectioncount">2.2<a name="2.2"> </a></span> Standard Parameters

The search parameter _id refers to the logical id of the resource, and can be used when the search context specifies a resource type:

<pre>
 GET [base-url]/patient?_id=23
</pre>

This search finds the patient resource with the given id (there can only be one 
resource for a given id). Functionally, this is equivalent to a [simple
read operation](http.html#read):

<pre>
 GET [base-url]/Patient/23
</pre>

except that it returns a bundle with the requested resource, rather than the 
resource itself. However additional parameters can be added which may provide
additional functionality on top of this base read equivalence.

### <span class="sectioncount">2.2.1<a name="2.2.1"> </a></span> Parameters for each resource

In addition to the _id parameter which exists for all resources, each 
FHIR resource type defines its own set of search parameters with 
their names, types, and meanings. These search parameters are on the 
same page as the resource definitions, and are also published as part
of the standard conformance statement ([XML](conformance-base.xml.html) or [JSON](conformance-base.json.html)).

Mostly, the defined search parameters correspond to a 
single element in the resource, but this is not required, and some 
search parameters refer to the same type of element in multiple 
places, or refer to derived values.

Some of the search parameters defined by the resources are associated 
with more than one path in the resource. This means that the search 
parameter matches if any of the paths contain matching content, and
which ever path matches, the whole resource is returned in the 
search results. The client may have to examine the resource to determine
which path contains the match.

Servers are not required to implement any of these search parameters
(except for the _id parameter described above), and may define their own 
additional parameters if they wish. 

<a name="ptypes"/>

### <span class="sectioncount">2.2.2<a name="2.2.2"> </a></span> Search Parameter Types

Each search parameter is defined with a type that defines how the search parameter
behaves. These are the defined parameter types:

<table class="codes">
 <tr><td>number</td><td>Search parameter SHALL be a number (a whole number, or a decimal).</td></tr>
 <tr><td>date</td><td>Search parameter is on a date/time. The date format is the standard XML format, though other formats may be supported.</td></tr>
 <tr><td>string</td><td>Search parameter is a simple string, like a name part. Search is case-insensitive and accent-insensitive. May match just the start of a string. String parameters may contain spaces.</td></tr>
 <tr><td>token</td><td>Search parameter on a coded element or identifier. May be used to search through the text, displayname, code and code/codesystem (for codes) and label, system and key (for identifier). Its value is either a string or a pair of namespace and value, separated by a &quot;|&quot;, depending on the modifier used.</td></tr>
 <tr><td>reference</td><td>A reference to another resource.</td></tr>
 <tr><td>composite</td><td>A composite search parameter that combines a search on two values together.</td></tr>
 <tr><td>quantity</td><td>A search parameter that searches on a quantity.</td></tr>
</table>

The search parameters can also have &quot;modifiers&quot; appended to them that control
their behavior. The kind of modifiers that can be used depend on the type
of parameter.

<a name="modifiers"/>

#### <span class="sectioncount">2.2.2.1<a name="2.2.2.1"> </a></span> Modifiers

Parameters are defined per resource, and their names may additionally specify a modifier as a suffix, 
separated from the parameter name by a colon. Modifiers are:

*   For all parameters (except combination): &quot;:missing&quot;. E.g. gender:missing=true (or false).  Searching for &quot;gender:missing=true&quot; will return all the resources that don't have any value for the gender parameter (which usually  equates to not having the relevant element in the resource). Searching for &quot;gender:missing=false&quot;
  will return all the resources that have a value for the &quot;gender&quot; parameter.*   For string: &quot;:exact&quot; (the match needs to be exact, no partial matches, case sensitive and accent-sensitive), instead of the default behavior, which is that the search does partial matches. It is at the discretion of the server whether to do a left-partial search
*   For token: &quot;:text&quot; (the match does a partial searches on the text portion of a CodeableConcept or the display portion of a Coding), instead of the default search which uses codes
*   For reference: &quot;:[type]&quot; where [type] is the name of a type of resource

<a name="number"/>

#### <span class="sectioncount">2.2.2.2<a name="2.2.2.2"> </a></span> number

The prefixes &gt;, &gt;=, &lt;=, and &lt; may be used on the parameter value, 
and have the usual meaning. Note that &quot;=&quot; must be escaped in the 
value in a URL. Examples:

<table class="grid">
 <tr><td>[parameter]=100</td><td>Values that equal 100, to 2 significant figures precision, so range [99.5 ... 100.5)</td></tr>
 <tr><td>[parameter]=100.00</td><td>Values that equal 100, to 4 significant figures precision, so range [99.995 ... 100.005). Whole numbers also equal 100.00, but not 100.01</td></tr>
 <tr><td>[parameter]=&lt;100</td><td>Values that are less than 100</td></tr>
 <tr><td>[parameter]=&lt;=100</td><td>Values that are less or equal to 100</td></tr>
 <tr><td>[parameter]=&gt;100</td><td>Values that are greater than 100</td></tr>
 <tr><td>[parameter]=&gt;=100</td><td>Values that are greater or equal to 100</td></tr>
</table>

For comparisons involving &lt; or &gt;, uncertainty does not factor, and the precision of the numbers is considered arbitrarily high.
Note that the way these search parameters operate here is not the same as whether two numbers are equal to each other in a mathematical sense.

<a name="date"/>

#### <span class="sectioncount">2.2.2.3<a name="2.2.2.3"> </a></span> date

A date parameter searches on a date/time or period. The prefixes &gt;, &gt;=, &lt;=, and &lt; may be used on the parameter value, 
and have the usual meaning. However, as is usual for date/time related functionality, while the 
concepts are relatively straight-forward, there are a number of subtleties involved in ensuring consistent behavior.

*   The date parameter format is yyyy-mm-ddThh:nn:ss(TZ) (the standard XML format).
        *   Technically, this is any of the [date](datatypes.html#date), [dateTime](datatypes.html#dateTime), and [instant](datatypes.html#instant) data types
    *   e.g. Any degree of precision can be provided, but it SHALL be populated from the left (e.g. can't specify a month without a year), except that the minutes SHALL be present if an hour is present, and you SHOULD provide a time zone if the time part is present
    *   Some user agents may escape the &quot;:&quot; characters in the URL, and servers SHALL handle this correctly
*   [parameter]=[date] searches for resources where the date is within
   the period implied by the given value in [date]. &quot;[parameter]=&gt;[date]&quot; searches for all resources where the specified date is after [date].   &quot;[parameter]=&lt;=[date]&quot; searches for all resources where the specified date is in or before [date], etc.*   The element the search refers to may have a datatype of [date](datatypes.html#date), [dateTime](datatypes.html#dateTime), [instant](datatypes.html#instant), [Period](datatypes.html#Period), or [Schedule](datatypes.html#Schedule). All of these time related types actually specify an interval of time, as does the search parameter itself.

        *   For Period and Schedule, the fact that they refer to an interval of time is explicit (though the upper or lower bound may not actually be specified in resources)
    *   For a date or a dateTime (and the search parameter), the interval is implicit. For example, the date 2013-01-10 specifies all the time from 00:00 on 10-Jan 2013 to immediately before 00:00 on 11-Jan 2013.
    *   An instant (which is the same as a fully specified dateTime with milliseconds) is considered a fixed point in time with an interval smaller than the precision of the system, i.e. an interval with an effective width of 0.
*   Date parameter searches are always matched based on the behavior of intervals, as follows:

        *   For [parameter]=[date], the requirement is that the search interval fully contains the time of the target. i.e. [parameter]=2013-01-14 includes 2013-01-14T00:00 (obviously) and also 2013-01-14T10:00 but not 2013-01-15T00:00
    *   For &quot;[parameter]=&lt;[date]&quot;, the requirement is that the interval of the time before [date] intersects (i.e. overlaps) with the interval of time in the relevant resource element.	    For instance, the resource time 2013-01-14 is included in the set of values that come before 2013-01-14T10:00, because it includes the part of 14-Jan 2013 before 10am*   For &quot;[parameter]=&gt;[date]&quot;, the requirement is that the interval of the time after [date] intersects (i.e. overlaps) with the interval of time in the relevant resource element.	    For instance, the resource time 2013-01-14 is included in the set of values that come after 2013-01-14T10:00, because it includes the part of 14-Jan 2013 after 10am
   Implicitly, a missing lower boundary is 'less than' any actual date.  A missing upper boundary is 'greater than' any actual date.
   For instance, the period from 21-Jan 2013 onwards is included in matches for date=&gt;=2013-03-14 because it may include times after 14-Mar 2013.
*   Similarly, when the date parameter is not fully specified, matches against it are based on the behavior of intervals, where:

        *   Dates with just the year specified are equivalent to an interval that starts at the first instant of January 1st to the last instant of December 31st, e.g. 2000 is equivalent to an interval of [2000-01-01T00:00, 2000-12-31T23:59]
    *   Dates with the year and month are equivalent to an interval that starts at the first instant of the first day of the month and ends on the last instant of the last day of the month, e.g. 2000-04 is equivalent to an interval of [2000-04-01T00:00, 2000-04-30T23:59]
*   Where possible, the system should correct for timezones when performing queries. Dates do not have time zones, and time zones   should not be considered. Where both search parameters and resource element date times do not have time zones, the servers local
   time zone should be assumed.
*   Note that for a Schedule data type, the specified scheduling details are ignored and only the outer limits matter. For instance, a schedule that specifies every second day between
   31-Jan 2013 and 24-Mar 2013 includes 1-Feb 2013, even though that is on an odd day that is not specified by the period. This is   to keep the server load processing queries reasonable.

As an example, the following query searches for all the procedures in a patient compartment that occurred over a 2 year period:

<pre>
 GET [base-url]/Patient/23/procedure?date=&gt;2010-01-01&amp;date=&lt;2011-12-31
</pre>

<a name="string"/>

#### <span class="sectioncount">2.2.2.4<a name="2.2.2.4"> </a></span> string

The string parameter refer to simple string searches against sequences of characters. 
Matches are case- and accent- insensitive. By default, a match exists if a portion of 
the parameter value contains the specified string. It is at the discretion of the 
server whether to do a left-partial search. The modifier :exact can be used to indicate
that the match needs to be exact (the whole string, including casing and accents). For example:

<pre>
 GET [base-url]/Patient?name=eve
 GET [base-url]/Patient?name:exact=Eve
</pre>

The first is a request to find any patients with &quot;eve&quot; in any part of the name. This would 
include patients with the name &quot;Eve&quot;, &quot;Severine&quot;, etc. The second search would only return
patients with the name &quot;Eve&quot;.

An additional modifier :text
can be used to specify a search with advanced text handling (see [below](#text))
though only a few servers are expected to offer this facility.

It is at the discretion of the server whether to pre-process names, addresses, 
and contact details to remove separator characters prior to matching in order
to ensure more consistent behavior. For example, a server might remove all 
spaces and &quot;-&quot; characters from phone numbers. What is most appropriate varies 
depending on culture and context.

<a name="token"/>

#### <span class="sectioncount">2.2.2.5<a name="2.2.2.5"> </a></span> token

A token type is a parameter that searches on a code or identifier value 
where the value may have a URI that scopes its meaning (from a [Coding](datatypes.html#Coding), 
a [CodeableConcept](datatypes.html#CodeableConcept) or an [Identifier](datatypes.html#Identifier) type, and also 
from a [code](datatypes.html#code) where the URI is implicit). 

If the parameter has no modifier, the search is performed against
the URI/value from a Coding or an Identifier. The syntax for the
value is one of the following:

*   **[parameter]=[code]** matches a code/value irrespective of it's system namespace
*   **[parameter]=[namespace]|[code]** matches a code/value in the given system namespace*   **[parameter]=|[code]** matches a code/value that has no system namespace

Note that the namespace URI and code both must be [escaped](#escaping).

If the modifier &quot;:text&quot;, is used, the search parameter is processed as a 
string that searches text associated with the code/value - either _CodeableConcept.text_,
_Coding.display_, or _Identifier.label_.

Here are some example searches:

<table>
 <tr><td width="50%">**Search**</td><td>**Description**</td></tr>
 <tr><td><pre> GET [base-url]/Patient?identifier=http://acme.org/patient|2345</pre></td><td>Search for all the patients with an identifier with key = &quot;2345&quot; in the system &quot;http://acme.org/patient&quot;</td></tr>
 <tr><td><pre> GET [base-url]/Patient?gender=male</pre></td><td>Search for any patient with a gender that has a code &quot;male&quot;, irrespective of the system. Note that this usually isn't very useful - systems generally define symbols where overlap is coincidental and not informative</td></tr>
 <tr><td><pre> GET [base-url]/Patient?gender=http://hl7.org/fhir/v2/0001|M</pre></td><td>Search for any patient with a gender which is coded as &quot;M&quot; in the HL7 Administrative Gender table</td></tr>
 <tr><td><pre> GET [base-url]/Patient?gender:text=male</pre></td><td>Search for any patient with a gender that has a text &quot;male&quot; associated with it (note: this will include &quot;female&quot;)</td></tr>
</table>

<a name="quantity"/>

#### <span class="sectioncount">2.2.2.6<a name="2.2.2.6"> </a></span> quantity

A quantity parameter searches on the [Quantity](datatypes.html#Quantity) data type.
The syntax for the value follows the form:

*   **[parameter]=[comparator][number]|[namespace]|[code]** matches a quantity with the given unit

The comparator is optional; if it is not present, the default comparator is &quot;=&quot;. A special value &quot;~&quot; can be used for approximation.  Example searches:

<table>
 <tr><td width="50%">**Search**</td><td>**Description**</td></tr>
 <tr><td><pre> GET [base-url]/Observation?value=5.4|http://unitsofmeasure.org|mg</pre></td><td>Search for all the observations with a value of 5.4 mg where mg is understood as a UCUM unit (system/code)</td></tr>
 <tr><td><pre> GET [base-url]/Observation?value=5.4||mg</pre></td><td>Search for all the observations with a value of 5.4 mg where the units - either the code  or the stated human units (units) are &quot;mg&quot;</td></tr>
 <tr><td><pre> GET [base-url]/Observation?value=&lt;5.4|http://unitsofmeasure.org|mg</pre></td><td>Search for all the observations where the value of is less than 5.4 mg where mg is understood as a UCUM unit</td></tr>
 <tr><td><pre> GET [base-url]/Observation?value=~5.4|http://unitsofmeasure.org|mg</pre></td><td>Search for all the observations where the value of is about 5.4 mg where mg is understood as a UCUM unit. 
   The recommended value for the approximation is 10% of the stated value, but systems may choose other values where appropriate</td></tr>
</table>

The search processor may choose to perform a search based on [canonical units](datatypes.html#quantity) (e.g. any value where the units can be converted to a value in mg in the case above)

<a name="chaining"/>
<a name="reference"/>

#### <span class="sectioncount">2.2.2.7<a name="2.2.2.7"> </a></span> reference

A reference parameter refers to [references between resources](references.html), e.g. find all 
Conditions where the subject reference is a particular patient, where the patient is selected by name or identifier.
The interpretation of a _reference_ parameter is either:

*   **[parameter]=[id]** the logical [id] of a resource using a local reference (i.e. a relative reference)
*   **[parameter]=[url]** where the [url] is an absolute URL - a reference to a resource by it's absolute location

Note that if a relative reference resolves to the same value as a specified absolute URL, or vice versa, this is a match too.

Some references are allowed to point to more than one type of resource. e.g. subject : Resource(Patient|Group|Device|..).
In these cases, multiple different resources may have the same logical identifier. In this case, the client can specify 
a type modifier after the name of the parameter to be explicit about the intended type:

<pre>
 GET [base-url]/condition?subject:Patient=23
</pre>

This searches for any conditions where the subject refers to the patient resource with the 
logical identifier &quot;23&quot;. The server SHOULD reject a query where the logical id refers to 
more than one matching resource across different types. Note that the :[type] modifier 
can't be used with a reference to a resource found on another server, since the server 
would not usually know what type that resource has (but since these are absolute
references, there can be no ambiguity about the type).

#### <span class="sectioncount">2.2.2.8<a name="2.2.2.8"> </a></span> Chained parameters

In order to save a client from doing a series of search operations, 
reference parameters may be &quot;chained&quot; by appending them with 
a period (.) followed by the name of a search parameter defined for the target 
resource. This can be done recursively, following a logical path 
through a graph of related resources, separated by &quot;.&quot;.
For instance, given that 
the resource [DiagnosticReport](diagnosticreport.html) 
has a search parameter named _subject_, which is usually a 
reference to a [Patient](patient.html) resource, and 
the Patient resource includes a parameter _name_ which 
searches on patient name, then the search

<pre>
 GET [base-url]/DiagnosticReport?subject.name=peter
</pre>

is a request to return all the lab reports that have a subject whose name includes &quot;peter&quot;. Because 
the Diagnostic Report subject can be one of a set of different resources, it's possible to limit
the search to a particular type:

<pre>
 GET [base-url]/DiagnosticReport?subject:Patient.name=peter
</pre>

Which is a request to return all the lab reports that have a subject which is a patient, whose name includes &quot;peter&quot;. 

Advanced Search Note: 
Where a chained parameter searches a resource reference that may have more than one 
different type of resource as its target, the parameter chain may end up referring 
to search parameters with the same name on more than one kind of resource at once. 
The parameter names defined in FHIR have consistent types wherever they are used. 
Implementers defining their own names need to be sure that they do not create 
unprocessable combinations. Servers SHOULD reject queries chained queries
that lead to disjoint types along the path (e.g. the client has to specify
the type explicitly using the syntax in the second example above).

<a name="composite"/>
<a name="combining"/>

### <span class="sectioncount">2.2.3<a name="2.2.3"> </a></span> Composite Search Parameters

The result of the search operation is the intersection of the resources that match the criteria specified by each 
individual search parameter. If a parameter repeats, such as /patient?language=FR&amp;language=NL, then 
this matches a patient who speaks both languages. If, instead, the search is to find patients that speak either 
language, then this is a single parameter with multiple values, separated by a ',': &quot;/patient?language=FR,NL&quot;. 

This allows for simple combinations of and/or values, but doesn't allow a search based on 
a pair of values, such as all observations with a sodium value &gt;150 mmol/L (particularly
as the end criteria of a chained search), or searching on Group.characteristic: you need 
find a combination of key/value, not an intersection of separate matches on key and value. 
Another example is spatial coordinates when doing geographical searches. 

To allow these searches, a resource may also specify _composite_ parameters 
that take sequences of single values that match other defined parameters as an 
argument. The matching parameter of each component in such a sequence 
is documented in the definition of the parameter. These sequences are formed by 
joining the single values with a &quot;$&quot;.  Note that this sequence is a single 
value and itself can be composed into a set of values, so that, for example, 
multiple matching state-on-date parameters can be specified as 
state-on-date=new$2013-05-04,active$2013-05-05.

Modifiers are not used on composite parameters.
  <!-- Future note: use \p and \m in query values? if we add a double = to parameter value for text, that would get rid 
of :exact. 
Won't try to get rid of type modifier - that's the real use for modifiers because it has to be in a chaining line. 
Other modifier is :text on token - use "~"? or ""? -->

<a name="escaping"/>

### <span class="sectioncount">2.2.4<a name="2.2.4"> </a></span> Escaping Search Parameters

In the rules above, special rules are defined for the characters &quot;$&quot;, &quot;,&quot;, and &quot;|&quot;. 
As a consequence, if these characters appear in an actual parameter value,
they must be differentiated from their use as separator characters. When 
any of these characters appear in an actual parameter value, they must be 
prepended by the character &quot;\&quot; (which also must be used to prepend itself).
So &quot;param=xxx$xxx&quot; means a composite parameter, while &quot;param=xx\$xx&quot; means that
the parameter has the literal value 'xx$xx'. The parameter value &quot;xx\xx&quot; is illegal,
and the parameter value &quot;param=xx\\xx&quot; means a literal value of 'xx\xx'.

<a name="text"/>

### <span class="sectioncount">2.2.5<a name="2.2.5"> </a></span> Text Search Parameters

There are two special text search parameters, _text and _content, which search 
on the narrative of the resource, and the entire content of the resource respectively. 
These parameters SHOULD support a sophisticated search functionality of the type 
offered by typical text indexing services is appropriate. 
The value of the parameter is a text based query, which may involve searching
multiple words with thesaurus and proximity considerations, and logical operations 
such as AND, OR etc. For example:

<pre>
 GET [base-url]/Condition?_text=(bone OR liver) and metastases
</pre>

This searches for all Condition resources with the word &quot;metastases&quot; and either 
&quot;bone&quot; or &quot;liver&quot; in the narrative. The server MAY choose to search 
for related words as well. 

<a name="dstu"> </a>
> **DSTU Note**: The issues around standardizing text search are not fully resolved. 
> During the trial use period for this specification, we recommend that systems use 
> the rules specified by [
> a forth coming release of the OData specification for the $search parameter](http://docs.oasis-open.org/odata/odata/v4.0/cs01/part1-protocol/odata-v4.0-cs01-part1-protocol.html#_The_$search_System).
> Typical implementations would use Lucene, an sql-based full text search, 
> or some indexing service. Feedback about consistent implementation in this area
> is welcome.

<a name="tag"/>
<a name="tags"/>
<a name="profile"/>

### <span class="sectioncount">2.2.6<a name="2.2.6"> </a></span> Selecting resources by tag, profile or security label

Resources may have [tags](extras.html#tag) affixed to them: either general tags, profile tags or
security labels. Search supports the _tag, _profile and _security parameters to search for any tagged resource
by the term (URI) within the specific tag scheme. For example:

<pre>
 GET [base-url]/Condition?_tag=http://acme.org/fhir/tags/needs-review
</pre>

This searches for all Condition resources with a tag &quot;http://acme.org/fhir/tags/needs-review&quot; in the
general tag scheme &quot;http://hl7.org/fhir/tag&quot;. In the same manner:

<pre>
 GET [base-url]/DiagnosticReport?_profile=http://hl7.org/fhir/profile/lipid
 GET [base-url]/DiagnosticReport?_profile=http://localhost/profile/lipid
</pre>

restricts the search to only DiagnosticReport resources that are tagged that they conform to a particular profile.
The reference to localhost refers to a local profile with the given logical id (&quot;lipid&quot;) in this case.

All three tag search parameter may have the modifiers &quot;:partial&quot; and &quot;:text&quot;, which mean 
to only match on the left side of the target tag term, or to search the label part of the tag respectively.

Note that when a resource is submitted to a server as a create or an update, the server is 
free to determine which profiles a resource conforms to, and add additional profile tags 
as appropriate so that resources can be found by this operation.

<a name="return"> </a>

## <span class="sectioncount">2.2<a name="2.2"> </a></span> Managing Returned Resources

### <span class="sectioncount">2.2.1<a name="2.2.1"> </a></span> Relevance

Where a search specifies a non-deterministic sort, the search algorithm
may generate some kind of ranking score to indicate which resources meet
the specified criteria better than others. The server can return this 
score using the OpenSearch Relevance extension:

<pre class="spec">  <span style="float: right">[![doco](help.png)](formats.html "Documentation for this format")</span>
  &lt;entry&gt;<span style="color:Gray;">&lt;!-- Zero+ --&gt;</span>
    &lt;os:score xmlns:os=&quot;http://a9.com/-/opensearch/extensions/relevance/1.0/&quot;&gt;[score]&lt;/os:score&gt;<span style="color:Gray;">&lt;!-- </span><span style="color: brown;">**0..1**</span><span style="color: Gray"> --&gt;</span>
    &lt;content type=&quot;text/xml&quot;&gt;<span style="color:Gray;">&lt;!-- </span><span style="color: brown;">**1..1**</span><span style="color: Gray"> --&gt;</span>
  &lt;/entry&gt;
</pre>

[score] is a decimal number with a value between (and including) 0 and 1. 

<a name="sort"/>

### <span class="sectioncount">2.2.2<a name="2.2.2"> </a></span> Sorting

The client can indicate which order to return the results in 
using the parameter &quot;_sort&quot;, which can have a value of one of the search parameters. 
The _sort parameter can repeat to indicate sort order, with the repeats indicating
a lower sort priority sequentially.

The _sort parameter takes one of two qualifiers, &quot;:asc&quot; and &quot;:desc&quot;, which specify 
ascending and descending sort order respectively. The default value is &quot;:asc&quot;. 

Notes:

*   When sorting, the actual sort value used is not returned explicitlyby the server for each resource, just the resource contents
*   To sort by relevance, use &quot;_sort:asc=_score&quot;
*   The server returns the sort it performs as part of the returned search parameters (see [below](#conformance))
*   A search parameter can refer to an element that repeat, and therefore
there can be multiple values for a given search parameter for a single
resource. In this case, the sort is based on the item in the set of
multiple parameters that comes earliest in the specified sort orderwhen ordering the returned resources.

### <span class="sectioncount">2.2.3<a name="2.2.3"> </a></span> Page Count

In order to keep the load on clients, servers and the network 
minimized, the server may choose to return the results in 
a series of pages. The search result set contains the URLs
that the client uses to request additional pages from the 
search set. For a simple RESTful search, the page links are 
[contained in the returned bundle as links](http.html#paging).

Typically a server will provide its own parameters in the links
that it uses to manage the state of the query as pages are 
retrieved. These parameters do not need to be understood 
or processed by the client.

The parameter _count is defined as a hint to the server 
regarding how many resources should be returned in a 
single page. Servers SHALL not return more resources than 
requested (even if they don't support paging) but are 
allowed to return less than the client asked for. Note 
that it is at the discretion of the search engine how to 
handle ongoing updates to the resources while the search 
is proceeding. 

<a name="include"/>

### <span class="sectioncount">2.2.4<a name="2.2.4"> </a></span> Including other resources in result (_include)

Clients may request that the engine return additional resources related to 
the search results, in order to reduce the overall network query time. 
A typical case where this is useful is where the client is querying on 
some type of clinical resource, but for every such resource returned, 
the client will also need the subject (patient) resource that the 
clinical resource refers to. The client requests that the subject 
resources be included in the results set by providing one or more 
_include parameters.

Each _include parameter specifies a path to a url (usually a resource reference):

<pre>
 GET [base-url]/MedicationDispense?_include=MedicationDispense.authorizingPrescription
    &amp;_include=MedicationPrescription.prescriber&amp;criteria...
</pre>

For each returned resource, the server collects the elements described by the path, 
and any resources they point to that the server also holds are added to the results.
This search returns all the [Medication 
Prescription](medicationprescription.html) resources and their [prescribing Practitioner](practitioner.html) Resources
for the matching [Medication Dispense](medicationdispense.html) resources.

#### <span class="sectioncount">2.2.4.1<a name="2.2.4.1"> </a></span> Include Paths

An include path begins at the root of a FHIR resource and must include exactly one property of 
type [ResourceReference](references.html#Identification) or [uri](datatypes.html#uri), 
which must appear in the terminal position. That means that an 
include path cannot &quot;cross the boundary&quot; from one resource to another.  So for example, 
`CarePlan.activity.simple.performer` is a valid include path, because it begins at the 
root of the CarePlan resource and ends with a reference to another resource 
(Practitioner|Organization|RelatedPerson|Patient). On the other hand, 
`CarePlan.patient.managingOrganization` is an invalid include path, because it 
includes two ResourceReferences (patient and managingOrganization), and `CarePlan.goal` 
is an invalid include path because it does not end with a ResourceReference or a URI.

When looking for the references indicated by an include path, all occurrences of 
the component last encountered 
on the that path need to be considered, including occurrences of that same 
component reachable via deeper (nested) relations. An example is the include path
Composition.section.content, where the content reference on the highest level 
Section is included, but also those reachable via the nested section relationship. 
Likewise, Questionnaire.group.subject will return all subject on all Groups, 
including those reachable by the deeper path via the nested Question and 
nested Groups within those questions.

Include paths may include wild cards, such as MedicationDispense.results.*, or even _include=*,
though both clients and servers need to take care not to request or return too many resources 
when doing this. Most notably, re-applying inclusion paths over newly included resources
might lead to cycles or the retrieval of the full patient's file: resources are
organized into an interlinked network and broad _include paths may eventually traverse all
possible paths on the server. For servers, these recursive and wildcard _includes are 
demanding and may slow the search response time significantly. Servers are expected to 
limit the number of iterations done and are not obliged to honor requests to include 
additional resources in the search results.

**Note**: for a server, it would generally only be required perform one iteration per
_include parameter

#### <span class="sectioncount">2.2.4.2<a name="2.2.4.2"> </a></span> External References

If the _include path selects a reference that refers to a resource on another server,
the server can element to include that resource in the search results for the convenience
of the client. 

If the _include path selects a reference that refers to an entity that is not a Resource
(e.g. an image attachment), the server may also elect to include this in the returned 
results as a [Binary](extras.html#binary) resource. For example, the include 
path may point to an attachment which is by reference, like this:

<pre>
 &lt;content&gt;
   &lt;contentType&gt;image/jpeg&lt;/contentType&gt;
   &lt;url&gt;http://example.org/images/2343434/234234.jpg&lt;/url&gt;
 &lt;/content&gt;
</pre>

The server can retrieve the target of this reference, and add this to the 
results for the convenience of the client. 

<a name="dstu-2"> </a>
> **DSTU Note**: HL7 is seeking feedback from implementers about whether additional
> rules should be made about how _include works, based on implementation experience.

#### <span class="sectioncount">2.2.4.3<a name="2.2.4.3"> </a></span> Paging

When returning paged results for a query with _include resources, all _include resources that are 
related to the primary resources returned for the page SHOULD also be returned as part of that 
same page, even if some of those resource instances have previously been returned on previous 
pages.  This allows both sender and receiver to avoid caching results of other pages.

<a name="summary"> </a>

### <span class="sectioncount">2.2.5<a name="2.2.5"> </a></span> Summary

The client can request the server to return a summary portion of the resources
only using the parameter &quot;_summary&quot;:

<pre>
   GET [base-url]/ValueSet?_summary=true
</pre>

The __summary_ parameter requests the server to return only the elements marked 
as &quot;summary&quot; in their definition. This is used to reduce the total processing load on 
server, client, and resources between them such as the network. It is most useful for 
resources that can be large, particularly ones that include images or elements that
may repeat many times. 

Servers are not obliged to return just a summary, and summaries are not defined for 
resources where there is no need for summarization. There is only one summary form
defined for each resource in order to allow servers to store the summarized form in
advance. 

<a name="conformance"/>

## <span class="sectioncount">2.2<a name="2.2"> </a></span> Server Conformance

In order to allow the client to be confident about what search parameters 
were used as a criteria by the server, the server SHALL return the parameters 
that were actually used to process the search. Applications processing search 
results SHALL check these returned values where necessary. For example, if 
the server did not support some of the filters specified in the search, a 
client might manually apply those filters to the retrieved result set, 
display a warning message to the user or take some other action. 

In the case of a RESTful search, these parameters are encoded in the 
self link in the atom feed that is returned:

<pre class="xml">
  &lt;link rel=&quot;self&quot; href=&quot;http://example.org/Patient?name=peter&quot;/&gt;
</pre>

In other respects, servers have considerable discretion with regards 
to supporting search:

*   Servers can choose which parameters to support (other than _id above)
*   Servers can choose when and where to implement parameter chaining, and when and where they support the _include parameter
*   Servers are able to declare additional parameters in the profiles referenced from their conformance statements. Servers should define search parameters    starting with a &quot;-&quot; character to ensure that the names they choose do not clash with future parameters defined by this specification
*   Servers are not required to enforce case sensitivity on parameter names, though the names are case sensitive (and URLs are generally case-sensitive)
*   Servers may choose how many results to return, though the client can use _count as above
*   Servers can choose how to sort the return results, though they SHOULD honor the _sort parameter

* * *

<a name="advanced"> </a>

## <span class="sectioncount">2.2<a name="2.2"> </a></span> Advanced Search/Query

The search framework described above is a useful framework 
for providing a simple search based on indexed criteria, 
but more sophistication is needed to handle precise 
queries, complex decision support based requests, and 
direct queries that have human resolution.

More advanced search/query operations are specified by the 
_query parameter:

<pre>
   GET [base-url]/Patient?_query=name&amp;parameters...
</pre>

The _query parameter names a custom search profile that
describes a specific search/query operation. The named query
may define additional parameters that are used with that 
particular named query, and  will define their type and 
behavior on repetition and omission. 

FHIR defines some named queries:

*   [Value Set Expansion](valueset.html#expansion)

In addition, servers can define their own additional named
queries to meet their own uses.

There can only ever be one _query parameter in a set of search
parameters. Servers processing search requests SHALL 
refuse to process a search request if they do not recognize 
the _query parameter value.

Some named queries may have side effects such as creating 
new clinical resources that may be persistent or transitory. 
The general search defined above always searches existing 
resources, and the only new resources that may be created 
are [Security Event](securityevent.html) resources 
auditing the search.

## <span class="sectioncount">2.2<a name="2.2"> </a></span> Executing Search / Query

FHIR defines 3 different ways in which a search through a repository of 
resources can be initiated:

*   Perform [search](http.html#search) operation on a RESTful interface (as described above)
*   Send a [query message](messaging.html#query), and receive a query response
*   Use the [query resource](query.html) on a RESTful interface  <!-- , create a query resource with an order, and wait for the order response (this allows asynchronous queries across a RESTful interface) -->

In all 3 cases, the basic operation is simple: given a set of parameters
which are name/value pairs, perform a query against a repository of 
resources, and return the set of matching resources, possibly with 
some additional related resources. The second two search methods are
implemented using the _Query_ Resource.

<a name="currency"> </a>

## <span class="sectioncount">2.2<a name="2.2"> </a></span> Search/Query Result Currency

The results of a search/query operation are only guaranteed to be current
at the moment the operation is executed. After the operation is executed,
ongoing actions performed on the resources against which the query was
executed will render the results increasingly stale. The significance
of this depends on the nature of the search, and the kind of use that 
is being made of the results. 

This is particularly relevant when the server is returning the results
in a series of pages. It is at the discretion of the search engine 
how to handle ongoing updates to the resources while the search 
is proceeding. 

Query result sets may include resources created by the processing of the 
search. Typically, these are the results of queries for decision support,
value set expansion, etc., and represent the outcome of processing the 
query. In order to be usable in the scenarios above, these resources
have a defined structure and have the same metadata as any other resource,
including a known identity, but they have the same currency issues as
the results from a query. 

Applications handling the results of an operation that creates 
resources should use these resources with careful consideration 
of their currency. Though the resources may be retained for audit 
purposes, implementers must be careful not to reuse these as if
they are current.

</div>

<div class="col-3"><div class="itoc">

On This Page:

[Search/Query](#base)

[Standard Parameters](#standard)

[Managing Returned Resources](#return)

[Conformance](#conformance)

[Advanced Query](#advanced)

[Managing Search Results](#currency)

</div></div>

				</div>  <!-- /inner-wrapper -->
            </div>  <!-- /row -->
        </div>  <!-- /container -->

    </div>  <!-- /segment-content -->

	<div id="segment-footer" class="segment">  <!-- segment-footer -->
		<div class="container">  <!-- container -->
			<div class="inner-wrapper">

        &copy; HL7.org 2011 - 2014. FHIR DSTU (v0.2.1-2606) generated on Wed, Jul 2, 2014 16:29+0800.   <!-- [QA Report](qa.html) -->   <!-- achive note -->

        <span style="color: #FFFF77">
        Links: [What's a DSTU?](dstu.html) | 
               [Version History](history.html) | 
               [Compare to DSTU](http://services.w3.org/htmldiff?doc1=http%3A%2F%2Fhl7.org%2Fimplement%2Fstandards%2Ffhir%2Fsearch.html&amp;doc2=http%3A%2F%2Fhl7.org%2Fimplement%2Fstandards%2FFHIR-Develop%2Fsearch.html) | 
               [License](license.html) | 
               [Propose a change](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemAdd&amp;tracker_id=677)   
        </span>

			</div>  <!-- /inner-wrapper -->
		</div>  <!-- /container -->
	</div>  <!-- /segment-footer -->
  <!-- disqus thread -->
  <!-- disqus -->
  <!-- end disqus -->        