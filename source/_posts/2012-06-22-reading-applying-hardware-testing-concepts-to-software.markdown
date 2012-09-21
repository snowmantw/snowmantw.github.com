---
layout: post
title: "Reading: Applying hardware testing concepts to software"
date: 2012-06-22 22:13
comments: true
categories: [Reading, Software Testing] 
---

[這篇文章][1]講述作者 [Dodgy_Coder][2] 自己測試 GUI 程式的經驗，
他覺得軟體的測試在時間長度的概念上可以借鑒硬體的測試概念分三種時間相關的測試概念

1. 短：功能性測試，包括 Unit Testing 與 Integration Testing。這邊可以除去絕大部分的問題。
2. 中：用來測試與減少隨機錯誤。隨機錯誤不太可能完全清除，但可以儘量減少、消除到機率合乎標準
3. 長：將軟體執行到超乎一般時間的長，用來測試諸如記憶體洩漏、效能下降等問題。

作者自己的經驗是他的程式一般只會開半小時，他故意開著兩個小時作測試，
然後在第一個小時時就發現了記憶體洩漏與效能下降的問題，並修正之。

其他概念可以上作者文章看；他那張引自 [wikipedia][3] 的圖還蠻好的

![Bathub curve about testing][3]

[1]: http://www.dodgycoder.net/2012/06/applying-hardware-testing-concepts-to.html
[2]: http://www.blogger.com/profile/14418022725678218844 
[3]: http://upload.wikimedia.org/wikipedia/commons/6/6e/Bathtub_curve.jpg 
