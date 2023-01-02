# linux services

### stand alone

​	1.隨時存在 processs alaways run in the background

​	2.較吃資源

### inet像代理者

​	1.有客戶時會喚起伺服器

​	2.反應時間較慢

***

## init & systemD

linux開機時的第一支程式

init較舊版本的systemd新版

d是daemon:application runing in the background

![image-20221121140120922](C:\Users\PAVI\AppData\Roaming\Typora\typora-user-images\image-20221121140120922.png)

### init

​	1.開機時伺服器一個一個啟動

​	2.開機時間較慢

### systemd

​	1.可以同時啟動

​	2.開機時間較快

```
守護進程(大陸用語)
戶號
httpd:80 將會被http取代:443
named:53
telnetd:23
ssh:22

```

![image-20221121140906398](C:\Users\PAVI\AppData\Roaming\Typora\typora-user-images\image-20221121140906398.png)

***

## man

man後面可以加不同的數字

```
man 8 sshd
```

![image-20221121141959102](C:\Users\PAVI\AppData\Roaming\Typora\typora-user-images\image-20221121141959102.png)

***

## init的七個階段

​	1.單人模式

​	3.文字模式

​	5.圖形模式

***

# [Telnet sever(期末之一)](https://blog.csdn.net/l_liangkk/article/details/105401435)