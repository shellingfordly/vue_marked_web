# git操作

---

## 1.1 $ git init
在项目中安装git

## 2.1 $ git add index.html
提交index.html文件

## 2.2 $ git add .
提交所有文件夹内的所有文件

## 3.1 配置
- \$ git config --global user.email "you@example.com"
- $ git config --global user.name "yourname"

## 3.2 $ git commit -m "新增了一个XXX文件"
提交放在分支中

## 4.1 $ git remote add origin xxx
推送到远程仓库之前，先关联本地和远程仓库，xxx建议使用ssh路径，http路径需要登录

## 4.2 $ git push origin master
推送到远程仓库---> yes，需要权限--->获取权限

## 4.3 $ ssh-keygen -t rsa -C "you@example.com"
一路回车获取密钥

## 5.1 打开id_rsa.pub
回到github--->setting--->SSH--->new SSH key--->将id_rsa.pub里的密钥复制到key中

## 5.2 \$ git pull origin master
- 当github中的仓库中被操作过时，先\$ git pull将仓库中的所有分子拉取下来
- $ git pull origin master将master分子pull下来
- 此操作的目的是为了将被修改过的远程仓库pull拉取到本地仓库来，让本地仓库完全等于远程仓库
- pull拉取时出现一个奇怪的界面时操作i--esc--:wq退出

## 5.3 pull结束后再push到github上去

## 6.1 $ git clone ssh路径
将整各仓库的项目克隆下来

## 7.1 master是主分支
当一个项目在开发时，放在分支中

## 7.2 $ git branch xxx
创建xxx分支

## 7.3 $ git branch
查看分支

## 7.4 $ git checkout xxx
切换到xxx分支

## 7.5 $ git merge xxx
将xxx分支整合到master分支上

## 7.6 $ git branch -d xxx
删除xxx分支

## 8.1 $ git log
可以看到提交的commit信息

## 8.2 $ git reset --hard "commitID"
回退到commit的某一个版本


---

