# OpenCV实现图片上输出中文 Python OpenCV实现图片上输出中文(IT技术)
想了解Python OpenCV实现图片上输出中文的相关内容吗，-牧野-在本文为您仔细讲解OpenCV实现图片上输出中文的相关知识和一些Code实例，欢迎阅读和指正，我们先划重点：Python图片输出中文,OpenCV图片输出中文,FreeType，下面大家一起来学习吧。

OpenCV中在图片上输出中文一般需要借助FreeType库实现。FreeType库是一个完全免费（开源）的、高质量的且可移植的字体引擎，它提供统一的接口来访问多种字体格式文件。但使用FreeType需要下载库并重新编译，过程麻烦一点。  

在Python中，可以借助PIL(Python Imaging Library)模块实现，相对简单很多，需要做的只是对图像进行OpenCV格式和PIL格式的相互转换。

```
\# -\*- coding: utf-8 -\*- 
import cv2 
import numpy 
from PIL import Image, ImageDraw, ImageFont 
 
if \_\_name\_\_ == '\_\_main\_\_': 
 
 img\_OpenCV = cv2.imread('01.jpg') 
 # 图像从OpenCV格式转换成PIL格式 
 img\_PIL = Image.fromarray(cv2.cvtColor(img\_OpenCV, cv2.COLOR\_BGR2RGB)) 
 
 # 字体 字体\*.ttc的存放路径一般是： /usr/share/fonts/opentype/noto/ 查找指令locate \*.ttc 
 font = ImageFont.truetype('NotoSansCJK-Black.ttc', 40) 
 # 字体颜色 
 fillColor = (255,0,0) 
 # 文字输出位置 
 position = (100,100) 
 # 输出内容 
 str = '在图片上输出中文' 
 
 # 需要先把输出的中文字符转换成Unicode编码形式 
 if not isinstance(str, unicode): 
  str = str.decode('utf8') 
 
 draw = ImageDraw.Draw(img\_PIL) 
 draw.text(position, str, font=font, fill=fillColor) 
 # 使用PIL中的save方法保存图片到本地 
 # img\_PIL.save('02.jpg', 'jpeg') 
 
 # 转换回OpenCV格式 
 img\_OpenCV = cv2.cvtColor(numpy.asarray(img\_PIL),cv2.COLOR\_RGB2BGR) 
 cv2.imshow("print chinese to image",img\_OpenCV) 
 cv2.waitKey() 
 cv2.imwrite('03.jpg',img\_OpenCV) 

```

输出效果：

 ![](http://img.jbzj.com/file_images/article/201801/2018012215220831.jpg)
  

字体 \*.ttc的存放路径一般是： /usr/share/fonts/opentype/noto/  

可以使用locate指令查找本机上已经下载的字体：

![](http://img.jbzj.com/file_images/article/201801/2018012215220832.png)
  

  

### 相关文章

*   [PHP GD库添加freetype拓展 PHP GD库添加freetype拓展的方法](https://www.qb5200.com/article/320779.html "PHP GD库添加freetype拓展 PHP GD库添加freetype拓展的方法")
*   [Mac OS X 自带PHP环境gd库扩展缺少freetype 解决Mac OS X 自带PHP环](https://www.qb5200.com/article/320778.html "Mac OS X 自带PHP环境gd库扩展缺少freetype 解决Mac OS X 自带PHP环境gd库扩展缺少freetype的问题")
*   [libfreetype编译 怎样编译libfreetype方法详解](https://www.qb5200.com/article/266349.html "libfreetype编译 怎样编译libfreetype方法详解")
*   [什么是glibc?glibc是什么?什么是freetype?freetype是什么?什么是?Xli](https://www.qb5200.com/article/202342.html "什么是glibc?glibc是什么?什么是freetype?freetype是什么?什么是?Xlib是什么?什么是lo")
*   [android 微信右滑退出 Android微信右滑退出功能的实](https://www.qb5200.com/article/324324.html "android 微信右滑退出 Android微信右滑退出功能的实现代码")
*   [android studio3.0.1填坑 Android Studio3.0.1填坑](https://www.qb5200.com/article/324323.html "android studio3.0.1填坑 Android Studio3.0.1填坑笔记")