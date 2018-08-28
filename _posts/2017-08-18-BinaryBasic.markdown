---
layout:       post
title:        "生成基本的二叉树"
subtitle:     "生成基本的二叉树"
date:         2018-08-28 20:00:00
author:       "严冬"
header-mask:  0.3
catalog:      true
multilingual: true
tags:
    - Java
    - 刷题
---

**二叉树的分类和定义**

  * 一棵深度为k，且有2^k-1个节点的二叉树，称为满二叉树。
	这种树的特点是每一层上的节点数都是最大节点数。
	而在一棵二叉树中，除最后一层外，若其余层都是满的，并且最后一层或者是满的，
	或者是在右边缺少连续若干节点，则此二叉树为完全二叉树。
	具有n个节点的完全二叉树的深度为log2(n+1)。
	深度为k的完全二叉树，至少有2k-1个节点，至多有2k-1个节点
  * 满二叉树——除了叶结点外每一个结点都有左右子叶且叶子结点都处在最底层的二叉树。
  * 平衡二叉树——平衡二叉树又被称为AVL树（区别于AVL算法），它是一棵二叉排序树，且具有以下性质：它是一棵空树或它的左右两个子树的高度差的绝对值不超过1，并且左右两个子树都是一棵平衡二叉树。
  *完全二叉树——若设二叉树的高度为h，除第 h 层外，其它各层 (1～h-1) 的结点数都达到最大个数，第h层有叶子结点，并且叶子结点都是从左到右依次排布，这就是完全二叉树。
  
**主要是根据根节点的位置来确定什么遍历顺序**
  * 前序:先遍历根节点，再次遍历左节点，然后遍历右节点
  * 后序:先遍历左节点，然后遍历右节点，最后遍历根节点
  * 中序:先遍历左节点，然后遍历根节点，然后遍历右节点
	所谓的数据结构不过是不同的数据存储方式而已，数据总归要有一种方式来进行存储，这就造就了各种各样的数据结构

	
```
package com.zyd.test;

public class BinaryTreeDemo {
/*
 *      A  
   B          C  
D     E            F  
 X  M   N  

 * */	
	private  TreeNode root=null;
	BinaryTreeDemo(){
		root=new TreeNode(1,"A");
	}
	//二叉树的建立
	void createBinaryTree(TreeNode root){
		TreeNode newNodeB=new TreeNode(2,"B");
		TreeNode newNodeC=new TreeNode(3,"C");
		TreeNode newNodeD=new TreeNode(4,"D");
		TreeNode newNodeE=new TreeNode(5,"E");
		TreeNode newNodeF=new TreeNode(6,"F");
		TreeNode newNodeM=new TreeNode(7,"M");
		TreeNode newNodeN=new TreeNode(8,"N");
		root.leftchild=newNodeB;
		root.rightchild=newNodeC;
		root.leftchild.leftchild=newNodeD;
		root.leftchild.rightchild=newNodeE;
		root.rightchild.rightchild=newNodeF;
		root.leftchild.rightchild.leftchild=newNodeM;
		root.leftchild.rightchild.rightchild=newNodeN;
        root.leftchild.leftchild.rightchild= new TreeNode(9,"X");  
	}
	
	public void visited (TreeNode treeNode){
		treeNode.isVisted=true;
		System.out.println("key:="+treeNode.key+"data:"+treeNode.data);
	}
	//二叉树递归前序遍历
	public void preOrder(TreeNode treeNode){
		if(treeNode !=null){
			visited(treeNode);
			preOrder(treeNode.leftchild);//通过递归进行去循环左子树
			preOrder(treeNode.rightchild);//通过递归进行调用有子树
		}
		
	}
	//二叉树递归中序遍历
	public void middleOrder(TreeNode treeNode){
		if(treeNode !=null){
		middleOrder(treeNode.leftchild);
		visited(treeNode);
		middleOrder(treeNode.rightchild);
		}
	}
	//二叉树递归后序遍历
	public void laterOrder(TreeNode treeNode){
		if(treeNode !=null){
		laterOrder(treeNode.leftchild);
		laterOrder(treeNode.rightchild);
		visited(treeNode);
		}
	}
	public static void main(String[] args) {
		//在静态的方法不能调用非静态的方法，静态代码块先加载，当前类没有被初始化，，
		BinaryTreeDemo binaryTree=new BinaryTreeDemo();
		binaryTree.createBinaryTree(binaryTree.root);
		System.out.println("前序遍历---------------");
		binaryTree.preOrder(binaryTree.root);
		System.out.println("后序遍历---------------");
		binaryTree.laterOrder(binaryTree.root);
		System.out.println("中序遍历---------------");
		binaryTree.middleOrder(binaryTree.root);
	}
	
}
package com.zyd.test;

//一个基本的二叉树节点的建立
public class TreeNode {
	int key;//节点的编号
	String data;//节点存储的数据
	TreeNode leftchild;//左节点
	TreeNode rightchild;//右节点
	boolean isVisted=false;//是否允许查看
	public TreeNode(int key, String data, TreeNode leftchild,
			TreeNode rightchild, boolean isVisted) {
		this.key = key;
		this.data = data;
		this.leftchild = leftchild;
		this.rightchild = rightchild;
		this.isVisted = isVisted;
	}
	
	public TreeNode() {
		
	}
	
	public TreeNode(int key) {
	
		this.key = key;
	}

	public TreeNode(int key, String data) {
		this.key = key;
		this.data = data;
	}
	

}


```

