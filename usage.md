# Usage
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
