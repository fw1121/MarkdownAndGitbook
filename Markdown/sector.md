##区段元素
###链接
Markdown 支持两种形式的链接语法： **行内式**和**参考式**两种形式。

不管是哪一种，链接文字都是用 [方括号] 来标记。

- 要建立一个行内式的链接，只要在方块括号后面紧接着圆括号并插入网址链接即可，如果你还想要加上链接的 title 文字，只要在网址后面，用双引号把 title 文字包起来即可，例如：

    ```bash
    This is [an example](http://example.com/ "Title") inline link.

    [This link](http://example.net/) has no title attribute.
    ```

- 如果你是要链接到同样主机的资源，你可以使用相对路径：
    ```bash
    See my [About](/about/) page for details.
    ```

- 参考式的链接是在链接文字的括号后面再接上另一个方括号，而在第二个方括号里面要填入用以辨识链接的标记：
    ```bash
    This is [an example][id] reference-style link.
    ```
    接着，在文件的任意处，你可以把这个标记的链接内容定义出来：

    ```bash
    [id]: http://example.com/  "Optional Title Here".
    ```

    链接内容定义的形式为：
    - 方括号（前面可以选择性地加上至多三个空格来缩进），里面输入链接文字
    - 接着一个冒号
    - 接着一个以上的空格或制表符
    - 接着链接的网址
    - 选择性地接着 title 内容，可以用单引号、双引号或是括弧包着<br>
    下面这三种链接的定义都是相同：
    ```bash
    [foo]: http://example.com/  "Optional Title Here".
    [foo]: http://example.com/  'Optional Title Here'.
    [foo]: http://example.com/  (Optional Title Here).
    ```

### 强调
Markdown 使用星号`*`和底线`_`作为标记强调字词的符号，
- 被 `*` 或`_` 包围的字词会被转成用 `<em>` 标签包围，
- 用 `**` 或 `__ `包起来的话，则会被转成 `<strong>`

```bash
*single asterisks*

_single underscores_

**double asterisks**

__double underscores__
```
- 如果你的 `*` 和 `_` 两边都有空白的话，它们就只会被当成普通的符号

### 图片
- Markdown 使用一种和链接很相似的语法来标记图片，同样也允许两种样式： **行内式**和**参考式**。

    ```bash
    ![Alt text](/path/to/img.jpg)

    ![Alt text](/path/to/img.jpg "Optional title")
    ```
- Markdown 还没有办法指定图片的宽高，如果你需要的话，你可以使用普通的 `<img>` 标签。



