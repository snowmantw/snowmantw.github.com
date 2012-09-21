---
layout: post
title: "Note: Computer Graphics #1"
date: 2012-09-19 13:11
comments: true
categories: 
- Course Notes
---

* Shading 是指在面與線的基礎上增加了光線與材質的交互作用層
* Texture 則是加在表面呈現出材質的效果
* Framebuffer 記憶體將儲存運算後的資料，然後顯示器朝之要這些資料並畫出來
* Framebuffer 如何更新是重點之一
* Model-Rendering-Animation 是三個領域
* Pixel 對記憶體就是位元組。比如 4 Bytes 對應到 32 萬色的一個像素
* 如果沒有 Shading ，每個面都會同色同光。加上去後才有光影立體的感覺 
* Shadow 與 Reflection 則是後面的工作

---

* Rendering Pipline ：平行處理
* 轉換觀點：Transformation ，去以相機為準變換整個影像
* Transformer --> Clipper --> Projector --> Rasterizer --> Pixels
* Transformer 是幾何轉換
* Clipper 把不在視覺中的物體遮掉不顯示
* Rasterizer 從幾何轉換成像素觀點（從平面頂點變為描述哪些像素要被填滿）
* Shading 還在後面。不過為了效率，會在過程中作

---

* Global Illumination ：全環境中的光線軌跡。包括散射之類的議題。
* 物理光學以外，還有一種是繪圖風格的渲染方式

---

* 課程會把 OpenGL 核心功能實做一次
* 根據老師的提醒，OpenGL 矩陣存到記憶體順序是 Column Major 。代表順序是從左上開始往下數，最後面是最右下。因此 

<pre>
    M[16] == {0,1,2,3,4,5,6,7}

    [ 0  4
      1  5
      2  6
      3  7 ]
</pre>


