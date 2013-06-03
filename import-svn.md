# 导入SVN仓库中的项目
## 标准SVN项目结构：

```
    project
    |- trunk
    |- tags
    |- |- v1
    |- |- v2
    |- branches
    |- |- br1
    |- |- br2
```
```
    git svn clone $url_to_project_path -s --prefix=svn/ $local_project_path
```

## 非标准SVN项目结构:

```
    project
    |- trunk
    |- baseline
    |- branches
    |- |- br1
    |- |- br2
```

### step 1:

```
    git svn init $url_to_project_path -T baseline -b branches --prefix=svn/ $local_project_path
```
### step 2:

```
    vi $local_project_path/.git/config
```
将

```
    fetch = $project/baseline:refs/remotes/svn/trunk
```
修改为

```
    fetch = $project/baseline:refs/remotes/svn/baseline
```
并增加

```
    [svn-remote "release"]
        url = $svn_url_to_project_parent
        fetch = $project/trunk:refs/remotes/svn/trunk
```
### step 3:
获取代码

```
    cd $local_project_path
    //取branches所有分支和baseline
    git svn fetch
    // 取trunk（后续对trunk的提交: git svn dcommit release）
    git svn fetch release
```

## 非标准SVN项目结构:

```
    project
    |- doc
```
```
   git svn clone $url_to_doc_path --prefix=svn/ $local_doc_path
```
