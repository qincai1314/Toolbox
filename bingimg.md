工具准备
------------------------
 

wget（点击下载）

批处理命令（点击下载）

网友提供的接口：http://area.sinaapp.com/bingImg?daysAgo=1（1代表天数）

 
实现步骤
-------------------
 

1、打开记事本，并将下面代码复制粘贴进去,新建-另存为，文件类型选择"所有文件"，文件名为：下载Bing背景图片.bat（点击下载），保存在桌面。

@echo off
set var=%cd%
md BingImg&cd BingImg
for /l %%i in (0,1,30) do %var%\wget http://area.sinaapp.com/bingImg?daysAgo=%%i

 

2、将下载好的文件解压到和Bing背景图片.bat同一级目录下（这里都放在桌面）。

 

3、双击Bing背景图片.bat。

 

4、下载完后，窗口会自动退出，此时桌面会多出一个BingImg的文件夹。

 

5、下载结果（历史图片23张）。

 
代码详解
---------------------
 

@echo off
set var=%cd%
md BingImg&cd BingImg
for /l %%i in (0,1,30) do %var%\wget http://area.sinaapp.com/bingImg?daysAgo=%%i

 

@echo off　　　　　　　　　　　　从本行开始关闭回显。

set var=%cd%　　　　　　　　 set var：声明一个变量var。%cd%：表示当前文件所在目录绝对地址，意思是将地址传递给var。

md BingImg&cd BingImg 　　　　创建（md）BingImg文件夹，并且(&)进入(cd)BingImg文件夹

for /l %%i in (0,1,30) do %var%\wget http://area.sinaapp.com/bingImg?daysAgo=%%i

 

    for　　批处理循环指令。
    /l　　for的参数，处理数字序列。（注：L为小写，虽然是废话，但还是提醒一下，避免看成“1”或者“|”了）。
    %%i　　传递参数的变量。
    in　　照写，他的后面是循环参数。
    (0,1,30) 　　循环参数，里面的参数依次代表从零开始，自增量为1，超过30循环结束。
    do　　照写，反正后面是需要执行的指令。
    %var%\       wget程序所在目录的绝对地址，也就是%cd%传递给var的值。（注：“\”不能少。啰嗦一下，例如：c:\Users\Youge\desktop\wget.exe,"\"就是wget.exe后的“\",如果去了的话就会变成c:\Users\Youge\desktopwget.exe，此时这个路径就无效了，抱歉啰嗦了）
    wget http://area.sinaapp.com/bingImg?daysAgo=%%i　　wget的下载指令，后面的是url，其中这里”%%i“为天数。

 

对于for指令不懂的可以在cmd中输入：for/?（这里又学到一招了：对于dos里不懂得指令，我们可以在指令后加上"/?",这样就可以查找出指令相关的帮助的信息）

 