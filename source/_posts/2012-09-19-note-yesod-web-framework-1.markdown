---
layout: post
title: "Note: Yesod Web Framework #1"
date: 2012-09-19 13:19
comments: true
categories:
- Haskell
- Web Application 
- Tech Notes
---

## Foundation.hs

* Foundation.hs 提供載入資源，以及變成內部資源參照值的函式。
* 該檔案中有分為 Route 、基本核心、儲存機制、認證等界面可以自訂，以此定義出應用本身所需要的各資源模組
* Route 是呼叫特定函式，載入 Route 檔案並建立出 AppRoute
* 基本核心包括 Session 後端組件、如何渲染頁面 Widget 、Static 檔案設定等
* Widget 應該說是子頁面，最終要併到 default-layout-wrapper 這種 Wrapper 的樣板檔中
* RenderMessage 是用來把一些預設訊息渲染出來，包括處理 i18n 之類議題的設定 Type Class

## Application.hs

* 此檔案將建立整個應用
* Handler 也是註冊在這邊。Cabal 檔裡也要記得增加
* 其中 makeFoundation 與 makeApplication 將會分別建立資源參照與 WAI 應用，而後者會相依前者。
* makeApplication 另外還會被 main 函式所直接呼叫
* mkYesodDispatch 會建立應用實體，是繼 mkYesodData 所建立好資料後，繼續接手的程式。這個函式也是實際上會建立 YesodSite 的函式。
* 從目前看到的只能說 mkYesodDispatch 建立網站本身，makeApplication 建立整個 WAI 應用。( WAI: Web Server 與 Application 的介面[^1] )

[^1]: http://www.yesodweb.com/book/web-application-interface "Yesod Official Site"


