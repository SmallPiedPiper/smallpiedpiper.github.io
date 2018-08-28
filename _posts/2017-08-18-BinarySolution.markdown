---
layout:       post
title:        "二叉树没毛病"
subtitle:     "二叉树没毛病"
date:         2018-08-28 20:00:00
author:       "严冬"
header-mask:  0.3
catalog:      true
multilingual: true
tags:
    - 剑指offer
    - Java
    - 刷题
---

**二叉树没毛病**

	输入某二叉树的前序遍历和中序遍历的结果，请重建出该二叉树。
	假设输入的前序遍历和中序遍历的结果中都不含重复的数字。
	例如输入前序遍历序列{1,2,4,7,3,5,6,8}和中序遍历序列{4,7,2,1,5,3,8,6}，
	则重建二叉树并返回
	
**解题思路应该充分运用 递归调用的思路使用**
  * 已知没有重复数字可以利用前序遍历中第一个值就是是根节点，得到中序序列里面的索引值。
  * 根据索引值去遍历 中序序列,前序序列（不管如何遍历切记，根节点下的左右子树下面节点数一定，这是根据索引去遍历的依据），
  * 找到根节点从而得到根节点的左右子树的两部分
  * 去递归上述两个步骤，每次得到一个根节点（子树里面暂且也叫根节点）
  * 最后可以拿到最后的所有节点

```
package com.zyd.test;

public class GetBinary {
	
	public TreeNode reConstructor(int [] pre,int [] in){
		TreeNode root=new TreeNode(pre[0]);//拿到根节点的值
		int length=pre.length;
		if(length==1)//仅仅只有一个根节点的情况
		{
			root.rightchild=null;
			root.leftchild=null;
			return root;
		}
		int rootCode=root.key;
		int i;
		//去遍历中序节点，找到根节点，从而找到左右子树的分界点
		for(i=0;i<length;i++)
		{
			if(rootCode==in[i])
			break;
		}
		//然后对左子树进行中序和前序的遍历
		if(i>0)
		{
			int [] pre_left=new int[i];
			int [] in_left=new int[i];
			for(int j=0;j<i;j++)
			{
				pre_left[j]=pre[j+1];
				
			}
			for(int j=0;j<i;j++)
			{
				in_left[j]=in[j];
			}
			root.leftchild=reConstructor(pre_left, in_left);
		}
		else
		{
			root.leftchild=null;
		}
		//对右子树进行中序和前序的遍历
		if(length-i-1>0){
			int [] pre_right=new int[length-i-1];
			int [] in_right=new int[length-i-1];
			for(int j=i+1;j<length;j++)
			{
				pre_right[j-i-1]=pre[j];
				in_right[j-i-1]=in[j];
				
			}
			
			root.rightchild=reConstructor(pre_right, in_right);
		}
		else {
			root.rightchild=null;
		}
		
		return root;
	}
	
	public static void main(String[] args) {
	
		GetBinary getBinary=new GetBinary();
		int [] pre=new int[]{1,2,4,7,3,5,6,8};
		int [] in= new int[]{4,7,2,1,5,3,8,6};
		TreeNode root=getBinary.reConstructor(pre,in);
		BinaryTreeDemo binary=new BinaryTreeDemo();
		binary.preOrder(root);
		binary.middleOrder(root);
}

}
```

