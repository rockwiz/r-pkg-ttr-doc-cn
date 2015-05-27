TTR
===

描述
    该包包含许多流行的技术分析函数以及从雅虎（Yahoo）财经获取美国股票代码和数据的函数

包信息
    :Package: TTR
    :Type: Package
    :Version: 0.20-2
    :Date: 2010-03-23
    :License: GPL Version 3 or later

用户也许对下列函数感兴趣：

    * ADX
    * BBands
    * changes
    * MovingAverages
    * MACD
    * RSI
    * runFun
    * stoch
    * VWAP
    * WebData

参考
    可访问以下网址获取文档相关的详细说明

    | http://www.fmlabs.com/reference/default.htm
    | http://www.equis.com/Customer/Resources/TAAZ/?p=0
    | http://www.linnsoft.com/tour/technicalindicators.htm
    | http://stockcharts.com/education/IndicatorAnalysis/

范例
::

    data(ttrc)

    # 布林带
    bbands <- BBands( ttrc[,c("High","Low","Close")] )

    # 趋向指数
    adx <- ADX(ttrc[,c("High","Low","Close")])

    # 移动平均
    ema <- EMA(ttrc[,"Close"], n=20)
    sma <- SMA(ttrc[,"Close"], n=20)

    # MACD
    macd <- MACD( ttrc[,"Close"] )

    # RSI
    rsi <- RSI(ttrc[,"Close"])

    # 随机指标
    stochOsc <- stoch(ttrc[,c("High","Low","Close")])

    ### 注: 要使用以下范例，须连接到互联网

    # 从网上获取美国股票代码
    nyseSymbols <- stockSymbols("NYSE")

    # 从网上获取雅虎财经数据
    ibm <- getYahooData("IBM", 19990404, 20050607)


