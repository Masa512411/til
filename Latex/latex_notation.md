# Latex記法  

## 基本スタイル
~~~ tex
\documentclass[a4j]{jsarticle}

\title{タイトル}
\author{著者}
\date{日付}

\begin{document}
\maketitle

\end{document}
~~~

## 画像の挿入
~~~ tex
\usepackage[dvipdfmx]{graphicx}

\begin{document}

\begin{figure}[htbp]
  \centering
  \includegraphics[オプション]{図のファイル名}
  \caption{図のキャプション}
\end{figure}

\end{document}
~~~
### オプション
| Option | Meaning |
| ------ | ------- |
| width  | 幅       |
| height | 高さ      |
| scale  | 拡大縮小率   |
| angle  | 回転率     |
| clip   | はみ出しを切る |
  
### 指定位置
| 位置指定 | 意味         |
| ---- | ---------- |
| h    | 記述した場所に出力  |
| t    | ページの上端に出力  |
| b    | ページの下端に出力  |
| p    | 表専用のべーじを用意 |

  
## 表の挿入
~~~ tex
\begin{document}

\begin{table}[htbp]
 \centering
 \caption{表のキャプション}
 \begin{tabular}{|c|c|c|c|}
  \hline
  a & b & c & d \\ \hline
  1 & 2 & 3 & 4 \\ \hline
  A & B & C & D \\ \hline
 \end{tabular}
\end{table}

\end{document}
~~~

## ソースコード挿入時のテンプレ
~~~ tex
\usepackage{listings,jlisting}
\lstset{
  basicstyle={\ttfamily},
  identifierstyle={\small},
  commentstyle={\smallitshape},
  keywordstyle={\small\bfseries},
  ndkeywordstyle={\small},
  stringstyle={\small\ttfamily},
  frame={tb},
  breaklines=true,
  columns=[l]{fullflexible},
  numbers=left,
  xrightmargin=0zw,
  xleftmargin=3zw,
  numberstyle={\scriptsize},
  stepnumber=1,
  numbersep=1zw,
  lineskip=-0.5ex
}

\begin{document}

\begin{lstlisting}[caption=hello.c]
#include<stdio.h>
int main(void){
  printf("Hello,World!\n");
  return 0;
}
\end{lstlisting}

\end{document}
~~~