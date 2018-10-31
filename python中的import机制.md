# python中的import机制
在学习tensorflow时发现，下面这段程序会提示出错
```
import tensorflow
model = keras.Sequential()
```
作为一个小白，想当然以为import tensorflow后，tensorflow下的所有模块都可以直接调用了，但其实python中是存在命名空间的，上面只是把tensorflow加入到命名空间中，正确使用方式如下
```
import tensorflow
model = tensorflow.keras.Sequential()
```
当然，也可以通过from ... import ... 来把keras加入到命名空间中
```
from tensorflow import keras
model = keras.Sequential()
```
还有种不太常见的写法
```
import tensorflow.keras
model = tensorflow.keras.Sequential()
```
有时也会见到from A import *这种方法，但不太推荐，因为这样会把A下面的所有模块和函数都加入命名空间中，容易导致程序出错

还有一点，import后只能加模块名，而from...import...后可以加模块名也可以加函数名
