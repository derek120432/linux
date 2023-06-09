# Zabbix Line Notify
[參考](https://dotblogs.com.tw/xerion30476/2019/08/28/153643)
> 取得line token

登入line:https://notify-bot.line.me/zh_TW/<br>
登入帳號後，下拉選項，選取「個人頁面」→「發行權杖」→「透過1對1聊天接收LINE Notify的通知」<br>
> zabbix server

`vim /usr/lib/zabbix/alertscripts/line_notify.sh`
```
#!/bin/bash
# LINE Notify Token - Media > "Send to".
TOKEN="從發行權杖取得"

# {ALERT.SUBJECT}
# subject="$1"

# {ALERT.MESSAGE}
message="$1"

curl https://notify-api.line.me/api/notify -H "Authorization: Bearer ${TOKEN}" -F "message=${message}"
```
權限
```
chmod 755 /usr/lib/zabbix/alertscripts/line_notify.sh
chown zabbix:zabbix /usr/lib/zabbix/alertscripts/line_notify.sh
```
test
```
./line_notify.sh test "Sent f from my centos7"
```
![](images/zabbixLine01.jpg)
> zabbix 網頁
![](images/zabbixLine02.jpg)
![](images/zabbixLine03.jpg)
![](images/zabbixLine04.jpg)
![](images/zabbixLine05.jpg)
![](images/zabbixLine06.jpg)
![](images/zabbixLine07.jpg)
![](images/zabbixLine08.jpg)
![](images/zabbixLine09.jpg)
![](images/zabbixLine10.jpg)
![](images/zabbixLine11.jpg)
## Successfully
![](images/zabbixLine12.jpg)
***
# custom_parameter
`vim /etc/zabbix/zabbix_agentd.conf`<br>
![](images/custom01.jpg)
![](images/custom02.jpg)
![](images/custom03.jpg)
![](images/custom04.jpg)
![](images/custom05.jpg)
* custom item<br>
###　successfully
![](images/custom06.jpg)
