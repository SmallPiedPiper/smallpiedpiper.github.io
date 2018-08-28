---
layout:       post
title:        "二维数组之间复制时间的比较"
subtitle:     "二维数组之间复制时间的比较"
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
**二维数组之间复制时间的比较**	

  *	结论：System.arraycopy(4196)<clone(5593)<Arrays.copyOf(36824)<for(47079)
  *源码没有来的及看
	 
```
package com.zyd.test;

import java.util.Arrays;

public class ArrayTest {

	public static void main(String[] args) {
		int [] a=new int[500];
		
		for(int j=0;j<500;j++)
		{
			a[j]=j;
		}
		
		int []b=new int [500];
		Long startTime=System.nanoTime();
		for(int i=0;i<a.length;i++)
		{
			b[i]=a[i];
		}
		Long endTime=System.nanoTime();
		System.out.println(b.toString());
		System.out.println("for循环进行赋值进行使用的时间"+(endTime-startTime));
	
		//一维数组之间的赋值
		int []d=new int [500];
		Long startTime1=System.nanoTime();
		System.arraycopy(a, 0, d, 0, 100);
		Long endTime1=System.nanoTime();
		System.out.println(d.toString());
		System.out.println("System.arraycopy循环进行赋值进行使用的时间"+(endTime1-startTime1));
	
		//Arrays.copyOf返回的是一个新的数组对象
		Long startTime2=System.nanoTime();
		int[] c=Arrays.copyOf(a, 100);
		Long endTime2=System.nanoTime();
		System.out.println(c.toString());
		System.out.println("Arrays.copyOf进行赋值进行使用的时间"+(endTime2-startTime2));
		
		//
		int []e=new int [500];
		Long startTime3=System.nanoTime();
		e=a.clone();
		Long endTime3=System.nanoTime();
		System.out.println(e.toString());
		System.out.println("clone进行赋值进行使用的时间"+(endTime3-startTime3));
	}
}

```

