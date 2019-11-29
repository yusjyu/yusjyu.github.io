---
title: Hexo 分支管理
categories:
- Hexo
tags:
- Hexo
---
>*master branch*: 存储 ```hexo g -d``` 生成的代码

>*hexo branch*: 存储hexo源代码

# Initial Setup
* Create folder on local:
```bash
mkdir blog; cd blog
```
* Setup hexo:
```bash
npm install hexo
npm  install hexo-deployer-git  --save
hexo init
```
* Use git submodule to download theme:
 * Fork theme: https://github.com/theme-next/hexo-theme-next
 * Add theme as submodule:
```bash
cd blog/
git submodule add git@github.com:yusjyu/hexo-theme-next.git themes/next/
git add .
git commit -m 'Add theme next as a submodule'
```
 * Add upstream:
```bash
cd themes/next/
git remote add upsteam https://github.com/theme-next/hexo-theme-next
```
 * Check remote repo:
 ```
$ git remote -v
origin	git@github.com:yusjyu/hexo-theme-next.git (fetch)
origin	git@github.com:yusjyu/hexo-theme-next.git (push)
upsteam	https://github.com/theme-next/hexo-theme-next (fetch)
upsteam	https://github.com/theme-next/hexo-theme-next (push)
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
* Deploy to Github
 * Setup git
```bash
git init
git add .
git commit -m ""
git remote add origin git@github.com:yusjyu/yusjyu.github.io.git
```
 * Set up ```hexo``` branch and push code
```bash
git branch hexo
git checkout hexo
git push origin master:hexo
```

# Update Blog
* Push change to hexo branch:
```bash
git add .
git commit –m ""
git push origin master:hexo
```
* Deploy page to master branch:
```bash
hexo g -d
```

# Update Theme
```bash
cd themes/next

# 如果要合入上游的更新
git fetch upstream
git checkout master
git merge upstream/master # 需要手动合并冲突

git add .
git commit -m ""
git push origin master
```

# 用其他设备
* Clone hexo source code
```
git clone -b hexo git@github.com:yusjyu/yusjyu.github.io.git
```
* Clone theme source code
```
cd themes
git clone git@github.com:yusjyu/hexo-theme-next.git
mv hexo-theme-next next
```
* Install hexo
```
npm install hexo    // No need for 'hexo init'
npm  install hexo-deployer-git  --save
```



