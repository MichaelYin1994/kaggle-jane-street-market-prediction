### 2020  Kaggle Jane-Street金融回报预测竞赛

---
### 队伍简介
队名：GradientBoostingTeam，队长：鱼丸粗面(zhuoyin94@163.com)。复赛流测评最高排名：136/4345（Silver，20210621），20201226开赛。

---
### 方案简介

本方案延续了开源策略中评分最高的方法：在历史交易数据上用Denoising Autoencoder进行预训练，然后在下游任务上进行fine-tune。不同的是，我们修正了开源方案中利用未来数据预训练的bug，严格执行了按时间顺序的预训练策略。

特征工程方面，主要采取了Stream features[6]与基础特征选择方法结合的方式，选取模型的输入特征。

推理加速方面，对训练好的NN模型采取了混合精度量化的策略[3]；训练策略方面，采取时序交叉验证策略进行模型训练。

提交方面，我们采用了一种简单的模型预测概率融合策略，详情见实时推理代码。

到目前为止（4个月测评），我们的平均排名大概在150名左右，位于银牌区。

---
### References

[1] https://www.kaggle.com/gogo827jz/optimise-speed-of-filling-nan-function

[2] https://www.kaggle.com/gogo827jz/jane-street-ffill-xgboost-purgedtimeseriescv

[3] https://medium.com/@micwurm/using-tensorflow-lite-to-speed-up-predictions-a3954886eb98

[4] https://www.kaggle.com/c/jane-street-market-prediction/discussion/199107

[5] https://www.kaggle.com/c/jane-street-market-prediction/overview/evaluation

[6] https://www.kaggle.com/lucasmorin/running-algos-fe-for-fast-inference