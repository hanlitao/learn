# day1

## <-- css基本问题 -->
 * 	1.css的全称是什么？
	层叠样式表(英文全称：Cascading Style Sheets
 *	2.样式表的组成？
	选择器，声明块，属性和属性值组成的键值对
 *	3.浏览器读取编译css的顺序？
		从右到左

## 1. LVHA 
* **由于a标签的:link和:visited可以覆盖了所有a标签的状态，所以当:link，:visited，:hover，:active同时出现在a标签身上时 :link和:visited不能放在最后！！！**
* 		链接伪类		注意:link，:visited，:target是作用于链接元素的！
				:link		表示作为超链接，并指向一个未访问的地址的所有锚
				:visited	表示作为超链接，并指向一个已访问的地址的所有锚
				:target 	代表一个特殊的元素，它的id是URI的片段标识符
*		动态伪类		注意:hover，:active基本可以作用于所有的元素！
				:hover		表示悬浮到元素上
				:active		表示匹配被用户激活的元素（点击按住时）
*				隐私与:visited选择器
					只有下列的属性才能被应用到已访问链接：
						color
						background-color
						border-color
*		表单相关伪类
				:enabled	匹配可编辑的表单
				:disable	匹配被禁用的表单
				:checked	匹配被选中的表单
				:focus		匹配获焦的表单

## 2. :target 代表一个元素id必须为uri  
* 浏览器地址栏末尾#后边
 ![](https://i.imgur.com/sBfiRdg.png)
 
## 3. css实现单选按钮（面试题）
* 思路：利用单选按钮分组（设置相同name属性）外部包裹lable
标签将radio移除可视区域（定位实现），添加一个span兄弟元素，warp设置overlfow：hidden
 * 代码实现：`<html>
	<head>
		<meta charset="UTF-8">
		<title></title>
		<style type="text/css">
			*{
				margin: 0;
				padding: 0;
			}
			label{
				position: relative;
				float: left;
				width: 100px;
				height: 100px;
				border: 2px solid;
				overflow: hidden;
				border-radius: 50%;
			}
			label > span{
				position: absolute;
				left: 0;
				top: 0;
				bottom: 0;
				right: 0;
			}
			input{
				position: absolute;
				left: -50px;
				top: -50px;
			}
			input:checked + span{
				background: pink;
			}
		</style>
	</head>
	<body>
		<label >
			<input type="radio" name="atguigu" />
			<span></span>
		</label>
		<label >
			<input type="radio" name="atguigu" />
			<span></span>
		</label>
		<label >
			<input type="radio" name="atguigu" />
			<span></span>
		</label>
	</body>
</html>`
 * 最终效果
![](https://i.imgur.com/WCwJ5Zg.png)

## 4. css实现选项卡(面试题)
 * 思路：利用:target伪元素
  * 代码实现
![](https://i.imgur.com/CreOBFK.png)

## 5.:nth-child 和 ：nth-of-type 区别？
 * 					#wrap ele:nth-child(index)		表示匹配#wrap中第index的子元素 这个子元素必须是ele
 *					#wrap ele:nth-of-type(index)	表示匹配#wrap中第index的ele子元素
 *  **除此之外:nth-child和:nth-of-type有一个很重要的区别,nth-of-type以元素为中心！！！** 
 
## 6. :not(面试题)
* 实现最后一个a不添加右边框
    `div > a:not(:last-of-type) {
	border-right: 1px solid red;
}`

![](https://i.imgur.com/yawEJnx.png)
## 7. :empty
* <div></div> 选中内容为空，空到不能有任何空格。

## 8. 一个元素的伪元素只能有两个 ：：before和：：after
## 9. opacity 属性不可以继承，但会影响子元素。（内容全部透明）
* 背景透明文字不透明用rgba（）属性

## 10. 移动端css实现模糊背景
* 代码实现：`<html>
	<head>
		<meta charset="UTF-8">
		<meta name="viewport" content="width=device-width,initial-scale=1.0,user-scalable=no" />
		<title></title>
		<style type="text/css">
			*{
				margin: 0;
				padding: 0;
			}
			#wrap{
				height: 100px;
				background: rgba(0,0,0,.5);
				position: relative;
			}
			#wrap #bg{
				position: absolute;
				left: 0;
				right: 0;
				top: 0;
				bottom: 0;
				background: url(img/avatar.jpg) no-repeat;
				background-size:100% 100% ;
				z-index: -1;
				filter: blur(10px);
			}
			img{
				margin: 24px 0 0 24px;
			}
		</style>
	</head>
	<body>
		<div id="wrap">
			<img src="img/avatar.jpg" width="64px" height="64px"/>
			<div id="bg"></div>
		</div>
	</body>
</html>
`
* 效果图
![](https://i.imgur.com/BllhUn2.png)

## 11.文字溢出显示省略号（面试题）
* 核心代码：`	
		width: 200px;
		height: 200px;
        display：block；
		border: 1px solid;
		margin: 0 auto;
		white-space: nowrap;
		overflow: hidden;
		text-overflow: ellipsis;
 **盒子大小不能依靠内容撑开，隐含属性display：block；**

## 12.css声明的优先级
* 选择器的特殊性
    选择器的特殊性由选择器本身的组件确定，特殊性值表述为4个部分，如    0,0,0,0
			一个选择器的具体特殊性如下确定：
			       1.对于选择器中给定的ID属性值，加 0,1,0,0
			       2.对于选择器中给定的各个类属性，属性选择，或伪类，加 0,0,1,0
			       3.对于选择器中的给定的各个元素和伪元素，加0,0,0,1
			       4.通配符选择器的特殊性为0,0,0,0
			       5.结合符对选择器特殊性没有一点贡献
			       6.内联声明的特殊性都是1,0,0,0
			       7.继承没有特殊性
 
				特殊性 1,0,0,0 大于所有以0开头的特殊性(不进位)
				选择器的特殊性最终都会授予给其对应的声明
				如果多个规则与同一个元素匹配，而且有些声明互相冲突时，特殊性越大的越占优势
 
				注意：id选择器和属性选择器
				      div[id="test"]（0,0,1,1） 和 #test（0,1,0,0）   
*	重要声明
			有时某个声明比较重要，超过了所有其他声明，css2.1就称之为重要声明
			并允许在这些声明的结束分号之前插入  !important  来标志
			必须要准确的放置  !important 否则声明无效。 
			!important 总是要放在声明的最后，即分号的前面
			 
			 标志为 !important的声明并没有特殊的特殊性值，不过要与非重要声明分开考虑。
			 实际上所有的重要声明会被浏览器分为一组，重要声明的冲突会在其内部解决
			 非重要声明也会被分为一组，非重要声明的冲突也会在其内部解决
			 如果一个重要声明与非重要声明冲突，胜出的总是重要声明
*	继承
			继承没有特殊性，甚至连0特殊性都没有
			0特殊性要比无特殊性来的强
*	来源
			css样式的来源大致有三种
			  创作人员
			  读者
			  用户代理   
			 
*	权重：
			   读者的重要声明
			   创作人员的重要声明
			   创作人员的正常声明
			   读者的正常声明
			   用户代理的声明
*	层叠
			1.找出所有相关的规则，这些规则都包含一个选择器
		    2.计算声明的优先级
		               先按来源排序
		               在按选择器的特殊性排序
		               最终按顺序
	`

# 13. 自定义字体
* 			@font-face {
				font-family:"Damu";
				src: url(font/BAUHS93.TTF);
			}
			
 * 注意自定义字体不能定义在标签内部
 

 ###day01
	1.Cascading  style sheets
	2.样式表的组成
		规则
			选择器+声明块
					声明
						CSS合法的属性名+属性值
	3.浏览器渲染样式表的顺序
		从右往左
	4.选择器
		基本选择器及其扩展
			* . # 后代 组合（#test.pink）
			> + ~ 分组（，结合符）
		属性选择器
			存在与值 属性选择器
				[attr] [attr="val"] [attr~="val"](只认空格)
			子串值 属性选择器
				^ $ * |(val val-)
		伪类与伪元素选择器
			链接伪类
				:link :visited :target(css实现选项卡)
			动态伪类
				:hover :active(lvha)
			表单伪类
				:disabled :enabled	:checked(自定义单选按钮) :focus
			结构性伪类
				ele:nth-child(index)
				ele:nth-of-type(index) 以元素为中心
				
				区别：
					1.nth-child找到第index个子元素  这个子元素必须满足ele的规则
					  nth-of-type找到底index个ele子元素
					2.nth-of-type以元素为中心
				注意：
					index可以是变量n（只能是n  0到正无穷）
							odd：奇数
							even：偶数	
			伪元素
				::after
				::before
				
		CSS声明的优先级
			层叠
				先按来源进行刷选
				如果来源相同，按选择器的特殊性继续刷选
				选择器的特殊性如果相同，按顺序继续刷选
	5.自定义字体
		@font-face
		字体图标
			1.制作一套矢量图
			2.将矢量图与字符进行绑定
			3.使用工具或者站点生成一套字体
			4.最终使用
		 字体兼容处理网站
	       https://www.fontsquirrel.com/tools/webfont-generator
	    icomoon字体图标
	       https://icomoon.io/#home
	
	6.文本新增样式
		文本阴影
		怎么溢出显示省略号
			white-space=no-wrap
			overflow=hidden
			text-overflow=ellipsis
			包裹区域必须不能让子元素撑开
			