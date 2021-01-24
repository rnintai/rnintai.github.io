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
  <div :style="{ color: activeColor, fontSize: fontSize + 'px' }">Hello</div>
  <!-- 여러 단어는 camelCase 사용-->
</div>

<script>
new Vue({
  el: '#app',
  data:{
    activeColor: 'red',
    fontSize: 30
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

# v-if와 v-show  
## v-if  
조건문의 용도. else 사용 가능  
여러 요소의 렌더링에 대한 조건을 걸고 싶을 경우, `<template>`을 사용하자

```html
<!DOCTYPE html>
<html>

<head>
  <meta charset="UTF-8">
  <title>v-if & v-show</title>
  <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
</head>

<body>  
<div id="app">
  <template v-if="show">
    <div>Yes1</div>
    <div>Yes2</div>
    <div>Yes3</div>
  </template>
  <template v-else>
    <div>No1</div>
    <div>No2</div>
    <div>No3</div>
  </template>
  <button @click="update">toggle</button>
</div>

<script>
new Vue({
  el: '#app',
  data: {
    show: true
  },
  methods:{
    update(){
      this.show = !this.show;
    }
  }
})
</script>
</body>

</html>
```

# v-else와 v-else-if
`v-if` 이외의 경우들의 조건을 걸어 줄 때에 사용한다.

## v-show  
`v-show`는 해당 속성의 불 값에 따라 **렌더링 여부**를 결정한다.
```html
<!DOCTYPE html>
<html>

<head>
  <meta charset="UTF-8">
  <title>v-show</title>
  <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
</head>

<body>  
<div id="app">
  <div v-show="show">show</div>  
  <button @click="update">toggle</button>
</div>

<script>
new Vue({
  el: '#app',
  data: {
    show: true
  },
  methods:{
    update(){
      this.show = !this.show;
    }
  }
})
</script>
</body>

</html>
```

## v-if vs. v-show
`v-if`는 토글의 비용이 높고, `v-show`는 초기 렌더링의 비용이 더 높다.  
이러한 특징을 고려하여, **토글이 잦은 경우** `v-show`를 사용하는 것이 좋고,  
**런타임 내에 변화가 적은 경우** `v-if`를 사용하자.

# v-for 리스트 렌더링
기본적으로 vue에서 배열은 **대괄호**로 감싸고, **쉼표**로 구분하여 표현한다.

`v-for`을 사용하면 배열을 **반복 접근**할 때 용이하다.
```html
<!DOCTYPE html>
<html>

<head>
  <meta charset="UTF-8">
  <title>v-show</title>
  <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
</head>

<body>  
<div id="app">
  <div v-for="a in people">
    {% raw %}{{ a.name }} {{ a.age }}{% endraw %}
  </div>
</div>

<script>
new Vue({
  el: '#app',
  data: {
    people: [
      { name: 'a', age: 20 },
      { name: 'b', age: 21 },
      { name: 'c', age: 22 },
      { name: 'd', age: 23 },
    ]
  },
  methods:{
  }
})
</script>
</body>

</html>
```
