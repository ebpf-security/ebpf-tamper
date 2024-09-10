# eBPF-tamper: Detecting and preventing file tampering
Anti-tampering is a security feature in endpoint protection that safeguards the software itself from being disabled or altered by attackers.
[![Build Status](https://drone.grafana.net/api/badges/grafana/beyla/status.svg?ref=refs/heads/main)](https://ebpf-security.github.io/navihtml/ebpf-dump.html)

## Requirements
Anti-Tampering Technology eBPF-based , It runs on/requires Linux Kernel >= 5.10 such as the following platforms:
* Fedora 33+
* RHEL 9.0+
* Debian 12+
* Rocky Linux 9.0+
* Ubuntu 22.04+/OpenSUSE 15+...(You need to edit the GRUB_CMDLINE_LINUX line in the /etc/default/grub file to add bpf support, and then run update-grub2 to update and restart the system)

## Building & Running
```console
# Ubuntu
sudo apt-get install -y make gcc libelf-dev

# RHEL
sudo yum install -y make gcc elfutils-libelf-devel

$ make
  cc  -w -o file-tamper  filetamper.c   ./libbpf/libbpf.a -lelf -lz -lm  -I./libbpf/

$ ./file-tamper /root/
  File protection directory is =/root/
  TIME           COMM             PID     PPID    FILENAME
  09:21:56       bash             1453    1452    /root/.bash_profile
  09:43:47       vi               1489    1453    /root/.a.txt.swp
  09:43:50       vi               1489    1453    /root/a.txt
```
Loading eBPF program  requires root privileges 


## eBPF-tamper+
**eBPF-tamper+** is a paid version and completely open source too, main features are:
- Web interfaces
- Detecting and preventing file tampering
- Multiple protected directories 
- Pure-C eBPF implementation

**Free Trial**

```console
$ wget https://ebpf-security.github.io/ebpf-tamper
$ chmod +x ./ebpf-tapmer 
$ ./ebpf-tamper 
  1. Kill all of  processes...........................
  2. Init  ok.........................................
  3. System is running................................
```

After loading is complete, Open a browser to http://<host ip>:9998/ to access the Web UI.
Full Trial version available at [https://ebpf-security.github.io/navihtml/ebpf-tamper.html](https://ebpf-security.github.io/navihtml/ebpf-tamper.html)

How to stop?

```console
$ ./ebpf-tamper stop
```

<a href="https://github.com/ebpf-security/ebpf-security.github.io/blob/main/img/1.png"><img height="500" width="820" src="https://github.com/ebpf-security/ebpf-security.github.io/blob/main/img/1.png"></img></a>
&nbsp;


## Contact Us
* Mail to `ebpf-sec@hotmail.com`
Before moving on, please consider giving us a GitHub star ⭐️. Thank you!

## License
This project is licensed under the terms of the
[MIT license](/LICENSE).
