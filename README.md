## Network Packet Capture in Java
Welcome to Sly Technologies main repo. 

Here you will find the following libraries that you can use to build your specialized networking apps and do it all in your favorite Java environment. Our libraries use either [Apache v2](https://www.apache.org/licenses/LICENSE-2.0) or [Sly Techs Free License](https://www.slytechs.com/licensing), meaning there is no cost to you for using our software under the terms of the licenses!

Feature highlights with what you can do.

- Capture and transmit network packets (**jNetWorks**, **jNetPcap v2**, **jNetPcap Pro**)
- Dissect captured packets and use high level API to access headers and data (**jNetWorks**, **jNetPcap Pro**)
- IP fragmentation reassembly and tracking (**jNetWorks**, **jNetPcap Pro**)
- TCP/UDP/SCTP/QUIC stream reassembly (**jNetWorks**)
- HTTP dechunking and decompression (**jNetWorks**)
- TLS decryption (**jNetWorks**)
- Multi-adapter, multi-port and multi-CPU processing and distribution (**jNetworks**)
- and much more...

Our libraries support both **libpcap** and **Napatech SmartNIC** hardware accelerators for high speed network caputure.

## Getting Started
To get started you need to select the main API you wish to use. We offer 2 different APIs depending on your needs. Which ever API you choose the **Protocol Packs** which offer protocol specific APIs such as protocol headers, packet dissection, data reassembly, tracking and analysis, need to be included in addition to that main API modules (ie. **jnetpcap-pro** or **jnetworks**.)

Both of the APIs listed below use the same **Protocol Packs** and at least one of the main APIs needs to be chosen. The **Protocol Packs** do not function on their own. To get protocol level support the [**core-protocols**](https://github.com/slytechs-repos/core-protocols) module is required at minimum.

### jNetPcap Pro API (See examples: [jnetpcap-examples](https://github.com/slytechs-repos/jnetpcap-examples))
**jNetPcap Pro** provides a simple, single threaded API very similar to the way that native **libpcap** API works, with some extensions for enabling IPF reassembly and support for protocol services (MAC OUI table lookups, IP address resolution, hexdumps, etc..)

### jNetWorks API (Examples coming soon!)
**jNetWorks** provides a more sophisticated API and significantly higher performance for multi-CPU packet capture with support for hardware acceleration. You can chosee to use a simple **libpcap** extension or **Napatech SmartNIC** drivers to hardware accelerate network capture and IPF processing. Perfomance using **jNetWorks** is suitable for traffic rates upto 100Gbps (1/10/25/40/100Gbps) with **SmartNICs**. You can configure capture and spread the load of processing the data onto multiple-CPUs in your system, with zero-copy from the NICs to your application thread.

## Contact Us
If you have any questions, please contact us.

**Email:** [sales@slytechs.com](mailto:sales@slytechs.com)

**Phone:** 1-315-930-0939 (US NY)

**Contact Form:** [www.slytechs.com](http://www.slytechs.com) - contact form at the bottom of each page
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
