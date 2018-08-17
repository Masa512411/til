# $愛しのJulia$

juliaはいいとこどりの言語で、Cのように速く、Rubyのように動的で、pythonのように汎用的に使える。  
juliaの面白いところは、ノートで式を書くのと同じ書き方で書けるところだ。  

## Juliaの面白く、便利なところ  
まず `*` を省略できる。
~~~ julia
x = 10
y = 3x+2

println(y)

#32
~~~

比較もスマートに

~~~ julia
x = 5

if 1 < x < 6
    println("Yes")
end

# Yes
~~~

変数の埋め込みもらくらく
~~~ julia
name = "Amas"


println("Hello $name !")

# Hello Amas !
~~~

行列もわかりやすくかける
~~~ julia
x = [1 2 3
     4 5 6
     7 8 9]

y = eye(3)

println(x * y)

# 3×3 Array{Float64,2}:
    0.0  2.0  3.0
    4.0  4.0  6.0
    7.0  8.0  8.0
~~~



