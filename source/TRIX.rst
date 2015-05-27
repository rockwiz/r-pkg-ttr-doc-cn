TRIX
====

描述
    TRIX指标计算三次指数移动平均的变动率，由Marc Chaikin发明

用法
::

    TRIX(price, n=20, nSig=9, maType, percent=TRUE, ...)

参数
    :price: 可强制转换成xts或matrix价格序列
    :n: 移动平均的期数
    :nSig: 信号线移动平均期数
    :maType: (1) 函数或字符串（要调用的函数名），或者
             (2) 一个列表，包括同（1）一样的第一个分量和由命名（named）分量设定的附加参数
    :percent: 逻辑值。如果为真（TRUE），返回慢速移动平均和快速移动平均的百分比差值；否则，返回两者之差
    :...: 第（1）种情况下，其它要传给maType函数的参数

说明
    TRIX计算如下：

    .. math::

        3MA = MA(MA(MA(price)))

        trix = 100 \times [ \frac{ 3MA(t)}{ 3MA(t-1)} - 1 ]



返回值
    一个price同类对象或（如果try.xts失败）包含TRIX值得向量

备注
    TRIX向上/向下穿越0轴时产生买入/卖出信号。缺省地，用TRIX的9期EMA作为信号线。当TRIX处于0轴以上/以下，向上/向下穿越信号线时发出买入/卖出信号。

参考
    可访问以下网址获取该指标的详细说明

    | http://www.fmlabs.com/reference/default.htm?url=TRIX.htm
    | http://www.equis.com/Customer/Resources/TAAZ/?c=3&p=114
    | http://www.linnsoft.com/tour/techind/trix.htm
    | http://stockcharts.com/education/IndicatorAnalysis/indic_trix.htm

    有关TRIX的原理和使用，请参阅拙作《K线图形态和常用技术指标使用手册》（P203）

另见
    关于移动平均选项，参考EMA、SMA

范例
::

    data(ttrc)
    trix <- TRIX(ttrc[,"Close"])
    trix4 <- TRIX(ttrc[,"Close"],
    maType=list(list(SMA), list(EMA, wilder=TRUE), list(SMA), list(DEMA)))
    volatility <- chaikinVolatility(ttrc[,c("High","Low")])


