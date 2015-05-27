TTRtools
========

描述
    各种在设计技术交易规则时可能有用的函数

用法
::

    growth(price, signals, ...)
    lags(x, n=1)
    wilderSum(x, n=10)

参数
    :price: 可强制转换成xts或matrix的价格序列
    :signals: 要用的信号（缺省为由1组成的向量）。“0”表示没有头寸，“1”表示多头头寸，“-1”表示空头头寸
    :x: 可强制转换成xts或matrix的对象
    :n: 期数

说明
    | growth用给定的价格和信号计算投资增长
    | lags计算给定序列的滞后
    | wilderSum计算Welles Wilder型加权总和

返回值
    一个HLC同类对象或（如果try.xts失败）包含集散量的向量

    :growth: 返回一个投资增长向量
    :lags: 返回一个原始向量滞后值的矩阵
    :wilderSum: 返回一个加权总和的向量

备注
    在计算价格序列的收益时，可以通过“...”参数在growth中指定期数和复合类型。
