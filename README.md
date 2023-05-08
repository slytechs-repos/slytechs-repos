## Network Packet Capture in Java
Welcome to Sly Technologies main repo. 

Here you will find the following libraries that you can use to build your specialized networking apps and do it all in your favorite Java environment. Our libraries use either [Apache v2](https://www.apache.org/licenses/LICENSE-2.0) or [Sly Techs Free License](https://www.slytechs.com/licensing), meaning there is no cost to you for using our software under the terms of the licenses!

Feature highlights with what you can do.

- Capture and transmit network packets ([**jNetWorks**][jnetworks], [**jNetPcap v2**][jnetpcap-v2], [**jNetPcap Pro**][jnetpcap-pro])
- Dissect captured packets and use high level API to access headers and data ([**jNetWorks**][jnetworks], [**jNetPcap Pro**][jnetpcap-pro])
- IP fragmentation reassembly and tracking ([**jNetWorks**][jnetworks], [**jNetPcap Pro**][jnetpcap-pro])
- TCP/UDP/SCTP/QUIC stream reassembly ([**jNetWorks**][jnetworks])
- HTTP dechunking and decompression ([**jNetWorks**][jnetworks])
- TLS decryption ([**jNetWorks**][jnetworks])
- Multi-adapter, multi-port and multi-CPU processing and distribution ([**jNetWorks**][jnetworks])
- and much more...

Our libraries support both **libpcap** and **Napatech SmartNIC** hardware accelerators for high speed network caputure.

## Download the bundle
To make it easy to get all the prerequisite modules, we've bundled everything for your convenience.

Download the bundle [**jNetPcap Pro**][jnetpcap-pro-download]

## Getting Started
To get started you need to select the main API you wish to use. We offer 2 different APIs depending on your needs. Which ever API you choose the **Protocol Packs** which offer protocol specific APIs such as protocol headers, packet dissection, data reassembly, tracking and analysis, need to be included in addition to that main API modules (ie. [**jnetpcap-pro**][jnetpcap-pro] or [**jNetWorks**][jnetworks].)

Both of the APIs listed below use the same **Protocol Packs** and at least one of the main APIs needs to be chosen. The **Protocol Packs** do not function on their own. To get protocol level support the [**core-protocols**][core-protocols] module is required at minimum.

### jNetPcap Pro API (See examples: [jnetpcap-examples][jnetpcap-examples])
**jNetPcap Pro** provides a simple, single threaded API very similar to the way that native **libpcap** API works, with some extensions for enabling IPF reassembly and support for protocol services (MAC OUI table lookups, IP address resolution, hexdumps, etc..)

Here is the shortest, fully functional pcap program you can write to read packets from a capture file:
```java
try (var pcap = PcapPro.openOffline(PCAP_FILE)) {
	pcap.loop(3, System.out::println);
}
```
Produces output:
```
Packet [#0: caplen=54, timestamp=2023-04-13 14:00:19.646005000]
Packet [#1: caplen=92, timestamp=2023-04-13 14:00:19.718989000]
Packet [#2: caplen=395, timestamp=2023-04-13 14:00:20.562253000]
```

### jNetWorks API (Examples coming soon!)
[**jNetWorks**][jnetworks] provides a more sophisticated API and significantly higher performance for multi-CPU packet capture with support for hardware acceleration. You can chosee to use a simple **libpcap** extension or [**Napatech SmartNIC**][jntapi] drivers to hardware accelerate network capture and IPF processing. Perfomance using [**jNetWorks**][jnetworks] is suitable for traffic rates upto 100Gbps (1/10/25/40/100Gbps) with **SmartNICs**. You can configure capture and spread the load of processing the data onto multiple-CPUs in your system, with zero-copy from the NICs to your application thread.

## Contact Us
If you have any questions, please contact us.

**Email:** [sales@slytechs.com][slytechs-email]

**Phone:** 1-315-930-0939 (US NY)

**Contact Form:** [www.slytechs.com][slytechs-web] - contact form at the bottom of each page
<!--
**slytechs-repos/slytechs-repos** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->

[slytechs-web]: http://www.slytechs.com
[slytechs-email]: mailto:sales@slytechs.com
[jnetpcap-v2]: https://github.com/slytechs-repos/jnetpcap
[jnetpcap-pro]: https://github.com/slytechs-repos/jnetpcap-pro
[jnetpcap-pro-download]: https://github.com/slytechs-repos/slytechs-repos/releases
[jnetpcap-examples]: https://github.com/slytechs-repos/jnetpcap-examples
[jnetworks]: http://slytechs.com/jnetworks
[jntapi]: https://www.slytechs.com/jnapatech
[core-protocols]: https://github.com/slytechs-repos/core-protocols
