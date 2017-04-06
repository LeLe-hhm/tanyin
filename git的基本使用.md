    首先git是一款分布式的代码管理工具  

一些基本的指令：
    #配置信息：1>git config --global user.name "hhm"
              2>git config --global user.email "hhm_1021@163.com"
              3>检测是否设置了：git config --list
    
    1#初始化一个仓库：git init   (其实就是创建了一个.git的隐藏文件)
            查看文件 git ls -a

    2#将代码提交到仓库的两个步骤：
            1>git add 文件名  （暂存区）
            2>git commit -m "对提交的代码的一个说明"  （仓库）
    3#查看当前代码的状态：git status