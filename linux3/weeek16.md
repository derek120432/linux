# ansible-playbook
ex1:Hello world
```
---  # 代表文件開始
- hosts: server1 # 應用在哪個主機，-後面記得要空白
  remote_user: root # 遠端使用哪個使用者操作 # 這個可寫可不寫

  tasks:
    - name: hello world # 工作名稱  # 不能使用tab，要用四個空白
      command: /usr/bin/wall hello world # 執行的指令
```
`/usr/bin/wall`: 用來傳送文字給所有連線的人<br>

use ansible:

    ansible server1 -m command -a '/usr/bin/wall hello world'
use ansible-playbook
    
    ansible-playbook -C hello.yml
***
ex2:setup_httpd.yml<br>
* 自動產生網頁的ansible book
```
---
- hosts: server1
  remote_user: root
  tasks:
    - name: create new file  # 產生新檔案 (測試用)
      file: name=/tmp/newfile state=touch  # 使用file模組產生
    - name: create new user  # 產生使用者 (測試用)
      user: name=test2 system=yes shell=/sbin/nologin  # 生成系統使用者
    - name: install package # 安裝 httpd 套件
      yum: name=httpd
    - name: copy html # 將檔案複製到 app2 的指定資料夾
      copy: src=a.html dest=/var/www/html
    - name: start service # 啟動 httpd 服務
      service: name=httpd state=started
```
***
ex3:test.yml

* 透過/bin/true，忽視錯誤輸出，並繼續執行
```
---
- hosts: server1
  remote_user: root
  tasks:
    - name: show date
      command: date
    - name: run a shell script  # 省略前方的 tasks
      shell: /usr/bin/somecommand || /bin/true  # 忽略錯誤
    - name: show hostname
      command: hostname
```
***
ex4:Notify, Handler

由於 ansible 不論執行一次或多次結果都相同，會導致儘管修改了 httpd 的 Port 後，Port 仍然留在 80<br>
notify 後的 restart httpd 會觸發 handlers 中 name 為 restart httpd 的 service<br>

step1:
```
scp root@centos7-2:/etc/httpd/conf/httpd.conf  # 複製另一台的httpd設定檔到本地，這邊是先做測試
vim /etc/httpd/conf/httpd.conf    #修改->Listen 8080
```
step2:httpd_setport.yml
```
---
- hosts: servers
  remote_user: root
  tasks:
  # 編輯 copy html 的 task
    - name: install package # 安裝 httpd 套件
      yum: name=httpd
    - name: copy html # 將檔案複製到 server1 的指定資料夾
      copy: src=/etc/httpd/conf/httpd.conf dest=/etc/httpd/conf
      notify: restart httpd # 完成這邊就要執行下面的內容
    # 省略 start service 的 task
  handlers: # 明確告訴電腦一定要執行這件事情
    - name: restart httpd # 名字必須要和notify一樣
      service: name=httpd state=started # new line
```
***
ex5:
```
cd ..

mkdir test5

cd test5

vim test5.yml

---
- hosts: app2
  remote_user: root
  tasks:
  # 省略前方的 tasks
  - name: install new package
    yum: name={{ pkgname }}

  handlers:
    - name: restart httpd
      service: name=httpd state=started
```
