---
layout: post
title: "窗口滚动条的位置"
description: "窗口滚动条的位置"
category: "note"
tags: [javascript, offset]
---
{% include JB/setup %}

## 获取窗口滚动条的位置

{% highlight javascript %}

/**
 * [ 查看滚动条位置]
 * @param  {[type]} w [description]
 * @return {[type]}   [description]
 */
function getScrollOffsets(w){

    w = w || window;

    //IE8+ + W3C
    if(w.pageXOffset != null){
        return {
            x: w.pageXOffset,
            y: w.pageYOffset
        };
		}
	
    var d = w.document;
    //IE标准模式 + W3C
    if(d.compatMode = "CSS1Compat"){
        return{
            x: d.documentElement.scrollLeft,
            y: d.documentElement.scrollTop,
        };
    }

    //怪异模式
    return {
        x: d.body.scrollLeft,
        y: d.body.scrollTop
    };

}

{% endhighlight %}
