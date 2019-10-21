# tensorflow中的切片

其实我还是第一次知道python中有省略号，算是一个语法糖吧

```
a = tf.random.normal([2, 4, 28, 28, 3])
a.shape
```

TensorShape([2, 4, 28, 28, 3])

```
a[0].shape
```

TensorShape([4, 28, 28, 3])

```
a[0, :, :, :, :].shape
```
TensorShape([4, 28, 28, 3])

```
a[0, ...].shape
```

TensorShape([4, 28, 28, 3])

```
a[:, :, :, :, 0].shape
```

TensorShape([2, 4, 28, 28])

```
a[..., 0].shape
```
TensorShape([2, 4, 28, 28])

```
a[0, ..., 2].shape
```
TensorShape([4, 28, 28])

```
a[1, 0, ..., 0].shape
```
TensorShape([28, 28])
