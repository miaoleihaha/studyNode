# npm

#### npm（全称 Node Package Manager）是 Node.js 的包管理工具，它是一个基于命令行的工具，用于帮助开发者在自己的项目中安装、升级、移除和管理依赖项。

#### npm命令

- **npm init** 

  - pack name(包名)
  - version (版本)
  - description(描述)
  - entry point (入口文件)
  - keywords (关键字-方便搜索)
  - license (开源协议)

  ###### npm init会生成一个package文件

  - name：项目名称，必须是唯一的字符串，通常采用小写字母和连字符的组合。
  - version：项目版本号，通常采用语义化版本号规范。
  - description：项目描述。
  - main：项目的主入口文件路径，通常是一个 JavaScript 文件。
  - keywords：项目的关键字列表，方便他人搜索和发现该项目。
  - author：项目作者的信息，包括姓名、邮箱、网址等。
  - license：项目的许可证类型，可以是自定义的许可证类型或者常见的开源许可证（如 MIT、Apache 等）。
  - dependencies：项目所依赖的包的列表，这些包会在项目运行时自动安装。
  - devDependencies：项目开发过程中所需要的包的列表，这些包不会随项目一起发布，而是只在开发时使用。
  - peerDependencies：项目的同级依赖，即项目所需要的模块被其他模块所依赖。
  - scripts：定义了一些脚本命令，比如启动项目、运行测试等。
  - repository：项目代码仓库的信息，包括类型、网址等。
  - bugs：项目的 bug 报告地址。
  - homepage：项目的官方网站地址或者文档地址。

  ```js
  {
  
   "name": "nodetest", //包名
   "version": "1.0.0", //版本
   "description": "---", //描述
   "main": "index.js", //入口文件
   "scripts": { // 执行命名了或者运行脚本
    "test": "echo \"Error: no test specified\" && exit 1"
   },
   "repository": {
    "type": "git",
    "url": "git+https://github.com/miaoleihaha/studyNode.git"
   },
  
   "keywords": [
    "study",
    "node"
   ],
   "author": "miaolei",
    "license": "ISC",
    "bugs": {
      "url": "https://github.com/miaoleihaha/studyNode/issues"
    },
    "homepage": "https://github.com/miaoleihaha/studyNode#readme",
    "dependencies": {
      "loadsh": "^0.0.4"
    },
    "devDependencies": {
      "md5": "^2.3.0"
    }
  }
  ```

  


- **npm install**：安装一个包或一组包，并且会在当前目录存放一个node_modules。

  --save 版本第不会放在**dependencies**文件里 造成**依赖丢失**

  **dependencies** ：npm i 包名\npm i 包名 --save 

  生产环境所需依赖

  比如 vue、vuex

  **devDependencies**：  npm i 包名 --save -dev\npm i 包名 -D

  开发依赖都装到这

  比如 webpack、vite 生产环境不需要

  **peerDependencies**：

  给编写插件人员或npm包开发人员使用

  

- **npm install** <package-name>：安装指定的包。

  npm install 安装模块的时候一般是扁平化安装的，但是有时候出现嵌套的情况是因为版本不同
  A 依赖 C1.0,
  B 依赖 C1.0,
  D 依赖 C2.0,
  此时C 1.0就会被放到A B的node_moduels,
  C2.0 会被放入D模块下面的node_moduels

- npm install <package-name> --save：安装指定的包，并将其添加到 package.json 文件中的依赖列表中。

- npm install <package-name> --save-dev：安装指定的包，并将其添加到 package.json 文件中的开发依赖列表中。

- npm install -g <package-name>：全局安装指定的包。

- npm update <package-name>：更新指定的包。
- npm uninstall <package-name>：卸载指定的包。
- **npm run** <script-name>：执行 package.json 文件中定义的脚本命令。
- npm search <keyword>：搜索 npm 库中包含指定关键字的包。
- npm info <package-name>：查看指定包的详细信息。
- npm list：列出当前项目中安装的所有包。
- npm outdated：列出当前项目中需要更新的包。
- npm audit：检查当前项目中的依赖项是否存在安全漏洞。
- npm publish：发布自己开发的包到 npm 库中。
- npm login：登录到 npm 账户。
- npm logout：注销当前 npm 账户。
- npm link: 将本地模块链接到全局的 node_modules 目录下
- **npm config list** 用于列出所有的 npm 配置信息。执行该命令可以查看当前系统和用户级别的所有 npm 配置信息，以及当前项目的配置信息（如果在项目目录下执行该命令）
- **npm get registry** 用于获取当前 npm 配置中的 registry 配置项的值。registry 配置项用于指定 npm 包的下载地址，如果未指定，则默认使用 npm 官方的包注册表地址
- **npm set registry npm config set registry <registry-url>** 命令，将 registry 配置项的值修改为指定的 <registry-url> 地址