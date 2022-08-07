---
id: 6277677fda672d1855a6e4ac
title: "Nuxt Server side rendering"
feature_image: /content/images/2022/05/---1.png
description: "最近在使用Nuxt發現有這個錯誤問題"
date: 2022-05-08
tags: posts
slug: nuxt-server-side
layout: layouts/post.njk
---

最近在使用Nuxt發現有這個錯誤問題

```
[Vue warn]: The client-side rendered virtual DOM tree is not matching server-rendered content. This is likely caused by incorrect HTML markup, for example nesting block-level elements inside <p>, or missing <tbody>. Bailing hydration and performing full client-side render.
```



像是這個狀態就會報錯

```html
<span>
    \{\{ $t('hello.success') }}:
    <!-- 註解 -->
</span>
<!-- Good -->
```

```html
<span>
    \{\{ $t('hello.error') }}
    <!-- 註解 -->
    :
</span>
<!-- BAD -->
```



注意v-if的問題和v-for的使用

```html
<template>
  <div>
    <client-only>
      <span v-show="$vuetify.breakpoint.mobile"><span/>
    </client-only>
  </div>
</template>
<!-- Good -->
```

```html
<template>
  <div>
    <client-only>
      <span v-if="$vuetify.breakpoint.mobile"><span/>
    </client-only>
  </div>
</template>
<!-- BAD -->
```

$vuetify.breakpoint.mobile 基本上只能在client-only上，
傳入的變數Server side可能和Client side不一樣。



將程式碼從created()換到mounted() 或是 在created()使用if(process.client)

其他的參考
[https://blog.lichter.io/posts/vue-hydration-error/](https://blog.lichter.io/posts/vue-hydration-error/)

[https://stackoverflow.com/questions/47862591/vuejs-error-the-client-side-rendered-virtual-dom-tree-is-not-matching-server-re/49202327#49202327](https://stackoverflow.com/questions/47862591/vuejs-error-the-client-side-rendered-virtual-dom-tree-is-not-matching-server-re/49202327#49202327)
