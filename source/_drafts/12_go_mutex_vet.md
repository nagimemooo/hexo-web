---
title: "[go]搜集關於鎖的注意事項及go vet 語法檢查"
date: 2020-06-22T16:53:36+08:00
categories: [" 後端 go"]
tags: ["golang", "race condition","Mutex"]
draft: false
---


> 本章搜集關於鎖的注意事項及go vet 語法檢查

#### 文章參考：
[Go: 关于锁（mutex）的一些使用注意事项](https://mozillazg.com/2019/04/notes-about-go-lock-mutex.html "Go: 关于锁（mutex）的一些使用注意事项")
[golang使用vet進行語法檢查](https://www.itdaan.com/tw/40ee8fde353a "golang使用vet進行語法檢查")


#### go vet 語法檢查
- 以用来检查 go 代码中可以通过编译但仍然有可能存在错误的代码

例如:鎖不能被複製等檢查
```go
檢查 package
D:\go\src\xxx>go vet .\internal\startup
# xxx/internal/startup
internal\startup\bootstrap.go:24:2: Println does not take io.Writer but has first arg os.Stderr

檢查 go file
D:\go\src\xxx>go vet main.go

檢查全部 ./... 三個點
D:\go\src\xxx>go vet ./...
# xxx/internal/cache
internal\cache\xx.go:265:11: Wrapf format %v reads arg #2, but call has 1 arg
	像是這邊這段錯誤寫法是:
	errors.Wrapf(err,"Couldn't add ID by %s,err: %v", ID)

```