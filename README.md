# 搭建pixi游戏环境
>此项目基于pixi.js v5版本，以一个简单的拼图游戏为例，演示了怎么搭建一个完整pixi游戏的开发环境，从开发到最终构建。

### 截屏

![demo](./doc/demo.png)

### 需要会的技术栈(你能学到什么)
* 需要会`pixi.js`v5版本，需要会使用`texturepacker`工具打包图集。
* 本项目为nodejs项目(使用`npm init`初始化项目)，所以本机需要安装nodejs环境，`nodejs`环境仅仅用于打包，和开发无关。
* 需要了解`requirejs(AMD)`模块化的使用方式，会编写`AMD`模块。
* 采用`es6`语法编写，但模块化用的`requrejs`方式，没有采用`es6`模块化的原因是目前尚有不少的第三方库并不支持`es6`。`requirejs`仅仅在开发期间使用，正式打包时候会用`webpack`将所有`js`文件(自己写的代码和第三方库)合并为一个文件`game.min.js`，并且会将所有`es6`的语法转换为`es5`以便达到最大的兼容性。
* 构建脚本使用`gulp`，需要安装`gulp`环境，构建脚本会合并混淆`js`文件，压缩图片等等。
* 需要少量的`css`和`html`知识，当浏览器视口大小发生变化时候，利用`css`对`canvas`进行自适应。
* 需要会搭建本地的一个`http`服务器，推荐使用`http-server`(`npm install -g http-server`安装)

### 目录及文件说明
* `res`目录: 存放`texturepacker`图集项目，字体等等。
* `src`目录: 存放完整游戏项目，包括自己编写的`js`，第三方库，游戏资源(图片，音频等等)，游戏的`html`页面。
* `dist`目录: 此目录为构建脚本动态生成，存放构建完成的项目文件，每次构建都会重新生成这个目录。
* `.babelrc`文件: 构建脚本将`es6`转`es5`时候需要的配置文件。
* `.eslintrc.json`文件: 配置`es6`语法检查器语法检查规则
* `.eslintignore`文件: 配置`es6`语法检查器忽略检查的目录和文件
* `.gitattributes`文件: `git`提交时候`mac/unix`和`windows`换行符不一致，利用这个将所有系统换行符都统一。
* `.gitignore`文件: 配置`git`仓库忽略的文件。
* `.gulpfile.js`文件:`gulp`构建脚本，用于发布项目时候时候构建和优化整个项目。
* `package.json`文件: `node`项目的配置文件。

### 使用项目
* 启动`http`服务器，如果用的`http-server`的话可以在项目根目录直接运行`http-server`就会启动服务器，然后浏览器访问`http://localhost:8080/src`就能看到项目效果。


### 项目构建
* 首先需要在项目根目录运行`npm install`来安装项目依赖的库。
* 项目根目录运行`npm run debug`可构建`debug`版本的项目，最终所有文件会拷贝到`dist`目录下，会合并所有的`js`文件，但并未混淆用于排错。
* 项目根目录运行`npm run dist`可构建`release`版本的项目，最终所有文件会拷贝到`dist`目录下，会合并所有的`js`文件并混淆，优化图片资源。