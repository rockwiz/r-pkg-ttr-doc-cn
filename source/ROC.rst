ROC
===

描述
    Calculate the (rate of) change of a series over n periods.

用法
::

    ROC(x, n = 1, type = c("continuous", "discrete"),na.pad = TRUE)
    momentum(x, n = 1, na.pad = TRUE)

参数
    :price: 可强制转换成xts或matrix的价格序列
    :n: 移动平均的期数
    :maType: (1) 函数或字符串（要调用的函数名），或者
             (2) 一个列表，包括同(1)一样的第一个分量和由命名（named）分量设定的附加参数
    :...: 第（1）种情况下，其它要传递给maType函数的参数

x Price, volume, etc. series that is coercible to xts or matrix.
n Number of periods to use.
type Compounding type; either "continuous" (the default) or "discrete".
na.pad Should periods prior to n be appended? Default is TRUE.
说明
    The ROC indicator provides the percentage difference of a series over two observations, while the
momentum indicator simply provides the difference.

返回值
    A object of the same class as x or a vector (if try.xts fails) containing the rate-of-change (or
return) values for ROC or a vector containing the differenced price series for momentum.


范例
::

    data(ttrc)
    roc <- ROC(ttrc[,"Close"])
    mom <- momentum(ttrc[,"Close"])

