##playbook-devstack

Provisions an **ec2 m3.medium instance**, assigns an **elastic ip** that is presumed to be bound to the dns entry **devstack.testing.ansible.com**. **Devstack** is then installed. **5** servers are brought up in 2 groups, **3** **eastcoast** and **2** **westcoast**.
```
sudo ansible-galaxy install -r requirements.yml
ansible-playbook site.yml -i inventory.devstack --extra-vars="nova_password=<yourpasswordhere>"
```
To verify the install go to http://devstack.testing.ansible.com and login with demo / `<yourpasswordhere>` Select demo from the Projects dropdown. Then select Project -> Compute -> Instances from the navigation on the left. You should see 3 autobot westcoast servers and 2 deceptacon eastcoast servers. These instances should appear when you run nova.py below.

##Requirements

The key specified in `ec2_key` must be available to the playbook via inventory.devstack `ansible_ssh_private_key_file`.

##Dependencies

[devstack](https://galaxy.ansible.com/list#/roles/2858) role

##Example Playbook Invocations

Only install devstack.
```
ansible-playbook site.yml -i 'devstack.testing.ansible.com,` -vvvv --tags "devstack_setup"
```
Only bring up nova instances.
```
ansible-playbook site.yml -i `devstack.testing.ansible.com,` -vvvv --tags "devstack_nova"
```