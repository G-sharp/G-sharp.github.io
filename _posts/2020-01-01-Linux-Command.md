---
layout: post
title: Linux Command
date: 2019-07-19 16:40:12
tags: Linux
---

# System
 
 |      Name       |       Usage        |     Remark   |url|
 |:-:|:-:|:-:|:-:|
 |Find File        |          find . -name "*.c"          |      find C format file at current workpath        |  [Linux 命令大全-find](https://www.runoob.com/linux/linux-comm-find.html) |
 
# Network
 |      Name       |       Usage        |     Remark   |url|
 |:-:|:-:|:-:|:-:|
 |search port|lsof -i:[port]|find Prot used infomation|--| 
 |expose port|iptables -A OUTPUT -p tcp --sport 22 -j ACCEPT ,service iptables save|开放22端口| |

# ZSH
  1. install zsh
  
  2. install oh-my-zsh

     > wget https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh -O - | sh  
   
  3. 配置文件  
      > vim ~/.zshrc
      ZHS_THEME="ys"
      

# VIM

## VIM的三种模式
   - 普通模式 (复制粘贴)
   - 编辑模式 (文本输入)
   - 命令模式 (监听命令)  

## 进入编辑模式   
    i    //insert即插入模式，从光标所在位置开始插入，即插入的内容位于原光标所在位置字符之前
    I    //从光标所在行的行首开始插入
    a    //append即附加模式，从光标所在位置之后附加，即新增内容位于原光标所在位置字符之后
    A    //从光标所在行的行末开始附加
    o    //在光标所在行的下一行加入新一行
    O    //在光标所在行的上一行加入新一行
    R    //进入替换模式，屏幕下方会出现Replace提示，此时的输入会直接替换光标所在位置的字符，与Windows下的 0 作用类似，同样通过ESC键返回

## 光标移动

```
    　　k          //  h -光标左移
 　　h     l　　　　//  l -光标右移
    　　j 　　　　　//  j -光标下移(形似向下的箭头)
                  //  k -光标上移

    w             //移动至下一个单词的第一个字符(即前一个字符为空白字符)
    e             //移动至单词的最后一个字符(即后一个字符为空白字符)
    $             //移动至行尾
    0             //移动至行首

    3j            //下移三格
    4h            //左移4格
    2w            //移动至第二个单词的词首字符
    3e            //移动至第三个单词的词尾字符

    Ctrl+f    　　//屏幕向下移动一页，相当于PageDown
    Ctrl+b   　　 //屏幕向上移动一页，相当于PageUp
    H　　　　　　   //移动至屏幕中第一行的第一个字符
    M　　　　　　　 //移动至屏幕中中间行的第一个字符
    L             //移动至屏幕中最低行的第一个字符 
    
    ngg nG :n    //跳转到n行 Ctrl+g显示当前行
    gg           //跳到开头
    G            //跳转到结尾
```

## 删除操作
```
    x          //删除光标所在处的字符(其大写形式X为将光标之前的字符删除，相当于Backspace)
    dd       　//删除光标所在行的操作(常用)
    dw         //删除一个单词
    d3w      　//删除三个单词
    d$         //删除光标所在处至行尾的字符
    d4l        //删除光标所在处起的四个字符
    d2j        //删除两行
```

## 复制粘贴
```
    p                    //put命令，将剪贴的内容(注意，既可以是复制的内容，也可以为之前删除的内容)放置在光标后的位置，其大小字母P则表示放置在光标之前的位置
    v                    //进入虚拟选择模式(visual selection)，被选择的文本段被高亮显示(v的选择对象为字符，对应的大写字母V则是以行为单位选择)
　　Ctrl + v　　　　　　　 //以矩形框的形式进行内容选择
    y                    //复制通过 v 操作选择的文本，或则其本身也可以与光标移动指令一同使用
                         //如y5w，则复制5个单词(注意复制是从光标所在处开始的)
    yy    //复制光标所在行的内容
    y0    //复制光标所在位置至行首的内容
    y$    //复制光标所在位置至行尾的内容
    yG    //复制光标所在位置至文本结束的内容
    ynG   //复制指令与nG指令的结合
　　　　　　//以及诸如y3w、y3j等指令
```

## 撤销操作
```
    u            //撤销上一次操作
    U            //撤销对光标所在行的所有操作
    Ctrl+r    　 //重做上一操作
```

## 替换和修改

> 文本的替换和修改主要使用替换r(replace)和修改c(change)指令完成。

    rc            //其中c为字符，则将光标所在处的字符替换为c

> 修改指令将指定的范围内的内容删除，并进入编辑模式，从而使得用户可以修改某一部分的文本。指令c与光标移动指令结合使用。用户修改完毕后，需使用ESC返回普通模式。

    ce        //删除光标所在处至词尾的所有内容，并进入编辑模式，供用户修改
    c3w     　//删除光标所在处其的三个词，并进入编辑模式
    c$        //删除光标所在处至行尾的所有字符，并进入编辑模式
    c0        //删除光标所在处至行首的所有字符，并进入编辑模式

## 修改编辑选项
```
    :set nu        　//显示行号，相应的set nonu则为不显示行号
    :set ic        　//搜索忽略大小写(ignore case),取消即为 set noic
    :set hlsearch    //搜索时匹配的结果高亮显示
    :set incserch    //设置搜索时的搜索顺序
                    //可以看到，在对应的选项前面加入前缀no即表示取消取消对应的选项
    :set ruler　　　　//右下角展示状态栏
    :set             //显示与系统默认设置不同的参数情况，即被修改过的参数情况
    :set syntax on　 //设置Vim会根据语法以不同颜色显示不同的内容
    :set syntax off
```

# PIP 
  ```
  pip install -i https:..pypi.tuna.tsinghua.edu.cn pip -U
  pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple
  ```
# PYTHON3
  
# COMPRESS FILE

> ## tar   
>>   -c: 建立压缩档案  
>>   -x：解压  
>>   -t：查看内容  
>>   -r：向压缩归档文件末尾追加文件  
>>   -u：更新原压缩包中的文件  
>>这五个是独立的命令，压缩解压都要用到其中一个，可以和别的命令连用但只能用其中一个。下面的参数是根据需要在压缩或解压档案时可选的。  
>> -z：有gzip属性的
>> -j：有bz2属性的  
>> -Z：有compress属性的  
>> -v：显示所有过程  
>> -O：将文件解开到标准输出  
>> 下面的参数-f是必须的  
>> **-f: 使用档案名字，切记，这个参数是最后一个参数，后面只能接档案名。**

### tar -cf all.tar *.jpg
这条命令是将所有.jpg的文件打成一个名为all.tar的包。-c是表示产生新的包，-f指定包的文件名。

### tar -rf all.tar *.gif
这条命令是将所有.gif的文件增加到all.tar的包里面去。-r是表示增加文件的意思。

### tar -uf all.tar logo.gif
这条命令是更新原来tar包all.tar中logo.gif文件，-u是表示更新文件的意思。

### tar -tf all.tar
这条命令是列出all.tar包中所有文件，-t是列出文件的意思

### tar -xf all.tar
这条命令是解出all.tar包中所有文件，-t是解开的意思

## 压缩

- tar -cvf jpg.tar *.jpg //将目录里所有jpg文件打包成jpg.tar 
- tar -czf jpg.tar.gz *.jpg   //将目录里所有jpg文件打包成jpg.tar后，并且将其用gzip压缩，生成一个gzi
- 压缩过的包，命名为jpg.tar.gz
-  tar -cjf jpg.tar.bz2 *.jpg //将目录里所有jpg文件打包成jpg.tar后，并且将其用bzip2压缩，生成一
- bzip2压缩过的包，命名为jpg.tar.bz2
- tar -cZf jpg.tar.Z *.jpg   //将目录里所有jpg文件打包成jpg.tar后，并且将其用compress压缩，生成一
- umcompress压缩过的包，命名为jpg.tar.Z
- rar a jpg.rar *.jpg //rar格式的压缩，需要先下载rar for linux
- zip jpg.zip *.jpg //zip格式的压缩，需要先下载zip for linux

## 解压

- tar -xvf file.tar //解压 tar包
- tar -xzvf file.tar.gz //解压tar.gz
- tar -xjvf file.tar.bz2   //解压 tar.bz2
- tar -xZvf file.tar.Z   //解压tar.Z
- unrar e file.rar //解压rar
- unzip file.zip //解压zip

## 总结

1. *.tar 用 tar -xvf 解压. 
2. *.gz 用 gzip -d或者gunzip 解压. 
3. *.tar.gz和*.tgz 用 tar -xzf 解压. 
4. *.bz2 用 bzip2 -d或者用bunzip2 解压. 
5. *.tar.bz2用tar -xjf 解压. 
6. *.Z 用 uncompress 解压. 
7. *.tar.Z 用tar -xZf 解压. 
8. *.rar 用 unrar e解压. 
9. *.zip 用 unzip 解压


