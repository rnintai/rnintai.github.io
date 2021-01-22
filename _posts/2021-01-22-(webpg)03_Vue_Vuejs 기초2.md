---
title: "02 Vue.js 기초 (2)"
categories: 
  - Web Programming
last_modified_at: 2021-01-18 15:23:00
toc: true #Table of Contents
comments: true
---

# 클래스 바인딩  
## 방법 1
클래스 앞에 콜론을 붙여주고, 속성의 내용을 `{}`으로 감싸준다.
```html
<!DOCTYPE html>
<html>

<head>
  <meta charset="UTF-8">
  <title>style</title>
  <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
  <style>
    .red {
      color: red;
    }

    .bold {
      font-weight: bold;
    }
  </style>
</head>

<body>  
<div id="app">
  <div :class="{ red: isRed, bold: isBold }">Hello</div>
  <button @click="update_red">Red</button>
  <button @click="update_bold">Bold</button>
</div>

<script>
new Vue({
  el: '#app',
  data:{
    isRed: false,
    isBold: false
  },
  methods:{
    update_red(){
      this.isRed = !this.isRed;
    },
    update_bold(){
      this.isBold = !this.isBold;
    }
  }
})
</script>
</body>

</html>
```  

위의 예제에서, `isRed`의 값이 `true`일 때에 `.red` class를 적용시킨다.  
`isRed`의 값을 버튼을 통해 바꾸어 준다.  

**참고** 클래스의 이름에 대쉬가 들어갈 경우, 따옴표로 묶어서 바인딩 호출을 해야 함.  
```html
<div :class="{ 'font-bold': isBold }"></div>
```

## 방법 2
`data`에 **객체**로 클래스의 내용을 선언.

```html
<div :class="classObject"></div>
```
```html
data: {
  classObject:{
    red: true,
    'font-bold': false
    ...
  },
...
}

```

## 그 이외의 방법
- 객체를 반환하는 `computed` 속성에 바인딩  
- 배열 구문 바인딩  
- 조건부 토글을 위한 삼항 연산자 구문

[참고](https://kr.vuejs.org/v2/guide/class-and-style.html)

# 스타일 바인딩
## 일반 바인딩
```html
<!DOCTYPE html>
<html>

<head>
  <meta charset="UTF-8">
  <title>style</title>
  <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
</head>

<body>  
<div id="app">
  <div :style="{ styleObject }">Hello</div>
  <!-- 여러 단어는 camelCase 사용-->
</div>

<script>
new Vue({
  el: '#app',
  data:{
   s
  },
  methods:{
    
  }
})
</script>
</body>

</html>
```
## 객체 바인딩
```html
<!DOCTYPE html>
<html>

<head>
  <meta charset="UTF-8">
  <title>style</title>
  <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
</head>

<body>  
<div id="app">
  <div :style="styleObject">Hello</div>
  <!-- 객체 바인딩 시 중괄호없이. -->
</div>

<script>
new Vue({
  el: '#app',
  data: {
    styleObject: {
      color: 'red',
      fontSize: '30px'
    }
  },
  methods:{
    
  }
})
</script>
</body>

</html>
```
