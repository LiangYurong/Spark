Usercf-based collaborative filtering algorithm


算法核心思想：在一个在线推荐系统中，当用户A需要个性化推荐时，可以先找到和他有相似兴趣的其它用户，然后把那些用户喜欢的、而用户A没有听说过的物品推荐给A，这种方法称为基于用户的协同过滤算法。

可以看出，这个算法主要包括两步：
1. 找到和目标用户兴趣相似的用户集合——计算两个用户的兴趣相似度
2. 找到这个集合中的用户喜欢的，且目标用户没有听说过的物品推荐给目标用户——找出物品推荐

python: https://github.com/Angelinaa/movie_userCF

reference link： https://blog.csdn.net/moakun/article/details/80704562
