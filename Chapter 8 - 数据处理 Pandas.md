# Chapter 8 - 数据处理 Pandas

## 01. 读取 Excel、文本、CSV 等不同类型数据

和 Excel 打交道时，由于数据量较大，人工来修改某些数据可能会有点浪费时间，这时候会用到 Python 数据处理工具 —— Pandas 库。

下面使用 Pandas 的 read_excel() 函数读取 .xls或 .xlsx 类型的 Excel  文件；使用 read_csv() 函数读取文本文件和 .csv 类型的 Excel 文件。

### 读取历史销售数据（.xls 和 .xlsx 类型文件）

```python
import pandas as pd

aa = './Data/TB2018.xlsx'
df = pd.DataFrame(pd.read_excel(aa))
df1 = df[['买家会员名', '买家实际支付金额']]
print(df1)
```

![1570546548590](C:\Users\Harrytsz\AppData\Roaming\Typora\typora-user-images\1570546548590.png)

### 读取股票数据（.csv 类型文件）

```python
bb = './Data/000001.csv'
df = pd.read_csv(bb, encoding = 'gbk')
df1 = df[['date', 'open', 'high', 'close', 'low']]
df1.columns = ['日期', '开盘价', '最高价', '闭市价', '最低价']
print(df1)
```

![1570546577283](C:\Users\Harrytsz\AppData\Roaming\Typora\typora-user-images\1570546577283.png)

### 读取文本数据（.txt 文本文件）

```python
cc = './Data/fl4_name.txt'
df = pd.read_csv(cc, encoding = 'gbk')
print(df)
```

![1570546599608](C:\Users\Harrytsz\AppData\Roaming\Typora\typora-user-images\1570546599608.png)

## 多学两招

读取各类型数据过程中经常遇到的 3 个问题：

**问题1：读取数据进行输出时，数据显示不全和列名不对齐。**

解决数据显示不全时，可设置数据显示的列数和宽度，代码如下：

```python
pd.set_option('display.max_columns', 500)
pd.set_option('display.width', 1000)
```

解决数据输出时列名不对齐问题，代码如下：

```python
pd.set_option('display.unicode.ambiguous_as_wide', True)
pd.set_option('display.unicode.east_asian_width', True)
```

**问题2：读取文本数据时，如果出现如图所示编码错误，可以尝试使用 GBK 编码。**

**问题3：如果数据量较大超出内存时，可以输出部分数据（如前 10 行），代码如下：**

```python
print(df.head(10))
```

