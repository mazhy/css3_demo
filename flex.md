#flex
##	容器
###	容器的排列方向
+	flex-direction
+	控制主轴是哪一根，控制主轴的方向
	-	row;		从左往右的x轴	
	-	row-reverse;从右往左的x轴
	-	column;		从上往下的y轴
	-	column-reverse;从下往上的y轴
	
###富裕空间的管理
+	只决定富裕空间的位置，不会给项目区分配空间
	-	主轴
		+	justify-content
			-	flex-start：		在主轴的正方向
			-	flex-end:		在主轴的反方向
			-	center：			在两边
			-	space-between：	在项目之间
			-	space-around：  在项目两边			
	-	侧轴
		+	align-items
			-	flex-start：在侧轴的正方向
			-	flex-end：    在侧轴的反方向
			-	center：		在两边
			-	baseline    基线对齐
			-	stretch		等高布局（项目没有高度）
    +	align-self（优先级高）
      - 定义flex子项单独在侧轴（纵轴）方向上的对齐方式
      - auto	默认值。元素继承了它的父容器的 align-items 属性。如果没有父容器则为 "stretch"。	
      - stretch	 元素被拉伸以适应容器。 如果指定侧轴大小的属性值为'auto'，则其值会使项目的边距盒的尺寸尽可能接近所 在行的尺寸，但同时会遵照'min/max-width/height'属性的限制。
      - center	元素位于容器的中心。弹性盒子元素在该行的侧轴（纵轴）上居中放置。（如果该行的尺寸小于弹性盒子元素的尺寸，则会向两个方向溢出相同的长度）。
      - flex-start	元素位于容器的开头。弹性盒子元素的侧轴（纵轴）起始位置的边界紧靠住该行的侧轴起始边界。
      - flex-end	元素位于容器的结尾。弹性盒子元素的侧轴（纵轴）起始位置的边界紧靠住该行的侧轴结束边界。
      - baseline 元素位于容器的基线上。 如弹性盒子元素的行内轴与侧轴为同一条，则该值与'flex-start'等效。其它情况下，该值将参与基线对齐。
      - initial	设置该属性为它的默认值。请参阅 initial。
      - inherit	从父元素继承该属性。请参阅 inherit。

##	项目
###	弹性空间管理
+	flex-grow：弹性因子（默认值为0）
+	原则
	-	可用空间 = (容器大小 - 所有相邻项目flex-basis的总和)
	   +	400 - 5*50 = 150
	-	可扩展空间 = (可用空间/所有相邻项目flex-grow的总和)
	   +	150 / 8 = 18.75
	-	每项伸缩大小 = (伸缩基准值 + (可扩展空间 x flex-grow值))
		+	50 + 18.75*4 = 125
					
				
###	容器
+	flex-wrap：控制的是侧轴的方向
	-	nowrap 不换行
	-	wrap   侧轴方向由上而下 			（flex-shrink失效）
	-	wrap-reverse 侧轴方向由下而上 	（flex-shrink失效）
+	align-content：多行/列时侧轴富裕空间的管理（把多行/列看成一个整体）
+	flex-flow：flex-direction和flex-wrap的简写属性
	-	本质上控制了主轴和侧轴分别是哪一根，以及他们的方向
+	项目
	-	order:控制项目的排列顺序
	-	align-self：项目自身富裕空间的管理
	-	flex-shrink：收缩因子（默认值为1）
	-	flex-basis：伸缩规则计算的基准值（默认拿width或height的值）
	
###	伸缩规则
+	flex-basis: 设置项目的初始长度
  - number	一个长度单位或者一个百分比，规定灵活项目的初始长度。
  - auto	默认值。长度等于灵活项目的长度。如果该项目未指定长度，则长度将根据内容决定。
  - initial	设置该属性为它的默认值。请参阅 initial。
  - inherit	从父元素继承该属性。请参阅 inherit。
+	flex-grow（默认值为0）
	-	可用空间 = (容器大小 - 所有相邻项目flex-basis的总和)
	-	可扩展空间 = (可用空间/所有相邻项目flex-grow的总和)
	-	每项伸缩大小 = (伸缩基准值flex-basis + (可扩展空间 x flex-grow值))
+	flex-shrink（默认值为1）
	-	计算收缩因子与基准值乘的总和  
		+	var a = 每一项flex-shrink*flex-basis之和
	-	计算收缩因数
		+	收缩因数=（项目的收缩因子*项目基准值）/第一步计算总和   
		+	var b =  (flex-shrink*flex-basis)/a
	-	移除空间的计算
		+	移除空间= 项目收缩因数 x 负溢出的空间 
	   +	var c =    b * 溢出的空间      
	