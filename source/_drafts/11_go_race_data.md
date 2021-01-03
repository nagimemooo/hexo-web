---
title: "[go]使用gorountine時避免資料競爭而輸出不正確結果"
date: 2020-06-22T16:43:48+08:00
categories: [" 後端 go"]
tags: ["golang", "race condition","Mutex"]
draft: false
---


> 為避免多個goroutine執行發生資料競爭（race condition）會造成結果偶爾會跟想像不同，本章介紹如何簡單避免與檢測方法．

<!--more-->

#### 參考資料:
- [golang中的race检测](https://www.cnblogs.com/yjf512/p/5144211.html "golang中的race检测")
- [30天就Go(17)：Goroutines](https://ithelp.ithome.com.tw/articles/10188220 "30天就Go(17)：Goroutines")
- [Go day 20 (race condition、Mutex)](https://ithelp.ithome.com.tw/articles/10203517 "Go day 20 (race condition、Mutex)") 避免的兩種方法
- [race-detector|Go](https://blog.golang.org/race-detector "race-detector|  Go")

#### race condition
- 多個 goroutine 同時執行工作時，如果有存取到共用的變數，會造成每次的結果可能不一致．
- Golang有自帶可以檢測競爭危害的功能，運行得時候採用參數-race
go run -race  main.go

然後去執行一些程式邏輯，會在過程中產生發生競爭的變數，Log 可能出現在過程中。
- 競爭危害最簡單可以用 Mutex 解決
- 錯誤標準是會用 default stderr 輸出，如果要把 stderr 的結果輸出到檔案，要用 2> 來把它輸出到檔案 ex: go run -race main.go 2>./out.txt，或者更改env GORACE (但我在win環境設定不出來)

範例:
```go
func main() {
	var w sync.WaitGroup
	var m sync.Mutex
	var sum = 0
	for i := 0; i < 100; i++ {
		w.Add(1)
		go func() {
			defer w.Done()
			m.Lock()
			sum++
			m.Unlock()
		}()
		w.Add(1)
		go func() {
			defer w.Done()
			m.Lock()
			fmt.Println(" sum is", sum)
			m.Unlock()
		}()
	}
	w.Wait()
	fmt.Println("final sum is", sum)
}
```


- 可以試著把Mutex拿掉，如果有競爭危害會出現以下LOG內容

```go
==================
WARNING: DATA RACE
Read at 0x00c00016c928 by goroutine 10:
  main.main.func2()
      D:/go/src/firstgodemo/main.go:42 +0x6d

Previous write at 0x00c00016c928 by goroutine 9:
  main.main.func1()
      D:/go/src/firstgodemo/main.go:35 +0x8d

Goroutine 10 (running) created at:
  main.main()
      D:/go/src/firstgodemo/main.go:40 +0x189

Goroutine 9 (finished) created at:
  main.main()
      D:/go/src/firstgodemo/main.go:32 +0x146
==================
因為有時候這段訊息會出現在畫面中間，可以用以下指定把它輸出到txt中。
go run -race main.go 2>./out.txt
final sum is 100
```