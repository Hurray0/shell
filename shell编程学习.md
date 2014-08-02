#shell编程学习
##0.执行shell
>chmod +x 【文件名】
>./【文件名】

##1.对文件、文件夹的操作
###新建
>touch 文件名	
\#新建文件，不打开

>vi [文件名] 
\#新建并用vim打开

>cat > 文件名 
\#新建,回车后开始输入内容，按快捷键退出

>echo "内容">文件名 
\#新建，可有空行

>-
>mkdir 文件夹名 
\#新建文件夹




###移动/重命名
>mv 移动前名称 移动后名称 
\#对于文件夹来说，如果后者存在则放其子目录，否则新建（重命名）

###删除
>rm 文件1 [文件2] [文件3]

>rm -ir 目录 
\#删除目录下所有文件，每个文件都提示= =

>rm -r 目录
\#这个删除目录所有内容，不会提示

###复制
>cp [选项] 源文件或目录 目标文件或目录 

>cp -f 源文件或目录 目标文件或目录 
\#相当于剪切

##2.快速cd目录
>(cd的基本用法已经会了)

>pwd \#查看当前路径

>export CDPATH=**** \#增加查找目录
>>例如export CDPATH=~/desktop/code，然后直接就可以cd shell了
>>>上一步至少当前使用固定，退出再开就不行了。为了使该基础目录永久改变, 增加代码行 export CDPATH=***到你的 ~/.bash_profile文件即可.

##3.top/ps命令
>直接输入top，快速查看进程动态

>直接输入ps，简要信息，很多进程被隐藏

##4.alias命令
>对于bash，alias命令可以将软件加入快捷命令
如：

>alia mysql=/usr/local/mysql/bin/mysql

>加入~/.bash_profile文件即可常用 #太好了！

##5.find
find是最常见和最强大的查找命令，你可以用它找到任何你想找的文件。
find的使用格式如下：
$ find <指定目录> <指定条件> <指定动作>
- <指定目录>： 所要搜索的目录及其所有子目录。默认为当前目录。
- <指定条件>： 所要搜索的文件的特征。
- <指定动作>： 对搜索结果进行特定的处理。

如果什么参数也不加，find默认搜索当前目录及其子目录，并且不过滤任何结果（也就是返回所有文件），将它们全都显示在屏幕上。
find的使用实例：
$ find . -name ‘my*’
搜索当前目录（含子目录，以下同）中，所有文件名以my开头的文件。
$ find . -name ‘my*’ -ls
搜索当前目录中，所有文件名以my开头的文件，并显示它们的详细信息。
$ find . -type f -mmin -10
搜索当前目录中，所有过去10分钟中更新过的普通文件。如果不加-type f参数，则搜索普通文件+特殊文件+目录。

##6.curl
>curl -d "SQL=show tables;&type=2&code=123456" http://hurraydb.sinaapp.com/db/demo.php

##7.ssh
>ssh root@107.191.118.218

##8.php脚本
>php -r "echo md5('123');"

##9.不小心删了或改错~/.bash_profile
>export PATH=/usr/bin:/bin:/usr/sbin:/sbin:/usr/local/bin:/usr/X11/bin

>再sudo vim ~/.bash_profile就好了

##10.修改时区
>cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime

>date

##11.重启
>reboot

##12.查看端口
>netstat -an | grep 5858

##13.写ios到U盘
>diskutil list ＃显示当前所有得磁盘情况

>diskutil unmountDisk /dev/disk1 ＃卸载U盘上的所有磁盘

>dd if={ISO_IMAGE_HERE_} of=/dev/disk1 bs=1m #拷贝磁盘

##14.参数
>echo "Program name is $0" //程序的完整路径和名字

>echo "There are totally $# parameters passed to this program"; //参数的总数

>echo "The last is $?";  //程序执行效果

>echo "The parameter are $*";  //返回由参数组成的字符串

>echo "The first parameter are $1" //返回第一个参数

##15.gzip压缩
>gzip 文件; 

##16.svn使用

###同步代码
>svn checkout https://svn.sinaapp.com/hurray0

###上传代码
>svn checkout https://svn.sinaapp.com/hurray0

>cd newapp/1

>cp -rf /path/to/wordpress/* ./

>svn add ./

>svn commit -m"add wordpress"

###修改代码

>svn checkout https://svn.sinaapp.com/hurray0 #如果已经checkout过了，不需要重新checkout。

>cd newapp/1

>vim index.php #这里编辑代码

>svn commit -m "edit index.php"

##17.chmod设置文件权限

>chmod ［who］ ［+ | - | =］ ［mode］ 文件名

>u 表示“用户（user）”，即文件或目录的所有者。

>g 表示“同组（group）用户”，即与文件属主有相同组ID的所有用户。

>o 表示“其他（others）用户”。

>a 表示“所有（all）用户”。它是系统默认值。

>例如chmod a+rwx README.md
