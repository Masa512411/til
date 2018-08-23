# JuliaでPythonライブラリを使う。

PyCallを使えばPythonライブラリを実行できる。  
juliaのREPLで以下のコマンドを実行
~~~ julia
Pkg.add("PyCall")
~~~

これでインストール完了！

例えばnumpyを使ってみる。
~~~ julia
using PyCall
@pyimport numpy.random as nr
nr.rand()

# 0.4915255399888825
~~~

このとき `No module named numpy`と言われたら参照するPythonを書き換えたら多分うまくいく。
~~~ julia
ENV["PYTHON"] = "usr/bin/python3"
Pkg.build("PyCall")
~~~
これで書き換わる.

