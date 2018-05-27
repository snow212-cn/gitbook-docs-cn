# Plugins

插件是扩展GitBook功能性的最佳方式，包括电子书和网站。已存在的插件可做很多事：数学公式显示支持，用`谷歌分析`追踪访问等。

### 如何找插件?

插件很容易在[plugins.gitbook.com](https://plugins.gitbook.com)找到。

### 如何安装？

找到插件后想安装，你需要把它添加到`book.json`:

```js
{
    "plugins": ["我的插件", "其它插件"]
}
```

你也可以明确指定其版本：`"我的插件@0.3.1"`。默认情况下，会解析和当前Gitbook兼容的最新版。

### legacy.gitbook.com

插件是自动去[legacy.gitbook.com](https://legacy.gitbook.com)安装的。在本地，执行`gitbook install`即可安装和准备所需的插件。

### 配置插件

插件配置存储于`pluginsConfig`。你必须查阅插件自带文档，以获得可用的配置信息。
