---
title: "Homelab"
date: 2022-12-23T09:03:20-08:00
tags : ["homelab", "vmware"]
---

<!--more-->

## Hardware
-  Dell PowerEdge R740
    - 2 x Intel Xeon Gold 6132 2.6Ghz 14-Core
    - 256GB RAM - 8 x 32GB 2400T DDR4 ECC
    - H730p 2gb Cache Raid Controller PCIe
    - 2x 1TB SSD in Raid 1 (Samsung 850)
    - Broadcom 2x 10Gbe SFP / 2x 1Gbe Network Daughter Card (165T0)
    - iDrac 9 Enterprise
    - 2x 750w Platinum Power Supplies
-  Dell PowerEdge R720
    - 2 x Intel(R) Xeon(R) CPU E5-2640 6-Core
    - 128GB RAM - 16 x 8GB ECC PC3-12800 1333Mhz 
    - Replaced DVD with Samsung SSD 860 EVO 500GB, used as boot drive [https://www.youtube.com/watch?v=Nx9-BK0WsxU](https://www.youtube.com/watch?v=Nx9-BK0WsxU)
    - SABRENT NVMe M.2 SSD to PCIe Riser [ https://www.amazon.com/gp/product/B084GDY2PW/](https://www.amazon.com/gp/product/B084GDY2PW/)
    - WD_BLACK 2TB SN770 NVMe [https://www.amazon.com/gp/product/B09QV5KJHV](https://www.amazon.com/gp/product/B09QV5KJHV)

## Software
[VMware vSphere 8](https://www.vmug.com/membership/vmug-advantage-membership/) Licenses provided by VMUG Advantage membership

## Outline

1. Install ESXi 8 to 500GB SSD on R720.  
    - YES I received the warning regarding unsupported CPU.  This has yet to keep me from using vSphere 8 on this server.  I did have to get creative with storage since my LSI2008 or PERC 310 aren't supported.  
    - After installation I had 337.5GB for `Datastore1` which I renamed to `local_ssd500GB` and have so far managed to squeeze 8 VMs onto it thanks to thin provisioning.
1. Install pi-hole on Ubuntu 22.04 LTS VM
    - [Configure pi-hole](https://www.youtube.com/watch?v=FnFtWsZ8IP0) with [recursive DNS](https://docs.pi-hole.net/guides/dns/unbound/) and add DNS entries for vCenter vm.
1. Install vCenter
1. [Install TrueNAS Core](https://www.truenas.com/docs/solutions/integrations/vmware/deploytninvmware/) as a VM and add 150GB drive to be used as [iSCSI target](https://www.servethehome.com/building-a-lab-part-3-configuring-vmware-esxi-and-truenas-core/)
1. [Install vSphere 8 as VM](https://www.infotechram.com/index.php/2022/09/17/how-to-install-esxi-server-8-vsphere-8-as-nested-vm/)

