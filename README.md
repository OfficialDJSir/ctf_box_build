# ctf_box_build

This will help build out ctf ready boxes

These should not be used for anthing else!!! (CTF ONLY)

# must run this first on the kali box
```
apt-get install -y ansible openssh
```
## Edit ./hosts file

```
[kali]
192.168.122.199 ansible_user=root ansible_ssh_pass=toor

[windows]
192.168.122.106
```

# config the kali box
```
sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/g' /etc/ssh/sshd_config
systemctl enable openssh
systemctl start openssh
```
# config the windows box 
On install, create admin account named ctf with a password of ctf

In a powershell term RUNNING AS ADMIN, run the following
```
(new-object net.webclient).DownloadFile('https://raw.githubusercontent.com/chashtag/ctf_box_build/master/ConfigureRemotingForAnsible.ps1','ConfigureRemotingForAnsible.ps1')
./ConfigureRemotingForAnsible.ps1
```

# Usage
```
$ ansible-playbook main.yaml -i hosts
```