# 中山大学课程论文 LaTeX 模板

本仓库将 `sysuthesis` 的本科页面样式整理为课程论文模板，采用单页封面和一份中文摘要，正文沿用 LaTeX 论文常见的目录、章节、参考文献和附录结构。模板面向课程作业使用；如需提交正式本科、硕士或博士学位论文，请按学校当前规范调整并使用对应模板。

## 快速开始

1. 编辑 `sysusetup.tex`，在 `cover-items` 中填写所有封面信息。
2. 按需修改 `cover-heading` 和 `header-title`，设置封面顶部标题与正文页眉。
3. 每行写成 `\sysucoverrow{行名}{内容}`；添加或删除这条命令即可增删信息行。
4. 在 `docs/` 中编辑摘要和各章节，在 `reference.bib` 中维护参考文献。
5. 编译生成 `main.pdf`。

文档类通过 `course-paper` 选项启用课程论文封面。示例配置：

```tex
\documentclass[fontset=auto,degree=bachelor,oneside,course-paper]{sysuthesis}

\sysusetup{
  cover-heading = {课程论文},
  header-title = {课程论文},
  cover-items = {
    \sysucoverrow{课程名称}{课程名称}
    \sysucoverrow{论文题目}{课程论文标题}
    \sysucoverrow{姓名}{作者姓名}
    \sysucoverrow{学号}{学号}
    \sysucoverrow{院系}{院系名称}
    \sysucoverrow{任课教师}{教师姓名}
  },
}
```

`course-paper` 让本科页面样式只输出一个封面，并把封面题目作为普通信息行显示。正文只保留中文摘要。`cover-heading` 和 `header-title` 分别控制封面顶部标题与正文页眉。所有封面信息都在 `cover-items` 中配置，不需要的行直接删除，需要新行时复制一条 `\sysucoverrow` 并修改标签和内容。

## 编译

需要 TeX Live 2020 或更新版本，并使用 XeLaTeX。编译正文：

```sh
make main
```

也可以直接运行：

```sh
latexmk -xelatex main.tex
```

使用 Debian 或 Ubuntu 的拆分版 TeX Live 时，缺少 `algorithm2e.sty` 可安装 `texlive-science`。运行 `make help` 查看其他 Makefile 命令。

## 文件结构

- `main.tex`：主文档，控制封面、摘要、目录、章节和附录的顺序。
- `sysusetup.tex`：课程信息、作者信息和封面行配置。
- `docs/`：摘要、章节和附录内容。
- `reference.bib`：BibTeX 参考文献数据库。
- `sysuthesis.cls`：页面样式与封面实现。

本项目基于 [SYSU-SCC/sysu-thesis](https://github.com/SYSU-SCC/sysu-thesis) 修改；原项目的许可证和版权说明见 [LICENSE](LICENSE)。
