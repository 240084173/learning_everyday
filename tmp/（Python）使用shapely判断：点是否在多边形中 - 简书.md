# （Python）使用shapely判断：点是否在多边形中 - 简书
（Python）使用shapely判断：点是否在多边形中 - 简书



（Python）使用shapely判断：点是否在多边形中
============================

2021.07.09 16:56:47字数 539阅读 6,343

判断点是否在多边形中的多种方法

1 使用shapely判断点是否在多边形中
=====================

使用python里的shapely库可以很方便地判断一个点是否在多边形中  
它的特点是你可以diy点和多边形。适用于**点和多边形都有自己构建的情况**  
首先，要先在控制台安装shapely

```
pip install shapely 
```

然后，在py文件中，构建一个shapely中的点:  
坐标（1，1）

```
import shapely.geometry
point = shapely.geometry.Point(1, 1) 
```

然后，构建一个多边形：  
这里要注意，我们的输入是字典格式的，有两个键，分别是'type'和'coordinates'，在'coordinates'里是多边形的边缘上的边的坐标。

```
import shapely.geometry
poly_context = {'type': 'MULTIPOLYGON',
    'coordinates': [[[[0, 0], [0, 2], [2, 2], [2, 0]]]]}
poly_shape = shapely.geometry.asShape(poly_context)
poly_shape 
```

![](https://upload-images.jianshu.io/upload_images/26412439-7cf15bb94bd259cf.png)

构建的多边形.png

  

最后，判断点是否在多边形中：

```
print(poly_shape.intersects(point))
#输出： True 
```

2 结合shapefile判断点是否在shp文件的多边形中
=============================

这时候，我们的**多边形通过shp文件读取**,点是我们自己构造的  
要用到shapefile和shapely两个库  
然后我这个情况是，shp文件中有多个多边形，我可以判断点是否在每一个多边形中，简单地说是用这个函数:

```
geometry.Point(point).within(geometry.shape(shape)) 
```

详细代码如下，我写了个循环，对于shp文件中的每个shape，我都判断一下，点是否在其中

```
import shapefile
import shapely.geometry as geometry
shp_path = './temp.shp'
sf = shapefile.Reader(shp_path)
point = [-73.98088709894267, 40.75348098873852]
    for i in range(len(shapes)):
        print(i, geometry.Point(point).within(geometry.shape(shapes[i]))) 
```

输出：

```
0 False
1 False
2 False
...
6 False
7 False
8 False 
```

3 结合geopandas判断点是否在shp文件的多边形中
=============================

关于geopandas的安装，请参考：  
[https://blog.csdn.net/weixin\_41608080/article/details/114494953](https://links.jianshu.com/go?to=https%3A%2F%2Fblog.csdn.net%2Fweixin_41608080%2Farticle%2Fdetails%2F114494953)  
Mac用户请参考：  
[https://blog.csdn.net/qq\_39805362/article/details/122741171](https://links.jianshu.com/go?to=https%3A%2F%2Fblog.csdn.net%2Fqq_39805362%2Farticle%2Fdetails%2F122741171)  
这个的前提，依然是，你有一个shp文件  
然后我们现在不用shapefile读取shp文件，而是geopandas读取，不得不说，geopandas是真的好用，可以之间看到shape具体是什么数据：

```
import geopandas
shp_path = './temp.shp'
shp_df = geopandas.GeoDataFrame.from_file(shp_path, )
print(shp_df.head()) 
```

输出：

```
 region_id                                           geometry
0          0  POLYGON ((-73.98089 40.75348, -73.98094 40.753...
1          1  POLYGON ((-73.94712 40.82590, -73.94761 40.825...
2          2  POLYGON ((-73.99260 40.72414, -73.99263 40.724...
3          3  POLYGON ((-73.95034 40.77556, -73.95080 40.774...
4          4  POLYGON ((-73.93131 40.85933, -73.93136 40.859... 
```

真的就所见即所得，我这个shp文件也是有多个多边形。  
然后比如说我们判断一个点是否在第一个多边形中,直接使用within函数即可：

```
pnts = Point(3, 3)
print(pnts.within(shp_df.iloc[0]['geometry'])) 
```

输出：

```
False 
```

**非常好用！**

