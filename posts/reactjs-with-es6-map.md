---
id: 5ee26439af38b667a8ca6614
title: "ReactJS with ES6 - Map"
# feature_image: undefined
description: "import React, { Component } from 'react'; class MapTest extends Component { render() { var newsNodes = this.props.data.map(function(news) {…"
date: 2016-04-09
tags: posts
slug: reactjs-with-es6-map
layout: layouts/post.njk
---

import React, { Component } from 'react'; class MapTest extends Component { render() { var newsNodes = this.props.data.map(function(news) { return ( {news.title} {news.time} ); }); return ( {newsNodes}

| 主題 | 時間 |
| --- | --- |

); } } export class Test extends Component { constructor(props) { super(props); this.state = {data: \[\]}; this.loadNewsFromServer(); } loadNewsFromServer() { $.ajax({ url: '[http://211.23.17.100/itravel/index.php?view=getTravelNewsList](http://211.23.17.100/itravel/index.php?view=getTravelNewsList)', dataType: 'json', type: 'POST', data: {page: 1}, success: function(data) { this.setState({data: data.result}); }.bind(this) }); } render() { return (

); } }
