# hs-ansible

A set of playbooks to deploy multiple hammerspace clusters, including across different sites.

## Getting Started

### Prerequisites

1. [Ansible](https://www.ansible.com/) including the `community.vmware.vmware_deploy_ovf` module
2. A [VMware](https://www.vmware.com/) cluster
3. A recent [Hammerspace](https://hammerspace.com/) OVA (e.g. hammerspace-4.6.6-197.ova)

### Installation

Clone or download and unzip this repository.

Copy the config template `hammerspace_clusters.yml.TEMPLATE` to `hammerspace_clusters.yml`.

Edit `hammerspace_clusters.yml` so it reflects your environment. The playbook will prompt for your VMware password as well as your desired admin password for login to the cluster WebUI.

Place the desired Hammerspace .ova file in the same directory with the ansible playbooks. If you've cloned the repo, git should ignore an .ova.

## Usage

Kick off the deployment by deploying all the anvils.

`ansible-playbook multi-site-ha.yml`

_Optional step (probably only necessary if you are sharing a network with multiple Hammerspace Anvils deployed)_: Connect the deployed anvils by going to the console of the secondary anvil and selecting the address of the primary. The address of the primary will be displayed on the console while it waits for a connection from the secondary.

Once the installation is complete and all the Anvil consoles display information about the running cluster, you may proceed to DSX deployment:

`ansible-playbook multi-site-ha-dsx.yml`

To join all clusters to the domain defined in the config:

`ansible-playbook multi-site-ha-ad.yml`

To add the defined object storage system and volume:

`ansible-playbook multi-site-osv-add.yml`

To create a share and add all other sites to it as participants

`ansible-playbook multi-site-gfs-join.yml`

## Contact

Mike Bott, Principal Systems Engineer - [@mabott](https://twitter.com/mabott) - mike.bott@hammerspace.com

Project Link: [https://github.com/mabott/hs-ansible](https://github.com/mabott/hs-ansible)

<p align="right">(<a href="#top">back to top</a>)</p>



<!-- ACKNOWLEDGMENTS -->
## Acknowledgments

This project wouldn't exist without these folks' contributions:

* [Lance Shelton](mailto:lance.shelton@hammerspace.com) of [Hammerspace](https://hammerspace.com/) 
for his Ansible and VMware automation knowledge and skills.
* [Douglas Fallstrom](mailto:douglas.fallstrom@hammerspace.com) of [Hammerspace](https://hammerspace.com/) for initial inspiration and many Ansible examples, including Hammerspace REST API playbooks.
* Our excellent crew at [Hammerspace](https://hammerspace.com/) for developing cool storage technology that solves interesting distributed storage problems
