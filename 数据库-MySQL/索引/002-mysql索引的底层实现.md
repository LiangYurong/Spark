
### 基础

底层是B+树

### 哪些数据结构可以加快查询？

哈希表。精确查询快；不支持范围查询，比如while id>1;

平衡二叉树

B树

B+树

### 为什么要使用B+树存放索引？

因为B+树的高度很低，查询的时候磁盘IO次数就会少。B+树存千万级别的数据，只要三到五层就可以了。

平衡二叉树，红黑树。如果数据量大的话，树的高度会很高，磁盘io会很多次。

Hash索引，精确查询很快，但是不支持范围查询。


