---
title: "[✍修正中]vscode 插件分享"
tags:
  - vscode
categories:
  - Tech.
  - tool
date: 2020-09-18 18:37:37
---

{% cq %}

# 什麼是 vscode

{% endcq %}

 <blockquote class="blockquote-center">
 Visual Studio Code（簡稱vscode）是一個由微軟開發，同時支援Windows 、 Linux和macOS等操作系統的免費程式碼編輯器，它支援測試，並內建了Git 版本控制功能，同時也具有開發環境功能，例如代碼補全、代碼片段和代碼重構等。 維基百科</blockquote>

<!--more-->

# 安裝插件

## Go

- Go

## 代碼格式化

- prettier - code formatter
- ESLint

## Task Kill

這個很好用 cmd+shift+p 可以叫出對話 輸入要砍的網路 port，

## Code Snippet
這個是vscode內建就有的程式碼內建設定，

## 根據插件會有對應的設定

(快速鍵 Command+ ,) 開啟 settings.json 使用者設定檔
### files

```
 "files.autoSave": "onFocusChange", 當焦點移開自動儲存
  "files.associations": {
    "*.js": "javascriptreact" 新增檔案後綴連接的檔案類型 （React用）
  },
```

### editor

自動存檔格式化與更改預設格式化工具

```
"editor.tabCompletion": "on", 
//type a snippet prefix (trigger text), and press Tab to insert a snippet.
"editor.formatOnSave": true,
"editor.defaultFormatter": "esbenp.prettier-vscode"
```

### React JSX 自動格式化設定

搭配 editor 根據檔案格式做設定

```

  "[javascriptreact]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "eslint.codeAction.showDocumentation": {
    "enable": true
  },

```
### prettier
```
'prettier.singleQuote': true,
使用單引號，這個打開，格式化會幫你把""變成單引號
'prettier.semi': false,
結束是否加分號
```


{% note class_name %} # 網路參考文章 {% endnote %}

| 連結| 摘要|
| --- | --- |
| [偏好的 Visual Studio Code 設定檔](https://blog.poychang.net/my-vscode-config)  |非常詳細|
| [vscode 如何自動格式化代碼？](https://kknews.cc/zh-tw/code/2kj8z9y.html "vscode 如何自動格式化代碼？")           | 編輯器默認的格式化工具 |
| [How do I enable automatic prettier formatting for .jsx files in VS Code?](https://stackoverflow.com/questions/62380051/how-do-i-enable-automatic-prettier-formatting-for-jsx-files-in-vs-code "How do I enable automatic prettier formatting for .jsx files in VS Code?") | each file type has to be individually<br>Note javascriptreact as the identifier for JSX |
| |  |
