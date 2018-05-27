# 内容参考

内容参考 (conref) 是方便从其它文件和书籍重用内容的一个机制

### 导入本地文件

用`include`标签很容易导入其他文件内容：

```twig
{% include "./test.md" %}
```

### 从另一本书导入文件

使用Git，可解析包含路径：

```twig
{% include "git+https://github.com/GitbookIO/documentation.git/README.md#0.0.1" %}
```

git url的格式:

```
git+https://user@hostname/owner/project.git/file#commit-ish
```

真正的Git URL部分应该以`.git`结束，在`.git`之后提取要导入的文件名，直到URL的片段。

`commit-ish`可以是任何标签、SHA或分支，作为参数提供给`git checkout`的。默认值是`master`。

### 继承

模板继承是一种使模板易于重用的方法。编写模板时，可以定义能让子模板覆盖的`blocks`。继承链可任意长度。

`block`定义模板上的一部分并用名称标识它。基模板可指定块，子模板可用新内容覆盖它们。

```twig
{% extends "./mypage.md" %}

{% block pageContent %}
# 这是我的页面内容
{% endblock %}
```

在文件`mypage.md`中，应指定可扩展块:

```twig
{% block pageContent %}
这是默认内容
{% endblock %}

# 许可

{% include "./LICENSE" %}
```
