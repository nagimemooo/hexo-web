---
title: fn-km
tags:
  - test
categories:
  - Tech.
  - Web
  - front-end
  - km
date: 2020-09-21 22:04:23
---

 <blockquote class="blockquote-center">
 紀錄前端名詞解釋與文章整理</blockquote>


<!--more-->

## 異步相關

先讀讀網路的神人文章 （連結如失效請見諒）：
|  來源 |  摘要 |
| ------------ | ------------ |
| [Callback(回調)](https://eyesofkids.gitbooks.io/javascript-start-from-es6/content/part4/callback.html "Callback(回調)")  | Callback＆回調地獄(Callback Hell)，回調地獄可以用例如Promise、generator、async/await之類的語法結構，或是Async、co外部函式庫等，來改善或重構原本的程式碼結構  |
| [你懂 JavaScript 嗎？#23 Callback](https://cythilya.github.io/2018/10/30/callback/ "你懂 JavaScript 嗎？#23 Callback") | Callback＆回調地獄(Callback Hell) |
| [異步程式設計與事件迴圈](https://eyesofkids.gitbooks.io/javascript-start-from-es6/content/part4/eventloop.html "異步程式設計與事件迴圈")   |理解JavaScript是如何執行程式，同步(Synchronous, sync)與異步(Asynchronous, async)程式執行的差異 ，有程式的執行模擬網站  |
| [【翻译】如何在React中使用async/await (componentDidMount Async)](https://juejin.im/post/5b52a840f265da0fb0186cab "【翻译】如何在React中使用async/await (componentDidMount Async)") | 如何在React中使用async/await |
| [async/await的學習及在react-native中的使用](https://www.itread01.com/content/1549748733.html "async/await的學習及在react-native中的使用") | async/await的學習及在react-native中的使用 |
| [Day 14 - 二周目 - 從Promise 昇華到 async/await](https://ithelp.ithome.com.tw/articles/10201420 "Day 14 - 二周目 - 從Promise 昇華到 async/await") | 非同步 callback 的產生的 callback hell 圖很可愛ＸＤＤＤ |



筆記：
- Callback：
把某個函式當作另一函式的傳入參數
  - JS使用大量的 Callback，只有單執行緒，在瀏覽器端只有一個使用者，但事件或網路要求(AJAX)要求不能阻塞其他程式的進行
  - JS有分為同步及異步callback，setTimeout是一種異步函數。
  - 所有的同步回調函式都執行完成了，才會開始依順序執行異步的回調函式。
> 異步程式執行的作法，是使用異步callback(回調)函式的語法，讓會造成阻塞的程式組成一個異步回調函式，先丟往一個任務佇列(task queue)先丟，在之後的某個時間再回傳它的值與狀態回來。這些函式裡的程式碼多半都是與外部資源存取的I/O有關。

- Promise
在多層callback裡迷失，error handle難處理，耦合性高。
改用Promise，使得callback hell的多層縮排變成一層縮排.then.then.then..
error變的更好處理了，任何then錯誤會進到最後面那個.catch
- await 只是JS中Promise的语法糖











apisauce, Axios + 標準化錯誤+ 請求/響應轉換

---


debounce如果為這些短時間內觸發非常多次的事件處理器綁定一些 DOM 節點操作，就會引發大量消耗效能的 DOM 計算，不斷重新計算 DOM 元素的絕對位置，造成頁面緩慢，甚至瀏覽器直接崩潰。

