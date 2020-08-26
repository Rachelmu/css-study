# css
## 小tip:CSS vw让overflow:auto页面滚动条出现时不跳动
- 首先，.wrap-outer指的是居中定宽主体的父级，如果没有，创建一个（使用主体也是可以实现类似效果，不过本着宽度分离原则，不推荐）；
- 然后，calc是CSS3中的计算，IE10+浏览器支持，IE9浏览器基本支持(不能用在background-position上)；
- 最后，100vw相对于浏览器的window.innerWidth，是浏览器的内部宽度，注意，滚动条宽度也计算在内！而100%是可用宽度，是不含滚动条的宽度。
- 于是，calc(100vw - 100%)就是浏览器滚动条的宽度大小（如果有，如果没有滚动条则是0）！左右都有一个滚动条宽度（或都是0）被占用，主体内容就可以永远居中浏览器啦，从而没有任何跳动！
```
.wrap-outer {
    margin-left: calc(100vw - 100%);
}
.wrap-outer {
    padding-left: calc(100vw - 100%);
}
```
```
@media screen and (min-width: 1150px) {
   .wrap-outer {
       margin-left: calc(100vw - 100%);
   }
}
```
```
html {
  overflow-y: scroll;
}

:root {
  overflow-y: auto;
  overflow-x: hidden;
}

:root body {
  position: absolute;
}

body {
  width: 100vw;
  overflow: hidden;
}
```