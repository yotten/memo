# 目的
今使っているLinux Kernelがどんなkernelなのか?、どんな設定で動いているのか?を確認する。
# input
[このKernel、どんなKernel？](https://qiita.com/takeoverjp/items/6f4f30cf634307fe25cc)
# 項目
1. Kernel Version  
1. CPU Architecture  
1. Kernel Build Config  
1. Command-line Parameters  
1. sysctl  
1. Device Tree
# Kernel Version
`uname -r`で実行中のkernel versionを確認する
```console
pi@raspberrypi ~ $ uname -r
3.18.13+
pi@raspberrypi ~ $
```
# CPU Architecture
どのCPU向けにビルドされたkernel?
```console
pi@raspberrypi ~ $ uname -m
armv6l
pi@raspberrypi ~ $
```
# Kernel Build Config
/proc/config.gzで確認できる。(CONFIG_IKCONFIG_PROCが有効であること)
```console
pi@raspberrypi ~ $ zcat /proc/config.gz | head
#
# Automatically generated file; DO NOT EDIT.
# Linux/arm 3.18.13 Kernel Configuration
#
CONFIG_ARM=y
CONFIG_SYS_SUPPORTS_APM_EMULATION=y
CONFIG_HAVE_PROC_CPU=y
CONFIG_STACKTRACE_SUPPORT=y
CONFIG_HAVE_LATENCYTOP_SUPPORT=y
CONFIG_LOCKDEP_SUPPORT=y
pi@raspberrypi ~ $
```
```consoloe
pi@raspberrypi ~ $ zcat /proc/config.gz | grep CONFIG_IKCONFIG_PROC
CONFIG_IKCONFIG_PROC=y
pi@raspberrypi ~ $
```
## Kernel Build Configにはどんな項目があるの？
Kernelのソースコードに含まれる、Kconfigというファイルで定義されている。

# Command-line Parameters
Kernelの起動時に引数として指定するオプション。bootloaderが指定するのが一般的。
```console
pi@raspberrypi ~ $ cat /proc/cmdline
dma.dmachans=0x7f35 bcm2708_fb.fbwidth=1824 bcm2708_fb.fbheight=984 bcm2708.boardrev=0x10 bcm2708.serial=0x672eb89d smsc95xx.macaddr=B8:27:EB:2E:B8:9D bcm2708_fb.fbswap=1 bcm2708.disk_led_gpio=47 bcm2708.disk_led_active_low=0 sdhci-bcm2708.emmc_clock_freq=250000000 vc_mem.mem_base=0x1ec00000 vc_mem.mem_size=0x20000000  dwc_otg.lpm_enable=0 console=ttyAMA0,115200 console=tty1 root=/dev/mmcblk0p2 rootfstype=ext4 elevator=deadline rootwait
pi@raspberrypi ~ $
```
```console
pi@raspberrypi ~ $ dmesg | grep "Kernel command line"
[    0.000000] Kernel command line: dma.dmachans=0x7f35 bcm2708_fb.fbwidth=1824 bcm2708_fb.fbheight=984 bcm2708.boardrev=0x10 bcm2708.serial=0x672eb89d smsc95xx.macaddr=B8:27:EB:2E:B8:9D bcm2708_fb.fbswap=1 bcm2708.disk_led_gpio=47 bcm2708.disk_led_active_low=0 sdhci-bcm2708.emmc_clock_freq=250000000 vc_mem.mem_base=0x1ec00000 vc_mem.mem_size=0x20000000  dwc_otg.lpm_enable=0 console=ttyAMA0,115200 console=tty1 root=/dev/mmcblk0p2 rootfstype=ext4 elevator=deadline rootwait
pi@raspberrypi ~ $
```
https://www.kernel.org/doc/html/latest/admin-guide/kernel-parameters.html
