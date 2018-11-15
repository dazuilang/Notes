# buffer_size参数的意义
shuffle()是tensorflow中用来打乱数据集顺序的函数，函数原型如下
```
shuffle(
    buffer_size,
    seed=None,
    reshuffle_each_iteration=None
)
```
buffer_size是其中一个参数，起初我并不太理解它的意义，官方文档中介绍如下

> buffer_size: A tf.int64 scalar tf.Tensor, representing the number of elements from this dataset from which the new dataset will sample.

首先，Dataset会取所有数据的前buffer_size数据项填充 buffer，然后每次从buffer中随机抽取一条数据输出，再从Dataset中选取一条填充到buffer中，理论上buffer_size越大，随机性就越高，而buffer_size为1则变成了顺序排列。
