# Extend Filters

过滤器本质上是可应用于变量的函数。它们用管道运算符`|`调用，可带参数。

```
{{ foo | title }}
{{ foo | join(",") }}
{{ foo | replace("foo", "bar") | capitalize }}
```

### 定义新过滤器

插件可以通过在`过滤器`范围内的入口点定义自定义函数来扩展过滤器。

过滤器函数将第一个参数作为要过滤的内容，并返回新内容。
参考[Context and APIs](./api.md) 了解更多关于 `this` 和 GitBook API.

```js
module.exports = {
    filters: {
        hello: function(name) {
            return 'Hello '+name;
        }
    }
};
```

过滤器 `hello` 之后可用在书中:

```
{{ "Aaron"|hello }}, 你好吗?
```

### 处理块参数

参数可传递给过滤器:

```
Hello {{ "Samy"|fullName("Pesse", man=true}} }}
```

参数被传递给函数，命名参数作为最后参数（对象）传递。

```js
module.exports = {
    filters: {
        fullName: function(firstName, lastName, kwargs) {
            var name = firstName + ' ' + lastName;

            if (kwargs.man) name = "Mr" + name;
            else name = "Mrs" + name;

            return name;
        }
    }
};
```
