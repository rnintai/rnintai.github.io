---
title: "[Web App] 04. CSS 실습"
categories: 
  - Web Programming
last_modified_at: 2021-03-14 15:23:00
toc: true #Table of Contents
comments: true
---

# 예제
```html
	<style>
		header{
			border-bottom:1px solid gray;
			padding: 20px;
		}
		nav{
			border-right: 1px solid gray;
			width:200px;
			height:600px;
			float: left;
		}
		nav ol{
			list-style: none;
		}
		article{
			float:left;
			padding: 20px;
		}
	</style>
```

# css의 분리
따로 style태그 내의 내용을 css파일로 분리시키고,  
적용할 html파일의 head부분에 아래의 코드 형태를 넣는다.  

```html
<link rel="stylesheet" type="text/css" href="http://localhost/style.css">
```

코드의 중복이 제거되어 수정 및 관리가 용이하다.  
