一、远程登陆
  远程登录客户端有 SecureCRT, Putty, SSH Secure Shell
  可以通过 ifconfig 来查看服务器IP

  Linux主机配置
  1）创建目录 /root/.ssh 并设置权限
    [root@localhost ~]# mkdir /root/.ssh 
    mkdir 命令用来创建目录
  2）创建文件 / root/.ssh/authorized_keys
    [root@localhost ~]# vim /root/.ssh/authorized_keys
    vim 命令是编辑一个文本文件的命令
  3）打开刚才生成的public key 文件 （生成的密钥文件）
    复制该文件中 AAAA开头至 "---- END SSH2 PUBLIC KEY ----" 上的所有内容
    粘贴到/root/.ssh/authorized_keys 文件中，要保证所有字符在一行
  4）再设置putty选项，点窗口左侧的SSh –> Auth ，单击窗口右侧的Browse…
    选择刚刚生成的私钥， 再点Open ，此时输入root，就不用输入密码就能登录了。


二、Linux文件基本属性
  1)修改 文件 或 目录 的所属 用户 与 权限 ：
    chown (change owner) ： 修改所属用户与组。
    chmod (change mode) ： 修改用户的权限。

  2)显示文件的属性以及文件所属的用户和组：
    ll 或者 ls -l 
    例如：
    [root@www /]# ls -l
    total 64
    dr-xr-xr-x   2 root root 4096 Dec 14  2012 bin
    dr-xr-xr-x   4 root root 4096 Apr 19  2012 boot
    ……
    实例中，bin 文件的第一个属性用 d 表示。d 在 Linux 中代表该文件是一个目录文件。
    在 Linux 中第一个字符代表这个文件是目录、文件或链接文件等等。
    当为 d 则是目录
    当为 - 则是文件；
    若是 l 则表示为链接文档(link file)；
    若是 b 则表示为装置文件里面的可供储存的接口设备(可随机存取装置)；
    若是 c 则表示为装置文件里面的串行端口设备，例如键盘、鼠标(一次性读取装置)。
    接下来的字符中，以三个为一组，且均为 rwx 的三个参数的组合。
    其中， r 代表可读(read)、 w 代表可写(write)、 x 代表可执行(execute)。
    要注意的是，这三个权限的位置不会改变，如果没有权限，就会出现减号 - 而已。

  3)更改文件属性
    1、chgrp：更改文件属组
      语法：
      chgrp [-R] 属组名 文件名
      参数选项:
      -R：递归更改文件属组，就是在更改某个目录文件的属组时，
      如果加上 -R 的参数，那么该目录下的所有文件的属组都会更改。

    2、chown：更改文件所有者（owner），也可以同时更改文件所属组。
      语法：
      chown [-R] 所有者 文件名
      chown [-R] 所有者:属组名 文件名
      
    3、chmod：更改文件9个属性
      Linux文件属性有两种设置方法，一种是数字，一种是符号。
      Linux 文件的基本权限就有九个，
      分别是 owner/group/others(拥有者/组/其他) 三种身份各有自己的 read/write/execute 权限。



