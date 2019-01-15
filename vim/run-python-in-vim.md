# Vimでプログラムの実行
Vimのプラグインでpythonやrubyなどをvimを閉じずに実行できる`vim-quickrun`というのがある。

~~~
:QuickRun
~~~
ですべてを実行

`option`を渡すと動作を動作を制御できる。例えば、
~~~ vim
" 引数をわたすとき
:QuickRun -arg hoge
" 実行プログラムの指定
:QuickRun python
"バッファを下に分割して出力
:QuickRun -outputter/buffer/split ":botright"
~~~

いちいちオプション指定するのはめんどうなので`g:quickrun_config`にデフォルト値を設定

~~~
let g:quickrun_config = {
   "_":{
       "outputter/buffer/split" : ":botright 8",
       "runner" : "vimproc",
       "runner/vimproc/updatetime" : 40,
   }
}
~~~
設定方法は[quickrunのデフォルト設定](https://github.com/thinca/vim-quickrun/blob/637aa0f9eab485874eb3606be35586735855d880/autoload/quickrun.vim#L16)を見たらわかりやすい。

