---
title: "[Web App] 00. 웹 애플리케이션 개요"
categories: 
  - Web Programming
last_modified_at: 2021-03-14 15:23:00
toc: true #Table of Contents
comments: true
---
[생활코딩](https://www.youtube.com/playlist?list=PLuHgQVnccGMAE4Sn_SYvMw5-qEADJcU-X)

# 배울 것

- 포스팅 기능
- 데이터베이스를 php언어로 접근하기, mysql
- 반응형 웹 (크기의 변화에 따라 반응)

# 대략적인 구조

1. Client  
html, css, JS, 웹브라우저

1. Server
미들웨어(php), 데이터베이스(MySQL), 웹 서버

구상 -> 기획 -> 개발 -> 테스트

# 기획
## UI 모델링 도구
1. 손그림
2. [pencil](http://pencil.evolus.vn/)
3. balsamiq
4. ppt

# 웹
## 웹이 무엇인가?
인터넷이라는 전세계적 망을 활용하여, HTML이라는 용어로 웹 페이지 데이터를 주고 받는 환경이다.  
자세히 말하면 웹 브라우저와 웹서버가  
HTTP라는 규약을 이용하여 HTML언어로 된 웹페이지를 주고받는 것.  

# 서버와 클라이언트
1. 웹브라우저(Client)가 서버에 서비스를 요청함.
2. 서버는 이에 응답한다.

# 내부 동작 과정
![image](https://user-images.githubusercontent.com/65759076/111058259-a4ed2100-84d0-11eb-822f-c0921bdce83c.png)
[출처]https://www.youtube.com/watch?v=3Ng9X1QYFaA&list=PLuHgQVnccGMAE4Sn_SYvMw5-qEADJcU-X&index=8

# HTML 태그
```html
안녕하세요. <strong>민타이</strong>입니다.
```
`<시작태그>컨텐츠</끝태그>`의 문법을 사용.

## a 태그
링크를 달 때에 사용.  
`<a href="http://rnintai.github.io">민타이</a>`  

**새 창에서 열기**  
: target의 속성 값을 \_blank로 지정.  
`<a href="http://rnintai.github.io" target="_blank">민타이</a>`  

**참고**: 태그의 속성은 공백으로 구분
