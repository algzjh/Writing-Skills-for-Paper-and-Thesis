# Using Latex on Ubuntu

## Environment

### Install Latex

```shell
sudo apt-get install texlive-full
sudo apt-get install latex-cjk-all
```

### Install Fonts

Create .fonts folder on home directory. Add some missing fonts needed for thesis.
Some frequently used fonts are:

- simfang.ttf
- SimSun.ttf
- Times New Roman.ttf

The fonts config in the repository is located in `/config/format/general/fonts.tex` or `/config/format/major/cs/fonts.tex`

## Writing Thesis

see the usage of "zjuthesis" at: <https://github.com/TheNetAdmin/zjuthesis/blob/master/docs/usage.md>

在 `zjuthesis.tex` 中 `\documentclass[]{zjuthesis}` 部分填写个人信息，注意以下信息用于控制文档的生成：

- `Degree` 为 `undergraduate` 时，编译本科生论文：

   | Type           | Period               | BlindReview                          | MajorFormat                            |
   | :------------- | :------------------- | :----------------------------------- | :------------------------------------- |
   | thesis: 论文类 | proposal: 开题报告   | true: 生成盲审用 pdf（隐藏个人信息） | 默认: general                          |
   | design: 设计类 | final: 最终论文/设计 | false: 生成提交用 pdf                | 与 `config/format/major/` 下目录名相同 |

- `Degree` 为 `graduate` 时，编译硕士生/博士生论文：

   | Type                 | BlindReview                          | MajorFormat                            | GradLevel    |
   | :------------------- | :----------------------------------- | :------------------------------------- | :----------- |
   | thesis: 学术论文     | true: 生成盲审用 pdf（隐藏个人信息） | 默认: general                          | master: 硕士 |
   | design: 专业学术论文 | false: 生成提交用 pdf                | 与 `config/format/major/` 下目录名相同 | doctor: 博士 |

1. 在 `body` 目录下编写内容
1. 在 `pages` 目录下填写必要的内容，如审核评语等
1. 在 `figure` 目录下保存图片，在 `body/ref.bib` 内插入文献条目
1. 在根目录下运行命令 `latexmk`（或者 `latexmk -xelatex -outdir=out zjuthesis`）即可编译 pdf 文件到 `out` 目录（该目录不会被记录版本）

## Writing Papers

```shell
make clean
make
```
