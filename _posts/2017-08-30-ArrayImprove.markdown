---
layout:       post
title:        "数组奇偶重组"
subtitle:     "数组奇偶重组"
date:         2018-08-30 20:00:00
author:       "严冬"
header-mask:  0.3
catalog:      true
multilingual: true
tags:
    - 剑指offer
    - Java
    - 刷题
---

**数组奇偶重组**

  输入一个整数数组，实现一个函数来调整该数组中数字的顺序，
  如果要保证奇数和奇数，偶数和偶数之间的相对位置不变。
	
**解题思路应该充分运用 斐波那契数列使用**
  *处分运用将有一到多的平行移动，然后奇数的跳跃式移动，吸收了插入排序的优点，
  *首先寻找第一个奇数，并将其放在数组最前面的位置。然后将第一个奇数之前的元素全部往后移一位。
  *依次在第一个奇数之后的元素中寻找奇数，并做移动操作。就可以保证原来的相对顺序。


```
public class ArrayOrder {

	  public static void main(String[] args) {
	        int []array = {2,4,6,1,3,5,7};
	        reOrderArray2(array);
	        for(int i=0;i<array.length;i++)
	        {
	            System.out.print(array[i]+" ");
	        }
	    }
	    public static void reOrderArray2(int []array)
	    {
	    	//记录第一个为奇数的位置
	        int j=0;
	        for(int i=0;i<array.length;i++)
	        {    
	            if(array[i]%2==1)//找到奇数
	            {
	                int temp = array[i];//记录奇数
	                int ti=i;
	                for(;ti>j;ti--)
	                {
	                    array[ti]=array[ti-1];//将奇数之前的所有元素往后移一个位置
	                }
	                array[j] = temp;//将奇数直接复制到数组前面
	                j=j+1;//随着数字的增加，前面数组的长度变得越来越长
	            }
	        }
	        
	        
	        
	        
	    }
}

```

