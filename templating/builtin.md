# 内置模版助手

GitBook 提供了一系列内置过滤器和块来帮您编写模板。

### 过滤器

`value|default(default, [boolean])`
如果value严格未定义，则返回default，否则为value。如果boolean为true，任何JavaScript伪值将返回默认值(false, "", ...)。

`arr|sort(reverse, caseSens, attr)`
用JavaScript的arr.sort函数排序arr。如果reverse是true，结果将被颠倒。Sort默认情况下不区分大小写，但将caseSens设为true会使其区分。如果传递了attr，将和每一项比较attr。

### 块

`{% markdown %}Markdown string{% endmarkdown %}`
翻译内联 markdown

`{% asciidoc %}AsciiDoc string{% endasciidoc %}`
翻译内联 asciidoc
