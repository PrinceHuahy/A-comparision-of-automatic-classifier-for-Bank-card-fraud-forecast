# -
在今天的数字世界，每天有数万亿的银行卡交易发生，检测欺诈行为的发生 是一个严峻挑战。该数据来自一些匿名的数据采集机构，数据共有七个特征和一列类标签。本文用包括LogisticRegression、KNN、Randomforest等多种分类器解决该问题。

特征：
distance_from_home：银行卡交易地点与家的距离；


distance_from_last_transaction：与上次交易发生的距离；

ratio_to_median_purchase_price：近一次交易与以往交易价格中位数的比率；

repeat_retailer：交易是否发生在同一个商户；

used_chip：是通过芯片（银行卡）进行的交易；

used_pin_number：交易时是否使用了PIN 码；

online_order：是否是在线交易订单；

标签：
fraud：诈骗行为（分类标签）；

解决问题：
1) 使用多种用于数据挖掘的机器学习模型对给定数据集进行建模；
2) 对样本数据进一步挖掘分析，通过交叉验证、网格调优对不同模型的参
数进行调整，寻找最优解，将多个最优模型进行进一步比较；
3) 通过对precision（预测精度）、recall（召回率）、f1-score（F1 分
数值）进行计算，给出选择某一种预测模型的理由；
4) 将模型性能评价通过多种作图方式进行可视化。

本项目主要分为三部分代码：数据预处理、模型训练、模型评估。
在数据预处理部分，进行了异常值检验、缺失值检查、归一化、标准化等操作，并通过箱线图、直方图、qq图等多种可视化方式观察数据特征。

在模型训练部分，我们使用5折交叉验证以及网格搜索，训练了多种分类器并寻找最优参数。与此同时，将训练好的数据保存（load）成pkl文件。在这一部分中，我们训练了"LogisticRegression","RandomForestClassifier","KNN","DecisionTreeClassifier","GradientBoostingClassifier","AdaBoostClassifier","GaussianNB","QuadraticDiscriminantAnalysis","MultinomialNB"分类器。

在模型评估部分，我们使用了多种指标对每个模型进行评估，这些指标包括：train_auc, test_auc,特异度specificity,召回率recall,精度precison,f1,约登指数youden,mcc,kappa,阴性预测值npv,阳性预测值ppv,阳性似然比plr,阴性似然比nlr。与此同时，我们画出了每个模型的ROC曲线，并且跳出了最好的模型：GradientBoostingClassifier，可视化了该模型的混淆矩阵。
