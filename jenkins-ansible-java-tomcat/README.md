# Setup slave machine
[Download Centos 9 x86_64](https://www.centos.org/download/)
[How to CentOS and Static IP](https://www.youtube.com/watch?v=wwnQy4XVJ6I&list=WL&index=150)
Centos:
```
nmtui 
```
```
useradd jenkins_agent
passwd jenkins_agent

usermod -aG test_group jenkins_agent

sudo visudo
    jenkins_agent ALL=(ALL) NOPASSWD:ALL
```
```
sudo firewall-cmd --zone=public --add-port=8080/tcp --permanent
sudo firewall-cmd --reload
```
Ubuntu:
```
ssh-keygen -t rsa -b 2048 -C "jenkins_agent@192.168.56.57"
    /home/peter/.ssh/id_rsa-jenkins_agent@192.168.56.57
ssh-copy-id -i /home/peter/.ssh/id_rsa-jenkins_agent@192.168.56.57 jenkins_agent@192.168.56.57
```

# Run Ansible
```
ansible-playbook -i inventory/hosts playbook.yml  --tags install_tomcat,restart,status
```

# Conclusions
Command:
```

```