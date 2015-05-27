CMO
===

描述
    Chande动量振荡器（Chande Momentum Oscillator，CMO）是一种改进过的RSI，由Tushar S. Chande发明。
用法
::

    CMO(x, n=14)

参数
    :x: 可强制转换成xts或matrix的价格、成交量或其它序列
    :n: 要计算的期数

说明
    CMO用总变动除以净变动（ :math:`\frac{up-down}{up+down}` ），而RSI用上升变动除以净变动（ :math:`\frac{up}{up+down}` ）。

返回值
    一个和x同类对象或（如果try.xts失败）包含CMO值的向量

备注
    有多种方式解释CMO：
    * 高于/低于+50/-50意味超买/超卖状态；
    * CMO值越高，则趋势越强；
    * 当CMO向上/下穿越它的移动平均线，通常是一个买入/卖出信号

参考
    可访问以下网址获取该指标的详细说明

    | http://www.fmlabs.com/reference/CMO.htm

另见
    RSI

范例
::

    data(ttrc)
    cmo <- CMO(ttrc[,"Close"])


