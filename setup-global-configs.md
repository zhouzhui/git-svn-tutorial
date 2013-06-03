# 初始化git全局配置
## 设置: 用户名&电邮地址（git本地提交显示的提交者，不影响svn的提交）

    git config --global user.name $your_name
    git config --global user.email $your_email
## 设置: 检出及提交时对换行符的处理
**Windows:**

    git config --global core.autocrlf true
**Mac&Ubuntu:**

    git config --global core.autocrlf input
## 设置: 全局的文件过滤列表（gitignore，类似svnignore）

    git config --global core.excludesfile $ignore_conf_file_path
## 设置: 将本地提交推送到远端SVN仓库时添加上svn:mergeinfo信息

    git config --global svn.pushmergeinfo true
## 设置: git pull时总是以rebase代替merge

    git config --global branch.autosetuprebase always
## 设置: git命令行输出时对终端着色

    git config --global color.ui true
## 设置: 查看当前分支所跟踪的远端分支

    git config --global alias.show-tracking '!sh -c "
    git for-each-ref --format=\"%(refname:short)\" refs/heads/* | while read branch; do if remote=\$(git config --get branch.\$branch.remote); then merge=\$(git config --get branch.\$branch.merge); echo \"\$branch tracks \$remote/\${merge##*/}\"; fi; done 
    " -'
## 设置: 查看所有跟踪的远端分支

    git config --global alias.show-all-trackings '!sh -c "
    git for-each-ref --format=\"%(refname:short)\" refs/heads/* | while read branch; do upstream=\$(git rev-parse --abbrev-ref \$branch@{upstream} 2>/dev/null); if [[ \$? == 0 ]]; then echo \"\$branch tracks \$upstream\"; else echo \"\$branch has no upstream configured\"; fi; done
    " -'
