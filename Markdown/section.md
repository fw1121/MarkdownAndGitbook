## 区块元素
### 段落和换行
- 使用`<br/>`标签插入换行
- 在插入处先按入两个以上的空格然后回车

### 标题
Markdown 支持两种标题的语法，类 `Setext` 和类 `atx` 形式。
- 类 `Setext` 形式是用底线的形式，利用 `=` （最高阶标题）和`-` （第二阶标题），例如：

    ```bash
    This is an H1
    =============

    This is an H2
    -------------
    ```

    任何数量的 `=` 和 `-` 都可以有效果。

- 类 `Atx` 形式则是在行首插入 1 到 6 个 `#` ，对应到标题 1 到 6 阶，例如：

    ```bash
    # This is H1

    ## This is H2

    ###### This is H6
    ```

### 区块引用 Blockquotes

Markdown 标记区块引用是使用类似 email 中用 `>` 的引用方式

- 每行的最前面加上 `>`

    ```bash
    > This is a blockquote with two paragraphs.
    > consectetuer adipiscing elit. Aliquam hendrerit
    >
    > Donec sit amet nisl. Aliquam semper ipsum
    > id sem consectetuer libero luctus adipiscing.
    ```

- 在整个段落的第一行最前面加上`>`

    ```bash
    > This is a blockquote with two paragraphs. Lorem ipsum dolor sit amet,
    consectetuer adipiscing elit.

    > Donec sit amet nisl. Aliquam semper ipsum sit amet velit. Suspendisse
    id sem consectetuer libero luctus adipiscin
    ```

- 根据层次加上不同数量的 `>`, 建立区块引用的嵌套（如：引用内的引用）

    ```bash
    > This is the first level of quoting.
    >
    > > This is nested blockquote.
    >
    > Back to the first level
    ```

- 引用的区块内也可以使用其他的 Markdown 语法，包括标题、列表、代码区块等：

    ```bash
    > ## 这是一个标题。
    >
    > 1.   这是第一行列表项。
    > 2.   这是第二行列表项。
    >
    > 给出一些例子代码：
    >
    >     return shell_exec("echo $input | $markdown_script");
    ```

###列表
Markdown 支持**有序列表**和**无序列表**。

- **无序列表**使用星号、加号或是减号作为列表标记：

    ```bash
    *   Red
    *   Green
    *   Blue
    ```
    等同于：

    ```bash
    +   Red
    +   Green
    +   Blue
    ```

    也等同于：
    ```bash
    -   Red
    -   Green
    -   Blue
    ```

- **有序列表**则使用数字接着一个英文句点：

    ```bash
    1.  Bird
    2.  McHale
    3.  Parish
    ```

- 列表项目可以包含多个段落，每个项目下的段落都必须缩进 4 个空格或是 1 个制表符:

    ```bash
    1.  This is a list item with two paragraphs. Lorem ipsum dolor
        sit amet, consectetuer adipiscing elit. Aliquam hendrerit
         mi posuere lectus.

        Vestibulum enim wisi, viverra nec, fringilla in, laoreet
        vitae, risus. Donec sit amet nisl. Aliquam semper ipsum
        sit amet velit.

    2.  Suspendisse id sem consectetuer libero luctus adipiscing
    ```
- 如果要在列表项目内放进引用，那 `>` 就需要缩进：

    ```bash
    *   A list item with a blockquote:

        > This is a blockquote
        > inside a list item.
    ```

### 代码区块
- 要在 Markdown 中建立代码区块很简单，只要简单地缩进 4 个空格或是 1 个制表符就可以
- 如果要在代码区段内插入反引号，你可以用多个反引号来开启和结束代码区段：
    ```
    ``There is a literal backtick (`) here.``
    ```

### 分隔线
你可以在一行中用三个以上的星号、减号、底线来建立一个分隔线，行内不能有其他东西。你也可以在星号或是减号中间插入空格。下面每种写法都可以建立分隔线：
```bash
* * *

***

*****

- - -

---------------------------------------
```
