# 模块化

[Nodejs](https://so.csdn.net/so/search?q=Nodejs&spm=1001.2101.3001.7020) 模块化规范遵循两套一 套`CommonJS`规范另一套`esm`规范

#### [CommonJS](https://so.csdn.net/so/search?q=CommonJS&spm=1001.2101.3001.7020) 规范

引入模块（require）支持四种格式

1. 支持引入内置模块例如 `http` `os` `fs` `child_process` 等nodejs内置模块
2. 支持引入第三方模块`express` `md5` `koa` 等
3. 支持引入自己编写的模块 ./ …/ 等
4. 支持引入addon C++扩展模块 .node文件

```
const fs = require('node:fs')// 导入核心模块
const express = require("express") // 导入node_modules 目录下的模块
const mlModule = require("xxx.js") //导入相对路径下的模块
const nodeModule = require('xxx.node') // 导入扩展模块
```

到处模块exports和module.exports

```
module.exports={
aa:1,
fn:()=>'qq'
}
```

如果不想导出对象直接导出值

```
module.exports = 111
```

#### ESM模块规范

引入模块**import**必须卸载头部

注意使用**ESM**模块的时候必须开启一个选项
打开**package.json** 设置 **type:module**

```
import fs from 'node:fs'
```

如果要引入**json**文件需要特殊处理 需要增加断言并且指定类型json node低版本不支持

```
import data from './data.json' assert { type: "json" };
console.log(data);
```

加载模块的整体对象

```
import * as all from 'xxx.js'
```

动态导入模块

import静态加载不支持掺杂在逻辑中如果想动态加载请使用import函数模式

```
if(true){
import('xxx').then()
}
```

模块导出

- 导出一个默认对象default只能有一个不可重复export default

  ```
  export default {
  name :'test'
  }
  ```

- 导出变量

  ```
  export const a = 1
  ```

#### Cjs 和 ESM 的区别

1. Cjs是基于**运行时的同步加载**，esm是**基于编译时的异步加载**
2. Cjs是可以**修改**值的，esm值并且**不可修改**（可读的）
3. Cjs不可以tree shaking，esm支持tree shaking
4. commonjs中顶层的this指向这个**模块本身**，而ES6中顶层this指向**undefined**

参考网址 ：https://xiaoman.blog.csdn.net/article/details/132273528