---
layout:       post
title:        "二维数组的查找"
subtitle:     "二维数组的查找"
date:         2018-08-28 19:00:00
author:       "严冬"
header-mask:  0.3
catalog:      true
multilingual: true
tags:
    - 剑指offer
    - Java
    - 刷题
---
**二维数组的查找**

  在一个二维数组中（每个一维数组的长度相同），每一行都按照从左到右递增的顺序排序
  * 每一列都按照从上到下递增的顺序排序
  * 请完成一个函数，输入这样的一个二维数组和一个整数，判断数组中是否含有该整数

**思路**
  *	由于这个数组具有一定的规律性，不一定要按照平常的方式进行遍历
  * 从数组的右上角开始遍历最为快速，右上角第一行第一列开始遍历，如果第一行第一列第一个就大于目标值，便跳过去，开始第二行第二列，以此类推
  
	 
```
public boolean Find(int target, int [][] array) {

	        int row=array.length;
	        int col=array[0].length;
	        int i=0;
	        int  j=col-1;
	        while(j>=0&&i<row){
	            if(array[i][j]>target){ 
	                //循环行
	                j--;
	                continue;
	            }
	            else if(array[i][j]<target)
	            {        
	                i++;
	                continue;
	            }
	            else{
	                return true;
	            }
	        }
	        return false;
	    }
	  
```

