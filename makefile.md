test
CC  
Cのコンパイラ。デフォルトはcc  
RM  
rm -f  

# 基本
<pre>
ターゲット: 依存するファイル
　　コマンド
</pre>

# マクロ
マクロの定義
<pre>
マクロ名 = 文字列
</pre>
マクロの参照
<pre>
$(マクロ名) または ${マクロ}
</pre>

# 定義済マクロ
|マクロ名|文字列|左記の引数用マクロ|説明|
|:---:|:---:|:---:|:---|
|AR|ar||アーカイブユーティリティ|
|AS|as||アセンブラ|
|CC|cc|CFLAGS|Cコンパイラのコマンド名。|
|CXX|g++|CXXFLAGS|C++コンパイラのコマンド名。|
|CO|co||RCSファイルからリビジョンをチェックアウトする|
|CPP|$(CC) -E|CPPFLAGS|Cプリプロセッサ|
|RM|rm -f||ファイルの削除|


#内部マクロ
|内部マクロ名|説明|
|:---:|:---|
|%|「:」の両側でファイル名の一致する部分。|
|$@|現在のターゲットのフルネーム。「:」の左側のファイル名。|
|$*|現在のターゲットからサフィックス（拡張子）を除いたもの|
|$+|Makefileと同じ順番の依存するファイルの名前|
|$|依存ファイルの先頭のファイル名|
|$?|依存ファイルのうち、更新があったもの|
|$^|依存ファイルのリスト|
|$<|先頭の依存ファイル|


#参考：URL  
http://d.hatena.ne.jp/cou929_la/20090929/1254243607  
http://www.jsk.t.u-tokyo.ac.jp/~k-okada/makefile/
