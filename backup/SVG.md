使用XML描述的矢量文件

位图（像素）基于颜色的描述
矢量图 基于数学的描述

基本图形
<rect> x, y, width, height, rx, ry
<circle>  cx, cy, r
<ellipse> 椭圆 cx, cy, rx, ry
<line> x1, y1, x2, y2
<polyline> 折线 points="x1 y1 x2 y2 x3 y3"
<polygon> 多边形 points="x1 y1 x2 y2 x3 y3"

基本属性
fill, stroke, stoke-width, transform

基本操作API
创建图形
document.createElementNS(ns, tagName)
添加图形
element.appendChild(childElement)
设置/获取属性
element.setAttribute(name, value)
element.getAttribute(name)

SVG中的坐标系统与坐标变换
世界，视野，视窗

<g>创建分组

用户坐标系 User Coordinate ->世界的坐标系
自身坐标系 Current Coordinate ->每个图形元素或分组与生俱来
前驱坐标系 Previous Coordinate ->父容器的坐标系
参考坐标系 Reference Coordinate ->使用其他坐标系来考究自身的情况时使用

坐标变换

线性变换方程
X' = aX + cY + e  
Y' = bX + dY + f
变换矩阵，记为M
[a  c  e]
[b  d  f]
[0  0  1]

matrix(<a>,<b>,<c>,<d>,<e>,<f>)

<radialGradient>
<pattern>笔刷

<path> 大写绝对位置，小写上次结束的相对位置

移动和直线命令

M(x,y)+ 移动画笔，后面如果有重复参数，当做L命令处理
L(x,y)+ 绘制直线到指定位置
H(x)+ 绘制水平线到指定的x位置
V(y)+ 绘制竖直线到指定的y位置
m、l、h、v使用相对位置绘制

弧线命令
A(rx, ry, xr, laf, sf, x, y)
rx -> radius-x -> 弧线所在椭圆的x半轴长
ry -> radius-y -> 弧线所在椭圆的y半轴长
xr -> xAxis-rotation -> 弧线所在椭圆的长轴角度
laf -> large-arc-flag -> 是否选择弧长较长的那一段弧
sf -> sweep-flag -> 是否选择逆时针方向的那一段弧
x,y -> 弧的终点位置

<textPath> 路径文本 xlink:href

<use> 创建图形引用 xlink:href="#id"
<clip> 裁切图形 clip-path="url(#clip-id)"
<mask> 创建蒙版 mask="url(#mask-id)"

<defs> fill="url(#id)"

<animate> attributeType attributeName dur from to repeatCount="indefinite"

<animateTransform> type from to duration

<animateMotion>