Code Promoter
=========

This playbook will promote code from the DEV organization to the Prod organization. There are a number of validation checks. THe first one checks for the existence of a README.md file in the DEV playbook and the DEV roles.Also, the playbook will fail if you have two Github repos that share the same name.

Requirements
------------

An inventory is required to run this playbook that only consist of Ansible Tower. Also, this playbook needs to have root access to run.


Role Variables
--------------

Too keep the playbook as simple as possible, an example of all the variables needed to run this playbook are stored in the vars directory.


Example Playbook
----------------
```
---
 - name: 'Code promotion'
   hosts: "{{ tower_fqdn }}"
   gather_facts: false
   roles:
     - role: check-github-readme
     - role: grab-tower-ids

 - hosts: "{{ tower_fqdn }}"
   gather_facts: false
   become: true
   roles:
     - role: create-github-role-repo
     - role: promote-dev-github-role-repo
     - role: create-github-playbook-repo
     - role: promote-dev-github-playbook-repo

 - hosts: "{{ tower_fqdn }}"
   gather_facts: false
   roles:
    - role: update-prod-playbook-repo
    - role: create-tower-project
    - role: create-tower-job-template
    - role: update-tower-job-template-survey
    
 ```        
License
-------

BSD
