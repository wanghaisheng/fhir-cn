title: 
date: 
categories: doc
---

[首页](../home/index.html) >[文档](documentation.html) >[数据类型](datatypes.html)> **数据类型的定义**        

本页内容:

*   [数据类型](datatypes.html)
*   [示例](datatypes-examples.html)
*   [详细描述](datatypes-definitions.html)
*   [映射](datatypes-mappings.html)
### 1.17.2   Data Type Detailed Descriptions

This page provides the detailed descriptions for the data types

**Table of Contents**

<table class="grid">
 <tr>
  <td>**Primitive Types**
<svg height="188" width="330" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns="http://www.w3.org/2000/svg" version="1.1">  <defs>
    <filter id="shadow" height="200%" width="200%" y="0" x="0">
      <feOffset result="offOut" dx="3" dy="3" in="SourceGraphic"/>
      <feColorMatrix result="matrixOut" values="0.2 0 0 0 0 0 0.2 0 0 0 0 0 0.2 0 0 0 0 0 1 0" type="matrix" in="offOut"/>
      <feGaussianBlur result="blurOut" stdDeviation="2" in="matrixOut"/>
      <feBlend in2="blurOut" in="SourceGraphic" mode="normal"/>
    </filter>
  </defs><rect height="28.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="50.4" filter="url(#shadow)" rx="4" y="50.0" ry="4" x="130.0"/><text fill="black" class="diagram-class-title" y="70.0" x="155.2">Element</text><rect height="28.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="50.4" filter="url(#shadow)" rx="4" y="0.0" ry="4" x="0.0"/><line style="stroke:dimgrey;stroke-width:1" y1="28.0" y2="28.0" x2="50.4" x1="0.0"/><text fill="black" class="diagram-class-title" y="20.0" x="25.2">[instant](#instant)</text><rect height="28.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="28.8" filter="url(#shadow)" rx="4" y="0.0" ry="4" x="80.0"/><line style="stroke:dimgrey;stroke-width:1" y1="28.0" y2="28.0" x2="108.8" x1="80.0"/><text fill="black" class="diagram-class-title" y="20.0" x="94.4">[time](#time)</text><rect height="28.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="28.8" filter="url(#shadow)" rx="4" y="0.0" ry="4" x="180.0"/><line style="stroke:dimgrey;stroke-width:1" y1="28.0" y2="28.0" x2="208.8" x1="180.0"/><text fill="black" class="diagram-class-title" y="20.0" x="194.4">[date](#date)</text><rect height="28.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="57.6" filter="url(#shadow)" rx="4" y="0.0" ry="4" x="230.0"/><line style="stroke:dimgrey;stroke-width:1" y1="28.0" y2="28.0" x2="287.6" x1="230.0"/><text fill="black" class="diagram-class-title" y="20.0" x="258.8">[dateTime](#datetime)</text><rect height="28.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="50.4" filter="url(#shadow)" rx="4" y="50.0" ry="4" x="0.0"/><line style="stroke:dimgrey;stroke-width:1" y1="78.0" y2="78.0" x2="50.4" x1="0.0"/><text fill="black" class="diagram-class-title" y="70.0" x="25.2">[decimal](#decimal)</text><rect height="28.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="50.4" filter="url(#shadow)" rx="4" y="50.0" ry="4" x="230.0"/><line style="stroke:dimgrey;stroke-width:1" y1="78.0" y2="78.0" x2="280.4" x1="230.0"/><text fill="black" class="diagram-class-title" y="70.0" x="255.2">[boolean](#boolean)</text><rect height="28.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="50.4" filter="url(#shadow)" rx="4" y="100.0" ry="4" x="0.0"/><line style="stroke:dimgrey;stroke-width:1" y1="128.0" y2="128.0" x2="50.4" x1="0.0"/><text fill="black" class="diagram-class-title" y="120.0" x="25.2">[integer](#integer)</text><rect height="28.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="43.2" filter="url(#shadow)" rx="4" y="100.0" ry="4" x="80.0"/><line style="stroke:dimgrey;stroke-width:1" y1="128.0" y2="128.0" x2="123.2" x1="80.0"/><text fill="black" class="diagram-class-title" y="120.0" x="101.6">[string](#string)</text><rect height="28.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="21.6" filter="url(#shadow)" rx="4" y="100.0" ry="4" x="180.0"/><line style="stroke:dimgrey;stroke-width:1" y1="128.0" y2="128.0" x2="201.6" x1="180.0"/><text fill="black" class="diagram-class-title" y="120.0" x="190.8">[uri](#uri)</text><rect height="28.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="86.4" filter="url(#shadow)" rx="4" y="100.0" ry="4" x="230.0"/><line style="stroke:dimgrey;stroke-width:1" y1="128.0" y2="128.0" x2="316.4" x1="230.0"/><text fill="black" class="diagram-class-title" y="120.0" x="273.2">[base64Binary](#base64binary)</text><rect height="28.0" style="fill:#f8ddf8;stroke:black;stroke-width:1" width="28.8" filter="url(#shadow)" rx="4" y="140.0" ry="4" x="30.0"/><line style="stroke:dimgrey;stroke-width:1" y1="168.0" y2="168.0" x2="58.8" x1="30.0"/><text fill="black" class="diagram-class-title" y="160.0" x="44.4">[code](#code)</text><rect height="28.0" style="fill:#f8ddf8;stroke:black;stroke-width:1" width="14.4" filter="url(#shadow)" rx="4" y="140.0" ry="4" x="130.0"/><line style="stroke:dimgrey;stroke-width:1" y1="168.0" y2="168.0" x2="144.4" x1="130.0"/><text fill="black" class="diagram-class-title" y="160.0" x="137.2">[id](#id)</text><rect height="28.0" style="fill:#f8ddf8;stroke:black;stroke-width:1" width="21.6" filter="url(#shadow)" rx="4" y="140.0" ry="4" x="220.0"/><line style="stroke:dimgrey;stroke-width:1" y1="168.0" y2="168.0" x2="241.6" x1="220.0"/><text fill="black" class="diagram-class-title" y="160.0" x="230.8">[oid](#oid)</text><line style="stroke:navy;stroke-width:1" y1="54.30769230769231" y2="23.692307692307693" x2="50.4" x1="130.0"/><polygon transform="rotate(-158.96248897457818 130.0 54.30769230769231)" style="fill:white;stroke:navy;stroke-width:1" points="130.0,54.30769230769231 138.0,60.30769230769231 138.0,48.30769230769231 130.0,54.30769230769231"/><line style="stroke:navy;stroke-width:1" y1="50.00000000000001" y2="25.842105263157897" x2="108.8" x1="138.176"/><polygon transform="rotate(-140.56720035264516 138.176 50.00000000000001)" style="fill:white;stroke:navy;stroke-width:1" points="138.176,50.00000000000001 146.176,56.00000000000001 146.176,44.00000000000001 138.176,50.00000000000001"/><line style="stroke:navy;stroke-width:1" y1="50.0" y2="28.0" x2="183.42399999999998" x1="166.176"/><polygon transform="rotate(-51.903553919725034 166.176 50.0)" style="fill:white;stroke:navy;stroke-width:1" points="166.176,50.0 174.176,56.0 174.176,44.0 166.176,50.0"/><line style="stroke:navy;stroke-width:1" y1="51.83783783783784" y2="27.89961389961391" x2="230.0" x1="180.4"/><polygon transform="rotate(-25.763140843290184 180.4 51.83783783783784)" style="fill:white;stroke:navy;stroke-width:1" points="180.4,51.83783783783784 188.4,57.83783783783784 188.4,45.83783783783784 180.4,51.83783783783784"/><line style="stroke:navy;stroke-width:1" y1="64.0" y2="64.0" x2="50.4" x1="130.0"/><polygon transform="rotate(180.0 130.0 64.0)" style="fill:white;stroke:navy;stroke-width:1" points="130.0,64.0 138.0,70.0 138.0,58.0 130.0,64.0"/><line style="stroke:navy;stroke-width:1" y1="64.0" y2="64.0" x2="230.0" x1="180.4"/><polygon transform="rotate(0.0 180.4 64.0)" style="fill:white;stroke:navy;stroke-width:1" points="180.4,64.0 188.4,70.0 188.4,58.0 180.4,64.0"/><line style="stroke:navy;stroke-width:1" y1="73.6923076923077" y2="104.3076923076923" x2="50.4" x1="130.0"/><polygon transform="rotate(158.96248897457818 130.0 73.6923076923077)" style="fill:white;stroke:navy;stroke-width:1" points="130.0,73.6923076923077 138.0,79.6923076923077 138.0,67.6923076923077 130.0,73.6923076923077"/><line style="stroke:navy;stroke-width:1" y1="78.0" y2="100.0" x2="116.60800000000002" x1="140.192"/><polygon transform="rotate(136.99017224975486 140.192 78.0)" style="fill:white;stroke:navy;stroke-width:1" points="140.192,78.0 148.192,84.0 148.192,72.0 140.192,78.0"/><line style="stroke:navy;stroke-width:1" y1="78.00000000000003" y2="100.00000000000003" x2="180.83200000000002" x1="165.168"/><polygon transform="rotate(54.549133928735905 165.168 78.00000000000003)" style="fill:white;stroke:navy;stroke-width:1" points="165.168,78.00000000000003 173.168,84.00000000000003 173.168,72.00000000000003 165.168,78.00000000000003"/><line style="stroke:navy;stroke-width:1" y1="74.6779661016949" y2="99.99999999999999" x2="240.16" x1="180.4"/><polygon transform="rotate(22.96377305985455 180.4 74.6779661016949)" style="fill:white;stroke:navy;stroke-width:1" points="180.4,74.6779661016949 188.4,80.6779661016949 188.4,68.6779661016949 180.4,74.6779661016949"/><line style="stroke:navy;stroke-width:1" y1="128.0" y2="143.93006993006992" x2="58.8" x1="81.57999999999998"/><polygon transform="rotate(145.03487922646644 81.57999999999998 128.0)" style="fill:white;stroke:navy;stroke-width:1" points="81.57999999999998,128.0 89.57999999999998,134.0 89.57999999999998,122.0 81.57999999999998,128.0"/><line style="stroke:navy;stroke-width:1" y1="128.0" y2="145.91011235955054" x2="130.0" x1="114.06"/><polygon transform="rotate(48.33091738045002 114.06 128.0)" style="fill:white;stroke:navy;stroke-width:1" points="114.06,128.0 122.06,134.0 122.06,122.0 114.06,128.0"/><line style="stroke:navy;stroke-width:1" y1="124.8" y2="143.2" x2="220.0" x1="201.6"/><polygon transform="rotate(44.999999999999986 201.6 124.8)" style="fill:white;stroke:navy;stroke-width:1" points="201.6,124.8 209.6,130.8 209.6,118.8 201.6,124.8"/></svg></td>
  <td>**Complex Types**
<svg height="218" width="440" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns="http://www.w3.org/2000/svg" version="1.1">  <defs>
    <filter id="shadow" height="200%" width="200%" y="0" x="0">
      <feOffset result="offOut" dx="3" dy="3" in="SourceGraphic"/>
      <feColorMatrix result="matrixOut" values="0.2 0 0 0 0 0 0.2 0 0 0 0 0 0.2 0 0 0 0 0 1 0" type="matrix" in="offOut"/>
      <feGaussianBlur result="blurOut" stdDeviation="2" in="matrixOut"/>
      <feBlend in2="blurOut" in="SourceGraphic" mode="normal"/>
    </filter>
  </defs><rect height="28.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="50.4" filter="url(#shadow)" rx="4" y="70.0" ry="4" x="150.0"/><text fill="black" class="diagram-class-title" y="90.0" x="175.2">Element</text><rect height="28.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="72.0" filter="url(#shadow)" rx="4" y="0.0" ry="4" x="300.0"/><line style="stroke:dimgrey;stroke-width:1" y1="28.0" y2="28.0" x2="372.0" x1="300.0"/><text fill="black" class="diagram-class-title" y="20.0" x="336.0">[Identifier](#identifier)</text><rect height="28.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="64.8" filter="url(#shadow)" rx="4" y="40.0" ry="4" x="310.0"/><line style="stroke:dimgrey;stroke-width:1" y1="68.0" y2="68.0" x2="374.8" x1="310.0"/><text fill="black" class="diagram-class-title" y="60.0" x="342.4">[HumanName](#humanname)</text><rect height="28.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="50.4" filter="url(#shadow)" rx="4" y="80.0" ry="4" x="315.0"/><line style="stroke:dimgrey;stroke-width:1" y1="108.0" y2="108.0" x2="365.4" x1="315.0"/><text fill="black" class="diagram-class-title" y="100.0" x="340.2">[Address](#address)</text><rect height="28.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="86.4" filter="url(#shadow)" rx="4" y="120.0" ry="4" x="320.0"/><line style="stroke:dimgrey;stroke-width:1" y1="148.0" y2="148.0" x2="406.4" x1="320.0"/><text fill="black" class="diagram-class-title" y="140.0" x="363.2">[ContactPoint](#contactpoint)</text><rect height="28.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="43.2" filter="url(#shadow)" rx="4" y="40.0" ry="4" x="0.0"/><line style="stroke:dimgrey;stroke-width:1" y1="68.0" y2="68.0" x2="43.2" x1="0.0"/><text fill="black" class="diagram-class-title" y="60.0" x="21.6">[Timing](#timing)</text><rect height="28.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="57.6" filter="url(#shadow)" rx="4" y="120.0" ry="4" x="140.0"/><line style="stroke:dimgrey;stroke-width:1" y1="148.0" y2="148.0" x2="197.6" x1="140.0"/><text fill="black" class="diagram-class-title" y="140.0" x="168.8">[Quantity](#quantity)</text><rect height="28.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="72.0" filter="url(#shadow)" rx="4" y="0.0" ry="4" x="200.0"/><line style="stroke:dimgrey;stroke-width:1" y1="28.0" y2="28.0" x2="272.0" x1="200.0"/><text fill="black" class="diagram-class-title" y="20.0" x="236.0">[Attachment](#attachment)</text><rect height="28.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="36.0" filter="url(#shadow)" rx="4" y="0.0" ry="4" x="150.0"/><line style="stroke:dimgrey;stroke-width:1" y1="28.0" y2="28.0" x2="186.0" x1="150.0"/><text fill="black" class="diagram-class-title" y="20.0" x="168.0">[Range](#range)</text><rect height="28.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="43.2" filter="url(#shadow)" rx="4" y="0.0" ry="4" x="80.0"/><line style="stroke:dimgrey;stroke-width:1" y1="28.0" y2="28.0" x2="123.2" x1="80.0"/><text fill="black" class="diagram-class-title" y="20.0" x="101.6">[Period](#period)</text><rect height="28.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="36.0" filter="url(#shadow)" rx="4" y="0.0" ry="4" x="15.0"/><line style="stroke:dimgrey;stroke-width:1" y1="28.0" y2="28.0" x2="51.0" x1="15.0"/><text fill="black" class="diagram-class-title" y="20.0" x="33.0">[Ratio](#ratio)</text><rect height="28.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="108.0" filter="url(#shadow)" rx="4" y="120.0" ry="4" x="0.0"/><line style="stroke:dimgrey;stroke-width:1" y1="148.0" y2="148.0" x2="108.0" x1="0.0"/><text fill="black" class="diagram-class-title" y="140.0" x="54.0">[CodeableConcept](#codeableconcept)</text><rect height="28.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="43.2" filter="url(#shadow)" rx="4" y="80.0" ry="4" x="0.0"/><line style="stroke:dimgrey;stroke-width:1" y1="108.0" y2="108.0" x2="43.2" x1="0.0"/><text fill="black" class="diagram-class-title" y="100.0" x="21.6">[Coding](#coding)</text><rect height="28.0" style="fill:#f0f8ff;stroke:black;stroke-width:1" width="79.2" filter="url(#shadow)" rx="4" y="120.0" ry="4" x="220.0"/><line style="stroke:dimgrey;stroke-width:1" y1="148.0" y2="148.0" x2="299.2" x1="220.0"/><text fill="black" class="diagram-class-title" y="140.0" x="259.6">[SampledData](#sampleddata)</text><rect height="28.0" style="fill:#f8ddf8;stroke:black;stroke-width:1" width="21.6" filter="url(#shadow)" rx="4" y="170.0" ry="4" x="0.0"/><line style="stroke:dimgrey;stroke-width:1" y1="198.0" y2="198.0" x2="21.6" x1="0.0"/><text fill="black" class="diagram-class-title" y="190.0" x="10.8">[Age](#age)</text><rect height="28.0" style="fill:#f8ddf8;stroke:black;stroke-width:1" width="57.6" filter="url(#shadow)" rx="4" y="170.0" ry="4" x="55.0"/><line style="stroke:dimgrey;stroke-width:1" y1="198.0" y2="198.0" x2="112.6" x1="55.0"/><text fill="black" class="diagram-class-title" y="190.0" x="83.8">[Distance](#distance)</text><rect height="28.0" style="fill:#f8ddf8;stroke:black;stroke-width:1" width="57.6" filter="url(#shadow)" rx="4" y="170.0" ry="4" x="140.0"/><line style="stroke:dimgrey;stroke-width:1" y1="198.0" y2="198.0" x2="197.6" x1="140.0"/><text fill="black" class="diagram-class-title" y="190.0" x="168.8">[Duration](#duration)</text><rect height="28.0" style="fill:#f8ddf8;stroke:black;stroke-width:1" width="36.0" filter="url(#shadow)" rx="4" y="170.0" ry="4" x="225.0"/><line style="stroke:dimgrey;stroke-width:1" y1="198.0" y2="198.0" x2="261.0" x1="225.0"/><text fill="black" class="diagram-class-title" y="190.0" x="243.0">[Count](#count)</text><rect height="28.0" style="fill:#f8ddf8;stroke:black;stroke-width:1" width="36.0" filter="url(#shadow)" rx="4" y="170.0" ry="4" x="300.0"/><line style="stroke:dimgrey;stroke-width:1" y1="198.0" y2="198.0" x2="336.0" x1="300.0"/><text fill="black" class="diagram-class-title" y="190.0" x="318.0">[Money](#money)</text><line style="stroke:navy;stroke-width:1" y1="73.02985074626865" y2="28.0" x2="303.84" x1="200.4"/><polygon transform="rotate(-23.52461868412063 200.4 73.02985074626865)" style="fill:white;stroke:navy;stroke-width:1" points="200.4,73.02985074626865 208.4,79.02985074626865 208.4,67.02985074626865 200.4,73.02985074626865"/><line style="stroke:navy;stroke-width:1" y1="79.47846889952152" y2="59.8133971291866" x2="310.0" x1="200.4"/><polygon transform="rotate(-10.172105852287535 200.4 79.47846889952152)" style="fill:white;stroke:navy;stroke-width:1" points="200.4,79.47846889952152 208.4,85.47846889952152 208.4,73.47846889952152 200.4,79.47846889952152"/><line style="stroke:navy;stroke-width:1" y1="85.52727272727272" y2="92.47272727272727" x2="315.0" x1="200.4"/><polygon transform="rotate(3.4682292589171513 200.4 85.52727272727272)" style="fill:white;stroke:navy;stroke-width:1" points="200.4,85.52727272727272 208.4,91.52727272727272 208.4,79.52727272727272 200.4,85.52727272727272"/><line style="stroke:navy;stroke-width:1" y1="90.70212765957447" y2="122.51063829787233" x2="320.0" x1="200.4"/><polygon transform="rotate(14.893472958841608 200.4 90.70212765957447)" style="fill:white;stroke:navy;stroke-width:1" points="200.4,90.70212765957447 208.4,96.70212765957447 208.4,84.70212765957447 200.4,90.70212765957447"/><line style="stroke:navy;stroke-width:1" y1="79.078125" y2="58.21875" x2="43.2" x1="150.0"/><polygon transform="rotate(-168.94854297333455 150.0 79.078125)" style="fill:white;stroke:navy;stroke-width:1" points="150.0,79.078125 158.0,85.078125 158.0,73.078125 150.0,79.078125"/><line style="stroke:navy;stroke-width:1" y1="98.0" y2="120.0" x2="170.59200000000004" x1="173.40800000000002"/><polygon transform="rotate(97.29419630854079 173.40800000000002 98.0)" style="fill:white;stroke:navy;stroke-width:1" points="173.40800000000002,98.0 181.40800000000002,104.0 181.40800000000002,92.0 173.40800000000002,98.0"/><line style="stroke:navy;stroke-width:1" y1="70.0" y2="28.0" x2="223.83999999999997" x1="187.35999999999999"/><polygon transform="rotate(-49.02335231903334 187.35999999999999 70.0)" style="fill:white;stroke:navy;stroke-width:1" points="187.35999999999999,70.0 195.35999999999999,76.0 195.35999999999999,64.0 187.35999999999999,70.0"/><line style="stroke:navy;stroke-width:1" y1="70.0" y2="28.0" x2="169.44" x1="173.76"/><polygon transform="rotate(-95.8726282810668 173.76 70.0)" style="fill:white;stroke:navy;stroke-width:1" points="173.76,70.0 181.76,76.0 181.76,64.0 173.76,70.0"/><line style="stroke:navy;stroke-width:1" y1="69.99999999999999" y2="28.0" x2="116.32" x1="160.47999999999996"/><polygon transform="rotate(-136.43608364184578 160.47999999999996 69.99999999999999)" style="fill:white;stroke:navy;stroke-width:1" points="160.47999999999996,69.99999999999999 168.47999999999996,75.99999999999999 168.47999999999996,63.999999999999986 160.47999999999996,69.99999999999999"/><line style="stroke:navy;stroke-width:1" y1="71.59493670886076" y2="22.860759493670884" x2="51.0" x1="150.0"/><polygon transform="rotate(-153.79061782922898 150.0 71.59493670886076)" style="fill:white;stroke:navy;stroke-width:1" points="150.0,71.59493670886076 158.0,77.59493670886076 158.0,65.59493670886076 150.0,71.59493670886076"/><line style="stroke:navy;stroke-width:1" y1="94.3960396039604" y2="120.0" x2="87.93600000000004" x1="150.0"/><polygon transform="rotate(157.5818325742615 150.0 94.3960396039604)" style="fill:white;stroke:navy;stroke-width:1" points="150.0,94.3960396039604 158.0,100.3960396039604 158.0,88.3960396039604 150.0,94.3960396039604"/><line style="stroke:navy;stroke-width:1" y1="85.640625" y2="92.59375" x2="43.2" x1="150.0"/><polygon transform="rotate(176.27506286658965 150.0 85.640625)" style="fill:white;stroke:navy;stroke-width:1" points="150.0,85.640625 158.0,91.640625 158.0,79.640625 150.0,85.640625"/><line style="stroke:navy;stroke-width:1" y1="98.0" y2="120.00000000000003" x2="235.96800000000007" x1="198.832"/><polygon transform="rotate(30.643224046543462 198.832 98.0)" style="fill:white;stroke:navy;stroke-width:1" points="198.832,98.0 206.832,104.0 206.832,92.0 198.832,98.0"/><line style="stroke:navy;stroke-width:1" y1="143.11392405063293" y2="180.58227848101268" x2="21.6" x1="140.0"/><polygon transform="rotate(162.43972794819933 140.0 143.11392405063293)" style="fill:white;stroke:navy;stroke-width:1" points="140.0,143.11392405063293 148.0,149.11392405063293 148.0,137.11392405063293 140.0,143.11392405063293"/><line style="stroke:navy;stroke-width:1" y1="148.0" y2="170.00000000000003" x2="107.5999999999999" x1="144.99999999999994"/><polygon transform="rotate(149.53445508054014 144.99999999999994 148.0)" style="fill:white;stroke:navy;stroke-width:1" points="144.99999999999994,148.0 152.99999999999994,154.0 152.99999999999994,142.0 144.99999999999994,148.0"/><line style="stroke:navy;stroke-width:1" y1="148.0" y2="170.00000000000003" x2="168.8" x1="168.8"/><polygon transform="rotate(90.0 168.8 148.0)" style="fill:white;stroke:navy;stroke-width:1" points="168.8,148.0 176.8,154.0 176.8,142.0 168.8,148.0"/><line style="stroke:navy;stroke-width:1" y1="148.0" y2="171.87061994609167" x2="225.0" x1="189.576"/><polygon transform="rotate(33.97423521213204 189.576 148.0)" style="fill:white;stroke:navy;stroke-width:1" points="189.576,148.0 197.576,154.0 197.576,142.0 189.576,148.0"/><line style="stroke:navy;stroke-width:1" y1="143.65147453083108" y2="177.96782841823057" x2="300.0" x1="197.6"/><polygon transform="rotate(18.52706414470336 197.6 143.65147453083108)" style="fill:white;stroke:navy;stroke-width:1" points="197.6,143.65147453083108 205.6,149.65147453083108 205.6,137.65147453083108 197.6,143.65147453083108"/></svg></td>
 </tr>
</table>

<a name="Primitive"/>
<a name="primitive"/>

### <span class="sectioncount">1.17.2.1<a name="1.17.2.1"> </a></span> Primitive Types

See also [Base Definition](datatypes.html#primitive), [Examples](datatypes-examples.html#primitive) and [Mappings](datatypes-mappings.html#primitive).

<a name="boolean"> </a>
<a name="integer"> </a>
<a name="string"> </a>
<a name="decimal"> </a>
<a name="uri"> </a>
<a name="base64Binary"> </a>
<a name="base64binary"> </a>
<a name="instant"> </a>
<a name="date"> </a>
<a name="dateTime"> </a>
<a name="datetime"> </a>
<a name="time"> </a>
<a name="patterns"/>
<a name="code"> </a>
<a name="oid"> </a>
<a name="uuid"> </a>
<a name="id"> </a>

_todo_

<a name="Attachment"/>
<a name="attachment"/>

### <span class="sectioncount">1.17.2.2<a name="1.17.2.2"> </a></span> Attachment

See also [Base Definition](datatypes.html#Attachment), [Examples](datatypes-examples.html#Attachment) and [Mappings](datatypes-mappings.html#Attachment).

<table class="dict">
  <tr><td colspan="2" class="structure"><a name="Attachment"> </a>**Attachment**</td></tr>
  <tr><td>Definition</td><td>

For referring to data content defined in other formats.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>1..1</td></tr>
  <tr><td>Requirements</td><td>

Many models need to include data defined in other specifications that is complex and opaque to the healthcare model. This includes documents, media recordings, structured data, etc.

</td></tr>
  <tr><td>Invariants</td><td>**Defined on this element**

**att-1**: It the Attachment has data, it SHALL have a contentType (xpath: not(exists(f:data)) or exists(f:contentType))</td></tr>
  <tr><td colspan="2" class="structure"><a name="Attachment.contentType"> </a>**Attachment.contentType**</td></tr>
  <tr><td>Definition</td><td>

Identifies the type of the data in the attachment and allows a method to be chosen to interpret or render the data. Includes mime type parameters such as charset where appropriate.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>0..1</td></tr>
  <tr><td>[Binding](terminologies.html)</td><td>MimeType: [Required](terminologies.html#required): [BCP 13 (RFCs 2045, 2046, 2047, 4288, 4289 and 2049)](http://www.rfc-editor.org/bcp/bcp13.txt) (The mime type of an attachment)</td></tr>
  <tr><td>[Type](datatypes.html)</td><td>[code](datatypes.html#code)</td></tr>
  <tr><td>Requirements</td><td>

Processors of the data need to be able to know how to interpret the data.

</td></tr>
  <tr><td colspan="2" class="structure"><a name="Attachment.language"> </a>**Attachment.language**</td></tr>
  <tr><td>Definition</td><td>

The human language of the content. The value can be any valid value according to BCP 47.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>0..1</td></tr>
  <tr><td>[Binding](terminologies.html)</td><td>Language: [Required](terminologies.html#required): [IETF language tag](http://tools.ietf.org/html/bcp47) (A human language)</td></tr>
  <tr><td>[Type](datatypes.html)</td><td>[code](datatypes.html#code)</td></tr>
  <tr><td>Requirements</td><td>

Users need to be able to choose between the languages in a set of attachments.

</td></tr>
  <tr><td colspan="2" class="structure"><a name="Attachment.data"> </a>**Attachment.data**</td></tr>
  <tr><td>Definition</td><td>

The actual data of the attachment - a sequence of bytes. In XML, represented using base64.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>0..1</td></tr>
  <tr><td>[Type](datatypes.html)</td><td>[base64Binary](datatypes.html#base64Binary)</td></tr>
  <tr><td>Requirements</td><td>

The data needs to able to be transmitted inline.

</td></tr>
  <tr><td>Comments</td><td>

The base64-encoded data SHALL be expressed in the same character set as the base resource XML or JSON.

</td></tr>
  <tr><td colspan="2" class="structure"><a name="Attachment.url"> </a>**Attachment.url**</td></tr>
  <tr><td>Definition</td><td>

An alternative location where the data can be accessed.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>0..1</td></tr>
  <tr><td>[Type](datatypes.html)</td><td>[uri](datatypes.html#uri)</td></tr>
  <tr><td>Requirements</td><td>

The data needs to be transmitted by reference.

</td></tr>
  <tr><td>Comments</td><td>

If both data and url are provided, the url SHALL point to the same content as the data contains. Urls may be relative references or may reference transient locations such as a wrapping envelope using cid: though this has ramifications for using signatures. Relative URLs are interpreted relative to the service url, like a resource reference, rather than relative to the resource itself. If a URL is provided, it SHALL resolve to actual data.

</td></tr>
  <tr><td colspan="2" class="structure"><a name="Attachment.size"> </a>**Attachment.size**</td></tr>
  <tr><td>Definition</td><td>

The number of bytes of data that make up this attachment.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>0..1</td></tr>
  <tr><td>[Type](datatypes.html)</td><td>[integer](datatypes.html#integer)</td></tr>
  <tr><td>Requirements</td><td>

Representing the size allows applications to determine whether they should fetch the content automatically in advance, or refuse to fetch it at all.

</td></tr>
  <tr><td>Comments</td><td>

The number of bytes is redundant if the data is provided as a base64binary, but is useful if the data is provided as a url reference.

</td></tr>
  <tr><td colspan="2" class="structure"><a name="Attachment.hash"> </a>**Attachment.hash**</td></tr>
  <tr><td>Definition</td><td>

The calculated hash of the data using SHA-1. Represented using base64.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>0..1</td></tr>
  <tr><td>[Type](datatypes.html)</td><td>[base64Binary](datatypes.html#base64Binary)</td></tr>
  <tr><td>Requirements</td><td>

Included so that applications can verify that the contents of a location have not changed and so that a signature of the content can implicitly sign the content of an image without having to include the data in the instance or reference the url in the signature.

</td></tr>
  <tr><td colspan="2" class="structure"><a name="Attachment.title"> </a>**Attachment.title**</td></tr>
  <tr><td>Definition</td><td>

A label or set of text to display in place of the data.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>0..1</td></tr>
  <tr><td>[Type](datatypes.html)</td><td>[string](datatypes.html#string)</td></tr>
  <tr><td>Requirements</td><td>

Applications need a label to display to a human user in place of the actual data if the data cannot be rendered or perceived by the viewer.

</td></tr>
  <tr><td colspan="2" class="structure"><a name="Attachment.creation"> </a>**Attachment.creation**</td></tr>
  <tr><td>Definition</td><td>

The date that the attachment was first created.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>0..1</td></tr>
  <tr><td>[Type](datatypes.html)</td><td>[dateTime](datatypes.html#dateTime)</td></tr>
  <tr><td>Requirements</td><td>

This is often tracked as an integrity issue for use of the attachment.

</td></tr>
</table>

<a name="Identifier"/>
<a name="identifier"/>

### <span class="sectioncount">1.17.2.3<a name="1.17.2.3"> </a></span> Identifier

See also [Base Definition](datatypes.html#identifier), [Examples](datatypes-examples.html#identifier) and [Mappings](datatypes-mappings.html#identifier).

<table class="dict">
  <tr><td colspan="2" class="structure"><a name="Identifier"> </a>**Identifier**</td></tr>
  <tr><td>Definition</td><td>

A technical identifier - identifies some entity uniquely and unambiguously.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>1..1</td></tr>
  <tr><td>Requirements</td><td>

Need to be able to identify things with confidence and be sure that the identification is not subject to misinterpretation.

</td></tr>
  <tr><td colspan="2" class="structure"><a name="Identifier.use"> </a>**Identifier.use**</td></tr>
  <tr><td>Definition</td><td>

The purpose of this identifier.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>0..1</td></tr>
  <tr><td>[Binding](terminologies.html)</td><td>IdentifierUse: [Required](terminologies.html#required): [http://hl7.org/fhir/identifier-use](identifier-use.html) (Identifies the purpose for this identifier, if known)</td></tr>
  <tr><td>[Type](datatypes.html)</td><td>[code](datatypes.html#code)</td></tr>
  <tr><td>[Is Modifier](conformance-rules.html#ismodifier)</td><td>true</td></tr>
  <tr><td>Requirements</td><td>

Allows the appropriate identifier for a particular context of use to be selected from among a set of identifiers.

</td></tr>
  <tr><td>Comments</td><td>

This is labeled as &quot;Is Modifier&quot; because applications should not mistake a temporary id for a permanent one. Applications can assume that an identifier is permanent unless it explicitly says that it is temporary.

</td></tr>
  <tr><td colspan="2" class="structure"><a name="Identifier.label"> </a>**Identifier.label**</td></tr>
  <tr><td>Definition</td><td>

A text string for the identifier that can be displayed to a human so they can recognize the identifier.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>0..1</td></tr>
  <tr><td>[Type](datatypes.html)</td><td>[string](datatypes.html#string)</td></tr>
  <tr><td>Requirements</td><td>

Allows humans to make use of identifiers when the identifier system is not known.

</td></tr>
  <tr><td colspan="2" class="structure"><a name="Identifier.system"> </a>**Identifier.system**</td></tr>
  <tr><td>Definition</td><td>

Establishes the namespace in which set of possible id values is unique.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>0..1</td></tr>
  <tr><td>[Type](datatypes.html)</td><td>[uri](datatypes.html#uri)</td></tr>
  <tr><td>Requirements</td><td>

There are many sequences of identifiers.  To perform matching, we need to know what sequence we're dealing with. The system identifies a particular sequence or set of unique identifiers.

</td></tr>
  <tr><td colspan="2" class="structure"><a name="Identifier.value"> </a>**Identifier.value**</td></tr>
  <tr><td>Definition</td><td>

The portion of the identifier typically displayed to the user and which is unique within the context of the system.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>0..1</td></tr>
  <tr><td>[Type](datatypes.html)</td><td>[string](datatypes.html#string)</td></tr>
  <tr><td>Comments</td><td>

If the value is a full URI, then the system SHALL be urn:ietf:rfc:3986.

</td></tr>
  <tr><td colspan="2" class="structure"><a name="Identifier.period"> </a>**Identifier.period**</td></tr>
  <tr><td>Definition</td><td>

Time period during which identifier is/was valid for use.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>0..1</td></tr>
  <tr><td>[Type](datatypes.html)</td><td>[Period](datatypes.html#Period)</td></tr>
  <tr><td colspan="2" class="structure"><a name="Identifier.assigner"> </a>**Identifier.assigner**</td></tr>
  <tr><td>Definition</td><td>

Organization that issued/manages the identifier.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>0..1</td></tr>
  <tr><td>[Type](datatypes.html)</td><td>[Reference](references.html#Reference)([Organization](organization.html))</td></tr>
  <tr><td>Comments</td><td>

The reference may be just a text description of the assigner.

</td></tr>
</table>

<a name="Coding"/>
<a name="coding"/>

### <span class="sectioncount">1.17.2.4<a name="1.17.2.4"> </a></span> Coding

See also [Base Definition](datatypes.html#Coding), [Examples](datatypes-examples.html#Coding) and [Mappings](datatypes-mappings.html#Coding).

<table class="dict">
  <tr><td colspan="2" class="structure"><a name="Coding"> </a>**Coding**</td></tr>
  <tr><td>Definition</td><td>

A reference to a code defined by a terminology system.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>1..1</td></tr>
  <tr><td>Requirements</td><td>

References to codes are very common in healthcare models.

</td></tr>
  <tr><td>Comments</td><td>

Codes may be defined very casually in enumerations or code lists, up to very formal definitions such as SNOMED CT - see the V3 Core Principles for more information.

</td></tr>
  <tr><td>Invariants</td><td>**Defined on this element**

**cod-1**: If a valueSet is provided, a system URI Is required (xpath: not (exists(f:valueSet) and exists(f:code)) or exists(f:system))</td></tr>
  <tr><td colspan="2" class="structure"><a name="Coding.system"> </a>**Coding.system**</td></tr>
  <tr><td>Definition</td><td>

The identification of the code system that defines the meaning of the symbol in the code.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>0..1</td></tr>
  <tr><td>[Type](datatypes.html)</td><td>[uri](datatypes.html#uri)</td></tr>
  <tr><td>Requirements</td><td>

Need to be unambiguous about the source of the definition of the symbol.

</td></tr>
  <tr><td>Comments</td><td>

The URI may be an OID (urn:oid:...) or a UUID (urn:uuid:...).  OIDs and UUIDs SHALL be references to the HL7 OID registry. Otherwise, the URI should come from HL7's list of FHIR defined special URIs or it should de-reference to some definition that establish the system clearly and unambiguously.

</td></tr>
  <tr><td colspan="2" class="structure"><a name="Coding.version"> </a>**Coding.version**</td></tr>
  <tr><td>Definition</td><td>

The version of the code system which was used when choosing this code. Note that a well-maintained code system does not need the version reported, because the meaning of codes is consistent across versions. However this cannot consistently be assured. and when the meaning is not guaranteed to be consistent, the version SHOULD be exchanged.

</td></tr>
  <tr><td>Note</td><td>This is a business versionId, not a resource identifier (see [discussion](resource.html#versions))</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>0..1</td></tr>
  <tr><td>[Type](datatypes.html)</td><td>[string](datatypes.html#string)</td></tr>
  <tr><td>Comments</td><td>

Where the terminology does not clearly define what string should be used to identify code system versions, the recommendation is to use the date (expressed in FHIR date format) on which that version was officially published as the version date.

</td></tr>
  <tr><td colspan="2" class="structure"><a name="Coding.code"> </a>**Coding.code**</td></tr>
  <tr><td>Definition</td><td>

A symbol in syntax defined by the system. The symbol may be a predefined code or an expression in a syntax defined by the coding system (e.g. post-coordination).

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>0..1</td></tr>
  <tr><td>[Type](datatypes.html)</td><td>[code](datatypes.html#code)</td></tr>
  <tr><td>Requirements</td><td>

Need to refer to a particular code in the system.

</td></tr>
  <tr><td colspan="2" class="structure"><a name="Coding.display"> </a>**Coding.display**</td></tr>
  <tr><td>Definition</td><td>

A representation of the meaning of the code in the system, following the rules of the system.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>0..1</td></tr>
  <tr><td>[Type](datatypes.html)</td><td>[string](datatypes.html#string)</td></tr>
  <tr><td>Requirements</td><td>

Need to be able to carry a human-readable meaning of the code for readers that do not know  the system.

</td></tr>
  <tr><td colspan="2" class="structure"><a name="Coding.primary"> </a>**Coding.primary**</td></tr>
  <tr><td>Definition</td><td>

Indicates that this code was chosen by a user directly - i.e. off a pick list of available items (codes or displays).

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>0..1</td></tr>
  <tr><td>[Type](datatypes.html)</td><td>[boolean](datatypes.html#boolean)</td></tr>
  <tr><td>Requirements</td><td>

This has been identified as a clinical safety criterium - that this exact code was chosen explicitly, rather than inferred by the system based on some rules or language processing.

</td></tr>
  <tr><td>Comments</td><td>

Amongst a set of alternatives, a directly chosen code is the most appropriate starting point for new translations.

</td></tr>
</table>

<a name="CodeableConcept"/>
<a name="codeableconcept"/>

### <span class="sectioncount">1.17.2.5<a name="1.17.2.5"> </a></span> CodeableConcept

See also [Base Definition](datatypes.html#CodeableConcept), [Examples](datatypes-examples.html#CodeableConcept) and [Mappings](datatypes-mappings.html#CodeableConcept).

<table class="dict">
  <tr><td colspan="2" class="structure"><a name="CodeableConcept"> </a>**CodeableConcept**</td></tr>
  <tr><td>Definition</td><td>

A concept that may be defined by a formal reference to a terminology or ontology or may be provided by text.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>1..1</td></tr>
  <tr><td>Requirements</td><td>

This is a common pattern in healthcare - a concept that may be defined by one or more codes from formal definitions including LOINC and SNOMED CT, and/or defined by the provision of text that captures a human sense of the concept.

</td></tr>
  <tr><td>Comments</td><td>

Not all terminology uses fit this general pattern. In some cases, models should not use CodeableConcept and use Coding directly and provide their own structure for managing text, codings, translations and the relationship between elements and pre- and post-coordination.

</td></tr>
  <tr><td>Invariants</td><td>**Defined on this element**

**ccc-2**: Only one coding in a set can be chosen directly by the user (xpath: count(f:coding[f:primary/@value='true'])&lt;=1)</td></tr>
  <tr><td colspan="2" class="structure"><a name="CodeableConcept.coding"> </a>**CodeableConcept.coding**</td></tr>
  <tr><td>Definition</td><td>

A reference to a code defined by a terminology system.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>0..*</td></tr>
  <tr><td>[Type](datatypes.html)</td><td>[Coding](datatypes.html#Coding)</td></tr>
  <tr><td>Requirements</td><td>

Allows for translations and alternate encodings within a code system.  Also supports communication of the same instance to systems requiring different encodings.

</td></tr>
  <tr><td>Comments</td><td>

Codes may be defined very casually in enumerations, or code lists, up to very formal definitions such as SNOMED CT - see the V3 Core Principles for more information.  Ordering of codings is undefined and SHALL not be used to infer meaning.

</td></tr>
  <tr><td colspan="2" class="structure"><a name="CodeableConcept.text"> </a>**CodeableConcept.text**</td></tr>
  <tr><td>Definition</td><td>

A human language representation of the concept as seen/selected/uttered by the user who entered the data and/or which represents the intended meaning of the user.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>0..1</td></tr>
  <tr><td>[Type](datatypes.html)</td><td>[string](datatypes.html#string)</td></tr>
  <tr><td>Requirements</td><td>

The codes from the terminologies do not always capture the correct meaning with all the nuances of the human using them, or sometimes there is no appropriate code at all. In these cases, the text is used to capture the full meaning of the source.

</td></tr>
  <tr><td>Comments</td><td>

Very often the text is the same as a displayName of one of the codings.

</td></tr>
</table>

<a name="Quantity"/>
<a name="quantity"/>
<a name="age"/>
<a name="distance"/>
<a name="duration"/>
<a name="count"/>
<a name="money"/>

### <span class="sectioncount">1.17.2.6<a name="1.17.2.6"> </a></span> Quantity

See also [Base Definition](datatypes.html#Quantity), [Examples](datatypes-examples.html#Quantity) and [Mappings](datatypes-mappings.html#Quantity).

<table class="dict">
  <tr><td colspan="2" class="structure"><a name="Quantity"> </a>**Quantity**</td></tr>
  <tr><td>Definition</td><td>

A measured amount (or an amount that can potentially be measured). Note that measured amounts include amounts that are not precisely quantified, including amounts involving arbitrary units and floating currencies.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>1..1</td></tr>
  <tr><td>Requirements</td><td>

Need to able to capture all sorts of measured values, even if the measured value are not precisely quantified. Values include exact measures such as 3.51g, customary units such as 3 tablets, and currencies such as $100.32USD.

</td></tr>
  <tr><td>Comments</td><td>

The context of use may frequently define what kind of quantity this is and therefore what kind of units can be used. The context of use may also restrict the values for the comparator.

</td></tr>
  <tr><td>Invariants</td><td>**Defined on this element**

**qty-3**: If a code for the units is present, the system SHALL also be present (xpath: not(exists(f:code)) or exists(f:system))</td></tr>
  <tr><td colspan="2" class="structure"><a name="Quantity.value"> </a>**Quantity.value**</td></tr>
  <tr><td>Definition</td><td>

The value of the measured amount. The value includes an implicit precision in the presentation of the value.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>0..1</td></tr>
  <tr><td>[Type](datatypes.html)</td><td>[decimal](datatypes.html#decimal)</td></tr>
  <tr><td>Requirements</td><td>

Precision is handled implicitly in almost all cases of measurement.

</td></tr>
  <tr><td>Comments</td><td>

The implicit precision in the value should always be honored. Monetary values have their own rules for handling precision (refer to standard accounting text books).

</td></tr>
  <tr><td colspan="2" class="structure"><a name="Quantity.comparator"> </a>**Quantity.comparator**</td></tr>
  <tr><td>Definition</td><td>

How the value should be understood and represented - whether the actual value is greater or less than the stated value due to measurement issues. E.g. if the comparator is &quot;&lt;&quot; , then the real value is &lt; stated value.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>0..1</td></tr>
  <tr><td>[Binding](terminologies.html)</td><td>QuantityComparator: [Required](terminologies.html#required): [http://hl7.org/fhir/quantity-comparator](quantity-comparator.html) (How the Quantity should be understood and represented)</td></tr>
  <tr><td>[Type](datatypes.html)</td><td>[code](datatypes.html#code)</td></tr>
  <tr><td>[Is Modifier](conformance-rules.html#ismodifier)</td><td>true</td></tr>
  <tr><td>Meaning if Missing</td><td>If there is no comparator, then there is no modification of the value</td></tr>
  <tr><td>Requirements</td><td>

Need a framework for handling measures where the value is &lt;5ug/L or &gt;400mg/L due to the limitations of measuring methodology.

</td></tr>
  <tr><td>Comments</td><td>

This is labeled as &quot;Is Modifier&quot; because the comparator modifies the interpretation of the value significantly. If there is no comparator, then there is no modification of the value.

</td></tr>
  <tr><td colspan="2" class="structure"><a name="Quantity.units"> </a>**Quantity.units**</td></tr>
  <tr><td>Definition</td><td>

A human-readable form of the units.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>0..1</td></tr>
  <tr><td>[Type](datatypes.html)</td><td>[string](datatypes.html#string)</td></tr>
  <tr><td>Requirements</td><td>

There are many representations for units and in many contexts, particular representations are fixed and required. I.e. mcg for micrograms.

</td></tr>
  <tr><td colspan="2" class="structure"><a name="Quantity.system"> </a>**Quantity.system**</td></tr>
  <tr><td>Definition</td><td>

The identification of the system that provides the coded form of the unit.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>0..1</td></tr>
  <tr><td>[Type](datatypes.html)</td><td>[uri](datatypes.html#uri)</td></tr>
  <tr><td>Requirements</td><td>

Need to know the system that defines the coded form of the unit.

</td></tr>
  <tr><td>Invariants</td><td>**Affect this element**

**qty-3**: If a code for the units is present, the system SHALL also be present (xpath: not(exists(f:code)) or exists(f:system))</td></tr>
  <tr><td colspan="2" class="structure"><a name="Quantity.code"> </a>**Quantity.code**</td></tr>
  <tr><td>Definition</td><td>

A computer processable form of the units in some unit representation system.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>0..1</td></tr>
  <tr><td>[Type](datatypes.html)</td><td>[code](datatypes.html#code)</td></tr>
  <tr><td>Requirements</td><td>

Need a computable form of the units that is fixed across all forms. UCUM provides this for quantities, but SNOMED CT provides many units of interest.

</td></tr>
  <tr><td>Comments</td><td>

The preferred system is UCUM, but SNOMED CT can also be used (for customary units) or ISO 4217 for currency.

The context of use may additionally require a code from a particular system.

</td></tr>
</table>

<a name="Range"/>
<a name="range"/>

### <span class="sectioncount">1.17.2.7<a name="1.17.2.7"> </a></span> Range

See also [Base Definition](datatypes.html#Range), [Examples](datatypes-examples.html#Range) and [Mappings](datatypes-mappings.html#Range).

<table class="dict">
  <tr><td colspan="2" class="structure"><a name="Range"> </a>**Range**</td></tr>
  <tr><td>Definition</td><td>

A set of ordered Quantities defined by a low and high limit.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>1..1</td></tr>
  <tr><td>Requirements</td><td>

Need to be able to specify ranges of values.

</td></tr>
  <tr><td>Comments</td><td>

The stated low and high value are assumed to have arbitrarily high precision when it comes to determining which values are in the range. I.e. 1.99 is not in the range 2 -&gt; 3.

</td></tr>
  <tr><td>Invariants</td><td>**Defined on this element**

**rng-2**: If present, low SHALL have a lower value than high (xpath: not(exists(f:low/f:value/@value)) or not(exists(f:high/f:value/@value)) or (number(f:low/f:value/@value) &lt;= number(f:high/f:value/@value)))
**rng-3**: Quantity values cannot have a comparator when used in a Range (xpath: not(exists(f:low/f:comparator) or exists(f:high/f:comparator)))</td></tr>
  <tr><td colspan="2" class="structure"><a name="Range.low"> </a>**Range.low**</td></tr>
  <tr><td>Definition</td><td>

The low limit. The boundary is inclusive.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>0..1</td></tr>
  <tr><td>[Type](datatypes.html)</td><td>[Quantity](datatypes.html#Quantity)</td></tr>
  <tr><td>Comments</td><td>

If the low element is missing, the low boundary is not known.

</td></tr>
  <tr><td>Invariants</td><td>**Affect this element**

**rng-2**: If present, low SHALL have a lower value than high (xpath: not(exists(f:low/f:value/@value)) or not(exists(f:high/f:value/@value)) or (number(f:low/f:value/@value) &lt;= number(f:high/f:value/@value)))
**rng-3**: Quantity values cannot have a comparator when used in a Range (xpath: not(exists(f:low/f:comparator) or exists(f:high/f:comparator)))</td></tr>
  <tr><td colspan="2" class="structure"><a name="Range.high"> </a>**Range.high**</td></tr>
  <tr><td>Definition</td><td>

The high limit. The boundary is inclusive.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>0..1</td></tr>
  <tr><td>[Type](datatypes.html)</td><td>[Quantity](datatypes.html#Quantity)</td></tr>
  <tr><td>Comments</td><td>

If the high element is missing, the high boundary is not known.

</td></tr>
  <tr><td>Invariants</td><td>**Affect this element**

**rng-2**: If present, low SHALL have a lower value than high (xpath: not(exists(f:low/f:value/@value)) or not(exists(f:high/f:value/@value)) or (number(f:low/f:value/@value) &lt;= number(f:high/f:value/@value)))
**rng-3**: Quantity values cannot have a comparator when used in a Range (xpath: not(exists(f:low/f:comparator) or exists(f:high/f:comparator)))</td></tr>
</table>

<a name="Ratio"/>
<a name="ratio"/>

### <span class="sectioncount">1.17.2.8<a name="1.17.2.8"> </a></span> Ratio

See also [Base Definition](datatypes.html#Ratio), [Examples](datatypes-examples.html#Ratio) and [Mappings](datatypes-mappings.html#Ratio).

<table class="dict">
  <tr><td colspan="2" class="structure"><a name="Ratio"> </a>**Ratio**</td></tr>
  <tr><td>Definition</td><td>

A relationship of two Quantity values - expressed as a numerator and a denominator.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>1..1</td></tr>
  <tr><td>Requirements</td><td>

Need to able to capture ratios for some measurements (titers) and some rates (costs).

</td></tr>
  <tr><td>Invariants</td><td>**Defined on this element**

**rat-1**: numerator and denominator SHALL both be present, or both be absent. If both are absent, there SHALL be some extension present (xpath: (count(f:numerator) = count(f:denominator)) and ((count(f:numerator) &gt; 0) or (count(f:extension) &gt; 0)))</td></tr>
  <tr><td colspan="2" class="structure"><a name="Ratio.numerator"> </a>**Ratio.numerator**</td></tr>
  <tr><td>Definition</td><td>

The value of the numerator.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>0..1</td></tr>
  <tr><td>[Type](datatypes.html)</td><td>[Quantity](datatypes.html#Quantity)</td></tr>
  <tr><td colspan="2" class="structure"><a name="Ratio.denominator"> </a>**Ratio.denominator**</td></tr>
  <tr><td>Definition</td><td>

The value of the denominator.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>0..1</td></tr>
  <tr><td>[Type](datatypes.html)</td><td>[Quantity](datatypes.html#Quantity)</td></tr>
</table>

<a name="Period"/>
<a name="period"/>

### <span class="sectioncount">1.17.2.9<a name="1.17.2.9"> </a></span> Period

See also [Base Definition](datatypes.html#Period), [Examples](datatypes-examples.html#Period) and [Mappings](datatypes-mappings.html#Period).

<table class="dict">
  <tr><td colspan="2" class="structure"><a name="Period"> </a>**Period**</td></tr>
  <tr><td>Definition</td><td>

A time period defined by a start and end date and optionally time.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>1..1</td></tr>
  <tr><td>Comments</td><td>

This is not a duration - that's a measure of time (a separate type), but a duration that occurs at a fixed value of time. A Period specifies a range of time; the context of use will specify whether the entire range applies (e.g. &quot;the patient was an inpatient of the hospital for this time range&quot;) or one value from the range applies (e.g. &quot;give to the patient between these two times&quot;). If a duration might be required, specify the type as Interval|Duration.

</td></tr>
  <tr><td>Invariants</td><td>**Defined on this element**

**per-1**: If present, start SHALL have a lower value than end (xpath: not(exists(f:start)) or not(exists(f:end)) or (f:start/@value &lt;= f:end/@value))</td></tr>
  <tr><td colspan="2" class="structure"><a name="Period.start"> </a>**Period.start**</td></tr>
  <tr><td>Definition</td><td>

The start of the period. The boundary is inclusive.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>0..1</td></tr>
  <tr><td>[Type](datatypes.html)</td><td>[dateTime](datatypes.html#dateTime)</td></tr>
  <tr><td>Comments</td><td>

If the low element is missing, the meaning is that the low boundary is not known.

</td></tr>
  <tr><td>Invariants</td><td>**Affect this element**

**per-1**: If present, start SHALL have a lower value than end (xpath: not(exists(f:start)) or not(exists(f:end)) or (f:start/@value &lt;= f:end/@value))</td></tr>
  <tr><td colspan="2" class="structure"><a name="Period.end"> </a>**Period.end**</td></tr>
  <tr><td>Definition</td><td>

The end of the period. If the end of the period is missing, it means that the period is ongoing.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>0..1</td></tr>
  <tr><td>[Type](datatypes.html)</td><td>[dateTime](datatypes.html#dateTime)</td></tr>
  <tr><td>Meaning if Missing</td><td>If the end of the period is missing, it means that the period is ongoing</td></tr>
  <tr><td>Comments</td><td>

The high value includes any matching date/time. i.e. 2012-02-03T10:00:00 is in a period that has a end value of 2012-02-03.

</td></tr>
  <tr><td>Invariants</td><td>**Affect this element**

**per-1**: If present, start SHALL have a lower value than end (xpath: not(exists(f:start)) or not(exists(f:end)) or (f:start/@value &lt;= f:end/@value))</td></tr>
</table>

<a name="SampledData"/>
<a name="sampleddata"/>

### <span class="sectioncount">1.17.2.10<a name="1.17.2.10"> </a></span> SampledData

See also [Base Definition](datatypes.html#SampledData), [Examples](datatypes-examples.html#SampledData) and [Mappings](datatypes-mappings.html#SampledData).

<table class="dict">
  <tr><td colspan="2" class="structure"><a name="SampledData"> </a>**SampledData**</td></tr>
  <tr><td>Definition</td><td>

A series of measurements taken by a device, with upper and lower limits. There may be more than one dimension in the data.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>1..1</td></tr>
  <tr><td>Requirements</td><td>

There is a need for a concise way to handle the data produced by devices that sample a physical state at a high frequency.

</td></tr>
  <tr><td>Comments</td><td>

The data is not interpretable without at least origin, period, and dimensions, but these are optional to allow a separation between the template of measurement and the actual measurement, such as between DeviceCapabilities and DeviceLog.

</td></tr>
  <tr><td colspan="2" class="structure"><a name="SampledData.origin"> </a>**SampledData.origin**</td></tr>
  <tr><td>Definition</td><td>

The base quantity that a measured value of zero represents. In addition, this provides the units of the entire measurement series.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>1..1</td></tr>
  <tr><td>[Type](datatypes.html)</td><td>[Quantity](datatypes.html#Quantity)</td></tr>
  <tr><td colspan="2" class="structure"><a name="SampledData.period"> </a>**SampledData.period**</td></tr>
  <tr><td>Definition</td><td>

The length of time between sampling times, measured in milliseconds.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>1..1</td></tr>
  <tr><td>[Type](datatypes.html)</td><td>[decimal](datatypes.html#decimal)</td></tr>
  <tr><td>Comments</td><td>

This is usually a whole number.

</td></tr>
  <tr><td colspan="2" class="structure"><a name="SampledData.factor"> </a>**SampledData.factor**</td></tr>
  <tr><td>Definition</td><td>

A correction factor that is applied to the sampled data points before they are added to the origin.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>0..1</td></tr>
  <tr><td>[Type](datatypes.html)</td><td>[decimal](datatypes.html#decimal)</td></tr>
  <tr><td>Default Value</td><td>1</td></tr>
  <tr><td colspan="2" class="structure"><a name="SampledData.lowerLimit"> </a>**SampledData.lowerLimit**</td></tr>
  <tr><td>Definition</td><td>

The lower limit of detection of the measured points. This is needed if any of the data points have the value &quot;L&quot; (lower than detection limit).

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>0..1</td></tr>
  <tr><td>[Type](datatypes.html)</td><td>[decimal](datatypes.html#decimal)</td></tr>
  <tr><td colspan="2" class="structure"><a name="SampledData.upperLimit"> </a>**SampledData.upperLimit**</td></tr>
  <tr><td>Definition</td><td>

The upper limit of detection of the measured points. This is needed if any of the data points have the value &quot;U&quot; (higher than detection limit).

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>0..1</td></tr>
  <tr><td>[Type](datatypes.html)</td><td>[decimal](datatypes.html#decimal)</td></tr>
  <tr><td colspan="2" class="structure"><a name="SampledData.dimensions"> </a>**SampledData.dimensions**</td></tr>
  <tr><td>Definition</td><td>

The number of sample points at each time point. If this value is greater than one, then the dimensions will be interlaced - all the sample points for a point in time will be recorded at once.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>1..1</td></tr>
  <tr><td>[Type](datatypes.html)</td><td>[integer](datatypes.html#integer)</td></tr>
  <tr><td>Comments</td><td>

If there is more than one dimension, the code for the type of data will define the meaning of the dimensions (typically ECG data).

</td></tr>
  <tr><td colspan="2" class="structure"><a name="SampledData.data"> </a>**SampledData.data**</td></tr>
  <tr><td>Definition</td><td>

A series of data points which are decimal values separated by a single space (character u20). The special values &quot;E&quot; (error), &quot;L&quot; (below detection limit) and &quot;U&quot; (above detection limit) can also be used in place of a decimal value.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>1..1</td></tr>
  <tr><td>[Type](datatypes.html)</td><td>[string](datatypes.html#string)</td></tr>
</table>

<a name="HumanName"/>
<a name="humanname"/>

### <span class="sectioncount">1.17.2.11<a name="1.17.2.11"> </a></span> HumanName

See also [Base Definition](datatypes.html#HumanName), [Examples](datatypes-examples.html#HumanName) and [Mappings](datatypes-mappings.html#HumanName).

<table class="dict">
  <tr><td colspan="2" class="structure"><a name="HumanName"> </a>**HumanName**</td></tr>
  <tr><td>Definition</td><td>

A human's name with the ability to identify parts and usage.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>1..1</td></tr>
  <tr><td>Requirements</td><td>

Need to be able to record names, along with notes about their use.

</td></tr>
  <tr><td>Comments</td><td>

Names may be changed, or repudiated, or people may have different names in different contexts. Names may be divided into parts of different type that have variable significance depending on context, though the division into parts does not always matter. With personal names, the different parts may or may not be imbued with some implicit meaning; various cultures associate different importance with the name parts and the degree to which systems must care about name parts around the world varies widely.

</td></tr>
  <tr><td colspan="2" class="structure"><a name="HumanName.use"> </a>**HumanName.use**</td></tr>
  <tr><td>Definition</td><td>

Identifies the purpose for this name.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>0..1</td></tr>
  <tr><td>[Binding](terminologies.html)</td><td>NameUse: [Required](terminologies.html#required): [http://hl7.org/fhir/name-use](name-use.html) (The use of a human name)</td></tr>
  <tr><td>[Type](datatypes.html)</td><td>[code](datatypes.html#code)</td></tr>
  <tr><td>[Is Modifier](conformance-rules.html#ismodifier)</td><td>true</td></tr>
  <tr><td>Requirements</td><td>

Allows the appropriate name for a particular context of use to be selected from among a set of names.

</td></tr>
  <tr><td>Comments</td><td>

This is labeled as &quot;Is Modifier&quot; because applications should not mistake a temporary or old name etc for a current/permanent one. Applications can assume that a name is current unless it explicitly says that it is temporary or old.

</td></tr>
  <tr><td colspan="2" class="structure"><a name="HumanName.text"> </a>**HumanName.text**</td></tr>
  <tr><td>Definition</td><td>

A full text representation of the name.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>0..1</td></tr>
  <tr><td>[Type](datatypes.html)</td><td>[string](datatypes.html#string)</td></tr>
  <tr><td>Requirements</td><td>

A renderable, unencoded form.

</td></tr>
  <tr><td>Comments</td><td>

Can provide both a text representation and structured parts.

</td></tr>
  <tr><td colspan="2" class="structure"><a name="HumanName.family"> </a>**HumanName.family**</td></tr>
  <tr><td>Definition</td><td>

The part of a name that links to the genealogy. In some cultures (e.g. Eritrea) the family name of a son is the first name of his father.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>0..*</td></tr>
  <tr><td>[Type](datatypes.html)</td><td>[string](datatypes.html#string)</td></tr>
  <tr><td title="Other names by which this resource/element may be known">Alternate Names</td><td>surname</td></tr>
  <tr><td>Comments</td><td>

For family name, hyphenated names such as &quot;Smith-Jones&quot; are a single name, but names with spaces such as &quot;Smith Jones&quot; are broken into multiple parts.

</td></tr>
  <tr><td colspan="2" class="structure"><a name="HumanName.given"> </a>**HumanName.given**</td></tr>
  <tr><td>Definition</td><td>

Given name.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>0..*</td></tr>
  <tr><td>[Type](datatypes.html)</td><td>[string](datatypes.html#string)</td></tr>
  <tr><td title="Other names by which this resource/element may be known">Alternate Names</td><td>first name; middle name</td></tr>
  <tr><td>Comments</td><td>

If only initials are recorded, they may be used in place of the full name.  Not called &quot;first name&quot; since given names do not always come first.

</td></tr>
  <tr><td colspan="2" class="structure"><a name="HumanName.prefix"> </a>**HumanName.prefix**</td></tr>
  <tr><td>Definition</td><td>

Part of the name that is acquired as a title due to academic, legal, employment or nobility status, etc. and that appears at the start of the name.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>0..*</td></tr>
  <tr><td>[Type](datatypes.html)</td><td>[string](datatypes.html#string)</td></tr>
  <tr><td colspan="2" class="structure"><a name="HumanName.suffix"> </a>**HumanName.suffix**</td></tr>
  <tr><td>Definition</td><td>

Part of the name that is acquired as a title due to academic, legal, employment or nobility status, etc. and that appears at the end of the name.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>0..*</td></tr>
  <tr><td>[Type](datatypes.html)</td><td>[string](datatypes.html#string)</td></tr>
  <tr><td colspan="2" class="structure"><a name="HumanName.period"> </a>**HumanName.period**</td></tr>
  <tr><td>Definition</td><td>

Indicates the period of time when this name was valid for the named person.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>0..1</td></tr>
  <tr><td>[Type](datatypes.html)</td><td>[Period](datatypes.html#Period)</td></tr>
  <tr><td>Requirements</td><td>

Allows names to be placed in historical context.

</td></tr>
</table>

<a name="Address"/>
<a name="address"/>

### <span class="sectioncount">1.17.2.12<a name="1.17.2.12"> </a></span> Address

See also [Base Definition](datatypes.html#Address), [Examples](datatypes-examples.html#Address) and [Mappings](datatypes-mappings.html#Address).

<table class="dict">
  <tr><td colspan="2" class="structure"><a name="Address"> </a>**Address**</td></tr>
  <tr><td>Definition</td><td>

There is a variety of postal address formats defined around the world. This format defines a superset that is the basis for all addresses around the world.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>1..1</td></tr>
  <tr><td>Requirements</td><td>

Need to be able to record postal addresses, along with notes about their use.

</td></tr>
  <tr><td>Comments</td><td>

Note: address is for postal addresses, not physical locations.

</td></tr>
  <tr><td colspan="2" class="structure"><a name="Address.use"> </a>**Address.use**</td></tr>
  <tr><td>Definition</td><td>

The purpose of this address.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>0..1</td></tr>
  <tr><td>[Binding](terminologies.html)</td><td>AddressUse: [Required](terminologies.html#required): [http://hl7.org/fhir/address-use](address-use.html) (The use of an address)</td></tr>
  <tr><td>[Type](datatypes.html)</td><td>[code](datatypes.html#code)</td></tr>
  <tr><td>[Is Modifier](conformance-rules.html#ismodifier)</td><td>true</td></tr>
  <tr><td>Requirements</td><td>

Allows an appropriate address to be chosen from a list of many.

</td></tr>
  <tr><td>Comments</td><td>

This is labeled as &quot;Is Modifier&quot; because applications should not mistake a temporary or old address etc for a current/permanent one. Applications can assume that an address is current unless it explicitly says that it is temporary or old.

</td></tr>
  <tr><td colspan="2" class="structure"><a name="Address.text"> </a>**Address.text**</td></tr>
  <tr><td>Definition</td><td>

A full text representation of the address.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>0..1</td></tr>
  <tr><td>[Type](datatypes.html)</td><td>[string](datatypes.html#string)</td></tr>
  <tr><td>Requirements</td><td>

A renderable, unencoded form.

</td></tr>
  <tr><td>Comments</td><td>

Can provide both a text representation and parts.

</td></tr>
  <tr><td colspan="2" class="structure"><a name="Address.line"> </a>**Address.line**</td></tr>
  <tr><td>Definition</td><td>

This component contains the house number, apartment number, street name, street direction,
P.O. Box number, delivery hints, and similar address information.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>0..*</td></tr>
  <tr><td>[Type](datatypes.html)</td><td>[string](datatypes.html#string)</td></tr>
  <tr><td>Requirements</td><td>

home | work | temp | old - purpose of this address.

</td></tr>
  <tr><td colspan="2" class="structure"><a name="Address.city"> </a>**Address.city**</td></tr>
  <tr><td>Definition</td><td>

The name of the city, town, village or other community or delivery center.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>0..1</td></tr>
  <tr><td>[Type](datatypes.html)</td><td>[string](datatypes.html#string)</td></tr>
  <tr><td title="Other names by which this resource/element may be known">Alternate Names</td><td>Muncipality</td></tr>
  <tr><td colspan="2" class="structure"><a name="Address.state"> </a>**Address.state**</td></tr>
  <tr><td>Definition</td><td>

Sub-unit of a country with limited sovereignty in a federally organized country. A code may be used if codes are in common use (i.e. US 2 letter state codes).

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>0..1</td></tr>
  <tr><td>[Type](datatypes.html)</td><td>[string](datatypes.html#string)</td></tr>
  <tr><td title="Other names by which this resource/element may be known">Alternate Names</td><td>Province; Territory</td></tr>
  <tr><td colspan="2" class="structure"><a name="Address.postalCode"> </a>**Address.postalCode**</td></tr>
  <tr><td>Definition</td><td>

A postal code designating a region defined by the postal service.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>0..1</td></tr>
  <tr><td>[Type](datatypes.html)</td><td>[string](datatypes.html#string)</td></tr>
  <tr><td title="Other names by which this resource/element may be known">Alternate Names</td><td>Zip</td></tr>
  <tr><td colspan="2" class="structure"><a name="Address.country"> </a>**Address.country**</td></tr>
  <tr><td>Definition</td><td>

Country - a nation as commonly understood or generally accepted.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>0..1</td></tr>
  <tr><td>[Type](datatypes.html)</td><td>[string](datatypes.html#string)</td></tr>
  <tr><td>Comments</td><td>

ISO 3166 3 letter codes can be used in place of a full country name.

</td></tr>
  <tr><td colspan="2" class="structure"><a name="Address.period"> </a>**Address.period**</td></tr>
  <tr><td>Definition</td><td>

Time period when address was/is in use.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>0..1</td></tr>
  <tr><td>[Type](datatypes.html)</td><td>[Period](datatypes.html#Period)</td></tr>
  <tr><td>Requirements</td><td>

Allows addresses to be placed in historical context.

</td></tr>
</table>

<a name="ContactPoint"/>
<a name="contactpoint"/>

### <span class="sectioncount">1.17.2.13<a name="1.17.2.13"> </a></span> ContactPoint

See also [Base Definition](datatypes.html#ContactPoint), [Examples](datatypes-examples.html#ContactPoint) and [Mappings](datatypes-mappings.html#ContactPoint).

<table class="dict">
  <tr><td colspan="2" class="structure"><a name="ContactPoint"> </a>**ContactPoint**</td></tr>
  <tr><td>Definition</td><td>

Details for All kinds of technology mediated contact points for a person or organization, including telephone, email, etc.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>1..1</td></tr>
  <tr><td>Requirements</td><td>

Need to track phone, fax, mobile, sms numbers, email addresses, twitter tags, etc.

</td></tr>
  <tr><td>Invariants</td><td>**Defined on this element**

**cpt-2**: A system is required if a value is provided. (xpath: not(exists(f:value)) or exists(f:system))</td></tr>
  <tr><td colspan="2" class="structure"><a name="ContactPoint.system"> </a>**ContactPoint.system**</td></tr>
  <tr><td>Definition</td><td>

Telecommunications form for contact point - what communications system is required to make use of the contact.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>0..1</td></tr>
  <tr><td>[Binding](terminologies.html)</td><td>ContactPointSystem: [Required](terminologies.html#required): [http://hl7.org/fhir/contact-point-system](contact-point-system.html) (Telecommunications form for contact point)</td></tr>
  <tr><td>[Type](datatypes.html)</td><td>[code](datatypes.html#code)</td></tr>
  <tr><td>Invariants</td><td>**Affect this element**

**cpt-2**: A system is required if a value is provided. (xpath: not(exists(f:value)) or exists(f:system))</td></tr>
  <tr><td colspan="2" class="structure"><a name="ContactPoint.value"> </a>**ContactPoint.value**</td></tr>
  <tr><td>Definition</td><td>

The actual contact point details, in a form that is meaningful to the designated communication system (i.e. phone number or email address).

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>0..1</td></tr>
  <tr><td>[Type](datatypes.html)</td><td>[string](datatypes.html#string)</td></tr>
  <tr><td>Requirements</td><td>

Need to support legacy numbers that are not in a tightly controlled format.

</td></tr>
  <tr><td>Comments</td><td>

Additional out of band data such as extensions, or notes about use of the contact are sometimes included in the value.

</td></tr>
  <tr><td colspan="2" class="structure"><a name="ContactPoint.use"> </a>**ContactPoint.use**</td></tr>
  <tr><td>Definition</td><td>

Identifies the purpose for the contact point.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>0..1</td></tr>
  <tr><td>[Binding](terminologies.html)</td><td>ContactPointUse: [Required](terminologies.html#required): [http://hl7.org/fhir/contact-point-use](contact-point-use.html) (Use of contact point)</td></tr>
  <tr><td>[Type](datatypes.html)</td><td>[code](datatypes.html#code)</td></tr>
  <tr><td>[Is Modifier](conformance-rules.html#ismodifier)</td><td>true</td></tr>
  <tr><td>Requirements</td><td>

Need to track the way a person uses this contact, so a user can choose which is appropriate for their purpose.

</td></tr>
  <tr><td>Comments</td><td>

This is labeled as &quot;Is Modifier&quot; because applications should not mistake a temporary or old contact etc for a current/permanent one. Applications can assume that a contact is current unless it explicitly says that it is temporary or old.

</td></tr>
  <tr><td colspan="2" class="structure"><a name="ContactPoint.period"> </a>**ContactPoint.period**</td></tr>
  <tr><td>Definition</td><td>

Time period when the contact point was/is in use.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>0..1</td></tr>
  <tr><td>[Type](datatypes.html)</td><td>[Period](datatypes.html#Period)</td></tr>
</table>

<a name="Timing"/>
<a name="timing"/>

### <span class="sectioncount">1.17.2.14<a name="1.17.2.14"> </a></span> Timing

See also [Base Definition](datatypes.html#Timing), [Examples](datatypes-examples.html#Timing) and [Mappings](datatypes-mappings.html#Timing).

<table class="dict">
  <tr><td colspan="2" class="structure"><a name="Timing"> </a>**Timing**</td></tr>
  <tr><td>Definition</td><td>

Specifies an event that may occur multiple times. Timing schedules are used to record when things are expected or requested to occur.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>1..1</td></tr>
  <tr><td>Requirements</td><td>

Need to able to track proposed timing schedules. There are several different ways to do this: one or more specified times, a simple rules like three times a day, or  before/after meals.

</td></tr>
  <tr><td>Comments</td><td>

A timing schedule can be either a list of events - intervals on which the event occurs, or a single event with repeating criteria or just repeating criteria with no actual event.

</td></tr>
  <tr><td>Invariants</td><td>**Defined on this element**

**tim-1**: There can only be a repeat element if there is none or one event (xpath: not(exists(f:repeat)) or count(f:event) &lt; 2)</td></tr>
  <tr><td colspan="2" class="structure"><a name="Timing.event"> </a>**Timing.event**</td></tr>
  <tr><td>Definition</td><td>

Identifies specific time periods when the event should occur.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>0..*</td></tr>
  <tr><td>[Type](datatypes.html)</td><td>[Period](datatypes.html#Period)</td></tr>
  <tr><td>Requirements</td><td>

Some schedules are just explicit lists of times.

</td></tr>
  <tr><td colspan="2" class="structure"><a name="Timing.repeat"> </a>**Timing.repeat**</td></tr>
  <tr><td>Definition</td><td>

Identifies a repeating pattern to the intended time periods.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>0..1</td></tr>
  <tr><td>Requirements</td><td>

Many timing schedules are determined by regular repetitions.

</td></tr>
  <tr><td>Comments</td><td>

If present, the Timing.event indicates the time of the first occurrence.

</td></tr>
  <tr><td>Invariants</td><td>**Defined on this element**

**tim-2**: Either frequency or when SHALL be present, but not both (xpath: exists(f:frequency) != exists(f:when))
**tim-3**: At most, only one of count or end can be present (xpath: not(exists(f:count) and exists(f:end)))
**Affect this element**

**tim-1**: There can only be a repeat element if there is none or one event (xpath: not(exists(f:repeat)) or count(f:event) &lt; 2)</td></tr>
  <tr><td colspan="2" class="structure"><a name="Timing.repeat.frequency"> </a>**Timing.repeat.frequency**</td></tr>
  <tr><td>Definition</td><td>

Indicates how often the event should occur.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>0..1</td></tr>
  <tr><td>[Type](datatypes.html)</td><td>[integer](datatypes.html#integer)</td></tr>
  <tr><td>Invariants</td><td>**Affect this element**

**tim-2**: Either frequency or when SHALL be present, but not both (xpath: exists(f:frequency) != exists(f:when))</td></tr>
  <tr><td colspan="2" class="structure"><a name="Timing.repeat.when"> </a>**Timing.repeat.when**</td></tr>
  <tr><td>Definition</td><td>

Identifies the occurrence of daily life that determines timing.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>0..1</td></tr>
  <tr><td>[Binding](terminologies.html)</td><td>EventTiming: [Required](terminologies.html#required): [http://hl7.org/fhir/event-timing](event-timing.html) (Real world event that the schedule relates to)</td></tr>
  <tr><td>[Type](datatypes.html)</td><td>[code](datatypes.html#code)</td></tr>
  <tr><td>Requirements</td><td>

Timings are frequently determined by occurrences such as waking, eating and sleep.

</td></tr>
  <tr><td>Invariants</td><td>**Affect this element**

**tim-2**: Either frequency or when SHALL be present, but not both (xpath: exists(f:frequency) != exists(f:when))</td></tr>
  <tr><td colspan="2" class="structure"><a name="Timing.repeat.duration"> </a>**Timing.repeat.duration**</td></tr>
  <tr><td>Definition</td><td>

How long each repetition should last.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>1..1</td></tr>
  <tr><td>[Type](datatypes.html)</td><td>[decimal](datatypes.html#decimal)</td></tr>
  <tr><td>Requirements</td><td>

Some activities are not instantaneous and need to be maintained for a period of time.

</td></tr>
  <tr><td>Invariants</td><td>**Defined on this element**

**tim-4**: duration SHALL be a non-negative value (xpath: @value &gt;= 0 or not(@value))
**Affect this element**

**tim-4**: duration SHALL be a non-negative value (xpath: @value &gt;= 0 or not(@value))</td></tr>
  <tr><td colspan="2" class="structure"><a name="Timing.repeat.units"> </a>**Timing.repeat.units**</td></tr>
  <tr><td>Definition</td><td>

The units of time for the duration.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>1..1</td></tr>
  <tr><td>[Binding](terminologies.html)</td><td>UnitsOfTime: [Required](terminologies.html#required): [http://hl7.org/fhir/units-of-time](units-of-time.html) (A unit of time (units from UCUM))</td></tr>
  <tr><td>[Type](datatypes.html)</td><td>[code](datatypes.html#code)</td></tr>
  <tr><td colspan="2" class="structure"><a name="Timing.repeat.count"> </a>**Timing.repeat.count**</td></tr>
  <tr><td>Definition</td><td>

A total count of the desired number of repetitions.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>0..1</td></tr>
  <tr><td>[Type](datatypes.html)</td><td>[integer](datatypes.html#integer)</td></tr>
  <tr><td>Requirements</td><td>

Repetitions may be limited by end time or total occurrences.

</td></tr>
  <tr><td>Comments</td><td>

An end need not be specified.

</td></tr>
  <tr><td>Invariants</td><td>**Affect this element**

**tim-3**: At most, only one of count or end can be present (xpath: not(exists(f:count) and exists(f:end)))</td></tr>
  <tr><td colspan="2" class="structure"><a name="Timing.repeat.end"> </a>**Timing.repeat.end**</td></tr>
  <tr><td>Definition</td><td>

When to stop repeating the timing schedule.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>0..1</td></tr>
  <tr><td>[Type](datatypes.html)</td><td>[dateTime](datatypes.html#dateTime)</td></tr>
  <tr><td>Requirements</td><td>

Repetitions may be limited by end time or total occurrences.

</td></tr>
  <tr><td>Comments</td><td>

An end need not be specified.

</td></tr>
  <tr><td>Invariants</td><td>**Affect this element**

**tim-3**: At most, only one of count or end can be present (xpath: not(exists(f:count) and exists(f:end)))</td></tr>
</table>

<a name="Signature"/>
<a name="timing"/>

### <span class="sectioncount">1.17.2.15<a name="1.17.2.15"> </a></span> Signature

See also [Base Definition](datatypes.html#Signature), [Examples](datatypes-examples.html#Signature) and [Mappings](datatypes-mappings.html#Signature).

<table class="dict">
  <tr><td colspan="2" class="structure"><a name="Signature"> </a>**Signature**</td></tr>
  <tr><td>Definition</td><td>

An XML digital signature along with supporting context.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>1..1</td></tr>
  <tr><td>Requirements</td><td>

There are a number of places where content must be signed in healthcare.

</td></tr>
  <tr><td>Comments</td><td>

The elements of the Signature Resource are for ease of access of these elements. The non-repudiation proof comes from the XML-Signature  validation, which includes validation of the referenced objects (e.g., Resources) (a.k.a., Content) in the XML-Signature Detached form.

</td></tr>
  <tr><td colspan="2" class="structure"><a name="Signature.type"> </a>**Signature.type**</td></tr>
  <tr><td>Definition</td><td>

An indication of the reason that the entity signed this document. This may be explicitly included as part of the signature information and can be used when determining accountability for various actions concerning the document.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>1..*</td></tr>
  <tr><td>[Binding](terminologies.html)</td><td>SignatureType: [Preferred](terminologies.html#preferred): [See http://hl7.org/fhir/vs/signature-type](valueset-signature-type.html) (An indication of the reason that an entity signed the object)</td></tr>
  <tr><td>[Type](datatypes.html)</td><td>[Coding](datatypes.html#Coding)</td></tr>
  <tr><td>Comments</td><td>

Examples include attesting to: authorship, correct transcription, and witness of specific event. Also known as a “Commitment Type Indication”.

</td></tr>
  <tr><td colspan="2" class="structure"><a name="Signature.when"> </a>**Signature.when**</td></tr>
  <tr><td>Definition</td><td>

When the digital signature was signed.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>1..1</td></tr>
  <tr><td>[Type](datatypes.html)</td><td>[instant](datatypes.html#instant)</td></tr>
  <tr><td>Comments</td><td>

This should agree with the information in the signature.

</td></tr>
  <tr><td colspan="2" class="structure"><a name="Signature.who_x_"> </a>**Signature.who[x]**</td></tr>
  <tr><td>Definition</td><td>

A reference to an application-usable description of the person that signed the certificate (e.g. the signature used their private key).

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>1..1</td></tr>
  <tr><td>[Type](datatypes.html)</td><td>[uri](datatypes.html#uri)|[Reference](references.html#Reference)([Practitioner](practitioner.html) | [RelatedPerson](relatedperson.html) | [Patient](patient.html))</td></tr>
  <tr><td>Comments</td><td>

This should agree with the information in the signature.

</td></tr>
  <tr><td colspan="2" class="structure"><a name="Signature.blob"> </a>**Signature.blob**</td></tr>
  <tr><td>Definition</td><td>

The base64 encoding of the XML-Signature.

</td></tr>
  <tr><td>[Control](conformance-rules.html#conformance)</td><td>1..1</td></tr>
  <tr><td>[Type](datatypes.html)</td><td>[base64Binary](datatypes.html#base64Binary)</td></tr>
  <tr><td>Comments</td><td>

Where the signed content is a FHIR Resource(s), the signature is of the XML form of the Resource(s) using  XML-Signature (XMLDIG) &quot;Detached Signature&quot; form.

</td></tr>
</table>
&copy; HL7.org 2011+. FHIR DSTU (v0.4.0-3900) 构建于2014  12月20号 2014 22:38+0000 星期六 . 
链接：[试行版是什么](http://hl7.org/implement/standards/fhir/dstu.html) |[版本更新情况](http://hl7.org/implement/standards/fhir/history.html) | [许可协议](http://hl7.org/implement/standards/fhir/license.html) |[提交变更建议](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemAdd&tracker_id=677) 	  