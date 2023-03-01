:::warning
# <center><i class="fa fa-edit"></i> Introduction to 5G, RAN, and O-RAN</center>
:::

###### tags: `5G` `RAN` `O-RAN` `TEEP` `Internship`

:::success
**Learning Objective:**

The study objectives were to:
- Understand the definition, technology, and architecture of 5G
- Understand about RAN definition, how the component works, and types of RAN.
- Study about Open RAN
:::

[TOC]

# I. Introduction to 5G

## I.I. Definition
:::success
Based on [SK Telecom White Paper](https://www.sktelecom.com/img/pds/press/SKT_5G%20White%20Paper_V1.0_Eng.pdf), there are several requirements for 5G i.e.
- **Ultra high speed and low latency**
    - Data transfer speeds 1000x faster than LTE
    - Ultra-low latency response time of less than a few miliseconds
- **Massive connectivity**
    - Accomodate 1000x more devices and traffic
    - Secure seamless connectivity
- **Flexible/Intelligent Network**
    - Provide software-based structure
    - Analyse data in real time
    - Provide intelligent/personalized services
- **Reliable/Secure Connection**
    - Secure more than 99% of network availability and reliability
    - Self healing/configuration
- **Energy/Cost-Efficient Infra**
    - 50-100x higher energy efficiency than LTE
    - Low cost infrastructure/devices
:::

**5G** is the fifth generation of cellular technology with the aim ==to greatly increase the speed and responsiveness of wireless networks.== For summary, 5G offers three main features:
- Faster data transmission speed (up to Gigabit/s).
- Greater capacity for IoT (internet of things) devices.
- Lower latency (down to single-digit ms).

5G architecture must supports low, mid, and high band spectrum due to the wide applications of it. ==The higher the frequency, the more data it can carry.== There are three frequency bands at the core of 5G networks:
- 5G high-band from 24 GHz to approximately 100 GHz. It requires more cellular infrastructure because high frequencies cannot easily move through obstacles.
- 5G mid-band from 2 GHz to 6 GHz. The peak rate of this frequency is hundred of Mbps.
- 5G low-band operates below 2 GHz. It provides a broad coverage area.

![image alt](https://www.digi.com/getattachment/Blog/post/5G-Network-Architecture/5g-spectrum-1280.jpg?lang=en-US)
*img src: https://www.digi.com/blog/post/5g-network-architecture*

## I.II. Technologies
![image alt](https://iili.io/HYe0q7a.png)
*img src: https://www.sktelecom.com/img/pds/press/SKT_5G%20White%20Paper_V1.0_Eng.pdf*

- **Realistic UX and 5G Contents Processing:**
    - Object/space recognition
    - Real-time rendering and display technology
    - Real-time hologram processing
- **Processing and Transmission of Tactile Multimedia:**
    - MPEG Media Transport Technology (MMT)
    - High efficiency multimedia coding
    - Cloud-based computing, caching, and orchestration
- **Cloud-based AII-IT Network and Service Platform:**
    - Network Functions Virtualization (NFV) based virtualized core network
    - Virtualized Radio Access Network (RAN)
    - Software Denfined Networking (SDN) and integrated orchestration
- **Analytics based Network Intelligence/Optimization:**
    - Big data analysis
    - Network intelligence & analytics
    - Analytics-based Self Organizing Network (SON)
- **Fast, Flexible Transport Network:**
    - Packet Optical Transport Network (POTN)
    - Transport SDN
- **Beyong-Cellular Network Architecture:**
    - Direct Device-to-Device (D2D) communications
    - Contents Centric Networking (CCN)
- **Enhanced Operation for Multi-cell/HetNet:**
    - Elastic cell
    - Aggregation of heterogeneous networks
- **Ultra-Dense Small Cell:**
    - Dynamic interference control and coordination
    - HetNet SON
- **Wideband High Frequency RF & 3D Beamforming:**
    - 3D beamforming
    - Beam switching
- **Enhancement of Multiple Antenna Technology including Massive MIMO:**
    - UE-specific beamforming
    - CSI/CQI feedback
- **Advanced IoT & New Waveform/Duplex:**
    - Cellular-based MTC (Maching Type Comm)
    - New waveform (NOMA, FBMC)
    - Hybrid duplex & full duplex communications

## I.III. Mobile Core

### 4G Mobile Core
![image alt](https://iili.io/HVTeqQI.jpg)
*img src: https://5g.systemsapproach.org/arch.html*

1. ==Control Panel (CP)=== Components:
	- **MME (Mobility Management Entity)**: responsible to track and manages user equipments (UE) throughout the RAN.
	- **HSS (Home Subscriber Server):** as a database that contains subscriber-related information.
	- **PCRF (Policy & Charging Rules Function):** responsible to track and manages policy rules and records billing data.

2. ==User Plane (UP)== Components:
	- **SGW (Serving Gateway):** responsible to forward IP packets to/from RAN.
	- **PGW (Packet Gateway):** responsible for connecting the mobile core to the external Internet.

### 5G Mobile Core
![image alt](https://5g.systemsapproach.org/_images/Slide33.png)
*img src: https://5g.systemsapproach.org/arch.html*

1. ==Control Plane (CP)== components:
	- **AMF (Core Access and Mobility Management Function):** responsible to connection management, mobility management, and location services.
	- **SMF (Session Management Function):** responsible to manages each user equipments session (such as, IP address allocation and QoS).
	- **PCF (Policy Control Function):** responsible to manages the policy rules for other control plane functions.
	- **UDM (Unified Data Management):** responsible to manages user identity.
	- **AUSF (Authentication Server Function):** an authentication server.
	- **SDSF (Structured Data Storage Network Function):** a *helper* service that used to store structured data.
	- **UDSF (Unstructured Data Storage Network Function):** a *helper* service that used to store unstructured data.
	- **NEF (Network Exposure Function):** a tools to expose select capabilities to third-party services.
	- **NRF (NF Repository Function):** a tools to discover available services.
	- **NSSF (Network Slicing Selector Function):** a tools to select a network slice.

2. ==User Plane (UP)== components:
	- **UPF (User Plane Function):** responsible to forwards traffic/packet between RAN and the internet.

## I.IV. Radio Access Network (RAN)
**Radio access network (RAN)** is a main component of wireless telecommunications system that is ==used to link individual user devices to other part of network using a radio connnection.==

![image alt](https://iili.io/HY4SmMJ.png)
*img src: https://www.brighttalk.com/webcast/16515/359818?utm_source=brighttalk-portal&utm_medium=web&utm_content=Parallel%20Wireless&utm_campaign=webcasts-search-results-feed*

The basic structure of RAN is consists of three main components i.e.
- **Antennas**. As a transmitter, the antennas are used to radiate the transmitted signal by convert electrical signal from RU into radio waves. As a receiver, the antennas are used to receive signal from user devices and convert it to electrical signals.
- **Radio unit (RU)**. Radio unit also called *remote radio unit (RRU)* or *remote radio head (RRH)*. As a transmitter, RU converts the data from BBU into electrical signal. As a receiver, RU converts the electrical signal from the antennas into data to communicate to the BBU. RU communicates with the BBU using an interface called **Common Public Radio Interface (CPRI)**.
- **Baseband unit (BBU)**. BBU is ==the main controller== for the base base station. BBU function is to organises the links to user devices, control the RU, processing data, detecting errors, securing, and ensuring that the wireless resources are used effectively.

![image alt](https://www.sdxcentral.com/cdn-cgi/image/w=748,h=820,fit=scale-down,f=auto,q=85/https://www.sdxcentral.com/wp-content/uploads/2021/01/SpringerLink-RAN-Architecture.jpg)
*img src: https://www.sdxcentral.com/cdn-cgi/image/w=748,h=820,fit=scale-down,f=auto,q=85/https://www.sdxcentral.com/wp-content/uploads/2021/01/SpringerLink-RAN-Architecture.jpg*

# II. Open Radio Access Network (O-RAN)
## II.I. Introduction to O-RAN
Disadvantages of traditional RAN:
- Limited reconfigurability
- Limited coordination among network nodes
- Limited options for operators to deploy and interface RAN equipment from multiple vendors
- The market is controlled by three or four vendors globally

==The goal of Open RAN: **interoperability between hardware and software from different vendors or manufacturers**.==

![image alt](https://iili.io/HaJvYqG.png)
*img src: https://www.brighttalk.com/webcast/16515/359818?utm_source=brighttalk-portal&utm_medium=web&utm_content=Parallel%20Wireless&utm_campaign=webcasts-search-results-feed*
:::info
**GPP (Generally Purpose Processor)** is generally called a Central Processing Unit (CPU). Example: Intel x86 and ARM
:::

## II.II. Principles of O-RAN
There are four principles for the O-RAN based on this [literature](https://arxiv.org/pdf/2202.01032.pdf):

### Disaggregation
==Functional split options proposed by 3GPP:==
![image alt](https://iili.io/Hadhq79.png)
*img src: https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=8479363*

![image alt](https://iili.io/HadN9zg.png)
*img src: https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=8479363*

According to the 3GPP 7.2 split, next generation node bases (gNBs) is splitted into three logical nodes :
- **Central Unit (CU)**
    - **Control Plane (CP)**
        - **Radio Resource Control (RRC)** layer is responsible to manages the life cycle of the connection.
        - **Packet Data Convergence Protocol (PDCP)** layer is responsible to takes care of reordering, packet duplication, and encryption for the air interface.
    - **User Plane (UP)**
        - **Service Data Adaptation Protocol (SDAP)** layer is responsible to manages the Quality of Service (QoS) of the traffic flows.
        - **Packet Data Convergence Protocol (PDCP)**.
- **Distributed Unit (DU)** consists of three layers i.e. **Radio Link Control (RLC)**, **Medium Access Control (MAC)**, **and Physical High** layers. MAC layer will generates transport blocks for the physical layer using the data from RLC layer. Physical high layer will take care of frequency domain functionalities.
- **Radio Unit (RU)** consists of two layers i.e **Radio Frequency (RF)** and **Physical Low** layers. RF layer is responsible to radiate the radio waves, which generates by physical layer. Physical low layer will take care of time domain functionalities.

![image alt](https://iili.io/HaF6sKN.png)
*img src: https://arxiv.org/pdf/2202.01032.pdf*

### RAN intelligent controllers (RICs)
**RAN intelligent controllers** with close loop control are introduced ==to optimze and orchestrate RAN.== Two RICs process KPMs (Key Performance Measurements) data using AI and ML algorithms to determine and apply control to the RAN.
![image alt](https://iili.io/Haz9Sje.png)
*img src: https://arxiv.org/pdf/2202.01032.pdf*

- **Non real time RIC** operates on a time scale ==longer than 1 s.== Non-RT RIC provides guidance, enrichment information, and manage ML models for the near-RT RIC.
- **Near real time RIC** operates on a time scale ==between 10 ms and 1 s.== Near-RT RIC consists of multiple application supporting custom logic called *xApps*.

![image alt](https://iili.io/Hazn3jR.png)
*img src: https://arxiv.org/pdf/2202.01032.pdf*

### Virtualization
**Virtualization** for the RAN components and O-RAN elements is aim ==to achieve the optimization of the power consumtion.== Control loop capabilities, together with the virtualization in the RAN will enable more refined and dynamic sleep cycles for the base stations and the RF components.

### Open interfaces
==The purposes of the **open interfaces** on the RAN is to break the vendor lock-in in the RAN.== For the example, near-RT RIC from one vendor can interact with base stations from another vendor or CUs, DUs, and RUs from different manufacturers can interoperate each other. 

## II.III. Near-RT RIC Architecture
![image alt](https://iili.io/HazMt49.png)
*img src: https://arxiv.org/pdf/2202.01032.pdf*

- **Internal messaging infrastructure** connects xApps, platform services, and interface terminations to each other. It provides APIs for sending and receiving messages. It also provides routing & robustness to avoid data loss.
- **Conflict mitigation** component will mitigate possible conflicts emerging among different xApps.
- **Subscription manager** allows xApps to connect to fuunction over the E2 interface.
- **Security sub-system** prevent malicious xApps from leaking sensitive RAN data or from affecting the RAN performance.

## II.IV. Non-RT RIC and SMO Architecture
![image alt](https://iili.io/HazV73X.png)
*img src: https://arxiv.org/pdf/2202.01032.pdf*

:::success
**References:**
- [5G Network Architecture](https://www.digi.com/blog/post/5g-network-architecture)
- [5G Basic Architecture](https://5g.systemsapproach.org/arch.html)
- [Understanding O-RAN: Architecture, Interfaces, Algorithms, Security, and Research Challenges](https://arxiv.org/pdf/2202.01032.pdf)
- [SK Telecom 5G White Paper](https://www.sktelecom.com/img/pds/press/SKT_5G%20White%20Paper_V1.0_Eng.pdf)
- [RAN Architecture Components](https://www.researchgate.net/publication/314493826_RAN_Architecture_Components_-_Intermediate_Report)
- [A Survey of the Functional Splits Proposed for 5G Mobile Crosshaul Networks](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=8479363)
- [Functional Splits: the foundation of an Open 5G RAN](https://www.5gtechnologyworld.com/functional-splits-the-foundation-of-an-open-5g-ran/)
:::
