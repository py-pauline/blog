---
title:  event对象事件
date: 2017-07-25 21:43:32
tags:
categories:
---

Event 对象代表事件的状态，比如事件在其中发生的元素、键盘按键的状态、鼠标的位置、鼠标按钮的状态。

<!-- more -->

##### 事件句柄

事件句柄是指能够使html事件触发浏览器中的行为。

| 属性 | 此事件发生在何时 | 支持该事件的js对象 |
| :--- | :---- | :---- |
| onabort | 图像加载被中断 | 仅支持图片 |
| onblur    | 对象失去焦点时 |      |
| onchange    | 域的内容改变时 |  |
| onclick |	点击 | |
| ondbclick |   双击    |      |
| onerror | 加载文档或图像时发生错误 | window，image |
| onfocus | 获得焦点 |  |
| onkeydown | 某个键盘按键被按下 |  |
| onkeypress | 某个键盘按键被按下并松开 |  |
| onkeyup | 键盘按键松开时 |  |
| onload | 在页面或图像完成后立即发生 | image,layer,window |
| onmousedown | 鼠标按钮被按下 |  |
| onmousemove | 鼠标被移走 |  |
| onmouseout | 鼠标从某元素上移开 |  |
| onmouseover | 鼠标移到某元素之上 |  |
| onmouseup | 鼠标按键被松开 |  |
| onrest | 重置按钮被点击 | form |
| onresize | 窗口或框架被重新调整大小 |  |
| onselect | 文本被选中 | window |
| onsubmit | 确认按钮被点击 | form |
| onunload | 用户退出页面 |   |


##### 鼠标/键盘属性

| 属性 | 此事件发生在何时 | 示例 |
| :--- | :---- | :---- |
| altKey | Alt键是否被按下并保持住 | event.altKey=true|false|1|0 |
| button | 哪个鼠标按键被点击 | event.button=0|1|2 |
| clientX,clientY | 当前窗口的坐标位置 | x=event.clientX y=event.clientY |
| ctrlKey | Ctrl键是否被按下 | event.ctrlKey=true|false|1|0 |
| metaKey | "meta" 键是否被按下 | event.ctrlKey=1|0 |
| relatedTarget |  | 对于 mouseover 事件来说，该属性是鼠标指针移到目标节点上时所离开的那个节点。
对于 mouseout 事件来说，该属性是离开目标时，鼠标指针进入的节点。 |
| screenX | 鼠标在当前屏幕的坐标位置 | x=event.screenX
  y=event.screenY |
| shiftKey | "SHIFT" 键是否被按下并保持住。 | event.shiftKey=true|false|1|0 |
|  |  |  |
|  |  |  |

##### 标准Event属性





