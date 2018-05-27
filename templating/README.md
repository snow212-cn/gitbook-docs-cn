# Templating

Gitbook用 [Nunjucks 模版语言](https://mozilla.github.io/nunjucks/) 处理页面与主题的模板。
nunjucks语法非常类似**Jinja2** 或 **Liquid**。它的语法用括号`{ }`标记要处理的内容。

### 变量

变量从模板上下文中查找值。如果你只是想显示一个变量，用`{{ variable }}`语法。例如：

```twig
我名字叫 {{ name }}, 见到你很高兴
```

This looks up username from the context and displays it. Variable names can have dots in them which lookup properties, just like JavaScript. You can also use the square bracket syntax.
这时从上下文中查找用户名并显示它。变量名可以加`.`点来查找属性，就像JavaScript一样。也可用方括号语法。

```twig
{{ foo.bar }}
{{ foo["bar"] }}
```

If a value is undefined, nothing is displayed. The following all output nothing if foo is undefined: `{{ foo }}`, `{{ foo.bar }}`, `{{ foo.bar.baz }}`.
如果值未定义，则什么都不显示。如果foo是未定义，以下均无输出: `{{ foo }}`, `{{ foo.bar }}`, `{{ foo.bar.baz }}`.

GitBook提供一组 [predefined  variables](variables.md) 从上下文.

### 过滤器

过滤器本质上是可以应用于变量的函数。它们用管道运算符`|`调用，并可以带参数。

```twig
{{ foo | title }}
{{ foo | join(",") }}
{{ foo | replace("foo", "bar") | capitalize }}
```

第三个示例演示了如何使用链过滤器。它将显示`bar`，即先用`bar`取代`foo`，再大写。

### 标签

##### if

`if`测试一个条件，并允许您选择性地显示内容。它的行为与JavaScript的`if`完全一样。

```twig
{% if variable %}
  It is true
{% endif %}
```

如果变量有定义并计算为true，将显示`It is true`。否则什么都不显示。

可以用`elif`和`else`指定其他条件：

```twig
{% if hungry %}
  I am hungry
{% elif tired %}
  I am tired
{% else %}
  I am good!
{% endif %}
```

##### for

`for` 用于遍历数组和字典。

```twig
# Chapters about GitBook

{% for article in glossary.terms['gitbook'].articles %}
* [{{ article.title }}]({{ article.path }})
{% endfor %}
```

##### set

`set` 允许您创建/修改变量。

```twig
{% set softwareVersion = "1.0.0" %}

Current version is {{ softwareVersion }}.
[Download it](website.com/download/{{ softwareVersion }})
```

##### 包含 和 块

包含和继承在[内容参考](conrefs.md)章节详细介绍。

### 忽略

如果您希望GITBook忽略任何特殊模板标记，您可以用raw，其内部一切都输出为纯文本。
``` twig
{% raw %}
  this will {{ not be processed }}
{% endraw %}
```
