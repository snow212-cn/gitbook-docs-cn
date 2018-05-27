# Hooks

钩子是一种用自定义回调函数增强或改变进程行为的方法。

### 钩子列表

### 全局管道相关

| Name            | Description                                 | Arguments |
|:----------------|:--------------------------------------------|:----------|
| `init`          | 调用在解析书之后, 生成输出和书页之前.       | 无        |
| `finish:before` | 调用在生成书页之后, 在复制 assets和封面之前 | 无        |
| `finish`        | 调用于其它一切之后.                         | 无        |

### 页面管道相关

> 推荐使用 [模版](./templating.md) 来扩展页面解析功能.

| Name          | Description                                             | Arguments |
|:--------------|:--------------------------------------------------------|:----------|
| `page:before` | 在页面上运行模板引擎之前调用 | 页对象    |
| `page`        | 在输出和给页编索引之前调用。         | 页对象    |

##### 页对象

```js
{
    // Parser named
    "type": "markdown",

    // File Path relative to book root
    "path": "page.md",

    // Absolute file path
    "rawpath": "/usr/...",

    // Title of the page in the SUMMARY
    "title": "",

    // Content of the page
    // Markdown/Asciidoc in "page:before"
    // HTML in "page"
    "content": "# Hello"
}
```

##### 添加标题示例

在`page:before`钩子中, `page.content` 就是 markdown/asciidoc 内容.

```js
{
    "page:before": function(page) {
        page.content = "# Title\n" +page.content;
        return page;
    }
}
```

##### 替换html示例

在`page`钩子中, `page.content` 是从 markdown/asciidoc 转换而生成的HTML。

```js
{
    "page": function(page) {
        page.content = page.content.replace("<b>", "<strong>")
            .replace("</b>", "</strong>");
        return page;
    }
}
```


### 异步操作

钩子回调可以是异步的并返回promises。

示例:

```js
{
    "init": function() {
        return writeSomeFile()
        .then(function() {
            return writeAnotherFile();
        });
    }
}
```
