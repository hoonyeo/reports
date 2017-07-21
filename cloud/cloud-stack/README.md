# CloudStack
 Apache CloudStack is a top-level project of the Apache Software Foundation (ASF). The project develops open source software for deploying public and private `Infrastructure-as-a-Service (IaaS)` clouds.  

CloudStack provides an open and flexible cloud orchestration platform to deliver reliable and scalable private and public clouds

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
