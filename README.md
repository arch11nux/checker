# checker
playbook checker
---
# Ansible Playbook - check Security Compliance on Linux servers \
- name: "Playing with Ansible" \
  hosts: esxcentos7:esxcentos8:esxubuntu \
  user: ransible \
  sudo: yes \
  connection: ssh \
  gather_facts: true \
  vars: \
    var_firewalld: False \
    var_linenum: False \
    var_obsolete_services: False \
    var_rh8_security_features: True \
    var_selinux: False \
    var_azure: False \
  tasks: \
  #--------------------------
  - name: "firewalld" \ \
    include_role: \
      name: firewalld \
    when: (var_firewalld and ansible_facts['distribution'] == "RedHat" and ansible_facts['distribution_major_version'] == "7") \
  #--------------------------
  - name: "linenum" \
    include_role: \
      name: linenum \
    when: (var_linenum and ansible_facts['distribution'] == "RedHat" and ansible_facts['distribution_major_version'] == "7") \
  #--------------------------
  - name: "obsolete-services" \
    include_role: \
      name: obsolete-services \
    when: (var_obsolete_services and ansible_facts['distribution'] == "RedHat" and ansible_facts['distribution_major_version'] == "7") \
  #--------------------------
  - name: "rh8-security-features" \
    include_role: \
      name: rh8-security-features \
    when: (var_rh8_security_features and ansible_facts['distribution'] == "RedHat" and ansible_facts['distribution_major_version'] == "8") \
  #--------------------------
  - name: "selinux" \
    include_role: \
      name: selinux \
    when: (var_selinux and ansible_facts['distribution'] == "RedHat" and ansible_facts['distribution_major_version'] == "7") \
  #--------------------------
   - name: "azure" \
    include_role: \
      name: azure \
    when: var_azure \
  #--------------------------
...
