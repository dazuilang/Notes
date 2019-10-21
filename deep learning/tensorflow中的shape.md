# tensorflow中的shape
tensorflow中的shape表示tensor的维度

[1,2]的shape值(2,)，意思是一维数组，数组中有2个元素

[[1],[2]]的shape值是(2,1)，意思是一个二维数组，每行有1个元素

[[1,2]]的shape值是(1，2)，意思是一个二维数组，每行有2个元素

如果不确定输入的tensor的维度，可以用None来代替，如[None,None,3]
