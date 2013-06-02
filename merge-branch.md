# 分支合并

    git merge --no-ff $branch_to_merged
# 冲突解决

    git mergetool // 可通过增加参数 -t $your_merge_tool 选定自定义的合并工具
# 中止合并，恢复原状

    git merge --abort
