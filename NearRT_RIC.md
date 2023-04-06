[![hackmd-github-sync-badge](https://hackmd.io/Gol_c6KYRaaNYm3P5HHtVg/badge)](https://hackmd.io/Gol_c6KYRaaNYm3P5HHtVg)
:::warning
# <center><i class="fa fa-edit"></i> Near-RT RIC </center>
:::

###### tags: `RIC` `TEEP` `Internship`

:::success
**Learning Objective:**

The study objectives were to:
- Study the architecture of Near-RT RIC
:::

[TOC]

# I. Near-RT RIC
## I.I. Definition
**Near-Real-Time RIC** is a logical function that ==enables near-real-time control and optimization== of O-RAN elements and resources through **xApps**. Near-Real-Time RIC operates on a time scale between **10 ms and 1 s**.

![image alt](https://www.juniper.net/content/dam/www/assets/images/us/en/research-topics/what-is/dgm-1200x535_what-is-RIC-fig-3-06OCT21.jpg/jcr:content/renditions/cq5dam.web.1280.1280.jpeg)
*img src: https://www.juniper.net/us/en/research-topics/what-is-ric.html*

## I.II. Architecture
![image alt](https://rimedolabs.com/wp-content/uploads/2021/04/image-8-smo.png)
*img src: https://rimedolabs.com/wp-content/uploads/2021/04/image-8-smo.png*

- **xApps:** 
    - An application designed to run on near-RT RIC (consist of one or more microservices) that identifies data to consume and provide.
    - Perform the data monitoring and parameter adjustment of RAN functions.
    - Divided into two main parts, i.e. ==image== and ==descriptor==.

- **Messaging Infrastructure:**
    - Deal with message interaction in Near-RT RIC
    - Provides APIs for sending & receiving messages and provides routing & robustness to avoid data loss.
    - Low latency and point to point

- **Conflict Mitigation:**
    -  This component will mitigate possible ==overlapping== or ==conflicting== request from different xApps.
    -  **Direct conflicts:** two or more xApps request different settings to control the target.
    -  **Indirect conflicts:** two or more parameters that affect the same target (e.g. antenna angle and measurement deviation).

- **xApp Subscription Manager:**
    - Manages subscriptions from the xApps to the E2 nodes.
    - Merges subscriptions from different xApps into a single subscription

- **Management Services:**
    - Life cycle management of xApp
    - FCAPS management of Near-RT RIC

- **Security:**
    - Prevent malicious third-party xApps from abusing radio network information.
    
- **Shared Data Layer:**
    - An API that used to store or show any data to database.




:::success
**References:**
- [O-RAN Near-RT RIC](https://rimedolabs.com/blog/o-ran-near-real-time-ric/)
- [Jonathan's notes](https://hackmd.io/bZKeMO7xSWCzZ4vTCM85Ag)
:::