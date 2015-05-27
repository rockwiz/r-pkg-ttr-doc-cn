CLV
===

描述
    收盘价位值（Close Location Value，CLV）将收盘价与当天交易范围关联起来

用法
::

    CLV(HLC)

参数
    :HLC: 可强制转换成xts或matrix，包含最高-最低-收盘价序列的对象

说明
    CLV落在-1和+1范围内，如果CLV是+1/-1，那么收盘价就是当天最高/最低价；如果CLV是0，那么当天最高价等于最低价。

返回值
    一个HLC同类对象或（如果try.xts失败）一个包含最高-最低-收盘价序列收盘价位值的向量

参考
    可访问以下网址获取该指标的详细说明

    | http://stockcharts.com/education/IndicatorAnalysis/indic_AccumDistLine.html

另见
    参考chaikinAD，该指标使用了CLV

范例
::

    data(ttrc)
    clv <- CLV(ttrc[,c("High","Low","Close")])


