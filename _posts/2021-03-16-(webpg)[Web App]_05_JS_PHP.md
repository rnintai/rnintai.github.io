---
title: "[Web App] 05. JavaScript, PHP"
categories: 
  - Web Programming
last_modified_at: 2021-03-14 15:23:00
toc: true #Table of Contents
comments: true
---
# 참고
[php파일 반영 delay 줄이기](https://hack.pe.kr/373)  
`php.ini`에서 `opcache.enable = 0`으로 수정.  
서버 재시작 잊지 말기  


# 개요  
HTML은 문서 작성에 적합하다.  
`<script>`태그는 자바 스크립트임을 알려준다.  

JavaScript와 PHP는 협력적이고, 경쟁적인 관계이다.  
이 둘은 서로 비슷한 일을 하기도 하고, 서로가 못하는 일을 대신 해주기도 하기 때문이다.  
HTML, CSS는 정적인 반면 JS와 PHP는 동적인 언어이다.  

PHP 엔진은 데이터베이스에 접근하여 데이터를 가져올 수 있게 해준다.  
데이터베이스에는 표가 있어, 그 표에서 정보를 가져온다.  

![image](https://user-images.githubusercontent.com/65759076/111323092-e89c8200-86ac-11eb-953d-311303053795.png)  
[출처](https://youtu.be/j63iZW0iB3o?list=PLuHgQVnccGMAE4Sn_SYvMw5-qEADJcU-X&t=773)

PHP를 적용함에 있어 장점은 예를 들어  
100개의 웹페이지를 수정해야 할 때에, PHP가 없더라면 각 웹페이지를 모두 수정해야 하지만  
PHP가 있으면 공통적인 부분을 수정할 때에 PHP파일만 수정해주면 되어 각각을 수정하는 수고를 덜게 된다.  


# 기초
## PHP
기본 시작은 `<?php ~ ?>`으로 한다.  

**출력** `echo "~";`  

## JavaScript
기본 시작은 `<script> ~ </script>`로 한다.   

**출력** `document.write("~");`

## 차이점  
![image](https://user-images.githubusercontent.com/65759076/111329637-99f1e680-86b2-11eb-9f6e-112620f6fa55.png)

소스를 보았을 때에 이러한 차이점이 나타나는 이유는  
결론적으로 php는 server side언어라 서버에서 해석을 위임하였기 때문이고,  
JS는 웹브라우저(클라이언트)에서 해석하여 화면에 반영하기 때문이다.


# 자료형
숫자의 경우 `"`으로 묶으면 문자열, 안묶으면 숫자 자료형으로 해석된다.  
## JavaScript
`+` 연산자는 문자열의 경우 문자열을 합치고, 숫자의 경우 덧셈으로 해석된다.

## php
`+` 연산자는 문자, 숫자 관계없이 수의 덧셈을 하고,  
문자열을 합치고 싶다면 `.`연산자를 사용해 주어야 한다.  


# 디버그  
## JavaScript 디버그
크롬 기준 관리자 도구의 콘솔, `Ctrl+Shift+J`을 이용  

## PHP 디버그
`C:\Bitnami\wampstack-8.0.3-0\apache2\htdocs\logs\error.log`의 맨 아래에 로깅되어있다.  

## 화면에서 확인하는 방법  
`C:\Bitnami\wampstack-8.0.3-0\php\php.ini`에서  
`display_errors = On`으로 변경하면 가능하다.  
이후 Apache Server을 재시작해주면 적용.  


# 변수  
## JavaScript
`var = data`의 문법

## PHP
`$var = data`의 문법
