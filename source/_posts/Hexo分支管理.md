---
title: Hexo 分支管理
categories:
- Hexo
tags:
- Hexo
---
>*master branch*: run ```hexo g -d``` and generate/update blog page.

>*hexo branch*: backup hexo source code

# Initial Setup
* Create folder on local:
```bash
mkdir blog; cd blog
```
* Setup hexo:
```bash
npm install hexo
hexo init
```
```bash
npm  install hexo-deployer-git  --save
```
* Download theme:
```bash
cd theme
```
```bash
git clone https://github.com/theme-next/hexo-theme-next.git next
```
* Modify ```_config.yml```
```
# URL
url: http://https://yusjyu.github.io/
root: /

# Deployment
deploy:
    type: git
    repository: https://github.com/yusjyu/yusjyu.github.io.git
    branch: master
```
* Setup git
```bash
git init
```
```bash
git add .
```
```bash
git commit
```
```bash
git remote add origin git@github.com:yusjyu/yusjyu.github.io.git
```
```bash
git pull --rebase origin master
```
* Set up ```hexo``` branch and push code
```bash
git branch hexo
```
```bash
git checkout hexo
```
```bash
git push origin hexo
```



# Update Blog
* Push change to hexo branch:
```bash
git add .
```
```bash
git commit –m ""
```
```bash
git push origin master:hexo
```
* Deploy page
```bash
hexo g -d
```

