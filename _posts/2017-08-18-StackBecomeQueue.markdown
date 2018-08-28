---
layout:       post
title:        "两个堆变成队列"
subtitle:     "两个堆变成队列"
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
**两个堆变成队列**

	队列:队列是一种特殊的线性表，
	特殊之处在于它只允许在表的前端（front）进行删除操作，
	而在表的后端（rear）进行插入操作，和栈一样，队列是一种操作受限制的线性表。
	进行插入操作的端称为队尾，进行删除操作的端称为队头。
	栈:栈（stack）又名堆栈，它是一种运算受限的线性表。其限制是仅允许在表的一端进行插入和删除运算。
	这一端被称为栈顶，相对地，把另一端称为栈底。
	向一个栈插入新元素又称作进栈、入栈或压栈，它是把新元素放到栈顶元素的上面，使之成为新的栈顶元素；
	从一个栈删除元素又称作出栈或退栈，它是把栈顶元素删除掉，使其相邻的元素成为新的栈顶元素。
	用两个栈来实现一个队列，完成队列的Push和Pop操作。 队列中的元素为int类型
** 思路 ** 

  *	用Stack1来进行入栈操作，Stack2进行出栈操作
  *	要能保持住Stack2始终有数据，（注意:只要把栈1栈顶数据压在栈2的栈低，就满足队列的先进先出的特性）
  *	采取的方法是当Stack2为空的时候，将Stack1的数据全部压入进去，等待出栈即可
	 
```
package com.zyd.test;
import java.util.Stack;
public class StackDemo {
    Stack<Integer> stack1 = new Stack<Integer>();
    Stack<Integer> stack2 = new Stack<Integer>();
    
    public void push(int node) {
        
    	stack1.push(node);//将数据入栈
    }
    
    public int pop() {
    	Integer result=null;
    	if(stack2.empty()){
    		while(!stack1.empty()){
    			result=stack1.pop();
    			stack2.push(result);//最先进入栈1的要在栈2的最上面
    		}
    	}
    	result=stack2.pop();//按照正常的出栈顺序就可以
		return result;
    
    }
}
```

