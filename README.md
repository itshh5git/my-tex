# My TeX Notes

这是一个个人数学学习笔记与文档仓库，主要使用 LaTeX 编写。仓库按主题或课程分目录保存源文件与已编译的 PDF，并在 `style/` 目录中维护通用宏包、字体、定理环境和版式配置。

## 内容概览

主要笔记包括：

- `A Primer of Algebraic D-modules/`：代数 D-模笔记
- `Algebraic Number Theory/`：代数数论
- `Algebraic Topology/`：代数拓扑
- `Category Theory/`：范畴论
- `Commutative Algebra/`：交换代数
- `complex analysis/`：复分析
- `Differential Geometry/`：微分几何
- `Differential Manifolds/`：微分流形
- `Functional Analysis/`：泛函分析
- `Homological Algebra/`：同调代数
- `PDE/`：偏微分方程
- `real analysis/`：实分析
- `Representation of Groups/`：群表示论
- `Topology/`：拓扑学
- `抽象代数/`：抽象代数

其他目录：

- `style/`：共享 LaTeX 样式文件，包括宏包、宏定义、字体、定理环境和格式设置。
- `简历/`：个人简历源文件与 PDF。
- `答辩ppt/`：答辩相关幻灯片和记录。
- `临时专用/`：临时文档、测试文件和参考文献。

## 仓库结构

```text
.
+-- style/
|   +-- mypackages.sty
|   +-- macro.sty
|   +-- font.sty
|   +-- theorem.sty
|   +-- format.sty
+-- Algebraic Topology/
|   +-- Algebraic Topology.tex
|   +-- Algebraic Topology.pdf
+-- Commutative Algebra/
|   +-- Commutative Algebra.tex
|   +-- Parts/
|   +-- Commutative Algebra.pdf
+-- ...
```

多数主题目录中都有一个主 `.tex` 文件和对应的 `.pdf` 文件。较大的笔记会把章节拆到 `Parts/` 子目录中，并由主文件通过 `\include{...}` 引入。

## 编译环境

建议安装 TeX Live、MiKTeX 或 MacTeX，并确保以下工具可用：

- `xelatex`
- `latexmk`，推荐使用
- 常用 LaTeX 宏包：`amsmath`、`amsthm`、`amssymb`、`fontspec`、`hyperref`、`tikz-cd`、`minitoc`、`titlesec`、`titletoc`、`zref`、`physics` 等

由于 `style/font.sty` 使用了 `fontspec` 并设置了 `Times New Roman`，推荐使用 XeLaTeX 编译。

## 编译方法

进入对应笔记目录后编译主文件。例如：

```powershell
cd "Commutative Algebra"
latexmk -xelatex "Commutative Algebra.tex"
```

也可以直接使用 `xelatex`，通常需要多次编译以生成目录、交叉引用和 `minitoc` 内容：

```powershell
cd "Commutative Algebra"
xelatex "Commutative Algebra.tex"
xelatex "Commutative Algebra.tex"
```

如果主文件中使用了分章节文件，建议始终从主 `.tex` 文件编译，不要单独编译 `Parts/` 下的章节文件。

## 共享样式

新的笔记建议使用下面的导言区结构：

```tex
\documentclass[12pt, oneside]{book}
\usepackage{../style/mypackages}
\usepackage{../style/macro}
\usepackage{../style/font}
\usepackage{../style/theorem}
\usepackage{../style/format}
```

其中：

- `mypackages.sty`：集中加载常用数学、图形、目录、超链接等宏包。
- `macro.sty`：数学常用符号与算子命令。
- `font.sty`：字体设置。
- `theorem.sty`：定理、定义、命题、推论等环境。
- `format.sty`：页面与标题格式。

## 注意事项

- 一些较早的 `.tex` 文件仍可能使用 `\usepackage{../mypackages}` 这类旧路径。如果编译时报找不到样式文件，可以改为引用 `../style/mypackages` 及其他共享样式文件。
- 仓库的 `.gitignore` 已忽略常见 LaTeX 辅助文件，例如 `.aux`、`.log`、`.toc`、`.synctex.gz`、`.fdb_latexmk` 等。
- PDF 文件当前保留在各主题目录中，便于直接阅读和同步。
- 文件名和目录名中包含空格、中文或大小写差异时，命令行中请使用引号包裹路径。

## 维护建议

- 每个主题目录保留一个清晰的主 `.tex` 文件。
- 长篇笔记按章节拆分到 `Parts/`，并在主文件中统一 `\include`。
- 新增通用命令时优先放入 `style/macro.sty`。
- 新增定理类环境时优先放入 `style/theorem.sty`。
- 编译成功后再提交源文件和需要保留的 PDF。
