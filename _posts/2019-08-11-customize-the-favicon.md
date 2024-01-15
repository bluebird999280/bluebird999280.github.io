---
title: 
author: cotes
date: 2019-08-11 00:34:00 +0800
categories: [Blogging, Tutorial]
tags: [favicon]
---
# Px, Em, Rem의 차이

> 절대단위(px), 상대단위(em, rem)

### **웹에서 사용되는 단위에는 절대단위와 상대단위가 있다는 것을 알고 계셨나요?**

절대 단위란 특정 기준에 관계없이 항상 고정된 값을 갖으며, 상대 단위는 특정 기준에 따라 값이 변하는 것이 특징입니다.

절대 단위에는 px이, 상대 단위에는 em과 rem이 있습니다.

그렇다면 웹 페이지를 만들때마다 고민하게 되는 반응형 페이지에서는 어떤 것을 사용하는 것이 더 유리할까요?

디바이스의 크기에 따라 다른 값을 줘야하는 상황에서는 상대단위인 em과 rem이 더 유리하지 않을까요?

만약 그렇다고 한다면 em과 rem의 차이는 또 무엇일까요?

### **em과 rem의 차이**

em과 rem은 특정 기준에 따라 값이 바뀌는 상대 단위입니다.

**그렇다면 특정 기준은 무엇일까요?**

**em**은 자신이 속한 요소의 font-size를 기준으로 하며,

**rem**은 최상위 요소의 font-size를 기준으로 값을 정합니다.

예를 들어볼게요.

```
<html>
	<head>
		<style>
			html {
				font-size: 16px;
			}

			.wrapper1 {
				height: 100px;
				background-color: black;
				padding-left: 10rem;
				padding-right: 10rem;
				border: 1px solid black;
			}

			.wrapper1 > .wrap {
				width: 100%;
				height: 100%;
				background-color: white;
			}

			.wrapper2 {
				height: 100px;
				background-color: black;
				font-size: 12px;
				padding-left: 10em;
				padding-right: 10em;
				border: 1px solid black;
			}

			.wrapper2 > .wrap {
				width: 100%;
				height: 100%;
				background-color: white;
			}
		</style>
	</head>
	<body>
		<div class="wrapper1">
			<div class="wrap">
				<div class="content"></div>
			</div>
		</div>
		<hr />
		<div class="wrapper2">
			<div class="wrap">
				<div class="content"></div>
			</div>
		</div>
	</body>
</html>
```


![](https://blog.kakaocdn.net/dn/IGG6q/btsDrmdfk0I/iPibhFzmFVkbkZ0VlbGvx0/img.png)

HTML에 대한 설명 이미지

첫번째 Wrapper는 padding의 양쪽을 10rem을 넣어줍니다.

rem은 가장 최상단 요소의 font-size를 1rem으로 설정합니다.

따라서 1rem = html의 font-size(16px)이 되므로 10rem은 160px이 됩니다.

두번째 Wrapper는 padding의 양쪽을 10em을 넣어줍니다.

em은 현재 요소의 font-size를 1em으로 설정합니다.

따라서 1em = Wrapper2의 font-size(12px)이 되므로 10em은 120px이 됩니다.

#### **그렇다면 최상단 요소의 font-size가 없거나 현재 요소의 font-size가 없다면 어떻게 될까요?**

1. 최상단 요소의 font-size가 없을 때 rem을 사용할 경우 브라우저가 설정한 값으로 rem이 설정됩니다.
2. 현재 요소의 font-size가 없을 경우에는 font-size는 inherit(상속)값을 기본값으로 갖기 때문에 현재 요소를 감싸주는 요소들에서 가장 가까운 font-size값을 가져와 사용합니다.
