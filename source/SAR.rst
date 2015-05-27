SAR
===

描述
    抛物线止损转向（Parabolic Stop-and-Reverse，SAR）计算后续止损点，由J. Welles Wilder发明

用法
::

    SAR(HL, accel=c(0.02, 0.2))

参数
    :HL: 可强制转换成xts或matrix，包含最高-最低价序列的对象
    :accel: - accel[1]：加速因子
            - accel[2]：最大加速因子

说明
    | SAR的计算非常复杂，参见“参考”部分。
    | SAR假设一直处于市场中，计算何时出清多头头寸或建仓空头头寸，或反过来的止损转向点。

返回值
    一个HL同类对象或（如果try.xts失败）包含SAR值的向量

参考
    可访问以下网址获取该指标的详细说明

    | http://www.linnsoft.com/tour/techind/sar.htm
    | http://www.fmlabs.com/reference/SAR.htm

另见
    参考同样由Welles Wilder发明的两个指标：ATR和ADX

范例
::

    data(ttrc)
    volatility <- chaikinVolatility(ttrc[,c("High","Low")])

