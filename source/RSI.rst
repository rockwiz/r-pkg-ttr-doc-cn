RSI
===

描述
    相对强弱指数（Relative Strength Index，RSI）计算最近上升价格运动和绝对价格运动的比率，由J. Welles Wilder发明

用法
::

    RSI(price, n=14, maType, ...)

参数
    :price: 可强制转换成xts或matrix的价格序列
    :n: 移动平均的期数
    :maType: (1) 函数或字符串（要调用的函数名），或者
             (2) 一个列表，包括同(1)一样的第一个分量和由命名（named）分量设定的附加参数
    :...: 第（1）种情况下，其它要传递给maType函数的参数

说明
    RSI的计算公式为 :math:`RSI=100-\frac{100}{1+RS}` ，RS是“平均”收益相对“平均”亏损平滑后的比率。所谓“平均”并不是真的平均，
    因为它们是除以n值而非收益/亏损期数。

返回值
    一个price同类对象或（如果try.xts失败）包含RSI值的向量

备注
    RSI经常作为超买/超卖指标。与价格的背离可能也有用，例如。如果价格创新高而RSI没有，则意味可能的反转。
    可以将 stoch 函数作用于RSI值来计算随机RSI。

参考
    可访问以下网址获取该指标的详细说明

    | http://www.fmlabs.com/reference/RSI.htm
    | http://www.equis.com/Customer/Resources/TAAZ/?c=3&p=100
    | http://linnsoft.com/tour/techind/rsi.htm
    | http://stockcharts.com/education/IndicatorAnalysis/indic_RSI.html

另见
    关于移动平均选项，参考EMA、SMA；关于RSI的变种，参考CMO

范例
::

    data(ttrc)
    price <- ttrc[,"Close"]
    # 缺省状态
    rsi <- RSI(price)
    # 2个MA用1个maType 的情况
    rsiMA1 <- RSI(price, n=14, maType="WMA", wts=ttrc[,"Volume"])
    #2个MA用不同maType 的情况
    rsiMA2 <- RSI(price, n=14, maType=list(maUp=list(EMA,ratio=1/5),
    maDown=list(WMA,wts=1:10)))
    volatility <- chaikinVolatility(ttrc[,c("High","Low")])


