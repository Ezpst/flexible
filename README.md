---
grammar_cjkRuby: true
---

## flexible
***

> **使用方法**

``` javascript
<meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, minimum-scale=1, user-scalable=no">
<script src="./amfe-flexible.js"></script>
```


> **px转换**

使用sass预处理器来快速转换

借助 [Koala][1] 对sass进行编译    ==注：一定要安装在C盘，不然会编译失败，亲测==

==如果要在 .scss 文件中写中文注释，在文件内添加 @charset "utf-8";==

 1. px —> rem
 
 ``` javascript
 $design-width: 750 !default;
  @function rem($px) {
  @return $px / $design-width * 10 + rem; // $design-width的值以设计图尺寸为准
}
 ```
 
 
 2. px —> em
 ``` javascript
 @function px2em($px, $base-font-size: 16px) {
  @if (unitless($px)) {
    @warn "Assuming #{$px} to be in pixels, attempting to convert it into pixels for you";
    @return px2em($px + 0px);
  }
  @else if (unit($px)==em) {
    @return $px;
  }
  @return ($px / $base-font-size) * 1em;
}
 ```
 
 
 > **文本字号不推荐使用==rem==**

我们在iPhone3G和iPhone4的Retina屏下面，希望看到的文本字号是相同的。也就是说，我们不希望文本在Retina屏幕下变小，另外，我们希望在大屏手机上看到更多文本，以及，现在绝大多数的字体文件都自带一些点阵尺寸，通常是16px和24px，所以我们不希望出现13px和15px这样的奇葩尺寸。

如此一来，就决定了在制作H5的页面中，rem并不适合用到段落文本上。所以文本还是使用px作为单位。
 
 

 


  [1]: http://koala-app.com/index-zh.html