EMV
===

描述
    简易波动指标 [1]_ （Arms’ Ease of Movement Value）强调价格容易变动的天数而漠视价格不容易变动的天数，由Richard W. Arms, Jr.发明。

用法
::

    EMV(HL, volume, n=9, maType, vol.divisor=10000, ...)

参数
    :HL: 可强制转换成xts或matrix，包含最高-最低价序列的对象
    :volume: 与HL对应的成交量向量或矩阵
    :n: 移动平均的期数
    :maType: 函数或字符串（要调用的函数名）
    :vol.divisor: 增量因子，扩大结果使之容易处理
    :...: 其它要传递给maType函数的参数

说明
    EMV通过将价格运动中点（ :math:`\frac{high+low}{2}` ）除以“箱体率”（ :math:`Box Ratio=\frac{volumn}{high-low}` ）计算而来。

返回值
    一个HL和volume同类对象或（如果try.xts失败）包含以下列的矩阵：

    :emv: 易动值
    :emvMA: 平滑（由ma设定）后的易动值

备注
    EMV向上/下穿越0轴产生一个买入/卖出信号。当EMV围绕0轴来回摆荡，说明价格变动幅度小并且/或者伴随巨大成交量，因而价格变动不容易。

参考
    可访问以下网址获取该指标的详细说明

    | http://www.fmlabs.com/reference/ArmsEMV.htm
    | http://www.equis.com/Customer/Resources/TAAZ/?c=3&p=51
    | http://linnsoft.com/tour/techind/arms.htm

另见
    关于移动平均选项，参考EMA、SMA

范例
::

    data(ttrc)
    emv <- EMV(ttrc[,c("High","Low")], ttrc[,"Volume"])

