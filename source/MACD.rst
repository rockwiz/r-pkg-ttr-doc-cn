MACD
====

描述
    平滑异同移动平均线（MACD）由Gerald Appel发明，可能是最流行的价格振荡器。本文档中的MACD函数比较一个序列的快速移动均线与其慢速移动
    均线，它可以作为通用振荡器用于任何单变量序列，而非仅价格

用法
::

    MACD(x, nFast=12, nSlow=26, nSig=9, maType, percent=TRUE, ...)

参数
    :x: 可强制转换成xts或matrix的价格、成交量或其它序列
    :nFast: 快速移动平均线期数
    :nSlow: 慢速移动平均线期数
    :nSig: 移动平均信号线的期数
    :maType: (1) 函数或字符串（要调用的函数名），或者
             (2) 一个列表，包括同(1)一样的第一个分量和由命名（named）分量设定的附加参数
    :percent: 逻辑值。如果为真（TRUE），返回慢速移动平均和快速移动平均的百分比差值；否则，返回两者之差
    :...: 第（1）种情况下，其它要传递给maType函数的参数

说明
    MACD或者将快速移动平均减去慢速移动平均（差），或者发现两者之间的变动率（百分比差）。

返回值
    一个x同类对象或（如果try.xts失败）包含以下列的矩阵

    :macd: 价格（成交量，等等）振荡器
    :signal: 振荡器信号线（振荡器的移动平均）

备注
    应用于价格的MACD是通用振荡器的一个特例，MACD可以作为通用振荡器应用于任何序列。时期数常被设定为26和12，但是函数初始使用指数常
    数0.075和0.15，分别接近25.6667和12.3333期。

参考
    可访问以下网址获取该指标的详细说明

    | http://www.fmlabs.com/reference/MACD.htm
    | http://www.fmlabs.com/reference/PriceOscillator.htm
    | http://www.fmlabs.com/reference/PriceOscillatorPct.htm
    | http://stockcharts.com/education/IndicatorAnalysis/indic_MACD1.html
    | http://stockcharts.com/education/IndicatorAnalysis/indic_priceOscillator.html

    关于MACD的原理和使用，请参阅拙作《K线图形态和常用技术指标使用手册》（P196）

另见
    关于移动平均选项，参考EMA、SMA

范例
::

    data(ttrc)
    macd <- MACD( ttrc[,"Close"], 12, 26, 9, maType="EMA" )
    macd2 <- MACD( ttrc[,"Close"], 12, 26, 9,
    maType=list(list(SMA), list(EMA, wilder=TRUE), list(SMA)) )

