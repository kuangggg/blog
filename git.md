---
title: Git
date: 2017-06-24 14:04:44
categories: tool
tags: git
---

## 下载 git 客户端
[命令行参考](https://git-scm.com/docs)
## 创建SSH KEY
    ssh-keygen -t rsa -C "[your email]"
在 **C:\Users\Administrator\.ssh** 目录下生成id_rsa和id_rsa.pub两个文件    
    ssh -T git@github.com //校验秘钥
## github 上添加私钥
登陆GitHub，打开“Account settings”，“SSH Keys”页面,点“Add SSH Key”，填上任意Title，在Key文本框里粘贴id_rsa.pub文件的内容
## 全局配置账户信息
    git config --global user.name kuangggg
    git config --global user.email [your email]
## 初次体验
    git init //初始化一个本地仓库
    git add //从工作区加载到缓存库中
    git commit -m "提示信息"
    git remote add origin git@github.com:kuangggg/kuangggg.github.io.git //将本地这个库和 github 上的库关联
    git push -u origin master //推送到远程库主分支 第一次提交-u

## 提交修改
    git status  //查看状态
    git diff file.txt  //查看修改
    git add //提交修改
    git push origin master  //推送

## 分支相关
    git chechout -b dev  //创建dev分支，然后切换到dev分支
    git branch //查看当前分支
    git merge name //合并某分支到当前分支
    git branch -d name //删除分支
