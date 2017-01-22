### Python之数据分析利器Panda ###

Panda有着2个高级的数据结构，Series 与DataFrame

Series 类似于数组，DataFrame是面板数据，有这2种数据结构的存在，从而使Python中的数据处理变得非常简单，快速

### Series###

Series简单地说是一维数组，但其具有索引

创建一个Series的基本格式是s = Series(data, index=index, name=name)

    a = np.random.randn(5)
	s = Series(a)

	
	s = Series(np.random.randn(5), index=['a', 'b', 'c', 'd', 'e'])
	print s
	
	d = {'a': 0., 'b': 1, 'c': 2}
	s = Series(d)

Series数据可以和数组一样使用下标，也可以像字典一样使用索引


### DataFrame ###

DataFrame是将Series按照列合并而成的二维数据结构，每一列单独取出来是一个Series。

	d = {'one': Series([1., 2., 3.], index=['a', 'b', 'c']), 'two': Series([1., 2., 3., 4.], index=['a', 'b', 'c', 'd'])}
	df = DataFrame(d)


可以使用dataFrame.column_name选取列，也可以使用dataFrame[]操作选取列，后一种方法可以选取多列；

如果DataFrame没有列明，[]可以使用非负整数，也就是下标选取列，若有列名，则必须使用列名选取

单独取出一列出来，其数据结构显示的是Series,取两列及两列以上的结果仍然是DataFrame

如果要选取行，可以使用dataframe.iloc按下标选择选取。或者使用dataframe.loc按索引选取。

