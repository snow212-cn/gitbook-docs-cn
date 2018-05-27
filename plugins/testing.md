# 测试你的插件

### 测试你的插件在本地

在出版前测试你的插件，可以用[npm link](https://docs.npmjs.com/cli/link)。

在插件文件夹中，运行：

```bash
$ npm link
```

然后在你书籍的目录中:

```bash
$ npm link gitbook-plugin-<插件名>
```

### 单元测试在Travis

[gitbook-tester](https://github.com/todvora/gitbook-tester)使得为插件编写**Node.js/Mocha**单元测试更容易。用[Travis.org](https://travis.org)，测试可运行在每个commits/tags上。
