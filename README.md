# XCPC 算法竞赛模板

个人 ICPC / XCPC（ACM）参赛算法模板手册的 LaTeX 源码：每一节给出可直接使用的代码模板，并配有简明的使用说明与时间复杂度标注。编译得到的成书 PDF 通过 **GitHub Releases** 发布，不在仓库中维护。

## 编译

需要 XeLaTeX 及常用宏包（`ctexbook`、`amsmath`、`minted`、`hyperref` 等，TeX Live 2022+ / MiKTeX 均可）。在仓库根目录执行两遍：

```bash
xelatex -shell-escape -interaction=nonstopmode -halt-on-error main.tex
xelatex -shell-escape -interaction=nonstopmode -halt-on-error main.tex
```

- `-shell-escape` 供 `minted` 调用 Pygments 做代码高亮，样式见 `vslight.style.minted`（`_minted/` 为生成目录）。
- 第二遍用于稳定目录与交叉引用。
- 仓库不含任何编译产物（见 `.gitignore`）；`*.log`、`_minted/` 等请勿提交。

## 目录结构

```
main.tex                  # 主文档（ctexbook）
vslight.style.minted      # minted 高亮样式（VSCode Light 风格）
frontmatter/              # 前言等前置内容
chapters/                 # 正文章节
└─ index.tex              # 章节入口：依次 \input 各专题
```

## 内容一览

| 目录 | 收录内容 |
|---|---|
| `basic` | 快速幂、三分、离散化、格雷码 |
| `math/Combination` | 组合数学基础、二项式定理与二项式反演 |
| `math/LinearAlgebra` | 矩阵、高斯消元、线性基 |
| `math/NumberTheorem` | 质数筛、Miller–Rabin、Pollard–Rho、exgcd、CRT/exCRT、欧拉函数、原根、BSGS、Cipolla（二次剩余） |
| `math/Numberic` | 拉格朗日插值、牛顿迭代法 |
| `math/Polynomials` | FFT / FWT（位运算卷积）/ NTT 及多项式全家桶 |
| `geometry/2D` | 点、直线、凸包、多边形与面积交、圆/三角、各类距离 |
| `data_structure` | 树状数组、并查集（含可撤销）、ST 表、线段树（静态/开点/可持久化）、笛卡尔树、平衡树（FHQ Treap、Splay）、莫队（普通/带修） |
| `tree` | LCA（O(1) RMQ、树链剖分）、长链剖分、虚树、Prufer 序列、Link Cut Tree |
| `graph` | 强连通分量与缩点、割点与割边、边双连通、欧拉路径/回路、最短路、Matrix-Tree 定理、KM（二分图最大权匹配）、网络流（最大流/费用流/上下界/Gomory–Hu） |
| `strings` | KMP、Manacher、Z 函数（exKMP）、Lyndon 分解、后缀数组、AC 自动机、广义后缀自动机（GSAM）、回文树（PAM/Eertree）、Thue–Morse 序列 |
| `other` | 高精度、分数、取模运算类、复数、时空优化、STL 常用库（pb_ds、`__int128`、左偏树） |

## Releases

成书 PDF 以版本号形式发布在 <https://github.com/Kendieer/XCPC-Templates/releases>，文件名如 `Kendieers-Template-v20260903B.pdf`。

## 使用约定

- 部分模板为**片段式**：会在当前作用域就地声明变量/闭包，需要配套上下文（如邻接表 `G`、点数 `n`）才能运行，具体前置条件写在各节说明里。
- 平衡树等数据结构按**多重集**语义使用：允许重复值，`remove(x)` 仅删除其中一个相等元素。
- 模板假设键值/数值落在类型的开区间 `(MIN, MAX)` 内，不处理等于类型极值的输入。
