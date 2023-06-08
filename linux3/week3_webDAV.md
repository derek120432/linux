webDAV建立

# 網路磁碟機

```
httpd -M | grep DAV //檢查httpd有沒有支援DAV
```

# linux sed

linux 三劍客 awk/grep/[sed](https://shengyu7697.github.io/linux-sed/)

``` 
sed 's///g' setting.conf # s代表(substitute) 如果g在最後面代表取代全部沒g代表取代第一個
sed 's/Alan/tom' setting.conf #收尋Alan用tom取代,在這裡有沒有g沒差
								#first/後面打要收尋的東西second/打要取代
sed 's/Alan/tom' setting.conf #只改螢幕上的內容
sed -i 's/Alan/tom' setting.conf #連檔案內的一起更改
```

![image-20230222105945137](C:\Users\PAVI\AppData\Roaming\Typora\typora-user-images\image-20230222105945137.png)

```
sed 's/name:.*/name:Dunk/g' setting.conf
```

![image-20230222113312037](C:\Users\PAVI\AppData\Roaming\Typora\typora-user-images\image-20230222113312037.png)

![image-20230222115757836](C:\Users\PAVI\AppData\Roaming\Typora\typora-user-images\image-20230222115757836.png)

```
 sed 's/abc\ d/a\ bcd/' bb #因為空白為特殊符號所以前面需要加\
 sed 's#abc\ d#a\ bcd#' bb #意思同上
```

![image-20230222113859905](C:\Users\PAVI\AppData\Roaming\Typora\typora-user-images\image-20230222113859905.png)

``` 
echo "1234" | sed 's/.*/(&)/' => (1234)
echo "qwertyuiop" | sed 's/.*/#&/' => #qwertyuiop #可以註解檔案
```



***



```
cat <<EOF >setting.conf #可以把輸入的文字存進setting.conf輸入EOF結束
```

### 例1:

腳本

```
echo "generate a.conf"
cat <<EOF >a.conf
name: Alan
age: 18
EOF


```

![image-20230222103122758](C:\Users\PAVI\AppData\Roaming\Typora\typora-user-images\image-20230222103122758.png)

執行結果

![image-20230222102957970](C:\Users\PAVI\AppData\Roaming\Typora\typora-user-images\image-20230222102957970.png)

![image-20230222103410918](C:\Users\PAVI\AppData\Roaming\Typora\typora-user-images\image-20230222103410918.png)

### 例2

腳本:

```
read -p "What's your name?" name #讀""裡的內容並存到後面
read -p "What's your age?" age

cat <<EOF > temp.sh 			#如果沒有temp.sh會自己建立
echo "hi " $name
echo "your age is: " $age
EOF

/usr/bin/bash temp.sh

```



![image-20230222103952647](C:\Users\PAVI\AppData\Roaming\Typora\typora-user-images\image-20230222103952647.png)

執行結果

![image-20230222103857875](C:\Users\PAVI\AppData\Roaming\Typora\typora-user-images\image-20230222103857875.png)

read

```
read -p "Do you want to continue? (Y/y for Yes, any other key for No) " answer
    case $answer in
        [Yy]* ) echo "Program continues..."; break;; #[Yy]* 正則表達式 重複前面的字元0次、1次...到多次
        * ) echo "Program exits."; exit;; # "*"代表default
    esac
```



![image-20230222104550755](C:\Users\PAVI\AppData\Roaming\Typora\typora-user-images\image-20230222104550755.png)

### 正則表達

```
^$ #代表空白行
echo "123456" | grep ".*" #收尋全部
echo "123456" | grep "3.*" #3開始到結束
```

刪除空白行

![image-20230222112233449](C:\Users\PAVI\AppData\Roaming\Typora\typora-user-images\image-20230222112233449.png)