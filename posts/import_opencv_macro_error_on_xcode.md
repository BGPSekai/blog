---
id: 5ee26439af38b667a8ca665e
title: "openCV 導入 iOS 專案筆記"
feature_image: https://images.unsplash.com/photo-1531312267124-cd1f431feb1e?ixlib=rb-1.2.1&q=80&fm=jpg&crop=entropy&cs=tinysrgb&w=2000&fit=max&ixid=eyJhcHBfaWQiOjExNzczfQ
description: "匯入的部分非常簡單只要確認 Framework 檔案有導入，專案設定確認有導入就可以直接用了(最下面的 opencv2.framework 那項)"
date: 2020-04-28
tags: posts
slug: import_opencv_macro_error_on_xcode
layout: layouts/post.njk
---

匯入的部分非常簡單只要確認 Framework 檔案有導入，專案設定確認有導入就可以直接用了
![導入列表](/img/content/images/import_opencv_macro_error_on_xcode/Y0ykSoh.png)
(最下面的 opencv2.framework 那項)

接下來就橋接到你的 object c 檔案吧 (要接到 Swift 還要再接一層 Bridge 有空再講)
但是邊譯時就遇到這錯誤了
![Expanded from macro 'NO'](/img/content/images/import_opencv_macro_error_on_xcode/Tu92USR.png)

`Expanded from macro 'NO'`

後來才發現是內建的 macro check 所導致的，最簡單的解法就是放在引入其他東西之前，像是下面這樣
![](/img/content/images/import_opencv_macro_error_on_xcode/KHbD93I.png)

這樣就可以順利編過囉
