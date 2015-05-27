CMF
===

描述
    Chaikin资金流比较过去n期总成交量与过去n期总成交量和CLV的乘积，由Marc Chaikin发明

用法
::

    CMF(HLC, volume, n = 20)

参数
    :HLC: 可强制转换成xts或matrix，包含最高-最低-收盘价序列的对象
    :volume: 与HLC对应的成交量向量或矩阵
    :n: 要计算的期数

说明
    Chaikin资金流由过去n期Chaikin集散量（Chaikin AD线）除以过去n期总成交量计算而来。

返回值
    一个HLC同类对象或（如果try.xts失败）包含Chaikin资金流数值的向量

备注
    当Chaikin资金流高于/低于+/-0.25时，它是一个看涨/看跌信号；如果Chaikin资金流保持0以下，而价格在上升，意味一个可能的反转。

参考
    可访问以下网址获取该指标的详细说明

    | http://www.fmlabs.com/reference/ChaikinMoneyFlow.htm
    | http://www.linnsoft.com/tour/techind/cmf.htm
    | http://stockcharts.com/education/IndicatorAnalysis/indic_ChaikinMoneyFlow1.html

另见
    参考CLV和chaikinAD

范例
::

    data(ttrc)
    cmf <- CMF(ttrc[,c("High","Low","Close")], ttrc[,"Volume"])

