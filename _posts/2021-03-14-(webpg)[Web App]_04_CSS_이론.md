---
title: "[Web App] 04. CSS 이론"
categories: 
  - Web Programming
last_modified_at: 2021-03-14 15:23:00
toc: true #Table of Contents
comments: true
---

# CSS란
Cascading Style Sheet  
HTML과 독립적이지 않다.  
HTML을 시각적으로 보기 좋게 Style을 부여하기 위함.  

# 태그 별 스타일
## 기본 문법
`태그명 {속성}`의 문법을 가진다.  
![image](https://user-images.githubusercontent.com/65759076/111064704-d7127900-84f8-11eb-8dce-f847efbf6a30.png)  
[출처](https://youtu.be/IxCPOBLQeU0?list=PLuHgQVnccGMAE4Sn_SYvMw5-qEADJcU-X&t=790)  
```css
h1 {color:red}
```

속성들 간의 구분자는 `;`이다.  
```html
    h1,h2 {
      color:red;
      font-size:10px
    }
```

하위 태그 지정 시 공백으로 하면 됨.  
```html
    header h1{
      border:1px solid red;
    }
```

한 속성의 내용의 구분도 공백으로 한다.  
```html
      border: 1px red solid;
```

id에 style을 부여하려면 `#`을 앞에 붙여줌  
```html
    #selected {
      border: 1px red solid;
    }
```

## border, 박스 모델  
![image](https://user-images.githubusercontent.com/65759076/111065169-b0a20d00-84fb-11eb-9b5f-03e224face83.png)  
[출처](https://youtu.be/6K-WMWP_94Q?list=PLuHgQVnccGMAE4Sn_SYvMw5-qEADJcU-X&t=787)  

크롬 브라우저의 개발자 도구를 통해 자세히 확인 가능.  

# float
## 이미지 태그
`<img src="url" />`을 통해 이미지를 띄울 수 있음  

## float 속성
`float: left`
예를 들어 이미지와 텍스트를 어우러지게 하기 위한 속성이다.

