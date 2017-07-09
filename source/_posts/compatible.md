---
title: 媒体查询器做屏幕适配
date: 2016-12-20 14:10:26
tags: 屏幕适配
categories:
---

### 页面中比较常用的尺寸

iphone4,5
=======
###  页面中比较常用的尺寸

##### iphone4,5(w:320px)

	@media all and (min-width:320px) and(max-width: 360px){
		body {  font-size: 12px;  }
	}

##### iphone6(w:375px)

	@media all and (min-width:360px) and(max-width: 400px){
	    body {  font-size: 13px;  }
	}

##### iphon6plus(w:414px)

	@media all and (min-width:400px) and(max-width: 560px){
	    body {  font-size: 14px;  }
	}
##### ipad(w:768px)	

	@media all and (min-width:560px) and(max-width: 640px){
	    body {  font-size: 15px;  }
	}
	
	@media all and (min-width:640px) and(max-width: 750px) {
	    body {  font-size: 16px;  }
	}
	@media all and (min-width:750px) {
	    body {  font-size: 17px;  }
	}