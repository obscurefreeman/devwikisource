# 语法

网站页面是使用Markdown格式来编辑的，因此Markdown语法全部适用。

此外，为寻求高效便捷，本网站使用了mkdocs作为模板，因此其他适用的语法可以参考[官方维基](https://squidfunk.github.io/mkdocs-material/)。

## 提示

以“笔记”为例，我们来看看有多少种不同的样式。

### 笔记

```
!!! note

    这是一篇笔记。
```

!!! note

    这是一篇笔记。

### 有自定义标题的笔记

```
!!! note "有自定义标题的自定义笔记"

    这是一篇有自定义标题的笔记。
```

!!! note "有自定义标题的自定义笔记"

    这是一篇有自定义标题的笔记。

### 可以折叠的笔记

```
???+ note "可以折叠的笔记"

    这是一篇可以折叠的笔记。
```

???+ note "可以折叠的笔记"

    这是一篇可以折叠的笔记。

除笔记之外，还有几种不同的效果。

??? abstract

    `abstract`摘要
??? info

    `info`详情
??? tip

    `tip`提示
??? success

    `success`成功
??? question

    `question`问题
??? warning

    `warning`警告
??? failure

    `failure`失败
??? danger

    `danger`危险
??? bug

    `bug`漏洞

## 按钮

```
[这是一个按钮](https://obscurefreeman.github.io/sourcewiki/){ .md-button }
```

[这是一个按钮](https://obscurefreeman.github.io/sourcewiki/){ .md-button }

```
[这是一个填充的按钮](https://obscurefreeman.github.io/sourcewiki/){ .md-button .md-button--primary }
```

[这是一个填充的按钮](https://obscurefreeman.github.io/sourcewiki/){ .md-button .md-button--primary }

