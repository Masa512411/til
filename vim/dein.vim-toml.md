# dein.tomlの書き方 
別ファイルでVimの設定ができ、init.vimをスマートにできる。  
init.vimにはtomlファイルを読み込む部分だけを書けばいい。  

## init.vimでの設定
~~~vim
  let s:toml_dir    = $HOME . '/.config/nvim/toml'  
  let s:toml      = s:toml_dir . '/dein.toml'  
  let s:lazy_toml = s:toml_dir . '/dein_lazy.toml'

  call dein#load_toml(s:toml,      {'lazy': 0})
  call dein#load_toml(s:lazy_toml, {'lazy': 1})
~~~

<br> 

## Tomlファイルの書き方
***
tomlファイルでは設定を読み込むタイミングを指定でき軽量化を図ることができる。  
例えばhook_addで指定したらプラグインが認識されたときに読み込まれる。

## dein.toml
~~~vim
"基本はプラグインのレポジトリー指定だけ
[[plugins]]
repo = 'Shougo/deoplete.nvim'
hook_add = 'let g:deoplete#enable_at_startup = 1'
~~~

lazyというフラグを立てれば遅延読み込みをすることができる。  
init.vimで `{'lazy':1}` でlazyがonになる。`{'lazy':0}` だと起動時に読み込まれる。
## dein_lazy.toml

~~~vim
[[plugins]]
repo = 'thinca/vim-quickrun'
on_ft = ['python']

hook_source = '''
au FileType qf nnoremap <silent><buffer>q :quit<CR>
let g:quickrun_config = {
    \'_' : {
           \  'outputter/buffer/split' : ':botright 8sp',
           \  'outputter/buffer/into'  : '1',
           \  'outputter/error/success': 'buffer',
           \  'outputter/quickfix/errorformat' : '%f:%l,%m in %f on line %l',
           \},    
           \}
'''
~~~
<br>

## 読み込みタイミングのOption
***
* **on_i**  &emsp; 1を指定するとインサートモードに入ったとき読み込まれる。
* **on_ft** &emsp; 指定したファイルタイプの時に読み込まれる。
* **on_path** &emsp; バッファ名が一致した時に読み込まれる。.*を指定すると何かのファイルを開いた時に読み込まれるので、filerなどのプラグインで使うと便利。
* **on_source** &emsp; 記載されたプラグインが読み込まれた後に読み込まれる。
* **on_cmd** &emsp; コマンドが実行された時に読み込まれる。`['Unite', 'UniteResume']`のようなプラグインのコマンドを指定する。
* **on_map** `on_cmd`のマッピング版で`['<Plug>(neosnippet_expand_or_jump)']`のように指定する。
* **depends** &emsp; プラグイン間で依存性がある場合に使う。
* **if** &emsp; `has("nvim")` などのように書いて条件に一致した場合のみ読み込まれる
<br>
<br>


## hook機能と種類
***
設定を実行するタイミングをhookで分けて設定できる。

## hookの種類

|Hook name|Timing|lazy Off|lazy On|  
|:--|:--:|:--:|:--:|
|hook_add| プラグインが dein.vim によって追加されたとき|OK|OK
|hook_source| プラグインが読み込まれる直前|NG |OK
|hook_post_source |プラグインが読み込まれた直後 |NG |OK
|hook_post_update |プラグインが更新された直後 |OK |OK
|hook_done_update|プラグイン全ての更新が終わった直後 |OK |OK
















