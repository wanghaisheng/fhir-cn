fhir-cn
=======

FHIR中文版  the Chinese translation of FHIR 

[demo](http://wanghaisheng.github.io/fhir-cn/home/index.html)
1.theme本地化
修改菜单
修改widget
git  clone https://github.com/wanghaisheng/hexo-theme-lion.git themes/lion
2._config.yml配置
home的exclude、https://github.com/hexojs/hexo/issues/654   

3. 未避免给后续校验工作带来额外的工作量，拟采取中英文对照的方式。所有中文后添加</br> 保持中英文的分离 便于读者阅读。
在正式版发布之后，考虑移除英文或者其他方式处理  。
4. issues 如何汉译的问题  
Compartments——逻辑类型  
bundle——组合/整合  
Contained Resources——内嵌资源		
Resolving references to Resources——resolve的翻译 解决？	
Narrative——叙述性文本	
local reference within the resource——局部/本地引用	  
5.  1.10.1.3中 converting relative URLs to absolute URL？  
For each resource in the list, the bundle has the resource and also its metadata as listed above.  
Each entry in the bundle retains its original identifier. This means that applications reading
the bundle should always look for a resource by its identity (after converting relative URLs
absolute URL) in the bundle first before trying to access it by its URL.    
6.  1.10.2.2 then a properly identified resource cannot be assembled 这里我理解是improperly吧？ 如果是properly 那这个resource指的是什么resource？	
7.  Since the availability of images that are not contained in the resource is not guaranteed 这里是contained in	
8.  formats.htm中title应改成format 而不是Roadmap	

