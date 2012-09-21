---
layout: post
title: "Note: Seminar -  Location Service Protocols for Vehicular Ad Hoc Networks Abstract"
date: 2012-09-20 15:10
comments: true
categories: 
- Seminar Notes
---

演講人：世新大學 許智舜教授

* 車載通訊網路的研究
* MANET, VANET, VANET+Coast Location Service Protocols
* MANET 是比較早出現的。與 VANET 不太一樣
* Location Service 是指知道別人位置並以知通訊
* 基本的車子需要有各種感測器，然後把這些感測器的訊息連接到處理中心，再與伺服器連結
* Ad Hoc Network ：車載隨意網路，包括車間通訊與 Roadside 基地台。放在道路旁邊，負責與網際網路作通訊
* 也可以在距離過遠時，以車間通訊作中介，間接的連上Roadside 基地台
* V2V, V2R 就是這兩種網路。OBU 是車載單元，RSU 是基地台單元

* 一個重點是支援智慧型的運輸系統
* GPCR 在知道目的地時，使用貪婪策略往一個個最靠近之節點作一步步導航往前。這問題是有可能有突出的分岔節點造成有一部份是要往回走，浪費該分枝
* GPSR 因此是先到交叉點，然後在交叉點再做決策
* Geocast 是指把訊息送到特定區域。這邊有像網路那種 Unicast, Boardcast。只是 Geocast 加上了地理區域的概念。現在是要傳給該區域中的所以節點
* 例如可以將事故位置的資訊傳給在附近位置的車輛

* MANET 的協定介紹
* GLS 是把地理區域化成小方格，小格又成大格，因此 Location Server 會去以「比該小格 Id 大，又離其最近的小格中 Sever 作為挑選」
* 對該大格以外的其他格，就只要一大格選一個 Location Server ，該使用者就可以以遠近決定減少或增加使用的 Location Server 密度
* 如果都以小格為單位，這樣一個使用者使用的 Location Server 過多，更新資料時成本過大
* 每個 Location Server 都會有目前知道位置資訊的節點。每一個 Location Server 會往外查詢直到取得了想要取得的資訊

* 另一種是超級節點概念：車節點中有些是超級節點，因此以線為準，線中間的超級節點負責其周圍所有的通訊與資訊更新。如果其中子節點有必要與其他節點作溝通，
就可以透過這樣的線圖作網路線方式的傳遞

* HLLS：歷史資訊為準。如果要傳訊息到某個目的地，節點會以初始狀況為基準，紀錄其經過路線，往其路線上剛好有的節點做成傳送路線

* HLS：階層概念，做成六腳蜂格網路。然後以階層為主一層層往上往外傳。只要該網格中有點，該點就會被臨時挑出作為中介點。這樣每一層區域擴大，點每層只有一個。
但這樣每個節點都必須知道其他節點的更新情況。而詢問訊息相反，是從自己開始往最高層一路降下去傳到基本網格，才到節點
* VANET 與 MANET 差別在於，前者是車輛，後者大部分是行人（Mobile Device）。VANET 維持連線方面更困難，但車輛會以道路形狀為主，所以比較規則

* VNAET 協定介紹
* VLS 是學之前 GLS 一樣切網格。網格現在會增加是否有道路的資訊，即是以該格內的道路中選一點作為該格中 Locaton Server 的調整位置
* 這邊所謂 Location Server 是以車節點為主，因此有無道路很重要

* Cache-Based 的則利用各時間點 T-delta 與零點位置的差異作資訊擴散。也就是隨著移動，大致會知道其附近資訊的車輛節點，這會逐漸形成擴散的圖。
也就是每個節點會按照移動時更新周圍節點，而隨著方向相反的節點資訊比較舊，移動前方向的資訊比較新，形成有方向差異的節點群，因此資訊的發送就會逐漸逼近目標。找到後建立了 Routing

* RLSMP：一樣把區域切成不同格，各格構成叢集。叢集中間則是該叢集中的節點位置資訊。要知道資訊時，則向該區域中間的節點 LSC 詢問，更新也一起往中間送

* Location Server 面對著密度與成本的背反。因此需要找到一個最有效率的方式佈署 Location Server 
* 假設在程式中，每個車輛都有導航與傳訊的能力，會先切成方格，然後也有階層
* 差異在於 Locatin Server 分成 Local Location Server 與 Dedicated Location Server 。前者會是目前所在位置的 Location Server ，因此節點可以就近詢問
* Dedicated Location Server 則是按照區域分群，選定該區域節點應該被哪個 Location Server 服務
* 所以分群的概念也是很重要的
* 而還可以以 Cost Functions 計算，看要分多少群，以及要有多少台 Location Server 
* 透過 Local/Dedicated Location Server 作道路為主的 MST 計算就可以找到通訊路線

* 更新資訊的時間是很重要的：計算更新與不更新，何者成本高，因此歷史資訊會很重要
* 也就是預估未知與實際位置不準的差異
* 最主要就是提出了 Cost 為主的考量，在 Update 方面勝過既有的方案，但 Query 比較不如
* 另外就是以現代的條件，有如此模組的車輛可能不夠形成可用的網路
