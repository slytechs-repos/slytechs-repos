# Network Packet Capture in Java

Welcome to Sly Technologies main repository! If you are interested in creating network applications, we have many of the tools you will need to quickly develop your products or complete projects on time. Incorporating our tried and tested libraries into your production environments and applications can help save both time and money.

## SDK Architecture

Our SDKs are organized into a hierarchical structure that promotes modularity and reuse:

### Core Platform
- **jnet-platform** - Core runtime and support functionality used by all SDKs
  - Base APIs and utilities
  - Packet Language (JNPL) for filter expressions
  - System tables and configuration
  - Common data structures and protocols
  - Thread and memory management

### Current Products (Available Now)

#### jnetpcap-sdk
Java wrapper and API for libpcap with high-level protocol support:
- Native libpcap integration
- Packet capture and transmission
- Protocol header access
- Live and offline capture
- IP reassembly
- Protocol services

#### protocol-sdk
Extensive protocol support including:
- TCP/IP protocol family
- Web protocols (HTTP, TLS)
- Telecom protocols
- Database protocols
- Microsoft protocols
- Media protocols (Voice/Video)

### Coming in Q1 2025

#### jnetworks-sdk
High-performance multi-CPU packet processing:
- Multi-CPU packet distribution
- Hardware acceleration support
- Zero-copy architecture
- Advanced stream processing
- High-speed packet capture
- In-line packet forwarding
- Traffic shaping

#### jnetntapi-sdk
Napatech SmartNIC integration:
- SmartNIC hardware acceleration
- High-speed packet processing
- Hardware-assisted filtering
- Advanced NIC features

#### jnetdpdk-sdk
Intel DPDK integration:
- DPDK packet processing
- High-performance networking
- Poll-mode drivers
- Memory management

## Getting Started

### 1. Basic Packet Capture (jNetPcap SDK)

First, add the dependencies:
```xml
<dependency>
    <groupId>com.slytechs.jnet.jnetpcap</groupId>
    <artifactId>jnetpcap-api</artifactId>
    <version>${jnetpcap.version}</version>
</dependency>

<dependency>
    <groupId>com.slytechs.jnet.protocol</groupId>
    <artifactId>protocol-tcpip</artifactId>
    <version>${protocol.version}</version>
</dependency>
```

Smallest possible example:
```java
try (var pcap = NetPcap.openOffline("capture.pcap")) {
    pcap.loop(System.out::println);
}
```

Advanced example with protocol handling:
```java
try (var pcap = NetPcap.openOffline("capture.pcap")) {
    // Initialize protocol headers once for reuse
    final Ethernet ethernet = new Ethernet();
    final Ip4 ip4 = new Ip4();
    final Tcp tcp = new Tcp();
    final Http http = new Http();

    // Configure packet formatting
    pcap.setPacketFormatter(new PacketFormat());
    
    pcap.loop(packet -> {
        // Headers bind to packet's native memory
        if (packet.hasHeader(ethernet))
            System.out.println(ethernet);

        if (packet.hasHeader(ip4))
            System.out.println(ip4);

        if (packet.hasHeader(tcp))
            System.out.println(tcp);

        if (packet.hasHeader(http))
            System.out.println(http);
    });
}
```

### 2. High Performance Processing (jNetWorks SDK)

```xml
<dependency>
    <groupId>com.slytechs.jnet.jnetworks</groupId>
    <artifactId>jnetworks-api</artifactId>
    <version>${jnetworks.version}</version>
</dependency>
```

Multi-CPU capture example:
```java
try (NetworkFramework framework = new PcapFramework()) {
    // Configure the adapter
    try (Config config = framework.createConfig()) {
        PortsConfig portsConfig = config.getPortsConfig();
        portsConfig.enablePort(0);
        
        NetworkConfig netConfig = config.getNetworkConfig();
        netConfig.assignFilter("tcp port 80");
    }

    // Setup capture
    try (NetTransceiver capture = framework.createTransceiver()) {
        // Initialize protocol headers once
        final Tcp tcp = new Tcp();
        final Http http = new Http();

        capture.forkRxPackets(packet -> {
            if (packet.hasHeader(tcp) && packet.hasHeader(http)) {
                System.out.printf("HTTP %s %s%n", 
                    http.methodString(),
                    http.uriString());
            }
        });

        capture.startCapture();
        Thread.sleep(Duration.ofMinutes(1).toMillis());
        capture.stopCapture();
    }
}
```

## License Information

All modules are available under either:
- [Apache v2 License](https://www.apache.org/licenses/LICENSE-2.0)
- [Sly Technologies Free License](https://www.slytechs.com/licensing)
  - 5 free developer installations
  - One-time distribution license fee
  - No royalties
  - Commercial support available (1 or 5 year terms)

## About Sly Technologies

We specialize in high-performance network packet capture and analysis solutions for Java. Our libraries are tried and tested in production environments, helping developers save time and money.

### Contact Information

- **Phone:** 1-315-930-0939 (US NY)
- **Email:** [sales@slytechs.com](mailto:sales@slytechs.com)
- **Address:** 224 Harrison Street, Syracuse, NY 13202 - USA
- **Website:** [www.slytechs.com](http://www.slytechs.com) (contact form available)

### Additional Resources

- [Software Release Roadmap](https://github.com/slytechs-repos/slytechs-repos/wiki/2.-Software-Release-Schedule)
- [Detailed Documentation](https://github.com/slytechs-repos/protocol-pack-sdk)
- [GitHub Repository](https://github.com/slytechs-repos)
