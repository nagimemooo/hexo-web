---
title: "[React] 練習 function component 改變 State 的用法 (useState Hook)"
date: 2020-06-22T16:36:43+08:00
draft: true
categories: ["前端"]
tags: ["react", "function component","useState"]
draft: false
---

> 本章練習使用function component更改state的用法。
<!--more-->


####  網路參考範例:
[React hook](https://zh-hant.reactjs.org/docs/hooks-intro.html) @React 中文解說Hook系列
[使用 State Hook](https://zh-hant.reactjs.org/docs/hooks-state.html "使用 State Hook") @React 中文解說State Hook中寫法對比

#### 使用 useState 更改 State:
- useState-是一個基礎的Hook，是可以在function component中使用設定state，而不需要轉換成class。
> hook意思是“鈎子”，在音樂上，指的是一首歌曲中最能鈎人的部分。Hook 是 React 16.8 增加的新功能。讓你不必寫 class 就能使用 state 以及其他 React 的功能。使用hook可以更簡化且被推崇使用。

- useState它回傳了一對值：目前的 state 跟一個可以更新 state 的 function。

範例改寫練習 [Refresh_Time_useState](https://codesandbox.io/s/refreshtimeusestate-xns3c?file=/src/index.js "Refresh_Time_useState")
```javascript
//1.加上useState引入
import React, { useState } from 'react';
import ReactDOM from "react-dom";

const Clock=()=>{
  // 2.宣告一個 state 變數，命名date。
  // 傳入 useState() 的參數就是 state 起始值
  const [date, changeTime] = useState(new Date());
// 3-1 return中直接寫上state變數-在 function 中可以直接使用 state
// 3-2 當使用者點擊，我們就呼叫 函式 並傳入新的值。
  return(
      <div>
        <h1>Hello, world!</h1>
        <h2>现在是 {date.toLocaleTimeString()}.</h2>
        <button onClick={()=>{changeTime(new Date())}}>刷新 </button>
      </div>
  );
}

const rootElement = document.getElementById("root");
ReactDOM.render(
  <React.StrictMode>
    <Clock/>
  </React.StrictMode>,
  rootElement
);

```