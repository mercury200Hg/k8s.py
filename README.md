# k8s.py
##### This project aims to provide ansible dynamic inventory for grouping of nodes based on various labels, annotations and IP

##### The snippet structure is similar to dynamic inventory structure required by ansible.

##### To know more about dynamic inventory click [ here ](https://docs.ansible.com/ansible/latest/user_guide/intro_dynamic_inventory.html)

---

#### CONTRIBUTIONS

1. For anyone who wishes to make contribution can fork the repository and raise pull request.
2. Kindly create following files as part of the pull requests.
..* changelog.md -  describing the changes.
..* usage.md - update this file with corresponding usage.

#### Usage
##### Make sure you have installed the requirements.txt via pip or easy_install on your path with Python version 3.6+

* Adhoc commands can be used like-
```shell script
ansible -i k8s.py workers_all -m shell -a "sysctl -w net.core.somaxconn=1024" 
```

* Playbooks can be of following format:
```yaml
- hosts: label_beta_kubernetes_io_instance-type_r5_4xlarge
  become: yes
  serial: 1
  asks:
  - name: Set soft ulimits for openfiles
    pam_limits:
      domain: root
      limit_type: soft
      limit_item: nofile
      value: unlimited
​
  - name: Set hard ulimits for openfiles
    pam_limits:
      domain: root
      limit_type: hard
      limit_item: nofile
      value: unlimited
```


