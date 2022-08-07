---
id: 5ee26439af38b667a8ca661f
title: "React es6 webpack 環境懶人包紀錄"
feature_image: 
description: "請確認已安裝webpack"
date: 2016-04-16
tags: posts
slug: react-es6-webpack--e7-92-b0-e5-a2-83-e6-87-b6-e4-ba-ba-e5-8c-85-e7-b4-80-e9-8c-84
layout: layouts/post.njk
---

請確認已安裝webpack

npm

npm install react react-dom babel-loader babel-preset-es2015 babel-preset-react --save-dev

webpack.config.js

var path = require('path'); var config = { entry: path.resolve(\_\_dirname, 'resources/assets/js/xxx.js'), output: { path: path.resolve(\_\_dirname, 'public/js'), filename: 'bundle.js' }, resolve: { extensions: \['', '.js', '.jsx'\] }, module: { loaders: \[ { test: /.jsx?$/, exclude: /node\_modules/, loader: 'babel', query: { presets: \['es2015', 'react'\] } } \] } }; module.exports = config;

`<code class="EnlighterJSRAW" data-enlighter-language="null">webpack -w` 即可
