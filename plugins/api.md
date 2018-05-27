# Context and APIs

GITBook为插件提供了不同的API和上下文。这些API可以根据所使用的gitbook版本而有所不同，相应地，您的插件要在`package.json`中指定`engines.gitbook`字段。

#### Book 实例

`Book`类是GITBook的核心，它集中所有的访问读取方法。该类定义在[book.js](https://github.com/GitbookIO/gitbook/blob/master/lib/book.js).


```js
// 从 book.json 读配置
var value = book.config.get('title', 'Default Value');

// 解析文件名为绝对路径
var filepath = book.resolve('README.md');

// 翻译行内标记字符串
book.renderInline('markdown', 'This is **Markdown**')
    .then(function(str) { ... })

// 翻译标记字符串 (块模式)
book.renderBlock('markdown', '* This is **Markdown**')
    .then(function(str) { ... })
```

#### Output 实例

`Output` 类表示输出/写入过程。

```js
// 返回output的根目录
var root = output.root();

// 解析根目录中的文件
var filepath = output.resolve('myimage.png');

// 转换文件名到URL (返回指向 html文件的路径)
var fileurl = output.toURL('mychapter/README.md');

// 向输出目录写文件
output.writeFile('hello.txt', 'Hello World')
    .then(function() { ... });

// 复制文件到输出目录
output.copyFile('./myfile.jpg', 'cover.jpg')
    .then(function() { ... });

// 验证文件是否存在
output.hasFile('hello.txt')
    .then(function(exists) { ... });
```

#### Page 实例

Page实例表示当前被解析页面。

```js
// 页面标题 (来自 SUMMARY)
page.title

// 页面内容 (Markdown/Asciidoc/HTML according to the stage)
page.content

// 在书中的相对路径
page.path

// 文件的绝对路径
page.rawPath

// 此文件所用的解析器类型
page.type ('markdown' or 'asciidoc')
```

#### Context for Blocks and Filters

块和筛选器可访问相同的上下文，该上下文绑定到模板引擎执行：

```js
{
    // 当前模版的语法
    "ctx": {
        // 例如, 跟在 {% set message = "hello" %} 后面
        "message": "hello"
    },

    // Book 实例
    "book" <Book>,

    // Output 实例
    "output": <Output>
}
```

例如，筛选器或块函数可用`this.book`访问当前图书。

#### 钩子的上下文

钩子只能用`this.book`访问`<Book>`实例。
