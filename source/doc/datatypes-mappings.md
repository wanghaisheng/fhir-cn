title: 
date: 
categories: doc
---

[首页](../home/index.html) >[文档](documentation.html) >[数据类型](datatypes.html)> **数据类型的映射**        

本页内容:

*   [数据类型](datatypes.html)
*   [示例](datatypes-examples.html)
*   [详细描述](datatypes-definitions.html)
*   [映射](datatypes-mappings.html)
### 1.17.1  数据类型的映射

This page provides mappings for the data types. There are mappings to HL7 v2, v3, and (where appropriate) vCard.

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

<a name="primitive"> </a>
<a name="primitives"> </a>

### <span class="sectioncount">1.17.3.1<a name="1.17.3.1"> </a></span> Primitive Types

See also [Base Definition](datatypes.html#primitive), [Examples](datatypes-examples.html#primitive) and [Detailed Descriptions](datatypes-definitions.html#primitive).

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

<table class="grid">
<tr><td>**Data Type**</td><td>**V2**</td><td>**RIM**</td></tr><tr><td>base64Binary</td><td>~ED</td><td>BIN</td></tr><tr><td>boolean</td><td>n/a</td><td>BL</td></tr><tr><td>date</td><td>DT</td><td>TS</td></tr><tr><td>dateTime</td><td>DTM</td><td>TS</td></tr><tr><td>decimal</td><td>~NM</td><td>REAL</td></tr><tr><td>instant</td><td>DTM</td><td>TS</td></tr><tr><td>integer</td><td>~NM/~SI</td><td>INT</td></tr><tr><td>string</td><td>ST</td><td>ST</td></tr><tr><td>time</td><td>TM</td><td>n/a</td></tr><tr><td>uri</td><td>n/a</td><td>URL</td></tr></table>

<a name="Attachment"> </a>
<a name="attachment"> </a>

### <span class="sectioncount">1.17.3.2<a name="1.17.3.2"> </a></span> Attachment

See also [Base Definition](datatypes.html#Attachment), [Examples](datatypes-examples.html#Attachment) and [Detailed Descriptions](datatypes-definitions.html#Attachment).

<a name="http://hl7.org/v2"> </a>
<a name="v2"> </a>

### <span class="sectioncount">1.17.3.3<a name="1.17.3.3"> </a></span> Mappings for HL7 v2 (http://hl7.org/v2)

<table class="grid">
 <tr><td><a name="Attachment"> </a><a name="attachment"> </a>**Attachment**</td><td>ED/RP</td></tr>
 <tr><td>    contentType</td><td>ED.2+ED.3/RP.2+RP.3. Note conversion may be needed if old style values are being used</td></tr>
 <tr><td>    language</td><td/></tr>
 <tr><td>    data</td><td>ED.5</td></tr>
 <tr><td>    url</td><td>RP.1+RP.2 - if they refer to a URL (see v2.6)</td></tr>
 <tr><td>    size</td><td/></tr>
 <tr><td>    hash</td><td/></tr>
 <tr><td>    title</td><td/></tr>
 <tr><td>    creation</td><td/></tr>
</table>
<a name="http://hl7.org/v3"> </a>
<a name="rim"> </a>

### <span class="sectioncount">1.17.3.4<a name="1.17.3.4"> </a></span> Mappings for RIM (http://hl7.org/v3)

<table class="grid">
 <tr><td><a name="Attachment"> </a><a name="attachment"> </a>**Attachment**</td><td>ED</td></tr>
 <tr><td>    contentType</td><td>./mediaType, ./charset</td></tr>
 <tr><td>    language</td><td>./language</td></tr>
 <tr><td>    data</td><td>./data</td></tr>
 <tr><td>    url</td><td>./reference/literal</td></tr>
 <tr><td>    size</td><td>N/A (needs data type R3 proposal)</td></tr>
 <tr><td>    hash</td><td>.integrityCheck[parent::ED/integrityCheckAlgorithm=&quot;SHA-1&quot;]</td></tr>
 <tr><td>    title</td><td>./title/data</td></tr>
 <tr><td>    creation</td><td>N/A (needs data type R3 proposal)</td></tr>
</table>

<a name="Identifier"> </a>
<a name="identifier"> </a>

### <span class="sectioncount">1.17.3.5<a name="1.17.3.5"> </a></span> Identifier

See also [Base Definition](datatypes.html#identifier), [Examples](datatypes-examples.html#identifier) and [Detailed Descriptions](datatypes-definitions.html#identifier).

<a name="http://hl7.org/v2"> </a>
<a name="v2"> </a>

### <span class="sectioncount">1.17.3.6<a name="1.17.3.6"> </a></span> Mappings for HL7 v2 (http://hl7.org/v2)

<table class="grid">
 <tr><td><a name="Identifier"> </a><a name="identifier"> </a>**Identifier**</td><td>CX / EI (occasionally, more often EI maps to a resource id or a URL)</td></tr>
 <tr><td>    use</td><td>N/A</td></tr>
 <tr><td>    label</td><td>CX.5</td></tr>
 <tr><td>    system</td><td>CX.4 / EI-2-4</td></tr>
 <tr><td>    value</td><td>CX.1 / EI.1</td></tr>
 <tr><td>    period</td><td>CX.7 + CX.8</td></tr>
 <tr><td>    assigner</td><td>CX.4 / (CX.4,CX.9,CX.10)</td></tr>
</table>
<a name="http://hl7.org/v3"> </a>
<a name="rim"> </a>

### <span class="sectioncount">1.17.3.7<a name="1.17.3.7"> </a></span> Mappings for RIM (http://hl7.org/v3)

<table class="grid">
 <tr><td><a name="Identifier"> </a><a name="identifier"> </a>**Identifier**</td><td>II - see see identifier pattern at http://wiki.hl7.org/index.php?title=Common_Design_Patterns#Identifier_Pattern for relevant discussion. The Identifier class is a little looser than the v3 type II because it allows URIs as well as registered OIDs or GUIDs.  Also maps to Role[classCode=IDENT]</td></tr>
 <tr><td>    use</td><td>Role.code or implied by context</td></tr>
 <tr><td>    label</td><td>Role.title or implied by context</td></tr>
 <tr><td>    system</td><td>II.root or Role.id.root</td></tr>
 <tr><td>    value</td><td>II.extension or II.root if system indicates OID or GUID (Or Role.id.extension or root)</td></tr>
 <tr><td>    period</td><td>Role.effectiveTime or implied by context</td></tr>
 <tr><td>    assigner</td><td>II.assigningAuthorityName but note that this is an improper use by the definition of the field.  Also Role.scoper</td></tr>
</table>
<a name="http://www.omg.org/spec/ServD/1.0/"> </a>
<a name="servd"> </a>

### <span class="sectioncount">1.17.3.8<a name="1.17.3.8"> </a></span> Mappings for ServD (http://www.omg.org/spec/ServD/1.0/)

<table class="grid">
 <tr><td><a name="Identifier"> </a><a name="identifier"> </a>**Identifier**</td><td>Identifier</td></tr>
 <tr><td>    use</td><td/></tr>
 <tr><td>    label</td><td/></tr>
 <tr><td>    system</td><td>./IdentifierType</td></tr>
 <tr><td>    value</td><td>./Value</td></tr>
 <tr><td>    period</td><td>./StartDate and ./EndDate</td></tr>
 <tr><td>    assigner</td><td>./IdentifierIssuingAuthority</td></tr>
</table>

<a name="Coding"> </a>
<a name="coding"> </a>

### <span class="sectioncount">1.17.3.9<a name="1.17.3.9"> </a></span> Coding

See also [Base Definition](datatypes.html#Coding), [Examples](datatypes-examples.html#Coding) and [Detailed Descriptions](datatypes-definitions.html#Coding).

<a name="http://hl7.org/v2"> </a>
<a name="v2"> </a>

### <span class="sectioncount">1.17.3.10<a name="1.17.3.10"> </a></span> Mappings for HL7 v2 (http://hl7.org/v2)

<table class="grid">
 <tr><td><a name="Coding"> </a><a name="coding"> </a>**Coding**</td><td>CE/CNE/CWE subset one of the sets of component 1-3 or 4-6</td></tr>
 <tr><td>    system</td><td>C*E.3</td></tr>
 <tr><td>    version</td><td>C*E.7</td></tr>
 <tr><td>    code</td><td>C*E.1</td></tr>
 <tr><td>    display</td><td>C*E.2 - but note this is not well followed</td></tr>
 <tr><td>    primary</td><td>Sometimes implied by being first</td></tr>
</table>
<a name="http://hl7.org/v3"> </a>
<a name="rim"> </a>

### <span class="sectioncount">1.17.3.11<a name="1.17.3.11"> </a></span> Mappings for RIM (http://hl7.org/v3)

<table class="grid">
 <tr><td><a name="Coding"> </a><a name="coding"> </a>**Coding**</td><td>CV</td></tr>
 <tr><td>    system</td><td>./codeSystem</td></tr>
 <tr><td>    version</td><td>./codeSystemVersion</td></tr>
 <tr><td>    code</td><td>./code</td></tr>
 <tr><td>    display</td><td>CV.displayName</td></tr>
 <tr><td>    primary</td><td>CD.codingRationale</td></tr>
</table>

<a name="CodeableConcept"> </a>
<a name="codeableconcept"> </a>

### <span class="sectioncount">1.17.3.12<a name="1.17.3.12"> </a></span> CodeableConcept

See also [Base Definition](datatypes.html#CodeableConcept), [Examples](datatypes-examples.html#CodeableConcept) and [Detailed Descriptions](datatypes-definitions.html#CodeableConcept).

<a name="http://hl7.org/v2"> </a>
<a name="v2"> </a>

### <span class="sectioncount">1.17.3.13<a name="1.17.3.13"> </a></span> Mappings for HL7 v2 (http://hl7.org/v2)

<table class="grid">
 <tr><td><a name="CodeableConcept"> </a><a name="codeableconcept"> </a>**CodeableConcept**</td><td>CE/CNE/CWE</td></tr>
 <tr><td>    coding</td><td>C*E.1-8, C*E.10-22</td></tr>
 <tr><td>    text</td><td>C*E.9. But note many systems use C*E.2 for this</td></tr>
</table>
<a name="http://hl7.org/v3"> </a>
<a name="rim"> </a>

### <span class="sectioncount">1.17.3.14<a name="1.17.3.14"> </a></span> Mappings for RIM (http://hl7.org/v3)

<table class="grid">
 <tr><td><a name="CodeableConcept"> </a><a name="codeableconcept"> </a>**CodeableConcept**</td><td>CD</td></tr>
 <tr><td>    coding</td><td>union(., ./translation)</td></tr>
 <tr><td>    text</td><td>./originalText[mediaType/code=&quot;text/plain&quot;]/data</td></tr>
</table>

<a name="Quantity"> </a>
<a name="quantity"> </a>
<a name="age"> </a>
<a name="distance"> </a>
<a name="duration"> </a>
<a name="count"> </a>
<a name="money"> </a>

### <span class="sectioncount">1.17.3.15<a name="1.17.3.15"> </a></span> Quantity

See also [Base Definition](datatypes.html#Quantity), [Examples](datatypes-examples.html#Quantity) and [Detailed Descriptions](datatypes-definitions.html#Quantity).

<a name="http://hl7.org/v2"> </a>
<a name="v2"> </a>

### <span class="sectioncount">1.17.3.16<a name="1.17.3.16"> </a></span> Mappings for HL7 v2 (http://hl7.org/v2)

<table class="grid">
 <tr><td><a name="Quantity"> </a><a name="quantity"> </a>**Quantity**</td><td>SN (see also Range) or CQ</td></tr>
 <tr><td>    value</td><td>SN.2  / CQ - N/A</td></tr>
 <tr><td>    comparator</td><td>SN.1  / CQ.1</td></tr>
 <tr><td>    units</td><td>(see OBX.6 etc) / CQ.2</td></tr>
 <tr><td>    system</td><td>(see OBX.6 etc) / CQ.2</td></tr>
 <tr><td>    code</td><td>(see OBX.6 etc) / CQ.2</td></tr>
</table>
<a name="http://hl7.org/v3"> </a>
<a name="rim"> </a>

### <span class="sectioncount">1.17.3.17<a name="1.17.3.17"> </a></span> Mappings for RIM (http://hl7.org/v3)

<table class="grid">
 <tr><td><a name="Quantity"> </a><a name="quantity"> </a>**Quantity**</td><td>PQ, IVL&lt;PQ&gt;, MO, CO, depending on the values</td></tr>
 <tr><td>    value</td><td>PQ.value, CO.value, MO.value, IVL.high or IVL.low depending on the value</td></tr>
 <tr><td>    comparator</td><td>IVL properties</td></tr>
 <tr><td>    units</td><td>PQ.unit</td></tr>
 <tr><td>    system</td><td>CO.codeSystem, PQ.translation.codeSystem</td></tr>
 <tr><td>    code</td><td>PQ.code, MO.currency, PQ.translation.code</td></tr>
</table>

<a name="Range"> </a>
<a name="range"> </a>

### <span class="sectioncount">1.17.3.18<a name="1.17.3.18"> </a></span> Range

See also [Base Definition](datatypes.html#Range), [Examples](datatypes-examples.html#Range) and [Detailed Descriptions](datatypes-definitions.html#Range).

<a name="http://hl7.org/v2"> </a>
<a name="v2"> </a>

### <span class="sectioncount">1.17.3.19<a name="1.17.3.19"> </a></span> Mappings for HL7 v2 (http://hl7.org/v2)

<table class="grid">
 <tr><td><a name="Range"> </a><a name="range"> </a>**Range**</td><td>NR and also possibly SN (but see also quantity)</td></tr>
 <tr><td>    low</td><td>NR.1</td></tr>
 <tr><td>    high</td><td>NR.2</td></tr>
</table>
<a name="http://hl7.org/v3"> </a>
<a name="rim"> </a>

### <span class="sectioncount">1.17.3.20<a name="1.17.3.20"> </a></span> Mappings for RIM (http://hl7.org/v3)

<table class="grid">
 <tr><td><a name="Range"> </a><a name="range"> </a>**Range**</td><td>IVL&lt;QTY[not(type=&quot;TS&quot;)]&gt; [lowClosed=&quot;true&quot; and highClosed=&quot;true&quot;]or URG&lt;QTY[not(type=&quot;TS&quot;)]&gt;</td></tr>
 <tr><td>    low</td><td>./low</td></tr>
 <tr><td>    high</td><td>./high</td></tr>
</table>

<a name="Ratio"> </a>
<a name="ratio"> </a>

### <span class="sectioncount">1.17.3.21<a name="1.17.3.21"> </a></span> Ratio

See also [Base Definition](datatypes.html#Ratio), [Examples](datatypes-examples.html#Ratio) and [Detailed Descriptions](datatypes-definitions.html#Ratio).

<a name="http://hl7.org/v2"> </a>
<a name="v2"> </a>

### <span class="sectioncount">1.17.3.22<a name="1.17.3.22"> </a></span> Mappings for HL7 v2 (http://hl7.org/v2)

<table class="grid">
 <tr><td><a name="Ratio"> </a><a name="ratio"> </a>**Ratio**</td><td>N/A</td></tr>
 <tr><td>    numerator</td><td/></tr>
 <tr><td>    denominator</td><td/></tr>
</table>
<a name="http://hl7.org/v3"> </a>
<a name="rim"> </a>

### <span class="sectioncount">1.17.3.23<a name="1.17.3.23"> </a></span> Mappings for RIM (http://hl7.org/v3)

<table class="grid">
 <tr><td><a name="Ratio"> </a><a name="ratio"> </a>**Ratio**</td><td>RTO</td></tr>
 <tr><td>    numerator</td><td>.numerator</td></tr>
 <tr><td>    denominator</td><td>.denominator</td></tr>
</table>

<a name="Period"> </a>
<a name="period"> </a>

### <span class="sectioncount">1.17.3.24<a name="1.17.3.24"> </a></span> Period

See also [Base Definition](datatypes.html#Period), [Examples](datatypes-examples.html#Period) and [Detailed Descriptions](datatypes-definitions.html#Period).

<a name="http://hl7.org/v2"> </a>
<a name="v2"> </a>

### <span class="sectioncount">1.17.3.25<a name="1.17.3.25"> </a></span> Mappings for HL7 v2 (http://hl7.org/v2)

<table class="grid">
 <tr><td><a name="Period"> </a><a name="period"> </a>**Period**</td><td>DR</td></tr>
 <tr><td>    start</td><td>DR.1</td></tr>
 <tr><td>    end</td><td>DR.2</td></tr>
</table>
<a name="http://hl7.org/v3"> </a>
<a name="rim"> </a>

### <span class="sectioncount">1.17.3.26<a name="1.17.3.26"> </a></span> Mappings for RIM (http://hl7.org/v3)

<table class="grid">
 <tr><td><a name="Period"> </a><a name="period"> </a>**Period**</td><td>IVL&lt;TS&gt;[lowClosed=&quot;true&quot; and highClosed=&quot;true&quot;] or URG&lt;TS&gt;[lowClosed=&quot;true&quot; and highClosed=&quot;true&quot;]</td></tr>
 <tr><td>    start</td><td>./low</td></tr>
 <tr><td>    end</td><td>./high</td></tr>
</table>

<a name="SampledData"> </a>
<a name="sampleddata"> </a>

### <span class="sectioncount">1.17.3.27<a name="1.17.3.27"> </a></span> SampledData

See also [Base Definition](datatypes.html#SampledData), [Examples](datatypes-examples.html#SampledData) and [Detailed Descriptions](datatypes-definitions.html#SampledData).

<a name="http://hl7.org/v2"> </a>
<a name="v2"> </a>

### <span class="sectioncount">1.17.3.28<a name="1.17.3.28"> </a></span> Mappings for HL7 v2 (http://hl7.org/v2)

<table class="grid">
 <tr><td><a name="SampledData"> </a><a name="sampleddata"> </a>**SampledData**</td><td>N/A (but see section 7.14 in v2.7)</td></tr>
 <tr><td>    origin</td><td/></tr>
 <tr><td>    period</td><td/></tr>
 <tr><td>    factor</td><td/></tr>
 <tr><td>    lowerLimit</td><td/></tr>
 <tr><td>    upperLimit</td><td/></tr>
 <tr><td>    dimensions</td><td/></tr>
 <tr><td>    data</td><td/></tr>
</table>
<a name="http://hl7.org/v3"> </a>
<a name="rim"> </a>

### <span class="sectioncount">1.17.3.29<a name="1.17.3.29"> </a></span> Mappings for RIM (http://hl7.org/v3)

<table class="grid">
 <tr><td><a name="SampledData"> </a><a name="sampleddata"> </a>**SampledData**</td><td>SLIST + GLIST</td></tr>
 <tr><td>    origin</td><td>SLIST.origin</td></tr>
 <tr><td>    period</td><td>GLIST.increment</td></tr>
 <tr><td>    factor</td><td>SLIST.factor</td></tr>
 <tr><td>    lowerLimit</td><td>N/A (use SLIST.digits.nullFlavor)</td></tr>
 <tr><td>    upperLimit</td><td>N/A (use SLIST.digits.nullFlavor)</td></tr>
 <tr><td>    dimensions</td><td>N/A (fixed to 1)</td></tr>
 <tr><td>    data</td><td>SLIST.digits</td></tr>
</table>

<a name="HumanName"> </a>
<a name="humanname"> </a>

### <span class="sectioncount">1.17.3.30<a name="1.17.3.30"> </a></span> HumanName

See also [Base Definition](datatypes.html#HumanName), [Examples](datatypes-examples.html#HumanName) and [Detailed Descriptions](datatypes-definitions.html#HumanName).

<a name="http://hl7.org/v2"> </a>
<a name="v2"> </a>

### <span class="sectioncount">1.17.3.31<a name="1.17.3.31"> </a></span> Mappings for HL7 v2 (http://hl7.org/v2)

<table class="grid">
 <tr><td><a name="HumanName"> </a><a name="humanname"> </a>**HumanName**</td><td>XPN</td></tr>
 <tr><td>    use</td><td>XPN.7, but often indicated by which field contains the name</td></tr>
 <tr><td>    text</td><td>implied by XPN.11</td></tr>
 <tr><td>    family</td><td>XPN.1</td></tr>
 <tr><td>    given</td><td>XPN.2 + XPN.3</td></tr>
 <tr><td>    prefix</td><td>XPN.5</td></tr>
 <tr><td>    suffix</td><td>XPN/4</td></tr>
 <tr><td>    period</td><td>XPN.13 + XPN.14</td></tr>
</table>
<a name="http://hl7.org/v3"> </a>
<a name="rim"> </a>

### <span class="sectioncount">1.17.3.32<a name="1.17.3.32"> </a></span> Mappings for RIM (http://hl7.org/v3)

<table class="grid">
 <tr><td><a name="HumanName"> </a><a name="humanname"> </a>**HumanName**</td><td>EN (actually, PN)</td></tr>
 <tr><td>    use</td><td>unique(./use)</td></tr>
 <tr><td>    text</td><td>./formatted</td></tr>
 <tr><td>    family</td><td>./part[partType = FAM]</td></tr>
 <tr><td>    given</td><td>./part[partType = GIV]</td></tr>
 <tr><td>    prefix</td><td>./part[partType = PFX]</td></tr>
 <tr><td>    suffix</td><td>./part[partType = SFX]</td></tr>
 <tr><td>    period</td><td>./usablePeriod[type=&quot;IVL&lt;TS&gt;&quot;]</td></tr>
</table>
<a name="http://www.omg.org/spec/ServD/1.0/"> </a>
<a name="servd"> </a>

### <span class="sectioncount">1.17.3.33<a name="1.17.3.33"> </a></span> Mappings for ServD (http://www.omg.org/spec/ServD/1.0/)

<table class="grid">
 <tr><td><a name="HumanName"> </a><a name="humanname"> </a>**HumanName**</td><td>ProviderName</td></tr>
 <tr><td>    use</td><td>./NamePurpose</td></tr>
 <tr><td>    text</td><td/></tr>
 <tr><td>    family</td><td>./FamilyName</td></tr>
 <tr><td>    given</td><td>./GivenNames</td></tr>
 <tr><td>    prefix</td><td>./TitleCode</td></tr>
 <tr><td>    suffix</td><td/></tr>
 <tr><td>    period</td><td>./StartDate and ./EndDate</td></tr>
</table>

<div class="mapping">

**[vCard](http://tools.ietf.org/html/rfc6350) Mappings**

*   HumanName.text = vCard &quot;FN&quot; field
*   HumanName.use = use of the vCard &quot;TYPE&quot; parameter
*   HumanName.family, .given, .prefix, .suffix = parts of vCard &quot;N&quot; field. Note that there is no FHIR equivalent for the poorly defined &quot;additional&quot; name field. In FHIR, given names go in &quot;middle&quot; names
*   The vCard nickname corresponds to a name with the use &quot;nickname&quot;
</div>

<a name="Address"> </a>
<a name="address"> </a>

### <span class="sectioncount">1.17.3.34<a name="1.17.3.34"> </a></span> Address

See also [Base Definition](datatypes.html#Address), [Examples](datatypes-examples.html#Address) and [Detailed Descriptions](datatypes-definitions.html#Address).

<a name="http://hl7.org/v2"> </a>
<a name="v2"> </a>

### <span class="sectioncount">1.17.3.35<a name="1.17.3.35"> </a></span> Mappings for HL7 v2 (http://hl7.org/v2)

<table class="grid">
 <tr><td><a name="Address"> </a><a name="address"> </a>**Address**</td><td>XAD</td></tr>
 <tr><td>    use</td><td>XAD.7</td></tr>
 <tr><td>    text</td><td>XAD.1 + XAD.2 + XAD.3 + XAD.4 + XAD.5 + XAD.6</td></tr>
 <tr><td>    line</td><td>XAD.1 + XAD.2 (note: XAD.1 and XAD.2 have different meanings for a company address than for a person address)</td></tr>
 <tr><td>    city</td><td>XAD.3</td></tr>
 <tr><td>    state</td><td>XAD.4</td></tr>
 <tr><td>    postalCode</td><td>XAD.5</td></tr>
 <tr><td>    country</td><td>XAD.6</td></tr>
 <tr><td>    period</td><td>XAD.12 / XAD.13 + XAD.14</td></tr>
</table>
<a name="http://hl7.org/v3"> </a>
<a name="rim"> </a>

### <span class="sectioncount">1.17.3.36<a name="1.17.3.36"> </a></span> Mappings for RIM (http://hl7.org/v3)

<table class="grid">
 <tr><td><a name="Address"> </a><a name="address"> </a>**Address**</td><td>AD</td></tr>
 <tr><td>    use</td><td>unique(./use)</td></tr>
 <tr><td>    text</td><td>./formatted</td></tr>
 <tr><td>    line</td><td>AD.part[parttype = AL]</td></tr>
 <tr><td>    city</td><td>AD.part[parttype = CTY]</td></tr>
 <tr><td>    state</td><td>AD.part[parttype = STA]</td></tr>
 <tr><td>    postalCode</td><td>AD.part[parttype = ZIP]</td></tr>
 <tr><td>    country</td><td>AD.part[parttype = CNT]</td></tr>
 <tr><td>    period</td><td>./usablePeriod[type=&quot;IVL&lt;TS&gt;&quot;]</td></tr>
</table>
<a name="http://w3.org/vcard"> </a>
<a name="vcard"> </a>

### <span class="sectioncount">1.17.3.37<a name="1.17.3.37"> </a></span> Mappings for vCard (http://w3.org/vcard)

<table class="grid">
 <tr><td><a name="Address"> </a><a name="address"> </a>**Address**</td><td/></tr>
 <tr><td>    use</td><td/></tr>
 <tr><td>    text</td><td/></tr>
 <tr><td>    line</td><td>street address</td></tr>
 <tr><td>    city</td><td>locality</td></tr>
 <tr><td>    state</td><td>region</td></tr>
 <tr><td>    postalCode</td><td>postal code</td></tr>
 <tr><td>    country</td><td>country name</td></tr>
 <tr><td>    period</td><td/></tr>
</table>
<a name="http://www.omg.org/spec/ServD/1.0/"> </a>
<a name="servd"> </a>

### <span class="sectioncount">1.17.3.38<a name="1.17.3.38"> </a></span> Mappings for ServD (http://www.omg.org/spec/ServD/1.0/)

<table class="grid">
 <tr><td><a name="Address"> </a><a name="address"> </a>**Address**</td><td>Address</td></tr>
 <tr><td>    use</td><td>./AddressPurpose</td></tr>
 <tr><td>    text</td><td/></tr>
 <tr><td>    line</td><td>./StreetAddress (newline delimitted)</td></tr>
 <tr><td>    city</td><td>./Jurisdiction</td></tr>
 <tr><td>    state</td><td>./Region</td></tr>
 <tr><td>    postalCode</td><td>./PostalIdentificationCode</td></tr>
 <tr><td>    country</td><td>./Country</td></tr>
 <tr><td>    period</td><td>./StartDate and ./EndDate</td></tr>
</table>

<div class="mapping">

**[vCard](http://tools.ietf.org/html/rfc6350) Mappings**

*   Address.text = vCard &quot;ADDRESS&quot; &quot;LABEL&quot; parameter
*   Address.use = vCard &quot;TYPE&quot; parameter
*   Address.line = vCard &quot;street&quot; list component
*   Address.city = vCard &quot;locality&quot; list component
*   Address.state = vCard &quot;region&quot; list component
*   Address.zip = vCard &quot;code&quot; list component
*   Address.country = vCard &quot;country&quot; list component
</div>

<a name="ContactPoint"> </a>
<a name="contactpoint"> </a>

### <span class="sectioncount">1.17.3.39<a name="1.17.3.39"> </a></span> ContactPoint

See also [Base Definition](datatypes.html#ContactPoint), [Examples](datatypes-examples.html#ContactPoint) and [Detailed Descriptions](datatypes-definitions.html#ContactPoint).

<a name="http://hl7.org/v2"> </a>
<a name="v2"> </a>

### <span class="sectioncount">1.17.3.40<a name="1.17.3.40"> </a></span> Mappings for HL7 v2 (http://hl7.org/v2)

<table class="grid">
 <tr><td><a name="ContactPoint"> </a><a name="contactpoint"> </a>**ContactPoint**</td><td>XTN</td></tr>
 <tr><td>    system</td><td>XTN.3</td></tr>
 <tr><td>    value</td><td>XTN.1 (or XTN.12)</td></tr>
 <tr><td>    use</td><td>XTN.2 - but often indicated by field</td></tr>
 <tr><td>    period</td><td>N/A</td></tr>
</table>
<a name="http://hl7.org/v3"> </a>
<a name="rim"> </a>

### <span class="sectioncount">1.17.3.41<a name="1.17.3.41"> </a></span> Mappings for RIM (http://hl7.org/v3)

<table class="grid">
 <tr><td><a name="ContactPoint"> </a><a name="contactpoint"> </a>**ContactPoint**</td><td>TEL</td></tr>
 <tr><td>    system</td><td>./scheme</td></tr>
 <tr><td>    value</td><td>./url</td></tr>
 <tr><td>    use</td><td>unique(./use)</td></tr>
 <tr><td>    period</td><td>./useablePeriod[type=&quot;IVL&lt;TS&gt;&quot;]</td></tr>
</table>
<a name="http://www.omg.org/spec/ServD/1.0/"> </a>
<a name="servd"> </a>

### <span class="sectioncount">1.17.3.42<a name="1.17.3.42"> </a></span> Mappings for ServD (http://www.omg.org/spec/ServD/1.0/)

<table class="grid">
 <tr><td><a name="ContactPoint"> </a><a name="contactpoint"> </a>**ContactPoint**</td><td>ContactPoint</td></tr>
 <tr><td>    system</td><td>./ContactPointType</td></tr>
 <tr><td>    value</td><td>./Value</td></tr>
 <tr><td>    use</td><td>./ContactPointPurpose</td></tr>
 <tr><td>    period</td><td>./StartDate and ./EndDate</td></tr>
</table>

<a name="Timing"> </a>
<a name="timing"> </a>

### <span class="sectioncount">1.17.3.43<a name="1.17.3.43"> </a></span> Timing

See also [Base Definition](datatypes.html#Timing), [Examples](datatypes-examples.html#Timing) and [Detailed Descriptions](datatypes-definitions.html#Timing).

<a name="http://hl7.org/v2"> </a>
<a name="v2"> </a>

### <span class="sectioncount">1.17.3.44<a name="1.17.3.44"> </a></span> Mappings for HL7 v2 (http://hl7.org/v2)

<table class="grid">
 <tr><td><a name="Timing"> </a><a name="timing"> </a>**Timing**</td><td>N/A</td></tr>
 <tr><td>    event</td><td/></tr>
 <tr><td>    repeat</td><td/></tr>
 <tr><td>        frequency</td><td/></tr>
 <tr><td>        when</td><td/></tr>
 <tr><td>        duration</td><td/></tr>
 <tr><td>        units</td><td/></tr>
 <tr><td>        count</td><td/></tr>
 <tr><td>        end</td><td/></tr>
</table>
<a name="http://hl7.org/v3"> </a>
<a name="rim"> </a>

### <span class="sectioncount">1.17.3.45<a name="1.17.3.45"> </a></span> Mappings for RIM (http://hl7.org/v3)

<table class="grid">
 <tr><td><a name="Timing"> </a><a name="timing"> </a>**Timing**</td><td>QSET&lt;TS&gt; (GTS)</td></tr>
 <tr><td>    event</td><td>QLIST&lt;TS&gt; or PIVL.offset</td></tr>
 <tr><td>    repeat</td><td>Implies PIVL or EIVL</td></tr>
 <tr><td>        frequency</td><td>PIVL.phase</td></tr>
 <tr><td>        when</td><td>EIVL.event</td></tr>
 <tr><td>        duration</td><td>PIVL.phase / EIVL.offset</td></tr>
 <tr><td>        units</td><td>PIVL.phase.unit</td></tr>
 <tr><td>        count</td><td>PIVL.count</td></tr>
 <tr><td>        end</td><td>N/A</td></tr>
</table>

<a name="Signature"> </a>
<a name="timing"> </a>

### <span class="sectioncount">1.17.3.46<a name="1.17.3.46"> </a></span> Signature

See also [Base Definition](datatypes.html#Signature), [Examples](datatypes-examples.html#Signature) and [Detailed Descriptions](datatypes-definitions.html#Signature).

</div>
  
&copy; © HL7.org 2011+. FHIR DSTU (v0.5.0-5149) generated on Fri, Apr 3, 2015 14:36+1100\.  
链接：[试行版是什么](http://hl7.org/implement/standards/fhir/dstu.html) |[版本更新情况](http://hl7.org/implement/standards/fhir/history.html) | [许可协议](http://hl7.org/implement/standards/fhir/license.html) |[提交变更建议](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemAdd&tracker_id=677) 	  