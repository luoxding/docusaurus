# LaTeX表格示例

## 经典表格样式

- tabularx

```tex
\documentclass[openany]{book}
\usepackage{graphicx}
\usepackage[explicit]{titlesec}

\makeatletter
\let\@chapterimage\relax
\newcommand\chapterimage[1]{%
  \if\relax\detokenize{#1}\relax
  \else
    \gdef\@chapterimage{\smash{\includegraphics[width=4cm,height=5cm,keepaspectratio]{#1}}}
  \fi
}

\titleformat{\chapter}[display]
  {\normalfont\huge\bfseries}
  {}
  {0pt}
  {\parbox[t]{.4\textwidth}{\chaptertitlename\ \thechapter}\hfill
    \parbox[t]{.4\textwidth}{\@chapterimage}\\[20pt]%
    \Huge#1
  }
\titleformat{name=\chapter,numberless}[display]
  {\normalfont\huge\bfseries}
  {}
  {0pt}
  {\parbox[t]{.4\textwidth}{\mbox{}}\hfill
    \parbox[t]{.4\textwidth}{\@chapterimage}\\[20pt]%
    \Huge#1
  }
\titlespacing*{\chapter}{0pt}{0pt}{40pt}

\newcommand\nochapterimage{
  \let\@chapterimage\relax
}
\makeatother

\begin{document}

\chapterimage{dog1}
\chapter*{Test unnumbered chapter}

\nochapterimage
\chapter*{Another test unnumbered chapter}

\chapter{Test numbered chapter}

\chapterimage{dog2}
\chapter{Another test numbered chapter}

\end{document}
```
