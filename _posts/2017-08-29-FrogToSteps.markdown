---
layout:       post
title:        "基于斐波那契数列的台阶问题"
subtitle:     "基于斐波那契数列的台阶问题"
date:         2018-08-29 20:00:00
author:       "严冬"
header-mask:  0.3
catalog:      true
multilingual: true
tags:
    - 剑指offer
    - Java
    - 刷题
---

**青蛙台阶问题**

	一只青蛙一次可以跳上1级台阶，也可以跳上2级。
	求该青蛙跳上一个n级的台阶总共有多少种跳法（
	先后次序不同算不同的结果）
	
**解题思路应该充分运用 斐波那契数列使用**
  * 斐波那契数列指的是这样一个数列，这个数列从第3项开始，每一项都等于前两项之和。即f(n)=f(n-1)+f(n-2)
  * 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144, 233，377，610，987，1597，2584，4181，6765，10946，17711，28657，46368.
  * 根据索引值去遍历 中序序列,前序序列（不管如何遍历切记，根节点下的左右子树下面节点数一定，这是根据索引去遍历的依据），
  * 问题最小化，青蛙想到达i层台阶，两种方式要么是从i-1阶跳，要么从i-2阶跳跳方式是固定的
  * 在多层也是两种方式重复而来，从上到下的递归，一直到可计算的范围内，然后得出最后的值
  * 切记递归的核心思想是充分利用事件的规律性，然后从上到下，寻找递归的尽头，也就最开始的初始值，不然递归毫无意义，也得不到想要的值

```
public class FrogToSteps {

	public static void main(String[] args) {
		
		System.out.println("共有几种跳法"+JumpFloor(3));
	}
	public  static int JumpFloor(int target) {
		
		if(target<0)
			return 0;
		int[] str={0,1,2};
		if(target<3)
		return str[target];
		
		return JumpFloor( target-1)+JumpFloor(target-2);

    }
	
}

```

