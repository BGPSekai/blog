---
id: 5ee26439af38b667a8ca6631
title: "LARAVEL CORS"
feature_image:
description: "[vc_row][vc_column][vc_column_text]"
date: 2016-07-28
tags: posts
slug: laravel-cors
layout: layouts/post.njk
---

<!-- \[vc\_row\]\[vc\_column\]\[vc\_column\_text\]![6](undefined) -->

如果我使用了Laravel當後端，然而在前端使用ajax呼叫時遇上這個錯誤該怎麼辦？

這篇文章教你如何解決！

這是因為一個cors的機制，Laravel預設會阻擋非同網域、甚至是port的請求。

假設我從localhost:3000想要透過ajax取得localhost:8000的資料，會被擋住，why？

因為你們不同網域嘛，這也是為了安全性之類的顧慮。

首先，我們建立一個[中介層](https://laravel.tw/docs/5.2/middleware)，command line: `<code class="EnlighterJSRAW" data-enlighter-language="null">artisan make:middleware Cors`

app\\Http\\Middleware\\cors

header('Access-Control-Allow-Origin', '\*') ->header('Access-Control-Allow-Methods', 'GET, POST, PUT, PATCH, DELETE, OPTIONS'); } } app\\Http\\Kernal.php protected $routeMiddleware = \[ 'cors' => \\App\\Http\\Middleware\\Cors::class, \]; 順便關了\[csrf\](https://laravel.tw/docs/5.2/routing#csrf-protection) 找到這行並註解\```\App\Http\Middleware\VerifyCsrfToken::class,` 然後在你所需要的路由上使用中介層(我就用[上篇](https://bgpsekai.thisistap.com/tutorials/laravel/2016/07/laravel-jwt/)來做了) Route::group(['prefix' => 'api', 'middleware' => 'cors'], function() { Route::get('auth', 'AuthController@index'); Route::post('auth', 'AuthController@auth'); }); 路由表如下(會在中介層出現cors) ![1](undefined) 能從jquery官網直接抓到本機的api資料也是滿狂的啊     參考文章： http://en.vedovelli.com.br/2015/web-development/Laravel-5-1-enable-CORS/[/vc_column_text][/vc_column][/vc_row]``
