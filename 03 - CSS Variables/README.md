# CSS Variables

这次练习的标题是CSS Variables(变量)，css变量这个功能用的比较少，更多的人会选择使用less或sass。

### 功能

滑动进度条改变背景大小和模糊度，调整背景和字体颜色

### 知识点分析

1.css变量

2.使用forEach遍历

3.setProperty()改变css样式

### 练习过程

首先获取表单元素

```js
let inputs = document.querySelector('.controls input');
```

然后遍历注册事件（这里使用了箭头函数）

```js
//遍历input注册change事件(在 input 失去焦点的时触发)
inputs.forEach(input => input.addEventListener('change', handleUpdate));

//遍历input注册mousemove事件(鼠标移动触发)
inputs.forEach(input => input.addEventListener('mousemove', handleUpdate));
```

设置函数改变css变量

```js
function handleUpdate() {
      //如果this有dataset-sizing就取dataset-sizing的值没有就取空
      let suffix = this.dataset.sizing || '';
      //setProperty()方法接口 为一个声明了CSS样式的对象 设置一个新的值 
	  document.documentElement.style.setProperty(`--${this.name}`, this.value + suffix);
    }
```

在获取html改变css变量时有三种获取方法、

1. document.documentElement
2. document.querySelector('html')
3. document.querySelector('html')

### 整体代码

```js
<script>
    //获取input
    let inputs = document.querySelectorAll('.controls input');

    function handleUpdate() {
      //比较不好的做法
      // switch (this.name) {
      //   case 'spacing':
      //     document.querySelector('img').style.padding = this.value + 'px';
      //     break;
      //   case 'blur':
      //   //filter CSS属性将模糊或颜色偏移等图形效果应用于元素
      //     document.querySelector('img').style.filter = `blur(${this.value}px)`;
      //     break;
      //   case 'base':
      //     document.querySelector('img').style.background = this.value;
      //     document.querySelector('.hl').style.color = this.value;
      //     break;
      //   default:
      //     break;
      // }

      //如果this有dataset-sizing就取dataset-sizing的值没有就取空
      let suffix = this.dataset.sizing || '';
      //setProperty()方法接口 为一个声明了CSS样式的对象 设置一个新的值 
      document.documentElement.style.setProperty(`--${this.name}`, this.value + suffix);
    }

    //遍历input注册change事件(在 input 失去焦点的时触发)
    inputs.forEach(input => input.addEventListener('change', handleUpdate));

    //遍历input注册mousemove事件(鼠标移动触发)
    inputs.forEach(input => input.addEventListener('mousemove', handleUpdate));
  </script>
```

