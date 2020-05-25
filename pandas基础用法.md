
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

### ILOC和LOC的用法 ###
**ILOC是根据行号来选取对应的行或列；LOC是根据标签(索引)来选取对应的行或列**



### CONCAT和MERGE的用法 ###

**CONCAT知识纵向或横向讲两个表拼接在一起，参数axis=0为纵向，=1为横向，默认为axis=0**
```python
data1=pd.DataFrame(np.arange(6).reshape(2,3),columns=list('abc'))
data2=pd.DataFrame(np.arange(20,26).reshape(2,3),columns=list('ayz'))
data=pd.concat([data1,data2],axis=1)
dat=pd.concat([data1,data2])
print(data)
print(dat)
```

**MERGE则是根据共同列进行合并，LEFT JOIN是以左表为基础，向右合并；RIGHT JOIN 从右往左合并，INNER JOIN 只合并两个表共同的部分，相当于交集；OUTER JOIN 全部合并，相当于并集**
