---
title: 二叉树学习笔记
date: 2024-04-28 14:42:31
tags: 
    - 学习
    - 数据结构
categories: 
    - 学习
    - 数据结构
top_img: http://gitee.com/TheUHO/blog/raw/master/images/202407212255291.jpg
cover: http://gitee.com/TheUHO/blog/raw/master/images/202407212255291.jpg
---

#### 树和二叉树
**2024.4.25 DS笔记**
| 目录跳转 |
| --- |
|[1. 树的结构](#section1)|
|[2. 树的储存结构](#section2)|
|[3. 二叉树](#section3)|
|[4. 二叉树的存储结构](#section4)|
|[5. 二叉树的遍历](#section5)|


<a id="section1"></a>
1. ##### 树的结构
    - **结点**：
        + **叶结点**：度为0的结点 *(终端结点)*；
        + **分支结点**：度非0的结点 *(非终端结点)*；
        + **结点的度**：结点子树的数目；
        <!--more-->
    - **结点间关系**：结点的子树的根称为该结点的孩子(child)，相应地，该结点称为孩子结点的父结点(或双亲，parent)同一个双亲的孩子之间互称兄弟;
    - **树的度**：结点度的最大值
    - **树的层次**：根结点为第一层，孩子结点依次加一；
    - **树的深度**：树中结点所处的最大层数；
    - **路径**：对于树中任意结点dj，若在树中存在一个结点序列d1，d2，…di，…，dj，使得di是di+1的双亲(1&le;i&lt;j)，则称该结点序列是从d1到dj的一条路径，路径的长度为j-1；
    - **树林**：m&ge;0 棵不相交的树组成的树的集合；
    - **树的有序性**：若树中结点的子树的相对位置不能随意改变, 则称该树为有序树，否则称该树为无序树；

<a id="sectio2"></a>

2. ##### 树的储存结构
    1. **多重链表结构** 
        + 定长结点的多重链表结构
        ![定长结点链表结构](https://gitee.com/TheUHO/blog/raw/master/images/202407221135093.png)
        + 不定长结点的多重链表结构
        ![不定长结点链表结构](https://gitee.com/TheUHO/blog/raw/master/images/202407221135092.jpg)
    2. **三重链表结构**
    ![三重链表结构](https://gitee.com/TheUHO/blog/raw/master/images/202407221135094.png)
<a id="section3"></a>

3. ##### 二叉树
    1.  <font color =#BB1C1C>二叉树</font>是 n &ge; 0个结点的有穷集合D与D上关系的集合R构成的结构，记为T，二叉树是有序树，区分左右子树；
    2. 两种特殊形态的二叉树
        + 满二叉树：二叉树中的结点,或者为叶结点， 或者具有两棵非空子树,并且叶结点都集中在二叉树的最下面一层；
        + 完全二叉树：二叉树中只有最下面两层的结点的度可以小于2，并且最下面一层的结点(叶结点)都依次排列在该层从左至右的位置上；
    3. 二叉树的性质
        * 具有n个结点的非空二叉树共有**n-1**个分支；
        * 非空二叉树的第 **i** 层最多有2<sup>i–1</sup>个结点( i &ge;1)；
        * 深度为 h 的非空二叉树最多有2<sup>h</sup> –1个结点；
        *  若非空二叉树有n<SUB>0</SUB>个叶结点,有n<SUB>2</SUB>个度为2的结点,则 n<SUB>0</SUB>=n<SUB>2</SUB>+1;
        * 具有n个结点的非空完全二叉树的深度为 h=&lfloor;log<SUB>2</SUB>n&rfloor;+1；
        * 若对具有n个结点的完全二叉树按照层次从上到下,每层从左到右的顺序进行编号, 则编号为i的结点具有以下性质:
            - (1) 当i=1,则编号为i的结点为二叉树的根结点；若i &gt;1,则编号为i 的结点的双亲的编号为&lfloor;i/2&rfloor;；
            - (2) 若2i&gt;n,则编号为i的结点无左子树; 若2i&le;n,则编号为i 的结点的左孩子的编号为2i；
            - (3) 若2i+1&gt;n,则编号为i 的结点无右子树; 若2i+1&le;n,则编号为i 的结点的右孩子的编号为 2i+1。
            ![图示](https://gitee.com/TheUHO/blog/raw/master/images/202407221135095.png)
    4. 二叉树的基本操作
        * <font color =#FF4500>INITIAL(T)</font> 初始(创建)一棵二叉树；
        * <font color =#FF4500>ROOT(T)</font> 求二叉树T的根结点, 或求结点x 所在二叉树的根结点；
        * <font color =#FF4500>PARENT(T,x)</font>  求二叉树T中结点x的双亲结点；
        * <font color =#FF4500>LCHILD(T,x)</font>或<font color =#FF4500>RCHILD(T,x)</font>  分别求二叉树T中结点x的左孩子结点或右孩子结点；
        * <font color =#FF4500> LDELETE(T,x)</font>或<font color =#FF4500> RDELETE(T,x)</font>   分别删除二叉树T中以结点x为根的左子树或右子树；
        * <font color =#FF4500>TRAVERSE(T)</font>  按照某种次序(或原则)依次访问二叉树T中各个结点，得到由该二叉树的所有结点组成的序列；
        * <font color =#FF4500>LAYER(T,x)</font> 求二叉树中结点x所处的层次；
        * <font color =#FF4500>DEPTH(T)</font> 求二叉树T的深度；
        * <font color =#FF4500>DESTROY(T)</font> 销毁一棵二叉树；
    5.  二叉树与树、树林之间的转换*
        * 树与二叉树的转换
            1) 在所有相邻的兄弟结点之间分别加一条连线；
            1) 对于每一个分支结点，除了其最左孩子外，删除该结点与其他孩子结点之间的连线；
            3) 以根结点为轴心，顺时针旋转45&deg;；
        ![图示](https://gitee.com/TheUHO/blog/raw/master/images/202407221135086.png)
        * 树林与二叉树的转换
            1) 分别将树林中每一棵树转换为一棵二叉树；
            2) 从最后那一棵二叉树开始，依次将后一棵二叉树的根结点作为前一棵二叉树的根结点的右孩子，直到所有二叉树都这样处理。这样得到的二叉树的根结点是树林中第一棵二叉树的根结点；
            ![图示](https://gitee.com/TheUHO/blog/raw/master/images/202407221135088.png)
        * 二叉树还原成树
            1) 若某结点是其双亲结点的左孩子，则将该结点的右孩子以及当且仅当连续地沿此右孩子的右子树方向的所有结点都分别与该结点的双亲结点用一根虚线连接；
            2) 去掉二叉树中所有双亲结点与其右孩子的连线；
            3) 规整图形(即使各结点按照层次排列),并将虚线改成实线；
<a id="section4"></a>

4. ##### 二叉树的存储结构
    1. 二叉树的顺序存储结构
        1) 完全二叉树的顺序存储结构：对于深度为h的完全二叉树, 将树中所有结点的数据信息按照编号的顺序依次存储到一维数组BT[0..2<sup>h</sup>-2]中,由于编号与数组下标一一对应，该数组就是该完全二叉树的顺序存储结构
        2) 一般二叉树的顺序存储结构：对于一般二叉树, 只须在二叉树中“添加”一些实际上二叉树中并不存在的“虚结点” (可以认为这些结点的数据信息为空)， 使其在形式上成为一棵“完全二叉树”，然后按照完全二叉树的顺序存储结构的构造方法将所有结点的数据信息依次存放于数组BT[0..2<sup>h</sup>-2]中；
    2. 二叉树的链式存储结构
         1) 二叉链表 `lchild` `data` `rchild` 分别表示左子树的指针域、数据域、右子树的指针域；
         ```c
        typedef struct _Node
        {
        ElemType data;
        struct _Node *lchild, *rchild;
        } BTNode, *BTNodeptr;
        ``` 
        ![图示](https://gitee.com/TheUHO/blog/raw/master/images/202407221135089.png)
            
        2) 二叉链表 `data` `parent` `lchild` `rchild` 分别表示数据域、双亲结点的指针域、左子树的指针域、右子树的指针域；
        ```c
        typedef struct _Node
        {
        ElemType data;
        struct _Node *parent, *lchild, *rchild;
        } BTNode, *BTNodeptr;
        ``` 
        ![图示](https://gitee.com/TheUHO/blog/raw/master/images/202407221135090.png)
<a id="section5"></a>

5. ##### 二叉树的遍历
    1. 常用的遍历方法：
        1) [<font color =#FF4500>前序遍历DLR</font>](#qianxubianli)
        1) [<font color =#FF4500>中序遍历LDR</font>](#zhongxubianli)
        1) [<font color =#FF4500>后序遍历LRD</font>](#houxubianli)
        1) [<font color =#FF4500>按层次遍历</font>](#cengcibianli)
    2. 前序遍历
    <a id="qianxubianli"></a>
        * 原则：若被遍历的二叉树非空, 则
            1. 访问根结点；
            2. 以前序遍历原则遍历根结点的左子树；
            3. 以前序遍历原则遍历根结点的右子树；
            ![图示](https://gitee.com/TheUHO/blog/raw/master/images/202407221135091.png)
            <font color =#3198FD>前序序列：</font><font color =#FF4500>A B D E C G H I F</font>
        * 递归算法
        ```c
        void preorder(BTNodeptr t)
        {
            if (t != NULL)
            {
                VISIT(t);//访问t结点
                preorder(t->lchild);
                preorder(t->rchild);
            }
        }
        ```

    2. 中序遍历
    <a id="qianxubianli"></a>
        * 原则：若被遍历的二叉树非空,则   
            1. 以中序遍历原则遍历根结点的左子树；
            2. 访问根结点；
            3. 以中序遍历原则遍历根结点的右子树；
            ![图示](https://gitee.com/TheUHO/blog/raw/master/images/202407221135091.png)
            <font color =#3198FD>中序序列：</font><font color =#FF4500>D E B A H G I C F
</font>
        * 递归算法
        ```c
        void inorder(BTNodeptr t)
        {
            if (t != NULL)
            {
                inorder(t->lchild);
                VISIT(t);//访问t结点
                inorder(t->rchild);
            }
        }
        ```
    2. 后序遍历
    <a id="qianxubianli"></a>
        * 原则：若被遍历的二叉树非空,则   
            1. 以中序遍历原则遍历根结点的左子树；
            2. 访问根结点；
            3. 以中序遍历原则遍历根结点的右子树；
            ![图示](https://gitee.com/TheUHO/blog/raw/master/images/202407221135091.png)
            <font color =#3198FD>中序序列：</font><font color =#FF4500>D E B A H G I C F
</font>
        * 递归算法
        ```c
        void inorder(BTNodeptr t)
        {
            if (t != NULL)
            {
                inorder(t->lchild);
                VISIT(t);//访问t结点
                inorder(t->rchild);
            }
        }
        ```