DonchianChannel
===============

描述
    Donchian通道 （Donchian Channel）由Richard Donchian发明，用于生成海龟交易系统的买/卖信号

用法
::

    DonchianChannel(HL, n=10)

参数
    :HL: 可强制转换成xts或matrix，包含最高-最低价序列的对象
    :n: 移动平均的期数

说明
    Donchian通道由两条（有时是三条）线组成：上端线是过去n期最高的最高价，下端线是过去n期最低的最低价，中间线是上线和下线的平均值。

返回值
    一个和HL同类对象或（如果try.xts失败）包含以下列的矩阵：

    :high: 最高的最高价序列
    :mid: high和low的平均值
    :low: 最低的最低价序列

参考
    可访问以下网址获取该指标的详细说明

    | http://www.linnsoft.com/tour/techind/donch.htm

另见
    BBands

范例
::

    data(ttrc)
    dc <- DonchianChannel(ttrc[,c("High","Low")])


