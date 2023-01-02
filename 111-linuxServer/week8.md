# cut

```
cut -d ',' -f 1,3 doc4 | sort -g k 2 -t ","

echo "12345678" | cut -c 2-5
```

### 檔案合併

```
cat 1.txt 2.txt 3.txt > 4.txt
```

### 檔案分割

```
dd if=/dev/zero of=3M count=3 bs=1M
split -b 1m 3M
```

# shall scrip

```
alias
\ls #不使用alias的原形
alias myls='ls -l -h --color'=auto #自訂alias
unalias myls #取消自訂alias
vim .bashrc #讓每個視窗都生效
	alias myls='ls -l -h --color'=auto #加在.bashrc
sourcr .bashrc (. .bashrc) #讓他生效
```

```
echo
echo "hi a=$a" #hi a=5
echo 'hi a=$a' #hi a=$a
echo "hi a=${a}a" #hi a=5a
echo -e "hello\tworld" #hellow	world
echo $USER #知道user
echo $HOME #知道家目錄
echo $PWD #知道現在路徑
echo $IFS #預設的分割符號
echo $UID #=0代表是超級使用者
```

![image-20221024151248989](C:\Users\PAVI\AppData\Roaming\Typora\typora-user-images\image-20221024151248989.png)

$UID==0 -> $UID -eq 0

```
env
!! #執行最後一個命令
echo $RANDOM | md5sum | cut -c 1-5 #產生固定大小的五位亂數
[ -d test ] && echo "1" || echo "0" #如果-d後面的檔案是資料夾則回傳 1 不是則回傳0
```

![image-20221024160355123](C:\Users\PAVI\AppData\Roaming\Typora\typora-user-images\image-20221024160355123.png)

![image-20221024160423843](C:\Users\PAVI\AppData\Roaming\Typora\typora-user-images\image-20221024160423843.png)



![image-20221024160630750](C:\Users\PAVI\AppData\Roaming\Typora\typora-user-images\image-20221024160630750.png)

第一行是錯的需加上雙引號

### 字串比較

![image-20221024161016945](C:\Users\PAVI\AppData\Roaming\Typora\typora-user-images\image-20221024161016945.png)

### 數字運算

![image-20221024161826206](C:\Users\PAVI\AppData\Roaming\Typora\typora-user-images\image-20221024161826206.png)

兩個一樣

![image-20221024162051371](C:\Users\PAVI\AppData\Roaming\Typora\typora-user-images\image-20221024162051371.png)

乘除

![image-20221024162131839](C:\Users\PAVI\AppData\Roaming\Typora\typora-user-images\image-20221024162131839.png)