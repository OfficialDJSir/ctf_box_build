# ctf_box_build
apt-get install -y ansible openssh

#if using remotely
sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/g' /etc/ssh/sshd_config
systemctl enable openssh
systemctl start openssh