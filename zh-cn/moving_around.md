---
layout: content
title: 在系统中四处移动
prev: 介绍
next: 数据类型
link_prev: /zh-cn/introduction.html
link_next: /zh-cn/types_of_data.html
---

早前的 Shell 允许你在系统中四处移动并且运行命令，像 Nu 这样的现代 Shell 同样允许你这么干。让我们看看这些你可能会在与系统交互时用到的命令。

## 观察目录内容

```
> ls
```

正如我们在其他章节所看到的， `ls` 用来观察一个路径下的内容。 Nu 将会以一个表的形式返回你可看到的内容。

`ls` 命令通常可以携带一个可选的参数，来改变你希望观察的目标。例如，我们可以列出以 ".md" 结尾的文件：

```
> ls *.md
───┬────────────────────┬──────┬─────────┬────────────
 # │ name               │ type │ size    │ modified
───┼────────────────────┼──────┼─────────┼────────────
 0 │ CODE_OF_CONDUCT.md │ File │  3.4 KB │ 5 days ago
 1 │ CONTRIBUTING.md    │ File │   886 B │ 5 days ago
 2 │ README.md          │ File │ 15.0 KB │ 5 days ago
 3 │ TODO.md            │ File │  1.6 KB │ 5 days ago
───┴────────────────────┴──────┴─────────┴────────────
```

在可选参数 "\*.md" 前的星号 (\*) 有时候也被叫做通配符。它匹配任何东西。你可以将 "\*.md" 认作 "在当前目录下以 .md 结尾的文件"

Nu 也可以很好地使用现代通配符，来允许你访问更深的目录。

```
 ls **/*.md
────┬───────────────────────────────────────────┬──────┬─────────┬────────────
 #  │ name                                      │ type │ size    │ modified
────┼───────────────────────────────────────────┼──────┼─────────┼────────────
  0 │ .github/ISSUE_TEMPLATE/bug_report.md      │ File │   592 B │ 5 days ago
  1 │ .github/ISSUE_TEMPLATE/feature_request.md │ File │   595 B │ 5 days ago
  2 │ CODE_OF_CONDUCT.md                        │ File │  3.4 KB │ 5 days ago
  3 │ CONTRIBUTING.md                           │ File │   886 B │ 5 days ago
  4 │ README.md                                 │ File │ 15.0 KB │ 5 days ago
  5 │ TODO.md                                   │ File │  1.6 KB │ 5 days ago
  6 │ crates/nu-source/README.md                │ File │  1.7 KB │ 5 days ago
  7 │ docker/packaging/README.md                │ File │  1.5 KB │ 5 days ago
  8 │ docs/commands/README.md                   │ File │   929 B │ 5 days ago
  9 │ docs/commands/alias.md                    │ File │  1.7 KB │ 5 days ago
 10 │ docs/commands/append.md                   │ File │  1.4 KB │ 5 days ago
```

这里我们在寻找任何以 ".md" 结尾的，双星号表示 "任何在当前目录下的子孙目录"。

## 改变当前目录

```
> cd new_directory
```

为了将当前目录改成另一个，我们使用 `cd` 命令。就像其他 Shell 一样，我们可以使用一个目录名，或者用 `..` 来向上一个目录。

## 文件系统命令

Nu 也提供了可跨平台工作的基本文件系统命令。

我们可以通过 `mv` 命令将文件从一个地方移动到另一个地方：

```
> mv item location
```

我们可以把文件复制到另一个地方：

```
> cp item location
```

也可以移除一个项目：

```
> rm item
```

这三条命令同样接受与 `ls` 相同的通配符参数。

最后，我们可以通过 `mkdir` 来新建一个目录：

```
> mkdir new_directory
```
