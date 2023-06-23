# docker
参考：https://maku77.github.io/p/y2biqx6/
## イメージを取得する
<pre>
$ docker image pull ubuntu:20.04
20.04: Pulling from library/ubuntu
56e0351b9876: Pull complete
Digest: sha256:f8f658407c35733471596f25fdb4ed748b80e545ab57e84efbdb1dbbb01bd70e
Status: Downloaded newer image for ubuntu:20.04
docker.io/library/ubuntu:20.04
$
</pre>
## イメージの一覧を表示する
<pre>
$ docker image ls
REPOSITORY       TAG       IMAGE ID       CREATED             SIZE
sample/webrick   latest    d1c7f0169613   About an hour ago   864MB
ubuntu           20.04     626a42b93d93   2 weeks ago         72.8MB
$
</pre>
## イメージを削除する
<pre>
$ sudo docker image rm ubuntu:20.04
</pre>
## Docker コンテナを起動する
<pre>
$ sudo docker container run ubuntu:20.04 echo Hello World!
Hello World!
$
</pre>
## 公式のhello-worldコンテナを実行
<pre>
$ sudo docker run hello-world
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
719385e32844: Pull complete
Digest: sha256:c2e23624975516c7e27b1b25be3682a8c6c4c0cea011b791ce98aa423b5040a0
Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/

$
</pre>
## 起動中のコンテナを確認
<pre>
$ sudo docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
$
</pre>
-a オプションを付けて停止中のコンテナも表示
<pre>
$ sudo docker ps -a
CONTAINER ID   IMAGE          COMMAND               CREATED          STATUS                      PORTS     NAMES
daea1e57f08e   hello-world    "/hello"              5 minutes ago    Exited (0) 5 minutes ago              flamboyant_wozniak
52a4a39ac6a8   ubuntu:20.04   "echo Hello World!"   18 minutes ago   Exited (0) 18 minutes ago             sweet_jennings
$
</pre>
* docker rm [CONTAINER ID（daea1e57f08e）]でコンテナの削除する
* docker rmi [イメージ名(hello-world)]でイメージを削除する
## sudoを付けないとエラーになる
### エラーメッセージ
<pre>
$ docker container ls
permission denied while trying to connect to the Docker daemon socket at unix:///var/run/docker.sock: Get "http://%2Fvar%2Frun%2Fdocker.sock/v1.24/containers/json": dial unix /var/run/docker.sock: connect: permission denied
$
</pre>
### 解決策
以下コマンドでユーザーをdockerグループに追加することで解決。
<pre>
sudo usermod -aG docker $USER
</pre>

# Linux

### Linuxの起動と終了

#### システムのブート
電源ONからLinuxが起動するまでの処理の流れ  

1. 電源ON  
1. BIOSの起動  
最近はUEFIの場合あり。
1. ブートローダーの起動  
最近の多くのLinuxでは_GNU GRUB2_というブートローダが使われている。  
デュアルブートの場合は、GRUBの画面で起動するOSを選ぶ。
1. カーネルの起動  
1. 起動プロセスの実行  
初期設定や初期化を行う
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

raspberry piのバージョン
<pre>
pi@raspberrypi ~ $ uname -r
3.18.7+
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

### printkによるデバッグ
printkに使用する主なメッセージレベル  
include/linux/kernel.h  
デフォルトのログレベルは「4」。

|名前|レベル|エイリアス関数|意味|
|:---|:---:|:---|:---|
|KERN_ALERT|1|pr_alert|ユーザが対応する必要がある深刻なエラー|
|KERN_CRIT|2|pr_cirt|深刻で回復不能なエラー|
|KERN_ERR|3|pr_err|一般的なエラーメッセージ|
|KERN_WARNING|4|pr_warning|エラーではないがユーザーに対する警告|
|KERN_NOTICE|5|pr_notis|エラーではないがユーザにとって重要な情報|
|KERN_INFO|6|pr_info|ごく一般的な情報|
|KERN_DEBUG|7|pr_debug|デバッグメッセージ|

現在のシステムのレベルは/proc/sys/kernel/printkで確認できる。
<pre>
$ cat /proc/sys/kernel/printk
3       4       1       3
</pre>
左から現在の設定、デフォルトの設定、最小設定、起動時の設定を意味する。

autoconfをインストール。
<pre>
 $ sudo apt-get install autoconf
</pre>
 
<pre>
pi@raspberrypi ~/test_hello $ ls
hello.c
pi@raspberrypi ~/test_hello $ cat hello.c
#include <stdio.h>

int main()
{
        printf("Hello, World!!\n");
        return 0;
}
</pre>

<pre>
$ autoscan
pi@raspberrypi ~/test_hello $ ls
autoscan.log  configure.scan  hello.c

$ mv configure.scan configure.in
</pre>

<pre>
$ aclocal
pi@raspberrypi ~/test_hello $ ls
autom4te.cache  autoscan.log  configure.in  hello.c
</pre>

<pre>
$ autoconf
pi@raspberrypi ~/test_hello $ ls
autom4te.cache  autoscan.log  configure  configure.in  hello.c
</pre>

<pre>
$ cat Makefile.am
bin_PROGRAMS=hello
hello_SOURCES=hello.c
</pre>

<pre>
$ autoheader
pi@raspberrypi ~/test_hello $ ls
Makefile.am     autoscan.log  config.log     configure     hello.c
autom4te.cache  config.h.in   config.status  configure.in
</pre>

<pre>
$ touch NEWS README AUTHORS ChangeLog
</pre>
