---
layout:     post
title:      "Hello World！"
subtitle:   " \"It is the first step that costs troublesome.\""
date:       2016-09-02 00:00:00
author:     "Daniel"
header-img: "img/20160902-personal-blog.jpg"
catalog: true
tags:
    - 博客
---

> “老生常谈的Github+Markdown+Jekyll搭建个人博客。”

## 前言

如果不写篇文章记录你所做过的事，那跟没做过有什么区别。

Jekyll是一个静态网站生成工具。它允许用户使用HTML、Markdown或Textile来建立静态页面，然后通过模板引擎Liquid（Liquid Templating Engine）来运行。
这篇文章主要讲[Windows 上安装 Jekyll](http://blog.csdn.net/kong5090041/article/details/38408211)。

其实写这类博客搭建的文章网上非常多，但是因为每个人不同的电脑配置，不同的知识掌握程度，总会遇到各种各样不同的问题，
况且每次版本更新总会有操作上的变化，所以还是在这里记录一下个人最新的操作实践吧。

<p id = "build"></p>
---

## 正文

总而言之，如果你想搭建的过程中比较顺利，你需要掌握以下三点：Github的仓库使用，Jekyll的安装以及Markdown的语法。

#### Github新建仓库

首先，登陆 GitHub，新建一个 repository, 命名为你的用户名 + github.io。如我的用户名为 weixingtai，所以 repository 命名为 weixingtai.github.io
然后将线上的 repository 克隆到本地 (我下载了 Github Desktop 用于同步，你也可以使用 Git 同步，看个人喜好)。

后面youusername.github.io就是你的域名。如果你想使用自己的域名，可以在仓库中新建一个file，将 file 命名为 CNAME (全部为大写)，然后添加你的个人域名 (不要带 http 前缀)，
保存，pull request 到 master。到你的域名创建所在网址，管理域名中，新建一个A record 指向youusername.github.io,这样你就可以使用个人域名访问你的博客了。
[我的 Github 个人博客是怎样炼成的](http://www.jianshu.com/p/4fd3cb0a11da)。

到这里为止，我们已经完成了第一步。

---

最初遇到的问题大概是软件的下载问题。没错，就是我大天朝的墙。不过，对于打算搭建博客的你我来说，各种下载技巧，翻墙，镜像网站balabala，应该不成问题。
由于之前下载墙外的东西较多，所以在这个问题上没有遇到太大的阻滞。

#### 安装 Ruby

1.	前往 http://rubyinstaller.org/downloads/；
2.	在 “RubyInstallers” 部分，选择某个版本点击下载（根据你电脑及系统的配置）。我的电脑是win10×64bit。我选择的是 rubyinstaller-2.3.1-x64安装包；
3.	通过安装包安装；
 	* 路径可以自己选择，但是切记不要使用带有空格的文件夹；
 	* 勾选 “Add Ruby executables to your PATH”，这样执行程序会被自动添加至 PATH（使用命令行访问）；
4.	打开一个命令提示行并输入以下命令来检测 Ruby是否成功安装。

		ruby -v

	输出示例：

		ruby 2.3.1p112 (2016-04-26 revision 54768) [x64-mingw32]

在涉及到命令行的地方，可以使用cmd窗口，但是也建议使用git bash，因为在cmd窗口有时会报一些奇怪的错误。

<p id = "devkit"></p>

#### 安装 DevKit

DevKit 是一个在 Windows 上帮助简化安装及使用 Ruby C/C++ 扩展如 RDiscount 和 RedCloth 的工具箱。详细的安装指南可以在程序的wiki页面阅读。

1.	再次前往 http://rubyinstaller.org/downloads/；
2.	下载同电脑与系统的配置及 Ruby 版本相对应的 DevKit安装包。网站上有版本对应列表，同样，我选择了相对应的DevKit-mingw64-64-4.7.2-20130224-1432-sfx；
3.	运行安装包并解压缩至某文件夹，如 D:\DevKit；
4.	通过初始化来创建 config.yml 文件；

		cd “D:\DevKit”
		ruby dk.rb init
		notepad config.yml

5.	在打开的记事本窗口中，于末尾添加新的一行 - D:\Ruby（ruby的安装地址），保存文件并退出；
6.	回到命令行窗口内，审查（非必须）并安装，（若上一步系统已经自动添加，这一步直接跳过不会出错）。

	输入以下命令:

		ruby dk.rb review
		ruby dk.rb install

<p id = "jekyll"></p>

#### 安装 Jekyll

1.	确保 gem 已经正确安装；

		gem -v

	输出示例：

		2.5.1

2.	安装 Jekyll gem；

	输入以下命令:

		gem install jekyll

<p id = "pygments"></p>

#### 安装 Pygments

Jekyll 里默认的语法高亮插件是 Pygments。 它需要安装 Python 并在网站的配置文件_config.yml 里将 highlighter 的值设置为pygments。
不久之前，Jekyll 还添加另一个高亮引擎名为 Rouge， 尽管暂时不如 Pygments 支持那么多的语言，但它是原生 Ruby 程序，而不需要使用 Python。

<p id = "sub_python"></p>

###### 安装 python

1.	前往 http://www.python.org/download/
2.	下载合适的 Python windows 安装包，如 python-3.5.2-amd64.exe。
3.	安装
4.	添加安装路径 (如： D:\Python) 至 PATH。
5.	检验 Python 安装是否成功

		python –V

	输出示例：

		Python 2.7.6

<p id = "sub_esayInstall"></p>

###### 安装 Easy Install

新版Python只需要将 ‘Python Scripts’ 路径 (如： D:\Python\Scripts) 添加至 PATH。

<p id = "sub_pygments"></p>

###### 安装 Pygments

1.	确保 easy_install 已经正确安装；

		easy_install --version

	输出示例：

		setuptools 20.10.1 from d:\program\jekyll\python\lib\site-packages (Python 3.5)

2.	使用 “easy_install” 来安装 Pygments；

		easy_install Pygments

<p id = "project"></p>
---

到这里为止，我们的环境搭建已经告一段落。但是在我创建项目的时候，竟然报错了，大概内容意思是找不到bundle，在网上搜了一些解决方案大多都是文不对题。后来无意中进入到jekyll的官网。上面赫然写着：

	~ $ gem install jekyll bundler
	~ $ jekyll new my-awesome-site
	~ $ cd my-awesome-site
	~ /my-awsome-site $ bundle install
	~ /my-awsome-site $ bundle exec jekyll serve

嗯，我们往往容易忽略最显而易见的东西。

#### 创建项目

接下就是最激动人心的时刻了！首先我们到想要创建项目的文件夹下（如d:/），运行命令：

	jekyll new blog

这样就会创建一个新文件夹d:/blog，其结构如下：
1. 文件夹_layouts：用于存放模板的文件夹，里面有两个模板，default.html和post.html；
2. 文件夹_posts：用于存放博客文章的文件夹，里面有一篇markdown格式的文章--2016-09-02-welcome-to-jekyll.markdown；
3. 文件夹css：存放博客所用css的文件夹；
4. .gitignore：可以删掉，后面会将项目添加到git项目，所以这个不需要了；
5. _coinfig.yml：jekyll的配置文件，里面可以定义相当多的配置参数，具体配置参数可以参照其官网；
6. index.html：项目的首页。

根据实际需要，可能还需要创建如下文件或文件夹：
1. _includes:用于存放一些固定的HTML代码段，文件为.html格式，可以在模板中通过liquid标签引入，常用来在各个模板中复用如 导航条、标签栏、侧边栏 之类的在每个页面上都一样不变的内容，需要注意的是，这个代码段也可以是未被编译的，也就是说也可以使用liquid标签放在这些代码段中；
2. image和js等自定义文件夹：用来存放一些需要的资源文件，如图片或者javascript文件，可以任意命名；
3. CNAME文件：用来在github上做域名绑定的，将在后面介绍；
4. favicon.ico：网站的小图标；
5. ....

回到第一步，现在可以把blog中的文件复制到我们从Github中clone到本地的仓库中，并pull request到master，然后登陆youusername.github.io你会惊奇的发现，我们的个人博客已经初具雏形。

接下来需要修改的就是jekyll的配置文件_config.yml，这个配置文件的内容相当多，详细见官方文档，如果没有太多的额外需求，只需要设定两个参数就行了，一个是编码的字符集，一个是项目的路径，
我这里是这么设定的：

	baseurl: /
	encoding: utf-8

这样一个博客项目就创建完成了。

<p id = "passage"></p>

#### 编写博文

首先你需要了解一下什么是[markdown语法](weixingtai.github.io/2016/09/02/markdown/)。

大致上jekyll生成html的流程，jekyll首先会读取如下内容进入内存中：
1. _posts及文件夹下的所有文章，将其参数和文章内容组织保存在内存中，所有的文章的内容、参数都在site.posts对象（其他文件夹下的文章不会放入site.posts中）；
2. _layouts文件夹下的所有模板；
3. _includes文件夹下的所有需要被引入的内容。

然后根据每一篇需要编译的文章选择的其参数定义的模板来创建一个模板，并将当前文章的内容、参数等进行扩展后放在page对象、content对象中，然后进行模板的编译，生成html文件，
并按照一定规则放在_site文件夹下。也就是说在创建一篇文章时，其实所有文章的内容都已经被读取出来了，这也为文章相互之间的关联提供了可能。

可以看一下_posts下的jekyll给的例子：

	---
	layout: post
	title:  "Welcome to Jekyll!"
	date:   2014-01-27 21:57:11
	categories: jekyll update
	---
	You'll find this post in your `_posts` directory - edit this post and re-build (or run with the `-w` switch) to see your changes!
	To add new posts, simply add a file in the `_posts` directory that follows the convention: YYYY-MM-DD-name-of-post.ext.
	Jekyll also offers powerful support for code snippets:
	def print_hi(name)
	puts "Hi, #{name}"
	end
	print_hi('Tom')
	#=> prints 'Hi, Tom' to STDOUT.
	Check out the [Jekyll docs][jekyll] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll's GitHub repo][jekyll-gh].
	[jekyll-gh]: https://github.com/mojombo/jekyll
	[jekyll]:    http://jekyllrb.com

可以看到在博文的最上方有被两个---包裹起来的一段，这里就定义了文章的一些参数，更多参数在FrontMatter和Variables获取，简单的只需要关注几个就好：
1. title：文章的标题；
2. date：文章的日期；
3. categories：定义了文章所属的目录，一个list，将会根据这个目录的list来创建目录并将文章html放在生成的目录下，文章分类时候用，这里就不使用了；
4. layout：文章所使用的模板名称，也就是_layouts中定义的模板的文件名去掉.html；
5. tags：例子中没有，定义了文章的标签，也是一个list，文章分类时候用，这里就不使用了。

这里就写一个最简单的文章，只是用其中的两个参数：layout，title，如下：

	---
	layout: mylayout
	title: hello-jekyll
	---
	Hello jekyll!

将这个写完的文章保存为 “年-月-日-标题.markdown”的名字形式，因为如果不修改permlinks，jekyll会根据文章的标题来创建文件夹，如2016-09-02-hello会创建成/2016/09/02/hello.html。这里就保存成2016-09-02-hello.markdown。

ps：如果你写文章的时候，把data参数设为当前时间，你可能会发现文章post之后，在网站上却没有显示更新。[用Jekyll创建博客本地正常，上传到GitHub后不能显示文章列表？](https://segmentfault.com/q/1010000004584816/a-1020000004586702),
这个问题是由于jekyll 3（github目前的jekyll版本）默认对于认定为"未来"的post，是不生成的，详情可以参考[Future posts - Jekyll](http://jekyllrb.com/docs/upgrading/2-to-3/#future-posts)。
另外，文章的文件名不要使用中文，否则会出现bug，因为在url中会escape，而服务器查找却是按照escape后的字符串去查找，就会出现找不到文章的情况，使用英文代替就好，定义了title变量就无所谓文件名中标题的内容了。

博客不能没有主页，所以我们修改index.html文件如下：

	---
	layout: mylayout
	title: Hello Jekyll!
	---
	<ul class="posts">
	{% for post in site.posts %}
	  <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ post.url }}">{{ post.title }}</a></li>
	{% endfor %}
	</ul>

还是使用我们刚才的模板，这回编译完成后生成的结果如下：

	<!DOCTYPE html>
	<html>
	    <head>
	        <meta charset="utf-8">
	        <title>test</title>
	    </head>
	    <body>
	        Hello Jekyll!
	        <ul class="posts">
	          <li><span>27 Jan 2014</span> &raquo; <a href="/2014/01/27/hello.html">hello-jekyll</a></li>
	        </ul>
	    </body>
	</html>

由于index文件名中没有时间，所以时间直接被忽略了，而内容段则通过liquid的for标签进行了迭代，遍历了_posts下的所有文章，将其文章的时间、路径、标题组织成html文件，生成指向博文的连接。

<p id = "template"></p>

#### 创建模板

如果你追求，快！那么这里有一些其他博客爱好者编写的一些现成的[模板](http://jekyllthemes.org/)。

当然你也可以自己编写，我们可以打开jekyll给的例子default.html看一看模板的结构:

	<!DOCTYPE html>
	<html>
	    <head>
    	    <meta charset="utf-8">
        	<meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">
        	<title>{{ page.title }}</title>
	        <meta name="viewport" content="width=device-width">
        	<!-- syntax highlighting CSS -->
    	    <link rel="stylesheet" href="/css/syntax.css">
    	    <!-- Custom CSS -->
        	<link rel="stylesheet" href="/css/main.css">
    	</head>
    	<body>
    	    <div class="site">
        	  <div class="header">
            	<h1 class="title"><a href="/">{{ site.name }}</a></h1>
            	<a class="extra" href="/">home</a>
          	</div>
    	      {{ content }}
    	      <div class="footer">
        	    <div class="contact">
            	  <p>
                	Your Name<br />
                	What You Are<br />
	                you@example.com
	              </p>
	            </div>
	            <div class="contact">
	              <p>
	                <a href="https://github.com/yourusername">github.com/yourusername</a><br />
	                <a href="https://twitter.com/yourusername">twitter.com/yourusername</a><br />
	              </p>
	            </div>
	          </div>
	        </div>
	    </body>
	</html>

可以看到，模板和普通的html文件几乎是一样的。jekyll使用的是一个叫liquid的模板引擎创建html文件，这个模板引擎也有详细的文档，现在就只关注其中比较核心的部分，文章的标题和文章的内容。

可以看到模板的有这么两句{{ page.title }}, {{ content }}，这两句就分别是文章标题和文章内容的占位符，如果有文章使用了这个模板，如果使用上面写的那篇hello的文章，
标题就是hello-jekyll，content就是Hello jekyll!，这里定义一个自己的新模板，保存为mylayout.html。

	<!DOCTYPE html>
	<html>
	    <head>
	        <meta charset="utf-8">
    	    <title>test</title>
    	</head>
    	<body>
    	      {{ page.title }}
    	      {{ page.date }}
    	      {{ content }}
    	</body>
	</html>

第一行是标题，然后是博文时间（在文件名中定义），然后是博文内容，这样一个简单的模板就创建好了。

<p id = "err"></p>

#### 诊断调试

在博客文件夹下，在命令行中输入jekyll build --trace就可以将所有文章文件根据其模板进行编译，生成结果，放在根目录下的_site中，
这里我们使用后，会出现如下结果：\weixingtai.github.io\_site\2016\09\02文件夹下有一个hello.html，其内容为：

	<!DOCTYPE html>
	<html>
	    <head>
    	    <meta charset="utf-8">
    	    <title>test</title>
    	</head>
    	<body>
    	      hello-jekyll
    	      2016-09-02 00:00:00 +0800
    	      <p>Hello jekyll!</p>
    	</body>
	</html>

可以看到，这就是编译完的博文文件，如我们设定的，第一行是标题，然后是文件名定义的时间，然后是博文内容，如果编译错误，
将会在命令行中看到一个错误栈，可以方便调试，具体哪里出错了，如果不需要看错误栈，直接使用jekyll build就行了。

如果想要在本地开启一个服务器查看效果，可以使用命令jekyll serve，这样会开启一个监听端口4000的服务器，浏览器中查看localhost:4000，则会进入index.html的内容中，点击文章的标题就可以跳转到具体的博文了。
如果你的电脑安装了福昕阅读器，相信端口占用这个问题你也一定会遇到。[谁占了我的端口 for Windows](http://www.cnblogs.com/lxconan/archive/2016/01/11/5119972.html),这篇文章有详细的解决方法。

主要是以下两个命令，查看并关闭占用端口的程序：

	netstat -ano				//查看各种端口被进程的占用情况
	tasklist /svc /FI "PID eq 11476"	//查看PID对应的进程

接下来，你就可以直接在任务管理器或者系统服务中关闭这个命令。别忘了在服务中把响应程序设置为手动启动。可以避免下次重启后又需要重新操作。

下面打开你的浏览器，输入你刚建的 repository 的文件名，比如我输入 weixingtai.github.io。如无意外，你的个人博客搭建成功了！

如果有意外，可能是之前运行的缓存问题，最简单粗暴的方法。换个浏览器试试！
如果绑定个人域名以后访问不到，可能是域名解析需要一定的时间，少的话一两个小时，多的话可能要二十四个小时。

## 后记

很多事情需要做三遍，是为了从外行看热闹，到内行看门道。如果你觉得，嗯，整个过程是这样子的，
这样做可能会完成得快一点，原来这个方法还可以这样用，那你就是有收获的。

—— Daniel 后记于 2016.02