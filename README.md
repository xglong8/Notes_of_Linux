# Linux 基础
  ## 一 关闭和重启系统
  * shutdown [optione] [time] [warning]
    + 立即关闭/重启系统 shutdown -h/r now
    + 定时关闭/重启系统 shutdown -h/r 18:35/+45
  * halt = shutdown -h
  * reboot = shutdown -r


  ## 二 Shell 基础
   ### 1. 获取帮助
   * man [option] [command]
   * whatis [command] = man -f [command]
   * [command] --help


   ### 2. 常用快捷键
   * 控制：ctrl+l, ctrl+c,ctrl+z..
   * 光标：ctrl+a, ctrl+e, ctrl+u, ctrl+k,ctrl+w,ctrl+y,Alt+f,Alt+b
   * Tab 命令补全


   ### 3. 常用操作命令
   * whoami  列出当前用户
   * which 查看命令：which ls
   * cd, mkdir, chmod
   * top,ps 查看进程，kill [PID]进程
   * alias/unalias 创建或查看/取消别名


   ### 4. 历史命令 ~/.bash_history
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


   ### 5. 特殊字符
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


  ## 三 vim基础
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
