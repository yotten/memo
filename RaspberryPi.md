# システムの状態を確認
数年ぶりにraspberryPI2を触ってみる。
現状のシステムの状態を確認する。  
参考：[インターフェース 2015:12] 
## RootFSサイズ/リソース使用量/カーネル・サイズを確認する
duコマンドでディスク使用量を確認する。(-hと-Hどちらで使用すべきかがよく分かっていない。)
```console
pi@raspberrypi ~ $ df -H
ファイルシス   サイズ  使用  残り 使用% マウント位置
rootfs            16G  3.5G   12G   24% /
/dev/root         16G  3.5G   12G   24% /
devtmpfs         224M     0  224M    0% /dev
tmpfs             46M  238k   46M    1% /run
tmpfs            5.3M     0  5.3M    0% /run/lock
tmpfs             92M     0   92M    0% /run/shm
/dev/mmcblk0p1    59M   24M   35M   41% /boot
pi@raspberrypi ~ $
```
* LinuxのRootFS(ルート・ファイル・システム)領域のサイズは16Gバイトあり、現在3.5Gバイト使用している。
* /boot領域は59Mバイト中、24Mバイトを使用している。
```console
pi@raspberrypi ~ $ free -h
             total       used       free     shared    buffers     cached
Mem:          435M        82M       353M         0B        13M        39M
-/+ buffers/cache:        28M       406M
Swap:          99M         0B        99M
pi@raspberrypi ~ $
```
Linuxに割り当てられたメモリ435Mバイトの内、現在82Mバイトを使用している。
```console
pi@raspberrypi ~ $ ps -el | wc -l
77
pi@raspberrypi ~ $
```
-e：全てのプロセスのを表示する。  
-l：プロセスの詳細情報を表示する。  
動作中のプロセス数=合計77個
```console
pi@raspberrypi ~ $ ls -lh /boot/kernel7.img
-rwxr-xr-x 1 root root 3.8M  2月 15  2015 /boot/kernel7.img
pi@raspberrypi ~ $
```
カーネル・サイズ：3.8Mバイト  

Raspbianのパッケージ・マネージャーでインストール済みのリストを確認
```
pi@raspberrypi ~ $ dpkg --list | wc -l
921
pi@raspberrypi ~ $
```
見出し行を含んでいるが900ほど入っている

# ラズベリー・パイ2の起動シーケンス
## ラズパイの起動シーケンスの全体像
### ステージ1：ROM化されたSoC内臓ブート・ストラップによる初期化
### ステージ2：ブートローダbootcode.binによる、メモリ周辺IPの初期化
### ステージ3：カーネル起動 & アプリケーションの実行準備
# LinuxPC上にビルドツリーを作成する
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

<pre>
$ sudo fdisk -l
Device     Boot    Start      End  Sectors   Size Id Type
/dev/sdb1           8192  1609375  1601184 781.8M  e W95 FAT16 (LBA)
/dev/sdb2        1613824 31209471 29595648  14.1G 85 Linux extended
/dev/sdb3       31209472 31275007    65536    32M 83 Linux
/dev/sdb5        1622016  1744895   122880    60M  c W95 FAT32 (LBA)
/dev/sdb6        1753088 31209471 29456384    14G 83 Linux
</pre>

