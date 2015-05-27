williamsAD
==========
描述
    威廉AD（Williams Accumulation/Distribution，AD）线是一种市场动量的度量，由Larry Williams发明

用法
    williamsAD(HLC)
参数
    :HLC: 可强制转换成xts或matrix，包含最高-最低-收盘价序列的对象

说明
    威廉AD与OBV和chaikinAD不同，它不考虑成交量。

返回值
    一个HLC同类对象或（如果try.xts失败）一个包含威廉集散量（Accumulation/Distribution）的向量

备注
    AD线的解释是寻找指标和价格方向的背离。

参考
    可访问以下网址获取该指标的详细说明

    | http://www.fmlabs.com/reference/WilliamsAD.htm
    | http://www.equis.com/Customer/Resources/TAAZ/?c=3&p=125

另见
    参见OBV、chaikinAD和ATR

范例
::

    data(ttrc)
    ad <- williamsAD(ttrc[,c("High","Low","Close")])

