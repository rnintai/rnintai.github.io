---
title: "02 Vue.js 기초"
categories: 
  - Web Programming
last_modified_at: 2021-01-18 15:23:00
toc: true #Table of Contents
comments: true
---

[코지코더님의 Vue.js 기초](https://www.youtube.com/watch?v=bxxZmYUpg6M&list=PLB7CpjPWqHOtYP7P_0Ls9XNed0NLvmkAh&index=2)

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

`v-bind:`라는 디렉티브를 통하여 바인딩을 해줄 수 있다.  
더 간단히 `v-bind`를 생략하고 `:`만 붙여주어도 바인딩을 할 수 있다.

# Event  
## Button 이용 예제  
```html
<!DOCTYPE html>
<html>

<head>
  <meta charset="UTF-8">
  <title>event_demo</title>
  <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
</head>

<body>  
<div id="app">
  {{ year }}<br>
  <button v-on:click="add">더하기</button>
  <button v-on:click="sub">빼기</button>
</div>

<script>
new Vue({
  el: '#app',
  data:{
    year: 2021
  },
  methods:{
    add(){
      this.year++;
    },
    sub(){
      this.year--;
    }

  }
})
</script>
</body>

</html>
```  
button이 클릭될 때의 이벤트를 처리할 때의 바인딩은  
`v-on:` 혹은 `@` 키워드를 이용한다.

## form과 submit 예제
```html
<!DOCTYPE html>
<html>

<head>
  <meta charset="UTF-8">
  <title>event_demo</title>
  <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
</head>

<body>  
<div id="app">
  <form v-on:submit="submit">
    <input type="text"><br>
    <button type="submit">Submit</button>
  </form>
</div>

<script>
new Vue({
  el: '#app',
  data:{
    
  },
  methods:{
    submit(){
      alert('submitted!');
    }
  }
})
</script>
</body>

</html>
```

**참고** form은 기본적으로 submit했을 때에 페이지를 다시 불러온다.

## 이벤트 수식어  
Vue는 이벤트 핸들러 내부에서 자주 호출되는 메서드들을 수식어로 지원한다.  
**이벤트 수식어**는`v-on`이벤트 뒤에 접미사처럼 사용한다.  
  
- `.stop`: 상위 element들로의 **이벤트 전파**를 중단시킴  
- `.prevent`: 해당 element의 **고유 동작**을 중단시킴  
- `.capture`  
- `.self`  
- `.once`  
- `.passive`  

## 키 수식어  
키보드의 키 입력에 대한 이벤트를 처리할 수 있다.  

### 키 이벤트  
- `keydown`: 키 입력 시 발생  
- `keypress`: 키 입력 시 발생. 특수키에는 반응 없음  
- `keyup`: 키가 release될 때에 발생  

### 키 코드  
- `.enter`  
- `.tap`  
- `.delete`(Backspace 키도 캡쳐)  
- `.esc`  
- `.space`  
- `.up`  
- `.down`  
- `.left`  
- `.right`  

```html
<input v-on:keyup.enter="submit">
```

### 시스템 키 수식어  
- `.ctrl`  
- `.shift`  
- `.alt`  
- `.meta`(윈도우 키 혹은 Mac의 command키)  

```html
<!-- Alt + C -->
<input @keyup.alt.67="clear">

<!-- Ctrl + Click -->
<div @click.ctrl="doSomething">Do something</div>
```

#### +`.exact` 수식어
다른 시스템 수식어와 조합하여도 실행되는 것을 방지  
정확한 키 조합을 눌러야 핸들러가 실행된다.

```html
<!-- Alt 또는 Shift와 함께 눌린 경우에도 실행됩니다. -->
<button @click.ctrl="onClick">A</button>

<!-- Ctrl 키만 눌려있을 때만 실행됩니다. -->
<button @click.ctrl.exact="onCtrlClick">A</button>

<!-- 아래 코드는 시스템 키가 눌리지 않은 상태인 경우에만 작동합니다. -->
<button @click.exact="onClick">A</button>
```

### 키 코드 확인 예제
```html
<!DOCTYPE html>
<html>

<head>
  <meta charset="UTF-8">
  <title>event_key</title>
  <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
</head>

<body>  
<div id="app">
    <input @keyup="key_check">
</div>

<script>
new Vue({
  el: '#app',
  data:{
    
  },
  methods:{
    submitted(){
      alert('submitted!');
    },
    key_check(event){
      console.log(event.keyCode);
    }
  }
})
</script>
</body>

</html>
```

input박스에 키를 입력하면 로그 창을 통해  
키 코드를 확인할 수 있다.  

---

[Vue.js 가이드: 이벤트](https://kr.vuejs.org/v2/guide/events.html)

# 양 방향 바인딩  
**양 방향 바인딩**이란 `Vue 인스턴스 <-> template`  
의 느낌으로 쌍방향으로 데이터에 접근할 수 있도록 하는 것이다.

`v-model` 디렉티브를 통해 할 수 있다.

```html
<!DOCTYPE html>
<html>

<head>
  <meta charset="UTF-8">
  <title>event_key</title>
  <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
</head>

<body>  
<div id="app">
    <!-- <input type="text" :value="text" @keyup="updateText"><br> -->
    <input type="text" v-model="text"><br>
    {{ text }}
</div>

<script>
new Vue({
  el: '#app',
  data:{
    text: ''
  },
  methods:{
    // updateText(event){
    //   var t = event.target.value;
    //   console.log(t);
    //   this.text = t;
    // }
  }
})
</script>
</body>

</html>
```
