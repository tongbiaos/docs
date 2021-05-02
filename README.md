---
typora-copy-images-to: image
typora-root-url: ./
---

## docsify

本系列文档都是使用docsify来编写的，在本档中记录了docsify的使用方法。

官网：https://docsify.js.org/#/

![img](/image/wps1.jpg)

类似产品：gitbook

### 初始化项目

#### 1.安装docsify-cli 工具

官网推荐全局安装 docsify-cli 工具，可以方便地创建及在本地预览生成的文档。这里使用的是nodejs的包管理工具npm

npm i docsify-cli -g

![img](/image/wps2.jpg) 

可以看到docsify-cli工具安装到了如下位置

![img](/image/wps3.jpg) 

#### 2.初始化项目

使用命令docsify init xxx，初始化一下项目。这里我们初始化了一个hello项目

![img](/image/wps4.jpg) 

初始化成功后，可以看到生成了hello目录，其下创建的3个文件  

①index.html 入口文件 

②README.md 会做为主页内容渲染 

③.nojekyll 用于阻止 GitHub Pages 忽略掉下划线开头的文件 

我们直接编辑 hello/README.md 就能更新文档内容，当然也可以添加更多页面。

![img](/image/wps5.jpg) 

![img](/image/wps6.jpg) 

#### 3.本地预览

通过运行 docsify serve 启动一个本地服务器，可以方便地实时预览效果。默认访问地址 http://localhost:3000 。  

docsify serve xxx，这里我们启动之前新建的hello项目。

![img](/image/wps7.jpg) 

默认效果如下，可以看到空空如也

![img](/image/wps8.jpg)

### 编辑md文档



#### 1.使用Typora编辑文档

详细内容参考本文位置：[Typora用法](#Typora用法)

![image-20210427145453186](/image/image-20210427145453186.png)

### 多页文档

如果需要创建多个页面，或者需要多级路由的网站，在 docsify 里也能很容易的实现。例如创建一个 guide.md 文件，那么对应的路由就是 /#/guide。

![image-20210427162214077.png](/image/image-20210427162214077.png)

在hello项目下新建一个WORK_BTR.md，然后同样使用Typora对其进行编辑，预览时特别注意网址的写法。

![image-20210427165355557.png](/image/image-20210427165355557.png)

![image-20210427165613817.png](/image/image-20210427165613817.png)

对比一下，在根目录下新建一个子文件夹，并在子文件夹下新建一个readme.md文件，其网址如下：

![/image/image-20210427165803029.png](/image/image-20210427165803029.png)

![/image/image-20210427165259749.png](/image/image-20210427165259749.png)

#### 子目录图片显示问题

![image-20210429184610420](/image/image-20210429184610420.png)

### 定制侧边栏

#### 侧边栏管理多页面

下图是index.html中的默认配置，其对应的侧边栏样式如下：

![image-20210427180039000](/image/image-20210427180039000.png)

![image-20210427180126743.png](/image/image-20210427180126743.png)

我们在根目录下新建一个子文件info，其下建立md文件readme和history，并简要编辑其内容。

![image-20210427231429684.png](/image/image-20210427231429684.png)

在根目录下新建_sidebar.md，并且将刚才新建的info下的readme和history加入其中。

![image-20210427231451641.png](/image/image-20210427231451641.png)

![image-20210427231645793](/image/image-20210427231645793.png)

修改根目录下的index.html文件，修改如下：

![image-20210427180454303](/image/image-20210427180454303.png)

可以看到name对应左侧侧边栏的标题，repo对应右上角的GitHub仓库链接图标。而loadSidebar: true；使得侧边栏样式也发生了改变。

![image-20210427231931833.png](/image/image-20210427231931833.png)

当我们点击“首页”和“历史”时，显示的对应的就是info下的readme.md和history.md。

![image-20210427232204442.png](/image/image-20210427232204442.png)

![image-20210427232213895](/image/image-20210427232213895.png)

#### 侧边栏嵌套

你可能想要浏览到一个目录时，只显示这个目录自己的侧边栏，这可以通过在每个文件夹中添加一个 _sidebar.md 文件来实现。

_sidebar.md 的加载逻辑是从每层目录下获取文件，如果当前目录不存在该文件则回退到上一级目录。例如当前路径为 /zh-cn/more-pages 则从 /zh-cn/_sidebar.md 获取文件，如果不存在则从 /_sidebar.md 获取。

下图是我根目录下_sidebar.md的配置，效果如下：

![image-20210427234919637](/image/image-20210427234919637.png)

![image-20210427234846548](/image/image-20210427234846548.png)

我这里想要info下的显示的侧边栏与根目录下的不一样，故在info下新建一个_sidebar.md，修改如下：

![image-20210427235030209](/image/image-20210427235030209.png)

![image-20210427235137214](/image/image-20210427235137214.png)

可以看到，当我们访问info下面的文档是，侧边栏确实显示不一样的信息

![image-20210427235155705](/image/image-20210427235155705.png)

？？没明白alias的作用？？回退是指什么？？

![image-20210427232727272](/image/image-20210427232727272.png)

#### 显示目录

自定义侧边栏同时也可以开启目录功能。设置 subMaxLevel 配置项。

![image-20210428000030847](/image/image-20210428000030847.png)

效果如下;

![image-20210427235941264.png](/image/image-20210427235941264.png)

#### 目录折叠

docsify官方并不支持侧边栏折叠，目前只能通过第三方插件实现或者自己DIY。

https://github.com/iPeng6/docsify-sidebar-collapse

### 定制导航栏

#### 显示导航栏

可以用 HTML 创建一个导航栏。  注意：文档的链接都要以 #/ 开头。

![image-20210428000629776](/image/image-20210428000629776.png)

![image-20210428000544794.png](/image/image-20210428000544794.png)

#### md文件配置导航

新建_navbar.md文件，并在其中编写目录

![image-20210429210540040](/image/image-20210429210540040.png)

![image-20210429211728097](/image/image-20210429211728097.png)

修改index.html中的配置。

```
  <script>
    window.$docsify = {
      name: '系统信息',
	  //仓库地址
      repo: 'https://github.com/tongbiaos/docs',
	  //自定义侧边栏
	  loadSidebar: true,
	  //自定义导航栏
	  loadNavbar: true,
	  //开启目录，并设置最大层级
	  subMaxLevel: 6,
	  //开启封面
	  //coverpage: true,
	  //开启全文检索
	  search: 'auto', // 默认值
    }
  </script>
```

效果如下：

![image-20210429211800181](/image/image-20210429211800181.png)

### 全文检索

![image-20210428095028396](/image/image-20210428095028396.png)

注意检索前，需要清空一下浏览器的缓存数据，然后重新加载网页，获取最新的网页数据，然后再检索。

![image-20210428095112239.png](/image/image-20210428095112239.png)

### 封面

通过设置 coverpage 参数，可以开启渲染封面的功能。

#### 基本用法



### 部署

我们可以把文档网站部署到 GitHub Pages 上，但对于国内用户来说，码云的访问速度显然会更快一些。

#### 1.部署到github

##### 域名映射

这里我使用一个我的二级域名来完成映射，修改github上的pages中Custom domain。

![image-20210502173633522](/image/image-20210502173633522.png)

注意配置完成之后会多一个CNAME文件。

![image-20210502182849710](/image/image-20210502182849710.png)

在阿里云上配置一下二级域名的映射记录，注意记录类型。

![image-20210502173822135](/image/image-20210502173822135.png)

#### 2.部署到码云



### 参考文档

[沉默王二]: https://blog.csdn.net/qing_gee/article/details/109854642	"入坑 docsify，一款神奇的文档生成利器！"

链接引用，不显示

![image-20210428102606168.png](/image/image-20210428102606168.png)



## Markdown语法

### 标题

用 # 可以表示标题，一级标题对应一个 # ，二级标题对应两个 # 号，最多至六级标题。



### 插入视频

#### iframe

![image-20210429195815086](/image/image-20210429195815086.png)

实例测试：这种情况会默认加载视频并播放，

![image-20210429195913235](/image/image-20210429195913235.png)

![image-20210429195608541](/image/image-20210429195608541.png)

#### video

![image-20210429200528737](/image/image-20210429200528737.png)

测试效果：

![image-20210429201726034](/image/image-20210429201726034.png)

![image-20210429201804001](/image/image-20210429201804001.png)

### 插入pdf

![image-20210502171113415](/image/image-20210502171113415.png)

在PC上显示正常，还可以显示指定页数，但是在android上就显示得不是太好。

![image-20210502171418483](/image/image-20210502171418483.png)

### 本页内/其他页跳转

![image-20210429192050877](/image/image-20210429192050877.png)

本页内测试效果：[跳转到“Typora用法-图片”](#图片)

其他页跳转测试效果：[跳转到“鸿学院-市场结构梳理归纳”](info/hongAcademy#市场结构梳理归纳)

![image-20210429193824474](/image/image-20210429193824474.png)

## Typora用法

一个markdown文件的编辑器，我目前就在用这个来编辑文件，外观如下：

![image-20210429212413842](/image/image-20210429212413842.png)

### 标题

在Typora中，# 后要紧接着一个空格才能表示标题，否则就是普通字符。Ctrl+0表示段落，Ctrl+1（2，3，4，5，6）表示相对应的标题。

![image-20210427140803932](/image/image-20210427140803932.png)

注意在规划标题时最好保留一级标题不使用，留给最终的目录。

### 段落

#### 首行缩进

![image-20210427142347696.png](/image/image-20210427142347696.png)

### 图片

在插入图片前，要先设置好图片的根目录。

![image-20210427140307419.png](/image/image-20210427140307419.png)

另外要设置好插入本地图片时，复制图片到项目文件夹的指定目录内，我一般是放在image中。这样在使用浏览器查看的时候图片也能正常显示。

![image-20210427140002732.png](/image/image-20210427140002732.png)

![image-20210427141342726.png](/image/image-20210427141342726.png)

### 页面内跳转

先插入一个超链接

![image-20210427155315541.png](/image/image-20210427155315541.png)

在[]中填入要显示的文字，()中填入#和跳转的标题。

![image-20210427154953687.png](/image/image-20210427154953687.png)

### 超链接

网上的一个教程：[最齐全的Typora使用教程](https://blog.csdn.net/qq_41261251/article/details/102817673?utm_medium=distribute.pc_relevant_t0.none-task-blog-2%7Edefault%7EBlogCommendFromMachineLearnPai2%7Edefault-1.control&dist_request_id=&depth_1-utm_source=distribute.pc_relevant_t0.none-task-blog-2%7Edefault%7EBlogCommendFromMachineLearnPai2%7Edefault-1.control)

