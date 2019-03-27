Ubuntu 安装latex和配置vscode Latex workshop

1. 安装latex
```
sudo apt-get install texlive-latex-base
sudo apt-get install texlive-latex-extra
sudo apt-get install texlive-scientice
sudo apt-get install texlive-xetex
sudo apt-get install texlive-publishers
sudo apt-get install texlive-fonts-recommended # 字体
sudo apt-get install texlive-fonts-extra # 更多字体，可选
sudo apt-get install latexmk # 要求系统已安装Perl
sudo apt-get install texlive-full # 最后还是提示找不到部分 “.sty” 文件
```
2. latex-workshop settings.json:
```
{
  "editor.wordWrap": "on",
  "editor.wordWrapColumn": 250,
  "latex-workshop.latex.clean.fileTypes": [
        "*.aux",
        "*.bbl",
        "*.blg",
        "*.idx",
        "*.ind",
        "*.lof",
        "*.lot",
        "*.out",
        "*.toc",
        "*.acn",
        "*.acr",
        "*.alg",
        "*.glg",
        "*.glo",
        "*.gls",
        "*.ist",
        "*.fls",
        "*.log",
        "*.fdb_latexmk"
      ],
  "latex-workshop.latex.recipes": [
    {
        "name": "xelatex",
    "tools": [
      "xelatex"
    ]
    },
    {
    "name": "xelatex->bibtex->exlatex*2",
    "tools": [
      "xelatex",
      "bibtex",
      "xelatex",
      "xelatex"
    ]
  },
  {
    "name": "pdflatex ➞ bibtex ➞ pdflatex`×2",
    "tools": [
        "pdflatex",
        "bibtex",
        "pdflatex",
        "pdflatex"
    ]
}],

  "latex-workshop.latex.tools":[
      {
          "name":"xelatex",
          "command": "xelatex",
          "args": [
              "-synctex=1",
              "-interaction=nonstopmode",
              "-file-line-error",
              "%DOC%"
          ]
      }, {
          "name":"bibtex",
          "command": "bibtex",
          "args": [
              "%DOCFILE%"
          ]
      },
      {
        "name": "pdflatex",
        "command": "pdflatex",
        "args": [
        "-synctex=1",
        "-interaction=nonstopmode",
        "-file-line-error",
        "%DOC%"
        ]
    },
  ],
  "latex-workshop.view.pdf.viewer": "tab",
  "window.zoomLevel": 1,
  "latex-workshop.view.autoFocus.enabled": true,
  "latex-workshop.latex.autoClean.run": "onBuilt"
}
```