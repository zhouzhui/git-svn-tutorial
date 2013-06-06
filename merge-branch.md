# **熊出没: 本章所有内容仅适用于合并未推送到远端SVN仓库的提交，否则请自行找个角落抱头痛哭**
# **PS: 推荐使用 `分支衍合` 代替 `分支合并`**
# 分支合并

    git merge $branch_to_merged    
# 冲突解决

    git mergetool // 可通过增加参数 -t $your_merge_tool 选定自定义的合并工具
# 中止合并，恢复原状

    git merge --abort
# 分支衍合

    git rebase $branch_base_on
# 中止衍合，恢复原状

    git rebase --abort
# 冲突已解决，继续衍合

    git rebase --continue