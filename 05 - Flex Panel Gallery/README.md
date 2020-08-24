# Flex面板画廊

### 功能分析

该练习小项目是用flex布局，点击页面会有两段动画效果（盒子变宽，出现文字，其余盒子变窄），需要自行添加css样式

### 知识点分析

1. flex布局

2. 点击事件

3. 添加css类名

4. transitonend


### 练习过程

#### css部分

首先添加一些css，使页面布局正确，用到了flex布局

```js
justify-content: center;
      align-self: center;
```

还使用了tansition属性将上下两行文字移出屏幕外

#### js部分

首先获取元素（列）

```js
//获取元素
      let panels = document.querySelectorAll('.panel');
```

遍历panels注册点击事件

```js
panels.forEach(panel => {
        //点击事件
        panel.addEventListener('click',function () {
          this.classList.toggle('open')
        })
        //过渡结束事件
        panel.addEventListener('transitionend',function (e) {
          // console.log(e);
          //限定flex过渡结束后进行类名的添加和删除
          if (e.propertyName.indexOf('flex') !== -1) {
            this.classList.toggle('active')
          }
        })
      })
```

这个练习与之前的比较起来，js部分比较简单，主要是一些知识点的记忆

### js代码

这里用了函数自调用，是为了有较好的封装性

具体说明可以参考MDN文档[IIFE](https://developer.mozilla.org/en-US/docs/Glossary/IIFE)（立即调用函数表达式）

```js
;(function () {
      //获取元素
      let panels = document.querySelectorAll('.panel');

      //遍历panels注册点击事件
      
      panels.forEach(panel => {
        //点击事件
        panel.addEventListener('click',function () {
          this.classList.toggle('open')
        })
        //过渡结束事件
        panel.addEventListener('transitionend',function (e) {
          // console.log(e);
          //限定flex过渡结束后进行类名的添加和删除
          if (e.propertyName.indexOf('flex') !== -1) {
            this.classList.toggle('active')
          }
        })
      })
    })()
```

