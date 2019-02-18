# VPN-implemented-on-OpenSSL-

The objective of this project is to implement a VPN. Many recent technological advances have
not only meant a shift toward industrial and retail globalization but also an increase in customer
expectation and knowledge. All of this has led many companies to look to technology to provide
an edge with which and on which to survive and excel. With facilities around the world and
vendors, partners and staff spread even wider, the need for reliable and secure communications
continues to increase.


A Virtual Private Network (VPN) is used to create a private scope of computer communications
or providing a secure extension of a private network into an insecure network such as the
Internet. VPN is a widely used security technology. VPN can be built upon IPSec or Secure
Socket Layer (SSL).
These are two fundamentally different approaches for building VPNs. SSL VPN (Secure
Sockets Layer virtual private network) is a form of VPN that can be used with a standard Web
browser. In contrast to the traditional Internet Protocol Security (IPsec) VPN, SSL VPN does not
require the installation of specialized client software on the end user's computer. It's used to
give remote users with access to Web applications, client/server applications and internal
network connections. In this lab, we focus on the SSL-based VPNs. This type of VPNs is often
referred to as SSL VPNs.

To achieve this goal, we have implemented a simple SSL VPN for Ubuntu. This includes
creating a host-host tunnel, host-gateway tunnel as well as a gateway-gateway tunnel using
TUN/TAP interfaces. The next step comprises of creating the VPN by encrypting the tunnel.
Encryption includes confidentiality and integrity. Encryption is taken care of by AES Encryption
Algorithm and confidentiality by HMAC-SHA256. Symmetric key algorithm will be used for both,
same key used for both encryption and MAC.VPN server will be authenticated using public key
certificates.

For this project, a variety of linux commad line utilties were used:

## Steps 

### Task 1: Create a Host-to-Host Tunnel using TUN/TAP

- TUN and TAP are virtual network kernel drivers; they implement network device thatare supported entirely in software. When a program is attached to a TUN/TAP interface, the IP packets that the computer sends to this interface will be piped into the program; on the other hand, the IP packets that the program sends to the interface will be piped into the computer, as if they came from the outside through this virtual network interface.

1. Firstly, we create a host-host tunnel using the TUN interface using a simple C program.

`$ gcc -o simpletun simpletun.c`

![host-hosttunnel](/images/1.JPG)

2. Launching two virtual machines to create the host-host tunnel. One side of the tunnel acts as the server and the other the client. Once the tunnel is established, there is no difference between client and server; they are simply two ends of a tunnel.

`# ./simpletun -i tun0 -s -d`

`# ip addr add 10.0.4.1/24 dev tun0`

`# ifconfig tun0 up`

- The "-s" flag is used on the VM that acts as the server side of the tunnel, likewise a "-c" flag is used on the client side VM.

`# ./simpletun -i tun0 -c 192.168.10.5 -d`

`# ip addr add 10.0.5.1/24 dev tun0`

`# ifconfig tun0 up`

- After this step, the tunnel is set up.

3. The following routing table entry directs all the packets to the 10.0.5.0/24 network (10.0.4.0/24 network for the second command) through the interface tun0, from where the packet will be hauled through the tunnel.

`# route add -net 10.0.5.0 netmask 255.255.255.0 dev tun0`

### Task 2: Create a Host-to-Gateway Tunnel

Setup a tunnel between two VM's on two different host machines.

### Task 3: Create a Gateway-to-Gateway Tunnel

A gateway-gateway tunnel is similarly setup.
