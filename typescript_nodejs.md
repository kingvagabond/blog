# Windows下Typescript的nodejs项目基建

现在主流的javascript三大framework里，react与vue越来越接近，而angular渐渐淡出。另外，尽量少使用这些framework的需求开始增强。那么在Windows下纯粹使用typescript与nodejs的项目框架，是个有趣的需求。很多时候想用typescript编一个实用的本地程序，应该怎么做呢？

1. typescript是javascript的现代超集，有很多优点。三大框架react，angular和Vue都采用了typescript，即使不用这三大框架，采用typescript也成为一个大趋势。

2. 使用node.js的目的，是把它当作ts或者js文件的运行环境，也是利用它自带的npm作为所需库包的管理器。所以，需要从官网下载安装node.js。升级node.js的唯一办法也就是下载最新版安装。对64位Windows系统来说，选择64位LTS(Long Term Support)即可。

3. 装好以后，在CMD命令行下输入"node -v"即可查看版本。一般来说，有些代码比较旧的项目需要低版本的node.js，那么无法同时在两个项目下工作，需要切换node.js的版本。node.js好像也有类似python的虚拟环境，但是似乎没什么人用，普遍采用nvm来切换node的版本。nvm在windows下的安装点击[这里](https://github.com/coreybutler/nvm-windows)。切换起来也不难，参看nvm的命令说明即可。

4. 主流工作环境还是vs code。基本不需要安装特殊插件。有一些插件属于锦上添花但非必需。

5. 新建一个工作目录，然后在CMD字符界面下进入那个目录，运行命令"code ."，即用vscode打开那个目录，这是最常用的开始编程的工作方式，vs code的统一启动方式。

6. 在vs code下按Ctrl+Shift+`打开Terminal窗口，输入以下命令安装全局的typescript：

```
npm install -g typescript
```

-g 参数表明这是global安装，也就是本机系统的全局安装，其实装在当前Windows用户的nvm包的目录下。对typescript没给参数，缺省安装最新版本。如果已经装有typescript，运行上述命令等于升级到最新版typescript。

7. 在Terminal窗口下输入"npm init"命令，完成当前工作目录的项目初始化。这个命令会提示一系列问题，绝大部分答案都很直观，缺省答案也足够安全，唯一需要把主文件改成ts后缀名，比如app.ts。运行完毕，当前项目目录下会生成package.json文件。该文件类似于python项目里的requirements.txt，还有更多功能。

8. 按理现在已经可以进行编程。比如新建一个app.ts文件，内容如下：

```
"use strict";
// exports.__esModule = true;
function welcomePerson(person:any) {
    console.log("Hey " + person.firstName + " " + person.lastName);
    return "Hey " + person.firstName + " " + person.lastName;
}
var james = {
    firstName: "James",
    lastName: "Quick"
};
welcomePerson(james);
```

在Terminal窗口输入"node app.ts"即可运行，看到输出。

9. 接下来做项目的typescript配置，在Terminal窗口运行命令"tsc --init"，则在项目目录下新建tsconfig.json文件，并给出了缺省typescript配置。对该文件进行修改，比如target的值从es5改为es6，可以将项目ts文件编译成ES6而不是ES5。这里我们可以做的修改是，增加一行：

```
"outDir": "./dist",
```

然后在Terminal窗口命令行输入命令"tsc"，即可看到app.ts被编译成app.js，保存在输出的dist子目录下。

上面就是完整的typescript与node.js编程项目的基建介绍。有了这个基础知识，我们就可以做编程工作了。对于vscode下的调试，将在新一篇中介绍。