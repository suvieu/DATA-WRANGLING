
### GROUPBY基础用法 ###

**1.导入数据，按照年龄分组,size()和count()的区别在于size会把NAN也算进去，count不会**

```python
import pandas as pd
user = pd.read_table("users.dat", sep="::",names=['UserID','Gender','Age','Occupation','Zip-code'],engine='python')
grouped_age=user.groupby('Age').size()
print(grouped_age)
```


**也可以在后面跟.mean()或者.median() 得出某组的平均数和中位数**

```python
grouped_age=user.groupby('Age').size()
```
**可以在groupby后面的括号里添加两个列名**
```python
grouped_age=user.groupby(['Age','Gender']).size()
print（grouped_Age.size()）
```

**分组后显示两种计算结果**
```python
print(doc.groupby(['Fireplace'])['Price','LivingArea'].agg(['mean','std']))
```


<br>

### ILOC和LOC的用法 ###
**ILOC是根据行号来选取对应的行或列；LOC是根据标签(索引)来选取对应的行或列**

<br>

### CONCAT和MERGE的用法 ###

**CONCAT只是纵向或横向将两个表拼接在一起，参数axis=0为纵向，=1为横向，默认为axis=0**
```python
data1=pd.DataFrame(np.arange(6).reshape(2,3),columns=list('abc'))
data2=pd.DataFrame(np.arange(20,26).reshape(2,3),columns=list('ayz'))
data=pd.concat([data1,data2],axis=1)
dat=pd.concat([data1,data2])
print(data)
print(dat)
```

**MERGE则是根据共同列进行合并，LEFT JOIN是以左表为基础，向右合并；RIGHT JOIN 从右往左合并，INNER JOIN 只合并两个表共同的部分，相当于交集；OUTER JOIN 全部合并，相当于并集**



<br>

### CUT基础用法 ###
**CUT方法将一个一维数组按要求分割成若干##
```
ages = np.array([1,5,10,40,36,12,58,62,77,89,100,18,20,25,30,32])
print(pd.cut(ages, 5))
```
**这里将ages数组分割成五个区间，输出会显示每个元素对应在哪个区间内**

**也可以利用label参数个每个区间贴上不同的标签**
```
print(pd.cut(ages, 5,labels=["婴儿","青年","中年","壮年","老年"]))
```
**还可以按自己的要求给数组划分区间**
```
pd.cut(train['Item_Visibility'],(0.000,0.065,0.13,0.2),labels=['Low Viz','Viz','High Viz'])
```
**这里把train里的名为Item_Visibility的列中的数据按照0.000~0.065,0.065~0.13,0.13~0.2分成三个区间，并贴上标签**



