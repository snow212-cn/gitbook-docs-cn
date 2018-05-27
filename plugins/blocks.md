# Extend Blocks

扩展模板块是提供额外功能的最佳方式。

最常见的用法是运行时在标签内处理内容。它就像[filters](./filters.md)，因为你不局限于单一表达式。

### 定义一个新块

块是由插件定义的，块是与块描述符相关的名称映射。块描述符至少包含一个`process`方法。

```js
module.exports = {
    blocks: {
        tag1: {
            process: function(block) {
                return "哈喽 "+block.body+"，你好吗?";
            }
        }
    }
};
```

`process`应返回将替换标签的HTML内容。参考[Context and APIs](./api.md)以了解更多`this`和Gitbook API。


### Handling block arguments

可以给块传递参数:

```twig
{% tag1 "参数 1", "参数 2", name="测试" %}
这是块体
{% endtag1 %}
```

而且在 `process` 方法中可以轻松访问参数:

```js
module.exports = {
    blocks: {
        tag1: {
            process: function(block) {
                // block.args 等于 ["参数 1", "参数 2"]
                // block.kwargs 等于 { "name": "测试" }
            }
        }
    }
};
```

### 处理子块

定义的块可被解析成不同子块，例如，我们考虑源码：

```twig
{% myTag %}
    Main body
    {% 子块1 %}
    Body of sub-block 1
    {% 子块2 %}
    Body of sub-block 1
{% endmyTag %}
```
