# JS时钟

### 功能

根据系统时间实时显示

### 知识点分析

1.获取时针，分针，秒针

2.使用Date()

3.计算时分秒，设置定时器

4.改变各个指针的旋转角度

### 练习过程

1.首先获取元素（表盘上的指针）

```js
//获取时、分、秒针
let second = document.querySelector('.second-hand');
let min = document.querySelector('.min-hand');
let hour = document.querySelector('.hour-hand');
```

2.封装设置指针函数，使用Date()，获取时分秒，并计算旋转的角度

```js
function setClock() {
	let now = new Date()
	let secondDeg = now.getSeconds() * 6 //一秒钟走6° 360/60
	let minDeg = now.getMinutes() * 6 + now.getSeconds() * 6 / 60 //一分钟走6° 360/60
	let hourDeg = now.getHours() * 30 + now.getMinutes() * 30 / 60 //一小时走30° 360/12
}
```

3.改变时、分、秒针的旋转角度

```js
function setClock() {
	let now = new Date()
	let secondDeg = now.getSeconds() * 6 //一秒钟走6° 360/60
	let minDeg = now.getMinutes() * 6 + now.getSeconds() * 6 / 60 //一分钟走6° 360/60
	let hourDeg = now.getHours() * 30 + now.getMinutes() * 30 / 60 //一小时走30° 360/12
    second.style.transform = `rotate(${secondDeg}deg)`;
	min.style.transform = `rotate(${minDeg}deg)`;
	hour.style.transform = `rotate(${hourDeg}deg)`;
}

```

4.初始化画面

```js
 //初始化画面
      setClock()
```

5.设置定时器

```js
 //设置定时器
      setInterval(setClock,1000)
```

