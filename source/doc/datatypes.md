title:  
date:  
categories: doc
---
# <span class="sectioncount">1.13.0<a name="1.13.0"> </a></span> Data Types

The FHIR specification defines a set of data types that are used for the 
resource elements. There are two categories of data type: simple / primitive types, imported from XML schema, and complex types, which are re-usable clusters of elements.
This page describes the data types. See also the [Examples](datatypes-examples.html), [Formal Definitions](datatypes-definitions.html) and 
[Mappings](datatypes-mappings.html).

<svg height="218.0" width="574.8" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns="http://www.w3.org/2000/svg" version="1.1">  <defs>
    <filter id="shadow" height="200%" width="200%" y="0" x="0">
      <feOffset result="offOut" dx="3" dy="3" in="SourceGraphic"/>
      <feColorMatrix result="matrixOut" values="0.2 0 0 0 0 0 0.2 0 0 0 0 0 0.2 0 0 0 0 0 1 0" type="matrix" in="offOut"/>
      <feGaussianBlur result="blurOut" stdDeviation="2" in="matrixOut"/>
      <feBlend in2="blurOut" in="SourceGraphic" mode="normal"/>
    </filter>
  </defs><rect height="28.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="50.4" filter="url(#shadow)" rx="4" y="70.0" ry="4" x="150.0"/><text fill="black" class="diagram-class-title" y="90.0" x="175.2">Element</text><rect height="28.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="72.0" filter="url(#shadow)" rx="4" y="0.0" ry="4" x="300.0"/><line style="stroke:dimgrey;stroke-width:1" y1="28.0" y2="28.0" x2="372.0" x1="300.0"/><text fill="black" class="diagram-class-title" y="20.0" x="336.0">[Identifier](#identifier)</text><rect height="28.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="64.8" filter="url(#shadow)" rx="4" y="40.0" ry="4" x="310.0"/><line style="stroke:dimgrey;stroke-width:1" y1="68.0" y2="68.0" x2="374.8" x1="310.0"/><text fill="black" class="diagram-class-title" y="60.0" x="342.4">[HumanName](#humanname)</text><rect height="28.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="50.4" filter="url(#shadow)" rx="4" y="80.0" ry="4" x="315.0"/><line style="stroke:dimgrey;stroke-width:1" y1="108.0" y2="108.0" x2="365.4" x1="315.0"/><text fill="black" class="diagram-class-title" y="100.0" x="340.2">[Address](#address)</text><rect height="28.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="50.4" filter="url(#shadow)" rx="4" y="120.0" ry="4" x="320.0"/><line style="stroke:dimgrey;stroke-width:1" y1="148.0" y2="148.0" x2="370.4" x1="320.0"/><text fill="black" class="diagram-class-title" y="140.0" x="345.2">[Contact](#contact)</text><rect height="28.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="57.6" filter="url(#shadow)" rx="4" y="40.0" ry="4" x="0.0"/><line style="stroke:dimgrey;stroke-width:1" y1="68.0" y2="68.0" x2="57.6" x1="0.0"/><text fill="black" class="diagram-class-title" y="60.0" x="28.8">[Schedule](#schedule)</text><rect height="28.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="57.6" filter="url(#shadow)" rx="4" y="120.0" ry="4" x="140.0"/><line style="stroke:dimgrey;stroke-width:1" y1="148.0" y2="148.0" x2="197.6" x1="140.0"/><text fill="black" class="diagram-class-title" y="140.0" x="168.8">[Quantity](#quantity)</text><rect height="28.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="72.0" filter="url(#shadow)" rx="4" y="0.0" ry="4" x="200.0"/><line style="stroke:dimgrey;stroke-width:1" y1="28.0" y2="28.0" x2="272.0" x1="200.0"/><text fill="black" class="diagram-class-title" y="20.0" x="236.0">[Attachment](#attachment)</text><rect height="28.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="36.0" filter="url(#shadow)" rx="4" y="0.0" ry="4" x="150.0"/><line style="stroke:dimgrey;stroke-width:1" y1="28.0" y2="28.0" x2="186.0" x1="150.0"/><text fill="black" class="diagram-class-title" y="20.0" x="168.0">[Range](#range)</text><rect height="28.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="43.2" filter="url(#shadow)" rx="4" y="0.0" ry="4" x="80.0"/><line style="stroke:dimgrey;stroke-width:1" y1="28.0" y2="28.0" x2="123.2" x1="80.0"/><text fill="black" class="diagram-class-title" y="20.0" x="101.6">[Period](#period)</text><rect height="28.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="36.0" filter="url(#shadow)" rx="4" y="0.0" ry="4" x="15.0"/><line style="stroke:dimgrey;stroke-width:1" y1="28.0" y2="28.0" x2="51.0" x1="15.0"/><text fill="black" class="diagram-class-title" y="20.0" x="33.0">[Ratio](#ratio)</text><rect height="28.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="108.0" filter="url(#shadow)" rx="4" y="120.0" ry="4" x="0.0"/><line style="stroke:dimgrey;stroke-width:1" y1="148.0" y2="148.0" x2="108.0" x1="0.0"/><text fill="black" class="diagram-class-title" y="140.0" x="54.0">[CodeableConcept](#codeableconcept)</text><rect height="28.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="43.2" filter="url(#shadow)" rx="4" y="80.0" ry="4" x="0.0"/><line style="stroke:dimgrey;stroke-width:1" y1="108.0" y2="108.0" x2="43.2" x1="0.0"/><text fill="black" class="diagram-class-title" y="100.0" x="21.6">[Coding](#coding)</text><rect height="28.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="79.2" filter="url(#shadow)" rx="4" y="120.0" ry="4" x="220.0"/><line style="stroke:dimgrey;stroke-width:1" y1="148.0" y2="148.0" x2="299.2" x1="220.0"/><text fill="black" class="diagram-class-title" y="140.0" x="259.6">[SampledData](#sampleddata)</text><rect height="28.0" style="fill:#f8ddf8;stroke:black;stroke-width:1" width="21.6" filter="url(#shadow)" rx="4" y="170.0" ry="4" x="0.0"/><line style="stroke:dimgrey;stroke-width:1" y1="198.0" y2="198.0" x2="21.6" x1="0.0"/><text fill="black" class="diagram-class-title" y="190.0" x="10.8">[Age](#age)</text><rect height="28.0" style="fill:#f8ddf8;stroke:black;stroke-width:1" width="57.6" filter="url(#shadow)" rx="4" y="170.0" ry="4" x="55.0"/><line style="stroke:dimgrey;stroke-width:1" y1="198.0" y2="198.0" x2="112.6" x1="55.0"/><text fill="black" class="diagram-class-title" y="190.0" x="83.8">[Distance](#distance)</text><rect height="28.0" style="fill:#f8ddf8;stroke:black;stroke-width:1" width="57.6" filter="url(#shadow)" rx="4" y="170.0" ry="4" x="140.0"/><line style="stroke:dimgrey;stroke-width:1" y1="198.0" y2="198.0" x2="197.6" x1="140.0"/><text fill="black" class="diagram-class-title" y="190.0" x="168.8">[Duration](#duration)</text><rect height="28.0" style="fill:#f8ddf8;stroke:black;stroke-width:1" width="36.0" filter="url(#shadow)" rx="4" y="170.0" ry="4" x="225.0"/><line style="stroke:dimgrey;stroke-width:1" y1="198.0" y2="198.0" x2="261.0" x1="225.0"/><text fill="black" class="diagram-class-title" y="190.0" x="243.0">[Count](#count)</text><rect height="28.0" style="fill:#f8ddf8;stroke:black;stroke-width:1" width="36.0" filter="url(#shadow)" rx="4" y="170.0" ry="4" x="300.0"/><line style="stroke:dimgrey;stroke-width:1" y1="198.0" y2="198.0" x2="336.0" x1="300.0"/><text fill="black" class="diagram-class-title" y="190.0" x="318.0">[Money](#money)</text><line style="stroke:navy;stroke-width:1" y1="73.02985074626865" y2="28.0" x2="303.84" x1="200.4"/><polygon transform="rotate(-23.52461868412063 200.4 73.02985074626865)" style="fill:white;stroke:navy;stroke-width:1" points="200.4,73.02985074626865 208.4,79.02985074626865 208.4,67.02985074626865 200.4,73.02985074626865"/><line style="stroke:navy;stroke-width:1" y1="79.47846889952152" y2="59.8133971291866" x2="310.0" x1="200.4"/><polygon transform="rotate(-10.172105852287535 200.4 79.47846889952152)" style="fill:white;stroke:navy;stroke-width:1" points="200.4,79.47846889952152 208.4,85.47846889952152 208.4,73.47846889952152 200.4,79.47846889952152"/><line style="stroke:navy;stroke-width:1" y1="85.52727272727272" y2="92.47272727272727" x2="315.0" x1="200.4"/><polygon transform="rotate(3.4682292589171513 200.4 85.52727272727272)" style="fill:white;stroke:navy;stroke-width:1" points="200.4,85.52727272727272 208.4,91.52727272727272 208.4,79.52727272727272 200.4,85.52727272727272"/><line style="stroke:navy;stroke-width:1" y1="91.41176470588235" y2="126.58823529411765" x2="320.0" x1="200.4"/><polygon transform="rotate(16.38954033403479 200.4 91.41176470588235)" style="fill:white;stroke:navy;stroke-width:1" points="200.4,91.41176470588235 208.4,97.41176470588235 208.4,85.41176470588235 200.4,91.41176470588235"/><line style="stroke:navy;stroke-width:1" y1="78.8360655737705" y2="59.90163934426229" x2="57.6" x1="150.0"/><polygon transform="rotate(-168.41938081777187 150.0 78.8360655737705)" style="fill:white;stroke:navy;stroke-width:1" points="150.0,78.8360655737705 158.0,84.8360655737705 158.0,72.8360655737705 150.0,78.8360655737705"/><line style="stroke:navy;stroke-width:1" y1="98.0" y2="120.0" x2="170.59200000000004" x1="173.40800000000002"/><polygon transform="rotate(97.29419630854079 173.40800000000002 98.0)" style="fill:white;stroke:navy;stroke-width:1" points="173.40800000000002,98.0 181.40800000000002,104.0 181.40800000000002,92.0 173.40800000000002,98.0"/><line style="stroke:navy;stroke-width:1" y1="70.0" y2="28.0" x2="223.83999999999997" x1="187.35999999999999"/><polygon transform="rotate(-49.02335231903334 187.35999999999999 70.0)" style="fill:white;stroke:navy;stroke-width:1" points="187.35999999999999,70.0 195.35999999999999,76.0 195.35999999999999,64.0 187.35999999999999,70.0"/><line style="stroke:navy;stroke-width:1" y1="70.0" y2="28.0" x2="169.44" x1="173.76"/><polygon transform="rotate(-95.8726282810668 173.76 70.0)" style="fill:white;stroke:navy;stroke-width:1" points="173.76,70.0 181.76,76.0 181.76,64.0 173.76,70.0"/><line style="stroke:navy;stroke-width:1" y1="69.99999999999999" y2="28.0" x2="116.32" x1="160.47999999999996"/><polygon transform="rotate(-136.43608364184578 160.47999999999996 69.99999999999999)" style="fill:white;stroke:navy;stroke-width:1" points="160.47999999999996,69.99999999999999 168.47999999999996,75.99999999999999 168.47999999999996,63.999999999999986 160.47999999999996,69.99999999999999"/><line style="stroke:navy;stroke-width:1" y1="71.59493670886076" y2="22.860759493670884" x2="51.0" x1="150.0"/><polygon transform="rotate(-153.79061782922898 150.0 71.59493670886076)" style="fill:white;stroke:navy;stroke-width:1" points="150.0,71.59493670886076 158.0,77.59493670886076 158.0,65.59493670886076 150.0,71.59493670886076"/><line style="stroke:navy;stroke-width:1" y1="94.3960396039604" y2="120.0" x2="87.93600000000004" x1="150.0"/><polygon transform="rotate(157.5818325742615 150.0 94.3960396039604)" style="fill:white;stroke:navy;stroke-width:1" points="150.0,94.3960396039604 158.0,100.3960396039604 158.0,88.3960396039604 150.0,94.3960396039604"/><line style="stroke:navy;stroke-width:1" y1="85.640625" y2="92.59375" x2="43.2" x1="150.0"/><polygon transform="rotate(176.27506286658965 150.0 85.640625)" style="fill:white;stroke:navy;stroke-width:1" points="150.0,85.640625 158.0,91.640625 158.0,79.640625 150.0,85.640625"/><line style="stroke:navy;stroke-width:1" y1="98.0" y2="120.00000000000003" x2="235.96800000000007" x1="198.832"/><polygon transform="rotate(30.643224046543462 198.832 98.0)" style="fill:white;stroke:navy;stroke-width:1" points="198.832,98.0 206.832,104.0 206.832,92.0 198.832,98.0"/><line style="stroke:navy;stroke-width:1" y1="143.11392405063293" y2="180.58227848101268" x2="21.6" x1="140.0"/><polygon transform="rotate(162.43972794819933 140.0 143.11392405063293)" style="fill:white;stroke:navy;stroke-width:1" points="140.0,143.11392405063293 148.0,149.11392405063293 148.0,137.11392405063293 140.0,143.11392405063293"/><line style="stroke:navy;stroke-width:1" y1="148.0" y2="170.00000000000003" x2="107.5999999999999" x1="144.99999999999994"/><polygon transform="rotate(149.53445508054014 144.99999999999994 148.0)" style="fill:white;stroke:navy;stroke-width:1" points="144.99999999999994,148.0 152.99999999999994,154.0 152.99999999999994,142.0 144.99999999999994,148.0"/><line style="stroke:navy;stroke-width:1" y1="148.0" y2="170.00000000000003" x2="168.8" x1="168.8"/><polygon transform="rotate(90.0 168.8 148.0)" style="fill:white;stroke:navy;stroke-width:1" points="168.8,148.0 176.8,154.0 176.8,142.0 168.8,148.0"/><line style="stroke:navy;stroke-width:1" y1="148.0" y2="171.87061994609167" x2="225.0" x1="189.576"/><polygon transform="rotate(33.97423521213204 189.576 148.0)" style="fill:white;stroke:navy;stroke-width:1" points="189.576,148.0 197.576,154.0 197.576,142.0 189.576,148.0"/><line style="stroke:navy;stroke-width:1" y1="143.65147453083108" y2="177.96782841823057" x2="300.0" x1="197.6"/><polygon transform="rotate(18.52706414470336 197.6 143.65147453083108)" style="fill:white;stroke:navy;stroke-width:1" points="197.6,143.65147453083108 205.6,149.65147453083108 205.6,137.65147453083108 197.6,143.65147453083108"/></svg>

The data types are available as a [W3C Schema](fhir-base.xsd).

<a name="primitive"/>

## <span class="sectioncount">1.13.0.1<a name="1.13.0.1"> </a></span> Primitive Types

<svg height="248.0" width="800.0" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns="http://www.w3.org/2000/svg" version="1.1">  <defs>
    <filter id="shadow" height="200%" width="200%" y="0" x="0">
      <feOffset result="offOut" dx="3" dy="3" in="SourceGraphic"/>
      <feColorMatrix result="matrixOut" values="0.2 0 0 0 0 0 0.2 0 0 0 0 0 0.2 0 0 0 0 0 1 0" type="matrix" in="offOut"/>
      <feGaussianBlur result="blurOut" stdDeviation="2" in="matrixOut"/>
      <feBlend in2="blurOut" in="SourceGraphic" mode="normal"/>
    </filter>
  </defs><rect height="46.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="104.0" filter="url(#shadow)" rx="4" y="80.0" ry="4" x="180.0"/><text fill="black" class="diagram-class-title" y="100.0" x="232.0">Element</text><line style="stroke:dimgrey;stroke-width:1" y1="108.0" y2="108.0" x2="284.0" x1="180.0"/><text fill="black" class="diagram-class-detail" y="122.0" x="186.0">[<title>Extensions - as described for all elements: additional information that is not part of the basic definition of the resource / type</title>extension](extensibility.html) : [Extension](extensibility.html) 0..*</text><rect height="50.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="92.0" filter="url(#shadow)" rx="4" y="70.0" ry="4" x="0.0"/><line style="stroke:dimgrey;stroke-width:1" y1="98.0" y2="98.0" x2="92.0" x1="0.0"/><text fill="black" class="diagram-class-title" y="90.0" x="46.0">[Decimal](#decimal)</text><text fill="black" class="diagram-class-detail" y="112.0" x="6.0"><tspan><title>Actual value attribute of the data type</title>value</tspan> : [xs:decimal](http://www.w3.org/TR/xmlschema-2/#decimal) 0..1</text><rect height="50.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="76.0" filter="url(#shadow)" rx="4" y="130.0" ry="4" x="0.0"/><line style="stroke:dimgrey;stroke-width:1" y1="158.0" y2="158.0" x2="76.0" x1="0.0"/><text fill="black" class="diagram-class-title" y="150.0" x="38.0">[Integer](#integer)</text><text fill="black" class="diagram-class-detail" y="172.0" x="6.0"><tspan><title>Actual value attribute of the data type</title>value</tspan> : [xs:int](http://www.w3.org/TR/xmlschema-2/#int) 0..1</text><rect height="50.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="92.0" filter="url(#shadow)" rx="4" y="70.0" ry="4" x="420.0"/><line style="stroke:dimgrey;stroke-width:1" y1="98.0" y2="98.0" x2="512.0" x1="420.0"/><text fill="black" class="diagram-class-title" y="90.0" x="466.0">[Boolean](#boolean)</text><text fill="black" class="diagram-class-detail" y="112.0" x="426.0"><tspan><title>Actual value attribute of the data type</title>value</tspan> : [xs:boolean](http://www.w3.org/TR/xmlschema-2/#boolean) 0..1</text><rect height="50.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="96.0" filter="url(#shadow)" rx="4" y="0.0" ry="4" x="0.0"/><line style="stroke:dimgrey;stroke-width:1" y1="28.0" y2="28.0" x2="96.0" x1="0.0"/><text fill="black" class="diagram-class-title" y="20.0" x="48.0">[Instant](#instant)</text><text fill="black" class="diagram-class-detail" y="42.0" x="6.0"><tspan><title>Actual value attribute of the data type</title>value</tspan> : [xs:dateTime](http://www.w3.org/TR/xmlschema-2/#dateTime) 0..1</text><rect height="50.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="172.0" filter="url(#shadow)" rx="4" y="0.0" ry="4" x="130.0"/><line style="stroke:dimgrey;stroke-width:1" y1="28.0" y2="28.0" x2="302.0" x1="130.0"/><text fill="black" class="diagram-class-title" y="20.0" x="216.0">[Date](#date)</text><text fill="black" class="diagram-class-detail" y="42.0" x="136.0"><tspan><title>Actual value attribute of the data type</title>value</tspan> : [xs:gYear](http://www.w3.org/TR/xmlschema-2/#gYear)|[xs:gYearMonth](http://www.w3.org/TR/xmlschema-2/#gYearMonth)|[xs:date](http://www.w3.org/TR/xmlschema-2/#date) 0..1</text><rect height="50.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="112.0" filter="url(#shadow)" rx="4" y="130.0" ry="4" x="420.0"/><line style="stroke:dimgrey;stroke-width:1" y1="158.0" y2="158.0" x2="532.0" x1="420.0"/><text fill="black" class="diagram-class-title" y="150.0" x="476.0">[Base64Binary](#base64binary)</text><text fill="black" class="diagram-class-detail" y="172.0" x="426.0"><tspan><title>Actual value attribute of the data type</title>value</tspan> : [xs:base64Binary](http://www.w3.org/TR/xmlschema-2/#base64Binary) 0..1</text><rect height="50.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="88.0" filter="url(#shadow)" rx="4" y="140.0" ry="4" x="130.0"/><line style="stroke:dimgrey;stroke-width:1" y1="168.0" y2="168.0" x2="218.0" x1="130.0"/><text fill="black" class="diagram-class-title" y="160.0" x="174.0">[String](#string)</text><text fill="black" class="diagram-class-detail" y="182.0" x="136.0"><tspan><title>Actual value attribute of the data type</title>value</tspan> : [xs:string](http://www.w3.org/TR/xmlschema-2/#string) 0..1</text><rect height="28.0" style="fill:#f8ddf8;stroke:black;stroke-width:1" width="28.8" filter="url(#shadow)" rx="4" y="200.0" ry="4" x="30.0"/><line style="stroke:dimgrey;stroke-width:1" y1="228.0" y2="228.0" x2="58.8" x1="30.0"/><text fill="black" class="diagram-class-title" y="220.0" x="44.4">[Code](#code)</text><rect height="50.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="220.0" filter="url(#shadow)" rx="4" y="0.0" ry="4" x="380.0"/><line style="stroke:dimgrey;stroke-width:1" y1="28.0" y2="28.0" x2="600.0" x1="380.0"/><text fill="black" class="diagram-class-title" y="20.0" x="490.0">[DateTime](#datetime)</text><text fill="black" class="diagram-class-detail" y="42.0" x="386.0"><tspan><title>Actual value attribute of the data type</title>value</tspan> : [xs:gYear](http://www.w3.org/TR/xmlschema-2/#gYear)|[xs:gYearMonth](http://www.w3.org/TR/xmlschema-2/#gYearMonth)|[xs:date](http://www.w3.org/TR/xmlschema-2/#date)|[xs:dateTime](http://www.w3.org/TR/xmlschema-2/#dateTime) 0..1</text><rect height="28.0" style="fill:#f8ddf8;stroke:black;stroke-width:1" width="14.4" filter="url(#shadow)" rx="4" y="200.0" ry="4" x="100.0"/><line style="stroke:dimgrey;stroke-width:1" y1="228.0" y2="228.0" x2="114.4" x1="100.0"/><text fill="black" class="diagram-class-title" y="220.0" x="107.2">[Id](#id)</text><rect height="50.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="88.0" filter="url(#shadow)" rx="4" y="140.0" ry="4" x="260.0"/><line style="stroke:dimgrey;stroke-width:1" y1="168.0" y2="168.0" x2="348.0" x1="260.0"/><text fill="black" class="diagram-class-title" y="160.0" x="304.0">[Uri](#uri)</text><text fill="black" class="diagram-class-detail" y="182.0" x="266.0"><tspan><title>Actual value attribute of the data type</title>value</tspan> : [xs:anyURI](http://www.w3.org/TR/xmlschema-2/#anyURI) 0..1</text><rect height="28.0" style="fill:#f8ddf8;stroke:black;stroke-width:1" width="21.6" filter="url(#shadow)" rx="4" y="200.0" ry="4" x="380.0"/><line style="stroke:dimgrey;stroke-width:1" y1="228.0" y2="228.0" x2="401.6" x1="380.0"/><text fill="black" class="diagram-class-title" y="220.0" x="390.8">[Oid](#oid)</text><rect height="28.0" style="fill:#f8ddf8;stroke:black;stroke-width:1" width="28.8" filter="url(#shadow)" rx="4" y="200.0" ry="4" x="450.0"/><line style="stroke:dimgrey;stroke-width:1" y1="228.0" y2="228.0" x2="478.8" x1="450.0"/><text fill="black" class="diagram-class-title" y="220.0" x="464.4">[Uuid](#uuid)</text><line style="stroke:navy;stroke-width:1" y1="100.76344086021504" y2="96.9784946236559" x2="92.0" x1="180.0"/><polygon transform="rotate(-177.53718332408314 180.0 100.76344086021504)" style="fill:white;stroke:navy;stroke-width:1" points="180.0,100.76344086021504 188.0,106.76344086021504 188.0,94.76344086021504 180.0,100.76344086021504"/><line style="stroke:navy;stroke-width:1" y1="116.93814432989691" y2="144.81443298969072" x2="76.0" x1="180.0"/><polygon transform="rotate(164.9950796171398 180.0 116.93814432989691)" style="fill:white;stroke:navy;stroke-width:1" points="180.0,116.93814432989691 188.0,122.93814432989691 188.0,110.93814432989691 180.0,116.93814432989691"/><line style="stroke:navy;stroke-width:1" y1="101.22222222222223" y2="96.57264957264957" x2="420.0" x1="284.0"/><polygon transform="rotate(-1.9580674292340465 284.0 101.22222222222223)" style="fill:white;stroke:navy;stroke-width:1" points="284.0,101.22222222222223 292.0,107.22222222222223 292.0,95.22222222222223 284.0,101.22222222222223"/><line style="stroke:navy;stroke-width:1" y1="80.95652173913044" y2="45.34782608695652" x2="96.0" x1="180.0"/><polygon transform="rotate(-157.02727866917132 180.0 80.95652173913044)" style="fill:white;stroke:navy;stroke-width:1" points="180.0,80.95652173913044 188.0,86.95652173913044 188.0,74.95652173913044 180.0,80.95652173913044"/><line style="stroke:navy;stroke-width:1" y1="80.0" y2="50.0" x2="221.12820512820514" x1="227.28205128205127"/><polygon transform="rotate(-101.59217541029105 227.28205128205127 80.0)" style="fill:white;stroke:navy;stroke-width:1" points="227.28205128205127,80.0 235.28205128205127,86.0 235.28205128205127,74.0 227.28205128205127,80.0"/><line style="stroke:navy;stroke-width:1" y1="114.08196721311475" y2="143.0655737704918" x2="420.0" x1="284.0"/><polygon transform="rotate(12.030596096537868 284.0 114.08196721311475)" style="fill:white;stroke:navy;stroke-width:1" points="284.0,114.08196721311475 292.0,120.08196721311475 292.0,108.08196721311475 284.0,114.08196721311475"/><line style="stroke:navy;stroke-width:1" y1="126.0" y2="140.0" x2="197.38709677419357" x1="210.48387096774195"/><polygon transform="rotate(133.0908475670036 210.48387096774195 126.0)" style="fill:white;stroke:navy;stroke-width:1" points="210.48387096774195,126.0 218.48387096774195,132.0 218.48387096774195,120.0 210.48387096774195,126.0"/><line style="stroke:navy;stroke-width:1" y1="181.6358024691358" y2="208.55555555555554" x2="58.8" x1="130.0"/><polygon transform="rotate(159.28907553741217 130.0 181.6358024691358)" style="fill:white;stroke:navy;stroke-width:1" points="130.0,181.6358024691358 138.0,187.6358024691358 138.0,175.6358024691358 130.0,181.6358024691358"/><line style="stroke:navy;stroke-width:1" y1="87.27906976744187" y2="50.0" x2="407.3076923076923" x1="284.0"/><polygon transform="rotate(-16.82140989004083 284.0 87.27906976744187)" style="fill:white;stroke:navy;stroke-width:1" points="284.0,87.27906976744187 292.0,93.27906976744187 292.0,81.27906976744187 284.0,87.27906976744187"/><line style="stroke:navy;stroke-width:1" y1="190.0" y2="208.7185628742515" x2="114.4" x1="139.91836734693877"/><polygon transform="rotate(143.73872608095996 139.91836734693877 190.0)" style="fill:white;stroke:navy;stroke-width:1" points="139.91836734693877,190.0 147.91836734693877,196.0 147.91836734693877,184.0 139.91836734693877,190.0"/><line style="stroke:navy;stroke-width:1" y1="126.0" y2="140.0" x2="274.96774193548384" x1="258.7096774193548"/><polygon transform="rotate(40.732106699709206 258.7096774193548 126.0)" style="fill:white;stroke:navy;stroke-width:1" points="258.7096774193548,126.0 266.7096774193548,132.0 266.7096774193548,120.0 258.7096774193548,126.0"/><line style="stroke:navy;stroke-width:1" y1="189.83870967741933" y2="207.9032258064516" x2="380.0" x1="348.0"/><polygon transform="rotate(29.445428729925595 348.0 189.83870967741933)" style="fill:white;stroke:navy;stroke-width:1" points="348.0,189.83870967741933 356.0,195.83870967741933 356.0,183.83870967741933 348.0,189.83870967741933"/><line style="stroke:navy;stroke-width:1" y1="178.44139650872822" y2="209.60099750623448" x2="450.0" x1="348.0"/><polygon transform="rotate(16.987193185898402 348.0 178.44139650872822)" style="fill:white;stroke:navy;stroke-width:1" points="348.0,178.44139650872822 356.0,184.44139650872822 356.0,172.44139650872822 348.0,178.44139650872822"/></svg>

<a name="imports"> </a>

The following table summarizes the primitive types and their simple restrictions that
are used in throughout this specification. Primitive types are those without sub-properties, though primitives, like all types, have [extensions](extensibility.html).
Primitive types have a value which has the same value domain as defined in the [W3C Schema (1.0) specification part 2](http://www.w3.org/TR/xmlschema-2/), 
though in a few cases, this specification makes additional constraints marked in bold. 

<a name="boolean"> </a>
<a name="integer"> </a>
<a name="decimal"> </a>
<a name="base64Binary"> </a>
<a name="base64binary"> </a>
<a name="instant"> </a>
<a name="string"> </a>
<a name="uri"> </a>
<a name="date"> </a>
<a name="dateTime"> </a>
<a name="datetime"> </a>

<table class="list">
 <tr>
   <td colspan="3">**Primitive Types**</td>
 </tr>
 <tr>
   <th>FHIR Name</th><th>Schema type</th><th>Description</th>
 </tr>
 <tr>
   <td>boolean</td><td>xs:boolean</td><td>Values can be either true or false (**0 and 1 are not valid values**)</td>
 </tr>
 <tr>
   <td>integer</td><td>xs:int</td><td>A signed 32-bit integer (for larger values, use decimal)</td>
 </tr>
 <tr>
   <td>decimal</td><td>xs:decimal</td><td>A rational number. Note: for implementations, do not use a IEEE type floating point 
      type, instead use something that works like a true decimal, with inbuilt precision (e.g. Java BigDecimal). Decimals may 
	  not use exponents.</td>
 </tr>
 <tr>
   <td>base64Binary</td><td>xs:base64Binary</td><td>A stream of bytes, base64 encoded ([RFC 4648](http://tools.ietf.org/html/rfc4648))</td>
 </tr>
 <tr>
   <td>instant</td><td>xs:dateTime</td><td>An instant in time - **known at least to the second and always includes a time zone**. 
   Note: This type is for system times, not human times (see date and dateTime below).</td>
 </tr>
 <tr>
   <td>string</td><td>xs:string</td><td>A sequence of Unicode characters. **Note that strings SHALL NOT exceed 1MB in size**</td>
 </tr>
 <tr>
   <td>uri</td><td>xs:anyURI</td><td>A Uniform Resource Identifier Reference. It can be absolute or relative, 
    and may have an optional fragment identifier ([RFC 3986](http://tools.ietf.org/html/rfc3986))</td>
 </tr>
 <tr><td>date</td><td>union of xs:date, xs:gYearMonth, xs:gYear</td><td>A date, or partial date (e.g. just year or year + month) as used 
 in human communication. There is no time zone. Dates SHALL be valid dates. 
date is a union of the w3c schema types date, gYearMonth, 
 and gYear
regex: -?([1-9][0-9]{3}|0[0-9]{3})(-(0[1-9]|1[0-2])(-(0[1-9]|[12][0-9]|3[01]))?)?</td></tr>
 <tr><td>dateTime</td><td>union of xs:dateTime, xs:date, xs:gYearMonth, xs:gYear</td><td>A date, date-time or partial date (e.g. just year or year + month)
 as used in human communication. If hours and minutes are specified, a time zone SHALL be populated. Seconds may be provided but may also be ignored.
 Dates SHALL be valid dates. 
dateTime is a union of the w3c schema types dateTime, date, gYearMonth, gYear

 regex:-?([1-9][0-9]{3}|0[0-9]{3})(-(0[1-9]|1[0-2])(-(0[1-9]|[12][0-9]|3[01])(T(([01][0-9]|2[0-3]):[0-5][0-9]:[0-5][0-9](\.[0-9]+)?|(24:00:00(\.0+)?))(Z|(\+|-)((0[0-9]|1[0-3]):[0-5][0-9]|14:00))?)?)?)?
_Note: not all restrictions imposed on this type can be expressed using regular expressions, so this regex still allows a broader set of values than
allowed by FHIR_
 </td></tr>
 <tr><td colspan="3"/></tr>
 <tr>
   <td colspan="3">**Simple Restrictions** <a name="patterns"/>
<a name="code"> </a>
<a name="oid"> </a>
<a name="uuid"> </a>
<a name="id"> </a></td>
 </tr>
 <tr>
   <th>FHIR Name</th><th>Base FHIR Type</th><th>Description</th>
 </tr>
 <tr><td>code</td><td>string</td><td>Indicates that the value is taken from a set of controlled strings defined elsewhere (see [Using codes](terminologies.html) for further discussion). Technically, a code is restricted to string which has at least one character and no leading or trailing whitespace, and where there is no whitespace other than single spaces in the contents 
regex: [^\s]+([\s]+[^\s]+)*</td></tr>
 <tr><td>oid</td><td>uri</td><td>An OID represented as a URI ([RFC 3001](http://www.ietf.org/rfc/rfc3001.txt)): urn:oid:1.2.3.4.5</td></tr>
 <tr><td>uuid</td><td>uri</td><td>A UUID, represented as a URI ([RFC 4122](http://www.ietf.org/rfc/rfc4122.txt)): urn:uuid:a5afddf4-e880-459b-876e-e4591b0acc11. Note the RFC comments about case: UUID values SHALL be represented in lower case, but systems SHOULD interpret them case insensitively</td></tr>
 <tr><td>id</td><td>string</td><td>A whole number in the range 0 to 2^64-1 (optionally represented in hex), a uuid, an oid, or any other combination of lowercase letters, numerals, &quot;-&quot; and &quot;.&quot;, with a length limit of 36 characters 
regex: [a-z0-9\-\.]{1,36}</td></tr>
</table>

In addition to having a value as described above, these primitive data types can also have an identity (e.g. xml:id), 
and they may have [extensions](extensibility.html) like any other element in a resource. Note that the 
value option is optional and might not be present, following the [standard rules for all elements](formats.html#element-rules).
For instance, a primitive element might have no value, and include a [data-absent-reason extension](general-extensions.html#data-absent-reason) instead.

In XML, these types are represented as XML Elements with the value of the type in the value attribute. 
The name of the element is defined where the type is used. The XML elements may have an [id attribute](references.html#idref), and child elements named &quot;extension&quot;. 
According to XML schema, leading and trailing whitespace in the value attribute is ignored for the types 
boolean, integer, decimal, base64Binary, instant, uri, date, dateTime, oid, and uri. Note that this means that the 
schema aware XML libraries give different attribute values to non schema aware libraries when reading the 
XML instances. For this reason, the value attribute for these types SHOULD not have leading and trailing spaces.
String values should only have leading and trailing spaces if they are part of the content of the value. 

In JSON, these types are represented as simple properties of the object that contains them. The name of the property is defined where the type is used.
The types still have an id property, and extensions. How these are represented is described in the [JSON format](json.html). Whitespace
is always significant in JSON. Primitive types other than string SHALL NOT have leading or trailing whitespace.

* * *

<a name="Types"/>

## <span class="sectioncount">1.13.0.2<a name="1.13.0.2"> </a></span> Complex Types

These types are represented as XML Elements with child elements with the name of the defined elements of the type. The name of the element is defined where the type is used. 
Any of the XML elements may have an [id attribute](references.html#idref). In JSON, the data type is represented by an object with properties named the same as the
XML elements. The JSON representation is almost exactly the same, so only the first [example](datatypes-examples.html#Attachment) has an additional JSON representation.

Complex data types may be &quot;profiled&quot;. A [profile](profile.html) makes 
a set of rules about which elements SHALL have values, and what the possible 
values are.

**UML Diagrams of the Data types**

<svg height="370.0" width="802.0" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns="http://www.w3.org/2000/svg" version="1.1">  <defs>
    <filter id="shadow" height="200%" width="200%" y="0" x="0">
      <feOffset result="offOut" dx="3" dy="3" in="SourceGraphic"/>
      <feColorMatrix result="matrixOut" values="0.2 0 0 0 0 0 0.2 0 0 0 0 0 0.2 0 0 0 0 0 1 0" type="matrix" in="offOut"/>
      <feGaussianBlur result="blurOut" stdDeviation="2" in="matrixOut"/>
      <feBlend in2="blurOut" in="SourceGraphic" mode="normal"/>
    </filter>
  </defs><rect height="46.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="104.0" filter="url(#shadow)" rx="4" y="150.0" ry="4" x="300.0"/><text fill="black" class="diagram-class-title" y="170.0" x="352.0">Element</text><line style="stroke:dimgrey;stroke-width:1" y1="178.0" y2="178.0" x2="404.0" x1="300.0"/><text fill="black" class="diagram-class-detail" y="192.0" x="306.0">[<title>Extensions - as described for all elements: additional information that is not part of the basic definition of the resource / type</title>extension](extensibility.html) : [Extension](extensibility.html) 0..*</text><rect height="106.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="196.0" filter="url(#shadow)" rx="4" y="135.0" ry="4" x="0.0"/><line style="stroke:dimgrey;stroke-width:1" y1="163.0" y2="163.0" x2="196.0" x1="0.0"/><text fill="black" class="diagram-class-title" y="155.0" x="98.0">[Quantity](#quantity)</text><text fill="black" class="diagram-class-detail" y="177.0" x="6.0">[<title>The value of the measured amount. The value includes an implicit precision in the presentation of the value</title>value](datatypes-definitions.html#Quantity.value) : [decimal](datatypes.html#decimal) 0..1</text><text fill="black" class="diagram-class-detail" y="191.0" x="6.0">[<title>How the value should be understood and represented - whether the actual value is greater or less than the stated value due to measurement issues. E.g. if the comparator is &quot;&lt;&quot; , then the real value is &lt; stated value (this element modifies the meaning of other elements)</title>comparator](datatypes-definitions.html#Quantity.comparator) : [code](datatypes.html#code) 0..1 芦 [<title>How the Quantity should be understood and represented</title>QuantityCompararator](quantity-comparator.html) 禄</text><text fill="black" class="diagram-class-detail" y="205.0" x="6.0">[<title>A human-readable form of the units</title>units](datatypes-definitions.html#Quantity.units) : [string](datatypes.html#string) 0..1</text><text fill="black" class="diagram-class-detail" y="219.0" x="6.0">[<title>The identification of the system that provides the coded form of the unit</title>system](datatypes-definitions.html#Quantity.system) : [uri](datatypes.html#uri) 0..1</text><text fill="black" class="diagram-class-detail" y="233.0" x="6.0">[<title>A computer processable form of the units in some unit representation system</title>code](datatypes-definitions.html#Quantity.code) : [code](datatypes.html#code) 0..1</text><rect height="134.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="152.0" filter="url(#shadow)" rx="4" y="120.0" ry="4" x="450.0"/><line style="stroke:dimgrey;stroke-width:1" y1="148.0" y2="148.0" x2="602.0" x1="450.0"/><text fill="black" class="diagram-class-title" y="140.0" x="526.0">[Attachment](#attachment)</text><text fill="black" class="diagram-class-detail" y="162.0" x="456.0">[<title>Identifies the type of the data in the attachment and allows a method to be chosen to interpret or render the data. Includes mime type parameters such as charset where appropriate</title>contentType](datatypes-definitions.html#Attachment.contentType) : [code](datatypes.html#code) 1..1 芦 [<title>The mime type of an attachment</title>MimeType](http://www.rfc-editor.org/bcp/bcp13.txt) 禄</text><text fill="black" class="diagram-class-detail" y="176.0" x="456.0">[<title>The human language of the content. The value can be any valid value according to BCP 47</title>language](datatypes-definitions.html#Attachment.language) : [code](datatypes.html#code) 0..1 芦 [<title>A human language</title>Language](http://tools.ietf.org/html/bcp47) 禄</text><text fill="black" class="diagram-class-detail" y="190.0" x="456.0">[<title>The actual data of the attachment - a sequence of bytes. In XML, represented using base64</title>data](datatypes-definitions.html#Attachment.data) : [base64Binary](datatypes.html#base64Binary) 0..1</text><text fill="black" class="diagram-class-detail" y="204.0" x="456.0">[<title>An alternative location where the data can be accessed</title>url](datatypes-definitions.html#Attachment.url) : [uri](datatypes.html#uri) 0..1</text><text fill="black" class="diagram-class-detail" y="218.0" x="456.0">[<title>The number of bytes of data that make up this attachment</title>size](datatypes-definitions.html#Attachment.size) : [integer](datatypes.html#integer) 0..1</text><text fill="black" class="diagram-class-detail" y="232.0" x="456.0">[<title>The calculated hash of the data using SHA-1. Represented using base64</title>hash](datatypes-definitions.html#Attachment.hash) : [base64Binary](datatypes.html#base64Binary) 0..1</text><text fill="black" class="diagram-class-detail" y="246.0" x="456.0">[<title>A label or set of text to display in place of the data</title>title](datatypes-definitions.html#Attachment.title) : [string](datatypes.html#string) 0..1</text><rect height="64.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="88.0" filter="url(#shadow)" rx="4" y="260.0" ry="4" x="40.0"/><line style="stroke:dimgrey;stroke-width:1" y1="288.0" y2="288.0" x2="128.0" x1="40.0"/><text fill="black" class="diagram-class-title" y="280.0" x="84.0">[Range](#range)</text><text fill="black" class="diagram-class-detail" y="302.0" x="46.0">[<title>The low limit. The boundary is inclusive</title>low](datatypes-definitions.html#Range.low) : [Quantity](datatypes.html#Quantity) 0..1</text><text fill="black" class="diagram-class-detail" y="316.0" x="46.0">[<title>The high limit. The boundary is inclusive</title>high](datatypes-definitions.html#Range.high) : [Quantity](datatypes.html#Quantity) 0..1</text><rect height="64.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="92.0" filter="url(#shadow)" rx="4" y="50.0" ry="4" x="380.0"/><line style="stroke:dimgrey;stroke-width:1" y1="78.0" y2="78.0" x2="472.0" x1="380.0"/><text fill="black" class="diagram-class-title" y="70.0" x="426.0">[Period](#period)</text><text fill="black" class="diagram-class-detail" y="92.0" x="386.0">[<title>The start of the period. The boundary is inclusive</title>start](datatypes-definitions.html#Period.start) : [dateTime](datatypes.html#dateTime) 0..1</text><text fill="black" class="diagram-class-detail" y="106.0" x="386.0">[<title>The end of the period. If the end of the period is missing, it means that the period is ongoing</title>end](datatypes-definitions.html#Period.end) : [dateTime](datatypes.html#dateTime) 0..1</text><rect height="64.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="116.0" filter="url(#shadow)" rx="4" y="50.0" ry="4" x="40.0"/><line style="stroke:dimgrey;stroke-width:1" y1="78.0" y2="78.0" x2="156.0" x1="40.0"/><text fill="black" class="diagram-class-title" y="70.0" x="98.0">[Ratio](#ratio)</text><text fill="black" class="diagram-class-detail" y="92.0" x="46.0">[<title>The value of the numerator</title>numerator](datatypes-definitions.html#Ratio.numerator) : [Quantity](datatypes.html#Quantity) 0..1</text><text fill="black" class="diagram-class-detail" y="106.0" x="46.0">[<title>The value of the denominator</title>denominator](datatypes-definitions.html#Ratio.denominator) : [Quantity](datatypes.html#Quantity) 0..1</text><rect height="64.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="108.0" filter="url(#shadow)" rx="4" y="260.0" ry="4" x="450.0"/><line style="stroke:dimgrey;stroke-width:1" y1="288.0" y2="288.0" x2="558.0" x1="450.0"/><text fill="black" class="diagram-class-title" y="280.0" x="504.0">[CodeableConcept](#codeableconcept)</text><text fill="black" class="diagram-class-detail" y="302.0" x="456.0">[<title>A reference to a code defined by a terminology system</title>coding](datatypes-definitions.html#CodeableConcept.coding) : [Coding](datatypes.html#Coding) 0..*</text><text fill="black" class="diagram-class-detail" y="316.0" x="456.0">[<title>A human language representation of the concept as seen/selected/uttered by the user who entered the data and/or which represents the intended meaning of the user</title>text](datatypes-definitions.html#CodeableConcept.text) : [string](datatypes.html#string) 0..1</text><rect height="120.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="144.0" filter="url(#shadow)" rx="4" y="230.0" ry="4" x="240.0"/><line style="stroke:dimgrey;stroke-width:1" y1="258.0" y2="258.0" x2="384.0" x1="240.0"/><text fill="black" class="diagram-class-title" y="250.0" x="312.0">[Coding](#coding)</text><text fill="black" class="diagram-class-detail" y="272.0" x="246.0">[<title>The identification of the code system that defines the meaning of the symbol in the code</title>system](datatypes-definitions.html#Coding.system) : [uri](datatypes.html#uri) 0..1</text><text fill="black" class="diagram-class-detail" y="286.0" x="246.0">[<title>The version of the code system which was used when choosing this code. Note that a well-maintained code system does not need the version reported, because the meaning of codes is consistent across versions. However this cannot consistently be assured. and When the meaning is not guaranteed to be consistent, the version SHOULD be exchanged</title>version](datatypes-definitions.html#Coding.version) : [string](datatypes.html#string) 0..1</text><text fill="black" class="diagram-class-detail" y="300.0" x="246.0">[<title>A symbol in syntax defined by the system. The symbol may be a predefined code or an expression in a syntax defined by the coding system (e.g. post-coordination)</title>code](datatypes-definitions.html#Coding.code) : [code](datatypes.html#code) 0..1</text><text fill="black" class="diagram-class-detail" y="314.0" x="246.0">[<title>A representation of the meaning of the code in the system, following the rules of the system</title>display](datatypes-definitions.html#Coding.display) : [string](datatypes.html#string) 0..1</text><text fill="black" class="diagram-class-detail" y="328.0" x="246.0">[<title>Indicates that this code was chosen by a user directly - i.e. off a pick list of available items (codes or displays)</title>primary](datatypes-definitions.html#Coding.primary) : [boolean](datatypes.html#boolean) 0..1</text><text fill="black" class="diagram-class-detail" y="342.0" x="246.0">[<title>The set of possible coded values this coding was chosen from or constrained by</title>valueSet](datatypes-definitions.html#Coding.valueSet) : [Resource](references.html#Resource)([ValueSet](valueset.html#ValueSet)) 0..1</text><rect height="134.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="108.0" filter="url(#shadow)" rx="4" y="0.0" ry="4" x="260.0"/><line style="stroke:dimgrey;stroke-width:1" y1="28.0" y2="28.0" x2="368.0" x1="260.0"/><text fill="black" class="diagram-class-title" y="20.0" x="314.0">[SampledData](#sampleddata)</text><text fill="black" class="diagram-class-detail" y="42.0" x="266.0">[<title>The base quantity that a measured value of zero represents. In addition, this provides the units of the entire measurement series</title>origin](datatypes-definitions.html#SampledData.origin) : [Quantity](datatypes.html#Quantity) 1..1</text><text fill="black" class="diagram-class-detail" y="56.0" x="266.0">[<title>The length of time between sampling times, measured in milliseconds</title>period](datatypes-definitions.html#SampledData.period) : [decimal](datatypes.html#decimal) 1..1</text><text fill="black" class="diagram-class-detail" y="70.0" x="266.0">[<title>A correction factor that is applied to the sampled data points before they are added to the origin</title>factor](datatypes-definitions.html#SampledData.factor) : [decimal](datatypes.html#decimal) 0..1</text><text fill="black" class="diagram-class-detail" y="84.0" x="266.0">[<title>The lower limit of detection of the measured points. This is needed if any of the data points have the value &quot;L&quot; (lower than detection limit)</title>lowerLimit](datatypes-definitions.html#SampledData.lowerLimit) : [decimal](datatypes.html#decimal) 0..1</text><text fill="black" class="diagram-class-detail" y="98.0" x="266.0">[<title>The upper limit of detection of the measured points. This is needed if any of the data points have the value &quot;U&quot; (higher than detection limit)</title>upperLimit](datatypes-definitions.html#SampledData.upperLimit) : [decimal](datatypes.html#decimal) 0..1</text><text fill="black" class="diagram-class-detail" y="112.0" x="266.0">[<title>The number of sample points at each time point. If this value is greater than one, then the dimensions will be interlaced - all the sample points for a point in time will be recorded at once</title>dimensions](datatypes-definitions.html#SampledData.dimensions) : [integer](datatypes.html#integer) 1..1</text><text fill="black" class="diagram-class-detail" y="126.0" x="266.0">[<title>A series of data points which are decimal values separated by a single space (character u20). The special values &quot;E&quot; (error), &quot;L&quot; (below detection limit) and &quot;U&quot; (above detection limit) can also be used in place of a decimal value</title>data](datatypes-definitions.html#SampledData.data) : [string](datatypes.html#string) 1..1</text><line style="stroke:navy;stroke-width:1" y1="176.07086614173227" y2="182.21259842519683" x2="196.0" x1="300.0"/><polygon transform="rotate(176.62031621667734 300.0 176.07086614173227)" style="fill:white;stroke:navy;stroke-width:1" points="300.0,176.07086614173227 308.0,182.07086614173227 308.0,170.07086614173227 300.0,176.07086614173227"/><line style="stroke:navy;stroke-width:1" y1="177.183908045977" y2="180.88505747126436" x2="450.0" x1="404.0"/><polygon transform="rotate(4.600095666263278 404.0 177.183908045977)" style="fill:white;stroke:navy;stroke-width:1" points="404.0,177.183908045977 412.0,183.183908045977 412.0,171.183908045977 404.0,177.183908045977"/><line style="stroke:navy;stroke-width:1" y1="196.0" y2="272.4626865671642" x2="128.0" x1="300.20168067226894"/><polygon transform="rotate(156.0573502834631 300.20168067226894 196.0)" style="fill:white;stroke:navy;stroke-width:1" points="300.20168067226894,196.0 308.20168067226894,202.0 308.20168067226894,190.0 300.20168067226894,196.0"/><line style="stroke:navy;stroke-width:1" y1="150.0" y2="114.0" x2="399.97802197802196" x1="370.7032967032967"/><polygon transform="rotate(-50.88244559009536 370.7032967032967 150.0)" style="fill:white;stroke:navy;stroke-width:1" points="370.7032967032967,150.0 378.7032967032967,156.0 378.7032967032967,144.0 370.7032967032967,150.0"/><line style="stroke:navy;stroke-width:1" y1="154.37007874015745" y2="102.77952755905511" x2="156.0" x1="300.0"/><polygon transform="rotate(-160.28903731265814 300.0 154.37007874015745)" style="fill:white;stroke:navy;stroke-width:1" points="300.0,154.37007874015745 308.0,160.37007874015745 308.0,148.37007874015745 300.0,154.37007874015745"/><line style="stroke:navy;stroke-width:1" y1="196.0" y2="260.0" x2="463.12605042016804" x1="381.3781512605042"/><polygon transform="rotate(38.05720496157285 381.3781512605042 196.0)" style="fill:white;stroke:navy;stroke-width:1" points="381.3781512605042,196.0 389.3781512605042,202.0 389.3781512605042,190.0 381.3781512605042,196.0"/><line style="stroke:navy;stroke-width:1" y1="196.0" y2="230.0" x2="332.5128205128205" x1="344.13675213675214"/><polygon transform="rotate(108.87454975820334 344.13675213675214 196.0)" style="fill:white;stroke:navy;stroke-width:1" points="344.13675213675214,196.0 352.13675213675214,202.0 352.13675213675214,190.0 344.13675213675214,196.0"/><line style="stroke:navy;stroke-width:1" y1="150.0" y2="134.0" x2="338.01886792452837" x1="343.7547169811321"/><polygon transform="rotate(-109.72227776444696 343.7547169811321 150.0)" style="fill:white;stroke:navy;stroke-width:1" points="343.7547169811321,150.0 351.7547169811321,156.0 351.7547169811321,144.0 343.7547169811321,150.0"/></svg>

<svg height="315.0" width="870.0" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns="http://www.w3.org/2000/svg" version="1.1">  <defs>
    <filter id="shadow" height="200%" width="200%" y="0" x="0">
      <feOffset result="offOut" dx="3" dy="3" in="SourceGraphic"/>
      <feColorMatrix result="matrixOut" values="0.2 0 0 0 0 0 0.2 0 0 0 0 0 0.2 0 0 0 0 0 1 0" type="matrix" in="offOut"/>
      <feGaussianBlur result="blurOut" stdDeviation="2" in="matrixOut"/>
      <feBlend in2="blurOut" in="SourceGraphic" mode="normal"/>
    </filter>
  </defs><rect height="46.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="104.0" filter="url(#shadow)" rx="4" y="180.0" ry="4" x="230.0"/><text fill="black" class="diagram-class-title" y="200.0" x="282.0">Element</text><line style="stroke:dimgrey;stroke-width:1" y1="208.0" y2="208.0" x2="334.0" x1="230.0"/><text fill="black" class="diagram-class-detail" y="222.0" x="236.0">[<title>Extensions - as described for all elements: additional information that is not part of the basic definition of the resource / type</title>extension](extensibility.html) : [Extension](extensibility.html) 0..*</text><rect height="120.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="160.0" filter="url(#shadow)" rx="4" y="160.0" ry="4" x="0.0"/><line style="stroke:dimgrey;stroke-width:1" y1="188.0" y2="188.0" x2="160.0" x1="0.0"/><text fill="black" class="diagram-class-title" y="180.0" x="80.0">[Identifier](#identifier)</text><text fill="black" class="diagram-class-detail" y="202.0" x="6.0">[<title>The purpose of this identifier (this element modifies the meaning of other elements)</title>use](datatypes-definitions.html#Identifier.use) : [code](datatypes.html#code) 0..1 芦 [<title>Identifies the purpose for this identifier, if known</title>IdentifierUse](identifier-use.html) 禄</text><text fill="black" class="diagram-class-detail" y="216.0" x="6.0">[<title>A text string for the identifier that can be displayed to a human so they can recognize the identifier</title>label](datatypes-definitions.html#Identifier.label) : [string](datatypes.html#string) 0..1</text><text fill="black" class="diagram-class-detail" y="230.0" x="6.0">[<title>Establishes the namespace in which set of possible id values is unique</title>system](datatypes-definitions.html#Identifier.system) : [uri](datatypes.html#uri) 0..1</text><text fill="black" class="diagram-class-detail" y="244.0" x="6.0">[<title>The portion of the identifier typically displayed to the user and which is unique within the context of the system</title>value](datatypes-definitions.html#Identifier.value) : [string](datatypes.html#string) 0..1</text><text fill="black" class="diagram-class-detail" y="258.0" x="6.0">[<title>Time period during which identifier is/was valid for use</title>period](datatypes-definitions.html#Identifier.period) : [Period](datatypes.html#Period) 0..1</text><text fill="black" class="diagram-class-detail" y="272.0" x="6.0">[<title>Organization that issued/manages the identifier</title>assigner](datatypes-definitions.html#Identifier.assigner) : [Resource](references.html#Resource)([Organization](organization.html#Organization)) 0..1</text><rect height="134.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="116.0" filter="url(#shadow)" rx="4" y="10.0" ry="4" x="0.0"/><line style="stroke:dimgrey;stroke-width:1" y1="38.0" y2="38.0" x2="116.0" x1="0.0"/><text fill="black" class="diagram-class-title" y="30.0" x="58.0">[HumanName](#humanname)</text><text fill="black" class="diagram-class-detail" y="52.0" x="6.0">[<title>Identifies the purpose for this name (this element modifies the meaning of other elements)</title>use](datatypes-definitions.html#HumanName.use) : [code](datatypes.html#code) 0..1 芦 [<title>The use of a human name</title>NameUse](name-use.html) 禄</text><text fill="black" class="diagram-class-detail" y="66.0" x="6.0">[<title>A full text representation of the name</title>text](datatypes-definitions.html#HumanName.text) : [string](datatypes.html#string) 0..1</text><text fill="black" class="diagram-class-detail" y="80.0" x="6.0">[<title>The part of a name that links to the genealogy. In some cultures (e.g. Eritrea) the family name of a son is the first name of his father</title>family](datatypes-definitions.html#HumanName.family) : [string](datatypes.html#string) 0..*</text><text fill="black" class="diagram-class-detail" y="94.0" x="6.0">[<title>Given name</title>given](datatypes-definitions.html#HumanName.given) : [string](datatypes.html#string) 0..*</text><text fill="black" class="diagram-class-detail" y="108.0" x="6.0">[<title>Part of the name that is acquired as a title due to academic, legal, employment or nobility status, etc. and that appears at the start of the name</title>prefix](datatypes-definitions.html#HumanName.prefix) : [string](datatypes.html#string) 0..*</text><text fill="black" class="diagram-class-detail" y="122.0" x="6.0">[<title>Part of the name that is acquired as a title due to academic, legal, employment or nobility status, etc. and that appears at the end of the name</title>suffix](datatypes-definitions.html#HumanName.suffix) : [string](datatypes.html#string) 0..*</text><text fill="black" class="diagram-class-detail" y="136.0" x="6.0">[<title>Indicates the period of time when this name was valid for the named person</title>period](datatypes-definitions.html#HumanName.period) : [Period](datatypes.html#Period) 0..1</text><rect height="148.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="128.0" filter="url(#shadow)" rx="4" y="0.0" ry="4" x="200.0"/><line style="stroke:dimgrey;stroke-width:1" y1="28.0" y2="28.0" x2="328.0" x1="200.0"/><text fill="black" class="diagram-class-title" y="20.0" x="264.0">[Address](#address)</text><text fill="black" class="diagram-class-detail" y="42.0" x="206.0">[<title>The purpose of this address (this element modifies the meaning of other elements)</title>use](datatypes-definitions.html#Address.use) : [code](datatypes.html#code) 0..1 芦 [<title>The use of an address</title>AddressUse](address-use.html) 禄</text><text fill="black" class="diagram-class-detail" y="56.0" x="206.0">[<title>A full text representation of the address</title>text](datatypes-definitions.html#Address.text) : [string](datatypes.html#string) 0..1</text><text fill="black" class="diagram-class-detail" y="70.0" x="206.0">[<title>This component contains the house number, apartment number, street name, street direction, 
P.O. Box number, delivery hints, and similar address information</title>line](datatypes-definitions.html#Address.line) : [string](datatypes.html#string) 0..*</text><text fill="black" class="diagram-class-detail" y="84.0" x="206.0">[<title>The name of the city, town, village or other community or delivery center</title>city](datatypes-definitions.html#Address.city) : [string](datatypes.html#string) 0..1</text><text fill="black" class="diagram-class-detail" y="98.0" x="206.0">[<title>Sub-unit of a country with limited sovereignty in a federally organized country. A code may be used if codes are in common use (i.e. US 2 letter state codes)</title>state](datatypes-definitions.html#Address.state) : [string](datatypes.html#string) 0..1</text><text fill="black" class="diagram-class-detail" y="112.0" x="206.0">[<title>A postal code designating a region defined by the postal service</title>zip](datatypes-definitions.html#Address.zip) : [string](datatypes.html#string) 0..1</text><text fill="black" class="diagram-class-detail" y="126.0" x="206.0">[<title>Country - a nation as commonly understood or generally accepted</title>country](datatypes-definitions.html#Address.country) : [string](datatypes.html#string) 0..1</text><text fill="black" class="diagram-class-detail" y="140.0" x="206.0">[<title>Time period when address was/is in use</title>period](datatypes-definitions.html#Address.period) : [Period](datatypes.html#Period) 0..1</text><rect height="92.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="152.0" filter="url(#shadow)" rx="4" y="20.0" ry="4" x="410.0"/><line style="stroke:dimgrey;stroke-width:1" y1="48.0" y2="48.0" x2="562.0" x1="410.0"/><text fill="black" class="diagram-class-title" y="40.0" x="486.0">[Contact](#contact)</text><text fill="black" class="diagram-class-detail" y="62.0" x="416.0">[<title>Telecommunications form for contact - what communications system is required to make use of the contact</title>system](datatypes-definitions.html#Contact.system) : [code](datatypes.html#code) 0..1 芦 [<title>Telecommunications form for contact</title>ContactSystem](contact-system.html) 禄</text><text fill="black" class="diagram-class-detail" y="76.0" x="416.0">[<title>The actual contact details, in a form that is meaningful to the designated communication system (i.e. phone number or email address)</title>value](datatypes-definitions.html#Contact.value) : [string](datatypes.html#string) 0..1</text><text fill="black" class="diagram-class-detail" y="90.0" x="416.0">[<title>Identifies the purpose for the address (this element modifies the meaning of other elements)</title>use](datatypes-definitions.html#Contact.use) : [code](datatypes.html#code) 0..1 芦 [<title>Location, type or status of telecommunications address indicating use</title>ContactUse](contact-use.html) 禄</text><text fill="black" class="diagram-class-detail" y="104.0" x="416.0">[<title>Time period when the contact was/is in use</title>period](datatypes-definitions.html#Contact.period) : [Period](datatypes.html#Period) 0..1</text><rect height="50.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="84.0" filter="url(#shadow)" rx="4" y="245.0" ry="4" x="240.0"/><line style="stroke:dimgrey;stroke-width:1" y1="273.0" y2="273.0" x2="324.0" x1="240.0"/><text fill="black" class="diagram-class-title" y="265.0" x="282.0">[Schedule](#schedule)</text><text fill="black" class="diagram-class-detail" y="287.0" x="246.0">[<title>Identifies specific time periods when the event should occur</title>event](datatypes-definitions.html#Schedule.event) : [Period](datatypes.html#Period) 0..*</text><rect height="120.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="140.0" filter="url(#shadow)" rx="4" y="160.0" ry="4" x="430.0"/><line style="stroke:dimgrey;stroke-width:1" y1="188.0" y2="188.0" x2="570.0" x1="430.0"/><text fill="black" class="diagram-class-title" y="180.0" x="500.0">Repeat</text><text fill="black" class="diagram-class-detail" y="202.0" x="436.0">[<title>Indicates how often the event should occur</title>frequency](datatypes-definitions.html#Schedule.repeat.frequency) : [integer](datatypes.html#integer) 0..1</text><text fill="black" class="diagram-class-detail" y="216.0" x="436.0">[<title>Identifies the occurrence of daily life that determines timing</title>when](datatypes-definitions.html#Schedule.repeat.when) : [code](datatypes.html#code) 0..1 芦 [<title>Real world event that the schedule relates to</title>EventTiming](event-timing.html) 禄</text><text fill="black" class="diagram-class-detail" y="230.0" x="436.0">[<title>How long each repetition should last</title>duration](datatypes-definitions.html#Schedule.repeat.duration) : [decimal](datatypes.html#decimal) 1..1</text><text fill="black" class="diagram-class-detail" y="244.0" x="436.0">[<title>The units of time for the duration</title>units](datatypes-definitions.html#Schedule.repeat.units) : [code](datatypes.html#code) 1..1 芦 [<title>A unit of time (units from UCUM)</title>UnitsOfTime](units-of-time.html) 禄</text><text fill="black" class="diagram-class-detail" y="258.0" x="436.0">[<title>A total count of the desired number of repetitions</title>count](datatypes-definitions.html#Schedule.repeat.count) : [integer](datatypes.html#integer) 0..1</text><text fill="black" class="diagram-class-detail" y="272.0" x="436.0">[<title>When to stop repeating the schedule</title>end](datatypes-definitions.html#Schedule.repeat.end) : [dateTime](datatypes.html#dateTime) 0..1</text><line style="stroke:navy;stroke-width:1" y1="207.37623762376236" y2="213.26732673267327" x2="160.0" x1="230.0"/><polygon transform="rotate(175.18941380563436 230.0 207.37623762376236)" style="fill:white;stroke:navy;stroke-width:1" points="230.0,207.37623762376236 238.0,213.37623762376236 238.0,201.37623762376236 230.0,207.37623762376236"/><line style="stroke:navy;stroke-width:1" y1="180.0" y2="109.625" x2="116.0" x1="241.11111111111111"/><polygon transform="rotate(-150.64224645720873 241.11111111111111 180.0)" style="fill:white;stroke:navy;stroke-width:1" points="241.11111111111111,180.0 249.11111111111111,186.0 249.11111111111111,174.0 241.11111111111111,180.0"/><line style="stroke:navy;stroke-width:1" y1="180.0" y2="148.0" x2="274.3255813953488" x1="278.7906976744186"/><polygon transform="rotate(-97.94347181059044 278.7906976744186 180.0)" style="fill:white;stroke:navy;stroke-width:1" points="278.7906976744186,180.0 286.7906976744186,186.0 286.7906976744186,174.0 278.7906976744186,180.0"/><line style="stroke:navy;stroke-width:1" y1="180.0" y2="112.0" x2="417.50364963503654" x1="316.24817518248176"/><polygon transform="rotate(-33.88407055266841 316.24817518248176 180.0)" style="fill:white;stroke:navy;stroke-width:1" points="316.24817518248176,180.0 324.24817518248176,186.0 324.24817518248176,174.0 316.24817518248176,180.0"/><line style="stroke:navy;stroke-width:1" y1="260.3669724770642" y2="236.05504587155963" x2="430.0" x1="324.0"/><polygon transform="rotate(-12.91781284393396 324.0 260.3669724770642)" style="fill:navy;stroke:navy;stroke-width:1" points="324.0,260.3669724770642 330.0,264.3669724770642 336.0,260.3669724770642 330.0,256.3669724770642 324.0,260.3669724770642"/><rect height="18.0" style="fill:white;stroke:black;stroke-width:0" width="24.0" y="241.0" x="365.0"/><text fill="black" class="diagram-class-linkage" y="251.0" x="377.0">[<title>Identifies a repeating pattern to the intended time periods</title>repeat](datatypes-definitions.html#Schedule.repeat)</text><text fill="black" class="diagram-class-linkage" y="232.05504587155963" x="410.0">0..1</text><line style="stroke:navy;stroke-width:1" y1="226.0" y2="245.0" x2="282.0" x1="282.0"/><polygon transform="rotate(90.0 282.0 226.0)" style="fill:white;stroke:navy;stroke-width:1" points="282.0,226.0 290.0,232.0 290.0,220.0 282.0,226.0"/></svg>

<a name="Attachment"/>
<a name="attachment"/>

## <span class="sectioncount">1.13.0.3<a name="1.13.0.3"> </a></span> 
Attachment

See also [Examples](datatypes-examples.html#Attachment), [Formal Definitions](datatypes-definitions.html#Attachment) and [Mappings](datatypes-mappings.html#Attachment).

This type is for containing or referencing attachments - additional data content defined in other 
formats. The most common use of this type is to include images or reports in 
some report format such as PDF. However it can be used for any 
data that has a mime type. 

<pre class="spec">
&lt;[**[name]**](datatypes-definitions.html#Attachment "For referring to data content defined in other formats.") xmlns=&quot;http://hl7.org/fhir&quot;&gt; <span style="float: right">[![doco](help.png)](formats.html "Documentation for this format")</span>
 &lt;!-- from Element: [extension](extensibility.html) --&gt;
 &lt;[**contentType**](datatypes-definitions.html#Attachment.contentType "Identifies the type of the data in the attachment and allows a method to be chosen to interpret or render the data. Includes mime type parameters such as charset where appropriate.") value=&quot;[<span style="color: darkgreen">[code](datatypes.html#code)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**1..1**</span> <span style="color: navy">[Mime type of the content, with charset etc.](http://www.rfc-editor.org/bcp/bcp13.txt.html)</span><span style="color: Gray"> --&gt;</span>
 &lt;[**language**](datatypes-definitions.html#Attachment.language "The human language of the content. The value can be any valid value according to BCP 47.") value=&quot;[<span style="color: darkgreen">[code](datatypes.html#code)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..1**</span> <span style="color: navy">[Human language of the content (BCP-47)](http://tools.ietf.org/html/bcp47.html)</span><span style="color: Gray"> --&gt;</span>
 &lt;[**data**](datatypes-definitions.html#Attachment.data "The actual data of the attachment - a sequence of bytes. In XML, represented using base64.") value=&quot;[<span style="color: darkgreen">[base64Binary](datatypes.html#base64Binary)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..1**</span> <span style="color: navy">Data inline, base64ed</span><span style="color: Gray"> --&gt;</span>
 &lt;[**url**](datatypes-definitions.html#Attachment.url "An alternative location where the data can be accessed.") value=&quot;[<span style="color: darkgreen">[uri](datatypes.html#uri)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..1**</span> <span style="color: navy">Uri where the data can be found</span><span style="color: Gray"> --&gt;</span>
 &lt;[**size**](datatypes-definitions.html#Attachment.size "The number of bytes of data that make up this attachment.") value=&quot;[<span style="color: darkgreen">[integer](datatypes.html#integer)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..1**</span> <span style="color: navy">Number of bytes of content (if url provided)</span><span style="color: Gray"> --&gt;</span>
 &lt;[**hash**](datatypes-definitions.html#Attachment.hash "The calculated hash of the data using SHA-1. Represented using base64.") value=&quot;[<span style="color: darkgreen">[base64Binary](datatypes.html#base64Binary)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..1**</span> <span style="color: navy">Hash of the data (sha-1, base64ed )</span><span style="color: Gray"> --&gt;</span>
 &lt;[**title**](datatypes-definitions.html#Attachment.title "A label or set of text to display in place of the data.") value=&quot;[<span style="color: darkgreen">[string](datatypes.html#string)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..1**</span> <span style="color: navy">Label to display in place of the data</span><span style="color: Gray"> --&gt;</span>
&lt;/[name]&gt;
</pre>

<table style="border: 0px; font-size: 11px; font-family: verdana; vertical-align: top;" cellpadding="0" border="0" cellspacing="0"><tr style="border: 1px #F0F0F0 solid; font-size: 11px; font-family: verdana; vertical-align: top;"><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Name</th><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Card.</th><th style="width: 100px" class="heirarchy">Type</th><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Description &amp; Constraints</th></tr><tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck1.png)" class="heirarchy">![.](tbl_spacer.png)![.](icon_element.gif) <span title="For referring to data content defined in other formats.">Attachment</span><a name="Attachment"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy"/><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Element</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Content in a format defined elsewhere</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_primitive.png) <span title="Identifies the type of the data in the attachment and allows a method to be chosen to interpret or render the data. Includes mime type parameters such as charset where appropriate.">contentType</span><a name="Attachment.contentType"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">1..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[code](datatypes.html#code)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Mime type of the content, with charset etc.
[MimeType](http://www.rfc-editor.org/bcp/bcp13.txt "The mime type of an attachment") ([Required](terminologies.html#code "One of the the defined codes must be used"))</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_primitive.png) <span title="The human language of the content. The value can be any valid value according to BCP 47.">language</span><a name="Attachment.language"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[code](datatypes.html#code)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Human language of the content (BCP-47)
[Language](http://tools.ietf.org/html/bcp47 "A human language") ([Required](terminologies.html#code "One of the the defined codes must be used"))</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_primitive.png) <span title="The actual data of the attachment - a sequence of bytes. In XML, represented using base64.">data</span><a name="Attachment.data"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[base64Binary](datatypes.html#base64Binary)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Data inline, base64ed</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_primitive.png) <span title="An alternative location where the data can be accessed.">url</span><a name="Attachment.url"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[uri](datatypes.html#uri)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Uri where the data can be found</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_primitive.png) <span title="The number of bytes of data that make up this attachment.">size</span><a name="Attachment.size"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[integer](datatypes.html#integer)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Number of bytes of content (if url provided)</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_primitive.png) <span title="The calculated hash of the data using SHA-1. Represented using base64.">hash</span><a name="Attachment.hash"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[base64Binary](datatypes.html#base64Binary)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Hash of the data (sha-1, base64ed )</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck00.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin_end.png)![.](icon_primitive.png) <span title="A label or set of text to display in place of the data.">title</span><a name="Attachment.title"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[string](datatypes.html#string)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Label to display in place of the data</td></tr>
</table>Alternate definitions: Resource Profile ([XML](Attachment.profile.xml.html), [JSON](Attachment.profile.json.html))

### <span class="sectioncount">1.13.0.3.1<a name="1.13.0.3.1"> </a></span> 
Terminology Bindings

<table class="grid">
 <tr><th>Path</th><th>Definition</th><th>Type</th><th>Reference</th></tr>
 <tr><td title="MimeType" valign="top">Attachment.contentType </td><td valign="top">The mime type of an attachment</td><td>[Incomplete](terminologies.html#incomplete)</td><td valign="top">[BCP 13 (RFCs 2045, 2046, 2047, 4288, 4289 and 2049)](http://www.rfc-editor.org/bcp/bcp13.txt)</td> </tr>
 <tr><td title="Language" valign="top">Attachment.language </td><td valign="top">A human language</td><td>[Incomplete](terminologies.html#incomplete)</td><td valign="top">[IETF language tag](http://tools.ietf.org/html/bcp47)</td> </tr>
</table>

The _contentType_ element SHALL always be populated. It can include charset information 
and other mime type extensions as appropriate. If there is no character set in the _contentType_
then the correct course of action is undefined, though some media types may define a default
character set and/or the correct character set may be able to be determined by inspection of the content.

The actual content of the 
Attachment can be conveyed directly using the _data_ element
or a _URL_ reference can be provided. If both are provided, the reference SHALL 
point to the same content as found in the data. The reference can never be reused to point to
some different data (i.e. the reference is version specific). The
_URL_ reference SHALL point to a location that resolves to actual data; some
URIs such as cid: meet this requirement. If the URL is a relative reference, it is interpreted
in the same way as a [resource reference](references.html#references).

The _hash_ is included so that applications can verify that the content returned by the URL has not changed. 

In many cases where Attachment is used, the cardinality is &gt;1. A valid use of repeats is to convey the same content in different mime types and languages.
Guidance on the meaning of repeating elements SHALL be provided in the definition of the repeating resource element or extension that references this type.
The language element describes the language of the attachment using the [codes defined in BCP 47](http://tools.ietf.org/html/bcp47).

<div class="use">

**Constraints**

If neither _data_ nor a _URL_ 
is provided, the value should be understood as an assertion that no content for 
the specified _mimeType_ and/or _language_ is available for the reason stated.

The context of use may frequently make rules about the kind of attachment
(and therefore, the kind of mime types) that can be used.

</div>

Attachment is used in the following places: [Media](media.html), [Practitioner](practitioner.html), [DiagnosticReport](diagnosticreport.html), [Observation](observation.html), [RelatedPerson](relatedperson.html) and [Patient](patient.html)

<a name="Coding"> </a>
<a name="coding"> </a>
<a name="codesystem"> </a>

## <span class="sectioncount">1.13.0.4<a name="1.13.0.4"> </a></span> Coding

See also [Examples](datatypes-examples.html#Coding), [Formal Definitions](datatypes-definitions.html#Coding) and [Mappings](datatypes-mappings.html#Coding).

A Coding is a representation of a defined concept using a symbol from a defined &quot;code system&quot;
- see [Using Codes in resources](terminologies.html) for more details.

<pre class="spec">
&lt;[**[name]**](datatypes-definitions.html#Coding "A reference to a code defined by a terminology system.") xmlns=&quot;http://hl7.org/fhir&quot;&gt; <span style="float: right">[![doco](help.png)](formats.html "Documentation for this format")</span>
 &lt;!-- from Element: [extension](extensibility.html) --&gt;
 &lt;[**system**](datatypes-definitions.html#Coding.system "The identification of the code system that defines the meaning of the symbol in the code.") value=&quot;[<span style="color: darkgreen">[uri](datatypes.html#uri)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..1**</span> <span style="color: navy">Identity of the terminology system</span><span style="color: Gray"> --&gt;</span>
 &lt;[**version**](datatypes-definitions.html#Coding.version "The version of the code system which was used when choosing this code. Note that a well-maintained code system does not need the version reported, because the meaning of codes is consistent across versions. However this cannot consistently be assured. and When the meaning is not guaranteed to be consistent, the version SHOULD be exchanged.") value=&quot;[<span style="color: darkgreen">[string](datatypes.html#string)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..1**</span> <span style="color: navy">Version of the system - if relevant</span><span style="color: Gray"> --&gt;</span>
 &lt;[**code**](datatypes-definitions.html#Coding.code "A symbol in syntax defined by the system. The symbol may be a predefined code or an expression in a syntax defined by the coding system (e.g. post-coordination).") value=&quot;[<span style="color: darkgreen">[code](datatypes.html#code)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..1**</span> <span style="color: navy">Symbol in syntax defined by the system</span><span style="color: Gray"> --&gt;</span>
 &lt;[**display**](datatypes-definitions.html#Coding.display "A representation of the meaning of the code in the system, following the rules of the system.") value=&quot;[<span style="color: darkgreen">[string](datatypes.html#string)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..1**</span> <span style="color: navy">Representation defined by the system</span><span style="color: Gray"> --&gt;</span>
 &lt;[**primary**](datatypes-definitions.html#Coding.primary "Indicates that this code was chosen by a user directly - i.e. off a pick list of available items (codes or displays).") value=&quot;[<span style="color: darkgreen">[boolean](datatypes.html#boolean)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..1**</span> <span style="color: navy">If this code was chosen directly by the user</span><span style="color: Gray"> --&gt;</span>
 &lt;[**valueSet**](datatypes-definitions.html#Coding.valueSet "The set of possible coded values this coding was chosen from or constrained by.")&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..1**</span> <span style="color: darkgreen">[Resource](references.html#Resource)([ValueSet](valueset.html#ValueSet))</span> <span style="color: navy">Set this coding was chosen from</span><span style="color: Gray"> --&gt;</span>&lt;/valueSet&gt;
&lt;/[name]&gt;
</pre>

<table style="border: 0px; font-size: 11px; font-family: verdana; vertical-align: top;" cellpadding="0" border="0" cellspacing="0"><tr style="border: 1px #F0F0F0 solid; font-size: 11px; font-family: verdana; vertical-align: top;"><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Name</th><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Card.</th><th style="width: 100px" class="heirarchy">Type</th><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Description &amp; Constraints</th></tr><tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck1.png)" class="heirarchy">![.](tbl_spacer.png)![.](icon_element.gif) <span title="A reference to a code defined by a terminology system.">Coding</span><a name="Coding"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy"/><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Element</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">A reference to a code defined by a terminology system
<span title="1">If a valueSet is provided, a system URI Is required</span></td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_primitive.png) <span title="The identification of the code system that defines the meaning of the symbol in the code.">system</span><a name="Coding.system"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[uri](datatypes.html#uri)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Identity of the terminology system</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_primitive.png) <span title="The version of the code system which was used when choosing this code. Note that a well-maintained code system does not need the version reported, because the meaning of codes is consistent across versions. However this cannot consistently be assured. and When the meaning is not guaranteed to be consistent, the version SHOULD be exchanged.">version</span><a name="Coding.version"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[string](datatypes.html#string)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Version of the system - if relevant</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_primitive.png) <span title="A symbol in syntax defined by the system. The symbol may be a predefined code or an expression in a syntax defined by the coding system (e.g. post-coordination).">code</span><a name="Coding.code"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[code](datatypes.html#code)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Symbol in syntax defined by the system</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_primitive.png) <span title="A representation of the meaning of the code in the system, following the rules of the system.">display</span><a name="Coding.display"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[string](datatypes.html#string)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Representation defined by the system</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_primitive.png) <span title="Indicates that this code was chosen by a user directly - i.e. off a pick list of available items (codes or displays).">primary</span><a name="Coding.primary"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[boolean](datatypes.html#boolean)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">If this code was chosen directly by the user</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck00.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin_end.png)![.](icon_reference.png) <span title="The set of possible coded values this coding was chosen from or constrained by.">valueSet</span><a name="Coding.valueSet"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[ValueSet](valueset.html)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Set this coding was chosen from</td></tr>
</table>Alternate definitions: Resource Profile ([XML](Coding.profile.xml.html), [JSON](Coding.profile.json.html))

The meaning of the Coding is defined by the code. The _system_ provides
the source of the definition of the code, along with an optional version reference.
The display is a human display for the text defined by the system - it adds no other 
value. The Value Set reference provides context information about the selection of the 
code. 

The _system_ is a URI that references the code system that defines the _code_. 
The URI may be: 

*   a URI defined in the [the named systems list](terminologies-systems.html)
*   an OID (urn:oid:) or a UUID (urn:uuid:). OIDs and UUIDs may be registered in the [HL7 OID registry](http://hl7.org/oid)
*   a URL that references a definition of the system directly, which may be a reference to a code system defined as part of [ValueSet](valueset.html) resource (i.e. the value in _ValueSet.define.system_)
*   or any other URI that uniquely identifies the code system definition

The correct value to use in the _system_ for a given code system can be determined by working through the following list, in order:

*   the [Named Systems List](terminologies-systems.html) section
*   the [HL7 OID Registry](http://www.hl7.org/oid/index.cfm?ref=common)
*   the documentation associated with the code system
*   consulting the owner of the code system
*   asking on the HL7 vocabulary mailing list

A code system version may also be supplied. If the meaning of codes within the code system is consistent across releases, this is not required. 
The version SHOULD be exchanged when this the system does not maintain consistent definitions across versions.
If a value set is referenced, and the value set defines the code system, and the code system definition specifies a version, the version SHALL be the same as in the value set. 
Note that the following systems SHOULD always have a version specified:

*   [LOINC](http://loinc.org)
*   Various versions of ICD
*   National releases of SNOMED CT (consistency of definitions varies amongst jurisdications, and some jurisdictions may make their own rules on this)

See the [discussion of code system versions in the Value Set resource](valueset.html#versioning) for further discussion on versioning.

If present, the _code_ SHALL be a syntactically correct symbol as defined by the _system_.
In some code systems such as SNOMED CT, the symbol may be an expression composed of other predefined symbol (e.g. post-coordination). 
Note that codes are case sensitive unless specified otherwise by the code system. The _display_ 
is a text representation of the code defined by the _system_ and is used to display 
the meaning of the code by an application that is not aware of the _system_. 

Where the code system defines multiple possible display strings, one of these SHALL be used in _display_. 
If one is labelled as preferred, it SHOULD be used. If the code system does not define a text representation 
(e.g. SNOMED CT Expressions) then _display_ cannot be populated, and the meaning of the code won't be 
accessible to systems that don't understand the code expression.

In some cases, the _system_ may not be known - only the code is known. 
In this case, no useful processing of the code may be performed unless
the system can be safely inferred by the context. 
This practice should be avoided where possible, as 
information sharing in a wider context is very likely to arise eventually, and codes cannot
be used in the absence of a known system.

If the system is present, and there is no code, then this is understood to mean that there
is no suitable code in the system in which to represent the code. 

If two codings have the same _system_, _version_ and _code_ then they have the same meaning.
If the version information is missing, or the _system_, _version_ or the _code_ elements differ, then 
how they codes are related can only be determined by consulting the definitions of the system(s) and any [mappings](conceptmap.html) available.

A coding may be marked as a &quot;primary&quot; if a user selected the particular coded value 
in a user interface (e.g. the user selects an item in a picklist). A primary
is the preferred choice for performing translations etc. 

A reference to a [value set](valueset.html) may be provided to help a user or system processing the code
to understand the context in which the code arose. In some contexts, the possible
set of codes from which the code was chosen influences how the code should be 
interpreted. A value set reference is not an acceptable substitute for a logical
URI in the system, and the system URI SHALL not contain a reference to a value set. 
(If the value set defines its own codes, then the correct value for the 
system is _ValueSet.define.system_, and the value set contains a direct reference
to the value set resource.

  <!-- 

### Version Management

Some code systems have periodic releases where the meanings of the codes are changed between
each release. Other code systems provide multiple releases where only minor consistent changes 
are allowed - mainly the addition of new codes. Finally, a few code systems provide an elaborate 
set of policies and procedures to allow concepts to be refined and modified within a single
definitional space. For the second two types of code system, it may help with implementation 
and interpretation tasks to track which minor release (version) of the code system is in use. 

For SNOMED CT, the minor release (and optionally module/release) are indicated as part of the 
_system_ element using the http://snomed.info/sct identifier as defined by SNOMED CT. For
all other code systems, the _version_ element is used to indicate the minor release. 
In the absence of a specified version release format by the code system (such as 2.36 for 
LOINC), the release date is to be used.

The _version_ element SHALL always be ignored when comparing _Coding_ values

 -->
<div class="use">

**Constraints**

  <!-- 

*   **Inv-1**: If a valueSet is provided, a system URI Is required (xpath: <span style="font-family: Courier New, monospace">not (exists(f:valueSet) and exists(f:code)) or exists(f:system)</span>)

Unless the Coding element has a dataAbsentReason flag, it SHALL contain a _system_ element 
and it should contain a _display_ if it contains a _code_.
<!-!- It can only contain a
_version_ element if it contains a _system_ element.-!->

 -->

If a valueSet is provided, a system URI SHALL also be provided.

The context of use (as defined in the resource or applicable profile) usually makes rules about what codes and systems are allowed or required in a 
particular context by [binding](terminologies.html) the element to a value set.

</div>

Coding is used in the following places: [CodeableConcept](#CodeableConcept), [Composition](composition.html), [Questionnaire](questionnaire.html), [OperationOutcome](operationoutcome.html), [Conformance](conformance.html), [Profile](profile.html), [ImagingStudy](imagingstudy.html), [Provenance](provenance.html), [MessageHeader](messageheader.html), [DataElement](dataelement.html) and [SecurityEvent](securityevent.html)

> **Design Note**: This specification defines two types for representing coded values:
> 
> *   **Coding**: a simple direct reference to a code defined by a code system
> *   **CodeableConcept**: a text description and/or a list of Codings (i.e.g a list of references to codes defned by codes systems)
> 
> The _Coding_ data type corresponds to the simple case of selecting 
> a single code from a code list. However this type is rarely used in the 
> FHIR specifications; long experience with exchanging coded values in
> HL7 shows that in the general case, systems need to able to exchange
> multiple translation codes, and/or an original text. 
> 
> The _Coding_ data type is used directly  when there is certainty that the value 
> must be selected directly from one of the available codes, and the list of 
> possible codes is agreed to by all participants. This is not usually the case
> in the context of FHIR - general interoperabiity - so Coding is mostly used
> in extensions, which are usually intended to be defined for a well-controlled context of use.

<a name="CodeableConcept"/>
<a name="codeableconcept"/>

## <span class="sectioncount">1.13.0.5<a name="1.13.0.5"> </a></span> 
CodeableConcept

See also [Examples](datatypes-examples.html#CodeableConcept), [Formal Definitions](datatypes-definitions.html#CodeableConcept) and [Mappings](datatypes-mappings.html#CodeableConcept).

A CodeableConcept represents a value that is usually supplied by providing a reference to one or more terminologies or ontologies, but may also be defined by the 
provision of text. This is a common pattern in healthcare data.

<pre class="spec">
&lt;[**[name]**](datatypes-definitions.html#CodeableConcept "A concept that may be defined by a formal reference to a terminology or ontology or may be provided by text.") xmlns=&quot;http://hl7.org/fhir&quot;&gt; <span style="float: right">[![doco](help.png)](formats.html "Documentation for this format")</span>
 &lt;!-- from Element: [extension](extensibility.html) --&gt;
 &lt;[**coding**](datatypes-definitions.html#CodeableConcept.coding "A reference to a code defined by a terminology system.")&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..***</span> <span style="color: darkgreen">[Coding](datatypes.html#Coding)</span> <span style="color: navy">Code defined by a terminology system</span><span style="color: Gray"> --&gt;</span>&lt;/coding&gt;
 &lt;[**text**](datatypes-definitions.html#CodeableConcept.text "A human language representation of the concept as seen/selected/uttered by the user who entered the data and/or which represents the intended meaning of the user.") value=&quot;[<span style="color: darkgreen">[string](datatypes.html#string)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..1**</span> <span style="color: navy">Plain text representation of the concept</span><span style="color: Gray"> --&gt;</span>
&lt;/[name]&gt;
</pre>

<table style="border: 0px; font-size: 11px; font-family: verdana; vertical-align: top;" cellpadding="0" border="0" cellspacing="0"><tr style="border: 1px #F0F0F0 solid; font-size: 11px; font-family: verdana; vertical-align: top;"><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Name</th><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Card.</th><th style="width: 100px" class="heirarchy">Type</th><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Description &amp; Constraints</th></tr><tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck1.png)" class="heirarchy">![.](tbl_spacer.png)![.](icon_element.gif) <span title="A concept that may be defined by a formal reference to a terminology or ontology or may be provided by text.">CodeableConcept</span><a name="CodeableConcept"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy"/><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Element</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Concept - reference to a terminology or just  text
<span title="2">Only one coding in a set can be chosen directly by the user</span></td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_datatype.gif) <span title="A reference to a code defined by a terminology system.">coding</span><a name="CodeableConcept.coding"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..*</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[Coding](datatypes.html#Coding)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Code defined by a terminology system</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck00.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin_end.png)![.](icon_primitive.png) <span title="A human language representation of the concept as seen/selected/uttered by the user who entered the data and/or which represents the intended meaning of the user.">text</span><a name="CodeableConcept.text"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[string](datatypes.html#string)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Plain text representation of the concept</td></tr>
</table>Alternate definitions: Resource Profile ([XML](CodeableConcept.profile.xml.html), [JSON](CodeableConcept.profile.json.html))

Each _coding_ is a representation of the concept as described above. The concept may be coded multiple times in different code systems (or even 
multiple times in the same code systems, where multiple forms are possible, such as 
with SNOMED CT). The different codings may have slightly different granularity due to the differences 
in the definitions of the underlying codes. There is no meaning associated with the ordering of _coding_ within a _CodeableConcept_. 
A typical use of _CodeableConcept_ is to send the local code that the concept was coded with, and also one or more translations to publicly defined 
code systems such as LOINC or SNOMED CT. Sending local codes is useful and important for the purposes of debugging and integrity auditing.  

Whether or not _coding_ elements are present, the _text_ 
is the representation of the concept as entered or chosen by the user, and which most closely 
represents the intended meaning of the user or concept. Very often the _text_ 
is the same as a _display_ of one of the codings. One of the codings 
may be flagged as the primary - the code or concept that the user actually selected directly. 
When none of the _coding_ elements is marked as primary, the text (if present)
is the preferred source of meaning. 

<div class="use">

**Constraints**

*   **Inv-2**: Only one coding in a set can be chosen directly by the user (xpath: <span style="font-family: Courier New, monospace">count(f:coding[f:primary/@value='true'])&lt;1</span>)

The context of use usually makes rules about what codes and systems are allowed or required in a 
particular context by [binding](terminologies.html) the element to a value set.

</div>

CodeableConcept is used in the following places: [Condition](condition.html), [Supply](supply.html), [Organization](organization.html), [Group](group.html), [ImmunizationRecommendation](immunizationrecommendation.html), [Appointment](appointment.html), [MedicationDispense](medicationdispense.html), [MedicationPrescription](medicationprescription.html), [Slot](slot.html), [AppointmentResponse](appointmentresponse.html), [MedicationStatement](medicationstatement.html), [Composition](composition.html), [Conformance](conformance.html), [Media](media.html), [Other](other.html), [DocumentReference](documentreference.html), [Immunization](immunization.html), [OrderResponse](orderresponse.html), [Practitioner](practitioner.html), [CarePlan](careplan.html), [Provenance](provenance.html), [Device](device.html), [Order](order.html), [Procedure](procedure.html), [Substance](substance.html), [DiagnosticReport](diagnosticreport.html), [Medication](medication.html), [MessageHeader](messageheader.html), [DocumentManifest](documentmanifest.html), [DataElement](dataelement.html), [Availability](availability.html), [MedicationAdministration](medicationadministration.html), [Encounter](encounter.html), [SecurityEvent](securityevent.html), [List](list.html), [DeviceObservationReport](deviceobservationreport.html), [FamilyHistory](familyhistory.html), [Location](location.html), [Observation](observation.html), [RelatedPerson](relatedperson.html), [Specimen](specimen.html), [Alert](alert.html), [Namespace](namespace.html), [Patient](patient.html), [AdverseReaction](adversereaction.html) and [DiagnosticOrder](diagnosticorder.html)

<a name="Quantity"/>
<a name="quantity"/>

## <span class="sectioncount">1.13.0.6<a name="1.13.0.6"> </a></span> 
Quantity

See also [Examples](datatypes-examples.html#Quantity), [Formal Definitions](datatypes-definitions.html#Quantity) and [Mappings](datatypes-mappings.html#Quantity).

A measured amount (or an amount that can potentially be measured).

<pre class="spec">
&lt;[**[name]**](datatypes-definitions.html#Quantity "A measured amount (or an amount that can potentially be measured). Note that measured amounts include amounts that are not precisely quantified, including amounts involving arbitrary units and floating currencies.") xmlns=&quot;http://hl7.org/fhir&quot;&gt; <span style="float: right">[![doco](help.png)](formats.html "Documentation for this format")</span>
 &lt;!-- from Element: [extension](extensibility.html) --&gt;
 &lt;[**value**](datatypes-definitions.html#Quantity.value "The value of the measured amount. The value includes an implicit precision in the presentation of the value.") value=&quot;[<span style="color: darkgreen">[decimal](datatypes.html#decimal)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..1**</span> <span style="color: navy">Numerical value (with implicit precision)</span><span style="color: Gray"> --&gt;</span>
 &lt;[<span style="text-decoration: underline">**comparator**</span>](datatypes-definitions.html#Quantity.comparator "How the value should be understood and represented - whether the actual value is greater or less than the stated value due to measurement issues. E.g. if the comparator is &quot;&lt;&quot; , then the real value is &lt; stated value (this element modifies the meaning of other elements)") value=&quot;[<span style="color: darkgreen">[code](datatypes.html#code)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..1**</span> <span style="color: navy">[&lt; | &lt;= | &gt;= | &gt; - how to understand the value](quantity-comparator.html)</span><span style="color: Gray"> --&gt;</span>
 &lt;[**units**](datatypes-definitions.html#Quantity.units "A human-readable form of the units.") value=&quot;[<span style="color: darkgreen">[string](datatypes.html#string)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..1**</span> <span style="color: navy">Unit representation</span><span style="color: Gray"> --&gt;</span>
 &lt;[**system**](datatypes-definitions.html#Quantity.system "The identification of the system that provides the coded form of the unit.") value=&quot;[<span style="color: darkgreen">[uri](datatypes.html#uri)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span title="Inv-3: If a code for the units is present, the system SHALL also be present" style="color: brown">**![??](lock.png) 0..1**</span> <span style="color: navy">System that defines coded unit form</span><span style="color: Gray"> --&gt;</span>
 &lt;[**code**](datatypes-definitions.html#Quantity.code "A computer processable form of the units in some unit representation system.") value=&quot;[<span style="color: darkgreen">[code](datatypes.html#code)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..1**</span> <span style="color: navy">Coded form of the unit</span><span style="color: Gray"> --&gt;</span>
&lt;/[name]&gt;
</pre>

<table style="border: 0px; font-size: 11px; font-family: verdana; vertical-align: top;" cellpadding="0" border="0" cellspacing="0"><tr style="border: 1px #F0F0F0 solid; font-size: 11px; font-family: verdana; vertical-align: top;"><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Name</th><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Card.</th><th style="width: 100px" class="heirarchy">Type</th><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Description &amp; Constraints</th></tr><tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck1.png)" class="heirarchy">![.](tbl_spacer.png)![.](icon_element.gif) <span title="A measured amount (or an amount that can potentially be measured). Note that measured amounts include amounts that are not precisely quantified, including amounts involving arbitrary units and floating currencies.">Quantity</span><a name="Quantity"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy"/><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Element</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">A measured or measurable amount
<span title="3">If a code for the units is present, the system SHALL also be present</span></td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_primitive.png) <span title="The value of the measured amount. The value includes an implicit precision in the presentation of the value.">value</span><a name="Quantity.value"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[decimal](datatypes.html#decimal)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Numerical value (with implicit precision)</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_primitive.png) <span title="How the value should be understood and represented - whether the actual value is greater or less than the stated value due to measurement issues. E.g. if the comparator is &quot;&lt;&quot; , then the real value is &lt; stated value.">comparator</span><a name="Quantity.comparator"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[code](datatypes.html#code)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">&lt; | &lt;= | &gt;= | &gt; - how to understand the value
[QuantityCompararator](quantity-comparator.html "How the Quantity should be understood and represented") ([Required](terminologies.html#code "One of the the defined codes must be used"))</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_primitive.png) <span title="A human-readable form of the units.">units</span><a name="Quantity.units"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[string](datatypes.html#string)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Unit representation</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_primitive.png) <span title="The identification of the system that provides the coded form of the unit.">system</span><a name="Quantity.system"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[uri](datatypes.html#uri)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">System that defines coded unit form</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck00.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin_end.png)![.](icon_primitive.png) <span title="A computer processable form of the units in some unit representation system.">code</span><a name="Quantity.code"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[code](datatypes.html#code)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Coded form of the unit</td></tr>
</table>Alternate definitions: Resource Profile ([XML](Quantity.profile.xml.html), [JSON](Quantity.profile.json.html))

### <span class="sectioncount">1.13.0.6.1<a name="1.13.0.6.1"> </a></span> 
Terminology Bindings

<table class="grid">
 <tr><th>Path</th><th>Definition</th><th>Type</th><th>Reference</th></tr>
 <tr><td title="QuantityCompararator" valign="top">Quantity.comparator </td><td valign="top">How the Quantity should be understood and represented</td><td>[Fixed](terminologies.html#code)</td><td valign="top">[http://hl7.org/fhir/quantity-comparator](quantity-comparator.html)</td> </tr>
</table>

The _value_ contains the numerical value of the quantity, including an implicit precision. 
If no comparator is specified, the value is a point value (i.e. '='). The _comparator_ element can never be ignored.

The _units_ element contains a displayable unit that defines what is measured. 
The units may additionally be coded in some formal way using the _code_ and the _system_ 
(see [Coding](#Coding) for further information about how to use the _system_ element). 

If the units are able to be coded in UCUM and a code is provided, it SHOULD be a UCUM code. 
If a UCUM unit is provided in the _code_ then a canonical value can be generated for 
purposes of comparison between quantities. Note that the _units_ element will often 
contain text that is actually a valid UCUM unit, but it cannot be assumed that doesthe units element actually contains a valid UCUM unit. 

<div class="use">

**Constraints**

*   **Inv-3**: If a code for the units is present, the system SHALL also be present (xpath: <span style="font-family: Courier New, monospace">not(exists(f:code)) or exists(f:system)</span>)

The context of use may frequently define what kind of quantity
this is and therefore what kind of units can be used. The context 
of use may additionally require a _code_ from a particular _system_.
The context of use may also restrict the values for the _value_ or _range_.

</div>

Coding is used in the following places: [Range](#Range), [Ratio](#Ratio), [SampledData](#SampledData), [Supply](supply.html), [Group](group.html), [MedicationDispense](medicationdispense.html), [MedicationPrescription](medicationprescription.html), [MedicationStatement](medicationstatement.html), [Immunization](immunization.html), [CarePlan](careplan.html), [Substance](substance.html), [Medication](medication.html), [MedicationAdministration](medicationadministration.html), [Observation](observation.html) and [Specimen](specimen.html)

### <span class="sectioncount">1.13.0.6.2<a name="1.13.0.6.2"> </a></span> 
Defined Variations on Quantity

These are used as types in resource content models, but they are really just a Quantity with some rules:

<a name="Age"> </a><a name="age"> </a>
<a name="Count"> </a><a name="count"> </a>
<a name="Money"> </a><a name="money"> </a>
<a name="Distance"> </a><a name="distance"> </a>
<a name="Duration"> </a><a name="duration"> </a>
<table class="list">
 <tr><td>Age</td><td>A duration (length of time) with a UCUM code</td><td>Profile ([XML](Age.profile.xml.html), [JSON](Age.profile.json.html))</td></tr>
 <tr><td>Count</td><td>A count of a discrete element (no unit)</td><td>Profile ([XML](Count.profile.xml.html), [JSON](Count.profile.json.html))</td></tr>
 <tr><td>Money</td><td>An amount of money. With regard to precision, see [[X]]</td><td>Profile ([XML](Money.profile.xml.html), [JSON](Money.profile.json.html))</td></tr>
 <tr><td>Distance</td><td>A measure of distance</td><td>Profile ([XML](Distance.profile.xml.html), [JSON](Distance.profile.json.html))</td></tr>
 <tr><td>Duration</td><td>A length of time</td><td>Profile ([XML](Duration.profile.xml.html), [JSON](Duration.profile.json.html))</td></tr>
</table>

<a name="Range"/>
<a name="range"/>

## <span class="sectioncount">1.13.0.7<a name="1.13.0.7"> </a></span> 
Range

See also [Examples](datatypes-examples.html#Range), [Formal Definitions](datatypes-definitions.html#Range) and [Mappings](datatypes-mappings.html#Range).

A set of ordered Quantity values defined by a low and high limit.

A Range specifies a set of possible values; usually, one value from the range applies (e.g. &quot;give the patient between 2 and 4 tablets&quot;).
Ranges are typically used in instructions.

<pre class="spec">
&lt;[**[name]**](datatypes-definitions.html#Range "A set of ordered Quantities defined by a low and high limit.") xmlns=&quot;http://hl7.org/fhir&quot;&gt; <span style="float: right">[![doco](help.png)](formats.html "Documentation for this format")</span>
 &lt;!-- from Element: [extension](extensibility.html) --&gt;
 &lt;[**low**](datatypes-definitions.html#Range.low "The low limit. The boundary is inclusive.")&gt;<span style="color: Gray">&lt;!--</span> <span title="Inv-2: If present, low SHALL have a lower value than high; Inv-3: Quantity values cannot have a comparator when used in a Range" style="color: brown">**![??](lock.png) 0..1**</span> <span style="color: darkgreen">[Quantity](datatypes.html#Quantity)</span> <span style="color: navy">Low limit</span><span style="color: Gray"> --&gt;</span>&lt;/low&gt;
 &lt;[**high**](datatypes-definitions.html#Range.high "The high limit. The boundary is inclusive.")&gt;<span style="color: Gray">&lt;!--</span> <span title="Inv-2: If present, low SHALL have a lower value than high; Inv-3: Quantity values cannot have a comparator when used in a Range" style="color: brown">**![??](lock.png) 0..1**</span> <span style="color: darkgreen">[Quantity](datatypes.html#Quantity)</span> <span style="color: navy">High limit</span><span style="color: Gray"> --&gt;</span>&lt;/high&gt;
&lt;/[name]&gt;
</pre>

<table style="border: 0px; font-size: 11px; font-family: verdana; vertical-align: top;" cellpadding="0" border="0" cellspacing="0"><tr style="border: 1px #F0F0F0 solid; font-size: 11px; font-family: verdana; vertical-align: top;"><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Name</th><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Card.</th><th style="width: 100px" class="heirarchy">Type</th><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Description &amp; Constraints</th></tr><tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck1.png)" class="heirarchy">![.](tbl_spacer.png)![.](icon_element.gif) <span title="A set of ordered Quantities defined by a low and high limit.">Range</span><a name="Range"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy"/><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Element</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Set of values bounded by low and high
<span title="3">Quantity values cannot have a comparator when used in a Range</span><span title="2">If present, low SHALL have a lower value than high</span></td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_datatype.gif) <span title="The low limit. The boundary is inclusive.">low</span><a name="Range.low"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[Quantity](datatypes.html#Quantity)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Low limit</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck00.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin_end.png)![.](icon_datatype.gif) <span title="The high limit. The boundary is inclusive.">high</span><a name="Range.high"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[Quantity](datatypes.html#Quantity)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">High limit</td></tr>
</table>Alternate definitions: Resource Profile ([XML](Range.profile.xml.html), [JSON](Range.profile.json.html))

The _units_ and _code_/_system_ elements of the _low_ or _high_ elements SHALL match. 
If the _low_ or _high_ elements are missing, the meaning
is that the low or high boundaries are not known and therefore neither is the complete range.

The _range_ flag on the _low_ or _high_ elements cannot be present. Note that the Range type should not be 
used to represent out of range measurements: A quantity type with the comparator element should be used instead.

The low and the high values are inclusive, and are assumed to have arbitrarily high precision. E.g. the range 1.5 to 2.5 
includes 1.50, and 2.50 but not 1.49 or 2.51.

<div class="use">

**Constraints**

*   **Inv-2**: If present, low SHALL have a lower value than high (xpath: <span style="font-family: Courier New, monospace">not(exists(f:low/f:value/@value)) or not(exists(f:high/f:value/@value)) or (number(f:low/f:value/@value) &lt;= number(f:high/f:value/@value))</span>)
*   **Inv-3**: Quantity values cannot have a comparator when used in a Range (xpath: <span style="font-family: Courier New, monospace">not(exists(f:low/f:comparator) or exists(f:high/f:comparator))</span>)
</div>

Range is used in the following places: [Group](group.html), [FamilyHistory](familyhistory.html) and [Observation](observation.html)

<a name="Ratio"/>
<a name="ratio"/>

## <span class="sectioncount">1.13.0.8<a name="1.13.0.8"> </a></span> 
Ratio

See also [Examples](datatypes-examples.html#Ratio), [Formal Definitions](datatypes-definitions.html#Ratio) and [Mappings](datatypes-mappings.html#Ratio).

A relationship between two Quantity values expressed as a numerator and a denominator.

<pre class="spec">
&lt;[**[name]**](datatypes-definitions.html#Ratio "A relationship of two Quantity values - expressed as a numerator and a denominator.") xmlns=&quot;http://hl7.org/fhir&quot;&gt; <span style="float: right">[![doco](help.png)](formats.html "Documentation for this format")</span>
 &lt;!-- from Element: [extension](extensibility.html) --&gt;
 &lt;[**numerator**](datatypes-definitions.html#Ratio.numerator "The value of the numerator.")&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..1**</span> <span style="color: darkgreen">[Quantity](datatypes.html#Quantity)</span> <span style="color: navy">Numerator value</span><span style="color: Gray"> --&gt;</span>&lt;/numerator&gt;
 &lt;[**denominator**](datatypes-definitions.html#Ratio.denominator "The value of the denominator.")&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..1**</span> <span style="color: darkgreen">[Quantity](datatypes.html#Quantity)</span> <span style="color: navy">Denominator value</span><span style="color: Gray"> --&gt;</span>&lt;/denominator&gt;
&lt;/[name]&gt;
</pre>

<table style="border: 0px; font-size: 11px; font-family: verdana; vertical-align: top;" cellpadding="0" border="0" cellspacing="0"><tr style="border: 1px #F0F0F0 solid; font-size: 11px; font-family: verdana; vertical-align: top;"><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Name</th><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Card.</th><th style="width: 100px" class="heirarchy">Type</th><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Description &amp; Constraints</th></tr><tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck1.png)" class="heirarchy">![.](tbl_spacer.png)![.](icon_element.gif) <span title="A relationship of two Quantity values - expressed as a numerator and a denominator.">Ratio</span><a name="Ratio"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy"/><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Element</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">A ratio of two Quantity values - a numerator and a denominator
<span title="1">numerator and denominator SHALL both be present, or both be absent</span></td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_datatype.gif) <span title="The value of the numerator.">numerator</span><a name="Ratio.numerator"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[Quantity](datatypes.html#Quantity)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Numerator value</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck00.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin_end.png)![.](icon_datatype.gif) <span title="The value of the denominator.">denominator</span><a name="Ratio.denominator"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[Quantity](datatypes.html#Quantity)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Denominator value</td></tr>
</table>Alternate definitions: Resource Profile ([XML](Ratio.profile.xml.html), [JSON](Ratio.profile.json.html))

Common factors in the numerator and denominator are not automatically cancelled out. The Ratio 
data type is used for titers (e.g., &quot;1:128&quot;) and other quantities produced by laboratories that 
truly represent ratios. Ratios are not simply &quot;structured numerics&quot; - for example blood pressure measurements 
(e.g. &quot;120/60&quot;) are not ratios. In addition, ratios are used where common factors in the numerator 
and denominator do not cancel out. The most common example of this is where the ratio represents a 
unit cost, and the numerator is a currency (e.g. 50/$10).

A proper ratio has both a numerator and a denominator; however these are not mandatory in order
to allow an invalid ratio with an extension with further information. 

<div class="use">

**Constraints**

*   **Inv-1**: numerator and denominator SHALL both be present, or both be absent (xpath: <span style="font-family: Courier New, monospace">count(f:numerator) = count(f:denominator)</span>)

The context of use may require particular types of Quantity for the numerator or denominator.

</div>

Ratio is used in the following places: [MedicationDispense](medicationdispense.html), [MedicationPrescription](medicationprescription.html), [MedicationStatement](medicationstatement.html), [Substance](substance.html), [Medication](medication.html), [MedicationAdministration](medicationadministration.html) and [Observation](observation.html)

<a name="Period"/>
<a name="period"/>

## <span class="sectioncount">1.13.0.9<a name="1.13.0.9"> </a></span> 
Period

See also [Examples](datatypes-examples.html#Period), [Formal Definitions](datatypes-definitions.html#Period) and [Mappings](datatypes-mappings.html#Period).

A time period defined by a start and end date/time.

A period specifies a range of times. The context
of use will specify whether the entire range applies (e.g. &quot;the patient
was an inpatient of the hospital for this time range&quot;) or one value 
from the period applies (e.g. &quot;give to the patient between 2 and 4 pm&quot;).

<pre class="spec">
&lt;[**[name]**](datatypes-definitions.html#Period "A time period defined by a start and end date and optionally time.") xmlns=&quot;http://hl7.org/fhir&quot;&gt; <span style="float: right">[![doco](help.png)](formats.html "Documentation for this format")</span>
 &lt;!-- from Element: [extension](extensibility.html) --&gt;
 &lt;[**start**](datatypes-definitions.html#Period.start "The start of the period. The boundary is inclusive.") value=&quot;[<span style="color: darkgreen">[dateTime](datatypes.html#dateTime)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span title="Inv-1: If present, start SHALL have a lower value than end" style="color: brown">**![??](lock.png) 0..1**</span> <span style="color: navy">Starting time with inclusive boundary</span><span style="color: Gray"> --&gt;</span>
 &lt;[**end**](datatypes-definitions.html#Period.end "The end of the period. If the end of the period is missing, it means that the period is ongoing.") value=&quot;[<span style="color: darkgreen">[dateTime](datatypes.html#dateTime)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span title="Inv-1: If present, start SHALL have a lower value than end" style="color: brown">**![??](lock.png) 0..1**</span> <span style="color: navy">End time with inclusive boundary, if not ongoing</span><span style="color: Gray"> --&gt;</span>
&lt;/[name]&gt;
</pre>

<table style="border: 0px; font-size: 11px; font-family: verdana; vertical-align: top;" cellpadding="0" border="0" cellspacing="0"><tr style="border: 1px #F0F0F0 solid; font-size: 11px; font-family: verdana; vertical-align: top;"><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Name</th><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Card.</th><th style="width: 100px" class="heirarchy">Type</th><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Description &amp; Constraints</th></tr><tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck1.png)" class="heirarchy">![.](tbl_spacer.png)![.](icon_element.gif) <span title="A time period defined by a start and end date and optionally time.">Period</span><a name="Period"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy"/><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Element</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Time range defined by start and end date/time
<span title="1">If present, start SHALL have a lower value than end</span></td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_primitive.png) <span title="The start of the period. The boundary is inclusive.">start</span><a name="Period.start"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[dateTime](datatypes.html#dateTime)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Starting time with inclusive boundary</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck00.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin_end.png)![.](icon_primitive.png) <span title="The end of the period. If the end of the period is missing, it means that the period is ongoing.">end</span><a name="Period.end"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[dateTime](datatypes.html#dateTime)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">End time with inclusive boundary, if not ongoing</td></tr>
</table>Alternate definitions: Resource Profile ([XML](Period.profile.xml.html), [JSON](Period.profile.json.html))

If the _start_ element is  missing, the start of the period is not
known. If the _end_ element is missing, it means that the period is ongoing.

The end value includes any matching date/time. For example, the period 
2011-05-23 to 2011-05-27 includes all the times of 23rd May through to 
the end of the 27th May.

  <!-- <div class="use">

**Constraints**

*   **Inv-1**: If present, start SHALL have a lower value than end (xpath: <span style="font-family: Courier New, monospace">not(exists(f:start)) or not(exists(f:end)) or (f:start/@value &lt;= f:end/@value)</span>)
</div> -->

Period is used in the following places: [Identifier](#Identifier), [Supply](supply.html), [MedicationDispense](medicationdispense.html), [MedicationPrescription](medicationprescription.html), [MedicationStatement](medicationstatement.html), [Composition](composition.html), [DocumentReference](documentreference.html), [Practitioner](practitioner.html), [CarePlan](careplan.html), [Provenance](provenance.html), [Procedure](procedure.html), [DiagnosticReport](diagnosticreport.html), [Availability](availability.html), [MedicationAdministration](medicationadministration.html), [Encounter](encounter.html), [FamilyHistory](familyhistory.html), [Observation](observation.html), [Specimen](specimen.html) and [Namespace](namespace.html)

<a name="SampledData"/>
<a name="sampleddata"/>

## <span class="sectioncount">1.13.0.10<a name="1.13.0.10"> </a></span> 
SampledData

See also [Examples](datatypes-examples.html#SampledData), [Formal Definitions](datatypes-definitions.html#SampledData) and [Mappings](datatypes-mappings.html#SampledData).

Data that comes from a series of measurements taken by a device, with upper and lower limits. There may be more than one dimension in the data.

A SampledData provides a concise way to handle the data produced by devices that sample a physical particular state at a high frequency. A typical 
use for this is for the output of an ECG or EKG device.

<pre class="spec">
&lt;[**[name]**](datatypes-definitions.html#SampledData "A series of measurements taken by a device, with upper and lower limits. There may be more than one dimension in the data.") xmlns=&quot;http://hl7.org/fhir&quot;&gt; <span style="float: right">[![doco](help.png)](formats.html "Documentation for this format")</span>
 &lt;!-- from Element: [extension](extensibility.html) --&gt;
 &lt;[**origin**](datatypes-definitions.html#SampledData.origin "The base quantity that a measured value of zero represents. In addition, this provides the units of the entire measurement series.")&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**1..1**</span> <span style="color: darkgreen">[Quantity](datatypes.html#Quantity)</span> <span style="color: navy">Zero value and units</span><span style="color: Gray"> --&gt;</span>&lt;/origin&gt;
 &lt;[**period**](datatypes-definitions.html#SampledData.period "The length of time between sampling times, measured in milliseconds.") value=&quot;[<span style="color: darkgreen">[decimal](datatypes.html#decimal)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**1..1**</span> <span style="color: navy">Number of milliseconds between samples</span><span style="color: Gray"> --&gt;</span>
 &lt;[**factor**](datatypes-definitions.html#SampledData.factor "A correction factor that is applied to the sampled data points before they are added to the origin.") value=&quot;[<span style="color: darkgreen">[decimal](datatypes.html#decimal)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..1**</span> <span style="color: navy">Multiply data by this before adding to origin</span><span style="color: Gray"> --&gt;</span>
 &lt;[**lowerLimit**](datatypes-definitions.html#SampledData.lowerLimit "The lower limit of detection of the measured points. This is needed if any of the data points have the value &quot;L&quot; (lower than detection limit).") value=&quot;[<span style="color: darkgreen">[decimal](datatypes.html#decimal)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..1**</span> <span style="color: navy">Lower limit of detection</span><span style="color: Gray"> --&gt;</span>
 &lt;[**upperLimit**](datatypes-definitions.html#SampledData.upperLimit "The upper limit of detection of the measured points. This is needed if any of the data points have the value &quot;U&quot; (higher than detection limit).") value=&quot;[<span style="color: darkgreen">[decimal](datatypes.html#decimal)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..1**</span> <span style="color: navy">Upper limit of detection</span><span style="color: Gray"> --&gt;</span>
 &lt;[**dimensions**](datatypes-definitions.html#SampledData.dimensions "The number of sample points at each time point. If this value is greater than one, then the dimensions will be interlaced - all the sample points for a point in time will be recorded at once.") value=&quot;[<span style="color: darkgreen">[integer](datatypes.html#integer)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**1..1**</span> <span style="color: navy">Number of sample points at each time point</span><span style="color: Gray"> --&gt;</span>
 &lt;[**data**](datatypes-definitions.html#SampledData.data "A series of data points which are decimal values separated by a single space (character u20). The special values &quot;E&quot; (error), &quot;L&quot; (below detection limit) and &quot;U&quot; (above detection limit) can also be used in place of a decimal value.") value=&quot;[<span style="color: darkgreen">[string](datatypes.html#string)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**1..1**</span> <span style="color: navy">Decimal values with spaces, or &quot;E&quot; | &quot;U&quot; | &quot;L&quot;</span><span style="color: Gray"> --&gt;</span>
&lt;/[name]&gt;
</pre>

<table style="border: 0px; font-size: 11px; font-family: verdana; vertical-align: top;" cellpadding="0" border="0" cellspacing="0"><tr style="border: 1px #F0F0F0 solid; font-size: 11px; font-family: verdana; vertical-align: top;"><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Name</th><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Card.</th><th style="width: 100px" class="heirarchy">Type</th><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Description &amp; Constraints</th></tr><tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck1.png)" class="heirarchy">![.](tbl_spacer.png)![.](icon_element.gif) <span title="A series of measurements taken by a device, with upper and lower limits. There may be more than one dimension in the data.">SampledData</span><a name="SampledData"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy"/><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Element</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">A series of measurements taken by a device</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_datatype.gif) <span title="The base quantity that a measured value of zero represents. In addition, this provides the units of the entire measurement series.">origin</span><a name="SampledData.origin"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">1..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[Quantity](datatypes.html#Quantity)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Zero value and units</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_primitive.png) <span title="The length of time between sampling times, measured in milliseconds.">period</span><a name="SampledData.period"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">1..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[decimal](datatypes.html#decimal)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Number of milliseconds between samples</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_primitive.png) <span title="A correction factor that is applied to the sampled data points before they are added to the origin.">factor</span><a name="SampledData.factor"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[decimal](datatypes.html#decimal)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Multiply data by this before adding to origin</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_primitive.png) <span title="The lower limit of detection of the measured points. This is needed if any of the data points have the value &quot;L&quot; (lower than detection limit).">lowerLimit</span><a name="SampledData.lowerLimit"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[decimal](datatypes.html#decimal)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Lower limit of detection</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_primitive.png) <span title="The upper limit of detection of the measured points. This is needed if any of the data points have the value &quot;U&quot; (higher than detection limit).">upperLimit</span><a name="SampledData.upperLimit"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[decimal](datatypes.html#decimal)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Upper limit of detection</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_primitive.png) <span title="The number of sample points at each time point. If this value is greater than one, then the dimensions will be interlaced - all the sample points for a point in time will be recorded at once.">dimensions</span><a name="SampledData.dimensions"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">1..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[integer](datatypes.html#integer)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Number of sample points at each time point</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck00.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin_end.png)![.](icon_primitive.png) <span title="A series of data points which are decimal values separated by a single space (character u20). The special values &quot;E&quot; (error), &quot;L&quot; (below detection limit) and &quot;U&quot; (above detection limit) can also be used in place of a decimal value.">data</span><a name="SampledData.data"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">1..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[string](datatypes.html#string)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Decimal values with spaces, or &quot;E&quot; | &quot;U&quot; | &quot;L&quot;</td></tr>
</table>Alternate definitions: Resource Profile ([XML](SampledData.profile.xml.html), [JSON](SampledData.profile.json.html))

The digits are a set of decimal values separated by a single space (Unicode character u20).
In addition to decimal values, the special values &quot;E&quot; (error), &quot;L&quot; (below detection limit) 
and &quot;U&quot; (above detection limit) can also be used. If there is more than one dimension, the
different dimensions are interlaced - all the data points for a particular time are
represented together. 
The default value for _factor_ is 1. 

SampledData is used in the following places: [Observation](observation.html)

<a name="Identifier"/>
<a name="identifier"/>

## <span class="sectioncount">1.13.0.11<a name="1.13.0.11"> </a></span> 
Identifier

See also [Examples](datatypes-examples.html#Identifier), [Formal Definitions](datatypes-definitions.html#Identifier) and [Mappings](datatypes-mappings.html#Identifier).

A numeric or alphanumeric string that is associated with a single object or entity within a given system. 
Typically, identifiers are used to connect content in resources to external content available in other frameworks or protocols.
Typically, identifiers are used to connect content in resources to external content available in other frameworks or protocols.
Identifiers are associated with objects, and may be changed or retired due to human or system process and
errors. 

<pre class="spec">
&lt;[**[name]**](datatypes-definitions.html#Identifier "A technical identifier - identifies some entity uniquely and unambiguously.") xmlns=&quot;http://hl7.org/fhir&quot;&gt; <span style="float: right">[![doco](help.png)](formats.html "Documentation for this format")</span>
 &lt;!-- from Element: [extension](extensibility.html) --&gt;
 &lt;[<span style="text-decoration: underline">**use**</span>](datatypes-definitions.html#Identifier.use "The purpose of this identifier (this element modifies the meaning of other elements)") value=&quot;[<span style="color: darkgreen">[code](datatypes.html#code)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..1**</span> <span style="color: navy">[usual | official | temp | secondary (If known)](identifier-use.html)</span><span style="color: Gray"> --&gt;</span>
 &lt;[**label**](datatypes-definitions.html#Identifier.label "A text string for the identifier that can be displayed to a human so they can recognize the identifier.") value=&quot;[<span style="color: darkgreen">[string](datatypes.html#string)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..1**</span> <span style="color: navy">Description of identifier</span><span style="color: Gray"> --&gt;</span>
 &lt;[**system**](datatypes-definitions.html#Identifier.system "Establishes the namespace in which set of possible id values is unique.") value=&quot;[<span style="color: darkgreen">[uri](datatypes.html#uri)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..1**</span> <span style="color: navy">The namespace for the identifier</span><span style="color: Gray"> --&gt;</span>
 &lt;[**value**](datatypes-definitions.html#Identifier.value "The portion of the identifier typically displayed to the user and which is unique within the context of the system.") value=&quot;[<span style="color: darkgreen">[string](datatypes.html#string)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..1**</span> <span style="color: navy">The value that is unique</span><span style="color: Gray"> --&gt;</span>
 &lt;[**period**](datatypes-definitions.html#Identifier.period "Time period during which identifier is/was valid for use.")&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..1**</span> <span style="color: darkgreen">[Period](datatypes.html#Period)</span> <span style="color: navy">Time period when id is/was valid for use</span><span style="color: Gray"> --&gt;</span>&lt;/period&gt;
 &lt;[**assigner**](datatypes-definitions.html#Identifier.assigner "Organization that issued/manages the identifier.")&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..1**</span> <span style="color: darkgreen">[Resource](references.html#Resource)([Organization](organization.html#Organization))</span> <span style="color: navy">Organization that issued id (may be just text)</span><span style="color: Gray"> --&gt;</span>&lt;/assigner&gt;
&lt;/[name]&gt;
</pre>

<table style="border: 0px; font-size: 11px; font-family: verdana; vertical-align: top;" cellpadding="0" border="0" cellspacing="0"><tr style="border: 1px #F0F0F0 solid; font-size: 11px; font-family: verdana; vertical-align: top;"><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Name</th><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Card.</th><th style="width: 100px" class="heirarchy">Type</th><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Description &amp; Constraints</th></tr><tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck1.png)" class="heirarchy">![.](tbl_spacer.png)![.](icon_element.gif) <span title="A technical identifier - identifies some entity uniquely and unambiguously.">Identifier</span><a name="Identifier"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy"/><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Element</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">An identifier intended for computation</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_primitive.png) <span title="The purpose of this identifier.">use</span><a name="Identifier.use"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[code](datatypes.html#code)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">usual | official | temp | secondary (If known)
[IdentifierUse](identifier-use.html "Identifies the purpose for this identifier, if known") ([Required](terminologies.html#code "One of the the defined codes must be used"))</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_primitive.png) <span title="A text string for the identifier that can be displayed to a human so they can recognize the identifier.">label</span><a name="Identifier.label"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[string](datatypes.html#string)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Description of identifier</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_primitive.png) <span title="Establishes the namespace in which set of possible id values is unique.">system</span><a name="Identifier.system"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[uri](datatypes.html#uri)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">The namespace for the identifier</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_primitive.png) <span title="The portion of the identifier typically displayed to the user and which is unique within the context of the system.">value</span><a name="Identifier.value"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[string](datatypes.html#string)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">The value that is unique</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_datatype.gif) <span title="Time period during which identifier is/was valid for use.">period</span><a name="Identifier.period"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[Period](datatypes.html#Period)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Time period when id is/was valid for use</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck00.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin_end.png)![.](icon_reference.png) <span title="Organization that issued/manages the identifier.">assigner</span><a name="Identifier.assigner"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[Organization](organization.html)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Organization that issued id (may be just text)</td></tr>
</table>Alternate definitions: Resource Profile ([XML](Identifier.profile.xml.html), [JSON](Identifier.profile.json.html))

### <span class="sectioncount">1.13.0.11.1<a name="1.13.0.11.1"> </a></span> 
Terminology Bindings

<table class="grid">
 <tr><th>Path</th><th>Definition</th><th>Type</th><th>Reference</th></tr>
 <tr><td title="IdentifierUse" valign="top">Identifier.use </td><td valign="top">Identifies the purpose for this identifier, if known</td><td>[Fixed](terminologies.html#code)</td><td valign="top">[http://hl7.org/fhir/identifier-use](identifier-use.html)</td> </tr>
</table>

The _system_ referred to by means of a URI defines how the identifier is defined (i.e. how the value is made unique). 
It might be a specific application or a recognized standard/specification for a set or identifiers
or a way of making identifiers unique. The _value_ SHALL be unique within the defined _system_
and have a consistent meaning wherever it appears. Both _system_ and _value_ are always case sensitive.

FHIR defines [some useful URIs directly](terminologies-systems.html). OIDs (urn:oid:) and UUIDs (urn:uuid:) 
may be registered in the [HL7 OID registry](http://hl7.org/oid) and should be if the 
content is shared or exchanged across institutional boundaries. If the identifier itself 
is naturally globally unique (e.g. an OID, a UUID, or a URI with no trailing local part), 
then the _system_ SHALL be &quot;urn:ietf:rfc:3986&quot;, and the URI is in the _value_.

In some cases, the system may not be known - only the value is known (e.g. a simple device that scans a barcode), 
or the system is known implicitly (simple exchange in a limited context, often driven by barcode readers). 
In this case, no useful matching may be performed using the value unless the system can be safely inferred by the 
context. This practice should be avoided where possible, as 
information sharing in a wider context is very likely to arise eventually, and values without a system are inherently limited in use.

The _assigner_ is used to indicate what registry/state/facility/etc. assigned the identifier. 

Identifier is used in the following places: [Condition](condition.html), [Supply](supply.html), [Organization](organization.html), [Group](group.html), [ValueSet](valueset.html), [ImmunizationRecommendation](immunizationrecommendation.html), [Appointment](appointment.html), [MedicationDispense](medicationdispense.html), [MedicationPrescription](medicationprescription.html), [Slot](slot.html), [AppointmentResponse](appointmentresponse.html), [MedicationStatement](medicationstatement.html), [Composition](composition.html), [Questionnaire](questionnaire.html), [Media](media.html), [Other](other.html), [Profile](profile.html), [DocumentReference](documentreference.html), [Immunization](immunization.html), [OrderResponse](orderresponse.html), [ImagingStudy](imagingstudy.html), [Practitioner](practitioner.html), [CarePlan](careplan.html), [Device](device.html), [Order](order.html), [Procedure](procedure.html), [Substance](substance.html), [DiagnosticReport](diagnosticreport.html), [DocumentManifest](documentmanifest.html), [DataElement](dataelement.html), [Availability](availability.html), [MedicationAdministration](medicationadministration.html), [Encounter](encounter.html), [SecurityEvent](securityevent.html), [List](list.html), [DeviceObservationReport](deviceobservationreport.html), [FamilyHistory](familyhistory.html), [Location](location.html), [AllergyIntolerance](allergyintolerance.html), [Observation](observation.html), [RelatedPerson](relatedperson.html), [Specimen](specimen.html), [Alert](alert.html), [Patient](patient.html), [AdverseReaction](adversereaction.html) and [DiagnosticOrder](diagnosticorder.html)

<a name="HumanName"/>
<a name="humanname"/>

## <span class="sectioncount">1.13.0.12<a name="1.13.0.12"> </a></span> 
HumanName

See also [Examples](datatypes-examples.html#HumanName), [Formal Definitions](datatypes-definitions.html#HumanName) and [Mappings](datatypes-mappings.html#HumanName).

A name of a human with text, parts and usage information.

Names may be changed or repudiated.  People may have different names in different 
contexts. Names may be divided into parts of different type that have variable 
significance depending on context, though the division into parts is not always 
significant. With personal names, the different parts may or may not be imbued with
some implicit meaning; various cultures associate different importance with the 
name parts and the degree to which systems SHALL care about name parts around the 
world varies widely.

<pre class="spec">
&lt;[**[name]**](datatypes-definitions.html#HumanName "A human") xmlns=&quot;http://hl7.org/fhir&quot;&gt; <span style="float: right">[![doco](help.png)](formats.html "Documentation for this format")</span>
 &lt;!-- from Element: [extension](extensibility.html) --&gt;
 &lt;[<span style="text-decoration: underline">**use**</span>](datatypes-definitions.html#HumanName.use "Identifies the purpose for this name (this element modifies the meaning of other elements)") value=&quot;[<span style="color: darkgreen">[code](datatypes.html#code)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..1**</span> <span style="color: navy">[usual | official | temp | nickname | anonymous | old | maiden](name-use.html)</span><span style="color: Gray"> --&gt;</span>
 &lt;[**text**](datatypes-definitions.html#HumanName.text "A full text representation of the name.") value=&quot;[<span style="color: darkgreen">[string](datatypes.html#string)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..1**</span> <span style="color: navy">Text representation of the full name</span><span style="color: Gray"> --&gt;</span>
 &lt;[**family**](datatypes-definitions.html#HumanName.family "The part of a name that links to the genealogy. In some cultures (e.g. Eritrea) the family name of a son is the first name of his father.") value=&quot;[<span style="color: darkgreen">[string](datatypes.html#string)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..***</span> <span style="color: navy">Family name (often called 'Surname')</span><span style="color: Gray"> --&gt;</span>
 &lt;[**given**](datatypes-definitions.html#HumanName.given "Given name.") value=&quot;[<span style="color: darkgreen">[string](datatypes.html#string)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..***</span> <span style="color: navy">Given names (not always 'first'). Includes middle names</span><span style="color: Gray"> --&gt;</span>
 &lt;[**prefix**](datatypes-definitions.html#HumanName.prefix "Part of the name that is acquired as a title due to academic, legal, employment or nobility status, etc. and that appears at the start of the name.") value=&quot;[<span style="color: darkgreen">[string](datatypes.html#string)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..***</span> <span style="color: navy">Parts that come before the name</span><span style="color: Gray"> --&gt;</span>
 &lt;[**suffix**](datatypes-definitions.html#HumanName.suffix "Part of the name that is acquired as a title due to academic, legal, employment or nobility status, etc. and that appears at the end of the name.") value=&quot;[<span style="color: darkgreen">[string](datatypes.html#string)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..***</span> <span style="color: navy">Parts that come after the name</span><span style="color: Gray"> --&gt;</span>
 &lt;[**period**](datatypes-definitions.html#HumanName.period "Indicates the period of time when this name was valid for the named person.")&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..1**</span> <span style="color: darkgreen">[Period](datatypes.html#Period)</span> <span style="color: navy">Time period when name was/is in use</span><span style="color: Gray"> --&gt;</span>&lt;/period&gt;
&lt;/[name]&gt;
</pre>

<table style="border: 0px; font-size: 11px; font-family: verdana; vertical-align: top;" cellpadding="0" border="0" cellspacing="0"><tr style="border: 1px #F0F0F0 solid; font-size: 11px; font-family: verdana; vertical-align: top;"><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Name</th><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Card.</th><th style="width: 100px" class="heirarchy">Type</th><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Description &amp; Constraints</th></tr><tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck1.png)" class="heirarchy">![.](tbl_spacer.png)![.](icon_element.gif) <span title="A human's name with the ability to identify parts and usage.">HumanName</span><a name="HumanName"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy"/><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Element</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Name of a human - parts and usage</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_primitive.png) <span title="Identifies the purpose for this name.">use</span><a name="HumanName.use"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[code](datatypes.html#code)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">usual | official | temp | nickname | anonymous | old | maiden
[NameUse](name-use.html "The use of a human name") ([Required](terminologies.html#code "One of the the defined codes must be used"))</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_primitive.png) <span title="A full text representation of the name.">text</span><a name="HumanName.text"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[string](datatypes.html#string)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Text representation of the full name</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_primitive.png) <span title="The part of a name that links to the genealogy. In some cultures (e.g. Eritrea) the family name of a son is the first name of his father.">family</span><a name="HumanName.family"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..*</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[string](datatypes.html#string)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Family name (often called 'Surname')</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_primitive.png) <span title="Given name.">given</span><a name="HumanName.given"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..*</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[string](datatypes.html#string)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Given names (not always 'first'). Includes middle names</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_primitive.png) <span title="Part of the name that is acquired as a title due to academic, legal, employment or nobility status, etc. and that appears at the start of the name.">prefix</span><a name="HumanName.prefix"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..*</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[string](datatypes.html#string)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Parts that come before the name</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_primitive.png) <span title="Part of the name that is acquired as a title due to academic, legal, employment or nobility status, etc. and that appears at the end of the name.">suffix</span><a name="HumanName.suffix"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..*</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[string](datatypes.html#string)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Parts that come after the name</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck00.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin_end.png)![.](icon_datatype.gif) <span title="Indicates the period of time when this name was valid for the named person.">period</span><a name="HumanName.period"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[Period](datatypes.html#Period)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Time period when name was/is in use</td></tr>
</table>Alternate definitions: Resource Profile ([XML](HumanName.profile.xml.html), [JSON](HumanName.profile.json.html))

### <span class="sectioncount">1.13.0.12.1<a name="1.13.0.12.1"> </a></span> 
Terminology Bindings

<table class="grid">
 <tr><th>Path</th><th>Definition</th><th>Type</th><th>Reference</th></tr>
 <tr><td title="NameUse" valign="top">HumanName.use </td><td valign="top">The use of a human name</td><td>[Fixed](terminologies.html#code)</td><td valign="top">[http://hl7.org/fhir/name-use](name-use.html)</td> </tr>
</table>

The parts of a name SHOULD NOT contain whitespace. For family name, hyphenated 
names such as &quot;Smith-Jones&quot; are a single name, but names with spaces such as 
&quot;Smith Jones&quot; are broken into multiple parts. For given names, initials may 
be used in place of the full name if that is all that is recorded. 

The _text_ element specifies the entire name as it should be represented. This
may be provided instead of or as well as specific parts. Applications updating a name
SHALL ensure either that the text and the parts are in agreement, or that only one
of the two is present. Systems that do not support as many name parts as are 
provided in an instance may wish to append some of the parts together 
using spaces

Note that the order of the  parts within a given part type has 
significance and SHALL be observed. The appropriate order between 
family name and given names depends on culture and context of use.  

HumanName is used in the following places: [Organization](organization.html), [Practitioner](practitioner.html), [RelatedPerson](relatedperson.html), [Namespace](namespace.html) and [Patient](patient.html)

  <!-- <div class="use">

**Constraints**

</div> -->

<a name="Address"/>
<a name="address"/>

## <span class="sectioncount">1.13.0.13<a name="1.13.0.13"> </a></span> 
Address

See also [Examples](datatypes-examples.html#Address), [Formal Definitions](datatypes-definitions.html#Address) and [Mappings](datatypes-mappings.html#Address).

A postal address. There is a variety of postal address formats defined around the world. 
Postal addresses are often also used to record a location that can be
visited to find a patient or person.

<pre class="spec">
&lt;[**[name]**](datatypes-definitions.html#Address "There is a variety of postal address formats defined around the world. This format defines a superset that is the basis for all addresses around the world.") xmlns=&quot;http://hl7.org/fhir&quot;&gt; <span style="float: right">[![doco](help.png)](formats.html "Documentation for this format")</span>
 &lt;!-- from Element: [extension](extensibility.html) --&gt;
 &lt;[<span style="text-decoration: underline">**use**</span>](datatypes-definitions.html#Address.use "The purpose of this address (this element modifies the meaning of other elements)") value=&quot;[<span style="color: darkgreen">[code](datatypes.html#code)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..1**</span> <span style="color: navy">[home | work | temp | old - purpose of this address](address-use.html)</span><span style="color: Gray"> --&gt;</span>
 &lt;[**text**](datatypes-definitions.html#Address.text "A full text representation of the address.") value=&quot;[<span style="color: darkgreen">[string](datatypes.html#string)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..1**</span> <span style="color: navy">Text representation of the address</span><span style="color: Gray"> --&gt;</span>
 &lt;[**line**](datatypes-definitions.html#Address.line "This component contains the house number, apartment number, street name, street direction, 
P.O. Box number, delivery hints, and similar address information.") value=&quot;[<span style="color: darkgreen">[string](datatypes.html#string)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..***</span> <span style="color: navy">Street name, number, direction &amp; P.O. Box etc</span><span style="color: Gray"> --&gt;</span>
 &lt;[**city**](datatypes-definitions.html#Address.city "The name of the city, town, village or other community or delivery center.") value=&quot;[<span style="color: darkgreen">[string](datatypes.html#string)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..1**</span> <span style="color: navy">Name of city, town etc.</span><span style="color: Gray"> --&gt;</span>
 &lt;[**state**](datatypes-definitions.html#Address.state "Sub-unit of a country with limited sovereignty in a federally organized country. A code may be used if codes are in common use (i.e. US 2 letter state codes).") value=&quot;[<span style="color: darkgreen">[string](datatypes.html#string)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..1**</span> <span style="color: navy">Sub-unit of country (abreviations ok)</span><span style="color: Gray"> --&gt;</span>
 &lt;[**zip**](datatypes-definitions.html#Address.zip "A postal code designating a region defined by the postal service.") value=&quot;[<span style="color: darkgreen">[string](datatypes.html#string)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..1**</span> <span style="color: navy">Postal code for area</span><span style="color: Gray"> --&gt;</span>
 &lt;[**country**](datatypes-definitions.html#Address.country "Country - a nation as commonly understood or generally accepted.") value=&quot;[<span style="color: darkgreen">[string](datatypes.html#string)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..1**</span> <span style="color: navy">Country (can be ISO 3166 3 letter code)</span><span style="color: Gray"> --&gt;</span>
 &lt;[**period**](datatypes-definitions.html#Address.period "Time period when address was/is in use.")&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..1**</span> <span style="color: darkgreen">[Period](datatypes.html#Period)</span> <span style="color: navy">Time period when address was/is in use</span><span style="color: Gray"> --&gt;</span>&lt;/period&gt;
&lt;/[name]&gt;
</pre>

<table style="border: 0px; font-size: 11px; font-family: verdana; vertical-align: top;" cellpadding="0" border="0" cellspacing="0"><tr style="border: 1px #F0F0F0 solid; font-size: 11px; font-family: verdana; vertical-align: top;"><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Name</th><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Card.</th><th style="width: 100px" class="heirarchy">Type</th><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Description &amp; Constraints</th></tr><tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck1.png)" class="heirarchy">![.](tbl_spacer.png)![.](icon_element.gif) <span title="There is a variety of postal address formats defined around the world. This format defines a superset that is the basis for all addresses around the world.">Address</span><a name="Address"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy"/><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Element</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">A postal address</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_primitive.png) <span title="The purpose of this address.">use</span><a name="Address.use"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[code](datatypes.html#code)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">home | work | temp | old - purpose of this address
[AddressUse](address-use.html "The use of an address") ([Required](terminologies.html#code "One of the the defined codes must be used"))</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_primitive.png) <span title="A full text representation of the address.">text</span><a name="Address.text"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[string](datatypes.html#string)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Text representation of the address</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_primitive.png) <span title="This component contains the house number, apartment number, street name, street direction, 
P.O. Box number, delivery hints, and similar address information.">line</span><a name="Address.line"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..*</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[string](datatypes.html#string)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Street name, number, direction &amp; P.O. Box etc</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_primitive.png) <span title="The name of the city, town, village or other community or delivery center.">city</span><a name="Address.city"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[string](datatypes.html#string)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Name of city, town etc.</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_primitive.png) <span title="Sub-unit of a country with limited sovereignty in a federally organized country. A code may be used if codes are in common use (i.e. US 2 letter state codes).">state</span><a name="Address.state"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[string](datatypes.html#string)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Sub-unit of country (abreviations ok)</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_primitive.png) <span title="A postal code designating a region defined by the postal service.">zip</span><a name="Address.zip"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[string](datatypes.html#string)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Postal code for area</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_primitive.png) <span title="Country - a nation as commonly understood or generally accepted.">country</span><a name="Address.country"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[string](datatypes.html#string)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Country (can be ISO 3166 3 letter code)</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck00.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin_end.png)![.](icon_datatype.gif) <span title="Time period when address was/is in use.">period</span><a name="Address.period"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[Period](datatypes.html#Period)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Time period when address was/is in use</td></tr>
</table>Alternate definitions: Resource Profile ([XML](Address.profile.xml.html), [JSON](Address.profile.json.html))

### <span class="sectioncount">1.13.0.13.1<a name="1.13.0.13.1"> </a></span> 
Terminology Bindings

<table class="grid">
 <tr><th>Path</th><th>Definition</th><th>Type</th><th>Reference</th></tr>
 <tr><td title="AddressUse" valign="top">Address.use </td><td valign="top">The use of an address</td><td>[Fixed](terminologies.html#code)</td><td valign="top">[http://hl7.org/fhir/address-use](address-use.html)</td> </tr>
</table>

The _text_ element specifies the entire address as it should be represented. This
may be provided instead of or as well as the specific parts. Applications updating an address
SHALL ensure either that the text and the parts are in agreement, or that only one
of the two is present.

<div class="use">

**Constraints**

</div>

Address is used in the following places: [Organization](organization.html), [Practitioner](practitioner.html), [Location](location.html), [RelatedPerson](relatedperson.html) and [Patient](patient.html)

<a name="Contact"/>
<a name="contact"/>

## <span class="sectioncount">1.13.0.14<a name="1.13.0.14"> </a></span> 
Contact

See also [Examples](datatypes-examples.html#Contact), [Formal Definitions](datatypes-definitions.html#Contact) and [Mappings](datatypes-mappings.html#Contact).

All kinds of technology-mediated contact details for a person or organization, including telephone, email, etc.

<pre class="spec">
&lt;[**[name]**](datatypes-definitions.html#Contact "All kinds of technology mediated contact details for a person or organization, including telephone, email, etc.") xmlns=&quot;http://hl7.org/fhir&quot;&gt; <span style="float: right">[![doco](help.png)](formats.html "Documentation for this format")</span>
 &lt;!-- from Element: [extension](extensibility.html) --&gt;
 &lt;[**system**](datatypes-definitions.html#Contact.system "Telecommunications form for contact - what communications system is required to make use of the contact.") value=&quot;[<span style="color: darkgreen">[code](datatypes.html#code)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span title="Inv-2: A system is required if a value is provided." style="color: brown">**![??](lock.png) 0..1**</span> <span style="color: navy">[phone | fax | email | url](contact-system.html)</span><span style="color: Gray"> --&gt;</span>
 &lt;[**value**](datatypes-definitions.html#Contact.value "The actual contact details, in a form that is meaningful to the designated communication system (i.e. phone number or email address).") value=&quot;[<span style="color: darkgreen">[string](datatypes.html#string)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..1**</span> <span style="color: navy">The actual contact details</span><span style="color: Gray"> --&gt;</span>
 &lt;[<span style="text-decoration: underline">**use**</span>](datatypes-definitions.html#Contact.use "Identifies the purpose for the address (this element modifies the meaning of other elements)") value=&quot;[<span style="color: darkgreen">[code](datatypes.html#code)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..1**</span> <span style="color: navy">[home | work | temp | old | mobile - purpose of this address](contact-use.html)</span><span style="color: Gray"> --&gt;</span>
 &lt;[**period**](datatypes-definitions.html#Contact.period "Time period when the contact was/is in use.")&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..1**</span> <span style="color: darkgreen">[Period](datatypes.html#Period)</span> <span style="color: navy">Time period when the contact was/is in use</span><span style="color: Gray"> --&gt;</span>&lt;/period&gt;
&lt;/[name]&gt;
</pre>

<table style="border: 0px; font-size: 11px; font-family: verdana; vertical-align: top;" cellpadding="0" border="0" cellspacing="0"><tr style="border: 1px #F0F0F0 solid; font-size: 11px; font-family: verdana; vertical-align: top;"><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Name</th><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Card.</th><th style="width: 100px" class="heirarchy">Type</th><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Description &amp; Constraints</th></tr><tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck1.png)" class="heirarchy">![.](tbl_spacer.png)![.](icon_element.gif) <span title="All kinds of technology mediated contact details for a person or organization, including telephone, email, etc.">Contact</span><a name="Contact"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy"/><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Element</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Technology mediated contact details (phone, fax, email, etc)
<span title="2">A system is required if a value is provided.</span></td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_primitive.png) <span title="Telecommunications form for contact - what communications system is required to make use of the contact.">system</span><a name="Contact.system"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[code](datatypes.html#code)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">phone | fax | email | url
[ContactSystem](contact-system.html "Telecommunications form for contact") ([Required](terminologies.html#code "One of the the defined codes must be used"))</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_primitive.png) <span title="The actual contact details, in a form that is meaningful to the designated communication system (i.e. phone number or email address).">value</span><a name="Contact.value"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[string](datatypes.html#string)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">The actual contact details</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_primitive.png) <span title="Identifies the purpose for the address.">use</span><a name="Contact.use"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[code](datatypes.html#code)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">home | work | temp | old | mobile - purpose of this address
[ContactUse](contact-use.html "Location, type or status of telecommunications address indicating use") ([Required](terminologies.html#code "One of the the defined codes must be used"))</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck00.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin_end.png)![.](icon_datatype.gif) <span title="Time period when the contact was/is in use.">period</span><a name="Contact.period"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[Period](datatypes.html#Period)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Time period when the contact was/is in use</td></tr>
</table>Alternate definitions: Resource Profile ([XML](Contact.profile.xml.html), [JSON](Contact.profile.json.html))

### <span class="sectioncount">1.13.0.14.1<a name="1.13.0.14.1"> </a></span> 
Terminology Bindings

<table class="grid">
 <tr><th>Path</th><th>Definition</th><th>Type</th><th>Reference</th></tr>
 <tr><td title="ContactSystem" valign="top">Contact.system </td><td valign="top">Telecommunications form for contact</td><td>[Fixed](terminologies.html#code)</td><td valign="top">[http://hl7.org/fhir/contact-system](contact-system.html)</td> </tr>
 <tr><td title="ContactUse" valign="top">Contact.use </td><td valign="top">Location, type or status of telecommunications address indicating use</td><td>[Fixed](terminologies.html#code)</td><td valign="top">[http://hl7.org/fhir/contact-use](contact-use.html)</td> </tr>
</table>

If capturing a phone, fax or similar contact, the value should be a properly formatted telephone number according to 
[ITU-T E.123](http://www.itu.int/rec/T-REC-E.123-200102-I/e). 
However, this is frequently not possible due to legacy data and/or recording methods.

<div class="use">

**Constraints**

*   **Inv-2**: A system is required if a value is provided. (xpath: <span style="font-family: Courier New, monospace">not(exists(f:value)) or exists(f:system)</span>)
</div>

Contact is used in the following places: [Organization](organization.html), [ValueSet](valueset.html), [Conformance](conformance.html), [Profile](profile.html), [Subscription](subscription.html), [ConceptMap](conceptmap.html), [Practitioner](practitioner.html), [Device](device.html), [MessageHeader](messageheader.html), [DataElement](dataelement.html), [Location](location.html), [RelatedPerson](relatedperson.html), [Namespace](namespace.html) and [Patient](patient.html)

<a name="Schedule"/>
<a name="schedule"/>

## <span class="sectioncount">1.13.0.15<a name="1.13.0.15"> </a></span> 
Schedule

See also [Examples](datatypes-examples.html#Schedule), [Formal Definitions](datatypes-definitions.html#Schedule) and [Mappings](datatypes-mappings.html#Schedule).

Specifies an event that may occur multiple times. Schedules are not used for recording when things did happen, but when they are expected or requested to occur.
A schedule can be either a list of events - periods on which the event occurs, 
or a single event with repeating criteria, or just repeating criteria with no actual event. 

  <!-- 

Note: a possible enhancement to this is to have the repeat content repeat with each event. This is richer and more complex - is the added functionality useful?

 -->
<pre class="spec">
&lt;[**[name]**](datatypes-definitions.html#Schedule "Specifies an event that may occur multiple times. Schedules are used for to reord when things are expected or requested to occur.") xmlns=&quot;http://hl7.org/fhir&quot;&gt; <span style="float: right">[![doco](help.png)](formats.html "Documentation for this format")</span>
 &lt;!-- from Element: [extension](extensibility.html) --&gt;
 &lt;[**event**](datatypes-definitions.html#Schedule.event "Identifies specific time periods when the event should occur.")&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**0..***</span> <span style="color: darkgreen">[Period](datatypes.html#Period)</span> <span style="color: navy">When the event occurs</span><span style="color: Gray"> --&gt;</span>&lt;/event&gt;
 &lt;[**repeat**](datatypes-definitions.html#Schedule.repeat "Identifies a repeating pattern to the intended time periods.")&gt;  <span style="color: Gray">&lt;!-- <span title="Inv-1: There can only be a repeat element if there is none or one event" style="color: brown">**![??](lock.png) 0..1**</span> Only if there is none or one event --&gt;</span>
  &lt;[**frequency**](datatypes-definitions.html#Schedule.repeat.frequency "Indicates how often the event should occur.") value=&quot;[<span style="color: darkgreen">[integer](datatypes.html#integer)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span title="Inv-2: Either frequency or when SHALL be present, but not both" style="color: brown">**![??](lock.png) 0..1**</span> <span style="color: navy">Event occurs frequency times per duration</span><span style="color: Gray"> --&gt;</span>
  &lt;[**when**](datatypes-definitions.html#Schedule.repeat.when "Identifies the occurrence of daily life that determines timing.") value=&quot;[<span style="color: darkgreen">[code](datatypes.html#code)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span title="Inv-2: Either frequency or when SHALL be present, but not both" style="color: brown">**![??](lock.png) 0..1**</span> <span style="color: navy">[HS | WAKE | AC | ACM | ACD | ACV | PC | PCM | PCD | PCV - common life events](event-timing.html)</span><span style="color: Gray"> --&gt;</span>
  &lt;[**duration**](datatypes-definitions.html#Schedule.repeat.duration "How long each repetition should last.") value=&quot;[<span style="color: darkgreen">[decimal](datatypes.html#decimal)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span title="Inv-4: duration SHALL be a positive value" style="color: brown">**![??](lock.png) 1..1**</span> <span style="color: navy">Repeating or event-related duration</span><span style="color: Gray"> --&gt;</span>
  &lt;[**units**](datatypes-definitions.html#Schedule.repeat.units "The units of time for the duration.") value=&quot;[<span style="color: darkgreen">[code](datatypes.html#code)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span style="color: brown">**1..1**</span> <span style="color: navy">[s | min | h | d | wk | mo | a - unit of time (UCUM)](units-of-time.html)</span><span style="color: Gray"> --&gt;</span>
  &lt;[**count**](datatypes-definitions.html#Schedule.repeat.count "A total count of the desired number of repetitions.") value=&quot;[<span style="color: darkgreen">[integer](datatypes.html#integer)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span title="Inv-3: At most, only one of count or end can be present" style="color: brown">**![??](lock.png) 0..1**</span> <span style="color: navy">Number of times to repeat</span><span style="color: Gray"> --&gt;</span>
  &lt;[**end**](datatypes-definitions.html#Schedule.repeat.end "When to stop repeating the schedule.") value=&quot;[<span style="color: darkgreen">[dateTime](datatypes.html#dateTime)</span>]&quot;/&gt;<span style="color: Gray">&lt;!--</span> <span title="Inv-3: At most, only one of count or end can be present" style="color: brown">**![??](lock.png) 0..1**</span> <span style="color: navy">When to stop repeats</span><span style="color: Gray"> --&gt;</span>
 &lt;/repeat&gt;
&lt;/[name]&gt;
</pre>

<table style="border: 0px; font-size: 11px; font-family: verdana; vertical-align: top;" cellpadding="0" border="0" cellspacing="0"><tr style="border: 1px #F0F0F0 solid; font-size: 11px; font-family: verdana; vertical-align: top;"><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Name</th><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Card.</th><th style="width: 100px" class="heirarchy">Type</th><th style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Description &amp; Constraints</th></tr><tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck1.png)" class="heirarchy">![.](tbl_spacer.png)![.](icon_element.gif) <span title="Specifies an event that may occur multiple times. Schedules are used for to reord when things are expected or requested to occur.">Schedule</span><a name="Schedule"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy"/><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Element</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">A schedule that specifies an event that may occur multiple times
<span title="1">There can only be a repeat element if there is none or one event</span></td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck10.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin.png)![.](icon_datatype.gif) <span title="Identifies specific time periods when the event should occur.">event</span><a name="Schedule.event"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..*</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[Period](datatypes.html#Period)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">When the event occurs</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck01.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_vjoin_end.png)![.](icon_element.gif) <span title="Identifies a repeating pattern to the intended time periods.">repeat</span><a name="Schedule.repeat"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy"/><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Element</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Only if there is none or one event
<span title="3">At most, only one of count or end can be present</span><span title="2">Either frequency or when SHALL be present, but not both</span></td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck010.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_blank.png)![.](tbl_vjoin.png)![.](icon_primitive.png) <span title="Indicates how often the event should occur.">frequency</span><a name="Schedule.repeat.frequency"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[integer](datatypes.html#integer)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Event occurs frequency times per duration</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck010.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_blank.png)![.](tbl_vjoin.png)![.](icon_primitive.png) <span title="Identifies the occurrence of daily life that determines timing.">when</span><a name="Schedule.repeat.when"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[code](datatypes.html#code)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">HS | WAKE | AC | ACM | ACD | ACV | PC | PCM | PCD | PCV - common life events
[EventTiming](event-timing.html "Real world event that the schedule relates to") ([Required](terminologies.html#code "One of the the defined codes must be used"))</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck010.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_blank.png)![.](tbl_vjoin.png)![.](icon_primitive.png) <span title="How long each repetition should last.">duration</span><a name="Schedule.repeat.duration"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">1..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[decimal](datatypes.html#decimal)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Repeating or event-related duration
<span title="4">duration SHALL be a positive value</span></td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck010.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_blank.png)![.](tbl_vjoin.png)![.](icon_primitive.png) <span title="The units of time for the duration.">units</span><a name="Schedule.repeat.units"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">1..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[code](datatypes.html#code)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">s | min | h | d | wk | mo | a - unit of time (UCUM)
[UnitsOfTime](units-of-time.html "A unit of time (units from UCUM)") ([Required](terminologies.html#code "One of the the defined codes must be used"))</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck010.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_blank.png)![.](tbl_vjoin.png)![.](icon_primitive.png) <span title="A total count of the desired number of repetitions.">count</span><a name="Schedule.repeat.count"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[integer](datatypes.html#integer)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">Number of times to repeat</td></tr>
<tr style="border: 0px; padding:0px; vertical-align: top; background-color: white;"><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px; white-space: nowrap; background-image: url(tbl_bck000.png)" class="heirarchy">![.](tbl_spacer.png)![.](tbl_blank.png)![.](tbl_vjoin_end.png)![.](icon_primitive.png) <span title="When to stop repeating the schedule.">end</span><a name="Schedule.repeat.end"> </a></td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">0..1</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">[dateTime](datatypes.html#dateTime)</td><td style="vertical-align: top; text-align : left; padding:0px 4px 0px 4px" class="heirarchy">When to stop repeats</td></tr>
</table>Alternate definitions: Resource Profile ([XML](Schedule.profile.xml.html), [JSON](Schedule.profile.json.html))

### <span class="sectioncount">1.13.0.15.1<a name="1.13.0.15.1"> </a></span> 
Terminology Bindings

<table class="grid">
 <tr><th>Path</th><th>Definition</th><th>Type</th><th>Reference</th></tr>
 <tr><td title="EventTiming" valign="top">Schedule.repeat.when </td><td valign="top">Real world event that the schedule relates to</td><td>[Fixed](terminologies.html#code)</td><td valign="top">[http://hl7.org/fhir/event-timing](event-timing.html)</td> </tr>
 <tr><td title="UnitsOfTime" valign="top">Schedule.repeat.units </td><td valign="top">A unit of time (units from UCUM)</td><td>[Fixed](terminologies.html#code)</td><td valign="top">[http://hl7.org/fhir/units-of-time](units-of-time.html)</td> </tr>
</table>

If events are specified, at least _event.start_ SHALL be specified for each event. If no _event.end_ is 
specified, the event is assumed to last a limited but unknown time as clinically relevant.

If the schedule has repeating criteria, the repeat can occur a given number of times per 
the specified duration or in relation to some real world event. Also, if the event repeats,
a time to end the schedule can be specified, either with a count of the number of times 
it can occur or a date/time at which to end the schedule. If no end condition is specified, 
the Schedule will terminate on some criteria that are expressed elsewhere. 

<div class="use">

**Constraints**

*   **Inv-1**: There can only be a repeat element if there is none or one event (xpath: <span style="font-family: Courier New, monospace">not(exists(f:repeat)) or count(f:event) &lt; 2</span>)
*   **Inv-2**: On Schedule.repeat: Either frequency or when SHALL be present, but not both (xpath on f:Schedule/f:repeat: <span style="font-family: Courier New, monospace">exists(f:frequency) != exists(f:when)</span>)
*   **Inv-3**: On Schedule.repeat: At most, only one of count or end can be present (xpath on f:Schedule/f:repeat: <span style="font-family: Courier New, monospace">not(exists(f:count) and exists(f:end))</span>)
*   **Inv-4**: On Schedule.repeat.duration: duration SHALL be a positive value (xpath on f:Schedule/f:repeat/f:duration: <span style="font-family: Courier New, monospace">@value &gt; 0 or not(@value)</span>)

</div>

Schedule is used in the following places: [MedicationDispense](medicationdispense.html), [MedicationPrescription](medicationprescription.html), [MedicationStatement](medicationstatement.html), [CarePlan](careplan.html) and [Order](order.html)

<a name="open"> </a>

## <span class="sectioncount">1.13.0.16<a name="1.13.0.16"> </a></span> Open Type Element

Some elements do not have a specified type. The type is represented by the wildcard symbol &quot;*&quot;. In these cases, the element type may be one of the following:

*   [integer](datatypes.html#integer)
*   [decimal](datatypes.html#decimal)
*   [dateTime](datatypes.html#dateTime)
*   [date](datatypes.html#date)
*   [instant](datatypes.html#instant)
*   [string](datatypes.html#string)
*   [uri](datatypes.html#uri)
*   [boolean](datatypes.html#boolean)
*   [code](datatypes.html#code) - if the extension definition provides a binding to a suitable set of codes
*   [base64Binary](datatypes.html#base64Binary)
*   [Coding](datatypes.html#Coding)
*   [CodeableConcept](datatypes.html#CodeableConcept)
*   [Attachment](datatypes.html#Attachment)
*   [Identifier](datatypes.html#Identifier)
*   [Quantity](datatypes.html#Quantity)
*   [Range](datatypes.html#Range)
*   [Period](datatypes.html#Period)
*   [Ratio](datatypes.html#Ratio)
*   [HumanName](datatypes.html#HumanName)
*   [Address](datatypes.html#Address)
*   [Contact](datatypes.html#Contact)
*   [Schedule](datatypes.html#Schedule)
*   [Resource](references.html#ResourceReference) - a reference to another resource

The element name ends with &quot;[x]&quot;, and this is replaced with the Title cased name of the data type.

Open references are used in the following places: [Profile](profile.html), [DataElement](dataelement.html) and [QuestionnaireAnswers](questionnaireanswers.html)

<a name="other"> </a>

## <span class="sectioncount">1.13.0.17<a name="1.13.0.17"> </a></span> Other Types

The following types are defined as part of the data types, but are documented elsewhere in the specification:

<svg height="219.0" width="780.0" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns="http://www.w3.org/2000/svg" version="1.1">  <defs>
    <filter id="shadow" height="200%" width="200%" y="0" x="0">
      <feOffset result="offOut" dx="3" dy="3" in="SourceGraphic"/>
      <feColorMatrix result="matrixOut" values="0.2 0 0 0 0 0 0.2 0 0 0 0 0 0.2 0 0 0 0 0 1 0" type="matrix" in="offOut"/>
      <feGaussianBlur result="blurOut" stdDeviation="2" in="matrixOut"/>
      <feBlend in2="blurOut" in="SourceGraphic" mode="normal"/>
    </filter>
  </defs><rect height="46.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="104.0" filter="url(#shadow)" rx="4" y="9.0" ry="4" x="280.0"/><text fill="black" class="diagram-class-title" y="29.0" x="332.0">Element</text><line style="stroke:dimgrey;stroke-width:1" y1="37.0" y2="37.0" x2="384.0" x1="280.0"/><text fill="black" class="diagram-class-detail" y="51.0" x="286.0">[<title>Extensions - as described for all elements: additional information that is not part of the basic definition of the resource / type</title>extension](extensibility.html) : [Extension](extensibility.html) 0..*</text><rect height="64.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="76.0" filter="url(#shadow)" rx="4" y="0.0" ry="4" x="504.0"/><line style="stroke:dimgrey;stroke-width:1" y1="28.0" y2="28.0" x2="580.0" x1="504.0"/><text fill="black" class="diagram-class-title" y="20.0" x="542.0">[Extension](extensibility.html#extension)</text><text fill="black" class="diagram-class-detail" y="42.0" x="510.0">[<title>Source of the definition for the extension code - a logical name or a URL</title>url](base-definitions.html#Extension.url) : [uri](datatypes.html#uri) 1..1</text><text fill="black" class="diagram-class-detail" y="56.0" x="510.0">[<title>Value of extension - may be a resource or one of a constrained set of the data types (see Extensibility in the spec for list)</title>value[x]](base-definitions.html#Extension.value_x_) : [*](datatypes.html#open) 0..1</text><rect height="64.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="160.0" filter="url(#shadow)" rx="4" y="0.0" ry="4" x="0.0"/><line style="stroke:dimgrey;stroke-width:1" y1="28.0" y2="28.0" x2="160.0" x1="0.0"/><text fill="black" class="diagram-class-title" y="20.0" x="80.0">[Narrative](narrative.html#narrative)</text><text fill="black" class="diagram-class-detail" y="42.0" x="6.0">[<title>The status of the narrative - whether it's entirely generated (from just the defined data or the extensions too), or whether a human authored it and it may contain additional data</title>status](base-definitions.html#Narrative.status) : [code](datatypes.html#code) 1..1 芦 [<title>The status of a resource narrative</title>NarrativeStatus](narrative-status.html) 禄</text><text fill="black" class="diagram-class-detail" y="56.0" x="6.0">[<title>The actual narrative content, a stripped down version of XHTML</title>div](base-definitions.html#Narrative.div) : [xhtml](narrative.html#xhtml) 1..1</text><rect height="64.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="122.4" filter="url(#shadow)" rx="4" y="135.0" ry="4" x="270.8"/><line style="stroke:dimgrey;stroke-width:1" y1="163.0" y2="163.0" x2="393.20000000000005" x1="270.8"/><text fill="black" class="diagram-class-title" y="155.0" x="332.0">[ResourceReference](references.html#resourcereference)</text><text fill="black" class="diagram-class-detail" y="177.0" x="276.8">[<title>A reference to a location at which the other resource is found. The reference may a relative reference, in which case it is relative to the service base URL, or an absolute URL that resolves to the location where the resource is found. The reference may be version specific or not. If the reference is not to a FHIR RESTful server, then it should be assumed to be version specific. Internal fragment references (start with '#') refer to contained resources</title>reference](base-definitions.html#ResourceReference.reference) : [string](datatypes.html#string) 0..1</text><text fill="black" class="diagram-class-detail" y="191.0" x="276.8">[<title>Plain text narrative that identifies the resource in addition to the resource reference</title>display](base-definitions.html#ResourceReference.display) : [string](datatypes.html#string) 0..1</text><line style="stroke:navy;stroke-width:1" y1="32.0" y2="32.0" x2="504.0" x1="384.0"/><polygon transform="rotate(0.0 384.0 32.0)" style="fill:white;stroke:navy;stroke-width:1" points="384.0,32.0 392.0,38.0 392.0,26.0 384.0,32.0"/><line style="stroke:navy;stroke-width:1" y1="32.0" y2="32.0" x2="160.0" x1="280.0"/><polygon transform="rotate(180.0 280.0 32.0)" style="fill:white;stroke:navy;stroke-width:1" points="280.0,32.0 288.0,38.0 288.0,26.0 280.0,32.0"/><line style="stroke:navy;stroke-width:1" y1="55.0" y2="135.00000000000003" x2="332.0" x1="332.0"/><polygon transform="rotate(90.0 332.0 55.0)" style="fill:white;stroke:navy;stroke-width:1" points="332.0,55.0 340.0,61.0 340.0,49.0 332.0,55.0"/></svg>

*   **[Resource](resources.html#metadata)** - the conceptual base class for all resources
*   **[ResourceReference](references.html#Resource)** - for references from one resource to another
*   **[Extension](extensibility.html)** - used to convey additional data in a resource
*   **[Narrative](narrative.html#Narrative)** - conveys a human-readable representation of the content of a resource

</div>
<div class="col-3"><div class="itoc">

On This Page:

[Primitive Types](#primitive)

[Data Types](#Types)

[Other Types](#other)

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
               [Compare to DSTU](http://services.w3.org/htmldiff?doc1=http%3A%2F%2Fhl7.org%2Fimplement%2Fstandards%2Ffhir%2Fdatatypes.html&amp;doc2=http%3A%2F%2Fhl7.org%2Fimplement%2Fstandards%2FFHIR-Develop%2Fdatatypes.html) | 
               [License](license.html) | 
               [Propose a change](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemAdd&amp;tracker_id=677)   
        </span>

			</div>  <!-- /inner-wrapper -->
		</div>  <!-- /container -->
	</div>  <!-- /segment-footer -->
  <!-- disqus thread -->
  <!-- disqus -->
  <!-- end disqus -->        