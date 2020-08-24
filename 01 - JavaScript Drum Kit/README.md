# JS打击鼓

### 功能

功能分析：

1. 对应键盘按下出现声音
2. 对应按键按下改变样式（出现黄色光圈）

知识点分析：

1. 键盘事件
2. audio标签
3. 模板字符串

### 获取元素

我们需要获取的有：

对应按键和audio标签

### 练习过程

可以先设置键盘按下事件，获取键盘，然后设置样式和播放声音。

1.通过模板字符串和属性名获取对应元素

```js
//创建键盘按下听事件 
window.addEventListener('keydown', playSound)
    function playSound(e) {
      //播放音乐
      const audio = document.querySelector(`audio[data-key="${e.keyCode}"]`);
      const key = document.querySelector(`div[data-key="${e.keyCode}"]`);
      
```

2.播放声音和进行样式的修改

```js
if (audio) {
        //改变媒体元素当前播放位置 实现连续触发的效果
        audio.currentTime = 0
        //播放声音 使用媒体标签具有的方法
        audio.play()
        //修改按键样式
        key.classList.add('playing')
      }
```

3.在过渡结束时清除样式(使用了forEach方法：可以用来遍历数组)

```js
//过渡结束时清除样式
      document.querySelectorAll('.key').forEach(function (key) {
        //transitionend 事件在 CSS 完成过渡后触发
        key.addEventListener('transitionend', transitonHandler)
      });
      
      function transitonHandler(e) {
      //当发生transitionend事件时，propertyName属性返回与转换关联的CSS属性的名称
        if (e.propertyName == 'transform') {
          //移出playing样式
          e.currentTarget.classList.remove('playing')
        }
      }
```

### 代码

```js
<script>
    window.addEventListener('keydown', playSound)

    function playSound(e) {
      //播放音乐
      const audio = document.querySelector(`audio[data-key="${e.keyCode}"]`);
      const key = document.querySelector(`div[data-key="${e.keyCode}"]`);
      if (audio) {
        //改变媒体元素当前播放位置 实现连续触发的效果
        audio.currentTime = 0
        //播放声音
        audio.play()
        //修改按键样式
        key.classList.add('playing')
      }

      //过渡结束时取消样式
      document.querySelectorAll('.key').forEach(function (key) {
        //transitionend 事件在 CSS 完成过渡后触发
        key.addEventListener('transitionend', transitonHandler)
      });
      
      function transitonHandler(e) {
      //当发生transitionend事件时，propertyName属性返回与转换关联的CSS属性的名称
        if (e.propertyName == 'transform') {
          //移出playing样式
          e.currentTarget.classList.remove('playing')
        }
      }
    }
 </script>
```

