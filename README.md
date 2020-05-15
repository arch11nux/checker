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
    global_check_mode__command: True \
    global_lineum_check__command: False \
    global_redhat_security_features__command: False \
    global_posix_capabilities_check__command: False \
    global_selinux_remediation__command: False \
  tasks: \
  #-------------------------- \
  - include_role: \
      name: global_lineum_check \
    when: global_lineum_check__command \
    check_mode: "{{ global_check_mode__command }} \
  #-------------------------- \
  - include_role: \
      name: global_redhat_security_features \
    when: global_redhat_security_features__command \
    check_mode: "{{ global_check_mode__command }} \
  #-------------------------- \
  - include_role: \
      name: global_posix_capabilities_check \
    when: global_posix_capabilities_check__command \
    check_mode: "{{ global_check_mode__command }} \
  #-------------------------- \
  - include_role: \
      name: global_selinux_remediation \
    when: global_selinux_remediation__command \
    check_mode: "{{ global_check_mode__command }} \
  #--------------------------
...
