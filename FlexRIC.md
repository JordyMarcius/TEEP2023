[![hackmd-github-sync-badge](https://hackmd.io/S9M1qdZATVejbHadNDZBnA/badge)](https://hackmd.io/S9M1qdZATVejbHadNDZBnA)
:::warning
# <center><i class="fa fa-edit"></i> FlexRIC</center>
:::

###### tags: `RIC` `TEEP` `Internship`

:::success
**Learning Objective:**

The study objectives were to:
- Understand the definition and purpose of FlexRIC
- Understand the basic architecture of FlexRIC and how it works
:::

[TOC]

# I. FlexRIC

## I.I. Introduction
**FlexRIC** is a Software Development Kit (SDK) that is used to build specialized service-oriented controllers. FlexRIC consists of two main libraries, i.e., ==server library== and ==agent library.== The **server library** will provide an API to implement custom RAN functions to control and/or monitor the RAN by applications. The **server library** manages agent connections and multiplexes messages between iApps and the agents. **iApps** is the short of  internal applications that used to build specialized controllers. iApps can implement the service models by themselves or sends the information to the xApps (external application) via a *northbound* interface.

![image alt](https://www.linkpicture.com/q/1_1386.png)
*img src: https://www.eurecom.fr/en/publication/6737*


## I.II. Architecture

### FlexRIC Agent

![image alt](https://www.linkpicture.com/q/2_855.png)
*img src: https://www.eurecom.fr/en/publication/6737*

The architecture of FlexRIC agent consists of **agent library** and **base station**. 
- The *agent library* provides support to connect to the controller. It consists of **networking interface**, **E2AP abstraction**, **message handler**, and **generic RAN function API**. The E2AP abstraction provides an intermediate representation for the E2 protocol. The generic RAN function API defines callback for E2AP messages.
- The *base station* provides basic node information. The base station uses the interface of pre-defined RAN functions to expose data and handle control messages.

### FlexRIC Controller

![image alt](https://www.linkpicture.com/q/3_599.png)
*img src: https://www.eurecom.fr/en/publication/6737*

The architecture of FlexRIC controller consists **server library** and **controller specialization**. 
- The FlexRIC *server library* is ==used to multiplex agent connections and dispatch E2AP messages.== The **RAN management functionality** in server library is used to handle connection between agent. The information from RAN managemen functionality is stored in the **RAN database**. The **subscription management** is used to keep track of existing subscriptions and deliver messages to the iApps.
- The **controller specialization** implements SD-RAN functionality through iApps (internal applications). The controller specialization communicate with other specialized controller via northbound interface over a custom protocol, such as REST, RMR, message broker, or E2AP.

:::success
**References:**
- [FlexRIC: An SDK for Next-Generation SD-RANs](https://www.eurecom.fr/en/publication/6737)
:::

