:::warning
# <center><i class="fa fa-edit"></i> Near-RT RIC Projects by OSC</center>
:::

###### tags: `RIC` `TEEP` `Internship`

:::success
**Learning Objective:**

The study objectives were to:
- Understand the components of near-RT RIC Platform Project and how it works
- To map the source code structure provided by OSC
- Understand the basic purpose of a file/folder in each components
:::

[TOC]

# I. RIC Platform (RICPLT)
## I.I. Project Overview
**Near-RT RIC** is subproject of the [O-RAN Software Community](https://o-ran-sc.org/) and working closely with [O-RAN Alliance](https://www.o-ran.org/). The outcome of this project is to develop ==a software based near‐real‐time micro‐service‐based platform for hosting micro-service-based applications (xApps)== that run on the near-RT RIC platform. 

The **near-RT RIC platform** provides infrastructure for controlling a distributed collection of RAN base stations (eNB, gNB, CU, DU) through *southbound* interfaces (**E2 interface**). It also provides the *northbound* interfaces for operators (**A1 and O1 interfaces**).

## I.II. Near-RT RIC Platform Components

![image alt](https://iili.io/H1JaXGR.png)
*img src: https://wiki.o-ran-sc.org/pages/viewpage.action?pageId=10715420&preview=/10715420/35882412/IEEE_oran_sc_2021.pdf*

### A1 Mediator
A1 mediator components listens for **policy types** and **policy instances** requests sent via HTTP from the *northbound* interface and publishes those requests to running xApps via RMR messages.
- **Policy types** are used by A1 to validate instance creation requests.
- **Policy instances** is a concrete values of policy from policy types. There may be many instances of a single type.

> A1 mediator root directory (```a1```) can be found in the [OSC source code](https://wiki.o-ran-sc.org/pages/viewpage.action?pageId=20876303) ==part 2== and contains following folders:
> >```a1```
> >
> >```docs```
> > 
> >```integration_tests```
> >
> > > ```a1mediator```
> > > 
> > > ```dbaas-service```
> > > 
> > > ```testreceiver```
> > > 
> > > ```testxappcode```
> > > 
> >```releases```
> >
> >```tests```

#### a1/a1
|File name|Description|
|----|----|
|```__init__.py```|contains the app|
|```a1rmr.py```|A1's RIC Message Router (RMR) functionality|
|```controller.py```|A1's main controller|
|```data.py```|represents A1 database and database access functions|
|```exceptions.py```|custom exeptions|
|```messages.py```|RMR messages|
|```run.py```|A1 entrypoint|
|```openapi.yaml```|OpenAPI specification for the *northbound* interface. You can use [Swagger Editor](https://editor.swagger.io/) to visualize the OpenAPI files.|

#### a1/docs
|File name|Description|
|----|----|
|```a1_xapp_contract_openapi.yaml```|OpenAPI specification to communicate between A1 and xApp|
|```conf.yaml```|define project_cfg as oran and A1 mediator|
|```developer-guide.rst```|developer guide docummentation and related to [this](https://docs.o-ran-sc.org/projects/o-ran-sc-ric-plt-a1/en/latest/developer-guide.html) webpage|
|```index.rst```|index docummentation|
|```installation-guide.rst```|installation guide docummentation and related to [this](https://docs.o-ran-sc.org/projects/o-ran-sc-ric-plt-a1/en/latest/installation-guide.html) webpage|
|```overview.rst```|overview docummentation and related to [this](https://docs.o-ran-sc.org/projects/o-ran-sc-ric-plt-a1/en/latest/overview.html) webpage|
|```release-notes.rst```|release notes docummentation and related to [this](https://docs.o-ran-sc.org/projects/o-ran-sc-ric-plt-a1/en/latest/release-notes.html) webpage|
|```user-guide-api.rst```|user guide and API's docummentation and related to [this](https://docs.o-ran-sc.org/projects/o-ran-sc-ric-plt-a1/en/latest/user-guide-api.html) webpage|

### O1 Mediator
> O1 mediator root directory (```o1```) can be found in the [OSC source code](https://wiki.o-ran-sc.org/pages/viewpage.action?pageId=20876303) ==part 1== and contains following folders:
> > ```agent```
> > 
> > > ```cli```
> > > 
> > > ```cmd```
> > > 
> > > ```config```
> > > 
> > > ```pkg```
> > > 
> > > > ```nbi```
> > > > 
> > > > ```sbi```
> > > > 
> > > ```test```
> > > 
> > > ```yang```
> > > 
> > ```config```
> > 
> > ```docs```
> > >```__static__```
> > 
> > ```manager```
> > 
> > > ```src```
> > > 
> > ```releases```

### Subscription Manager
**Subscription manager** is responsible for ==managing E2 subscriptions services== from xApps to the E2 Node. The type of services that supported by Subscription manager is **REPORT**, **INSERT**, and **POLICY** (CONTROL is not supported). Subscription manager also ==manages message request routing of the subscribed messages from **Routing Manager**==. 

![image alt](https://docs.o-ran-sc.org/projects/o-ran-sc-ric-plt-submgr/en/latest/_images/PlaceInRICSoftwareArchitecture.png)
*img src: https://docs.o-ran-sc.org/projects/o-ran-sc-ric-plt-submgr/en/latest/user-guide.html*

- Interface between xApp and Subscription Manager is HTTP based on **REST** interface.
- Interface between Routing Manager and Subscription Manager is based on **REST** interface.
- Interface between Subscription Manager and E2 Termination is based on **RMR messages** interface.

:::success
**<center>SUBSCRIPTION PROCEDURE</center>**

![image alt](https://docs.o-ran-sc.org/projects/o-ran-sc-ric-plt-submgr/en/latest/_images/Successful_Subscription.png)
*img src: https://docs.o-ran-sc.org/projects/o-ran-sc-ric-plt-submgr/en/latest/user-guide.html*

1. xApp sends REST subscription request message to Subscription Manager. The request message contains single/multiple E2 subscriptions and xApp instance id for every E2 subscription.
2. Subscription Manager makes validation for data in the request message. The data will be copied to Golang data types. If it succeeds, Subscription Manager will send a successful response to the xApp.
3. Subscription Manager sends route create request to Routing Manager over REST interface.
4. Subscription Manager encodes the E2 messages and forwards those messages (RIC subscription request) to E2 Termination. Then, E2 Termination forward the messages to the E2 node. 
5. E2 Termination forwards feedback messages (RIC subscription response) from E2 Node to the Subscription Manager.
6. Subscription Manager forwards REST subscription notification to xApp. The notification contains REST request id, xApp instance id, and E2 instance id.
:::

> Subscription manager root directory (```submgr```) can be found in the [OSC source code](https://wiki.o-ran-sc.org/pages/viewpage.action?pageId=20876303) ==part 1== and contains following folders:
> >```3rdparty```
> > >```E2AP-v01.00.00```
> > > 
> >```api```
> >
> >```cmd```
> >
> >```config```
> >
> >```docs```
> > > ```__static__```
> > > 
> > > ```images```
> > > 
> >```e2ap```
> > >```libe2ap_wrapper```
> > >
> > >```pkg```
> > >
> >```pkg```
> > > ```control```
> > > 
> > > ```teststub```
> > > 
> > > ```teststubdummy```
> > > 
> > > ```teststube2ap```
> > > 
> >```releases```
> >
> >```test```

#### submgr/api
|File name|Description|
|----|----|
|```routing_manager.yaml```|Routing Manager's RESTful API definition|

#### submgr/cmd
| File name|Description|
|----|----|
|```submgr.go```|to run the Subscription Manager's controller (entrypoint)|

#### submgr/config
|File name|Description|
|----|----|
|```submgr-config.yaml```|Subscription Manager's configuration file defining configuration for local host, logger, RMR, rtmgr (routing manager), and controls|

#### submgr/docs
|File name|Description|
|----|----|
|```release-notes.rst```|release notes docummentation and related to [this](https://docs.o-ran-sc.org/projects/o-ran-sc-ric-plt-submgr/en/latest/release-notes.html) webpage|
|```user-guide.rst```|user guide docummentation and related to [this](https://docs.o-ran-sc.org/projects/o-ran-sc-ric-plt-submgr/en/latest/user-guide.html) webpage|
|```index.rst```|index docummentation|
|```conf.yaml```|define project_cfg as oran and project as submgr|

#### submr/pkg/control
|File name|Description|
|----|----|
|```client.go```|contains functions to create, update, and delete subscription request for routing manager client|
|```control.go```|contains functions to handle subscription request from xApp, subscription delete request from xApp, subscription create, subscription delete, send subscription request to E2T, send subscription delete request to E2T, handle subscription response from E2T, subscription failure from E2T, subscription delete response from E2T, and subscription delete failure from E2T|
|```e2ap.go```|contains functions to pack/unpack subscription request, subscription response, subscription failure, subscription delete request, subscription delete response, and subscription delete failure|
|```registry.go```|contains functions to find existing subscription, assign to subscription, checking service action types, remove from subscription, and get subscription|
|```subscription.go```|contains functions to set/get subscription cached response, get subscription requestor ID, get RMR message ID, and check the mergeable of subscription (only REPORT type subscriptions can be be merged)|
|```timer.go```|contains functions to start/stop the timer|
|```tracker.go```|contains functions to track/untrack the transaction|
|```transaction.go```|contains functions to send event, wait event, get message ID & type, get subscription ID, get payload, release transaction|

### Routing Manager
**Routing Manager** is responsible for ==distributing routing policies== among the other platform components and xApps.

:::success
**<center>STARTUP PROCEDURE</center>**
![image alt](https://wiki.o-ran-sc.org/download/attachments/19071030/rtmgr_start.png?version=1&modificationDate=1584620494229&api=v2)
*img src: https://wiki.o-ran-sc.org/display/RICP/Routing+Manager+Architecture*

1. The Control component through HTTP Client send an HTTP GET method to retrieve the list of deployed xApps and their properties.
2. If it succeeds, xApp manager will send the status OK (code 200) and return the xApp list over HTTP Client.
3. The Routing Policy Engine component will generates the routing table based on the xApp list and return the routing table to the Control component.
4. Control component sends set up connection request to xApps through Messaging component. 
5. After the connection is set up, control component will distributes the routing table to the Messaging, and forwards the routing table to the xApps.
:::

> Routing manager root directory (```rtmgr```) can be found in the [OSC source code](https://wiki.o-ran-sc.org/pages/viewpage.action?pageId=20876303) ==part 1== and contains following folders:
> >```.releases```
> >
> >```api```
> >
> >```cmd```
> >
> >```docs```
> > >```__static__```
> > >
> > >```example```
> > >
> > >```images```
> >
> >```manifests```
> > > ```rtmgr```
> >
> >```pkg```
> > > ```nbi```
> > > 
> > > ```rpe```
> > > 
> > > ```rtmgr```
> > > 
> > > ```sbi```
> > > 
> > > ```sdl```
> > > 
> > > ```stub```
> > 
> >```tst```
> > >```robot```

#### rtmgr/api
|File name|Description|
|----|----|
|```routing_manager.yaml```|Routing Manager's RESTful API definition|

#### rtmgr/cmd
|File name|Description|
|----|----|
|```rtmgr.go```|Routing Manager's main file (entrypoint)|

#### rtmgr/docs
|File name|Description|
|----|----|
|```release-notes.rst```|release notes docummentation and related to [this](https://docs.o-ran-sc.org/projects/o-ran-sc-ric-plt-rtmgr/en/latest/release-notes.html) webpage|
|```developer-guide.rst```|developer guide docummentation and related to [this](https://docs.o-ran-sc.org/projects/o-ran-sc-ric-plt-rtmgr/en/latest/developer-guide.html) webpage|
|```installation-guide.rst```|installation guide docummentation and related to [this](https://docs.o-ran-sc.org/projects/o-ran-sc-ric-plt-rtmgr/en/latest/installation-guide.html) webpage|
|```index.rst```|index docummentation|
|```conf.yaml```|define project_cfg as oran and project as rtmgr|

#### rtmgr
|Folder name|Description|
|----|----|
|```manifests```|contains deployment files|

#### rtmgr/pkg
|Folder name|Description|
|----|----|
|```nbi```|maintains the communication channels towards RIC manager components|
|```rpe```|provides the logic to calculate routing policies|
|```rtmgr```|controls the operation of all functions|
|```sbi```|maintains the communication channels towards RIC tenants and control components|
|```sdl```|provides access to different kind data stores|

#### rtmgr/pkg/nbi
|File name|Description|
|----|----|
|```control.go```|Routing Manager's main controller|
|```httpgetter.go```|HTTP Get method to retrieve the xApp list|
|```httprestful.go```|HTTP Restful API for *northbound* interface|
|```nbi.go```|contains *northbound* interface module definitions components|
|```httpgetter_test.go```|HTTPgetter unit tests|
|```httprestful_test.go```|HTTP Restful API unit tests|
|```nbi_test.go```|*northbound* interface unit tests|
|```types.go```|contains *northbound* interface specific types|

#### rtmgr/pkg/rpe
|File name|Description|
|----|----|
|```rmr.go```|produces RMR (RIC Management Routing) formatted route messages|
|```rmr_test.go```|RMR unit tests|
|```rpe.go```|contains Route Policy Engine module definitions and components|
|```types.go```|contains Route Policy Engine specific types|

#### rtmgr/pkg/rtmgr
|File name|Description|
|----|----|
|```rtmgr.go```|contains Routing Manager module's generic variables and functions|
|```rtmgr_test.go```|Routing Manager unit tests|
|```types.go```|contains Routing Manager specific types|

#### rtmgr/pkg/sbi
|File name|Description|
|----|----|
|```nngpush.go```|RMR Pipeline *southbound* interface implementation|
|```nngpush_test.go```|unit tests|
|```sbi.go```|contains *southbound* interface module definitions and components|
|```sbi_test.go```|*southbound* interface unit tests|
|```types.go```|contains *southbound* interface specific types|

#### rtmgr/pkg/sdl
|File name|Description|
|----|----|
|```file.go```|file Shared Data Layer implementation|
|```sdl.go```|contains Shared Data Layer module definitions and components|
|```sdl_test.go```|Shared Data Layer unit tests|
|```types.go```|contains Shared Data Layer specific types|

### RIC Alarm System

:::success
**<center>RIC ALARM SYSTEM ARCHITECTURE</center>**
![image alt](https://www.linkpicture.com/q/RIC_Alarm_System.png)
*img src: alarm-go/docs/images*
:::

**RIC alarm system** consists of three components: 
1. **Alarm Manager**
	-  Responsible for managing alarm situations in RIC cluster and interfacing with Northbound applications such as **Prometheus Alert Manager** to post the alarms as alerts.
	-  The Alarm Manager listens alarms coming via **RMR & REST interfaces** and commands coming from **CLI (Command Line Interface)**.
	-  ==Alarm Manager commands:== list active alarms, list alarm history, add new alarms definition, delete existing alarm definition, re-raise alarms and clear all alarms.
	
2. **Application Library**
	- Alarm Library ==provides a simple interface== for RIC applications to raise and clear alarms.
	- Interacts with the Alarm Manager via **RMR interface**.
	- Alarm APIs:
    	- **Raise:** raises the alarm instance given as a parameter.
    	- **Clear:** clears the alarm instance given as a parameter, if it the alarm active.
    	- **Reraise:** re-raise the alarm instance given as a parameter.
    	
4. **Command Line Interface (CLI)**
	- Check active alarms/alarm history
	- Raise/clear an alarm
	- Configure maximum active alarms and maximum alarms in alarm history
	- Add/delete alarm definitions that can be raised

> RIC alarm system root directory (```alarm-go```) can be found in the [OSC source code](https://wiki.o-ran-sc.org/pages/viewpage.action?pageId=20876303) ==part 2== and contains following folders:
> > ```alarm```
> > 
> > ```assets```
> > 
> > ```build```
> > 
> > ```cli```
> > 
> > ```config```
> > 
> > ```definitions```
> > 
> > ```docs```
> > > ```__static```
> > > 
> > > ```images```
> > 
> > ```manager```
> >  > ```cmd```
> >  > 
> > ```releases```
> > 
> > ```schemas```
> > 
> > ```testresources```

#### alarm-go/alarm
|File name|Description|
|----|----|
|```alarm.go```|contains function to create a new alarm instance, AlarmMessage instance, clear/raise/re-raise alarm, and clear all alarm raised by applications|
|```alarm_test.go```|RIC alarm unit test|
|```types.go```|RIC alarm specific types|

#### alarm-go/cli
|File name|Description|
|----|----|
|```alarm-cli.go```|RIC alarm command line interface|

#### alarm-go/definitions
|File name|Description|
|----|----|
|```alarm-definition.json```|RIC alarm definition to specifies alarm ID, text, event type, raise/clear delay|

#### alarm-go/docs
|File name|Description|
|----|----|
|```conf.yaml```|define project_cfg as oran and project as alarm-go|
|```index.rst```|index docummentation|
|```user-guide.rst```|user guide docummentation|
|```release-notes.rst```|release notes docummentation|

#### alarm-go/manager/cmd
|File name|Description|
|----|----|
|```manager.go```|contains alarm manager module definitions and components|
|```manager_test.go```|Alarm manager unit tests|
|```restapi.go```|Alarm manager Restful API definitions|
|```restapi_test.go```|Alarm manager Restful API unit tests|
|```types.go```|contains alarm manager specific types|

#### alarm-go/schemas
|File name|Description|
|----|----|
|```alarm-schema.json```|schema for RIC alarm messages|

### E2 Terminator (E2T)

**E2 interface** is used by xApps to collect near-real-time information and provide services.

:::success
**<center>E2AP FUNCTIONAL PROCEDURE</center>**
![image alt](https://www.linkpicture.com/q/3_578.png)
*img src: https://static.sched.com/hosted_files/ones2020/99/ONeS_NA_2020_Thoralf_Czichy_Matti_Hiltunen.pdf*

- **E2 Report**
	- The E2 report service is activated upon subscription from an xApp to the E2 node.
	- During the subscription, xApp in the near-RT RIC can specify event trigger or timer for the E2 node to send the report messages.

- **E2 Insert**
	-  Responsible to notify the xApp about specific event in the E2 node. It is activated upon subscription from an xApp.

- **E2 Control**
	- The E2 control initiated by the RIC based on a procedure with two messages, a *RIC Control Request* and a *RIC Control Acknowledge*.
	- It can be initiated due to the consequence of the reception of an *insert message*.
	
- **E2 Policy**
	- This E2 policy involves a subscription procedure that specifies an event trigger and a policy
	- The policy is followed by E2 node to perform radio resource management.
:::

> E2 Terminator directory (```e2```) can be found in the [OSC source code](https://wiki.o-ran-sc.org/pages/viewpage.action?pageId=20876303) ==part 2== and contains following folders:
> > ```config```
> > 
> > ```docs```
> > > ```_static```
> > > 
> > ```releases```
> > 
> > ```RIC-E2-TERMINATION```
> > > ```3rdparty```
> > > > ```asnTextFiles```
> > > > 
> > > > ```oranE2```
> > > > 
> > > > ```oranE2SM```
> > > > 
> > > ```config```
> > > 
> > > ```TEST```
> > > > ```ASN_LOG```
> > > > 
> > > > ```base64```
> > > > 
> > > > ```ConfigurationFileTest```
> > > > 
> > > > ```e2smTest```
> > > > 
> > > > ```T1```
> > > > 
> > > > ```testAsn```

:::success
**References:**
- [ORAN Software Community Projects](https://wiki.o-ran-sc.org/display/ORAN/Projects) 
- [Near-RT RIC for Open Networking Summit](https://static.sched.com/hosted_files/ones2020/99/ONeS_NA_2020_Thoralf_Czichy_Matti_Hiltunen.pdf)
-  [O-RAN SC G Release Documentation](https://docs.o-ran-sc.org/en/latest/)
-  [Ferlinda's notes](https://hackmd.io/@ferlinda/r1R0VVsAB)
-  [Jonathan's notes](https://hackmd.io/@jonathanrichard/S1X3vo-lO)
:::