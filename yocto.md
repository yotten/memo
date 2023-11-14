<details>
<summary>core-image-minimalの起動ログ</summary>
<pre>
$ runqemu qemuarm64 nographic
runqemu - INFO - Running MACHINE=qemuarm64 bitbake -e ...
runqemu - INFO - Continuing with the following parameters:
KERNEL: [/home/yoshida/myyocto/build/tmp/deploy/images/qemuarm64/Image]
MACHINE: [qemuarm64]
FSTYPE: [ext4]
ROOTFS: [/home/yoshida/myyocto/build/tmp/deploy/images/qemuarm64/core-image-minimal-qemuarm64-20231108160923.rootfs.ext4]
CONFFILE: [/home/yoshida/myyocto/build/tmp/deploy/images/qemuarm64/core-image-minimal-qemuarm64-20231108160923.qemuboot.conf]

runqemu - INFO - Setting up tap interface under sudo
runqemu - INFO - Network configuration: ip=192.168.7.2::192.168.7.1:255.255.255.0::eth0:off:8.8.8.8
runqemu - INFO - Running /home/yoshida/myyocto/build/tmp/work/x86_64-linux/qemu-helper-native/1.0-r1/recipe-sysroot-native/usr/bin/qemu-system-aarch64 -device virtio-net-pci,netdev=net0,mac=52:54:00:12:34:02 -netdev tap,id=net0,ifname=tap0,script=no,downscript=no -object rng-random,filename=/dev/urandom,id=rng0 -device virtio-rng-pci,rng=rng0 -drive id=disk0,file=/home/yoshida/myyocto/build/tmp/deploy/images/qemuarm64/core-image-minimal-qemuarm64-20231108160923.rootfs.ext4,if=none,format=raw -device virtio-blk-pci,drive=disk0 -device qemu-xhci -device usb-tablet -device usb-kbd  -machine virt -cpu cortex-a57 -smp 4 -m 256 -serial mon:stdio -serial null -nographic -device virtio-gpu-pci -kernel /home/yoshida/myyocto/build/tmp/deploy/images/qemuarm64/Image -append 'root=/dev/vda rw  mem=256M ip=192.168.7.2::192.168.7.1:255.255.255.0::eth0:off:8.8.8.8 console=ttyAMA0 console=hvc0  '

runqemu - INFO - Host uptime: 43635.19

[    0.000000] Booting Linux on physical CPU 0x0000000000 [0x411fd070]
[    0.000000] Linux version 5.15.124-yocto-standard (oe-user@oe-host) (aarch64-poky-linux-gcc (GCC) 11.4.0, GNU ld (GNU Binutils) 2.38.20220708) #1 SMP PREEMPT Thu Aug 3 18:08:15 UTC 2023
[    0.000000] Machine model: linux,dummy-virt
[    0.000000] Memory limited to 256MB
[    0.000000] efi: UEFI not found.
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x0000000040000000-0x000000004fffffff]
[    0.000000]   DMA32    empty
[    0.000000]   Normal   empty
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x0000000040000000-0x000000004fffffff]
[    0.000000] Initmem setup node 0 [mem 0x0000000040000000-0x000000004fffffff]
[    0.000000] psci: probing for conduit method from DT.
[    0.000000] psci: PSCIv0.2 detected in firmware.
[    0.000000] psci: Using standard PSCI v0.2 function IDs
[    0.000000] psci: Trusted OS migration not required
[    0.000000] percpu: Embedded 26 pages/cpu s67032 r8192 d31272 u106496
[    0.000000] Detected PIPT I-cache on CPU0
[    0.000000] CPU features: detected: Spectre-v2
[    0.000000] CPU features: detected: Spectre-v4
[    0.000000] CPU features: detected: Spectre-BHB
[    0.000000] CPU features: detected: ARM erratum 1742098
[    0.000000] CPU features: detected: ARM erratum 832075
[    0.000000] CPU features: detected: ARM errata 1165522, 1319367, or 1530923
[    0.000000] Built 1 zonelists, mobility grouping on.  Total pages: 64512
[    0.000000] Kernel command line: root=/dev/vda rw  mem=256M ip=192.168.7.2::192.168.7.1:255.255.255.0::eth0:off:8.8.8.8 console=ttyAMA0 console=hvc0
[    0.000000] Dentry cache hash table entries: 32768 (order: 6, 262144 bytes, linear)
[    0.000000] Inode-cache hash table entries: 16384 (order: 5, 131072 bytes, linear)
[    0.000000] mem auto-init: stack:off, heap alloc:off, heap free:off
[    0.000000] Memory: 232940K/262144K available (11648K kernel code, 1856K rwdata, 2704K rodata, 3648K init, 685K bss, 29204K reserved, 0K cma-reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] ftrace: allocating 35969 entries in 141 pages
[    0.000000] ftrace: allocated 141 pages with 4 groups
[    0.000000] trace event string verifier disabled
[    0.000000] rcu: Preemptible hierarchical RCU implementation.
[    0.000000] rcu:     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
[    0.000000]  Trampoline variant of Tasks RCU enabled.
[    0.000000]  Rude variant of Tasks RCU enabled.
[    0.000000]  Tracing variant of Tasks RCU enabled.
[    0.000000] rcu: RCU calculated value of scheduler-enlistment delay is 25 jiffies.
[    0.000000] rcu: Adjusting geometry for rcu_fanout_leaf=16, nr_cpu_ids=4
[    0.000000] NR_IRQS: 64, nr_irqs: 64, preallocated irqs: 0
[    0.000000] Root IRQ handler: gic_handle_irq
[    0.000000] GICv2m: range[mem 0x08020000-0x08020fff], SPI[80:143]
[    0.000000] kfence: initialized - using 2097152 bytes for 255 objects at 0x(____ptrval____)-0x(____ptrval____)
[    0.000000] arch_timer: cp15 timer(s) running at 62.50MHz (virt).
[    0.000000] clocksource: arch_sys_counter: mask: 0xffffffffffffff max_cycles: 0x1cd42e208c, max_idle_ns: 881590405314 ns
[    0.000106] sched_clock: 56 bits at 62MHz, resolution 16ns, wraps every 4398046511096ns
[    0.011864] Console: colour dummy device 80x25
[    0.013615] Calibrating delay loop (skipped), value calculated using timer frequency.. 125.00 BogoMIPS (lpj=250000)
[    0.013846] pid_max: default: 32768 minimum: 301
[    0.014970] LSM: Security Framework initializing
[    0.016081] landlock: Up and running.
[    0.019919] Mount-cache hash table entries: 512 (order: 0, 4096 bytes, linear)
[    0.020026] Mountpoint-cache hash table entries: 512 (order: 0, 4096 bytes, linear)
[    0.063477] /cpus/cpu-map: empty cluster
[    0.079694] rcu: Hierarchical SRCU implementation.
[    0.088043] EFI services will not be available.
[    0.089730] smp: Bringing up secondary CPUs ...
[    0.096340] Detected PIPT I-cache on CPU1
[    0.098076] CPU1: Booted secondary processor 0x0000000001 [0x411fd070]
[    0.106226] Detected PIPT I-cache on CPU2
[    0.106513] CPU2: Booted secondary processor 0x0000000002 [0x411fd070]
[    0.109817] Detected PIPT I-cache on CPU3
[    0.110086] CPU3: Booted secondary processor 0x0000000003 [0x411fd070]
[    0.110899] smp: Brought up 1 node, 4 CPUs
[    0.111013] SMP: Total of 4 processors activated.
[    0.111101] CPU features: detected: 32-bit EL0 Support
[    0.111222] CPU features: detected: CRC32 instructions
[    0.167103] CPU: All CPU(s) started at EL1
[    0.215690] alternatives: patching kernel code
[    0.254952] devtmpfs: initialized
[    0.271034] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
[    0.271579] futex hash table entries: 1024 (order: 4, 65536 bytes, linear)
[    0.279345] DMI not present or invalid.
[    0.294248] NET: Registered PF_NETLINK/PF_ROUTE protocol family
[    0.302835] DMA: preallocated 128 KiB GFP_KERNEL pool for atomic allocations
[    0.303212] DMA: preallocated 128 KiB GFP_KERNEL|GFP_DMA pool for atomic allocations
[    0.303511] DMA: preallocated 128 KiB GFP_KERNEL|GFP_DMA32 pool for atomic allocations
[    0.309717] hw-breakpoint: found 6 breakpoint and 4 watchpoint registers.
[    0.311636] ASID allocator initialised with 65536 entries
[    0.312097] Serial: AMBA PL011 UART driver
[    0.350361] 9000000.pl011: ttyAMA0 at MMIO 0x9000000 (irq = 47, base_baud = 0) is a PL011 rev1
[    0.381277] printk: console [ttyAMA0] enabled
[    0.591203] raid6: neonx8   gen()  2666 MB/s
[    0.664855] raid6: neonx8   xor()   674 MB/s
[    0.740129] raid6: neonx4   gen()  1725 MB/s
[    0.815048] raid6: neonx4   xor()   710 MB/s
[    0.889938] raid6: neonx2   gen()  1244 MB/s
[    0.965802] raid6: neonx2   xor()   603 MB/s
[    1.040645] raid6: neonx1   gen()   833 MB/s
[    1.215819] raid6: neonx1   xor()   442 MB/s
[    1.291076] raid6: int64x8  gen()  1031 MB/s
[    1.364735] raid6: int64x8  xor()   625 MB/s
[    1.438355] raid6: int64x4  gen()  1424 MB/s
[    1.513663] raid6: int64x4  xor()   764 MB/s
[    1.589017] raid6: int64x2  gen()  1341 MB/s
[    1.663662] raid6: int64x2  xor()   736 MB/s
[    1.740066] raid6: int64x1  gen()  1001 MB/s
[    1.815577] raid6: int64x1  xor()   604 MB/s
[    1.816131] raid6: using algorithm neonx8 gen() 2666 MB/s
[    1.816589] raid6: .... xor() 674 MB/s, rmw enabled
[    1.817021] raid6: using neon recovery algorithm
[    1.819419] iommu: Default domain type: Translated
[    1.819883] iommu: DMA domain TLB invalidation policy: strict mode
[    1.822109] vgaarb: loaded
[    1.825357] SCSI subsystem initialized
[    1.826733] usbcore: registered new interface driver usbfs
[    1.827566] usbcore: registered new interface driver hub
[    1.828492] usbcore: registered new device driver usb
[    1.829352] pps_core: LinuxPPS API ver. 1 registered
[    1.829545] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
[    1.829927] PTP clock support registered
[    1.895047] clocksource: Switched to clocksource arch_sys_counter
[    2.053278] NET: Registered PF_INET protocol family
[    2.055989] IP idents hash table entries: 4096 (order: 3, 32768 bytes, linear)
[    2.065809] tcp_listen_portaddr_hash hash table entries: 256 (order: 0, 4096 bytes, linear)
[    2.066130] Table-perturb hash table entries: 65536 (order: 6, 262144 bytes, linear)
[    2.066363] TCP established hash table entries: 2048 (order: 2, 16384 bytes, linear)
[    2.066713] TCP bind hash table entries: 2048 (order: 3, 32768 bytes, linear)
[    2.067047] TCP: Hash tables configured (established 2048 bind 2048)
[    2.069193] UDP hash table entries: 256 (order: 1, 8192 bytes, linear)
[    2.069674] UDP-Lite hash table entries: 256 (order: 1, 8192 bytes, linear)
[    2.074377] NET: Registered PF_UNIX/PF_LOCAL protocol family
[    2.095307] RPC: Registered named UNIX socket transport module.
[    2.095604] RPC: Registered udp transport module.
[    2.095724] RPC: Registered tcp transport module.
[    2.095909] RPC: Registered tcp NFSv4.1 backchannel transport module.
[    2.096812] PCI: CLS 0 bytes, default 64
[    2.110118] hw perfevents: enabled with armv8_pmuv3 PMU driver, 5 counters available
[    2.626111] workingset: timestamp_bits=46 max_order=16 bucket_order=0
[    2.646965] NFS: Registering the id_resolver key type
[    2.650618] Key type id_resolver registered
[    2.651534] Key type id_legacy registered
[    2.683465] Key type cifs.idmap registered
[    2.722301] xor: measuring software checksum speed
[    2.730080]    8regs           :  1992 MB/sec
[    2.737393]    32regs          :  1711 MB/sec
[    2.746982]    arm64_neon      :  1317 MB/sec
[    2.747961] xor: using function: 8regs (1992 MB/sec)
[    2.750961] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 250)
[    2.760897] io scheduler mq-deadline registered
[    2.762725] io scheduler kyber registered
[    2.771454] pci-host-generic 4010000000.pcie: host bridge /pcie@10000000 ranges:
[    2.774745] pci-host-generic 4010000000.pcie:       IO 0x003eff0000..0x003effffff -> 0x0000000000
[    2.777902] pci-host-generic 4010000000.pcie:      MEM 0x0010000000..0x003efeffff -> 0x0010000000
[    2.785313] pci-host-generic 4010000000.pcie:      MEM 0x8000000000..0xffffffffff -> 0x8000000000
[    2.788650] pci-host-generic 4010000000.pcie: Memory resource size exceeds max for 32 bits
[    2.790900] pci-host-generic 4010000000.pcie: ECAM at [mem 0x4010000000-0x401fffffff] for [bus 00-ff]
[    2.795293] pci-host-generic 4010000000.pcie: PCI host bridge to bus 0000:00
[    2.797860] pci_bus 0000:00: root bus resource [bus 00-ff]
[    2.799361] pci_bus 0000:00: root bus resource [io  0x0000-0xffff]
[    2.801398] pci_bus 0000:00: root bus resource [mem 0x10000000-0x3efeffff]
[    2.803047] pci_bus 0000:00: root bus resource [mem 0x8000000000-0xffffffffff]
[    2.807467] pci 0000:00:00.0: [1b36:0008] type 00 class 0x060000
[    2.815776] pci 0000:00:01.0: [1af4:1000] type 00 class 0x020000
[    2.818020] pci 0000:00:01.0: reg 0x10: [io  0x0000-0x001f]
[    2.819376] pci 0000:00:01.0: reg 0x14: [mem 0x00000000-0x00000fff]
[    2.821026] pci 0000:00:01.0: reg 0x20: [mem 0x00000000-0x00003fff 64bit pref]
[    2.822204] pci 0000:00:01.0: reg 0x30: [mem 0x00000000-0x0003ffff pref]
[    2.823931] pci 0000:00:02.0: [1af4:1005] type 00 class 0x00ff00
[    2.825523] pci 0000:00:02.0: reg 0x10: [io  0x0000-0x001f]
[    2.826800] pci 0000:00:02.0: reg 0x20: [mem 0x00000000-0x00003fff 64bit pref]
[    2.829347] pci 0000:00:03.0: [1af4:1001] type 00 class 0x010000
[    2.830724] pci 0000:00:03.0: reg 0x10: [io  0x0000-0x007f]
[    2.831830] pci 0000:00:03.0: reg 0x14: [mem 0x00000000-0x00000fff]
[    2.833439] pci 0000:00:03.0: reg 0x20: [mem 0x00000000-0x00003fff 64bit pref]
[    2.835402] pci 0000:00:04.0: [1b36:000d] type 00 class 0x0c0330
[    2.837578] pci 0000:00:04.0: reg 0x10: [mem 0x00000000-0x00003fff 64bit]
[    2.839914] pci 0000:00:05.0: [1af4:1050] type 00 class 0x038000
[    2.841796] pci 0000:00:05.0: reg 0x14: [mem 0x00000000-0x00000fff]
[    2.842991] pci 0000:00:05.0: reg 0x20: [mem 0x00000000-0x00003fff 64bit pref]
[    2.848140] pci 0000:00:01.0: BAR 6: assigned [mem 0x10000000-0x1003ffff pref]
[    2.850711] pci 0000:00:01.0: BAR 4: assigned [mem 0x8000000000-0x8000003fff 64bit pref]
[    2.853260] pci 0000:00:02.0: BAR 4: assigned [mem 0x8000004000-0x8000007fff 64bit pref]
[    2.854972] pci 0000:00:03.0: BAR 4: assigned [mem 0x8000008000-0x800000bfff 64bit pref]
[    2.857234] pci 0000:00:04.0: BAR 0: assigned [mem 0x800000c000-0x800000ffff 64bit]
[    2.858510] pci 0000:00:05.0: BAR 4: assigned [mem 0x8000010000-0x8000013fff 64bit pref]
[    2.859687] pci 0000:00:01.0: BAR 1: assigned [mem 0x10040000-0x10040fff]
[    2.861490] pci 0000:00:03.0: BAR 1: assigned [mem 0x10041000-0x10041fff]
[    2.862691] pci 0000:00:05.0: BAR 1: assigned [mem 0x10042000-0x10042fff]
[    2.863841] pci 0000:00:03.0: BAR 0: assigned [io  0x1000-0x107f]
[    2.866262] pci 0000:00:01.0: BAR 0: assigned [io  0x1080-0x109f]
[    2.867197] pci 0000:00:02.0: BAR 0: assigned [io  0x10a0-0x10bf]
[    2.870646] pci 0000:00:04.0: enabling device (0000 -> 0002)
[    2.886449] virtio-pci 0000:00:01.0: enabling device (0000 -> 0003)
[    2.899124] virtio-pci 0000:00:02.0: enabling device (0000 -> 0003)
[    2.907375] virtio-pci 0000:00:03.0: enabling device (0000 -> 0003)
[    2.917544] virtio-pci 0000:00:05.0: enabling device (0000 -> 0002)
[    2.963045] [drm] pci: virtio-gpu-pci detected at 0000:00:05.0
[    2.964443] random: crng init done
[    2.966127] [drm] features: -virgl +edid -resource_blob -host_visible
[    2.973162] [drm] number of scanouts: 1
[    2.973813] [drm] number of cap sets: 0
[    2.991165] [drm] Initialized virtio_gpu 0.1.0 0 for virtio3 on minor 0
[    3.066796] virtio_gpu virtio3: [drm] drm_plane_enable_fb_damage_clips() not called
[    3.098997] Console: switching to colour frame buffer device 128x48
[    3.123874] virtio_gpu virtio3: [drm] fb0: virtio_gpudrmfb frame buffer device
[    3.128258] cacheinfo: Unable to detect cache hierarchy for CPU 0
[    3.191908] brd: module loaded
[    3.202872] virtio_blk virtio2: [vda] 22932 512-byte logical blocks (11.7 MB/11.2 MiB)
[    3.242479] xhci_hcd 0000:00:04.0: xHCI Host Controller
[    3.243669] xhci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 1
[    3.251283] xhci_hcd 0000:00:04.0: hcc params 0x00087001 hci version 0x100 quirks 0x0000000000000010
[    3.270828] xhci_hcd 0000:00:04.0: xHCI Host Controller
[    3.271144] xhci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 2
[    3.271486] xhci_hcd 0000:00:04.0: Host supports USB 3.0 SuperSpeed
[    3.306560] hub 1-0:1.0: USB hub found
[    3.307980] hub 1-0:1.0: 4 ports detected
[    3.323025] usb usb2: We don't know the algorithms for LPM for this host, disabling LPM.
[    3.326259] hub 2-0:1.0: USB hub found
[    3.326857] hub 2-0:1.0: 4 ports detected
[    3.381285] rtc-pl031 9010000.pl031: registered as rtc0
[    3.382253] rtc-pl031 9010000.pl031: setting system clock to 2023-11-09T23:08:19 UTC (1699571299)
[    3.467282] device-mapper: ioctl: 4.45.0-ioctl (2021-03-22) initialised: dm-devel@redhat.com
[    3.479839] usbcore: registered new interface driver usbhid
[    3.480063] usbhid: USB HID core driver
[    3.481732] u32 classifier
[    3.481941]     input device check on
[    3.482074]     Actions configured
[    3.485359] NET: Registered PF_INET6 protocol family
[    3.518734] Segment Routing with IPv6
[    3.520480] In-situ OAM (IOAM) with IPv6
[    3.522430] sit: IPv6, IPv4 and MPLS over IPv4 tunneling driver
[    3.530955] NET: Registered PF_PACKET protocol family
[    3.534128] Bridge firewalling registered
[    3.536292] Key type dns_resolver registered
[    3.538755] NET: Registered PF_VSOCK protocol family
[    3.569996] Key type .fscrypt registered
[    3.570232] Key type fscrypt-provisioning registered
[    3.593146] Btrfs loaded, crc32c=crc32c-generic, zoned=no, fsverity=no
[    3.661508] usb 1-1: new high-speed USB device number 2 using xhci_hcd
[    3.711913] Key type encrypted registered
[    3.723676] printk: console [netcon0] enabled
[    3.724141] netconsole: network logging started
[    3.805307] IP-Config: Complete:
[    3.805946]      device=eth0, hwaddr=52:54:00:12:34:02, ipaddr=192.168.7.2, mask=255.255.255.0, gw=192.168.7.1
[    3.807408]      host=192.168.7.2, domain=, nis-domain=(none)
[    3.808230]      bootserver=255.255.255.255, rootserver=255.255.255.255, rootpath=
[    3.808677]      nameserver0=8.8.8.8
[    3.847045] md: Waiting for all devices to be available before autodetect
[    3.865085] md: If you don't use raid, use raid=noautodetect
[    3.866055] md: Autodetecting RAID arrays.
[    3.866986] md: autorun ...
[    3.867822] md: ... autorun DONE.
[    4.001397] input: QEMU QEMU USB Tablet as /devices/platform/4010000000.pcie/pci0000:00/0000:00:04.0/usb1/1-1/1-1:1.0/0003:0627:0001.0001/input/input0
[    4.006887] hid-generic 0003:0627:0001.0001: input: USB HID v0.01 Mouse [QEMU QEMU USB Tablet] on usb-0000:00:04.0-1/input0
[    4.037635] EXT4-fs (vda): mounted filesystem with ordered data mode. Opts: (null). Quota mode: disabled.
[    4.041329] VFS: Mounted root (ext4 filesystem) on device 253:0.
[    4.046669] devtmpfs: mounted
[    4.095191] Freeing unused kernel memory: 3648K
[    4.098888] Run /sbin/init as init process
[    4.152649] usb 1-2: new high-speed USB device number 3 using xhci_hcd
[    4.267060] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
INIT: [    4.370050] input: QEMU QEMU USB Keyboard as /devices/platform/4010000000.pcie/pci0000:00/0000:00:04.0/usb1/1-2/1-2:1.0/0003:0627:0001.0002/input/input1
version 3.01 booting
[    4.443263] hid-generic 0003:0627:0001.0002: input: USB HID v1.11 Keyboard [QEMU QEMU USB Keyboard] on usb-0000:00:04.0-2/input0
Starting udev
[    6.964149] udevd[131]: starting version 3.2.10
[    7.189336] udevd[132]: starting eudev-3.2.10
[    9.300801] EXT4-fs (vda): re-mounted. Opts: (null). Quota mode: disabled.
INIT: Entering runlevel: 5
Configuring network interfaces... ip: RTNETLINK answers: File exists
Starting syslogd/klogd: done

Poky (Yocto Project Reference Distro) 4.0.14 qemuarm64 /dev/ttyAMA0

qemuarm64 login: root
root@qemuarm64:~#
root@qemuarm64:~# poweroff

Broadcast message from root@qemuarm64 (ttyAMA0) (Thu Nov  9 23:08:39 2023):

The system is going down for system halt NOW!
INIT: Switching to runlevel: 0
INIT: Sending processes configured via /etc/inittab the TERM signal
Stopping syslogd/klogd: stopped syslogd (pid 240)
stopped klogd (pid 243)
done
Unmounting remote filesystems...
Deconfiguring network interfaces... ifdown: interface lo not configured
done.
Sending all processes the TERM signal...
Sending all processes the KILL signal...
Deactivating swap...
Unmounting local filesystems...
[   30.771077] EXT4-fs (vda): re-mounted. Opts: (null). Quota mode: disabled.
[   31.025744] reboot: Power down
runqemu - INFO - Cleaning up
runqemu - INFO - Host uptime: 43667.17

Set 'tap0' nonpersistent
$
</pre>
</details>
