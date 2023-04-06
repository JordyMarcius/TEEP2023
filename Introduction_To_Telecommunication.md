[![hackmd-github-sync-badge](https://hackmd.io/e0MDt37NRZOsOrwBAOHHwA/badge)](https://hackmd.io/e0MDt37NRZOsOrwBAOHHwA)
:::warning
# <center><i class="fa fa-edit"></i> Introduction to Telecommunication and Networking</center>
:::

###### tags: `Telecommunication` `Networking` `TEEP` `Internship`

:::success
**Learning Objective:**

The study objectives were to:
- Find out telecommunication definition
- Understand the elements of telecommunication system
- Understand basic mode of telecommunication
- Understand analog & digital communication system
- Understand about network definition
- Find out types of networks
- Understand what is network protocol and how it works
- Understand about mobile network
:::

[TOC]

# I. Telecommunication

## I.I. What is Telecommunication?
**Telecommunication** is the ==exchange of information over a significant distance== by electrical or electronic devices which covers text, voice, and video transmission. Telecommunications technology refers to distance communications, such as radio, wired phone, mobile phone, satellite, microwave, fiber optics, internets, and telegraphs.

## I.II. Elements of a Telecommunication System
![image alt](https://iili.io/H0Q7RCG.png)

Telecommunication system consists of three primary elements i.e. 
1. **Transmitter**. 
The transmitter side is responsible to ==takes information from a source of information and converts it to a transmitted signal.== Process to converts source of information into transmitted signal called **encode**.

2. **Transmission medium**
Transmission medium also called **channel** is responsible to ==deliver the transmitted signal== from transmitter side to receiver side.

3. **Receiver**
Receiver side is responsible to ==receive and converts the information signal into real information.== Process to converts received signal into user of information called **decode**.

:::info
**Functions of telecommunication system:**
- To transmit the information
- Establish interface between transmiter and receiver
- Process the information
- Control flow of information
:::

## I.III. Basic Modes of Telecommunication
![image alt](https://www.digi.com/resources/documentation/Digidocs/90001456-13/resources/images/rf_kits/communication_models_2_500x250.png)
*img src: https://www.digi.com/resources/documentation/Digidocs/90001456-13/resources/images/rf_kits/communication_models_2_500x250.png*

| Broadcasting | Point to point |
|--------------|----------------|
|Communication between single transmitter  linked together with a large number of receiver|Communication over a single link or channel between a single transmitter and single receiver|
|Single or multiple receiver devices|Single receiver device|
|Security issues because information transmitted to all receiver devices|Provides security and privacy because communication channel is not shared|
|Example: radio and television broadcasting|Example: telephone, email|

## I.IV. Types of Communications System
### a. Analog Communications
Analog communication refers to **continous signal** or data that is transferred in the communication system. In analog communication, the data is transferred from transmitter to receiver with the help of analog signal. ==Analog signal represented as  continuous signal wave with varying amplitude with time.==

![image alt](https://media.geeksforgeeks.org/wp-content/uploads/20200824100253/analog.png)
*img src: https://media.geeksforgeeks.org/wp-content/uploads/20200824100253/analog.png*

Firstly, the data from source of information (such as text, voice, or video) needs to be converted into **continous signal** form using input transducer. Then, the output signal from input transducer is converted into **electromagnetic waves** with the help of analog modulation technique. ==Modulation is the process of multiplying the low-frequency information signal with a high-frequency carrier signal.== After that, this signal is transmitted through the communication channel. In the receiver side, there is **demodulator** and output transducer to convert electromagnetic waves of data into output message.

:::info
**Analog modulation technique:**
- Amplitude modulation
- Frequency modulation
- Pulse code modulation
:::

### b. Digital Communications
Digital communication use **digital data** during the transmission. ==Digital data refers to information that has **discrete values** and only consists of two states i.e. LOW & HIGH or 0 & 1.== 

![image alt](https://media.geeksforgeeks.org/wp-content/uploads/20200824101738/digital.png)
*img src: https://media.geeksforgeeks.org/wp-content/uploads/20200824101738/digital.png*

Generally, both analog and digital communication system is similar to each other. The main difference is digital communication use **encoder** to converts information data into discrete signal form. On the other side, **decoder** is used to converts discrete signal form into output message.

:::info
**Digital modulation technique:**
- Amplitude Shift Keying (ASK)
- Frequency Shift Keying (FKS)
- Phase Shift Keying (PSK)

**Digital encoding technique:**
- Non Return to Zero (NRZ)
- Return to Zero (RZ)
- Manchester Coding
- Alternate Mark Inversion (AMI)
:::

# II. Network

## II.I. Network Definition
**Network** is a communication system that are ==linking two or more computers/electronic devices== in order to share resources, exchange data, and to communicate with each other. The computers or electronic devices on a network may be linked through cables, radio waves, fiber optic, or satellites.

## II.II. Types of Networks
- **Personal Area Network (PAN):**
    - Cover very small area (single room or building).
    - Used to connect a small number of devices.
    - Example: bluetooth connection.
- **Local Area Network (LAN):**
    - Connects a groups of devices in a local area such as office, home, and school.
    - Rely on cables to connect to the network.
- **Wireless Local Area Network (WLAN):**
    - Basically, WLAN is LAN without cables to connect to the network.
    - Example: WiFi.
- **Metropolitan Area Network (MAN):**
    - Larger than LAN, but smaller than WAN.
    - Connects multiple LANs together.
    - Cover large area such as town or city.
- **Wide Area Network (WAN):**
    - Connects computers and devices worldwide.
    - Maintained by multiple administrators.
- **Storage Area Network (SAN):**
    - A LAN that is designed to handle large data transfers and storage.
- **Virtual Private Network (VPN):**
    - Used to increase security and privacy while accessing a network.
    - VPN acts as a middleman between users and the network by encrypting users data and hiding user identity.

## II.III. Network Topology
![image alt](https://www.swissns.ch/site/wp-content/uploads/2017/06/network-topologies.png)
*img src: https://www.swissns.ch/site/2017/06/the-various-types-of-network-topologies/*

## II.IV. Network Protocol
A **network protocol** is ==a set of rules that govern data communication between different devices in the network.== Network protocols break larger processes into small and specific tasks or functions. Computer or devices on both sides (transmitter and receiver) of a communication  exchange must accept and follow protocol conventions. Otherwise, the devices can't communicate to each other.

The majority of network protocols used are structurally based on the standard **OSI (Open Systems Interconnection)** model. The OSI model splits the communication process between two network devices into 7 layers and one or more network protocols govern activities at each layer. ==Layer 7, 6, 5 are grouped as upper layer== which deal with **software and applications** and ==layer 4, 3, 2, 1 are grouped as lower layer== which deal with **data transport**.
![image alt](https://www.manageengine.com/network-monitoring/images/network-protocols-osi.jpg)
*img src: https://www.manageengine.com/network-monitoring/images/network-protocols-osi.jpg*

|No|Layer|Function|
|--------------|----------------|----------------|
|7|Application layer|It provides protocols that allow software to send and receive information, present data to users, example: Hypertext Transfer Protocol (HTTP)|
|6|Presentation layer|It is responsible to encode, encrypt, and compress data.|
|5|Session layer|It creates communication channels called sessions, ensure the sessions still open while data is being transfered, and close the sessions when communication ends|
|4|Transport layer|Responsible to flow control, set the data rate, error control, request again if the data is received incorrectly|
|3|Network layer|Breaking up segments into network packets, and reassembling the packets on the receiving end|
|2|Data link layer|Breaking up packets into frames and sends them from source to destination|
|1|Physical layer|It is responsible for the physical cable or wireless connection between network nodes|


# III. Mobile Network
## III.I. Definition
**Mobile network** or **cellular network** is ==a communication network that allows mobile phones to communicate each others wirelessly.== Mobile phones work by sending and receiving low power radio signals. The signals are sent to and received from antennas that are attached to radio transmitters and receivers, also called **base station**. The base stations are linked to the others mobile phones and and pass the signal/call on into those networks.

![image alt](https://amta.org.au/wp-content/uploads/2019/06/Network-transfer-path.jpg)
*img src: https://amta.org.au/wp-content/uploads/2019/06/Network-transfer-path.jpg*

:::info
**Advantages:**
- Increased efficiency: faster data transfer.
- Flexibility: can be used everywhere without need to carry cables.
- Reduced cost: more cheaper to install and maintain than wired networks.
:::

## III.II. Main Components
![image alt](https://5g.systemsapproach.org/_images/Slide01.png)
*img src: https://5g.systemsapproach.org/arch.html*

Mobile/cellular network consists of two main components i.e. **Radio Access Network** and **Mobile Core**. In 4G term, RAN base station is called ==*eNodeB*/*eNB*== (evolved node B and mobile core called ==*EPC*== (Evolved Packet Core). In 5G term, RAN base station is called ==*gNodeB*/*gNB*== (next generation node B) and the mobile core is called ==*NG-Core*== (Next Generation Core).

**The RAN purposes:**
- Manages the radio spectrum
- Ensures the efficiency RAN energy
- To optimize the quality-of-service (QoS) requirements for every user.

**The Mobile Core purposes:**
- Provides Internet connectivity for data and voice services.
- Tracks user mobility to ensure uninterrupted service.
- Tracks subscriber usage for billing and charging.

## III.III. Evolution of Mobile Network
### 0G
- 0G refers to ==pre cellular mobile telephony== technology in 1970’s., such as radio telephones in cars or trucks.
- Used for ==basic voice communication.==
- Example technology:
    - **Autoradiopuhelin (ARP)** launched in 1971 in Finland
    - **B-Netz** launched in 1972 in Germany
### 1G
- Analog system and the ==first generation of analog cell phones== that supports speed up to 2.4kbps.
- Unable to interoperate between countries.
- Lack of security.
- Used for ==basic voice communication.==
- Example technologies:
    - **Advance Mobile Phone System (AMPS)** launched by US.
    - **Total Access Communication System (TACS)**

### 2G
- **Wireless cellphones** based on **digital system**, which ==used for text message, picture messages, and multimedia messaging service (MMS).==
- Has greater security because all messages are digitally encrypted.
- Uses digital mobile access technology such as TDMA and CDMA. **TDMA (Time Division Multiple Access)** divides signal in time slot. **CDMA (Code Division Multiple Access)** will allocates each user with a special code to communicate over a multiplex pyshical channel.
- Example technologies:
    - **Group Special Mobile (GSM)** as a standard of all the mobile technologies in the world. Data transfer ==speed up to 14.4 Kbps.==
    - **General Packet Radio Service (GPRS)** and known as 2.5G system because the extension of existing 2G networks. Data rates from ==56 Kbps up to 284 Kbps.== Provides services such as Wireless Application Protocol (WAP) access, Multimedia Messaging Service (MMS), and internet communication seervices.

### 3G
- 3G is based on the **International Telecommunication Union (ITU)** plan to implement global frequency band in the 2000 MHz range, which will support wireless communication standard for all countries throughout the world (IMT-2000). 
- 3G networks technologies offer services such as ==wide area wireless voice telephony, video calls, mobile television, global positioning system (GPS), internet access, and broadband wireless data.==
- Improved CDMA to wide CDMA or W-CDMA
- Example technologies:
    - **High Speed Downlink Packet Access (HSDPA)**, also called 3.5G which allow for higher data transfers speeds. Downlink data transmission rate up to 8-10 Mbit/s over 5MHz bandwidth.
    - **High Speed Uplink Packet Access (HSUPA)** which enhance uplink speed up to 1.4-5.8 Mbps.

### 4G
- ==Strong security== as well as high data transfer speed.
- Download rate up to ==100Mbps.==
- Introduced **OFDMA (Orthogonal Frequency Division Multiple Access)**, the data packets sends by dividing the channel into a narrow band for greater efficiency.
- Example technologies:
    -  **Worldwide Interoperability for Microwave Access (WiMAX)**
    -  **Long Term Evolution (LTE)**

|Features|1G|2G|3G|4G|5G|
|----|----|----|----|----|----|
|Technology|AMPS, NMT, TACS|GSM|WCDMA|LTE, WiMax|MIMO|
|Frequency|30 KHz|1.8 GHz|1.6-2 GHz|2-8 GHz|3-30 GHz|
|Bandwidth|2 kbps|14.4-64 kbps|2 Mbps|2 Mbps - 1 Gbps|> 1 Gbps|
|Access systems|FDMA|TDMA CDMA|CDMA|CDMA|OFDM BDMA|

:::success
**References:**
- [Telecommunications](https://www.techtarget.com/searchnetworking/definition/telecommunications-telecom)
- [Telecommunication Technologies](https://www.ripublication.com/aeee/54_pp%20%20%20421-426.pdf) 
- [Computer networks](https://www.sierraexperts.com/7-types-of-computer-networks-explained)
- [Network protocol](https://www.techtarget.com/searchnetworking/definition/protocol)
- [How mobile networks works](https://amta.org.au/1041-2/)
- [Evolution of mobile networks](https://www.academia.edu/13885065/Mobile_Network_Architecture_Evolution_1G_to_4G) 
- [Evolution of Mobile Wireless Technology from 0G to 5G](https://ijcsit.com/docs/Volume%206/vol6issue03/ijcsit20150603123.pdf)
- [OSI Model](https://www.imperva.com/learn/application-security/osi-model/)
- [1G Vs. 2G Vs. 3G Vs. 4G Vs. 5G](http://net-informations.com/q/diff/generations.html)
- [Evolution of wireless technologies 1G to 5G in mobile communication](https://www.rfpage.com/evolution-of-wireless-technologies-1g-to-5g-in-mobile-communication/)
:::