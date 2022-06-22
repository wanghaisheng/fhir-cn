fhir-cn

just check new update version https://github.com/FHIR-CN/fhir-spec-ZhCN


=======

FHIR中文版    
the Chinese translation of FHIR   
版本：DSTU R2 ballot   http://hl7.org/fhir/2015May          
[demo请查看](http://wanghaisheng.github.io/fhir-cn/home/index.html)	
##环境配置
1.prerequirement  
*  nodejs 
*  npm 
*  hexo3.0   

注意：如果你的电脑中存在iojs、nodejs 多个版本，请先使用 nvm use选择一个版本，比如，这里选择
```
nvm  use iojs-v3.0.0
```
由于我电脑上也存在多个python版本，请切换至2.7
```
pyenv global 2.7.7

npm install hexo --no-optional
```
2.theme的安装  
```
git clone https://github.com/wanghaisheng/hexo-theme-lion.git themes/lion   
```  
3. 编译运行  
```
npm install 
hexo clean
hexo generate
hexo server
```  



## 校对进度

| 名称 | 中文地址 | 原始地址 | 状态 | 更新日期 |
| ---- | ---- | ---- | ---- | ---- |
| HL7 FHIR简介 |  http://wanghaisheng.github.io/fhir-cn/doc/summary.html |  http://hl7-fhir.github.io/summary.html | [x] | 2015-08-17 |
| HL7 FHIR 入门指南 | http://wanghaisheng.github.io/fhir-cn/doc/overview.html | http://hl7-fhir.github.io/overview.html | [x] |2015-08-17 |
| HL7 FHIR 开发人员入门指南 | http://wanghaisheng.github.io/fhir-cn/doc/overview-dev.html | http://hl7-fhir.github.io/overview-dev.html | [x] |2015-08-17 |
| HL7 FHIR 医护人员入门指南 | http://wanghaisheng.github.io/fhir-cn/doc/overview-clinical.html | http://hl7-fhir.github.io/overview-clinical.html | [x] |2015-08-17 |
| HL7 FHIR 信息学在被动式医疗向主动式医疗转变中的作用 | http://wanghaisheng.github.io/fhir-cn/doc/change.html |  http://hl7-fhir.github.io/change.html | [x] |2015-08-18 |
| HL7 FHIR与其他HL7标准的关系| http://wanghaisheng.github.io/fhir-cn/doc/comparison.html |  http://hl7-fhir.github.io/comparison.html | [x] |2015-08-18 |
| HL7 FHIR与EHR功能模型对应表 | http://wanghaisheng.github.io/fhir-cn/doc/ehr-fm.html |  http://hl7-fhir.github.io/ehr-fm.html | [x] |2015-08-18 |







