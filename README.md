# Linux 基础
参考：
* 《Linux 实用教程 第三版》 於岳
* 《鸟哥的Linux私房菜 基础学习篇》 鸟哥，王世江


## 一 Shell 基础
### 1. 获取帮助
 * man [option] [command]
 * whatis [command] = man -f [command]
 * [command] --help


### 2. 关闭和重启系统
 * shutdown [optione] [time] [warning]
   + 立即关闭/重启系统 shutdown -h/r now
   + 定时关闭/重启系统 shutdown -h/r 18:35/+45
 * halt = shutdown -h
 * reboot = shutdown -r


### 3. 常用快捷键
 * 控制：ctrl+l, ctrl+c,ctrl+z..
 * 光标：ctrl+a, ctrl+e, ctrl+u, ctrl+k,ctrl+w,ctrl+y,Alt+f,Alt+b
 * Tab 命令补全


### 4. 常用操作命令
 * whoami  列出当前用户
 * which 查看命令：which ls
 * cd, mkdir, chmod
 * top,ps 查看进程，kill [PID]进程
 * alias/unalias 创建或查看/取消别名


### 5. 历史命令 ~/.bash_history
 * 运行历史命令
   + history [option]
   + history n 显示最近n个命令
   + history -c 清空历史记录
   + ！！运行上一个命令
   + ！6 运行第6个命令，！-6运行带倒数第6个命令
   + ！?gfd? 运行上一个包含gfd字符的命令
   + ！ls 运行上一个以ls开头的命令
   + ！ls:s/GF/D 运行上一个ls命令，并把期中的GF替换为D
   + ！$ 前一个命令的参数
 * 搜索历史命令
   + 上下箭头或ctrl+p/n
   + ctrl+r 向上搜索历史列表


### 6. 特殊字符
 * \` 命令替换，反引号内的命令先执行，并把结果传到引号外
 * \# 注释
 * & 后台进程
 * \\ 命令换行符
 * cat < temp 把键盘输入的内容写入temp文件，按ctrl+d结束
 * command  2> file 把运行命令时的错误信息写入或追加(2>>)到文件
 * command &> file  把运行命令时的输出信息及错误信息一起写入文件
 * $(command) 或 'command' 把命令运行结果作为一个新的参数或命令
 * ;(命令分隔符)，同时执行多个任务,command 1 ; command 2; ……
 * &&严格按先后顺序执行多个命令 command 1 && command 2 && ……
 * 其他：~, |, > ,>> , /, ?, \*, [a-z], [!0-9]


## 二 vim基础
### 命令模式
 * 光标移动
  + k上j下h左l右，nk上翻n行
  + H,M,L光标移动到屏幕顶端,中间，底端
  + ctrl+b/+f/+u/+d,往后/前翻一页/半页
  + 0/$光标移动到行首/尾
  + gg/G光标移动到文件首/尾
 * 删除
  + x/X删除光标所在位置/前的字符
  + nx/nX往后/前山删n个字符
  + dd删除当前行，ndd删除n行
  + dw/ndw删除一个/n个单词
  + d$删到行尾，d^删到行首
  + dgg,dG删到文件头/尾
 * 复制粘贴
  + yw, nyw复制到光标所在位置单词尾或到第n个单词尾
  + yy,nyy复制当前行或n行
  + y^,y$复制到行首/尾
  + p粘贴已复制的内容到当前位置
 * 撤销和重复
  + u撤消上一个操作，U撤消所有操作
  + .再次执行一次上一个操作
 * 查找匹配 /往后查找，?往前查找
 * 合并行 J,nJ合并当前行与下一行，或下n行
 * 保存和退出 ZZ保存退出，ZQ不保存操作退出


### 插入模式
 * 进入插入模式
  + i,a从光标所在位置前/后开始插入
  + I,A从光标所在行首/尾插入
  + o,O从光标所在下/上一新开一行插入


### 末行模式
1. 运行shell命令
 * : ! command
 * :r! command 把命令的输出从光标所在行开始插入
 * : n1, n2 w ! command 把n1行到n2行的内容作为命令的输入
 * :n 跳到第n行
2. 查找替换
 * :/str/ :?str? 向后或向前查找
 * :s/str1/str2/ 把光标所在行的下一个str1换成str2
 * :s/str1/str2/ 把光标所在行所有str1换成str2
 * :n1,n2 s/str1/str2/g 把n1行和n2之间的所有str1换成str2
 * :.$s/str1/str2/g 把当前位置到文件尾所有srt1替换掉
 * :%s/str1/str2/g 把文件当中所有str1替换掉
3. 删除
 * :n1,n2 d 从n1行删除到n2行
 * :.,$ d 从当前位置删除到文件尾
 * :/str1/, /str2/ d 从str1位置删除到str2位置
4. 复制和移动
 * :n1,n2 co n3 把n1到n2行复制后放到n3行之后
 * n1,n2 m n3 把n1到n2行内容移动到n3行之后
5. 设置vim
 * :set number显示箱行号
 * :set nonumber取消显示行号
 * :set readonly设置文件为只读状态避免错误改动
6. 保存和退出
 * :w [filename] 保存当前文件或另存为新文件
 * :q :wq (file name) : wq! (filename)
 * n1,n2 w filename 把n1行到n2行的内容保存到新文件
 * :1,. w filename :.,$ w filename
 * : r/e filename 打开/新建另一个文件
 * :/str/ w filename 把包含str的行写入文件
 * :/str1/,/str2/ w filename 把str1到str2之间的内容写到文件



## 三 目录和文件管理
### 1. Linux文件类型
* 普通文件 用ls -lh 查看，属性第一个符号为"-",如'-xrwxrwxrw'
* 目录文件 属性第一个符号为'd'，表示directory
* 设备文件
 + 属性第一个符号为'b',表示block块设备文件，如磁盘
 + 属性第一个符号为'c',表示char字符设备文件，如打印机
* 管道文件
* 链接文件 属性第一个符号为'l'
 + 软链接
   - 类似windows快捷方式，修改链接文件会直接改变源文件
   - 删除链接文件，源文件不变
   - 删除源文件，链接文件同时被删除
 + 硬链接
   - 删除源文件，硬链接文件不删除
   - 其他与软链接相同


### 2. Linux 目录结构
* / 根目录
* /home 用户主目录
* /root root用户主目录
* /bin 包含用户常用命令文件
* /sbin 包含系统管理员和root用户常用命令文件
* /dev 包含大部分设备文件，如磁盘，光驱等
* /lib 包含系统共享文件和内核模块文件，/lib/modules存放核心可加载模块
* /lib64 包含64位版本的共享和内核模块文件
* /tmp 包含临时文件
* /media 系统自动挂载设备的挂载目录
* /mnt 手动挂载设备时的挂载目录
* /boot 包含系统内核文件和引导装载程序文件，如Grub
* /opt 第三方应用程序安装地址
* /var 存放不经常变化的数据，如系统日志，DNS数据库文件
* /etc 系统配置文件，建议修改之前先备份
* /usr 包含可以供所有用户使用的数据和程序
* /srv 存储服务启动后所需取用的资料目录
* /run 临时文件系统，一些程序或服务启动后，pid会被放置在该目录中
* /sys 包含所有检测到的硬件设置，它们会被转换成/dev目录中的设备文件
* /proc 虚拟文件系统，由内核在内存中产生，不存在磁盘当中，用来提供系统相关信息，如：
  + /proc/cpuinfo 计算机CPU信息
  + /proc/filesystems Linux文件系统信息
  + /proc/ioports 计算机I/O端口信息
  + /proc/version Linux 系统版本信息
  + /proc/meminfo 计算机内存信息


### 3. 文件和目录操作
* 3.1 pwd 显示当前目录
* 3.2 cd 更改当前目录
* 3.3 ls 列出目录和文件信息
 ls -lth README.md 命令显示的详细信息如下：
 -rw-r--r--  1 usr  staff   7.2K 10 13 12:56 README.md

 第1列 | 第2列 | 第3列 | 第4列 | 第5列 | 第6-8列 |第9列
 :-:|:-:|:-:|:-:|:-:|:-:|:-:
 第1个字符表示文件类型，2-4、5-7、8-10三段字符分别表示用户所有者、群组和其他用户对此文件的权限，r-读，w-写，x-执行 | 文件的链接数 | 文件的用户所有者 | 文件的群组所有者 | 文件长度，即文件大小 | 文件的更改时间(mtime),或最后访问时间(atime) | 文件名称

 + -h 以方便读的形式显示文件大小，如用b,kb,M,G等
 + -a 显示隐藏文件,-A显示隐藏文件，但是不显示.和..
 + -c 配合-lt,显示ctime（创建时间）并根据ctime排序
 + -d 对目录文件，只显示文件夹不显示其下文件和子目录
 + -F 对目录文件，显示其下子文件和目录
 + -i 在输出的第一列显示文件inode号
 + -l 用长格式显示文件详细信息
 + -r 逆序排列
 + -t 根据修改时间排序
 + -s 在第一列以块数形式显示每个文件分配的尺寸
 + -S 根据文件大小排序


* 3.4 touch [option] [file]
  创建空文件或改变文件的访问时间(atime)和修改时间(mtime)
 + -a 只更改访问时间(atime)
 + -m 更改修改时间(mtime)
 + -c 修改时间时，如果文件不存在，不建立新的文件
 + -r\<file> 使用指定文件的时间属性而非当前时间
 + -d\<char> 使用指定字符串表示的时间而非当前时间
 + -t\<[[CC]YY]MMDDhhmm[.ss]> 使用指定格式的时间而非当前时间，如touch -c -t 09011830 file1


* 3.5 mkdir [option] [dir] 创建目录
 + -m 对新建立的目录设置权限，默认为755
 + -v 对创建的目录显示详细信息
 + -p 可以输入一个路径，若路径中某些目录不存在则自动创建那些目录，即一次创建多个目录


* 3.6 rmdir [option] [dir] 删除目录
 + -p 递归删除目录，当子目录被删除后，若父目录为空也一并删除
 + -v 输出处理的目录详情


* 3.7 cp [option] [original file\|dir] [target file\|dir] 复制文件和目录
 + -a 复制目录时保留链接和文件属性，并递归地复制目录
 + -d 保留链接
 + -f 覆盖目标文件之前不提示用户确认
 + -i 与-f相反，提示用户确认
 + -p 保留源文件修改时间和访问权限
 + -l 不复制，创建链接文件
 + -r 递归复制目录下的所有文件和子目录


* 3.8 mv [option] [original file\|dir] [target file\|dir] 移动文件、目录或给文件、目录改名
 + -i 覆盖前询问
 + -f 覆盖前不询问
 + -n 不覆盖已存在的文件
 + -u 只有在源文件比目标文件新，或者目标文件不存在时才移动
 + -T 将目标文件当作普通文件处理


* 3.9 rm [option] [file\|dir]
 + -f 强制删除
 + -r 递归删除
 + -i 删除前提示确认


* 3.10 wc [option] [file] 统计文件行数，单词数，字节数为字符数
 + -l 行数
 + -w 单词数
 + -c 字节数
 + -m 字符数
 + -L 统计文件中最长行的长度
