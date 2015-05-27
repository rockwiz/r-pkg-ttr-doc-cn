WPR
===

描述
    William’s %R
用法
::

    WPR(HLC, n=14)

参数
    :HLC: 可强制转换成xts或matrix，包含最高-最低-收盘价序列的对象
    :n: 要用的期数

说明
    如果参数提供High-Low-Close序列，那么指标就用最高/最低价计算；如果提供的是向量，那么就只使用那个序列。

返回值
    一个HLC同类对象或（如果try.xts失败）包含威廉%R值得向量

备注
    威廉%R计算与随机快速%K的计算一样。

参考
    可访问以下网址获取该指标的详细说明

    | http://www.fmlabs.com/reference/WilliamsR.htm
    | http://www.equis.com/Customer/Resources/TAAZ?c=3&p=126
    | http://linnsoft.com/tour/techind/willR.htm
    | http://stockcharts.com/education/IndicatorAnalysis/indic_williamsR.html

    有关William’s %R的原理和使用，请参阅拙作《K线图形态和常用技术指标使用手册》（P213）

另见
    stoch

范例
::

    data(ttrc)
    stochOsc <- stoch(ttrc[,c("High","Low","Close")])
    stochWPR<- WPR(ttrc[,c("High","Low","Close")])
    plot(tail(stochOsc[,"fastK"], 100), type="l",
    main="Fast %K and Williams %R", ylab="",
    ylim=range(cbind(stochOsc, stochWPR), na.rm=TRUE) )
    lines(tail(stochWPR, 100), col="blue")
    lines(tail(1-stochWPR, 100), col="red", lty="dashed")

