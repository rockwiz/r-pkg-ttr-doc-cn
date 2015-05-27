SMA
===

描述
    计算一个序列各种形式的移动平均

用法
::

    SMA(x, n=10)
    EMA(x, n=10, wilder=FALSE, ratio=NULL)
    WMA(x, n=10, wts=1:n)
    DEMA(x, n=10, v=1)
    EVWMA(price, volume, n=10)
    ZLEMA(x, n=10, ratio=NULL)
    VWMA(price, volume, n=10)
    VWAP(price, volume, n=10)

参数
    :x: 可强制转换成xts或matrix的价格、成交量或其它序列
    :price: 可强制转换成xts或matrix的价格序列
    :n: 移动平均的期数
    :v: 成交量因子（一个介于[0,1]之间的数），参见备注
    :wts: 权重向量。wts的长度必须等于x或n（缺省）的长度
    :wilder: 逻辑值。如果为真（TRUE），则计算Welles Wilder型EMA。参见备注
    :ratio: 要用的平滑/衰减比率（在EMA中覆盖wilder）

说明
    | SMA计算一个序列过去n个观测值的算术平均值。
    | EMA计算指数加权平均值，赋予近期观测值较多权重。参见下文警示部分。
    | WMA与EMA类似，但是如果xts长度等于n，就用线性加权；如果wts的长度与x的长度相等，那么WMA用wts的值作为权重。
    | DEMA的计算如下：

        | EVMA使用成交量（volume）来定义移动平均期数。
        | ZLEMA与EMA类似，同样给予近期观测值较多权重，但试图通过减去(n-1)/2期之前的数据去除滞后以使累积效应最小。
        | VWMA和VWAP计算成交量加权的价格移动平均。

返回值
    一个x或price同类对象或（如果try.xts失败）包含以下列的向量：

    :SMA: 简单移动平均
    :EMA: 指数移动平均
    :WMA: 加权移动平均
    :DEMA: 双指数移动平均
    :EVWMA: 弹性成交量加权移动平均
    :ZLEMA: 零滞后指数移动平均
    :VWMA: 成交量加权移动平均（同VWAP）
    :VWAP: 成交量加权移动平均（同VWMA）

警示
    一些指标（如EMA、DEMA、EVWMA等）使用本身先前的值计算，因此短期内不稳定。指标接收到的数据越多，其输出越稳定。参见以下范例。

备注
    对EMA，wilder=FALSE（缺省）时，使用2/(n+1)作为指数平滑比率；wilder=TRUE时，使用1/n作为指数平滑比率。

    由于WMA能接受长度与x的长度或n相等的权重向量，因此可以用作普通移动平均（wts=1:n情况下）或用成交量等其它指标加权的移动平均。

    由于DEMA允许调整v，技术上它是Tim Tillson广义DEMA（GD）。v=1（缺省）时，结果就是标准DEMA；v=0，结果是普通EMA。
    其它所有v值返回GD结果。该函数可以用来计算Tillson T3指标。参见以下范例。

    对EVWMA，如果volume是一个序列，n应该被选择，以使n期成交量之和近似于平均后的流通股数。如果volume是一个常数，它应代表平均后的流通股数。

参考
    可访问以下网址获取该指标的详细说明

    | http://www.fmlabs.com/reference/ExpMA.htm
    | http://www.fmlabs.com/reference/WeightedMA.htm
    | http://www.fmlabs.com/reference/DEMA.htm
    | http://www.fmlabs.com/reference/T3.htm
    | http://linnsoft.com/tour/techind/evwma.htm
    | http://www.fmlabs.com/reference/ZeroLagExpMA.htm

相关参考
    参考用来计算Welles Wilder型移动平均的指标wilderSum

范例
::

    data(ttrc)
    ema.20 <- EMA(ttrc[,"Close"], 20)
    sma.20 <- SMA(ttrc[,"Close"], 20)
    dema.20 <- DEMA(ttrc[,"Close"], 20)
    evwma.20 <- EVWMA(ttrc[,"Close"], ttrc[,"Volume"], 20)
    zlema.20 <- ZLEMA(ttrc[,"Close"], 20)
    ## Tim Tillson T3 指标
    T3 <- function(x, n=10, v=1) DEMA(DEMA(DEMA(x,n,v),n,v),n,v)
    t3 <- T3(ttrc[,"Close"])
    ## EMA（和以上提到的其它指标）的短期不稳定性
    x <- rnorm(100)
    tail( EMA(x[90:100],10), 1 )
    tail( EMA(x[70:100],10), 1 )
    tail( EMA(x[50:100],10), 1 )
    tail( EMA(x[30:100],10), 1 )
    tail( EMA(x[10:100],10), 1 )
    tail( EMA(x[ 1:100],10), 1 )
    volatility <- chaikinVolatility(ttrc[,c("High","Low")])

