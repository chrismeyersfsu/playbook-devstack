##playbook-devstack
Provisions an **ec2 m3.medium instance**, assigns an **elastic ip** that is presumed to be bound to the dns entry **devstack.testing.ansible.com**. **Devstack** is then installed. **5** servers are brought up in 2 groups, **3** **eastcoast** and **2** **westcoast**.
```
sudo ansible-galaxy install -r requirements.yml
ansible-playbook site.yml -i devstack.yml -vvvv
```
To verify the install go to http://devstack.testing.ansible.com and login with demo / UbEYy68XF2Uk6eKaLX Select demo from the Projects dropdown. Then select Project -> Compute -> Instances from the navigation on the left. You should see 3 autobot westcoast servers and 2 deceptacon eastcoast servers. These instances should appear when you run nova.py below.

**Note:** The url and password are set in (devstack)[https://github.com/chrismeyersfsu/role-devstack/blob/master/defaults/main.yml] and may be overridden in `common/vars/main.yml`.
