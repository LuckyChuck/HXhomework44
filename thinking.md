# Thinking1	在实际工作中，FM和MF哪个应用的更多，为什么 #
答：FM会更多，因为MF只有user 和 item 两个维度，而在实际过程中，推荐的维度会很多，MF已经不能够满足需要了。而Fm是特征之间两两进行组合。可以说MF是FM的一个只有两个特征的特例。
在推荐系统中，影响结果的维度肯定不能是唯一的，所以Fm从一定意义上，是更符合现实情况的，效果也会更好。


# Thinking2	FFM与FM有哪些区别？ #

答：FFM相较于FM引入了场的概念，对于FM说，每个特征都有一个隐向量，而FFM来说，是每个特征有多个个隐向量。所以FFM在一定程度上计算的粒度更细。在时间复杂度上，FFM高于FM，运算时间更长。


# Thinking3	DeepFM相比于FM解决了哪些问题，原理是怎样的 #

答：虽然理论上FM可以对高阶特征组合进行建模，但实际上因为计算复杂度原因，一般都只用到了二阶特征组合，而deepFM处理了对于D阶的处理。deepfm = fm + DNN。DeepFM目的是同时学习低阶和高阶的特征交叉，主要由FM和DNN两部分组成，底部共享同样的输入。、


# Thinking4	Surprise工具中的baseline算法原理是怎样的？BaselineOnly和KNNBaseline有什么区别？ #

答：baseline算法：基于统计的基准预测线打分
bui 预测值
bu 用户对整体的偏差
bi 商品对整体的偏差

bui = mu + bu + bi
Baseline模型虽然简单， 但其中其实已经包含了用户和item的个性化信息。在面对大规模数据时， 简单算法能够减少大量的计算时间。 

KNNBaseline,考虑到用户打分的偏差，偏差计算时使用baseline
在KNNWithMeans基础上，用baseline替代均值


# Thinking5	基于邻域的协同过滤都有哪些算法，请简述原理 #

答：主要分为userCF和itemCF
UserCF: 推荐和当前用户相似度高的N个用户产生过行为的物品给当前用户
ItemCF: 推荐和当前用户历史上行为过的物品相似的物品给当前用户(可解释性强)
用户数远大于物品数时，使用采用ItemCF；用户数少于物品数时，使用UserCF更准确
如果物品列表经常变换，那么采用UserCF更准确；如果物品列表相对于用户更稳定，那么采用ItemCF
在冷启动阶段，UserCF对于新加入的物品能很快进入推荐列表，ItemCF对新加入的用户可以很快进行推荐






