# Git 服务器搭建 | 菜鸟教程
  Git 服务器搭建 | 菜鸟教程              

[菜鸟教程 -- 学的不仅是技术，更是梦想！](/)
==========================

*   [首页](//www.runoob.com/)
*   [HTML](/html/html-tutorial.html)
*   [CSS](/css/css-tutorial.html)
*   [JavaScript](/js/js-tutorial.html)
*   [Vue](javascript:void(0);)
*   [Bootstrap](javascript:void(0);)
*   [NodeJS](/nodejs/nodejs-tutorial.html)
*   [Python3](/python3/python3-tutorial.html)
*   [Python2](/python/python-tutorial.html)
*   [Java](/java/java-tutorial.html)
*   [C](/cprogramming/c-tutorial.html)
*   [C++](/cplusplus/cpp-tutorial.html)
*   [C#](/csharp/csharp-tutorial.html)
*   [Go](/go/go-tutorial.html)
*   [SQL](/sql/sql-tutorial.html)
*   [Linux](/linux/linux-tutorial.html)
*   [jQuery](/jquery/jquery-tutorial.html)
*   [本地书签](/browser-history)

*   [首页](//www.runoob.com/)
*   [HTML](/html/html-tutorial.html)
*   [CSS](/css/css-tutorial.html)
*   [JS](/js/js-tutorial.html)
*   [本地书签](/browser-history)
*   [Search](javascript:void(0))

*   [Python3 教程](/python3/python3-tutorial.html)
*   [Python2 教程](/python/python-tutorial.html)

*   [Vue3 教程](/vue3/vue3-tutorial.html)
*   [vue2 教程](/vue/vue-tutorial.html)

*   [Bootstrap3 教程](/bootstrap/bootstrap-tutorial.html)
*   [Bootstrap4 教程](/bootstrap4/bootstrap4-tutorial.html)
*   [Bootstrap5 教程](/bootstrap5/bootstrap5-tutorial.html)
*   [Bootstrap2 教程](/bootstrap/bootstrap-v2-tutorial.html)

Git 教程[](javascript:void(0); "夜间模式")[](javascript:void(0); "日间模式")

[Git 教程](/git/git-tutorial.html "Git 教程") [Git 安装配置](/git/git-install-setup.html "Git 安装配置") [Git 工作流程](/git/git-workflow.html "Git 工作流程") [Git 工作区、暂存区和版本库](git-workspace-index-repo.html "Git 工作区、暂存区和版本库") [Git 创建仓库](/git/git-create-repository.html "Git 创建仓库") [Git 基本操作](/git/git-basic-operations.html "Git 基本操作") [Git 分支管理](/git/git-branch.html "Git 分支管理") [Git 查看提交历史](/git/git-commit-history.html "Git 查看提交历史") [Git 标签](/git/git-tag.html "Git 标签") [Git Github](/git/git-remote-repo.html "Git 远程仓库(Github)") [Git Gitee](/git/git-gitee.html "Git Gitee") [Git 服务器搭建](/git/git-server.html "Git 服务器搭建") [Sourcetree](/git/source-tree-intro.html "Git Gitee") [Git 测验](/git/git-quiz.html "Git 测验")

[](https://www.runoob.com/git/git-gitee.html)[Git Gitee](https://www.runoob.com/git/git-gitee.html "Git Gitee")

[Git Gitee](https://www.runoob.com/git/source-tree-intro.html "Git Gitee")[](https://www.runoob.com/git/source-tree-intro.html)

Git 服务器搭建
=========

上一章节中我们远程仓库使用了 Github，Github 公开的项目是免费的，2019 年开始 Github 私有存储库也可以无限制使用。

这当然我们也可以自己搭建一台 Git 服务器作为私有仓库使用。

接下来我们将以 Centos 为例搭建 Git 服务器。

### 1、安装Git

```
$ yum install curl\-devel expat\-devel gettext\-devel openssl\-devel zlib\-devel perl\-devel
$ yum install git
```

接下来我们 创建一个git用户组和用户，用来运行git服务：

```
$ groupadd git
$ useradd git \-g git
```

### 2、创建证书登录

收集所有需要登录的用户的公钥，公钥位于id\_rsa.pub文件中，把我们的公钥导入到/home/git/.ssh/authorized\_keys文件里，一行一个。

如果没有该文件创建它：

```
$ cd /home/git/ $ mkdir .ssh
$ chmod 755  .ssh
$ touch .ssh/authorized\_keys
$ chmod 644  .ssh/authorized\_keys
```

### 3、初始化Git仓库

首先我们选定一个目录作为Git仓库，假定是/home/gitrepo/runoob.git，在/home/gitrepo目录下输入命令：

```
$ cd /home
$ mkdir gitrepo
$ chown git:git gitrepo/ $ cd gitrepo

$ git init \--bare runoob.git Initialized empty Git repository in  /home/gitrepo/runoob.git/
```

以上命令Git创建一个空仓库，服务器上的Git仓库通常都以.git结尾。然后，把仓库所属用户改为git：

```
$ chown \-R git:git runoob.git
```

### 4、克隆仓库

```
$ git clone git@192.168.45.4:/home/gitrepo/runoob.git Cloning  into  'runoob'... warning:  You appear to have cloned an empty repository.  Checking connectivity...  done.
```

192.168.45.4 为 Git 所在服务器 ip ，你需要将其修改为你自己的 Git 服务 ip。

这样我们的 Git 服务器安装就完成。

[](https://www.runoob.com/git/git-gitee.html)[Git Gitee](https://www.runoob.com/git/git-gitee.html "Git Gitee")

[Git Gitee](https://www.runoob.com/git/source-tree-intro.html "Git Gitee")[](https://www.runoob.com/git/source-tree-intro.html)

### 点我分享笔记

[取消](javascript:;)

写笔记...

  

选择程序语言 BashC++C#CSSErlangLessSassDiffCoffeeScriptHTML,XMLJSONJavaJavaScriptMarkdownObjective CPHPPerlPythonRubySQL

图片地址 

图片描述 

图片尺寸  ×  [](javascript:; "还原图片尺寸") 

 

分享笔记

*   昵称昵称 (必填)
*   邮箱邮箱 (必填)
*   引用地址引用地址

 

[分类导航](javascript:void(0);)

*   [HTML / CSS](javascript:void(0);)
    *   [HTML 教程](//www.runoob.com/html/html-tutorial.html "HTML 教程")
    *   [HTML5 教程](//www.runoob.com/html/html5-intro.html "HTML5 教程")
    *   [CSS 教程](//www.runoob.com/css/css-tutorial.html "CSS 教程")
    *   [CSS3 教程](//www.runoob.com/css3/css3-tutorial.html "CSS3 教程")
    *   [Bootstrap3 教程](//www.runoob.com/bootstrap/bootstrap-tutorial.html "Bootstrap3 教程")
    *   [Bootstrap4 教程](//www.runoob.com/bootstrap4/bootstrap4-tutorial.html "Bootstrap4 教程")
    *   [Bootstrap5 教程](//www.runoob.com/bootstrap5/bootstrap5-tutorial.html "Bootstrap5 教程")
    *   [Font Awesome 教程](//www.runoob.com/font-awesome/fontawesome-tutorial.html "Font Awesome 教程")
    *   [Foundation 教程](//www.runoob.com/foundation/foundation-tutorial.html "Foundation 教程")
*   [JavaScript](javascript:void(0);)
    *   [JavaScript 教程](//www.runoob.com/js/js-tutorial.html "JavaScript 教程")
    *   [HTML DOM 教程](//www.runoob.com/htmldom/htmldom-tutorial.html "HTML DOM 教程")
    *   [jQuery 教程](//www.runoob.com/jquery/jquery-tutorial.html "jQuery 教程")
    *   [AngularJS 教程](//www.runoob.com/angularjs/angularjs-tutorial.html "AngularJS 教程")
    *   [AngularJS2 教程](//www.runoob.com/angularjs2/angularjs2-tutorial.html "AngularJS2 教程")
    *   [Vue.js 教程](//www.runoob.com/vue2/vue-tutorial.html "Vue.js 教程")
    *   [Vue3 教程](//www.runoob.com/vue3/vue3-tutorial.html "Vue3 教程")
    *   [React 教程](//www.runoob.com/react/react-tutorial.html "React 教程")
    *   [TypeScript 教程](//www.runoob.com/typescript/ts-tutorial.html "TypeScript 教程")
    *   [jQuery UI 教程](//www.runoob.com/jqueryui/jqueryui-tutorial.html "jQuery UI 教程")
    *   [jQuery EasyUI 教程](//www.runoob.com/jeasyui/jqueryeasyui-tutorial.html "jQuery EasyUI 教程")
    *   [Node.js 教程](//www.runoob.com/nodejs/nodejs-tutorial.html "Node.js 教程")
    *   [AJAX 教程](//www.runoob.com/ajax/ajax-tutorial.html "AJAX 教程")
    *   [JSON 教程](//www.runoob.com/json/json-tutorial.html "JSON 教程")
    *   [Echarts 教程](//www.runoob.com/echarts/echarts-tutorial.html "Echarts 教程")
    *   [Highcharts 教程](//www.runoob.com/highcharts/highcharts-tutorial.html "Highcharts 教程")
    *   [Google 地图 教程](//www.runoob.com/googleapi/google-maps-basic.html "Google 地图 教程")
*   [服务端](javascript:void(0);)
    *   [Python 教程](//www.runoob.com/python3/python3-tutorial.html "Python 教程")
    *   [Python2.x 教程](//www.runoob.com/python/python-tutorial.html "Python2.x 教程")
    *   [Linux 教程](//www.runoob.com/linux/linux-tutorial.html "Linux 教程")
    *   [Docker 教程](//www.runoob.com/docker/docker-tutorial.html "Docker 教程")
    *   [Ruby 教程](//www.runoob.com/ruby/ruby-tutorial.html "Ruby 教程")
    *   [Java 教程](//www.runoob.com/java/java-tutorial.html "Java 教程")
    *   [C 教程](//www.runoob.com/c/c-tutorial.html "C 教程")
    *   [C++ 教程](//www.runoob.com/cplusplus/cpp-tutorial.html "C++ 教程")
    *   [Perl 教程](//www.runoob.com/perl/perl-tutorial.html "Perl 教程")
    *   [Servlet 教程](//www.runoob.com/servlet/servlet-tutorial.html "Servlet 教程")
    *   [JSP 教程](//www.runoob.com/jsp/jsp-tutorial.html "JSP 教程")
    *   [Lua 教程](//www.runoob.com/lua/lua-tutorial.html "Lua 教程")
    *   [Rust 教程](//www.runoob.com/rust/rust-tutorial.html "Rust 教程")
    *   [Scala 教程](//www.runoob.com/scala/scala-tutorial.html "Scala 教程")
    *   [Go 教程](//www.runoob.com/go/go-tutorial.html "Go 教程")
    *   [PHP 教程](//www.runoob.com/php/php-tutorial.html "PHP 教程")
    *   [数据结构与算法](//www.runoob.com/data-structures/data-structures-tutorial.html "数据结构与算法")
    *   [Django 教程](//www.runoob.com/django/django-tutorial.html "Django 教程")
    *   [Zookeeper 教程](//www.runoob.com/w3cnote/zookeeper-tutorial.html "Zookeeper 教程")
    *   [设计模式](//www.runoob.com/design-pattern/design-pattern-tutorial.html "设计模式")
    *   [正则表达式](//www.runoob.com/regexp/regexp-tutorial.html "正则表达式")
    *   [Maven 教程](//www.runoob.com/maven/maven-tutorial.html "Maven 教程")
    *   [Verilog 教程](//www.runoob.com/w3cnote/verilog-tutorial.html "Verilog 教程")
    *   [ASP 教程](//www.runoob.com/asp/asp-tutorial.html "ASP 教程")
    *   [AppML 教程](//www.runoob.com/appml/appml-tutorial.html "AppML 教程")
    *   [VBScript 教程](//www.runoob.com/vbscript/vbscript-tutorial.html "VBScript 教程")
*   [数据库](javascript:void(0);)
    *   [SQL 教程](//www.runoob.com/sql/sql-tutorial.html "SQL 教程")
    *   [MySQL 教程](//www.runoob.com/mysql/mysql-tutorial.html "MySQL 教程")
    *   [PostgreSQL 教程](//www.runoob.com/postgresql/postgresql-tutorial.html "PostgreSQL 教程")
    *   [SQLite 教程](//www.runoob.com/sqlite/sqlite-tutorial.html "SQLite 教程")
    *   [MongoDB 教程](//www.runoob.com/mongodb/mongodb-tutorial.html "MongoDB 教程")
    *   [Redis 教程](//www.runoob.com/redis/redis-tutorial.html "Redis 教程")
    *   [Memcached 教程](//www.runoob.com/Memcached/Memcached-tutorial.html "Memcached 教程")
*   [数据分析](javascript:void(0);)
    *   [Python 教程](//www.runoob.com/python3/python3-tutorial.html "Python 教程")
    *   [NumPy 教程](//www.runoob.com/numpy/numpy-tutorial.html "NumPy 教程")
    *   [Pandas 教程](//www.runoob.com/pandas/pandas-tutorial.html "Pandas 教程")
    *   [Matplotlib 教程](//www.runoob.com/matplotlib/matplotlib-tutorial.html "Matplotlib 教程")
    *   [Scipy 教程](//www.runoob.com/scipy/scipy-tutorial.html "Scipy 教程")
    *   [R 教程](//www.runoob.com/r/r-tutorial.html "R 教程")
    *   [Julia 教程](//www.runoob.com/julia/julia-tutorial.html "Julia 教程")
*   [移动端](javascript:void(0);)
    *   [Android 教程](//www.runoob.com/w3cnote/android-tutorial-intro.html "Android 教程")
    *   [Swift 教程](//www.runoob.com/swift/swift-tutorial.html "Swift 教程")
    *   [jQuery Mobile 教程](//www.runoob.com/jquerymobile/jquerymobile-tutorial.html "jQuery Mobile 教程")
    *   [ionic 教程](//www.runoob.com/ionic/ionic-tutorial.html "ionic 教程")
    *   [Kotlin 教程](//www.runoob.com/kotlin/kotlin-tutorial.html "Kotlin 教程")
*   [XML 教程](javascript:void(0);)
    *   [XML 教程](//www.runoob.com/xml/xml-tutorial.html "XML 教程")
    *   [DTD 教程](//www.runoob.com/dtd/dtd-tutorial.html "DTD 教程")
    *   [XML DOM 教程](//www.runoob.com/dom/dom-tutorial.html "XML DOM 教程")
    *   [XSLT 教程](//www.runoob.com/xsl/xsl-tutorial.html "XSLT 教程")
    *   [XPath 教程](//www.runoob.com/xpath/xpath-tutorial.html "XPath 教程")
    *   [XQuery 教程](//www.runoob.com/xquery/xquery-tutorial.html "XQuery 教程")
    *   [XLink 教程](//www.runoob.com/xlink/xlink-tutorial.html "XLink 教程")
    *   [XPointer 教程](//www.runoob.com/xlink/xlink-tutorial.html "XPointer 教程")
    *   [XML Schema 教程](//www.runoob.com/schema/schema-tutorial.html "XML Schema 教程")
    *   [XSL-FO 教程](//www.runoob.com/xslfo/xslfo-tutorial.html "XSL-FO 教程")
    *   [SVG 教程](//www.runoob.com/svg/svg-tutorial.html "SVG 教程")
*   [ASP.NET](javascript:void(0);)
    *   [ASP.NET 教程](//www.runoob.com/aspnet/aspnet-tutorial.html "ASP.NET 教程")
    *   [C# 教程](//www.runoob.com/csharp/csharp-tutorial.html "C# 教程")
    *   [Web Pages 教程](//www.runoob.com/aspnet/webpages-intro.html "Web Pages 教程")
    *   [Razor 教程](//www.runoob.com/aspnet/razor-intro.html "Razor 教程")
    *   [MVC 教程](//www.runoob.com/aspnet/mvc-intro.html "MVC 教程")
    *   [Web Forms 教程](//www.runoob.com/aspnet/aspnet-intro.html "Web Forms 教程")
*   [Web Service](javascript:void(0);)
    *   [Web Service 教程](//www.runoob.com/webservices/webservices-tutorial.html "Web Service 教程")
    *   [WSDL 教程](//www.runoob.com/wsdl/wsdl-tutorial.html "WSDL 教程")
    *   [SOAP 教程](//www.runoob.com/soap/soap-tutorial.html "SOAP 教程")
    *   [RSS 教程](//www.runoob.com/rss/rss-tutorial.html "RSS 教程")
    *   [RDF 教程](//www.runoob.com/rdf/rdf-tutorial.html "RDF 教程")
*   [开发工具](javascript:void(0);)
    *   [Eclipse 教程](//www.runoob.com/eclipse/eclipse-tutorial.html "Eclipse 教程")
    *   [Git 教程](//www.runoob.com/git/git-tutorial.html "Git 教程")
    *   [Svn 教程](//www.runoob.com/svn/svn-tutorial.html "Svn 教程")
    *   [Markdown 教程](//www.runoob.com/markdown/md-tutorial.html "Markdown 教程")
*   [网站建设](javascript:void(0);)
    *   [HTTP 教程](//www.runoob.com/http/http-tutorial.html "HTTP 教程")
    *   [网站建设指南](//www.runoob.com/web/web-buildingprimer.html "网站建设指南")
    *   [浏览器信息](//www.runoob.com/browsers/browser-information.html "浏览器信息")
    *   [网站主机教程](//www.runoob.com/hosting/hosting-tutorial.html "网站主机教程")
    *   [TCP/IP 教程](//www.runoob.com/tcpip/tcpip-tutorial.html "TCP/IP 教程")
    *   [W3C 教程](//www.runoob.com/w3c/w3c-tutorial.html "W3C 教程")
    *   [网站品质](//www.runoob.com/quality/quality-tutorial.html "网站品质")

  

[Advertisement](javascript:void(0);)

 反馈/建议  反馈/建议 

在线实例

·[HTML 实例](/html/html-examples.html)

·[CSS 实例](/css/css-examples.html)

·[JavaScript 实例](/js/js-examples.html)

·[Ajax 实例](/ajx/ajax-examples.html)

·[jQuery 实例](/jquery/jquery-examples.html)

·[XML 实例](/xml/xml-examples.html)

·[Java 实例](/java/java-examples.html)

字符集&工具

· [HTML 字符集设置](/charsets/html-charsets.html)

· [HTML ASCII 字符集](/tags/html-ascii.html)

· [JS 混淆/加密](https://c.runoob.com/front-end/6939/)

· [PNG/JPEG 图片压缩](https://c.runoob.com/front-end/6232/)

· [HTML 拾色器](/tags/html-colorpicker.html)

· [JSON 格式化工具](//c.runoob.com/front-end/53)

· [随机数生成器](//c.runoob.com/front-end/6680/)

最新更新

· [JavaScript 获取...](http://www.runoob.com/w3cnote/javascript-get-the-value-of-text-input-field.html "JavaScript 获取 input 输入框内容的几种方法")

· [JavaScript 实现...](http://www.runoob.com/w3cnote/javascript-copy-clipboard.html "JavaScript 实现复制功能")

· [HTML DOM style ...](http://www.runoob.com/jsref/prop-element-style.html "HTML DOM style 属性")

· [HTML DOM scroll...](http://www.runoob.com/jsref/prop-element-scrollwidth.html "HTML DOM scrollWidth 属性")

· [HTML DOM scroll...](http://www.runoob.com/jsref/prop-element-scrolltop.html "HTML DOM scrollTop 属性")

· [HTML DOM scroll...](http://www.runoob.com/jsref/prop-element-scrollleft.html "HTML DOM scrollLeft 属性")

· [Docker stats 命令](http://www.runoob.com/docker/docker-stats-command.html "Docker stats 命令")

站点信息

· [意见反馈](//mail.qq.com/cgi-bin/qm_share?t=qm_mailme&email=ssbDyoOAgfLU3crf09venNHd3w)

· [免责声明](/disclaimer)

· [关于我们](/aboutus)

· [文章归档](/archives)

**关注微信**

![](https://www.runoob.com/wp-content/themes/runoob/assets/images/qrcode.png)

Copyright © 2013-2022 **[菜鸟教程](//www.runoob.com/)**  **[runoob.com](//www.runoob.com/)** All Rights Reserved. 备案号：[闽ICP备15012807号-1](https://beian.miit.gov.cn/)

[](javascript:void(0) "返回顶部")[](javascript:void(0) "关注我们")[](javascript:void(0) "标记/收藏")

#### 微信关注

![](https://www.runoob.com/wp-content/themes/runoob/assets/images/qrcode.png)