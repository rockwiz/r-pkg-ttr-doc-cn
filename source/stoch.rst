stoch
=====

描述
    随机振荡器是一种将每天收盘价与过去n期最高价/最低价范围关联起来的振荡器，由George C. Lane在1950年代后期发明。
    SMI将最高价/最低价范围中点关联起来，由William Blau于1993年发明

用法
::

    stoch(HLC, nFastK=14, nFastD=3, nSlowD=3, maType, bounded=TRUE, smooth=1, ...)
    SMI(HLC, n=13, nFast=2, nSlow=25, nSig=9, maType, bounded=TRUE, ...)

参数
    :HLC: 可强制转换成xts或matrix，包含最高-最低-收盘价序列的对象
    :nFastK: 快速%K的期数（即，要用的过去期数）
    :nFastD: 快速%D的期数（即，应用于%K的平滑期数）
    :nSlowD: 慢速%D的期数（即，应用于%D的平滑期数）
    :n: 要计算的期数
    :nFast: 初始平滑期数
    :nSlow: 双平滑期数
    :nSig: 信号线期数
    :bounded: 逻辑值，当期是否要计算？
    :smooth: 计算%K前用于内部平滑期数
    :maType: (1) 函数或字符串（要调用的函数名），或者
             (2) 一个列表，包括同（1）一样的第一个分量和由命名（named）分量设定的附加参数
    :...: 第（1）种情况下，其它要传递给maType函数的参数

说明
    如果提供了最高-最低-收盘价序列，则指标用最高/最低值计算；如果提供的是一个向量，则计算该单序列。这允许随机指标计算：
    1) 没有HLC定义的序列（如汇率）
    2) 随机化指标（如随机RSI-参见范例）

    smooth参数用于计算快速K线前最高-最低-收盘价差分的内部平滑期数

返回值
    一个HLC同类对象或（如果try.xts失败）一个包含以下列的矩阵：

    :fastK: 随机快速%K
    :fastD: 随机快速%D
    :slowD: 随机慢速 %D
    :SMI: 随机动量指数
    :signal: 随机动量指数信号线

备注
    William’s %R的计算与随机指标快速%K的计算类似。

    随机振荡器和SMI分别计算收盘价与最高/最低价范围、收盘价与最高/最低价范围的中点的相对值。

    随机振荡器和SMI的解释类似。读数低于20（高于80）被看做超卖（超买）。然而，低于20（高于80）并非一定看跌（看涨）。Lane相信最佳的卖出（买入）信号出现在当振荡器从超买（超卖）返回80以下（20以上）时。

    对振荡器，买入（卖出）信号也可以在%K向上（向下）穿越%D时给出。然而穿越信号非常频繁，很容易导致锯齿。

参考
    可访问以下网址获取该指标的详细说明

    * 随机振荡器

        | http://www.fmlabs.com/reference/StochasticOscillator.htm
        | http://www.equis.com/Customer/Resources/TAAZ?c=3&p=106
        | http://linnsoft.com/tour/techind/stoc.htm
        | http://stockcharts.com/education/IndicatorAnalysis/indic_stochasticOscillator.html

    * SMI

        | http://www.fmlabs.com/reference/default.htm?url=SMI.htm

    有关随机指标的原理和使用，请参阅拙作《K线图形态和常用技术指标使用手册》（P180）

另见
    关于移动平均选项，参考EMA、SMA；参考WPR，并比较它的结果和快速%K

范例
::

    data(ttrc)
    stochOSC <- stoch(ttrc[,c("High","Low","Close")])
    stochWPR <- WPR(ttrc[,c("High","Low","Close")])
    plot(tail(stochOSC[,"fastK"], 100), type="l",
    main="Fast %K and Williams %R", ylab="",
    ylim=range(cbind(stochOSC, stochWPR), na.rm=TRUE) )
    lines(tail(stochWPR, 100), col="blue")
    lines(tail(1-stochWPR, 100), col="red", lty="dashed")
    stoch2MA <- stoch( ttrc[,c("High","Low","Close")],
    maType=list(list(SMA), list(EMA, wilder=TRUE), list(SMA)) )

    SMI3MA <- SMI(ttrc[,c("High","Low","Close")],
    maType=list(list(SMA), list(EMA, wilder=TRUE), list(SMA)) )

    stochRSI <- stoch( RSI(ttrc[,"Close"]) )

