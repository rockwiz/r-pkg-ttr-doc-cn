ZigZag
======

描述
    ZigZag通过剔除小于极值间差距的价格变动，并将极值点连线的方式突出趋势

用法
::

    ZigZag( HL, change=10, percent=TRUE, retrace=FALSE, lastExtreme=TRUE )

参数
    :HL: 可强制转换成xts或matrix，包含最高-最低价序列的对象
    :change: 最小的价格变动，元（点）或百分比。（参见percent）
    :percent: 使用百分比还是元（点）表达变动
    :retrace: change是之前运动的回调，还是从顶（峰）到底（谷）的绝对变动？
    :lastExtreme: 如果多期极值价格一样，那么该极值是否作为第一或最后一个观测值？

说明
    ZigZag不是预测性的，其目的是过滤噪音以使图形更清晰。它更多是作为可视化工具而非指标使用。

返回值
    一个HL同类对象或（如果try.xts失败）包含ZigZag指标的向量

备注
    如果参数提供High-Low价格，那么函数计算最高/最低价的最大/最小值；否则，计算单个序列的最大/最小值。

参考
    可访问以下网址获取该指标的详细说明

    | http://www.fmlabs.com/reference/default.htm?url=ZigZag.htm
    | http://www.linnsoft.com/tour/techind/zigzag.htm
    | http://www.linnsoft.com/tour/techind/zigosc.htm
    | http://www.equis.com/Customer/Resources/TAAZ/?c=3&p=127
    | http://stockcharts.com/school/doku.php?id=chart_school:technical_indicators:zigzag

范例
::

    ## Get Data and Indicator ##
    data(ttrc)
    zz <- ZigZag( ttrc[,c("High", "Low")], change=20 )


.. rubric:: 脚注
.. [1] “简易波动指标”是常用译法，作者认为翻译成“易动值”可能更准确。
