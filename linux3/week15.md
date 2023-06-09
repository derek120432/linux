# Ansible
```
ansible servers -m ping
ansible servers --list-hosts
```
* 查看目標開機多久<br>
`ansible servers -m command -a "uptime"`
* 查看使用者是否存在<br>
`ansible servers -m command -a "id user"`
> shell
```
ansible servers -m shell -a "ifconfig | grep -A 5 enps33"
ansible-doc -s shell  # 查看shell指令可以加入什麼參數
ansible servers -m shell -a "chdir=/tmp cmd='echo hi>a.txt'" 
ansible servers -m shell -a "echo hi > /tmp/a.txt"  # 跟上面是一樣的效果
ansible servers -m shell -a "chdir=/tmp create=/etc/passwd cmd='echo hi'"  # 不執行ls
ansible servers -m shell -a "chdir=/tmp create=/etc/passwd@@ cmd='echo hi'" # 執行ls
```
* 在遠程主機上執行本地主機上的腳本文件<br>
`ansible server1 -m script -a "./a.sh"`<br>
`ansible server1 -m script -a "./b.sh"`

  * b.sh
  
  ```
  result=`ifconfig | grep -A 5 ens33 | grep inet | grep -v inet6 | awk '{print $2}'`
  echo $result
  ```
* 安裝<br>
`ansible server1 -m yum -a "name=httpd state=latest"`
* 查詢是否安裝 httpd<br>
`ansible server1 -m shell -a "rpm -qa | grep httpd"`
* 移除軟體<br>
`ansible server1 -m yum -a "name=httpd state=absent""`
* 複製<br>

  * `backup=yes` 若是檔案已經存在則會進行備份
  
```
ansible server1 -m copy -a "src=/root/1.txt dest=/tmp/hi.txt backup=yes mode=664 owner=user group=user"
```
* fetch

   * 從遠端複製檔案到本地
`ansible server1 -m fetch -a "src=/etc/passwd dest=/root"`
* 同時安裝

  ```sh
  ansible server1 -m yum -a "name=httpd,vsftpd state=present"
  ```

* 同時查詢兩個套件是否安裝成功

  * `&&`  第一個成功才會執行第二個
  * `||`  第一個成功則不會執行第二個
  * `;`  兩個都會執行

  ```sh
  ansible server1 -m shell -a "rpm-qa | grep httpd; rpm -qa | grep vsftp"
  ```
