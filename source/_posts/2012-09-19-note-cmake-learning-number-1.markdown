---
layout: post
title: "Note: Cmake Learning #1"
date: 2012-09-19 20:32
comments: true
categories: 
- Tech Notes
- Cmake
---

* 參考資源
  * [Cmake 入門](http://zh.wikibooks.org/wiki/CMake_%E5%85%A5%E9%96%80)
  * [Cmake 官方網站：命令列表](http://www.cmake.org/cmake/help/v2.8.8/cmake.html#section_Commands)

----

* 如果要尋找系統中有沒有特定函式庫，首先要確定有該函式庫的模組。可用 `cmake --help-module-list` 協助尋找是否該模組存在
* 如果有該模組，可以用 `find_package` 命令去找。注意該命令給定的名字必須符合前述搜尋模組給的名字，而不是系統中套件名稱。例如

<pre>
     # Find GLUT package in system. 
     # Not system package name like "freeglut3-dev".
     find_package (GLUT REQUIRED) 
</pre>

* 如果要作不符合條件即中斷 Cmake 執行，可以使用 `message(FATAL_ERROR "<message>")` 的方式印出錯誤後中止執行。
例如前述尋找系統套件，找不到就可以用這種方式報錯離開

---

* `target_link_library` 是該 Cmake 所針對的編譯單元，需要連結哪些函式庫
* `add_library` 則是把該編譯單元包成函式庫，兩者目的相關方向相反
* `target_link_library` 可以指定編譯器連結參數，例如

<pre>
     # Require compiler compiling with these arguments.
     target_link_libraries(CGHW1 -lGL -lglut -lGLU)
</pre>

* 這邊的連結參數會影響產生的 Makefile 中所下參數，所以是必要的
* `include_directory` 是指定該次編譯尋找引入檔的目錄路徑（不知道非 C 類是否適用這概念？）
* `add_subdirectory` 則是指定要遞回進子目錄，先作該 CMake 再回來
* 有些屬性要自己隨著目錄結構而設定，例如 `IMPORTED_LOCATION` 就關係到產生函式庫後擺放檔案的位置

---

* Cmake 2.8 還是需要在 `else` 這個關鍵字後面接上條件的樣子。不能如前面那樣省略，而是必需變成 `else(<condition>)` 
* 推薦使用所謂 "Out-of-source Build" ，將建置目錄與原始碼目錄分開
* Cmake 執行時指定目錄，會自動找尋其中是否有 CMakeLists.txt 並利用執行
* Cmake 範例的結構中，看起來是每個模組或其他編譯單元的目錄中都各有一個 CMakeLists.txt ，整個專案再一個。
例如「Cmake 入門」中的[範例][1]:

<pre>
    lib1/
        src/
            app/
                CMakeLists.txt
                main.c
            calc/
                CMakeLists.txt
                calc.c
                calc.h
    CMakeLists.txt
</pre>

[1]: http://zh.wikibooks.org/wiki/CMake_%E5%85%A5%E9%96%80/%E5%BB%BA%E7%BD%AE%E8%88%87%E9%80%A3%E7%B5%90%E7%A8%8B%E5%BC%8F%E5%BA%AB
