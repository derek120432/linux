linux

```markdown
ifconfig |grep inet |  | awk '{print $2}' #
apt-get install -- ##ubuntu
sum install --- ## centos
ctrl+a ##移到最前面
ctrl+e ##移到最後面
ls -a ##檢視隱藏檔案 .cache(隱藏檔案)
ls -l -h -a = ls -lha = ls -ahl
echo "123456" | passwd --stdin tom ##更改其他使用者密碼
shutdown -h now
shutdown -h +10
rm -rf * ##刪除全部檔案 rm:remove ,-r:recursive ,-f:force
echo 1 > /proc/sys/net/ipv4/ip_forward ##開熱點
echo 1 > /proc/sys/net/ipv4/ip_forward ##關熱點
```

linux破解

```
1.取得IP位址
	yum install nmap
進入單人模式
nmap,hydra
rockyou ## 密碼字典

靶機 2022/3/22
ip :192.168.60.3 ===>/root/flag.txt ?

加分
output.png ##找出圖片裡隱藏內容
a.zip ##解密
```

集縮比

```
```

PT test

```
滲透測試
```

堆疊(stacking)

```
```

```
"echo hi" > a.sh ##輸入echo hi 到a.sh
chmod +x a.sh ##change mod +x(可執行)
./a.sh ##執行結果 hi(加./增加安全性)
cat a.sh ##執行結果 echo hi
file a.sh ##可察看檔案屬性
file /usr/bin/data
usr ##放第三方可執行檔的地方
which ##可知道執行檔位置
echo "2" 1>a.txt == echo "2" >a.txt
ls /aaa ##會報錯
ls /aaa 2>error.txt ##把報錯寫入error.txt(2不能省略)
ls /tmp/aaa 1>a.txt 2>&1 ##1可省略
ls /tmp/aaa >/dev/null 2>&1 ##把內容丟掉
echo $? ##0執行成功 非0失敗
```

路徑

```
export PATH=$PATH:(路徑) ##更改路徑只在此視窗有用
gedit .bashrc ##永久更改路徑(不會在現在視窗立即生效)
source .bashrc (. .bashrc) ##使永久更改的路徑立即生效
```



df指令

```
df -h ##知道磁碟檔案大小
```

使用者

```
adduser tom ##新增使用者
echo "tom" | passwd --stiden tom ##修改使用者密碼
```

## 腳本

![image-20220503095003465](https://github.com/derek120432/linux/blob/main/linux%20picture/image-20220503095003465.png)

![image-20220503095130910]((https://github.com/derek120432/linux/blob/main/linux%20picture/image-20220503095130910.png)

------



#  檔案收尋



link:https://blog.gtwang.org/linux/unix-linux-find-command-examples/

``` 
find /homw=e -iname/gtwang.txt ##-iname 代表不分大小寫
{r--} 4 {-w-} 2  {--x} 1
suid(4) sgid(2) stickybit(1) ##-rwsr-xr-x(477)
find . -type f -perm 0777
find . -type f -name "*.txt" -exec rm -f {} \; ##一次刪除所有集合的檔案
touch {a..z}.txt ##創建a~z個.txt檔
mkdir a ##創建資料夾a
```

# find . ctime [] mtime [] ##是有修改

##　![image-20220524100746634](https://github.com/derek120432/linux/blob/main/linux%20picture/image-20220524100746634.png)

##　suid(4) sgid(2) stickybit(1) ##-rwsr-xr-x(477)

find . -type f -perm 0777

![image-20220503104824793](https://github.com/derek120432/linux/blob/main/linux%20picture/image-20220503104824793.png)

------



## find . -type f -name "*.txt" -exec rm -f {}

![image-20220503110119898](https://github.com/derek120432/linux/blob/main/linux%20picture/image-20220503110119898.png)

## 量檔案備份

![image-20220503114759656](https://github.com/derek120432/linux/blob/main/linux%20picture/image-20220503114759656.png)

![image-20220503114806929](https://github.com/derek120432/linux/blob/main/linux%20picture/image-20220503114806929.png)

```
cat /etc/resolv.conf ##可以修改ping(把resolv.conf當檔案)
cat < /etc/resolv.conf ##把resolv.conf當標準輸入
wc (word count)
cat <<EOF
grep name /etc/resolv.conf ##從resolv.conf中篩選name
cat /etc/resolv.conf | grep name ##從標準輸入讀
通配符(wildcard) *:是用來匹配檔案名稱的  正則表達室友來表達檔案內容的 (regular expression)
cat /etc/passwd | grep "h$" ##以h為結尾
cat /etc/hosts | grep -v "^$" ##可以去除空白行
```

## tac與cat差異

![image-20220510093146978](https://github.com/derek120432/linux/blob/main/linux%20picture/image-20220510093146978.png)

## cat <<EOF

![image-20220510093553789](https://github.com/derek120432/linux/blob/main/linux%20picture/image-20220510093553789.png)

## cat <<EOF < /tmp/a.txt

![image-20220510093820064](https://github.com/derek120432/linux/blob/main/linux%20picture/image-20220510093820064.png)

## cat <<< "hi" (hi is a string)讀取並顯示

![image-20220510093730119](https://github.com/derek120432/linux/blob/main/linux%20picture/image-20220510093730119.png)

## [grep](https://dotblogs.com.tw/xerion30476/2021/05/21/Linux)

![image-20220510094722078](https://github.com/derek120432/linux/blob/main/linux%20picture/image-20220510094722078.png)

## 通配符(wildcard) *:是用來匹配檔案名稱的  正則表達室友來表達檔案內容的 (regular expression)

![image-20220510095743192](https://github.com/derek120432/linux/blob/main/linux%20picture/image-20220510095743192.png)

## grep 在資料夾中收尋關鍵字

![image-20220510100446349](https://github.com/derek120432/linux/blob/main/linux%20picture/image-20220510100446349.png)

## 只收尋.conf檔

![image-20220510100459488](https://github.com/derek120432/linux/blob/main/linux%20picture/image-20220510100459488.png)

# **顯示前後幾行**

```
grep -A 1 127 /etc/hosts ##after
grep -B 1 127 /etc/hosts ##befor
grep -C 1 127 /etc/hosts ##前跟後
```

## cat /etc/hosts | grep -v "^$" 

![image-20220510102822675](https://github.com/derek120432/linux/blob/main/linux%20picture/image-20220510102822675.png)

***

## **正規表示法**

`grep` 在搜尋關鍵字時，其實是以正規表示法的方式匹配文字的，所以一般的正規表示法都可以直接使用，以下是一些常用的範例。開頭與結尾是最常用的：

```
# a 開頭
ls | grep "^a"
# b 結尾
ls | grep "b$"
# a 或 b 開頭
ls | grep "^[ab]"
# a 或 b 結尾
ls | grep "[ab]$"
```

各種出現次數的指定：

```
# r 開頭，接著 o 出現零次以上
cat /etc/passwd | grep "^ro*"
# r 開頭，接著 o 出現零次或一次
cat /etc/passwd | egrep "^ro?"
# r 開頭，接著 o 出現一次以上
cat /etc/passwd | egrep "^ro+"
```

多種字眼的組合，也很常用：

```
# 含有 ab 或 cd
cat /etc/passwd | egrep "root|user|tom"
# 含有 ab 或 cd（另一種寫法，作用相同）
cat /etc/passwd | grep -E "root|user|tom" ##使用擴充型的正則表達式(同egrep)
```



如果只想要精準篩選出 net 這個單字，可以這樣寫：

```
# net 這個單字
grep -w net
```

***



# cat /etc/passwd | grep "^r.*h$" 

r.* ##任意字串的匹配

# vim

命令模式

```
w: write  
q:quit   
wq:write and quit   
q!:quit and give up modified things
```

lsblk

![image-20220517092534822](https://github.com/derek120432/linux/blob/main/linux%20picture/image-20220517092534822.png)

lsblk -f

![image-20220517092801348](https://github.com/derek120432/linux/blob/main/linux%20picture/image-20220517092801348.png)

```
ext2 ext3 ext4 xfs (linux常用掛載檔案格式)
```

![image-20220517093216385](https://github.com/derek120432/linux/blob/main/linux%20picture/image-20220517093216385.png)

umount /media

```
卸載USB ##必須離開USB目錄
```

USB

```
vfat 不需要驅動程式
備份USB把檔案變成xfat
```

找尋在線的使用者

![image-20220524094430463](https://github.com/derek120432/linux/blob/main/linux%20picture/image-20220524094430463.png)

# FIND尋找檔案Grep可以找得更廣

## linux 開機執行的第一個程式

![image-20220531092329342](https://github.com/derek120432/linux/blob/main/linux%20picture/image-20220531092329342.png)

## 為什麼init會被systemb取代

![image-20220531092540293](https://github.com/derek120432/linux/blob/main/linux%20picture/image-20220531092540293.png)

```
free -m ##看memory使用情形
```

## 看到執行程式花的時間

![image-20220531105134097](https://github.com/derek120432/linux/blob/main/linux%20picture/image-20220531105134097.png)

ctrl+c

中斷程式執行

ctrl+z

丟到背景執行

![image-20220531113335539](https://github.com/derek120432/linux/blob/main/linux%20picture/image-20220531113335539.png)

## 符號

```
#	註解
;	不管前面的指令成功與否後面的指令都會繼續執行
&&	前面的指令如果失敗後面的就會拒絕執行
```

```
$$	
$?	可以看下的只領有沒有成功(有=0,沒有=非0值)
$#	輸入參數的個數
$_	$0可知道命令本身
$@	
!!	
```



![image-20220607092709651](https://github.com/derek120432/linux/blob/main/linux%20picture/image-20220607092709651.png)

![image-20220607095244944](https://github.com/derek120432/linux/blob/main/linux%20picture/image-20220607095244944.png)

***

![image-20220607093616265](https://github.com/derek120432/linux/blob/main/linux%20picture/image-20220607093616265.png)

![image-20220607093944420](https://github.com/derek120432/linux/blob/main/linux%20picture/image-20220607093944420.png)

***

# zombie process ; orphan process

zombie process

```
當child process執行完成後就會變成zombie process ,parents process 會將它回收
如果parents process 沒回收會一直存在
```

orphan process

```
當child process還在執行中parents process死掉就會變成orphan process
```

![image-20220607100437805](https://github.com/derek120432/linux/blob/main/linux%20picture/image-20220607100437805.png)

zombie

![image-20220607101515576](https://github.com/derek120432/linux/blob/main/linux%20picture/image-20220607101515576.png)

***

su 跟 su-差別

環境變量

![image-20220607110118672](https://github.com/derek120432/linux/blob/main/linux%20picture/image-20220607110118672.png)

