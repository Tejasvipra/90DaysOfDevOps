#top
top - 13:51:58 up 29 min,  0 user,  load average: 0.02, 0.01, 0.02
Tasks: 121 total,   1 running, 120 sleeping,   0 stopped,   0 zombie
%Cpu(s):  0.0 us,  0.3 sy,  0.0 ni, 99.7 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st 
MiB Mem :   1903.3 total,    481.3 free,    480.5 used,   1134.5 buff/cache     
MiB Swap:   1024.0 total,   1024.0 free,      0.0 used.   1422.8 avail Mem 

    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND                                                                   
     17 root      20   0       0      0      0 I   0.3   0.0   0:00.29 rcu_preempt                                                               
   1671 root      39  19  843976  58788  29440 S   0.3   3.0   0:06.82 node                                                                      
      1 root      20   0   22200  13160   9448 S   0.0   0.7   0:03.98 systemd                                                                   
      2 root      20   0       0      0      0 S   0.0   0.0   0:00.00 kthreadd                                                                  
      3 root      20   0       0      0      0 S   0.0   0.0   0:00.00 pool_workqueue_release                                                    
      4 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-rcu_g                                                           
      5 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-rcu_p                                                           
      6 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-slub_                                                           
      7 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-netns                                                           
      8 root      20   0       0      0      0 I   0.0   0.0   0:00.07 kworker/0:0-events                                                        
      9 root      20   0       0      0      0 I   0.0   0.0   0:00.10 kworker/0:1-cgroup_destroy                                                
     10 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/0:0H-events_highpri                                               
     11 root      20   0       0      0      0 I   0.0   0.0   0:00.29 kworker/u2:0-events_unbound                                               
     12 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-mm_pe                                                           
     13 root      20   0       0      0      0 I   0.0   0.0   0:00.00 rcu_tasks_kthread                                                         
     14 root      20   0       0      0      0 I   0.0   0.0   0:00.00 rcu_tasks_rude_kthread                                                    
     15 root      20   0       0      0      0 I   0.0   0.0   0:00.00 rcu_tasks_trace_kthread                                                   
     16 root      20   0       0      0      0 S   0.0   0.0   0:00.10 ksoftirqd/0                                                               
     18 root      rt   0       0      0      0 S   0.0   0.0   0:00.00 migration/0                                                               
     19 root     -51   0       0      0      0 S   0.0   0.0   0:00.00 idle_inject/0                                                             
     20 root      20   0       0      0      0 S   0.0   0.0   0:00.00 cpuhp/0                                                                   
     21 root      20   0       0      0      0 S   0.0   0.0   0:00.00 kdevtmpfs                                                                 
     22 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-inet_                                                           
     23 root      20   0       0      0      0 S   0.0   0.0   0:00.00 kauditd                                                                   
     24 root      20   0       0      0      0 S   0.0   0.0   0:00.00 khungtaskd                                                                
     26 root      20   0       0      0      0 S   0.0   0.0   0:00.00 oom_reaper                                                                
     28 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-write                                                           
     29 root      20   0       0      0      0 S   0.0   0.0   0:00.05 kcompactd0                                                                
     30 root      25   5       0      0      0 S   0.0   0.0   0:00.00 ksmd 


ubuntu:~ pgrep nginx
2436
2439
ubuntu:~ systemctl status nginx
● nginx.service - A high performance web server and a reverse proxy server
     Loaded: loaded (/usr/lib/systemd/system/nginx.service; enabled; preset: enabled)
     Active: active (running) since Mon 2026-02-02 13:53:25 UTC; 35s ago
       Docs: man:nginx(8)
    Process: 2400 ExecStartPre=/usr/sbin/nginx -t -q -g daemon on; master_process on; (code=exited, status=0/SUCCESS)
    Process: 2406 ExecStart=/usr/sbin/nginx -g daemon on; master_process on; (code=exited, status=0/SUCCESS)
   Main PID: 2436 (nginx)
      Tasks: 2 (limit: 2237)
     Memory: 1.7M (peak: 3.7M)
        CPU: 37ms
     CGroup: /system.slice/nginx.service
             ├─2436 "nginx: master process /usr/sbin/nginx -g daemon on; master_process on;"
             └─2439 "nginx: worker process"

Feb 02 13:53:24 ubuntu systemd[1]: Starting nginx.service - A high performance web server and a reverse proxy server...
Feb 02 13:53:25 ubuntu systemd[1]: Started nginx.service - A high performance web server and a reverse proxy server.
ubuntu:~  systemctl list-units
  UNIT                                                                                     LOAD   ACTIVE SUB       DESCRIPTION                  >
  proc-sys-fs-binfmt_misc.automount                                                        loaded active running   Arbitrary Executable File For>
  sys-devices-pci0000:00-0000:00:02.0-0000:01:00.0-virtio0-net-enp1s0.device               loaded active plugged   Virtio 1.0 network device
  sys-devices-pci0000:00-0000:00:02.5-0000:06:00.0-virtio2-virtio\x2dports-vport2p1.device loaded active plugged   /sys/devices/pci0000:00/0000:>
  sys-devices-pci0000:00-0000:00:02.6-0000:07:00.0-virtio3-block-vda-vda1.device           loaded active plugged   /sys/devices/pci0000:00/0000:>
  sys-devices-pci0000:00-0000:00:02.6-0000:07:00.0-virtio3-block-vda-vda14.device          loaded active plugged   /sys/devices/pci0000:00/0000:>
  sys-devices-pci0000:00-0000:00:02.6-0000:07:00.0-virtio3-block-vda-vda15.device          loaded active plugged   /sys/devices/pci0000:00/0000:>
  sys-devices-pci0000:00-0000:00:02.6-0000:07:00.0-virtio3-block-vda-vda16.device          loaded active plugged   /sys/devices/pci0000:00/0000:>
  sys-devices-pci0000:00-0000:00:02.6-0000:07:00.0-virtio3-block-vda.device                loaded active plugged   /sys/devices/pci0000:00/0000:>
  sys-devices-platform-serial8250-serial8250:0-serial8250:0.1-tty-ttyS1.device             loaded active plugged   /sys/devices/platform/serial8>
  sys-devices-platform-serial8250-serial8250:0-serial8250:0.10-tty-ttyS10.device           loaded active plugged   /sys/devices/platform/serial8>
  sys-devices-platform-serial8250-serial8250:0-serial8250:0.11-tty-ttyS11.device           loaded active plugged   /sys/devices/platform/serial8>
ubuntu:~$ systemctl list-units --all | grep nginx
  nginx.service                                                                            loaded    active   running   A high performance web server and a reverse proxy server
ubuntu:~ journalctl -u nginx
Feb 02 13:53:24 ubuntu systemd[1]: Starting nginx.service - A high performance web server and a reverse proxy server...
Feb 02 13:53:25 ubuntu systemd[1]: Started nginx.service - A high performance web server and a reverse proxy server.

ubuntu:~  tail -n 50 /var/log/nginx/access.log = last 50 lines of logs shows 
ubuntu:~ tail -n 50 /var/log/nginx/error.log  
2026/02/02 13:53:25 [notice] 2436#2436: using inherited sockets from "5;6;"
ubuntu:~  journalctl -u nginx -f
Feb 02 13:53:24 ubuntu systemd[1]: Starting nginx.service - A high performance web server and a reverse proxy server...
Feb 02 13:53:25 ubuntu systemd[1]: Started nginx.service - A high performance web server and a reverse proxy server.

ubuntu:~ journalctl  ---journalctl shows logs of systemd and all services on your system.     
Feb 10 22:04:48 ubuntu kernel: Linux version 6.8.0-51-generic (buildd@lcy02-amd64-091) (x86_64-linux-gnu-gcc-13 (Ubuntu 13.3.0-6ubuntu2~24.04) 13.3.0, GNU ld (GNU Binutils for Ubunt>
Feb 10 22:04:48 ubuntu kernel: Command line: BOOT_IMAGE=/vmlinuz-6.8.0-51-generic root=LABEL=cloudimg-rootfs ro console=tty1 console=ttyS0
Feb 10 22:04:48 ubuntu kernel: KERNEL supported cpus:
Feb 10 22:04:48 ubuntu kernel:   Intel GenuineIntel
Feb 10 22:04:48 ubuntu kernel:   AMD AuthenticAMD
Feb 10 22:04:48 ubuntu kernel:   Hygon HygonGenuine
Feb 10 22:04:48 ubuntu kernel:   Centaur CentaurHauls
Feb 10 22:04:48 ubuntu kernel:   zhaoxin   Shanghai  
Feb 10 22:04:48 ubuntu kernel: BIOS-provided physical RAM map:
Feb 10 22:04:48 ubuntu kernel: BIOS-e820: [mem 0x0000000000000000-0x000000000009fbff] usable
Feb 10 22:04:48 ubuntu kernel: BIOS-e820: [mem 0x000000000009fc00-0x000000000009ffff] reserved
Feb 10 22:04:48 ubuntu kernel: BIOS-e820: [mem 0x00000000000f0000-0x00000000000fffff] reserved
Feb 10 22:04:48 ubuntu kernel: BIOS-e820: [mem 0x0000000000100000-0x000000007ffdcfff] usable
Feb 10 22:04:48 ubuntu kernel: BIOS-e820: [mem 0x000000007ffdd000-0x000000007fffffff] reserved
Feb 10 22:04:48 ubuntu kernel: BIOS-e820: [mem 0x00000000b0000000-0x00000000bfffffff] reserved
Feb 10 22:04:48 ubuntu kernel: BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
Feb 10 22:04:48 ubuntu kernel: BIOS-e820: [mem 0x00000000feffc000-0x00000000feffffff] reserved
Feb 10 22:04:48 ubuntu kernel: BIOS-e820: [mem 0x00000000fffc0000-0x00000000ffffffff] reserved
Feb 10 22:04:48 ubuntu kernel: BIOS-e820: [mem 0x0000000100000000-0x000000017fffffff] usable
Feb 10 22:04:48 ubuntu kernel: NX (Execute Disable) protection: active
Feb 10 22:04:48 ubuntu kernel: APIC: Static calls initialized
Feb 10 22:04:48 ubuntu kernel: SMBIOS 2.8 present.
Feb 10 22:04:48 ubuntu kernel: DMI: KubeVirt None/RHEL-AV, BIOS 1.15.0-1.module_el8.6.0+1087+b42c8331 04/01/2014
Feb 10 22:04:48 ubuntu kernel: Hypervisor detected: KVM
Feb 10 22:04:48 ubuntu kernel: kvm-clock: Using msrs 4b564d01 and 4b564d00
Feb 10 22:04:48 ubuntu kernel: kvm-clock: using sched offset of 967662215 cycles
Feb 10 22:04:48 ubuntu kernel: clocksource: kvm-clock: mask: 0xffffffffffffffff max_cycles: 0x1cd42e4dffb, max_idle_ns: 881590591483 ns
Feb 10 22:04:48 ubuntu kernel: tsc: Detected 3504.000 MHz processor
Feb 10 22:04:48 ubuntu kernel: e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
Feb 10 22:04:48 ubuntu kernel: e820: remove [mem 0x000a0000-0x000fffff] usable
Feb 10 22:04:48 ubuntu kernel: last_pfn = 0x180000 max_arch_pfn = 0x400000000
Feb 10 22:04:48 ubuntu kernel: MTRR map: 4 entries (3 fixed + 1 variable; max 19), built from 8 variable MTRRs
Feb 10 22:04:48 ubuntu kernel: x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WP  UC- WT  
Feb 10 22:04:48 ubuntu kernel: last_pfn = 0x7ffdd max_arch_pfn = 0x400000000
Feb 10 22:04:48 ubuntu kernel: found SMP MP-table at [mem 0x000f5b60-0x000f5b6f]
