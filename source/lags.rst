lags
====

描述
    各种在设计技术交易规则时可能有用的函数

用法
::

    lags(x, n = 1)
    growth(price, signals, ...)
    naCheck(x, n = 0)

参数
    :price: 可强制转换成xts或matrix的价格序列
    :signals: 信号（缺省为1的向量）。0为无头寸，1为多头，-1为空头
    :x: 强制转换成xts或matrix的对象
    :n: 期数
    :...: 从其它方法传入或传给其它方法的参数

说明
    growth 用给定价格和信号计算投资增长

    lags 计算给定序列的滞后

返回值
    growth返回投资增长的向量

    lags返回原向量滞后值的矩阵
备注
    在growth中，通过...参数计算价格序列的收益时，可以指定期数和复合类型
