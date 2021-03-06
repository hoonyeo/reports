# CloudStack
 Apache CloudStack is a top-level project of the Apache Software Foundation (ASF). The project develops open source software for deploying public and private `Infrastructure-as-a-Service (IaaS)` clouds.  

CloudStack provides an open and flexible cloud orchestration platform to deliver reliable and scalable private and public clouds  

## 시작하기전에

- IaaS : Infrastructure-as-a-Service
- PaaS : Platform-as-a-Service
- SaaS : Service-as-a-Service

![클라우드 서비스 방식](http://ncc.phinf.naver.net/20160713_127/1468377668993GdoYV_PNG/03.png?type=w646)

## Concepts and Terminology
### What is Apache CloudStack?
 Apache CloudStack is an open source Infrastructure-as-a-Service platform that manages and orchestrates pools of storage, network, and computer resources to build a public or private `IaaS` compute cloud.  

With CloudStack you can :  

- Set up an on-demand elastic cloud computing service.
- Allow end-users to provision resources

### What can Apache CloudStack do?
#### Multiple Hypervisor Support
 CloudStack works with a variety of hypervisors and hypervisor-like technologies. A single cloud can contain multiple hypervisor implementations. As of the current release CloudStack supports:  

- BareMetal (via IPMI)
- Hyper-V
- KVM
- LXC
- vSphere (via vCenter)
- Xenserver
- Xen Project

> BareMetal : 물리서버  
>
> Hyper-V : 마이크로소프트 하이퍼 V(Hyper-V, 코드이름 Viridian)는 x64 시스템을 위한 하이퍼바이저 기반의 가상화 시스템.  
>
> 하이퍼바이저(hypervisor)는 호스트 컴퓨터에서 다수의 운영 체제(operating system)를 동시에 실행하기 위한 논리적 플랫폼(platform)  
>
> KVM : 커널 기반 가상 머신(Kernel-based Virtual Machine, KVM),
 리눅스 커널을 하이퍼바이저로 변환하기 위한 가상화 인프라스트럭처의 하나이다. ([see](https://www.linux-kvm.org/page/Main_Page))  
>
>LXC : LXC (LinuX Containers)는 단일 컨트롤 호스트 상에서 여러개의 고립된 리눅스 시스템 (컨테이너)들을 실행하기 위한 운영 시스템 레벨 가상화 방법이다. ([see](https://linuxcontainers.org/lxc/introduction/))  
>
>vSphere : VMWare vSphere. ([see](https://www.vmware.com/products/vsphere.html))
>
>Xenserver : Open source Virtualization. ([see](https://xenserver.org))  
>&nbsp;&nbsp;&nbsp; Commercial support for XenServer is available from Citrix.
>
>Xen Project : The mission of the Xen Project is to focus upon the development and support of an open source hypervisor and related components, developed and designed to run with the Linux platform. ([see](https://www.xenproject.org))  

#### Massively Scalable Infrastructure Management
CloudStack can manage tens of thousands of physical servers installed in geographically distributed datacenters. The management server scales near-linearly eliminating the need for cluster-level management servers. Maintenance or other outages of the management server can occur without affecting the virtual machines running in the cloud.

#### Automatic Cloud Configuration Management
CloudStack automatically configures the network and storage settings for each virtual machine deployment. Internally, a pool of virtual appliances support the operation of configuration of the cloud itself. These appliances offer services such as firewalling, routing, DHCP, VPN, console proxy, storage access, and storage replication. The extensive use of horizontally scalable virtual machines simplifies the installation and ongoing operation of a cloud.

#### Graphical User Interface
CloudStack offers an administrators web interface used for provisioning and managing the cloud, as well as an end-user’s Web interface, used for running VMs and managing VM templates. The UI can be customized to reflect the desired service provider or enterprise look and feel.

#### API
CloudStack provides a `REST`-like API for the operation, management and use of the cloud.  

> REST : Representational State Transfer


#### AWS EC2 API Support
CloudStack provides an `EC2 API` translation layer to permit the common EC2 tools to be used in the use of a CloudStack cloud.  

> Amazon EC2 : Amazon Elastic Compute Cloud ([see](https://aws.amazon.com/ec2/))

#### High Availability
CloudStack has a number of features to increase the availability of the system. The Management Server itself may be deployed in a multi-node installation where the servers are load balanced. MySQL may be configured to use replication to provide for failover in the event of database loss. For the hosts, CloudStack supports `NIC bonding` and the use of separate networks for storage as well as `iSCSI` Multipath.  

> NIC bonding : 가용 대역폭을 늘리기위해 다수의 NIC를 하나로 묶는 기술. 하나로 묶인 NIC는 동일한 MAC Address를 갖음.  
>
> iSCSI :  Internet Small Computer Systems Interface 의 약어.  
> &nbsp;&nbsp;&nbsp;&nbsp; LAN, WAN, Internet을 이용하여 멀리 떨어진 위치의 Storage를 접근, 사용하는 기술.
