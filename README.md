
`version: 2020.12.30`  
`author: xiaoying.zhang`  
### Commands
>   
> 
    git clone *  

    git remote -vv // 查看关联  
    git remote add origin git@**.git // 创建远程仓库关联  
    git remote remove origin // 删除远程关联  

    git add . // 增加所有文件  
    git ls-files // 查看add添加的文件  
    git rm --cached *fileneme // 删除add添加的文件  
    git rm -r --cached // 删除文件夹  
    git commit -m '*' // 添加描述  

    git checkout v1 // 切换到新分支  
    git checkout v0.10.1 // 切换到tag v0.10.1版本  
    git checkout -b v1 // 创建分支v1并切换到该分支  
    git checkout -b master --track origin/master // 创建本地分支master并与远程分支建立关联  
    git checkout -b gpu --track origin/gpu // 合并分支  

    git branch  
    git branch -vv //查看本地分支与远程分支关联  
    git branch -d * // 删除分支  
    git branch -m * // 重名该分支  
    git branch --set-upstream-to origin/*远程分支名 // 与远程分支创建关联  

    git push origin v1  
    git push --set-upstream origin v1 // 远程创建v1并push本地v1到远程v1  
    git push origin --delete v1 // 删除远程分支v1  
    git push --all // 上传所有  
    git push --tags // 上传所有tags  
    git push origin master --tags // 连同标签一起推送  

    git tag -l // 查看存在tags  
    git tag v0.1 // 创建tag  
    git tag -a v0.1 -m "add tag0.1"  
    git tag v0.1 *c809ddbf83939a89659e51dc2a5fe183af384233 // 在某个commit_id上打tag  
    git tag -d v0.1 // 删除本地tag同时git push origin:refs/tags/test_tag删除远程tag  

    git config --global core.editor vim // nano转vim  
    git config --global user.name "xiaoying.zhang"  
    git config --global user.email "xiaoying.zhang@**.com"  
    git config --local user.name "ZhangXiaoying0116"  
    git config --local user.email "zhangxiaoying0116@gmail.com"  

    git cherry-pick --abort // 当前分支恢复到cherry-pick前的状态  
    git diff **commit_id** // 查看当前commit版本和其他commit版本的区别  
    git submodule update --init --recursive // 拉取相关依赖  
    git fetch origin  
    git merge origin/next  
    git fetch --all // 下载远程仓库最新内容，不做合并  
    git reset --hard origin/master // 把HEAD指向master最新版本  
    git pull // 拉下最新分支  
    git pull origin master // 从远程获取代码并合并本地的版本, git fetch和git merge  
    
    git config --global core.editor vim // 将git commit的默认编辑器从nano转为vim  
### Requirements  
>   查看文件相关提交历史
> 
    git log --pretty=oneline **Convolution.cc** // 查看文件相关的log  
    git log *filename // 可以看到filename相关的commit记录  
    git log -p *filename // 可以显示每次提交的diff  
    git show *c5e69804bbd9725b5dece57f8cbece4a96b9f80b or *filename // 只看某次提交中的某个文件变化  
>   从一个git拷贝到另外git，all-branchs，all-tags，all-logs
> 
    step1.从原地址克隆一份裸版本库  
          git clone --bare http://github...**source.git  
    step2.进入克隆下来的目录  
          cd project.git  
    step3.以镜像推送的方式上传代码到新的仓库地址  
          git push --mirror http://github...**target.git  
>   上传一个新的git目录至关联的git
> 
    git init  
    git config --local user.name "ZhangXiaoying0116"  
    git config --local user.email "zhangxiaoying0116@gmail.com"  
    git remote remove origin  
    git remote add origin https://github.com/ZhangXiaoying0116/**.git  
    git add .  
    git commit -m ""  
    git push --set-upstream origin "branch-name"  
### Questions  
>   Q1
> 
    error: refname refs/heads/HEAD not found  
    fatal: Branch rename failed  
    // 处于独立状态，必须签出一个新分支以将其与当前提交关联  
>   Q2
> 
    若存在git文件夹打不开，后面跟着@***；git中嵌套了之前的git，删除之前的.git/  
