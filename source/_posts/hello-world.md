---
title: 使用Ｈexo 撰寫部落格
tags:
  - hexo
  - blog
categories:
  - Web
  - blog
---
> 這篇是採用hexo安裝後，自動產生的說明內容，再加上依照自己喜愛的設定所編寫之文章＾＾
<!--more-->



## 安裝 Hexo
```
$ npm install -g hexo-cli
$ hexo init <folder>
$ cd <folder>
$ npm install
```


## Quick Start


Welcome to [Hexo](https://hexo.io/)! This is your very first post. Check [documentation](https://hexo.io/docs/) for more info. If you get any problems when using Hexo, you can find the answer in [troubleshooting](https://hexo.io/docs/troubleshooting.html) or you can ask me on [GitHub](https://github.com/hexojs/hexo/issues).


### 顯示版本資訊。
``` bash
$ hexo version
(node:5190) ExperimentalWarning: The fs.promises API is experimental
INFO  Validating config
hexo: 5.1.1
hexo-cli: 4.2.0
os: Darwin 19.0.0 darwin x64
http_parser: 2.8.0
node: 10.16.3
v8: 6.8.275.32-node.54
uv: 1.28.0
zlib: 1.2.11
brotli: 1.0.7
ares: 1.15.0
modules: 64
nghttp2: 1.39.2
napi: 4
openssl: 1.1.1c
icu: 64.2
unicode: 12.1
cldr: 35.1
tz: 2019a
```

### Create a new post

``` bash
$ hexo new "My New Post"
```

More info: [Writing](https://hexo.io/docs/writing.html)

### Run server

``` bash
$ hexo server
```

More info: [Server](https://hexo.io/docs/server.html)

### Generate static files

``` bash
$ hexo generate
$ hexo g
```

### Clean static files
清除快取檔案 (db.json) 和已產生的靜態檔案 (public)。
``` bash
$ hexo clean
```

More info: [Generating](https://hexo.io/docs/generating.html)

### Deploy to remote sites

``` bash
$ hexo deploy
```

More info: [Deployment](https://hexo.io/docs/one-command-deployment.html)

### 更換部落格主題
- Hexo 預設主題是landscape，可以修改網站設定_config.yml來更換．

- 這天換成theme：next，但是啟動hexo s後，開啟的網站卻是亂碼參數頁面＠＠
啟動畫面也出現以下訊息：
```bash
WARN  ========================= ATTENTION! ==========================
  ===============================================================
WARN   NexT repository is moving here: https://github.com/theme-next
  ===============================================================
WARN   It's rebase to v6.0.0 and future maintenance will resume there
 ===============================================================
```
因此直接參考官方更新步驟[从 NexT v5.1.x 更新](https://github.com/theme-next/hexo-theme-next/blob/master/docs/zh-CN/UPDATE-FROM-5.1.X.md "从 NexT v5.1.x 更新")

1. 克隆新的仓库到任一异于 next 的目录（如 next-reloaded）：
$ git clone https://github.com/theme-next/hexo-theme-next themes/next-reloaded
2. 在 Hexo 的主配置文件中设置主题：
theme: next-reloaded
3. 重新開啟就正常了

#### 更換NexT版面
/hexo-web/themes/next-reloaded/_config.yml
scheme: Pisces

#### 新增頁面
1. 新增頁面
hexo new page tags
hexo new page categories

2. 開啟頁面

menu:
  home: / || fa fa-home
  categories: /categories/ || fa fa-th
  archives: /archives/ || fa fa-archive
  tags: /tags/ || fa fa-tags
  about: /about/ || fa fa-user

3. 為文章加上Tag與categories
tags:
  - Testing
  - Another Tag

代表Web->blog
categories:
  - Web
  - blog

代表Diary->PlayStation
categories:
- [Diary, PlayStation] 
- [Diary, Games]
- [Life

4. 在標頭放上可愛的git連結（右上角）

github_banner:
  enable: true

5. 開啟作者照片
avatar：圖片網址

6. 放上社群連結
social

 

### 參考文章
[HEXO 指令](https://hexo.io/zh-tw/docs/commands.html)
[NextT開始使用](https://theme-next.iissnan.com/getting-started.html)
[NextT主题配置](https://theme-next.iissnan.com/theme-settings.html)