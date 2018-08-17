# 面白い関数の引数

juliaは関数の引数の型が違うものは名前が同じでも別の定義`(multiple dispatch)`ができる。

~~~ julia
function s(x::Float64) #引数は浮動小数
    x * 10
end

function s(y::Int64) ＃引数は整数
    y + 5
end
~~~
実行結果は

~~~ julia
s(3.6660), s(60)

# (36.66,65)
~~~
