# Ansible: The Language of DevOps
Ansible can manage powerful automation tasks and can adapt to many workflows and environments. At the same time, new users of Ansible can very quickly use it to become productive.

---

### Installing Ansible 
**Step 1:  Install the ansible-navigator package that provides automation content navigator so that you can use that machine as your control node.**

`python3 -m pip install ansible-navigator`

**Step 2: Verify that automation content navigator is installed on the system. Run the ansible-navigator command with the --version option.**

`ansible-navigator --version`

---

### Example of creating a custom static inventory file

`[webservers]`

`server[a:d].lab.example.com`   

`[raleigh]`

`servera.lab.example.com`

`serverb.lab.example.com`   

`[mountainview]`

`serverc.lab.example.com`

`[london]`

`serverd.lab.example.com`

`[development]`

`servera.lab.example.com`

`[testing]`

`serverb.lab.example.com`

`[production]`

`serverc.lab.example.com`

`serverd.lab.example.com`

`[us:children]`

`raleigh`

`mountainview`

---

### Use variations of the ansible-navigator inventory command to verify the managed hosts and groups in the custom inventory file.

`ansible-navigator inventory -i playbook-inventory -m stdout --list `

`ansible-navigator inventory -i playbook-inventory -m stdout --graph`

`ansible-navigator inventory -i playbook-inventory -m stdout --host servera.lab.example.com`

`ansible-navigator inventory -i playbook-inventory -m stdout --host serverz.lab.example.com`

`ansible-navigator inventory -i playbook-inventory -m stdout --graph us`

`ansible-navigator inventory -i playbook-inventory -m stdout --graph ungrouped`

`ansible-navigator inventory -i playbook-inventory`

---

### Configure automation content navigator to use the execution environment image quay.io/ansible/creator-ee:v0.9.1 and to only pull the image if it is missing. Also configure automation content navigator to disable playbook artifacts.

![image](https://github.com/saurabhkothawade01/ansible-practice-mini-projects/assets/68688738/a11b71be-1897-4464-98ff-893699fd8ade)

---

### Run the ansible-navigator images command to list the available execution environment images.

`ansible-navigator images`

---

### Example of ansible.cfg file

[defaults]  
inventory = ./inventory  
remote_user = someuser  
ask_pass = false  


[privilege_escalation]  
become = true  
become_method = sudo  
become_user = root  
become_ask_pass = false  

---

### Running Playbooks

`ansible-navigator run -m stdout playbook.yml -i inventory`

---

### Syntax Verification

`ansible-navigator run -m stdout playbook.yml -i inventory --syntax-check`

---

### Executing a Dry Run

`ansible-navigator run -m stdout playbook.yml -i inventory --check`

---
