# Setup master and slave machines
**Useful links:**
[Download Centos 9 x86_64](https://www.centos.org/download/)<br>
[How to CentOS and Static IP](https://www.youtube.com/watch?v=wwnQy4XVJ6I&list=WL&index=150)<br>

**Centos:**
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

**Ubuntu:**
```
ssh-keygen -t rsa -b 2048 -C "jenkins_agent@192.168.56.57"
    /home/peter/.ssh/id_rsa-jenkins_agent@192.168.56.57
ssh-copy-id -i /home/peter/.ssh/id_rsa-jenkins_agent@192.168.56.57 jenkins_agent@192.168.56.57
```

**Set actual date and time:**
```
sudo date -s $(curl -s "http://worldtimeapi.org/api/timezone/Europe/Warsaw" | grep -oE '"datetime":"[^"]+"' | cut -d'"' -f4)
```
