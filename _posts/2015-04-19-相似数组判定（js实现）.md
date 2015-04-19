---
published: true
title: 相似数组判定
layout: post
author: Yu
categories: [articles]
tags: 
  - js
  - 算法
  - 数据类型
---
#题目
请在index.html文件中，编写arraysSimilar函数，实现判断传入的两个数组是否相似。

具体需求：

* 数组中的成员类型相同，顺序可以不同。例如[1, true] 与 [false, 2]是相似的
* 数组的长度一致
* 类型的判断范围，需要区分:String, Boolean, Number, undefined, null, 函数，日期, window

当以上全部满足，则返回"判定结果:通过"，否则返回"判定结果:不通过"。

代码实现：
	```java
	/*
	* param1 Array
	* param2 Array
	* return true or false
	*/

	function arraysSimilar(arr1, arr2){
	    var type = function(p){
	        if(p === null){
	            return "null";
	        }
	        var types = {
	            'function':Function,
	            'window':Window,
	            'date': Date,
	            'array': Array
	        };
	        for(var t in types){
	            if (p instanceof types[t]){
	                return t;
	            }
	        }
	        //undifined,boolean,string,number,object
	        return typeof p;
	    };
	    if(!(arr1 instanceof Array && arr2 instanceof Array)
	        || arr1.length !== arr2.length){
	        return false;
	    }
	    var a1 = [],a2 = [];
	    for(var i in arr1){
	        a1[i] = type(arr1[i]);
	        a2[i] = type(arr2[i]);
	    }
	    return JSON.stringify(a1.sort())===JSON.stringify(a2.sort());
	}

    /*
    a1 = a1.sort();
    a2 = a2.sort();
    for(var i in a1){
        if(a1[i] !== a2[i]){
            return false;
        }
    }
    return true;
    */
	```
