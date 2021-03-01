## 容器属性

### flex-direction属性 

1. 翻译：
   1. direction[dəˈrekʃn] : 方向 ；
   2. row[rəʊ , raʊ] : 行; 
   3. reverse：颠倒；
   4. column [ˈkɒləm] ：柱（竖）；
2. 用于决定主轴的方向（即项目的排列方向）。
3. 取值：row(默认) | row-reverse | column | column-reverse
4. 该属性可取4个值： 
   1. row(默认)，即横向排列，项目排列顺序为正序1-2-3；
   2. row-reverse同为横向排列，但项目顺序为倒序3-2-1;
   3. column 与row相反，为纵向排列，项目顺序为正序1-2-3;
   4. column-reverse同为纵向排列，项目顺序为倒序3-2-1。

### flex-wrap属性

2. 用于控制项目是否换行，nowrap表示不换行；
3. 取值：nowrap(默认) | wrap | wrap-reverse
4. 该属性可取两个值： 
   1. wrap表示换行，即项目不会等分容器宽度，而是根据自身宽度进行排列，如果超出父容器宽度则自然换行。
   2. wrap-reverse同样表示换行，需要注意的是第一排会紧贴容器底部，而不是我们想象的项目6紧贴容器顶部，效果与wrap相反。

### flex-flow属性

1. flex-flow属性是flex-deriction与flex-wrap属性的简写集合，默认属性为row nowrap，即横向排列，且不换行，如果需要控制项目排列与换行，推荐使用此属性，而非单独写两个。

### justify-content属性

1. 用于控制项目在横轴的对齐方式，
2. 取值：flex-start(默认) | flex-end | center | space-between | space-around
3. 假设主轴为从左到右
   1. flex-start即左对齐(默认)，
   2. center 为居中，
   3. flex-end为右对齐，
   4. space-between为两端对齐，项目之间的间隔都相等
   5. space-around为每个项目两侧的间隔相等。所有，项目之间的间隔比项目与边框的间隔大一倍



### align-items 属性

1. 用于定义项目在交叉轴上如何对齐

2. 取值：flex-start | flex-end | center | baseline | stretch;

3. 假设主轴从上到下：

   1. stretch(默认值): 如果项目未设置高度或设为auto，将占满整个容器的高度

   2. flex-start: 交叉轴起点对齐；

   3. flex-end: 交叉轴的终点对齐；

   4. center: 交叉轴的终点对齐；

   5. baseline: 项目的第一行文字的基线对齐；

      

### align-content属性

1. 用于定义了多根的对齐方式。如果项目只有一根轴线，该属性不起作用。

2. 取值： flex-start | flex-end | center | space-between | space-around | stretch;

3. 该属性可能取6个值：

   1. stretch: (默认值): 轴线占满整个交叉轴

   2. flex-start: 与交叉轴的起点对齐；

   3. flex-end: 与交叉轴的终点对齐；

   4. center： 与交叉轴的终点对齐；

   5. space-between: 与交叉轴的两端对齐，轴线之间的间隔平均分布；

   6. space-around: 每根轴线两侧的间隔都相等。所以，轴线之间的间隔比轴线与边框的间隔大一倍。

      

​		

​	

​		



