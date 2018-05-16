# ctf_box_build



#must run this first on the kali box
```
apt-get install -y ansible openssh
```
##Edit ./hosts file

```
[kali]
192.168.122.199 ansible_user=root ansible_ssh_pass=toor
```

#If using remotely run this on kali box
```
sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/g' /etc/ssh/sshd_config
systemctl enable openssh
systemctl start openssh
```


#Usage
```
$ ansible-playbook main.yaml -i hosts
```