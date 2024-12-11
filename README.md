
## 前言


之前在【[基于.NetCore 开发博客项目 StarBlog \- (32\) 第一期完结](https://github.com)】里说到 StarBlog 的 Vue 前端系列已经写好了


本来打算后面再发的，不过最近有点懒没去写新的文章 😂 还是整理一些老文发出来吧\~



> PS：这个系列的文章最后编辑于 2023 年 6 月


本公众号开通了付费文章的功能，我打算在这个 StarBlog Vue 系列上开始尝试一下。不想付费也没关系，您可以在我的博客上完整阅读本系列的全部文章\~


如果有同学觉得我的文章有帮助，可以在公众号付费支持一下，一点不起眼的鼓励都是对创作者莫大的鼓励！


另外再碎碎念一下\~


对于创作变现，我一直没有明确的规划，运营公众号和博客纯粹是作为兴趣爱好，以及作为日常学习的记录。


之前我也一直缺乏完全转型的决心，但在如今大环境寒冬的背景下，行业形势愈发严峻，也许还得等很久，才能迎来下一轮经济爆发期。


所以我建议各位程序员朋友，即使目前有稳定的收入，也应该居安思危，尝试拓展一下副业，多一种选择也多一种未来的可能。


如今的付费文章只能算在初步摸索，接下来我会尝试更多的“商业模式”，不打工是每个打工人的终极梦想，毕竟理想总要有的嘛，万一实现了呢？😃


## 本系列内容规划


本系列的写作背景是从零开始边学边用 Vue 开发一套博客的管理后台，写作视角是 Vue 的初学者，所以挺适合刚入门的同学阅读。


整个项目已经开源，搭配源码阅读的话效果更佳: [https://github.com/Deali\-Axy/StarBlog\-Admin](https://github.com)


内容覆盖到 StarBlog 博客的后台功能，包括：


* 页面路由
* SASS 与 SCSS
* 第三方图标库的使用
* 网络通信
* 登录页面编写
* 主页面（使用 Vue 实现多标签页）
* 状态管理与 Vuex
* vue\-router 路由
* 常见页面布局（Grid、Flex、瀑布流等）
* 常用交互功能（文件上传、弹窗）
* 富文本编辑器
* 第三方组件库使用（主要是 ElementUI）
* 可视化大屏开发
* 常见问题与解决
* 扩展学习资料


本项目的技术不是最新的，不过实现的功能覆盖到管理后台常见的功能需求。


比起各种高大上的模板，本系列更侧重于一步步学习，并且在学习中举一反三。


最终把管理后台这个开发场景随便拿捏 😎


## 环境准备


说了这么多，终于开始正题了，本文的内容很简单，就是安装环境和创建项目。


### NodeJs


现代前端开发讲究工程化，万物基于 Nodejs 这个 JavaScript 运行环境


### 入门版


首先需要安装 NodeJs


最简单的方式是在官网下载安装


下载地址: [http://nodejs.cn/download/](https://github.com)


### 进阶版


使用 NVM 管理 Nodejs 环境是更好的选择，可以安装多个版本，随时能切换，方便得很。


在 Windows 平台开发的话，如果搭配 scoop 之类的包管理器，体验更好。


详情见我今年春节后开工发的文章:


* [2024 年，提升 Windows 开发和使用体验的一些实践 \- 包管理器篇](https://github.com)
* [2024 年，提升 Windows 开发和使用体验实践 \- 终端\&命令行篇](https://github.com)


关于 NVM 的使用不是本文的重点，请参考 NVM 官网: [https://github.com/nvm\-sh/nvm](https://github.com):[milou加速器](https://xinminxuehui.org)


### 安装前端工具链


国内使用 NPM 需要设置国内镜像才能正常安装，之前常用的淘宝镜像说是要停止解析了，可以用这个 **npmmirror 中国镜像**，命令如下：



```
npm config set registry https://registry.npmmirror.com

```

npmmirror 中国镜像站官网：[https://npmmirror.com/](https://github.com)


更多配置国内镜像的内容可以参考我之前的博客：[https://mp.weixin.qq.com/s/TQt7r\-xyphy2KfrOvg2OBA](https://github.com)


#### 安装 webpack


新版本的脚手架都是内置的了，不过 StarBlog 用的 Vue 比较老… 需要自己安装



```
npm install -g webpack

```

#### 安装 vue\-cli


Vue 项目必须安装这个脚手架


前端组件必须特别注意版本，很多奇奇怪怪的问题都是版本不兼容导致的


具体到本项目，使用的 vue 版本是 2\.5\.2



```
npm install -g vue-cli

```

#### 安装 yarn


Yarn 是 Facebook 发布的 node.js 包管理器，比 npm 更快、更高效，可以使用 Yarn 替代 npm。


关于 yarn 我在之前的这篇博客里有提到: [代码使我头疼之 React 初学习](https://github.com)


安装命令



```
npm install -g yarn

```

设置国内镜像，跟 NPM 的操作一样



```
yarn config set registry https://registry.npmmirror.com

```


> PS：顺便提一嘴，我现在用 pnpm 更多，感觉是更好的选择，不过新手还是用 yarn 吧，简单好用，pnpm 还是有一些坑的，这里就不展开了\~


## 创建项目


使用 `vue-cli` 来创建项目



```
vue init webpack starblog-admin-ui

```

然后会问一堆信息，我是这样填的：



```
> vue init webpack starblog-admin-ui

? Project name: starblog-admin-ui
? Project description: Admin dashboard of StarBlog
? Author: DealiAxy 
? Vue build standalone
? Install vue-router? Yes
? Use ESLint to lint your code? No
? Set up unit tests: No
? Pick a test runner: noTest
? Setup e2e tests with Nightwatch? No
? Should we run `npm install` for you after the project has been created? (recommended) yarn

```

最后一步可以选 `Yes use npm` 和 `Yes use yarn`，毫无疑问我选了 yarn，然后回车



```
# Project initialization finished!
# ========================

To get started:

  cd starblog-admin-ui
  npm run dev

Documentation can be found at https://vuejs-templates.github.io/webpack

```

搞定！`vue-cli` 很贴心，帮我们把依赖也安装好了\~


## 运行测试


自动生成项目的目录结构如下



```
starblog-admin-ui
├── build
├── config
├── node_modules
├── src
├── static
├── test
├── README.md
├── index.html
├── package.json
└── yarn.lock

```


> 另外提一点，Windows 的 `tree` 命令不支持定义要显示的目录层级，这里我选择了基于 Node 的 `tree-node-cli` 工具
> 
> 
> 只需要 `npm install -g tree-node-cli` 即可
> 
> 
> 要实现以上的效果，命令是：`treee -L 1`


切换到项目目录下，执行命令



```
yarn run dev

```

提示



```
 DONE  Compiled successfully in 2301ms                                                                          
 I  Your application is running here: http://localhost:8080

```

OK，打开浏览器测试一切正常\~ （截图我就不放了）


## 安装 ElementUI


vue 的 UI 好像不是很多，先选这个 elementUI 吧，后续再看看


话不多说


官网文档：[https://element.eleme.cn/\#/zh\-CN/component/installation](https://github.com)


### 安装依赖


直接命令



```
yarn add element-ui

```

### 导入项目


修改 `src/main.js` 文件


原本长这样



```
import Vue from 'vue'
import App from './App'
import router from './router'

Vue.config.productionTip = false

/* eslint-disable no-new */
new Vue({
  el: '#app',
  router,
  components: {App},
  template: ''
})

```

添加了 ElementUI 之后长这样



```
import Vue from 'vue'
import App from './App'
import router from './router'
import ElementUI from 'element-ui'
import 'element-ui/lib/theme-chalk/index.css'

Vue.config.productionTip = false

Vue.use(ElementUI)

/* eslint-disable no-new */
new Vue({
  el: '#app',
  router,
  components: {App},
  template: ''
})

```

OK 然后打开默认的页面，`src/components/HelloWorld.vue`


随便找个地方添加一个 elementUI 的按钮



```
<el-button type="primary">按钮el-button>

```

然后打开浏览器测试一下，能看到按钮就是引入 ElementUI 成功了\~


准备篇到这就收工啦。


