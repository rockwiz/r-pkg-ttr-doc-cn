adjRatios
=========

描述
    生成股票分拆和分红调整比率向量

用法::

    adjRatios(splits, dividends, close)

参数
    :splits: 可强制转换成xts的分拆序列
    :dividends: 可强制转换成xts的分红序列
    :close: 可强制转换成xts的收盘价序列

说明
    * 如果如果仅提供splits，生成的对象仅包含和splits一样多的数值
    * 如果splits和close都被提供，生成对象的长度等于max(NROWS(splits), NROWS(close))
    * 如果提供了dividends，那么必需提供close

返回值
    一个包含以下列的xts对象

    :Split: 分拆调整比率
    :DIV: 分红调整比率

