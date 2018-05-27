# 变量

以下是书籍解析和主题生成过程中可用数据的参考。

### 全局变量

| Variable | Description |
| -------- | ----------- |
| `book` | `book.json`中的全书信息+配置设定。详见下文. |
| `gitbook` | GitBook 信息 |
| `page` | 当前页信息 |
| `file` | 当前页相关文件信息 |
| `readme` | 关于Readme的信息 |
| `glossary` | 关于Glossary（术语表）的信息 |
| `summary` | 关于目录的信息 |
| `languages` | 多语言书籍的语言列表 |
| `output` | 关于输出生成器的信息 |
| `config` | `book.json`的转储 |

### Book 变量

| Variable | Description |
| -------- | ----------- |
| `book.[CONFIGURATION_DATA]` | All the `variables` set via the `book.json` are available through the book variable. |
| `book.language` | Current language for a multilingual book |

### GitBook 变量

| Variable | Description |
| -------- | ----------- |
| `gitbook.time` | The current time (when you run the `gitbook` command) . |
| `gitbook.version` | Version of GitBook used to generate the book |

### File 变量

| Variable | Description |
| -------- | ----------- |
| `file.path` | The path to the raw page |
| `file.mtime` | Modified Time. Last time the file was modified |
| `file.type` | The name of the parser used to compile this file (ex: `markdown`, `asciidoc`, etc) |

#### Page 变量

| Variable | Description |
| -------- | ----------- |
| `page.title` | Title of the page |
| `page.previous` | Previous page in the Table of Contents (can be `null`) |
| `page.next` | Next page in the Table of Contents (can be `null`) |
| `page.dir` | Text direction, based on configuration or detected from content (`rtl` or `ltr`) |

#### 目录变量

| Variable | Description |
| -------- | ----------- |
| `summary.parts` | List of sections in the Table of Contents |

The whole table of contents (`SUMMARY.md`) can be accessed:

`summary.parts[0].articles[0].title` will return the title of the first article.

#### 多语言book 变量

| Variable | Description |
| -------- | ----------- |
| `languages.list` | List of languages for this book |

Languages are defined by `{ id: 'en', title: 'English' }`.

### Output 变量

| Variable | Description |
| -------- | ----------- |
| `output.name` | Name of the output generator, possible values are `website`, `json`, `ebook` |
| `output.format` | When `output.name == "ebook"`, `format` defines the ebook format that will be generated, possible values are `pdf`, `epub` or `mobi` |

### Readme 变量

| Variable | Description |
| -------- | ----------- |
| `readme.path` | Path to the Readme in the book |

### Glossary 变量

| Variable | Description |
| -------- | ----------- |
| `glossary.path` | Path to the Glossary in the book |
