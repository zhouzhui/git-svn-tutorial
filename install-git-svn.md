## 安装git-svn
* **Mac:**
  1. 安装 [Command Line Tools for XCode](https://developer.apple.com/downloads/index.action)  (请选择匹配Mac版本的Command Line Tools for XCode)
  2. 安装 `Homebrew`:

          ruby -e "$(curl -fsSL https://raw.github.com/mxcl/homebrew/go)"  
  3. 初始化 `Homebrew`:

          brew doctor  
          brew update  
  4. 安装 `git` & `svn`:

          brew install git subversion  
  5. 若使用过程中出现`Can't locate SVN/Core.pm in @INC`的错误提示，添加以下软链接(perl的版本根据自己实际情况替换)：

          sudo ln -s  /Library/Developer/CommandLineTools/Library/Perl/5.16/darwin-thread-multi-2level/SVN /System/Library/Perl/Extras/5.16/SVN
          sudo ln -s /Library/Developer/CommandLineTools/Library/Perl/5.16/darwin-thread-multi-2level/auto/SVN/ /System/Library/Perl/Extras/5.16/auto/SVN

* **Ubuntu:**
  1. 安装 `git` & `svn` & `git-svn`:

           sudo add-apt-repository ppa:git-core/ppa  
           sudo apt-get update  
           sudo apt-get install git subversion git-svn  
  **注1:** 若无法安装 `git-svn`, 可在 `http://www.ubuntuupdates.org/pm/git-svn` 根据安装的 `Ubuntu` 版本及 `git` 版本选择相应的安装包下载安装  
  **注2:** 强烈建议安装git 1.8以上版本，git 1.7版本需要另外编译安装 [git-credential-helper](https://github.com/pah/git-credential-helper)  

* **Windows:**
  1. 安装 [msysgit](https://msysgit.googlecode.com/files/Git-1.8.1.2-preview20130201.exe)  

## 设置SVN认证信息
若 `${user.home}` 目录下不存在 `.subversion` 目录

* **Mac & Ubuntu:**
  * 通过 `svn co` 命令检出 svn repo 中的一个项目，用以生成 `.subversion` 目录。检出后可删除`$local_project_path` 目录

          svn co $a_svn_repo_url $local_project_path --username $your_username  

* **Windows:**
  1. 通过 `svn co` 命令检出 svn repo 中的一个项目，用以生成 `Subversion` 目录。检出后可删除`$local_project_path` 目录

          svn co $a_svn_repo_url $local_project_path --username $your_username  
  2. 将 `${user.home}/AppData/Roaming/Subversion` 目录下的所有内容复制到 `${username.home}/.subversion` 目录
  3. 修改 `${username.home}/.subversion/auth/svn.simple/$file` ($file的文件名根据svn server的不同而不同), 将第三行的 `V 8` 改为 `V 6`, 第四行的 `wincrypt` 改为 `simple`, 第7行的 `V $old_length` 改为 `V $new_length` (`$new_length` 指密码长度), 第八行改为 `$password` (`$password` 指明文密码). 这一步的修改是因为`git-credential-helper` 似乎不支持Windows的密码管理器 `wincred`(很有可能是我的使用方式不对，如有正确使用方式求patch)
