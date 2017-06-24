---
title: hexo 搭建个人博客
date: 2017-06-24 07:23:56
tags: hexo
---

## 环境准备

- node.js 安装ok
- [blogname].github.io 博客库创建ok

## 安装 [Hexo](https://hexo.io/)

    npm install hexo-cli -g
    hexo init blog
    cd blog
    npm install

## hexo 常用操作

#### 生成
	hexo g
#### 本地 http://localhost:4000/ 查看站点
	hexo s
#### 部署
	hexo d
#### 合并以上两条命令，在部署前生成
	hexo d -g
## 将 Hexo 博客推送到 Github 仓库上

#### 安装推送扩展
	npm install hexo-deployer-git --save
#### 配置 _config.yuml 文件推送方式和地址

    deploy:
      type: git
      repo: git@github.com:kuangggg/kuanggg.github.io.git
      branch: master
## 文章创建
	hexo new post "article title"
在 source\ _posts 将会看到 article title.md 文件，对其进行修改编辑，然后生成发布即可。
## 安装next主题
#### 下载主题
	git clone https://github.com/iissnan/hexo-theme-next themes/next
#### 修改默认主题配置
	theme: next
#### 清楚原有主题缓存
	hexo clean
