# Tiny Ray Tracer
## Overview
This project is a tiny ray tracer in C++ inspired by [Dmitry V. Sokolov](https://github.com/ssloy).<br>
I rewrote it and added some more functions along with a more detailed Chinese/English version tutorial.
## English Version Tutorial
## Chinese Version Tutorial
### 预备知识
这个模型涉及到了Blinn-Phong着色模型和一定的有关Whitted Style Ray Tracing/Path Tracing的知识，本文中涉及到必要的原理解释和相关内容来帮助读者理解代码，同时也建议读者观看闫令琪老师的GAMES101课程，其中设计这部分知识的课程是lecture 7-8，13-16。
#### Blinn-Phong着色模型
**首先需要注意：Blinn-Phong模型是一个经验模型，并不是符合物理和规律的物理模型，所以在很多场景中会有比较明显的或者是不太明显的问题（总归有一定的不完善嘛）。在我们的项目中实际上也不是用了完整的Blinn-Phong模型来对物体表面进行着色，而是使用了该模型处理模型高光(Specular)和漫反射(Diffuse)的思路来输出一个更好的物体表面显示结果。**<br>
下面我们简单介绍一下Blinn-Phong模型。<br>
<br>
Blinn-Phong模型总体的思路是把物体表面一个点的亮度抽象为三个部分的加和，这三个部分分别为Diffuse、Specular和Ambient。（以下图片来自维基百科）<br>
![image](https://github.com/bryceyin13/tinyraytracer/blob/main/images/1.png)
<br>
Diffuse是漫反射部分，就是环境光作用在物体表面一个点上，物体表面这个点向四面八方均匀反射的光。因为是向四面八方“均匀”反射的光，所以我们认为这个光线（在被摄像机捕捉到之后就转化为“亮度”）向各个方向的大小都是相同的，具体的公式如下图所示，图源GAMES101的slide。在代码实现中，我们写成以下的形式：material.diffuse_color * diffuse_light_intensity。实际上就是物体具有的值乘上一个漫反射系数。
<br>
Ambient可以理解为物体本身具有的亮度，这个亮度实际上是为了弥补Diffuse和Specular两项作用在模型上产生的光照的不足而添加的，这个项没有任何物理依据。在本项目中没有使用这一项来计算光照，但是并不是说这个项不正确，相反，。
