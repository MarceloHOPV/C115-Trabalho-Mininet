
# 📡 Relatório Mininet - Topologia Linear com 6 Switches

## 🎯 Objetivo

Implementar e testar uma topologia linear com 6 switches no Mininet, utilizando:

- Largura de banda de 25 Mbps
- MAC padrão
- Controlador padrão (ovs-controller)
- Testes de conectividade e desempenho com ping e iperf

---

## 🧱 Etapa 1: Criar a topologia

```bash
sudo mn --topo linear,6 --switch ovsk --controller=ovsc --link tc,bw=25
```

📷 **Print da criação da topologia no terminal** ⬇️ 
```bash
*** Creating network
*** Adding controller
*** Adding hosts:
h1 h2 h3 h4 h5 h6 
*** Adding switches:
s1 s2 s3 s4 s5 s6 
*** Adding links:
(25.00Mbit) *** Error: Warning: sch_htb: quantum of class 50001 is big. Consider r2q change.
(25.00Mbit) *** Error: Warning: sch_htb: quantum of class 50001 is big. Consider r2q change.
(h1, s1) (25.00Mbit) *** Error: Warning: sch_htb: quantum of class 50001 is big. Consider r2q change.
(25.00Mbit) *** Error: Warning: sch_htb: quantum of class 50001 is big. Consider r2q change.
(h2, s2) (25.00Mbit) *** Error: Warning: sch_htb: quantum of class 50001 is big. Consider r2q change.
(25.00Mbit) *** Error: Warning: sch_htb: quantum of class 50001 is big. Consider r2q change.
(h3, s3) (25.00Mbit) *** Error: Warning: sch_htb: quantum of class 50001 is big. Consider r2q change.
(25.00Mbit) *** Error: Warning: sch_htb: quantum of class 50001 is big. Consider r2q change.
(h4, s4) (25.00Mbit) *** Error: Warning: sch_htb: quantum of class 50001 is big. Consider r2q change.
(25.00Mbit) *** Error: Warning: sch_htb: quantum of class 50001 is big. Consider r2q change.
(h5, s5) (25.00Mbit) *** Error: Warning: sch_htb: quantum of class 50001 is big. Consider r2q change.
(25.00Mbit) *** Error: Warning: sch_htb: quantum of class 50001 is big. Consider r2q change.
(h6, s6) (25.00Mbit) *** Error: Warning: sch_htb: quantum of class 50001 is big. Consider r2q change.
(25.00Mbit) *** Error: Warning: sch_htb: quantum of class 50001 is big. Consider r2q change.
(s2, s1) (25.00Mbit) *** Error: Warning: sch_htb: quantum of class 50001 is big. Consider r2q change.
(25.00Mbit) *** Error: Warning: sch_htb: quantum of class 50001 is big. Consider r2q change.
(s3, s2) (25.00Mbit) *** Error: Warning: sch_htb: quantum of class 50001 is big. Consider r2q change.
(25.00Mbit) *** Error: Warning: sch_htb: quantum of class 50001 is big. Consider r2q change.
(s4, s3) (25.00Mbit) *** Error: Warning: sch_htb: quantum of class 50001 is big. Consider r2q change.
(25.00Mbit) *** Error: Warning: sch_htb: quantum of class 50001 is big. Consider r2q change.
(s5, s4) (25.00Mbit) *** Error: Warning: sch_htb: quantum of class 50001 is big. Consider r2q change.
(25.00Mbit) *** Error: Warning: sch_htb: quantum of class 50001 is big. Consider r2q change.
(s6, s5) 
*** Configuring hosts
h1 h2 h3 h4 h5 h6 
*** Starting controller
c0 
*** Starting 6 switches
s1 s2 s3 s4 s5 s6 ...(25.00Mbit) *** Error: Warning: sch_htb: quantum of class 50001 is big. Consider r2q change.
(25.00Mbit) *** Error: Warning: sch_htb: quantum of class 50001 is big. Consider r2q change.
(25.00Mbit) *** Error: Warning: sch_htb: quantum of class 50001 is big. Consider r2q change.
(25.00Mbit) *** Error: Warning: sch_htb: quantum of class 50001 is big. Consider r2q change.
(25.00Mbit) *** Error: Warning: sch_htb: quantum of class 50001 is big. Consider r2q change.
(25.00Mbit) *** Error: Warning: sch_htb: quantum of class 50001 is big. Consider r2q change.
(25.00Mbit) *** Error: Warning: sch_htb: quantum of class 50001 is big. Consider r2q change.
(25.00Mbit) *** Error: Warning: sch_htb: quantum of class 50001 is big. Consider r2q change.
(25.00Mbit) *** Error: Warning: sch_htb: quantum of class 50001 is big. Consider r2q change.
(25.00Mbit) *** Error: Warning: sch_htb: quantum of class 50001 is big. Consider r2q change.
(25.00Mbit) *** Error: Warning: sch_htb: quantum of class 50001 is big. Consider r2q change.
(25.00Mbit) *** Error: Warning: sch_htb: quantum of class 50001 is big. Consider r2q change.
(25.00Mbit) *** Error: Warning: sch_htb: quantum of class 50001 is big. Consider r2q change.
(25.00Mbit) *** Error: Warning: sch_htb: quantum of class 50001 is big. Consider r2q change.
(25.00Mbit) *** Error: Warning: sch_htb: quantum of class 50001 is big. Consider r2q change.
(25.00Mbit) *** Error: Warning: sch_htb: quantum of class 50001 is big. Consider r2q change.
```
---

## 🔍 Etapa 2: Verificar IP e MAC do host 1 + interfaces do switch s1

```bash
h1 ip a
s1 ifconfig -a
```

📷 **Print com IP/MAC do h1 e as portas/interfaces do s1** ⬇️
```bash
: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host proto kernel_lo 
       valid_lft forever preferred_lft forever
2: h1-eth0@if61: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc htb state UP group default qlen 1000
    link/ether ba:96:90:43:91:04 brd ff:ff:ff:ff:ff:ff link-netnsid 0
    inet 10.0.0.1/8 brd 10.255.255.255 scope global h1-eth0
       valid_lft forever preferred_lft forever
    inet6 fe80::b896:90ff:fe43:9104/64 scope link proto kernel_ll 
       valid_lft forever preferred_lft forever
```bash
enp0s3: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 10.0.2.15  netmask 255.255.255.0  broadcast 10.0.2.255
        inet6 fe80::a00:27ff:fe31:c136  prefixlen 64  scopeid 0x20<link>
        inet6 fd17:625c:f037:2:e32b:8f5b:bbfd:2397  prefixlen 64  scopeid 0x0<global>
        inet6 fd17:625c:f037:2:a00:27ff:fe31:c136  prefixlen 64  scopeid 0x0<global>
        ether 08:00:27:31:c1:36  txqueuelen 1000  (Ethernet)
        RX packets 784  bytes 774765 (774.7 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 459  bytes 55946 (55.9 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 15236  bytes 1104169 (1.1 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 15236  bytes 1104169 (1.1 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

ovs-system: flags=4098<BROADCAST,MULTICAST>  mtu 1500
        ether 72:d1:dc:b1:0b:f1  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

s1: flags=4098<BROADCAST,MULTICAST>  mtu 1500
        ether 2a:1b:52:47:8e:4f  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

s2: flags=4098<BROADCAST,MULTICAST>  mtu 1500
        ether f6:c7:65:dd:5d:4a  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

s3: flags=4098<BROADCAST,MULTICAST>  mtu 1500
        ether 46:40:33:8c:dd:48  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

s4: flags=4098<BROADCAST,MULTICAST>  mtu 1500
        ether e6:2c:2a:47:4c:45  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

s5: flags=4098<BROADCAST,MULTICAST>  mtu 1500
        ether 9a:60:aa:fb:b4:41  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

s6: flags=4098<BROADCAST,MULTICAST>  mtu 1500
        ether ee:3f:3d:54:ec:4c  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

s1-eth1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet6 fe80::68cf:1dff:fe37:7650  prefixlen 64  scopeid 0x20<link>
        ether 6a:cf:1d:37:76:50  txqueuelen 1000  (Ethernet)
        RX packets 12  bytes 936 (936.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 196  bytes 21406 (21.4 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

s1-eth2: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet6 fe80::d80b:edff:fe03:2d11  prefixlen 64  scopeid 0x20<link>
        ether da:0b:ed:03:2d:11  txqueuelen 1000  (Ethernet)
        RX packets 173  bytes 18587 (18.5 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 36  bytes 3845 (3.8 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

s2-eth1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet6 fe80::8860:abff:fe70:5085  prefixlen 64  scopeid 0x20<link>
        ether 8a:60:ab:70:50:85  txqueuelen 1000  (Ethernet)
        RX packets 12  bytes 936 (936.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 199  bytes 21656 (21.6 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

s2-eth2: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet6 fe80::7c3c:7ff:fe83:d24d  prefixlen 64  scopeid 0x20<link>
        ether 7e:3c:07:83:d2:4d  txqueuelen 1000  (Ethernet)
        RX packets 36  bytes 3845 (3.8 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 173  bytes 18587 (18.5 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

s2-eth3: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet6 fe80::30f8:31ff:fe48:230a  prefixlen 64  scopeid 0x20<link>
        ether 32:f8:31:48:23:0a  txqueuelen 1000  (Ethernet)
        RX packets 140  bytes 15008 (15.0 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 69  bytes 7424 (7.4 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

s3-eth1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet6 fe80::cfe:7eff:fe44:34ba  prefixlen 64  scopeid 0x20<link>
        ether 0e:fe:7e:44:34:ba  txqueuelen 1000  (Ethernet)
        RX packets 12  bytes 936 (936.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 199  bytes 21656 (21.6 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

s3-eth2: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet6 fe80::2c44:16ff:fe5c:eacc  prefixlen 64  scopeid 0x20<link>
        ether 2e:44:16:5c:ea:cc  txqueuelen 1000  (Ethernet)
        RX packets 69  bytes 7424 (7.4 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 140  bytes 15008 (15.0 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

s3-eth3: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet6 fe80::d077:1cff:fe38:d4c8  prefixlen 64  scopeid 0x20<link>
        ether d2:77:1c:38:d4:c8  txqueuelen 1000  (Ethernet)
        RX packets 107  bytes 11429 (11.4 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 102  bytes 11003 (11.0 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

s4-eth1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet6 fe80::38af:8bff:fe74:becb  prefixlen 64  scopeid 0x20<link>
        ether 3a:af:8b:74:be:cb  txqueuelen 1000  (Ethernet)
        RX packets 12  bytes 936 (936.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 199  bytes 21656 (21.6 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

s4-eth2: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet6 fe80::5c58:4aff:fe1a:1811  prefixlen 64  scopeid 0x20<link>
        ether 5e:58:4a:1a:18:11  txqueuelen 1000  (Ethernet)
        RX packets 102  bytes 11003 (11.0 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 107  bytes 11429 (11.4 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

s4-eth3: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet6 fe80::c1f:37ff:fe4a:3970  prefixlen 64  scopeid 0x20<link>
        ether 0e:1f:37:4a:39:70  txqueuelen 1000  (Ethernet)
        RX packets 72  bytes 7674 (7.6 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 135  bytes 14582 (14.5 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

s5-eth1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet6 fe80::1c6a:f1ff:fed8:b2cd  prefixlen 64  scopeid 0x20<link>
        ether 1e:6a:f1:d8:b2:cd  txqueuelen 1000  (Ethernet)
        RX packets 12  bytes 936 (936.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 196  bytes 21410 (21.4 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

s5-eth2: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet6 fe80::48a1:bcff:fe31:6857  prefixlen 64  scopeid 0x20<link>
        ether 4a:a1:bc:31:68:57  txqueuelen 1000  (Ethernet)
        RX packets 135  bytes 14582 (14.5 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 72  bytes 7674 (7.6 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

s5-eth3: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet6 fe80::f8db:7bff:feb5:b934  prefixlen 64  scopeid 0x20<link>
        ether fa:db:7b:b5:b9:34  txqueuelen 1000  (Ethernet)
        RX packets 36  bytes 3845 (3.8 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 171  bytes 18411 (18.4 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

s6-eth1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet6 fe80::b405:4eff:fe77:7bfa  prefixlen 64  scopeid 0x20<link>
        ether b6:05:4e:77:7b:fa  txqueuelen 1000  (Ethernet)
        RX packets 12  bytes 936 (936.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 198  bytes 21566 (21.5 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

s6-eth2: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet6 fe80::6077:d4ff:feee:5473  prefixlen 64  scopeid 0x20<link>
        ether 62:77:d4:ee:54:73  txqueuelen 1000  (Ethernet)
        RX packets 171  bytes 18411 (18.4 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 36  bytes 3845 (3.8 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```
---

## 🔄 Etapa 3: Testar conectividade entre os nós

```bash
pingall
```

📷 **Print do resultado dos testes de ping entre os hosts**  ⬇️
```bash
*** Ping: testing ping reachability
h1 -> h2 h3 h4 h5 h6 
h2 -> h1 h3 h4 h5 h6 
h3 -> h1 h2 h4 h5 h6 
h4 -> h1 h2 h3 h5 h6 
h5 -> h1 h2 h3 h4 h6 
h6 -> h1 h2 h3 h4 h5 
*** Results: 0% dropped (30/30 received)
```
---

## 🌐 Etapa 4: Iniciar servidor TCP no host 1 (porta 5555)

```bash
h1 iperf -s -p 5555 &
```
Sem resposta
---

## 📶 Etapa 5: Executar o cliente TCP no host 2 com relatório por segundo

```bash
h2 iperf -c 10.0.0.1 -p 5555 -i 1 -t 15
```

📷 **Print com os resultados do iperf mostrando o throughput a cada segundo** ⬇️
```bash
------------------------------------------------------------
Client connecting to 10.0.0.1, TCP port 5555
TCP window size: 85.3 KByte (default)
------------------------------------------------------------
[  1] local 10.0.0.2 port 35416 connected with 10.0.0.1 port 5555
[ ID] Interval       Transfer     Bandwidth
[  1] 0.0000-1.0000 sec  4.00 MBytes  33.6 Mbits/sec
[  1] 1.0000-2.0000 sec  2.50 MBytes  21.0 Mbits/sec
[  1] 2.0000-3.0000 sec  3.00 MBytes  25.2 Mbits/sec
[  1] 3.0000-4.0000 sec  2.50 MBytes  21.0 Mbits/sec
[  1] 4.0000-5.0000 sec  3.12 MBytes  26.2 Mbits/sec
[  1] 5.0000-6.0000 sec  2.50 MBytes  21.0 Mbits/sec
[  1] 6.0000-7.0000 sec  3.00 MBytes  25.2 Mbits/sec
[  1] 7.0000-8.0000 sec  2.50 MBytes  21.0 Mbits/sec
[  1] 8.0000-9.0000 sec  3.12 MBytes  26.2 Mbits/sec
[  1] 9.0000-10.0000 sec  2.50 MBytes  21.0 Mbits/sec
[  1] 10.0000-11.0000 sec  2.50 MBytes  21.0 Mbits/sec
[  1] 11.0000-12.0000 sec  3.12 MBytes  26.2 Mbits/sec
[  1] 12.0000-13.0000 sec  2.50 MBytes  21.0 Mbits/sec
[  1] 13.0000-14.0000 sec  2.50 MBytes  21.0 Mbits/sec
[  1] 14.0000-15.0000 sec  2.50 MBytes  21.0 Mbits/sec
[  1] 15.0000-15.5313 sec   128 KBytes  1.97 Mbits/sec
[  1] 0.0000-15.5313 sec  42.0 MBytes  22.7 Mbits/sec
```
---

## 🧼 Etapa Final: Encerrar e limpar a rede

```bash
exit
sudo mn -c
```

📷 (opcional) Print de finalização e limpeza da rede⬇️
```bash
*** Stopping 1 controllers
c0 
*** Stopping 11 links
...........
*** Stopping 6 switches
s1 s2 s3 s4 s5 s6 
*** Stopping 6 hosts
h1 h2 h3 h4 h5 h6 
*** Done
completed in 773.082 seconds
```
```bash
*** Removing excess controllers/ofprotocols/ofdatapaths/pings/noxes
killall controller ofprotocol ofdatapath ping nox_corelt-nox_core ovs-openflowd ovs-controllerovs-testcontroller udpbwtest mnexec ivs ryu-manager 2> /dev/null
killall -9 controller ofprotocol ofdatapath ping nox_corelt-nox_core ovs-openflowd ovs-controllerovs-testcontroller udpbwtest mnexec ivs ryu-manager 2> /dev/null
pkill -9 -f "sudo mnexec"
*** Removing junk from /tmp
rm -f /tmp/vconn* /tmp/vlogs* /tmp/*.out /tmp/*.log
*** Removing old X11 tunnels
*** Removing excess kernel datapaths
ps ax | egrep -o 'dp[0-9]+' | sed 's/dp/nl:/'
***  Removing OVS datapaths
ovs-vsctl --timeout=1 list-br
ovs-vsctl --timeout=1 list-br
*** Removing all links of the pattern foo-ethX
ip link show | egrep -o '([-_.[:alnum:]]+-eth[[:digit:]]+)'
ip link show
*** Killing stale mininet node processes
pkill -9 -f mininet:
*** Shutting down stale tunnels
pkill -9 -f Tunnel=Ethernet
pkill -9 -f .ssh/mn
rm -f ~/.ssh/mn/*
*** Cleanup complete.
```
---

## ✅ Conclusão

A topologia linear foi criada com sucesso, mesmo com os warnings e foram realizados testes de conectividade e desempenho entre os nós. Os resultados demonstram que os hosts estão corretamente configurados e conectados, com largura de banda aplicada via Traffic Control.

