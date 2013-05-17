---
layout: post
title: "lightbox test"
description: "lightbox 源码学习"
category: lessons
tags: [lightbox]
---
{% include JB/setup %}

## lightbox

{% highlight javascript %}
	/**
	 * [initLightbox 初始化]
	 * @return {[type]} [description]
	 */

	function initLightbox() {
		if (!document.getElementsByTagName) return;
		//获取所有锚点
		var anchors = document.getElementsByTagName("a");

		//循环处理锚点的单击事件
		for (var i = 0; i < anchors.length; i++) {
			var anchor = anchors[i];
			if (anchor.getAttribute("href") && (anchor.getAttribute("rel") == "lightbox")) {
				anchor.onclick = function() {
					console.log("创建弹出窗口 " + this);
					return false;
				}
			}
		}
	}

	/**
	 * [createMask 创建遮盖层]
	 * @return {[type]} [description]
	 */
	function createMask() {
		var objBody = document.getElementsByTagName("body").item(0);

		var objPopUp = document.createElement("div");
		objPopUp.setAttribute('id', 'mask');
		objPopUp.onclick = function() {
			this.style.display = "none";
			return false;
		}
		objPopUp.style.display = 'block';
		objPopUp.style.position = 'absolute';
		objPopUp.style.top = '0';
		objPopUp.style.left = '0';
		objPopUp.style.zIndex = '90';
		objPopUp.style.width = '100%';
		objPopUp.style.height = '100%';
		objPopUp.style.backgroundColor = "black";
		objBody.insertBefore(objPopUp, objBody.firstChild);
	}

	/**
	 * [createPopUpFrame 创建弹出窗口框架]
	 * @return {[type]} [description]
	 */
	function createPopUpFrame(){
		var objBody = document.getElementsByTagName("body").item(0);

		var objPopUp = document.createElement("div");
		objPopUp.setAttribute('id', 'popup');
		objPopUp.onclick = function() {
			this.style.display = "none";
			return false;
		}
		objPopUp.style.display = 'block';
		objPopUp.style.position = 'absolute';
		objPopUp.style.top = '0';
		objPopUp.style.left = '0';
		objPopUp.style.zIndex = '100';
		objPopUp.style.width = '300px';
		objPopUp.style.height = '200px';
		objPopUp.style.backgroundColor = "red";
		objBody.insertBefore(objPopUp, objBody.firstChild);
	}

	/**
	 * [fillContent 填充弹窗口内容]
	 * @return {[type]} [description]
	 */
	function fillContent(){
		var popupFrame = document.getElementById("popup");
		popupFrame.innerHTML = "Hello World!";
	}
	/**
	 * [closeMask description]
	 * @return {[type]} [description]
	 */
	function closeMask(){

	}

	/**
	 * [closePopUpFrame description]
	 * @return {[type]} [description]
	 */
	function closePopUpFrame(){

	}
	/**
	 * [addLoadEvent add window.onload function]
	 * @param {[type]} func [description]
	 */
	function addLoadEvent(func)
	{	
		var oldonload = window.onload;
		if (typeof window.onload != 'function'){
		  	window.onload = func;
		} else {
			window.onload = function(){
			oldonload();
			func();
			}
		}

	}
{% endhighlight %}
