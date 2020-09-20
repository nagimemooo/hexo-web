---
title: "[✍練習]在 React 中套用 css-in-js (Emotion 庫)撰寫 CSS"
tags:
  - test
categories:
  - Tech.
  - Web
  - front-end
  - react
date: 2020-09-18 21:21:19
---

> 練習React JS寫法與 css-in-js( Emotion 庫) 撰寫 CSS

<!--more-->

# 一般要在 React 中撰寫 CSS 有幾種做法

- 可定義 className，另外將.CSS 檔案往外拉,再 import 套用。
```
import "./styles.css";
<div className="App">   
```

- 直接用 Inline-style 在屬性中加入style
```
<h2 style ={{color:'red', backgroundColor: "#3f51b5"}}>JS寫法</h2>
裡面是 JS 寫法，值需加''，且-需改成駱駝式寫法(不能含-字元)
```

- 套用css-in-js 庫 直接撰寫 CSS，不用再改 JS 寫法啦
```
/** @jsx jsx */ import { css, jsx } from "@emotion/core"; 
//不知道為什麼一定要加前述/** @jsx jsx */ 才有效果喔！！！ 之前漏了查好久＠＠

定義常數， CSS 區塊要用css`` 包起來
  const TextRed = css`
    color: red;
  `;

然後在要套用的地方加上css={xxx}
  <h2 css={TextRed}>emotion css 寫法</h2>

其他進階套用法持續更新在範例檔案中 ex: 多重套用，階層樣式，標籤樣式...
```
  而 css-in-js 庫的主要有: styled-components, emotion, glamorous。
  - Emotion 是一個旨在使用 JavaScript 編寫 CSS 樣式的庫 - 加上兩個反引號，之間就可以直接撰寫 CSS ，有styled 寫法，本篇主要用這個練習看看。 
  - styled 寫法
    要建立 < div> 標籤樣式時，使用 styled.div；如果要建立的是 < button> 則是使用 styled.button 以此類推。

------
## 練習一下（[✍修正中]

> 可側邊開啟程式碼 ⛅ 🌤 如有更好的寫法介紹還請多多指教，謝謝🙏． 

<iframe src="https://codesandbox.io/embed/emotion-css-nqey4?fontsize=14&theme=dark"
     style="width:100%; height:500px; border:0; border-radius: 4px; overflow:hidden;"
     title="emotion CSS"
     allow="accelerometer; ambient-light-sensor; camera; encrypted-media; geolocation; gyroscope; hid; microphone; midi; payment; usb; vr; xr-spatial-tracking"
     sandbox="allow-forms allow-modals allow-popups allow-presentation allow-same-origin allow-scripts"
   ></iframe>



----

{% note class_name %} # 網路參考文章 {% endnote %}

| 連結  | 摘要與大致內容 |
| ----- | ----------|
| [【Day 10】CSS && Inline-style](https://ithelp.ithome.com.tw/articles/10215415 "【Day 10】CSS && Inline-style")  | React CSS && Inline-style 介紹，JS 物件寫法。 |
|[https://github.com/rtsao/csjs/wiki/How-to-apply-multiple-classnames-to-an-element](https://github.com/rtsao/csjs/wiki/How-to-apply-multiple-classnames-to-an-element)|多重classnames寫法|
| [谈一谈在 React 项目中使用 css-in-js 方案](https://juejin.im/post/6844903993047531533 "谈一谈在React项目中使用css-in-js方案") | 鉴于 emotion 已经支持了 styled 模式，可以优先选择 emotion。內涵 emotion 用法示例(進階 待看 ☐👈) |
| [[Day 14 - 即時天氣] 把 CSS 寫在 JavaScript 中！？ - CSS in JS 的使用](https://ithelp.ithome.com.tw/articles/10223071 "[Day 14 - 即時天氣] 把 CSS 寫在 JavaScript 中！？ - CSS in JS 的使用") | 使用 emotion 撰寫 styled components  |
| [emotion Introduction](https://emotion.sh/docs/introduction "emotion Introduction") | install & CSS ``sample | [介紹撰寫 React CSS 的神套件 Styled Components](https://medium.com/@shihKai/%E4%BB%8B%E7%B4%B9%E6%92%B0%E5%AF%ABreact-css%E7%9A%84%E7%A5%9E%E5%A5%97%E4%BB%B6styled-components-77455c849198 "介紹撰寫React CSS的神套件Styled Components") | Styled Components sample |
｜[emotion Composition](https://emotion.sh/docs/composition)|套用兩個樣式寫法  |
