
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

<pre>
$ sudo fdisk -l
Device     Boot    Start      End  Sectors   Size Id Type
/dev/sdb1           8192  1609375  1601184 781.8M  e W95 FAT16 (LBA)
/dev/sdb2        1613824 31209471 29595648  14.1G 85 Linux extended
/dev/sdb3       31209472 31275007    65536    32M 83 Linux
/dev/sdb5        1622016  1744895   122880    60M  c W95 FAT32 (LBA)
/dev/sdb6        1753088 31209471 29456384    14G 83 Linux
</pre>

