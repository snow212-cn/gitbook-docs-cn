# 创建并发布插件

插件是个node包，发布在NPM上并遵守协定。

## 结构

#### package.json

`package.jSON`是一个用于描述**Node.js 模块**的清单格式。GITBook插件是建立在node模块之上的。它声明了在GITBook中运行插件所需的依赖关系、版本、所有权和其他信息。这篇文档详细描述了纲要。

插件清单`package.json`还可以包含有关所需配置的详细信息。配置模式在`package.jSON`的“GITBook”字段中定义(此字段遵循[JSON-Schema](http://json-schema.org) 指南)：

```js
{
    "name": "gitbook-plugin-mytest",
    "version": "0.0.1",
    "description": "This is my first GitBook plugin",
    "engines": {
        "gitbook": ">1.x.x"
    },
    "gitbook": {
        "properties": {
            "myConfigKey": {
                "type": "string",
                "default": "it's the default value",
                "description": "It defines my awesome config!"
            }
        }
    }
}
```

从 [NPM documentation](https://docs.npmjs.com/files/package.json)了解更多关于`package.json`的内容.

**包名称**必须从'gitbook-plugin-'开始，并且**包引擎**应该包含'gitbook'。

#### index.js

`index.js`是插件runtime的主要入口点:

```js
module.exports = {
    // Map of hooks
    hooks: {},

    // Map of new blocks
    blocks: {},

    // Map of new filters
    filters: {}
};
```

## 发布插件

插件可发布到 [NPM](https://www.npmjs.com).

要发布插件, 你需要创建账号在 [npmjs.com](https://www.npmjs.com)， 然后执行命令行:

```bash
$ npm publish
```

## 私有插件

私人插件可以托管在GITHUB上，并用`Git`URL包含：

```js
{
    "plugins": [
        "myplugin@git+https://github.com/MyCompany/mygitbookplugin.git#1.0.0"
    ]
}
```
