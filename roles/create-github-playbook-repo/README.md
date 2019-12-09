Code Promoter
=========

This role will validate the existence of the README file in each of the DEV repos.

Requirements
------------

The user may run this from tower.


Role Variables
--------------

repos_dict                  - the dict storing the repo information
dev_github_fqdn
dev_github_org
dev_github_personal_token
dev_playbook_tag

Example Playbook
----------------

---
 - name: test 
   hosts: all
   gather_facts: false
   roles:
    - role: check-github-readme
    
         
License
-------

BSD
