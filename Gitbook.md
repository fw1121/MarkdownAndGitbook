# Gitbook 简明教程

Gitbook是一个命令行工具(node.js库)， 使用Github/Git创建漂亮的图书。 你可以看一些用它编写的图书的例子： 学习Javascript. 你也可以很容易的通过gitbook.io网站发布在线图书。 editor 是一个图形化的编辑工具， 提供Windows, Mac 和Linux的版本. 关注Twitter帐号 @GitBookIO.

这篇文章只是一个起步教程，完整的文档可以在help.gitbook.io网站找到.

## 1. 怎么用
GitBook 可以通过 NPM 安装:
```bash
$ npm install gitbook -g
```

你可以将一个repository作为一本书:
```bash
$ gitbook serve ./repository
```

或者简单的生成静态网站:
```bash
$ gitbook build ./repository --output=./outputFolder
```

命令 `build` 和 `serve` 的参数为:
```bash
-o, --output <directory>  输出文件件, 默认为 ./_book
-f, --format <name>       产生的书籍的类型, 默认为静态站点, 可用的格式为: site, page, ebook, json
--config <config file>    配置文件, 默认为 book.js 或 book.json
```
GitBook 会从仓库中的 `book.json`文件加载默认的配置，前提是此文件存在.

下面是此文件的一些配置项:
```bash
{
    // 输出文件夹
    // 注意: 它会覆盖命令行传入的参数
    // 不建议在此文件中配置
    "output": null,
    // 产生的书籍的类型
    // 注意: 它会覆盖命令行传入的参数
    // 不建议在此文件中配置
    "generator": "site",
    // 图书标题和描述 (默认从README抽取)
    "title": null,
    "description": null,
    // 对于ebook格式, 扩展名the extension to use for generation (default is detected from output extension)
    // "epub", "pdf", "mobi"
    // 注意: 它会覆盖命令行传入的参数
    // 不建议在此文件中配置
    "extension": null,
    // GitHub 信息(defaults are extracted using git)
    "github": null,
    "githubHost": "https://github.com/",
    // 插件列表, can contain "-name" for removing default plugins
    "plugins": [],
    // 插件通用配置
    "pluginsConfig": {
        "fontSettings": {
            "theme": "sepia", "night" or "white",
            "family": "serif" or "sans",
            "size": 1 to 4
        }
    },
    // 模版中的链接 (null: default, false: remove, string: new value)
    "links": {
    	// Custom links at top of sidebar
    	"sidebar": {
    	    "Custom link name": "https://customlink.com"
    	},
        // Sharing links
        "sharing": {
            "google": null,
            "facebook": null,
            "twitter": null,
            "weibo": null,
            "all": null
        }
    },
    // PDF 参数
    "pdf": {
        // Add toc at the end of the file
        "toc": true,
        // Add page numbers to the bottom of every page
        "pageNumbers": false,
        // Font size for the fiel content
        "fontSize": 12,
        // Paper size for the pdf
        // Choices are [u’a0’, u’a1’, u’a2’, u’a3’, u’a4’, u’a5’, u’a6’, u’b0’, u’b1’, u’b2’, u’b3’, u’b4’, u’b5’, u’b6’, u’legal’, u’letter’]
        "paperSize": "a4",
        // Margin (in pts)
        // Note: 72 pts equals 1 inch
        "margin": {
            "right": 62,
            "left": 62,
            "top": 36,
            "bottom": 36
        }
    }
}
```
## 2. 输出格式
GitBook可以产生下列类型的图书:

- 静态站点: 默认格式. 创建一个完全交互式的静态网站，可以发布到GitHub Pages等网站.

- eBook: 图书完成后可以使用它创建电子书. 创建命令: gitbook ebook ./myrepo. 你需要安装 `ebook-convert` 输出格式可以是 PDF, ePub 或 MOBI.
  - Generate a **PDF** using: `gitbook pdf ./myrepo ./mybook.pdf`
  - Generate a **ePub** using: `gitbook epub ./myrepo ./mybook.epub`
  - Generate a **MOBI** using: `gitbook mobi ./myrepo ./mybook.mobi`

- 单页网页: 可以生成一个单页的HTML网页。这个格式可以用来转换PDF或者eBook. 创建命令: `gitbook build ./myrepo -f page`.

- JSON: 此格式用来调试或者抽取图书的元数据. 创建命令: `gitbook build ./myrepo -f json`.

## 3. 图书格式
一本图书就是一个Git repository， 至少包含两个文件: `EADME.md` 和 `SUMMARY.md`.

**README.md**

&emsp;&emsp;典型的, 它应该是你的图书的介绍. 它可以自动的被加到最终的summary中.

**SUMMARY.md**

&emsp;&emsp;`SUMMARY.md` 定义了你的图书的结构. 它应该包含章节的列表,以及它们的链接.

例如:
```bash
# Summary
This is the summary of my book.
* [section 1](section1/README.md)
    * [example 1](section1/example1.md)
    * [example 2](section1/example2.md)
* [section 2](section2/README.md)
    * [example 1](section2/example1.md)
```

不被`SUMMARY.md`包含的文件不会被gitbook处理.

**多语言**

&emsp;&emsp;GitBook 支持使用多种语言编写图书. 每种语言应该是一个子目录， 遵循正常gitbook格式, `LANGS.md`文件应该被放到repository的根文件夹， 格式如下:
```bash
* [English](en/)
* [French](fr/)
* [Español](es/)
```

**词汇表**

&emsp;&emsp;允许你列出条目以及它们的定义. 基于这些条目 gitbook会自动创建一个索引，并在页面中加亮这些条目.

`GLOSSARY.md` 格式很简单 :
```bash
# term
Definition for this term
# Another term
With it's definition, this can contain bold text and all other kinds of inline markup ...
```

**忽略文件和文件夹**

&emsp;&emsp; GitBook 读取`.gitignore`, `.bookignore` 和 `.ignore` 得到需要忽略的文件/文件夹的列表. (文件的格式和 `.gitignore`一样).

&emsp;&emsp;`.gitignore`最佳实践是忽略build文件，这些文件来自 **node.js** (`node_modules`, ...) 和GitBook的build文件: `_book`, `*.epub`, `*.mobi` and`*.pdf`.

**封面**

&emsp;&emsp;封面文件为: /cover.jpg.
尺寸为 1800x2360. 插件 autocover可以自动创建一个文件.

&emsp;&emsp;封面的小尺寸图形为: /cover_small.jpg.

**发布图书**

&emsp;&emsp;平台 GitBook.io就像"Heroku for books": 你可以在它上面创建图书 (公开的, 付费的, 或者私有的)， 并且使用 git push 就可以更新.

**插件**

&emsp;&emsp;插件可以扩展图书的功能. 查看插件介绍 GitbookIO/plugin来了解如何创建一个插件.

**调试**

&emsp;&emsp;增加环境变量 `DEBUG=true` 来得到更好的错误信息(包含错误堆栈).例如:
```bash
$ export DEBUG=true
$ gitbook build ./
```
----
{% include book.myCopyright %}


