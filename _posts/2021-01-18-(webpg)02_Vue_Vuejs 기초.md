---
title: "02 Vue.js 기초"
categories: 
  - Web Programming
last_modified_at: 2021-01-18 15:23:00
toc: true #Table of Contents
comments: true
---

[Vue.js 기초](https://www.youtube.com/watch?v=bxxZmYUpg6M&list=PLB7CpjPWqHOtYP7P_0Ls9XNed0NLvmkAh&index=2)

# Vue instance
```html
<!DOCTYPE html>
<html>

<head>
  <title>Hello Vue.js</title>
</head>

<body>  
<div id="app">
  <h1>Hello {% raw %} {{ str }} {% endraw %} world!</h1>
</div>

<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
<script>
var app = new Vue({     // Vue Instance
  el: '#app',
  data: {
    str: 'Vue.js'
  }
})
</script>
</body>

</html>
```

- **el**: 인스턴스가 사용될 html element  
- **data**: 사용자에게 보여주기 위한 데이터  
- **methods**: 인스턴스 내에서 사용될 메서드  

data나 methods를 참조할 때에는 {% raw %}`{{ ... }}`{% endraw %}를 이용.

## methods 포함 예제
```html
<!DOCTYPE html>
<html>

<head>
  <title>Hello Vue.js</title>
</head>

<body>  
<div id="app">
  <h1> {% raw %}{{ nextYear('잘 가 2021년') }}{% endraw %} </h1>
</div>

<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
<script>
var app = new Vue({
  el: '#app',
  data: {
    person: {
    	name: '민타이',
    	age: 25
    } 
  },
  methods: {
  	nextYear(greeting){
  		var result = '';
  		result = greeting + "! " + this.person.name + "는 내년에 "
               + (this.person.age + 1) + "살이 됩니다.";
  		return result;
  	}
  }
})
</script>
</body>

</html>
```  
**주의!** 여러 `data`나 `methods`를 사용할 때에, 쉼표 구분을 잘 하자.  

# Data binding
html 태그들의 속성 부분은 큰 따옴표로 감싸져 있다.  
이 부분에 vue 인스턴스의 데이터나 메서드를 참조하려면  
**데이터 바인딩**을 해주어야 한다.  

예시를 살펴보자.

```html
<div>
  <input type="text" :value="input_data"> 
<!-- ':' 대신 'v-bind:'도 가능. -->
</div>

...

data: {
  ... ,
  input_data: 'hello'
}
```

`v-bind:`라는 예약어를 통하여 바인딩을 해줄 수 있다.  
더 간단히 `v-bind`를 생략하고 `:`만 붙여주어도 바인딩을 할 수 있다.

