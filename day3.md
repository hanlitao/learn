 # day03

 ## 过渡 transition 是一个简写属性，书写顺序很重要。第一个可以解析为时间的值会被赋给transition-duration，第二个可以解析为时间的值会被赋值给transition-delay。
 
 * 推荐书写顺序：过渡时间 过渡样式 过渡形式 延迟时间[,过渡时间 过渡样式 过渡形式 延迟时间]
 
 * transition-property 指定过渡属性的名称，默认值all，表示所有可被动画的属性都表现出过渡动画。
 
 * 可以指定多个property
	 * 属性值 
	 * none 没有过渡动画
	 * all 表示所有可被动画的属性都表现出过渡动画
	 * IDENT 属性名称（可以指定多个）
	 
 * transition-duration 以s或ms为单位指定过渡动画所需的时间。
 
 * 默认值为 0s，表示不出现过渡动画，可以指定多个时长，每个时长会被应用到由transition-property指定的对应属性上，如果指定的时长个数小于属性个数，那么时长列表会重复。如果时长列表更长，那么会被裁剪。两种情况下，属性列表保持不变。
 
 * 属性值：以s或ms为单位的数值
 * time 类型。表示过渡属性从旧的值转变到新的值所需要的时间。如果时长是 0s ，表示不会呈现过渡动画，属性会瞬间完成转变。不接受负值。一定要加单位(不能写0 一定要写0s  1s,0s,1s)！
 
 * transition-timing-function 默认值:ease
 * 确立一条速度曲线，因此在整个transition变化过程中，变化速度可以不断改变。
 * 你可以规定多个timing function,通过使用 transition-property属性，可以根据主列表(transition property的列表)给每个CSS属性应用相应的timing function.如果timing function的个数比主列表中数量少，缺少的值被设置为初始值（ease） 。如果timing function比主列表要多，timing function函数列表会被截断至合适的大小。这两种情况下声明的CSS属性都是有效的。
 
 属性值：
         1、ease：（加速然后减速）默认值，ease函数等同于贝塞尔曲线(0.25, 0.1, 0.25, 1.0).
         2、linear：（匀速），linear 函数等同于贝塞尔曲线(0.0, 0.0, 1.0, 1.0).
         3、ease-in：(加速)，ease-in 函数等同于贝塞尔曲线(0.42, 0, 1.0, 1.0).
         4、ease-out：（减速），ease-out 函数等同于贝塞尔曲线(0, 0, 0.58, 1.0).
         5、ease-in-out：（加速然后减速），ease-in-out 函数等同于贝塞尔曲线(0.42, 0, 0.58, 1.0)
         6、cubic-bezier： 贝塞尔曲线
         7、step-start：等同于steps(1,start)
              step-end：等同于steps(1,end)

* transition-delay 默认值：0s；
* 可以指定多个延迟时间，每个延迟将会分别作用于你所指定的相符合的css属性。如果指定的时长个数小于属性个数，那么时长列表会重复。如果时长列表更长，那么该列表会被裁剪。两种情况下，属性列表都保持不变
* 属性值：值以秒（s）或毫秒（ms）为单位，表明动画过渡效果将在何时开始。取值为正时会延迟一段时间来响应过渡效果；取值为负时会导致过渡立即开始。
* 检测过渡是否完成:当过渡完成时触发一个事件，在符合标准的浏览器下，这个事件是transitionend在webkit下是webkitTransitionEnd（每个拥有过渡的属性在其完成过渡时都会触发一次transitionend事件，且在transition完成前设置display：none，事件同样不会被触发）
	
## 注意：

1. transition在元素首次渲染还没有结束的情况下是不会被触发的。要有异步思想（回调、异步、定时器、同步调用，回调注册）.
2. 在绝大部分样式变换中，如果变换函数的位置时，如果变换函数的位置，个数不同时也不会触发。
3. transform只能作用于块级元素。
4. transform的变换是根据基点
5. transform的底层实现是根据矩阵函数，并且矩阵函数就可作为transform的值。
6. 矩阵函数计算根据“-1”原则，并且运算结果不可逆。
7. 变换组合时计算顺序从右往左。

#变换（变形）
 * 旋转 transform：rotate（deg）
	 * 正值：顺时针旋转 rotate（360deg）
	 * 负值：逆时针旋转 rotate（-360deg）
	 * 只能设置单值
	 
 * 平移 transform：translate（tx[,ty]）如果ty没有指定，它的默认值为0。可设置单值，也可以设置双值。正数表示XY轴正向位移，负数为反向位移。设单值表示只X轴位移，Y轴坐标不变，例如transform: translate(100px);等价于transform: translate(100px,0);
	* X方向平移:transform:  translateX(tx)
	* Y方向平移:transform:  translateY(ty) 
	* 二维平移：transform:  translate(tx[, ty])； 如果ty没有指定，它的值默认为0。
	
 * 倾斜 transform:skewX(45deg);
    * X方向倾斜:transform:skewX(angle)
               skewX(45deg):参数值以deg为单位 代表与y轴之间的角度
    * Y方向倾斜:transform:skewY(angle)
               skewY(45deg):参数值以deg为单位 代表与x轴之间的角度
    * 二维倾斜:transform:skew(ax[, ay]);  如果ay未提供，在Y轴上没有倾斜
               skew(45deg,15deg):参数值以deg为单位 第一个参数代表与y轴之间的角度第二个参数代表与x轴之间的角度
               单值时表示只X轴扭曲，Y轴不变，如transform:skew(30deg);等价于transform: skew(30deg, 0);
               考虑到可读性，不推荐用单值，应该用transform: skewX(30deg);。skewY表示只Y轴扭曲，X轴不变  
               正值:拉正斜杠方向的两个角
			   负值:拉反斜杠方向的两个角
 * 缩放（scale）
		transform:scale(2);
		X方向缩放:transform:  scaleX(sx); 
		Y方向缩放:transform:  scaleY(sy);
		二维缩放 :transform:  scale(sx[, sy]);  (如果sy 未指定，默认认为和sx的值相同)  
		要缩小请设0.01～0.99之间的值，要放大请设超过1的值。
		例如缩小一倍可以transform: scale(.5);
		放大一倍可以transform: scale(2);	
		如果只想X轴缩放，可以用scaleX(.5)相当于scale(.5, 1)。
		同理只想Y轴缩放，可以用scaleY(.5)相当于scale(1, .5)
		正值:缩放的程度
		负值:不推荐使用（有旋转效果）
		单值时表示只X轴,Y轴上缩放粒度一样，如transform: scale(2);等价于transform: scale(2,2);

 * 基点变换
  transform-origin
  transform-origin CSS属性让你更改一个元素变形的基点。

 