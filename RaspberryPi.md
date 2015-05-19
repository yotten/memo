
#LinuxPC上にビルドツリーを作成する
カーネルのビルドに必要なツールをインストール。
<pre>
$ sudo apt-get install build-essential libncurses-dev git git-core
</pre>

カーネルツリーを取得
<pre>
$ git clone https://github.com/raspberrypi/linux
</pre>
※　上記では30分立っても1%も進まなかったので、  
　　オプション_-depth 1_を付けて最新リビジョンだけを取得。約10分で取得完了。
