# Linux

### Linuxの起動と終了

#### システムのブート
電源ONからLinuxが起動するまでの処理の流れ  

1. 電源ON  
1. BIOSの起動  
1. ブートローダーの起動  
1. カーネルの起動  
1. 起動プロセスの実行  
1. Linuxシステムの起動  

### カーネルの実態
<pre>
$ ls -l /boot  
vmlinuz-3.16.0-24-generic
</pre>
### カーネルのバージョンの確認
<pre>
$ uname -r
3.16.0-24-generic
</pre>
### モジュールのファイルの場所
<pre>
/lib/modules/カーネルのバージョン  
</pre>

### 現在組み込まれているモジュールの一覧
<pre>
$ lsmod
Module                  Size  Used by
nls_utf8               12557  1 
isofs                  39837  1 
bnep                   19543  2 
':
</pre>

