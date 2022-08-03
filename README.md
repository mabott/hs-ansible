# hs-ansible

Deploying Hammerspace OVA in VMware

This set of playbooks deploys multiple Hammerspace clusters.

Copy the config template hammerspace_clusters.yml.TEMPLATE to hammerspace_clusters.yml.

Place the desired Hammerspace .ova file in the same directory with the ansible playbooks.

Edit it so it reflects your environment. The playbook will prompt for your VMware password as well as your desired admin password for login to the cluster WebUI.

ansible-playbook multi-site-ha.yml

Connect the deployed anvils by going to the console of the secondary anvil and selecting the address of the primary. The address of the primary will be displayed on the console while it waits for a connection from the secondary.

Once the installation is complete and the console displays information about a running cluster, you may proceed to DSX deployment.

ansible-playbook multi-site-ha-dsx.yml

To join all clusters to a domain

ansible-playbook multi-site-ha-ad.yml

To create a share and add all other sites to it as participants

ansible playbook multi-site-gfs-join.yml

