---
title: "02 Vue.js 기초 (2)"
categories: 
  - Web Programming
last_modified_at: 2021-01-18 15:23:00
toc: true #Table of Contents
comments: true
---

# 클래스, 스타일 바인딩  
클래스 앞에 콜론을 붙여주고, 속성의 내용을 `{}`으로 감싸준다.
```html
<div id="app">
  <div :class="{ red: isRed }">Hello</div>
  
  <button @click="update">Toggle</button>
</div>

<script>
new Vue({
  el: '#app',
  data:{
    isRed: false
  },
  methods:{
    update(){
      this.isRed = !this.isRed;
    }
  }
})
</script>
```
