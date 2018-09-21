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
