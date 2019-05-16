# TeX 模板

用于存放一些学校可能用到的 TeX 模板。主要内容在 [preamble.tex](./preamble.tex) 文件，包含了 package 的使用声明及样式、指令等的配置。

## 目录

- [test（不包含参考文献）](test)
- [课程设计报告 / 实习报告（包含参考文献）](course-project)
- [课程实验报告](experiment-report)（已经过时）

## 用法

构建命令使用两遍 `xelatex -shell-escape main.tex`，代码高亮需要额外安装 `pygments` 包（通过 `pip install pygments` 安装）。

建议使用 TeX Live + VS Code + LaTeX Workshop 插件，以实现保存时自动构建以及丰富的自动补全。如果使用 LaTeX Workshop 插件，则配置如下：

```json
{
    "latex-workshop.latex.tools": [
        {
            "name": "xelatex",
            "command": "xelatex",
            "args": [
                "-synctex=1",
                "-interaction=nonstopmode",
                "-file-line-error",
                "-shell-escape",
                "%DOC%"
            ]
        },
        {
            "name": "bibtex",
            "command": "bibtex",
            "args": [
                "%DOCFILE%"
            ]
        }
    ],
    "latex-workshop.latex.recipes": [
        {
            "name": "xelatex",
            "tools": [
                "xelatex",
                "xelatex"
            ]
        },
        {
            "name": "xelatex-bib",
            "tools": [
                "xelatex",
                "bibtex",
                "xelatex",
                "xelatex"
            ]
        }
    ]
}
```

上面的配置中还提供了支持 `bibliography` 的 `xelatex-bib` 构建方案，可以通过 `LaTeX Workshop: Build with recipe` 命令选择，或直接修改配置文件中的 recipe 顺序，使之成为默认方案。
