---
title: heroku-deploy
tags:
  - heroku
categories:
  - Tech.
  - Web
  - deploy
date: 2020-09-18 10:46:22
---


 <blockquote class="blockquote-center">
Heroku是一個支援多種程式語言的雲平台即服務，免費版提供每個月平台550-1,000小時時間，但每 30 分鐘未使用都會休眠一次，需等待他從休眠時間中甦醒，時間大約 30 秒左右．</blockquote>



<!--more-->


## 註冊heroku
  - 先上官網註冊一個帳號


## 安裝heroku CLI
參考：https://devcenter.heroku.com/articles/heroku-cli#download-and-install

- 安裝
```
  ➜  testmemooo git:(master) heroku version        
 ›   Warning: heroku update available from 7.40.0 to 7.43.0.
heroku/7.40.0 darwin-x64 node-v12.16.2
➜  testmemooo git:(master) npm install -g heroku
/usr/local/bin/heroku -> /usr/local/lib/node_modules/heroku/bin/run
+ heroku@7.43.0
added 788 packages from 316 contributors in 54.332s
➜  testmemooo git:(master) heroku version       
heroku/7.43.0 darwin-x64 node-v10.16.3
  ```

- 登入
heroku login

### 部署React
#### 方式一：兩分鐘0配置快速部署
- 官方已先配置好並照說明指令輸入即可 
[Deploying React with Zero Configuration](https://blog.heroku.com/deploying-react-with-zero-configuration)
```
npm install -g create-react-app
create-react-app '自命名專案'
cd '自命名專案'
git init
heroku create -b https://github.com/mars/create-react-app-buildpack.git
git add .
git commit -m "react-create-app on Heroku"
git push heroku master
heroku open
```
其中中間那一句heroku create 會在剛剛的網站上新增一個damp-stream-02723專案（命名應該是隨機的）
最後一句是開啟網站：
https://damp-stream-02723.herokuapp.com/
這樣就看到網站了，但不知道為什麼不能用原本的命名．

登入該網站後直接在專案上改名字
之後要回到專案上改git 上傳的位置
[update git remote](https://devcenter.heroku.com/articles/renaming-apps#updating-git-remotes)
```
➜  demomemooo git:(master) git remote rm heroku
使用指令刪除舊有的 remote
➜  demomemooo git:(master) heroku git:remote -a demomemooo
 ›   Error: Couldn't find that app.
 ›
 ›   Error ID: not_found  
 利用heroku指令綁定，這邊會失敗是因為當時還沒有在網站上更名
➜  demomemooo git:(master) heroku git:remote -a demomemooo
set git remote heroku to https://git.heroku.com/demomemooo.git
```

https://demomemooo.herokuapp.com/



#### 方法二 自行建立設定
 - 先建立React 命名testdemooo
 ```
 create-react-app testdemooo
 ```
  - 進入後 按New->Create New App 輸入命名新增一個專案
  (ex testdemooo)

- 產生完會有部署指令，照做即可

```
新的 Git repository 需做

$ cd my-project/
$ git init
$ heroku git:remote -a testmemooo


針對已存在Git repository，簡單新增“ heroku remote

$ heroku git:remote -a testmemooo
```

- 但這樣做打開網站會錯誤，以下面文章的最佳解答照做即可
[React專案佈署heroku問題](
https://ithelp.ithome.com.tw/questions/10198600)
大致上做法是自行建立server.js與產生build，只需要推build檔案上去即可（記得gitignor要拿掉build folder）