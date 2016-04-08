## 各种小问题
- Attributes provide additional information about HTML elements.
- Meta data means data about data. HTML meta data is data about the HTML document.
- Browsers display \<strong\> as \<b\>, and \<em\> as \<i\>.  

However, there is a difference in the meaning of these tags: \<b\> and \<i\> defines bold and italic text,  
but \<strong\> and \<em\> means that the text is "important".

- Both the width, height, and style attributes are valid in the latest HTML5 standard.  

We suggest you use the style attribute. It prevents styles sheets from changing the original size of images:

---

##CSS 与 Javascript 的外联（external style sheet）和内联（internal style sheet）


<!------------------------------------------------------------------------>
<!------------------------------------------------------------------------>
<!------------------------------------------------------------------------>
<!------------------------------------------------------------------------>

1. Css external style sheet

优点：css在同一个文件中，当页面需要修改的时候只需要修改一个文件即可，方便维护。<br>
缺点：HTTP请求多，浏览器要加载完CSS才能渲染页面，因此影响页面的性能。<br>

2. Css internal style sheet

优点：内联 CSS 可以有效减少 HTTP 请求，提升页面性能，缓解服务器压力。由于浏览器加载完 CSS 才能渲染页面，因此能防止 CSS 文件无法读取而造成页面裸奔的现象。<br>

缺点：每次修改css的时候需要修改多个页面<br>


3. Javascrip内联和外置的区别其实也差不多<br>

JavaScript文件外部加载的好处<br>
统一定义JavaScript代码，方便查看，方便维护。<br>
使代码更安全，可以压缩，加密单个JavaScript文件。<br>
浏览器可以缓存JavaScript文件，减少宽带使用（当多个页面同时使用一个JavaScript文件的时候，通常只需下载一次）。<br>
 

JavaScript文件外部加载的注意事项<br>
不要把JavaScript分为多个文件，多个文件会增加服务器的负担，增加服务器的HTTP请求。<br>
一个JavaScript文件也会增大HTTP请求。<br>
 
---
使用外部JavaScript和CSS   
很多性能规则都是关于如何处理外部文件的。但是，在你采取这些措施前你可能会问到一个更基本的问题：JavaScript和CSS是应该放在外部文件中呢还是把它们放在页面本身之内呢？<br>  

在实际应用中使用外部文件可以提高页面速度，因为JavaScript和CSS文件都能在浏览器中产生缓存。内置在HTML文档中的JavaScript  和CSS则会在每次请求中随HTML文档重新下载。这虽然**减少了HTTP请求的次数，却增加了HTML文档的大小**。从另一方面来说，如果外部文件中的 JavaScript和CSS被浏览器缓存，在没有增加HTTP请求次数的同时可以减少HTML文档的大小。

关键问题是，外部JavaScript和CSS文件缓存的频率和请求HTML文档的次数有关。虽然有一定的难度，但是仍然有一些指标可以一测量它。 如果一个会话中用户会浏览你网站中的多个页面，并且这些页面中会**重复使用相同的脚本和样式表**，缓存外部文件就会带来更大的益处。  
许多网站没有功能建立这些指标。对于这些网站来说，最好的坚决方法就是把JavaScript和CSS作为外部文件引用。**例外** 就是网站的主页，如Yahoo!主页和My Yahoo!。主页在一次会话中拥有较少（可能只有一次）的浏览量，你可以发现内置JavaScript和CSS对于终端用户来说会加快响应时间。

对于拥有较大浏览量的首页来说，有一种技术可以平衡内置代码带来的HTTP请求减少与通过使用外部文件进行缓存带来的好处。其中一个就是在 首页中内置 JavaScript和CSS，但是在页面下载完成后动态下载外部文件，在子页面中使用到这些文件时，它们已经缓存到浏览器了。  


---

<!----------------------------------------------------------------------------------------------------->
##src和href
src和href之间存在区别，能混淆使用。src用于替换当前元素，href用于在当前文档和引用资源之间确立联系。  <br> <br>
src是source的缩写，指向外部资源的位置，指向的内容将会嵌入到文档中当前标签所在位置；在请求src资源时会将其指向的资源下载并应用到文档内，例如js脚本，img图片和frame等元素。 <br><br> 
**\<script src ="js.js"\>\</script\>**<br> <br> 
当浏览器解析到该元素时，会暂停其他资源的下载和处理，直到将该资源加载、编译、执行完毕，图片和框架等元素也如此，类似于将所指向资源嵌入当前标签内。这也是为什么将js脚本放在底部而不是头部。 <br> <br> 

href是Hypertext Reference的缩写，指向网络资源所在位置，建立和当前元素（锚点）或当前文档（链接）之间的链接，如果我们在文档中添加<br>  
**\<link href="common.css" rel="stylesheet"/\>** <br><br>
那么浏览器会识别该文档为css文件，就会并行下载资源并且不会停止对当前文档的处理。这也是为什么建议使用link方式来加载css，而不是使用@import方式。
