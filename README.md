# shadertoy 简单的2d阴影
## 思路:采用画家算法
1. 绘制背景色
2. 绘制光源
3.  找到阴影区域,绘制阴影区域
> <p>1.通过遍历所有的盒子顶点求张角最大的两个点,生成三角片(阴影区域)</p> 
> <p>2.绘制阴影区域</p>
4. 绘制盒子 </br>

<p>（shadertoy里面不能cpu处理阶段代码，本次例子在shadertoy中在每帧中对每个像素都对正方体进行求阴影计算这个地方会浪费很多性能，考虑到2d界面经过剔除物体不会太多所以可以把求阴影算法放到cpu处理然后传入顶点给gpu，可以减小gpu负担从而加快渲染速度。）</p>

https://www.shadertoy.com/view/WdlXW7


# shadertoy RayMarching

RayMarching是光线投射算法中的一种暴力实现,是为了实现射线与几何体求交
## 思路:模拟光线发射,每次走一定距离直到碰到几何体表面

场的概念这里介绍球体距离场:标量和距离有关 </br>

float sdSphere( vec3 p, float s )//离球壳距离越远值越大 </br>
{ </br>
  return length(p)-s; </br>
} </br>

通过场值设定步长(距离越远迈的步子越大) </br>
每根射线走100步基本都会落在球体上.</br>
参考代码:
https://www.jianshu.com/p/46e161b911dd


更多场公式:  </br>
http://www.iquilezles.org/www/articles/distfunctions/distfunctions.htm






