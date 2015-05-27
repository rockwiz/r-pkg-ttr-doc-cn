PBands
======

描述
    John Bollinger’s famous adaptive volatility bands most often use the typical price of an HLC series, or may be calculated on a univariate price series (see BBands).

用法
::

    PBands(prices, n = 20, maType = "SMA", sd = 2, ..., fastn = 2, centered = FALSE, lavg = FALSE)

参数
    :price: 可强制转换成xts或matrix的价格序列
    :n: 移动平均的期数
    :maType: (1) 函数或字符串（要调用的函数名），或者
             (2) 一个列表，包括同(1)一样的第一个分量和由命名（named）分量设定的附加参数
    :...: 第（1）种情况下，其它要传递给maType函数的参数

说明
    This function applies a second moving average denoted by fastn to filter out higher-frequency noise, making the bands somewhat more stable to temporary fluctuations and spikes.

    If centered is TRUE, the function also further smoothes and centers the bands around a centerline adjusted to remove this higher frequency noise. If lavg is also TRUE, the smoothing applied for the middle band (but not the volatility bands) is doubled to further smooth the price-response function.

    If you have multiple different price series in prices, and want to use this function, call this functions using lapply(prices,PBands,...).

返回值
    一个price同类对象或（如果try.xts失败）包含RSI值的向量

另见
    BBands

范例
::

    data(ttrc)
    pbands.close <- PBands( ttrc[,"Close"] )

.. TODO
