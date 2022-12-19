[TOC]

# animation库

## 引入

#### npm引入

```js
// 全局引入样式
npm install animate.css --save
import 'animate.css';
```

#### link引入

```html
<link
    rel="stylesheet"
    href="https://cdnjs.cloudflare.com/ajax/libs/animate.css/4.1.1/animate.min.css"
  />
```



## 使用方法

### 基本使用

```html
// 需要添加 animate__animated 类名前缀 后面再添加需要引入的动画
<div class="animate__animated animate__bounce"></div>
```

### 在css中使用

```css
// 需要在 动画样式css 里面使用  i给动画属性用的i
.animate__animated.animate__bounce{
  --animate-duration: 800ms; // 动画持续时间
	--animate-delay: 0.9s; // 延迟
} 
```

```css
// 直接在 css 中使用 i给class样式用的i
.my-element{
   	animation: bounce; // 反弹动画
  	animation-duration: 2s;  // 持续时间
}
```

### 在js中使用

```js
// 全局使用 动画都是一秒完成的 
document.documentElement.style.setProperty('--animate-duration', '2s'); // 持续两秒,减慢运动速度
document.documentElement.style.setProperty('--animate-duration', '.5s'); // 持续 0.5秒,加快运动速度
```

```js
// 此类方法可以与js做一些交互
const element = document.querySelector('.my-element');
element.classList.add('animate__animated', 'animate__bounceOutLeft');
```

### 添加事件

```js
const element = document.querySelector('.my-element');
element.classList.add('animate__animated', 'animate__bounceOutLeft');
element.addEventListener('animationend', () => {
  // do something
});

```

or change its duration:

```js
const element = document.querySelector('.my-element');
element.style.setProperty('--animate-duration', '0.5s');
```

```js
// 封装方法
const animateCSS = (element, animation, prefix = 'animate__') =>
  // We create a Promise and return it
  new Promise((resolve, reject) => {
    const animationName = `${prefix}${animation}`;
    const node = document.querySelector(element);

    node.classList.add(`${prefix}animated`, animationName);

    // When the animation ends, we clean the classes and resolve the Promise
    function handleAnimationEnd(event) {
      event.stopPropagation();
      node.classList.remove(`${prefix}animated`, animationName);
      resolve('Animation ended');
    }

    node.addEventListener('animationend', handleAnimationEnd, {once: true});
  });

// or
animateCSS('.my-element', 'bounce').then((message) => {
  // Do something after the animation
});
```



### 直接添加在class类名中

```html
<div class="animat__animated animate__xxxxxxx animate__delay-1s"></div>
```

> 固定时间属性(动画的快慢)
>
> ```css
> // 时间固定了 
> 属性								展示效果时间
> animate__slow				2s			// 慢
> animate__slower			3s
> animate__fast				800ms  	
> animate__faster			500ms 	// 很快
> ```
>
> 

> 延迟
>
> ```html
> // 自定义时间
> animate__delay-x  // 延迟 后面能添加时间
> ```
>
> 

> ​	执行次数
>
> ```html
> 属性								次数
> animate__repeat-1		1
> animate__repeat-2		2
> animate__repeat-3		3
> animate__infinite		infinite // 无限循环
> ```
>
> 
>
> 

### 方法扩展

> 全局改变
>
> ```css
> :root {
> --animate-duration: 800ms; // 持续
> --animate-delay: 0.9s; // 延迟
> }
> ```
>
> 局部css改变
>
> ```css
> .animate__animated.animate__bounce {
> --animate-duration: 2s; 
> }
> ```
>
> 

> 适配浏览器
>
> ```html
> <body>
> <main class="animate__animated animate__fadeInLeft">
>  <!-- Your code -->
> </main>
> </body>
> 
> ```

# react-transition-group

## 引入

### npm引入

```js
npm i react-transition-group -S

```

## 使用方法

```js

```

# animation属性

### 常用

~~~css
// 简写
animation: 动画名称 动画持续时间 动画运动方式 动画开始延迟时间 
动画应用次数 动画结束后是否原路返回 动画前后的状态 
;
@keyframes 定义关键帧 from to 或者 %0 %100

~~~

```css
animation-name:动画名称
animation-duration:动画时间
animation-timing-function:动画曲线
{
    liner:匀速
    ease: 开始和结束慢速
    ease-in: 开始慢速
    ease-out:结束慢速
    ease-in-out:开始和结束慢
    steps:动画步数
}
animation-delay:动画延迟
animation-iteration-count:动画播放次数 n/infinite
animation-direction:动画是否原路返回 normal(默认不返回)/alternate(返回)
animation-play-state:动画状态 paused(停止)/running(运动)



```



# transform

## 属性(固定值)

```css
transfrom-origin:left top;left bottom;center center;50px 50px;设置变形的中心点  --默认 center center

scale(0.5/2):缩放转换
scale(x,y)：同时缩放
scaleX()：只操作 X 轴
scaleY()：只操作 Y 轴

rotate(deg角度):旋转 - 默认 - 面朝屏幕旋转 
retateX
retateY
retateZ(不能是百分比) == rotate 默认朝屏幕转

translate(x,y):移动
translateX(x)：仅移动x轴
translateY(y)：仅移动y轴
translateZ : 朝屏幕-与人眼垂直
translate3d : 不清楚

skew()：倾斜








```

## 阴影

```css
box-shadow: -8px -8px 15px rgba(255, 255, 255, 1),
8px 8px 25px rgba(0, 0, 0, 0.15);

```



# react-transition-group

## Transition(通过in控制动画)

```css
// 使用方法 主要是通过改变 css 属性变成动画
const transitionStyles = {
  entering: { opacity: 1 }, // 进场与离场
  entered: { opacity: 1 },
  exiting: { opacity: 0 },
  exited: { opacity: 0 },
};
 <Transition
	in={inProp}
	timeout={duration}
	// 钩子,可以再各个阶段执行各个函数
	onEnter={onEnter}
	onEntering={onEntering}
	onEntered={onEntered}
	onExit={onExit}
	onExiting={onExiting}
	onExited={onExited}
	>
        {(state) => {   // 这里是最重要的，state的值会以此变化上面的状态
          return ( // 返回你的组件
            <button style={{ ...defaultStyle, ...transitionStyles[state]}}>
              {state}
            </button>
          );
        }}
 </Transition>
<button onClick={() => setInProp(!inProp)}>
	{inProp ? "hide" : "show"}   
</button>

```

## CSSTransition(通过in控制动画)

```css
//使用方法 通过改变 class 类名实现动画
<CSSTransition in={inProp} timeout={duration} classNames="items">
	<button className="fade">按钮</button>
</CSSTransition>
<button onClick={() => setInProp(!inProp)}>
	{inProp ? "hide" : "show"} // 通过 inProp 的状态控制进场与离场
</button>
再通过改变 css 样式实现动画

```

```css
// 自己本身默认
.fade{
    background-color: black;
}
// 进场， 从无到有
.items-enter {
    opacity: .1;
    background-color: orange;
}
.items-enter-active {
    opacity: 1;
    transition: 1s;
    background-color: orchid;
}
.items-enter-done {
    opacity: 1;
    background-color: palegreen;
}
// 离场， 从有到无
.items-exit {
    opacity: 1;
    background-color: gray;
}
.items-exit-active {
    opacity: .1;
    transition: 1s;
    background-color: red;
}
.items-exit-done {
    opacity: .1;
    background-color: aqua;
}

```

## SwitchTransition(无in有key)

```css
// 使用场景，控制状态转换之间的渲染时，可以用到他，例如组件切换 state?<App/>:<Child/>
// 两个组件切换时会等待上一个的 离场 动画结束完后，再执行另一个组件的进场动画
      <SwitchTransition>
        <CSSTransition
			key={state}  // 通过 key 是否发生改变来控制动画的执行
			timeout={duration} 
			classNames="items">
          <button className="fade" onClick={()=>setState(!state)}>
				{state?<App/>:<Child/>}
          </button>
        </CSSTransition>
      </SwitchTransition>


```

# TransitionGroup

```css
// 同样是通过 key 值的变化来执行动画，有进场和离场动画  
	<TransitionGroup>
        {num.map((item) => {
          return <CSSTransition
            key={item}
            timeout={duration}
            classNames="items"
          >
              <div key={item}>
                  <li>{item}</li>
                  <button onClick={()=>{
                      setNum(num.filter(key=>key!==item))
                  }}>点击删除</button>
              </div>
          </CSSTransition>;
        })}
      </TransitionGroup>

```

