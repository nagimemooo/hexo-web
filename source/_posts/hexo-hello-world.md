---
title: 使用Ｈexo 撰寫部落格
tags:
  - hexo
  - blog
categories:
  - Web
  - blog
---
{% cq %} 
## 前文 ：hexo是什麼？
 {% endcq %}
 <blockquote class="blockquote-center">
 
：Hexo 是一個快速、簡單且強大的網誌框架。Hexo 使用 Markdown 標記語言）解析您的文章，並在幾秒鐘內，透過漂亮的主題產生靜態檔案。（來自 https://hexo.io/zh-tw/docs/）</blockquote>



### 本文將會知道：
  1. 如何使用 Hexo 產生部落格
  2. 如何使用 markdown 撰寫文章
  3. 如何部署到 Git 個人網頁
  4. 如何更改主題與內文風格 

<!--more-->



{% note class_name %} ## 安裝hexo與初始化 {% endnote %}


### 產生基本部落格結構

```
安裝工具
$ npm install -g hexo-cli
初始資料夾
$ hexo init <folder>
進入資料夾及安裝相依
$ cd <folder>
$ npm install
這邊就已經做好初始化了
```
###  啟動部落格 Run server

``` bash
$ hexo server
開啟瀏覽器 http://localhost:4000 就可以看到部落格了
```
More info: [Server](https://hexo.io/docs/server.html)

### 顯示版本資訊 
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


{% note class_name %} ## 開始撰寫文章 {% endnote %}

### 新增文章 Create a new post 

``` bash
$ hexo new "My New Post"
會在source/posts 底下新增一個 .md 檔案
採用 markdown語法開始撰寫文章
```
More info: [Writing](https://hexo.io/docs/writing.html)







## 部署網站



### 建立與設定 Git 空間

- 先在git上新增一個專案叫做[yourname].github.io
- 配置 _config.yml
```
deploy:
  type: git
  repo: https://github.com/yourname/yourname.github.io
  branch: master
```

### 產生靜態文件 Generate static files

``` bash
$ hexo generate 或是hexo g
會在public資料夾產生網站靜態檔案
這是用來部署到網站的檔案
```
More info: [Generating](https://hexo.io/docs/generating.html)

### 一鍵部署

``` bash
$ hexo deploy
```

其他空間(ex:heroku) More info: [Deployment](https://hexo.io/docs/one-command-deployment.html)

### 個人網站網址

https://yourname.github.io/


### 清理靜態文件 Clean static files

``` bash
$ hexo clean
清除快取檔案 (db.json) 和已產生的靜態檔案 (public)
```



## 更換部落格主題
- Hexo 預設主題是landscape，可以修改主網站設定_config.yml來更換．

- 這天換成 theme：next，但是啟動hexo s後，開啟的網站卻是亂碼參數頁面＠＠
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

1. Clone 新的倉庫（如 next-reloaded）：
$ git clone https://github.com/theme-next/hexo-theme-next themes/next-reloaded
2. 在 Hexo 的主配置文件中设置主题：
theme: next-reloaded
3. 重新開啟就正常了

### 更換主題設定檔
主題設定位置：/hexo-web/themes/next-reloaded/_config.yml

### 更換NexT版面
```

scheme: Pisces
```

### 新增文章標籤與分類
1. 新增頁面
```
hexo new page tags
hexo new page categories
```

2. 開啟頁面
```
_config.yml
menu:
  home: / || fa fa-home
  categories: /categories/ || fa fa-th
  archives: /archives/ || fa fa-archive
  tags: /tags/ || fa fa-tags
  about: /about/ || fa fa-user
```
3. 為文章加上Tag與categories
```
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
```

### 文章中顯示引言
```
有分號的上下引言，兩種皆可
<!-- 标签 方式，要求版本在0.4.5或以上 -->
{% centerquote %}blah blah blah{% endcenterquote %}
<!-- 标签别名 -->
{% cq %} blah blah blah {% endcq %}

單純的置中引言
<!-- HTML方式: 直接在 Markdown 文件中编写 HTML 来调用 -->
<!-- 其中 class="blockquote-center" 是必须的 -->
<blockquote class="blockquote-center">blah blah blah</blockquote>

顯示效果在本文開頭喔

```

### 文章開頭標記
```
{% note class_name %} Content (md partial supported) {% endnote %}
其中class_name可不設或是改成下方關鍵字
```
{% note class_name %} Content (不設定) {% endnote %}

{% note default %} default {% endnote %}

{% note primary %} primary {% endnote %}

{% note success %} success {% endnote %}

{% note info %} info {% endnote %}

{% note warning %} warning {% endnote %}

{% note danger %} danger {% endnote %}

### 在標頭放上可愛的git連結
```
_config.yml
github_banner:
  enable: true
（本部落格右上角範例）
```

### 顯示部落格作者照片
```
_config.yml
avatar：圖片網址
```

### 放上個人社群連結
```
social
可自由新增
```

------------

{% note class_name %} ## 參考文章 {% endnote %}

- Quick Start
Welcome to [Hexo](https://hexo.io/)!  Check [documentation](https://hexo.io/docs/) for more info. If you get any problems when using Hexo, you can find the answer in [troubleshooting](https://hexo.io/docs/troubleshooting.html) or you can ask me on [GitHub](https://github.com/hexojs/hexo/issues)

- [HEXO 指令](https://hexo.io/zh-tw/docs/commands.html)
- [NextT開始使用](https://theme-next.iissnan.com/getting-started.html)
- [NextT 主题配置](https://theme-next.iissnan.com/theme-settings.html)
- [NextT 內置標籤](https://theme-next.iissnan.com/tag-plugins.html)

