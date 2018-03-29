# yan_cheng_shang_pai_shu_liang

 本人参加阿里云天池“印象盐城·数创未来大数据竞赛 - 盐城汽车上牌量预测”的源码，
 比赛链接https://tianchi.aliyun.com/competition/introduction.htm?spm=5176.100150.711.6.67bc20096sfJGU&raceId=231641
 用juperty notebook编写的，anaconda3环境

1.开始是我是按照A榜提交数据对测试数据进行处理，只保留data、day_of_week、cnt三项，然后按照day_of_week对数据分组，然后分别套模型，主要是用KNN、随机森林和XGBOOST，随后把数据整合在一起，测试数据集的MSE是30多万，但实际上线测出了MSE是150多万，差距太大，所以换了个思路。

2.中间尝试过ARMA模型，用的facebook的prophet模型，还是按day_of_week，不过实际效果还是不行。

3.最后尝试用brand进行分类，考虑到有些日期某个品牌无上牌量，所以用0值进行填充，选了线性回归、随机森林、决策时、adaboost、Xgboost五个模型，生成对应的预测值LR_brand、RF_brand、DT_brand、XGB_brand、ADA_brand，而后用data、day_of_week进行goupby，最后用date、day_of_week、LR_brand、RF_brand、DT_brand、XGB_brand、ADA_brand几个作为输入项，用Xgboost模型算出x1项作为最后的预测项目。

