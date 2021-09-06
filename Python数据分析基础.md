### Python数据分析基础

#### 1 Jupyter notebook的使用

使用anacanda promt进入项目目录，使用jupyter notebook

- [ ] ```python
  import numpy as np`
   a=np.arange(10)`
   print(a)
   
  ```

#### 2 numpy

性能高，做科学计算很好

##### 2.1 numpy数组的创立

- [ ] ```python
  import numpy as np //numpy中的数组的数据类型必须一致 
  a=[1,2,3,'4']
  print(a)
  b=np.array([4,5,6])
  print(b)
  #### 1 使用np.array来创建数组
  a=np.array([1,2,2])
  print(type(a))
  #### 2 使用np.arange创建数组
  b=np.arange(0,10,2)//2表示步长
  #### 3 np.random来生成随机数的数组
  c=np.random.random((2,2))//生成两行两列的数组
  c1=np.random.randint(0,9,size(3,4))//使用randomint指定数据范围0—9,
  //3行3列
  ### 4 特殊函数np.zeros((n,m)),np.ones((n,m),)np.full((n,m),3),np.eye(n)
  np.zeros((3,3))//全是0的矩阵3行3列矩阵
  np.ones((n,m))//全是1的矩阵
  np.full((n,m),K)//全是K的矩阵
  np.eye(n)//对角线为1的n阶矩阵
  
  ```

##### 2.2numpy的数据类型

dtype数据类型

- [ ] ```python
  ## dtype数据类型
  a=np.arange(0,10)
  print(a.dtype)
  b=np.array([1,2,3],dtype=np.float16)
  print(b)
  print(b.dtype)
  ### astype修改数据类型
  f=b.astype("U")
  print(uf.dtype)
  print(f.dtype)
  ```

##### 2.3多维数组操作

- [ ] ```python
  import numpy as np
  a1=np.array([1,2,3])
  print.(a1.ndim)
  a2=np.array([[1,2,3],[4,5,6]])##二维数组
  print.(a2.ndim)
  a3=np.array([[[1,2,3],[4,5,6]],[[7,8,9],[10,11,12]]])##三维数组
  print.(a3.ndim)
  print(a.shape)##查看数组的形状
  ###reshape重塑数组形状
  a4=a3.reshape((2,6))
  ###装换一维数组
  ##a5=a3.reshape((1,12))
  a5=a3.reshape(12,)
  ##采用flatten来装换为一维数组
  a6=a3.flatten()
  print(a6)
  ###数组元素的获取
  count=a3.size
  print(count)
  
  ```

##### 2.4 Numpy数组索引和切片

- [ ] ```python
  import numpy as np
  ###一维数组的索引和切片
  a1=np.arange(10)
  #进行索引操作
  print(a1[4])
  #进行切片操作
  print(a1[4:6])
  #使用等步长
  print(a1[::2])
  #使用负数来做索引
  print(a1[-1])
  ####多维数组的索引和切片
  ##使用中括号来索引和切片，使用逗号进行分割，逗号前面是行，逗号后面是列。如果只有一个值那么那个值是行。
  a2=np.random.ranint(0,10,size=(4,6))
  print(a2)//得到一个四行六列的数组
  a2[0]//得到第一行的数组的值
  a2[1:3]//得到第二行和第三行的值
  a2[[0,2,3]]//获取第0,2,3行的数据
  ###获取某行某列的数据
  a2[1,2]//获取第一行第二列的数据
  a2[[1,2],[4,5]]//获取到第一行第四列和第二行第五列的数据
  a2[1:2,4:6]//获取
  ###获取某一列的数据
  a2[:1]获取第一列的数据
  ##布尔索引
  a2=np.arange(0,24).reshape(4,6)
  print(a2)//提取小于10的数据
  a2<10
  a2[a2<10]//获取a2小于10的数
  a2[(a2<5)|(a2>7)]//获取大于7或者小于5的数据
  ###数组值的替换
  a3=np.random.ranint(0,10,size=(4,6))
  a3[1]=0//将第一行的值替换为0
  a3[1]=np.array([1,2,3,4,6,7])//将第一行的值替换为1，2,3,4，6,7
  a3[a3<3]=1//将a3中的值小于3的替换为1
  ###使用where函数来进行值的替换
  result=np.where(a3<5)//小于5的坐标值
  result
  result = np.where(a3<5,0,1)//表示a3中的小于5的替换成0大于0的替换成1
  
  
  ```

##### 2.5numpy的广播机制

- [ ] ```python
  ###数组和数的计算
  import numpy as np
  a1=np.random.randint(0,5,size(3,5))
  a1*2//
  ###数组和数组之间的运算
  a2=np.random.randint(0,5,size(3,5))
  a1+a2  //可以运算
  a3=np.random.randint(0,5,size(3,4))
  a1+a3//不能运算，shape不一致
  a4=np.random.randint(0,5,size(3,1))
  a1+a4//可以运算，行数相同，列数只有一列，列数相同，行数只有一列同样可以运算。
  
  ```

##### 2.6numpy数组形状操作

- [ ] ```python
  ###reshape，resize。reshape是将数组转换成指定的形状，然后返回转换的结果，resize是将数组转为指定的形状，会修改数组的本身，不会返回任何值
  import numpy as np
  a1=np.random.randint(0,5,size(3,4))
  a1.reshape((2,6))
  a1.resize((4,3))
  ###flatten和ravel将多维矩阵转化为一维矩阵。flatten,是一种拷贝，ravel 类似于指针的意思。
  ####数组的叠加1垂直方向叠加列数相同vstack，2水平叠加行数要相同hstack
  vstack1=np.random.randint(0,5,size(3,4))
  vstack2=np.random.randint(0,5,size(2,4))
  vstack3=np.vstack([vstack1,vatack3])
  hstack1=np.random.randint(0,5,size(3,4))
  hstack2=np.random.randint(0,5,size(3,1))
  hstack3=np.hstack([hstack1,hstack2])
  ###concatenate([],axis)如果axis是1表示水平方向叠加，是0表示垂直方向叠加
  h3=np.concatenate([hstack1,hstack2],axis=1)
  h3=np.concatenate([vstack1,vstack2],axis=0)
  //当axis=none时表示先进行叠加，在转换为一维数组
  ```

##### 2.7数组的切割

- [ ] ```python
  ###水平切割hsplit按照列来切割，垂直切割vsplit按照行来切割
  import numpy as np
  a1=np.random.randint(0,5,size(4,4))
  np.hsplit(a1,2)//
  //指定位置切割
  np.hsplit(a1,(1,2))
  np.vsplit(a1,2)
  np.vsplit(a1,(1,2))
  np.split(a1,4,axis=1)//手动操作
  np.split(a1,4,axis=0)
  ###数组的转置
  a1=np.random.randint(0,5,size(3,4))
  a1.T
  a1.dot(a1.T)//矩阵和转置矩阵相乘
  a2=a1.transpose()//返回新的数组是一个视图
  ###数组的拷贝，不拷贝，深拷贝，浅拷贝
  //浅拷贝拷贝的值和之前的指向同一个内存空间修改一个两个都会改变
  a=np.arange(12)
  c=a.view()
  print(c is a)
  c[0]=100
  print(a[0])
  d=a.copy()//深拷贝
  print(d is a)
  d[0]=100
  print(a[10])//说明d和a指向的内存空间完全不同了ravel是浅拷贝，flatten是深拷贝
  ```

##### 2.8csv文件

- [ ] ```python
  ###文件的保存
  import numpy as np
  a1=np.random.randint(0,100,size(20,4))
  np.savetxt("score.csv",a1,delimiter=',',header"英语，数学"，commments="",fmt="%d")//文件名score.csv用逗号分割,fmt="%d"表示用整型表示
  ###文件的读取
  b=np.loadtxt("score.csv",dtype=np.int,delimiter=",",skiprows=1)//skiprows表示跳过多少行。
  ###np的独有存储解决方案
  c=np.random.randint(0,100,size(10,4))
  np.save("c",c)
  c1=np.load("c.npy")//savetxt只能存储二维及以下的数组，save可以存储三维以上数组
  ```

  ##### 2.9NAN和INF值的处理

  NAN，不是一个数字的意思，属于浮点类型的意思。INF表示无穷大

  - [ ] ```python
    import numpy as np
    data=np.random.randint(0,100,size=(3,4))
    data=data.astype(np.float)//先将数据改为浮点类型的值
    data[0,1]=np.NAN//任何值和NAN运算都是NAN
    ###如何处理缺失值
    ****1删除缺失值 2用其他值代替
    data[1,2]=np.NAN
    data
    np.isnan(data)//检测数组中的nan值
    data[np.isnan(data)]//提取nan的值
    data[~np.isnan(data)]//过滤所有的nan的值，但是会变成一维数组。
    //删除行或者列保持数组的形状，采用delete函数
    lines=np.where(np.isnan(data))[0]//获取数组中nan的值行号
    np.delete(data,lines,axis=0)//删除nan所在的行
    ###用其他值替代空值，可以采用平均值来替换
    score=np.loadtxt("nan_scores.csv",delimiter="",skiprows=1,encoding="utf-8",dtype=np.str)
    score[scores=""]=np.NAN
    score1=score.astype(np.float)//数据的解析，转化为float类型
    score1[np.isnan(score1)]=0
    scoer1.sum(axis=1)//除了delete axis=0表示行以外，其他大部分函数都是用axis表示行。
    score2=score.astype(np.float)
    for x  in range score2.shape[1]:
        col=score2[:,x]
        non_nan_col = col[~np.isnan(col)]
        mean = non_nan_col.mean()
        col[np.isnan(col)]=mean
        score2
    ```

    ##### 2.10np.random模块

    ```python
    import numpy as np
    np.random.seed(1)//如果seed设置唯一随机数就是唯一的一般不设置
    np.random.rand()//生成一个0-1之间的随机数
    np.random.randn()//生成一个标准正态分布的值
    np.random.choice(5,size=(3,4))//小于5的3行4列的数组
    np.random.shuffle(data1)//打乱data1的值
    ```

    ##### Axis的理解

    ```python
    
    ```

    ##### 2.10 numpy的通用函数

    - [ ] ```python
      ###一元函数
      import numpy as np
      a=np.random.uniform(-10,10,size=(3,4))
      np.abs(a)//绝对值
      np.sqrt(a)//开根号
      np.squre(a)//平方
      np.exp(a)//指数
      np.log(a)//对数
      np.sign(a)//大于0的变1，等于0变为0，小于0的变为-1
      np.ceil(a)//朝着正无穷方向取整
      np.floor(a)//朝着负方向取整
      np.rint(a)//四舍五入
      np.modf(a)//返回两个部分整数部分和小数部分
      np.sin.cos.tan(a)
      ###二元函数
      
      
      ```

    ![image-20210903212909406](C:\Users\XMC\AppData\Roaming\Typora\typora-user-images\image-20210903212909406.png)

- [ ] ```python
  np.any//验证任意一个元素是否为真
  np.all//验证所有元素是否为真
  ###排序np.sort,指定轴进行排序，如果没有指定轴就默认数组的最后一个轴进行排序。ndarray.sort()会影响原来数组。np.argsort(),返回下标值。-np.sort(-a)实现倒序排序。
  idexes=np.argsort(-a)
  np.take(a,indexes)//实现倒序排序
  ###其他函数补充
  //求行的平均值，去掉最高值，最小值
  c=np.random.randint(0,100,size=(3,20))
  def get_mean(x)
  print(x)
  y=x[np.logical_and(x!=x.max(),x!=x.min())].mean()
  np.apply_alone_axis(lamda x :x[np.logical_and(x!=x.max(),x!=x.min())].mean()get_mean,axis=1,arr=c)
  np.linespace(1,10,10)//平均分割，用来指定区间内的值平均分成多少份
  np.unique://返回数组中的唯一值，并且返回唯一值出现的次数
   d=np.random.randint(3,5,size=(3,4))
  np.unique(d)
  np.unique(d,return_counts=ture)
  ```


#### 3 pandas库

##### 3.1series,DataFrame数据结构

- [ ] ```python
  series的创建
  1通过列表来创建
  import pandas as pd
  import numpy as np
  s1 = pd.Series([1,2,3,4,5])
  print(s1)
  type(s1)
  2通过numpy数组的创建
  arr1 = np.arange(0,6)
  s2 = pd.Series(arr1,index=['a','c','d'，'b','e','f'])//指定索引
  s1.values
  s1.index
  3采用字典创建
  dict={'name':'lining','age':'16','class':'一班'}
  s3=pd.Series(dict,index=['name','age','class'])
  //指定索引顺序
  
  ```

