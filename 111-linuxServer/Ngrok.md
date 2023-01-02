Ngrok

```
su
rpm -aq | gerp httpd
如果沒有insatall yum -y httpd
systemctl startppd
systemctl status httpd
lsof -i:80 or netstat -tunlp | grep 80
curl 127.0.0.1
echo $?
ifconfig
yum install epel_release
yum install snapd
systemctl enable --now snapd.socket
ln -s /var/lib/snapd/snap /snap
snap install ngrok
之後 token

```

