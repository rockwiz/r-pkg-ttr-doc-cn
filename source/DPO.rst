DPO
===

描述
    去趋势化价格振荡器（De-Trended Price Oscillator，DPO）通过将价格减去其移动平均来消除价格（或其它序列）的趋势

用法
::

    DPO(x, n=10, maType, shift=n/2+1, percent=FALSE, ...)

参数
    :x: 可强制转换成xts或matrix的价格、成交量或其它序列
    :n: 移动平均的期数
    :maType: 函数或字符串（要调用的函数名）
    :shift: 变换移动平均的期数
    :percent: 逻辑值。如果为真（TRUE），返回慢速移动平均和快速移动平均的百分比差值；否则，返回两者之差
    :...: 其它要传递给maType函数的参数

说明
    去趋势后的价格显示周期和超买/超卖状态。注意该计算变换了结果的变换期间，因此最后的变换期间将是零。

返回值
    一个x同类对象或（如果try.xts失败）一个包含DPO值的向量

备注
    如上所述，DPO可以基于任何单变量序列，而不仅是价格。

参考
    可访问以下网址获取该指标的详细说明

    | http://www.fmlabs.com/reference/DPO.htm
    | http://www.equis.com/Customer/Resources/TAAZ/?c=3&p=48

另见
    关于移动平均选项，参考EMA、SMA；关于一般振荡器指标，参考MACD

范例
::

    data(ttrc)
    priceDPO <- DPO(ttrc[,"Close"])
    volumeDPO <- DPO(ttrc[,"Volume"])


