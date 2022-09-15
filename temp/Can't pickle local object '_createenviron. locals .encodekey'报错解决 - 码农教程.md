# Can't pickle local object '_createenviron.<locals>.encodekey'报错解决 - 码农教程
  Can't pickle local object '\_createenviron.<locals>.encodekey'报错解决 - 码农教程    

[![](http://www.manongjc.com/Public/images/logo.gif)
](/)

 

   

*   [**首页**](/ "码农教程首页")
*   [**JAVA**](/java/java_tutorial.html "JAVA教程")
*   [**PHP**](/php/php_tutorial.html "PHP教程")
*   [**HTML**](/html/html_tutorial.html "HTML教程")
*   [**CSS**](/css/css_tutorial.html "CSS教程")
*   [**CSS3**](/css3/css3_tutorial.html "CSS3教程")
*   [**JAVASCRIPT**](/javascript/javascript_tutorial.html "JAVASCRIPT教程")
*   [**Sass**](/sass/sass_tutorial.html "Sass教程")
*   [**MYSQL**](/mysql_basic/mysql-tutorial-basic.html "MYSQL教程")
*   [**SQL**](/sql/sql_tutorial.html "SQL教程")
*   [**PL/SQL**](/oracle/pl-sql-tutorial.html "PL/SQL教程")
*   [**SQLITE**](/sqlite/sqlite_tutorial.html "SQLite教程")
*   [**REDIS**](/redis/redis_tutorial.html "Redis教程")

[首页](/) > [编程笔记](/biji) > [其他](/category/6.html) > Can't pickle local object '\_createenviron.<locals>.encodekey'报错解决

Can't pickle local object '\_createenviron.<locals>.encodekey'报错解决
==================================================================

时间:2021-01-30

本文章向大家介绍Can't pickle local object '\_createenviron.<locals>.encodekey'报错解决，主要包括Can't pickle local object '\_createenviron.<locals>.encodekey'报错解决使用实例、应用技巧、基本知识点总结和需要注意事项，具有一定的参考价值，需要的朋友可以参考一下。

关于selenium传参报错问题，用下面是报错信息：

Traceback (most recent call last):
  File "D:/code/read\_book/main.py", line 327, in <module> main()
  File "D:/code/read\_book/main.py", line 303, in main
    read\_one.start()
  File "C:\\Users\\23914\\AppData\\Local\\Programs\\Python\\Python38-32\\lib\\multiprocessing\\process.py", line 121, in start
    self.\_popen \= self.\_Popen(self)
  File "C:\\Users\\23914\\AppData\\Local\\Programs\\Python\\Python38-32\\lib\\multiprocessing\\context.py", line 224, in \_Popen return \_default\_context.get\_context().Process.\_Popen(process\_obj)
  File "C:\\Users\\23914\\AppData\\Local\\Programs\\Python\\Python38-32\\lib\\multiprocessing\\context.py", line 326, in \_Popen return Popen(process\_obj)
  File "C:\\Users\\23914\\AppData\\Local\\Programs\\Python\\Python38-32\\lib\\multiprocessing\\popen\_spawn\_win32.py", line 93, in \_\_init\_\_ reduction.dump(process\_obj, to\_child)
  File "C:\\Users\\23914\\AppData\\Local\\Programs\\Python\\Python38-32\\lib\\multiprocessing\\reduction.py", line 60, in dump
    ForkingPickler(file, protocol).dump(obj)
AttributeError: Can't pickle local object '\_createenviron.<locals>.encodekey'

找了很久的问题，发现是导包问题，把

from multiprocessing import Process, Queue

改为：

from multiprocessing.dummy import Process, Queue

问题解决！

原文地址：https://www.cnblogs.com/1314h/p/14348381.html

随机文章

*   [初识数据库](/detail/50-futkbrtumiqonjp.html "初识数据库")
*   [Python之IO模型](/detail/50-fjvxevasmlawzex.html "Python之IO模型")
*   [jQuery基础](/detail/50-gjrautrondxeslo.html "jQuery基础")
*   [1893\. \[国家集训队2011\]等差子序列(bitset)](/detail/50-hqxcocyoulzuhzy.html "1893. [国家集训队2011]等差子序列(bitset)")
*   [任务管理器编码详解](/detail/50-egiwgdpxrdbphta.html "任务管理器编码详解")
*   [Python3实现TCP端口扫描器](/detail/50-vbrsefuctpotjws.html "Python3实现TCP端口扫描器")
*   [Python之协程](/detail/50-ibzqxftmdlpfaxy.html "Python之协程")
*   [BZOJ 1568: \[JSOI2008\]Blue Mary开公司(超哥线段树)](/detail/50-btztmeyhgswvlfr.html "BZOJ 1568: [JSOI2008]Blue Mary开公司(超哥线段树)")
*   [2000 楼房重建 2012年](/detail/50-ensdeqjydnjtskq.html "2000 楼房重建  2012年")
*   [HUST 1017 - Exact cover](/detail/50-cfazrylspfcally.html "HUST 1017 - Exact cover")
*   [jQuery实例](/detail/50-wmxknlmlvyuwokf.html "jQuery实例")
*   [CSS实例](/detail/50-vmkvlctxuicwjni.html "CSS实例")
*   [HDU 2089 不要62](/detail/50-hjvfuirgtmfnjtx.html "HDU 2089 不要62")
*   [P3376 【模板】网络最大流](/detail/50-ookzkwbdtwmvsvj.html "P3376 【模板】网络最大流")

[![](http://www.manongjc.com/Public/aliyun/336x280.jpg)
](https://www.aliyun.com/minisite/goods?userCode=da65xs35)

本站知识点必读

*   [JavaScript 教程](/javascript/javascript_tutorial.html)
*   [JavaScript 编辑工具](/javascript/js_editor_tool.html)
*   [JavaScript 与HTML](/javascript/js_apply_html.html)
*   [JavaScript 与Java](/javascript/js_java.html)
*   [JavaScript 数据结构](/javascript/js_data_structure.html)
*   [JavaScript 基本数据类型](/javascript/js_basic_data_types.html)
*   [JavaScript 特殊数据类型](/javascript/js_special_data_type.html)
*   [JavaScript 运算符](/javascript/js_operator.html)
*   [JavaScript typeof 运算符](/javascript/js_typeof_operator.html)
*   [JavaScript 表达式](/javascript/js_expression.html)
*   [JavaScript 类型转换](/javascript/js_data_conversion.html)
*   [JavaScript 基本语法](/javascript/js_basic_syntax.html)
*   [JavaScript 注释](/javascript/js_comments.html)
*   [Javascript 基本处理流程](/javascript/js_basic_flow_control.html)
*   [Javascript 选择结构](/javascript/js_select_structure.html)
*   [Javascript if 语句](/javascript/js_if_statements.html)
*   [Javascript if 语句的嵌套](/javascript/js_if_nested.html)
*   [Javascript switch 语句](/javascript/js_switch.html)
*   [Javascript 循环结构](/javascript/js_loop_structure.html)
*   [Javascript 循环结构实例](/javascript/js_loop_example.html)
*   [Javascript 跳转语句](/javascript/js_break_continue.html)
*   [Javascript 控制语句总结](/javascript/js_flow_summary.html)
*   [Javascript 函数介绍](/javascript/js_function_brief.html)
*   [Javascript 函数的定义](/javascript/js_function_define.html)
*   [Javascript 函数调用](/javascript/js_function_call.html)
*   [Javascript 几种特殊的函数](/javascript/js_special_function.html)
*   [JavaScript 内置函数简介](/javascript/js_in_function.html)
*   [Javascript eval() 函数](/javascript/js_eval.html)
*   [Javascript isFinite() 函数](/javascript/js_isfinite.html)
*   [Javascript isNaN() 函数](/javascript/js_isnan.html)
*   [parseInt() 与 parseFloat()](/javascript/js_parseint_parsefloat.html)
*   [escape() 与 unescape()](/javascript/js_escape_unescape.html)
*   [Javascript 字符串介绍](/javascript/js_string_object.html)
*   [Javascript length属性](/javascript/js_length.html)
*   [javascript 字符串函数](/javascript/js_string_functions.html)
*   [Javascript 日期对象简介](/javascript/js_data_object_brief.html)
*   [Javascript 日期对象用途](/javascript/js_data_use_example.html)
*   [Date 对象属性和方法](/javascript/js_date_attr_function.html)
*   [Javascript 数组是什么](/javascript/js_what_is_array.html)
*   [Javascript 创建数组](/javascript/js_create_array.html)
*   [Javascript 数组赋值与取值](/javascript/js_array_get_set_value.html)
*   [Javascript 数组属性和方法](/javascript/js_array_method_attr.html)

本网站教程列表： [JAVA教程](/java/java_tutorial.html) [Java实例](/java_example/java_environment_example.html) [JSP教程](/jsp/jsp_tutorial.html) [Apache POI教程](/poi/poi_tutorial.html) [EJB 教程](/ejb/ejb_tutorial.html) [JDBC 教程](/jdbc/jdbc_tutorial.html) [Spring 教程](/spring/spring_tutorial.html) [PHP教程](/php/php_tutorial.html) [Codeigniter教程](/codeigniter/ci_tutorial.html) [MYSQL 教程](/mysql/mysql_tutorial.html) [Mysql 基础教程](/mysql_basic/mysql-tutorial-basic.html) [SQL 教程](/sql/sql_tutorial.html) [PL/SQL教程](/oracle/pl-sql-tutorial.html ) [SQLite 教程](/sqlite/sqlite_tutorial.html) [Redis 教程](/redis/redis_tutorial.html) [HTML 教程](/html/html_tutorial.html) [CSS教程](/css/css_tutorial.html) [CSS3 教程](/css3/css3_tutorial.html) [CSS 参考手册](/cssref/css_reference.html) [Javascript 教程](/javascript/javascript_tutorial.html) [Bootstrap 教程](/bootstrap/bootstrap_tutorial.html) [Sass 教程](/sass/sass_tutorial.html)

[最近更新](/category/6.html)

*   [js实用方法记录-js动态加载css、js脚本文件](/detail/52-hafodllhxgjfbpx.html "js实用方法记录-js动态加载css、js脚本文件")
*   [使用bat脚本部署hexo到coding和github](/detail/52-ejypaczdvmgpjiw.html "使用bat脚本部署hexo到coding和github")
*   [iis发布后模板字体不能加载的解决方案](/detail/52-apxgdarpipvrvwg.html "iis发布后模板字体不能加载的解决方案")
*   [.net core建站踩坑记录](/detail/52-sbqrqquqtqcafli.html ".net core建站踩坑记录")
*   [使用travis-ci自动部署github上的项目](/detail/52-cmxzsbakqizlzui.html "使用travis-ci自动部署github上的项目")
*   [layui中使用autocomplete.js](/detail/52-fnkwfbmzrfpugvg.html "layui中使用autocomplete.js")
*   [一个简单的时间轴demo](/detail/52-gzrtkemyxnnowkh.html "一个简单的时间轴demo")
*   [winform制作小工具的技巧](/detail/52-ixmopmsbmupvirb.html "winform制作小工具的技巧")
*   [winform复制文件到指定目录](/detail/52-vybmrlqeknsyboi.html "winform复制文件到指定目录")
*   [DB数据导出工具分享](/detail/52-jwfwlviexvymqhd.html "DB数据导出工具分享")
*   [使用批处理脚本愉快的清理缓存](/detail/52-rcbsotefyosqnuf.html "使用批处理脚本愉快的清理缓存")
*   [mvc一对多模型表单的快速构建](/detail/52-vdbbznxhrvcqhsx.html "mvc一对多模型表单的快速构建")
*   [进制的相互转换学习记录](/detail/52-lkzncohhtfwmwjg.html "进制的相互转换学习记录")
*   [.NET Core+Selenium+Github+Travis CI => SiteHistory](/detail/52-bfjdhiqfqiatyhm.html ".NET Core+Selenium+Github+Travis CI => SiteHistory")
*   [使用jenkins自部署Coding项目](/detail/52-wtwwgzkngetdqpm.html "使用jenkins自部署Coding项目")

Copyright (C) 2015 www.manongjc.com, All Rights Reserved. 版权所有 码农教程  
备案号：[鄂ICP备2022014784号-1](https://beian.miit.gov.cn/)