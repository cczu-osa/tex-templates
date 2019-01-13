# TeX 模板

用于存放一些学校可能用到的 TeX 模板。

## 目录

- [课程实验报告](experiment-report)（可能已经过时）
- [课程设计报告 / 实习报告](course-project)

## 用法

建议使用 TeX Live + VS Code 的 LaTeX Workshop 插件，代码高亮可能需要额外安装 `pygmentize` 包。渲染命令使用两遍 `xelatex -shell-escape main.tex`。如果使用 LaTeX Workshop 插件，则配置如下：

```json
{
    "latex-workshop.latex.tools": [
        {
            "name": "xelatex",
            "command": "xelatex",
            "args": [
                "-shell-escape",
                "%DOC%"
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
        }
    ]
}
```

另外，注意可能需要按需修改字体和封面的表格内容。
