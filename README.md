# Arista Lab Builder - VMware ESXi Edition

This project will build a 4 spine, 6 leaf Arista Networks switch topology on top of VMware ESXi, complete with Arista CloudVision Portal (CVP), Arista CloudVision eXchange (CVX), and VMware vCenter. It will also take care of VMware vSwitches as well.

Please bear in mind that I built this to create my environment and it's highly opinionated on its configuration. Perhaps over time I can make this less so.
## Requirements
You will need the following to make this project work:
* This project uses Ansible to build. Anything version 2.1 or above will work.
* You will need a copy of VMware's `ovftool` in `/files`
* A working ESXi host. All you really need for this is a management IP address and a single datastore.
* If you wish to install CVP, you will need the Arista CVP OVA in `files/`
* If you would like to install VMware vCenter, put the OVA in `files/`
* You will need the Arista vEOS-combined VMDK. Put it in `files/`

If you don't wish to install vCenter or CVP, or both, please edit `esxi.yml` and comment out or remove the lines that contain `  - role: vmware-vcenter` and `- role: veos-cvp`.
## Using this Ansible script

Please edit the `groupvars/all` file to change variables. There are hard coded things in there that you will _need_ to change, such as the ESXi datastore, IP addresses, and usernames/passwords. You will also need to edit the `lab` file and modify the IP address for [lab-esxi] to reflect your ESXi management IP address.

Once done, you can run it by issuing a `ansible-playbook -i lab site.yml` 

Please allow for some time (could be as much as an hour) for this to deploy.