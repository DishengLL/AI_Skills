## Batch Normalization
BN最为重要的作用是`加速了训练时，模型的收敛`，而防止过拟合算是BN的一个副产品  
BatchNormalization 有Google在2015年提出
1. 背景
在模型的训练中，输出数据无法保证每个batch都有相同的数据分布，这就造成了`internal Covariate Shift(ICS)`， 即因为输入数据有不通的分布，导致模型训练过程中输出数据的不断shift。  
在模型训练的过程中，可能导致每一个batch都要去适应数据分布shift带来的差异， 这加大了训练的难度。  
同时，由于存在激活函数，随着网络的加深，各层的推理输出结果会越来越趋向于大值，而这可能导致出现梯度饱和的现象（如sigmoid的两端）， 从而导致了模型优化缓慢。  
当加入BN后，缓解了激活函数陷入梯度饱和区。
综上，BN有效的提高了模型训练的速度和稳定性。
2. 定义
BN：针对每一个batch中的数据，对各个特征在batch范围中进行归一化处理。  
3. 效果分析  
   神经网络的各层之间具有依赖性， 底层输入的分布变化需要深层网络去不断的适应， 网络越深适应的难度越大，模型越难以训练。
   使用BN可以将数据进行归一化，增加的数据分布的稳定性，从而减少了网络各层之间的耦合性，**提升了模型的收敛效率**。 
   
   激活函数的非线性带来了梯度梯度爆炸和梯度消失的问题，这些问题是因为数据落在了激活函数的梯度饱和区。使用BN能将数据拉会到梯度不饱和区，得到有效的梯度，**提升模型收敛的效率**。
   
   间接进行了网络正则化， 提升了网络的鲁棒性（防止过拟合）  

## Reference
[Batch Normalization](https://mp.weixin.qq.com/s?__biz=MzAxMzgzOTc2NA==&mid=2652180716&idx=1&sn=a74fc2d81785af29fc6859e503a63232&chksm=807dcc17b70a450185a1cf0dc52278b8fa287698d9666cf99ca1be04bf72c630a123c521937c&cur_album_id=2379956886927622146&scene=189#wechat_redirect)  
[Application of BN](https://mp.weixin.qq.com/s?__biz=MzAxMzgzOTc2NA==&mid=2652180738&idx=1&sn=d9b09ad4eea987e80c84f9b0092d1422&chksm=807dcdf9b70a44ef14c9f6dd6140dfbf3d832a1b66d697bfbd4edbc38318c95571b97b832938&cur_album_id=2379956886927622146&scene=189#wechat_redirect)
