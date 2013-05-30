# 初始化git全局配置
## 设置: 用户名&电邮地址（git本地提交显示的提交者，不影响svn的提交）

    git config --global user.name $your_name
    git config --global user.email $your_email
## 设置: 全局的文件过滤列表（gitignore，类似svnignore）

    git config --global core.excludesfile $ignore_conf_file_path
## 设置: 将本地提交推送到远端SVN仓库时添加上svn:mergeinfo信息

    git config --global svn.pushmergeinfo true
