# 設定使用者容量

```
進入單人模式
vi /etc/fstab
	編輯/home那邊新增usrquota,grpquto
cat /etc/mtab | grep usrquota #查是否有更改到
xfs _quota -xc 'report -h' /home #soft 超過會警告 hard最多只能使用到這容量 數值為0代表沒有限制
xfs_quota -xc "free -h" /home
xfs_quota -xc "quota -h user" /home # 看單獨使用者
xfs_quota -xc "limit bsoft=10m bhard=12m user" /home #設定使用者的soft和hard
dd #可以用來產生特定大小的指令
dd if=/dev/zero of=test bs=1M count=13 # 會產生很多0存在test一次1M會產生13次共13M

```

![](C:\Users\PAVI\AppData\Roaming\Typora\typora-user-images\image-20220926134204651.png)

![image-20220926135908366](C:\Users\PAVI\AppData\Roaming\Typora\typora-user-images\image-20220926135908366.png)

![image-20220926135914308](C:\Users\PAVI\AppData\Roaming\Typora\typora-user-images\image-20220926135914308.png)

![image-20220926135919973](C:\Users\PAVI\AppData\Roaming\Typora\typora-user-images\image-20220926135919973.png)

![image-20220926135928339](C:\Users\PAVI\AppData\Roaming\Typora\typora-user-images\image-20220926135928339.png)

![image-20220926135944361](C:\Users\PAVI\AppData\Roaming\Typora\typora-user-images\image-20220926135944361.png)

![image-20220926135949921](C:\Users\PAVI\AppData\Roaming\Typora\typora-user-images\image-20220926135949921.png)

![image-20220926140002521](C:\Users\PAVI\AppData\Roaming\Typora\typora-user-images\image-20220926140002521.png)