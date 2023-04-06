[![hackmd-github-sync-badge](https://hackmd.io/7w6MsiqhTZ-iF0--y39gvg/badge)](https://hackmd.io/7w6MsiqhTZ-iF0--y39gvg)
:::warning
# <center><i class="fa fa-edit"></i> O-RAN Components and Interfaces</center>
:::

###### tags: `O-RAN` `TEEP` `Internship`

:::success
**Learning Objective:**

The study objectives were to:
- Study about O-RAN architecture, components, and interfaces
:::

[TOC]

# I. O-RAN Architecture Overview
![image alt](https://docs.o-ran-sc.org/en/latest/_images/o-ran-architecture.png)
*img src: https://docs.o-ran-sc.org/en/latest/_images/o-ran-architecture.png*

![image alt](https://rimedolabs.com/wp-content/uploads/2021/04/Screenshot_2-1024x510.jpg)
*img src: https://rimedolabs.com/wp-content/uploads/2021/04/Screenshot_2-1024x510.jpg*

## I.II. Components
- **O-Cloud:** a cloud computing platform to host O-RAN functions, like near RT-RIC, O-DU, etc
- **O-RU (O-RAN Radio Unit):** a logical node hosting Low-physical layer and RF processing based on a lower layer functional split
- **O-DU (O-RAN Distributed Unit):** a logical node hosting RLC (Radio Link Control)/MAC (Medium Access Control)/high-physical layers based on a lower layer functional split
- **O-CU-CP (O-RAN Central Unit-Control Plane):** a logical node hosting RRC (Radio Resource Control) and CP (Control Plane) part of the PDCP (Packet Data Convergence Protocol)
- **O-CU-UP (O-RAN Central Unit–User Plane):** a logical node hosting the user plane part of the PDCP protocol and the SDAP (Service Data Adaptation Protocol)
- **Near-Real-Time RIC:** a logical function that enables near-real-time control and optimization of O-RAN elements and resources through *xApps*. ==Near-Real-Time RIC operates on a time scale between 10 ms and 1 s.==
- **Non-Real-Time RIC:** a logical function that enables non-real-time control and optimization of RAN elements and resources. ==Non-Real-Time RIC operates on a time scale longer than 1 s.== Non-RT RIC provides guidance, enrichment information, and manage ML models for the near-RT RIC through *rApps*.
- **xApp:** an application designed to run on near-RT RIC (consist of one or more microservices) that identifies data to consume and provide.
- **SMO (Service and Management Orchestration):** a system supporting orchestration of O-RAN components that includes non-RT RIC.

## I.III. Interfaces

### **E2** 
**E2 interface** is an open interface between the near-RT RIC and the E2 nodes (CUs, DUs). The E2 interface ==allows the RIC to control radio resource management and other functionalities of the E2 nodes.== Each E2 nodes contains the RAN functions data. This data can be published by E2 nodes and  the xApps on the near-RT RIC can subscribe to one or more of RAN functions through E2 interface.
![image alt](https://iili.io/Ha6jBSf.png)
*img src: https://arxiv.org/pdf/2202.01032.pdf*

**E2AP (E2 Application Protocol)** provides four services:
- **E2 Report** is responsible to ==report E2 RIC messages that contain data from an E2 node.== This service can send the report messages based on xApp trigger events or periodically.
\
![image alt](https://www.linkpicture.com/q/1.4.png)
*img src: https://static.sched.com/hosted_files/ones2020/99/ONeS_NA_2020_Thoralf_Czichy_Matti_Hiltunen.pdf*

- **E2 Insert** is responsible to ==notify the xApp about specific event in the E2 node.== It is also activated upon subscription from an xApp.
\
![image alt](https://www.linkpicture.com/q/1.7.png)
*img src: https://static.sched.com/hosted_files/ones2020/99/ONeS_NA_2020_Thoralf_Czichy_Matti_Hiltunen.pdf*

- **E2 Control**. This service is based on a procedure with two messages, a ==RIC Control Request== from the RIC to the E2 node, and a ==RIC Control Acknowledge== from the E2 node to the RIC.
\
![image alt](https://www.linkpicture.com/q/1.5_1.png)
*img src: https://static.sched.com/hosted_files/ones2020/99/ONeS_NA_2020_Thoralf_Czichy_Matti_Hiltunen.pdf*


- **E2 Policy**. This service involves a subscription procedure that specifies an ==event trigger== and ==a policy== that the E2 node should autonomously follow to perform radio resource management.
\
![image alt](https://www.linkpicture.com/q/1.6_1.png)
*img src: https://static.sched.com/hosted_files/ones2020/99/ONeS_NA_2020_Thoralf_Czichy_Matti_Hiltunen.pdf*
    
### **O1** 
**O1 interface** ==connects the SMO and the non-RT RIC to the O-RAN== managed elements (near-RT RIC and RAN nodes). ==The O1 interface supports *Management Services* (MnS).== These services allow the SMO to push configurations to the managed nodes, reporting updates from managed nodes to the SMO, stream or report performance data to the SMO, and push or download files on the nodes managed by the SMO.
![image alt](https://iili.io/HaPAbZQ.png)
*img src: https://arxiv.org/pdf/2202.01032.pdf*

### **A1** 
**A1 interface** ==connects the non-RT RIC to the near-RT RIC.==
![image alt](https://iili.io/HaPMe8Q.png)
*img src: https://arxiv.org/pdf/2202.01032.pdf*

The A1 interface provides three main services:
- **A1 policy management** service  is used by the non-RT RIC to ==drive the functionalities of the near-RT RIC== to achieve *Quality of Service* (QoS) and *Key Performance Indicator* (KPI) goals for the RAN.
- **A1 Machine Learning (ML) model management**
- **A1 Enrichment information** service is responsible to ==improve the RAN performance== by providing information that is generally not available to the RAN itself (e.g., capacity forecasts, information elements from sources outside the RAN, aggregate analytics).

### O2
**O2 interface** is responsible to manage the platform resources and workload (FCAPS management).

:::info
**FCAPS** refers to five working levels of network management i.e. fault, configuration, accounting, performance, and security.
:::

:::success
**References:**
- [O-RAN Architecture Overview](https://docs.o-ran-sc.org/en/latest/architecture/architecture.html)
- [The O-RAN SC RIC](https://static.sched.com/hosted_files/ones2020/99/ONeS_NA_2020_Thoralf_Czichy_Matti_Hiltunen.pdf)
- [O-RAN Near-Real-Time RIC](https://rimedolabs.com/blog/o-ran-near-real-time-ric/)
:::
