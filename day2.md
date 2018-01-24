  #day02

## 水平居中方案
 *  `#test{
				position: absolute;
				left: 0;
				right: 0;
				bottom: 0;
				top: 0;
				margin: auto;
				width: 100px;
				height: 100px;
				background: pink;
				text-align: center;
				line-height: 100px;
				box-shadow: -10px -10px 10px 0px black , 20px 20px 10px -10px deeppink;
			}`

 * 适用于图片 原理：对准基线，inline-block元素对齐参照高度大的（必须是inline-block）
![](https://i.imgur.com/5HzRQXL.png)

 * 方案3 `div{
				width: 200px;
				height: 200px;
				padding: 50px;
				background: pink;
				position: absolute;
				left: 50%;
				top: 50%;
				margin-left: -100px;
				margin-top: -100px;
				box-sizing: border-box;
			}`
   
#盒模型新增样式
1. 盒模型阴影
 * box-shadow 默认值：none 不可继承（x,y,blur-radius（0），spread-radius（0），color）
 * 值inset outset默认

2. 倒影
 * -webkit-box-reflect（不是css3属性）
 * 默认值：none 不可继承
 * 值（必须是123的顺序）
	* 方向：above，below，right，left
	* 倒影的距离：长度单位
	* 渐变

3. resize css属性允许你控制一个元素的可调整大小性。
（一定配合overflow：auto使用）
 * 默认值：none 不可继承
 * 值：
   	* none：元素不能被用户缩放
   	* both：允许用户在水平和垂直方向上调整元素大小
   	* horizontal：允许用户在水平方向上调整元素的大小
   	* vertical:允许用户在垂直方向上调整元素的大小
   
4. box-sizing
 * border-box
 * content-box（默认）

# 新增UI样式

1. 圆角
 * border-radius 默认值：0 不可继承
 * 值：固定的px值定义圆形半径或椭圆的半长轴，半短轴。不能用负值
       使用百分数定义圆形半径或椭圆的半长轴，半短轴。水平半轴相对于盒模型的宽度；垂直半轴相对于盒模型的高度。不能用负值
2. 边框图片
 * border-image-source 属性定义使用一张图片来代替边框样式；如果只为none，则仍然使用border-style 定义的样式。
 	* 默认值：none   不可继承
 * border-image-slice 属性会通过规范将 border-image-source  的图片明确的分割为9个区域：四个角，四边以及中心区域。并可指定偏移量
 ![](https://i.imgur.com/9yie91z.jpg)
 	* 默认值100% 不可继承，值的百分比参照与image本身
 * border-image-repeat 定义图片如何填充边框。或为单个值，设置所有的边框；或为两个值，分别设置水平与垂直的边框。 
 * 默认值：stretch  不可继承
 * 值：
	* stretch （拉伸）
	* repeat，round（平铺）
 * border-image-width 定义图像边框宽度。 
	* 默认值：1   不可继承
 * border-image-outset属性定义边框图像可超出边框盒的大小
	* 默认值：0  不可继承
	* 正值： 可超出边框盒的大小
3. 背景
 * background-color 会设置元素的背景色
	* 默认值：  transparent    不可继承
 * background-image属性用于为一个元素设置一个或多个背景图像，图像在绘制时，以z轴方向堆叠的方式进行。先指定的图像会在之后指定的图像上面进行绘制。
 * 注意：background-color会在image之下进行绘制，边框和内容会在image之上进行绘制 
	* 默认值：none   不可继承
 * background-repeat CSS 属性定义背景图像的重复方式。背景图像可以沿着水平轴，垂直轴，两个轴重复，或者根本不重复。
	* 默认值：repeat 不可继承
 
 * 值： 
	* repeat-x   =    repeat no-repeat
    * repeat-y   =    no-repeat repeat
    * repeat      =    repeat repeat 
    * no-repeat  =    no-repeat no-repeat 
  第一个值代表水平方向。
  第二个值代表垂直方向。
 * 指定背景位置的初始位置
	* 默认值：0% 0%   不可继承
 * 值：
   百分比：参照尺寸为背景图片定位区域的大小减去背景图片的大小  
          第一个值：元素在水平方向的位移
          第二个值：元素在垂直方向的位移 
 * background-attachment 决定背景是在视口中固定的还是随包含它的区块滚动的。
 	* 默认值：scroll 不可继承 
 
 * 值：
   fixed
       此关键字表示背景相对于视口固定。即使一个元素拥有滚动机制，背景也不会随着元素的内容滚动 。
   scroll
       此关键字表示背景相对于元素本身固定， 而不是随着它的内容滚动
 ### css3
 * background-origin
 * 设置背景的渲染的起始位置
       border-box
       padding-box
       content-box
 * background-clip
 * 设置背景裁剪位置
 * background-size
 * background-size 设置背景图片大小
	* 默认值：auto auto  不可继承
 
 * 值：
   百分比：  指定背景图片相对背景区（background positioning area）的百分比。背景区由background-origin设置，默认为盒模型的内容区与内边距
   auto：  以背景图片的比例缩放背景图片。
 * 注意：
  单值时，这个值指定图片的宽度，图片的高度隐式的为auto
  两个值: 第一个值指定图片的宽度，第二个值指定图片的高度
 * background   
 * background 是CSS简写属性，用来集中设置各种背景属性。background 可以用来设置一个或多个属性:background-color, background-image, background-position, background-repeat, background-size, background-attachment。 
 * 默认值：    不可继承
background-image: none
background-position: 0% 0%
background-size: auto auto
background-repeat: repeat
background-origin: padding-box
background-clip: border-box
background-attachment: scroll
background-color: transparent
 顺序无关   
4. 渐变（是图片类型）
 * 线性渐变
	* linear-gradient(角度,red,blue);
	* -颜色节点的分布（第一个不写为0%，最后一个不写为100%）
            linear-gradient(red 长度或者百分比,blue 长度或者百分比);
	* -重复渐变
           repeating-linear-gradient(60deg,red 0,blue 30%);
 * 径向渐变
	* radial-gradient() 函数创建一个<image>，用来展示由原点（渐变中心）辐射开的颜色渐变
	* -默认均匀分布
    radial-gradient(red,blue);
	* -不均匀分布
    radial-gradient(red 50%,blue 70%);
	* -改变渐变的形状
    radial-gradient(circle ,red,blue)
    circle
    ellipse（默认为椭圆）
	* -渐变形状的大小
    radial-gradient(closest-corner  circle ,red,blue)
    closest-side   最近边
    farthest-side  最远边
    closest-corner 最近角
    farthest-corner 最远角  
	* -改变圆心
    radial-gradient(closest-corner  circle at 10px 10px,red,blue);  

#注意: 
 * 描边、倒影、图片按文字剪切 —webkit
 * 隐藏滚动条
    heml,body{
     overflow: hieden;
     height: 100%;} 
   任何时候滚动条都不可能出现在html上
 * 移动端border-radius 最好用px
 * 用绝对定位模拟规定定位：`<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title></title>
		<style type="text/css">
			*{
				margin: 0;
				padding: 0;
			}
			html{
				height: 100%;
				overflow: hidden;
			}
			body{
				height: 100%;
				overflow: hidden;
			}
			#wrap{
				height: 100%;
				border: 1px solid deeppink;
				overflow: auto;
			}
			#pink{
				position: absolute;
				left: 0;
				top: 0;
				width: 200px;
				height: 200px;
				background: pink;
			}
		</style>
	</head>
	<body>
		<!--初始包含块：是一个视窗大小的矩形！！-->
		<div id="wrap">
			<div id="pink">
				
			</div>
			<div id="test" style="height: 3000px;">
			
			</div>
		</div>
	</body>
</html>
`
 * background-position %是相对于（包含他的边框-图片大小）*100%
 * background-attcuhment 存在性能问题
 * 默认情况下背景图片是从padding-box开始绘制，从border-box开始剪裁
 * 渐变式图片类型
 * 径向渐变默认值从最远角开始
 * 绝对定位模拟固定定位`<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title></title>
		<style type="text/css">
			*{
				margin: 0;
				padding: 0;
			}
			html{
				height: 100%;
				overflow: hidden;
			}
			body{
				height: 100%;
				overflow: hidden;
			}
			#wrap{
				height: 100%;
				border: 1px solid deeppink;
				overflow: auto;
			}
			#pink{
				position: absolute;
				left: 0;
				top: 0;
				width: 200px;
				height: 200px;
				background: pink;
			}
		</style>
	</head>
	<body>
		<!--初始包含块：是一个视窗大小的矩形！！-->
		<div id="wrap">
			<div id="pink">
				
			</div>
			<div id="test" style="height: 3000px;">
			
			</div>
		</div>
	</body>
</html>
`