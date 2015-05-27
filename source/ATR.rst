ATR
===

描述
    真实范围（True Range，TR）衡量最高-最低-收盘价序列的波动性，平均真实范围（ATR）是TR的Welles Wilder类型的移动平均。
    由Welles Wilder在1978年发明

用法
::

    ATR(HLC, n=14, maType, ...)

参数
    :HLC: 可强制转换成xts或matrix，包含最高-最低-收盘价序列的对象
    :n: 移动平均的期数
    :maType: 函数或字符串（要调用的函数名）
    :...: 其它要传给maType函数的参数

说明
    TR将昨收价引入计算（最高价减去最低价）中。例如，如果昨收价高于今天的最高价，那么TR等于昨天收盘价减去今天最低价。
    ATR是Welles Wilder趋向指数（DX、ADX）的一个计算因子。

返回值
    一个HLC或matrix（如果try.xts失败）同类，包含以下列的对象

    :tr: 序列的真实范围
    :atr: 序列的平均（由ma设定）真实范围
    :true.high: 序列的真实最高价
    :true.low: 序列的真实最低价

备注
    如果提供最高-最低价，该函数用最高/最低价计算最大/最小值。否则，函数就计算单个序列的最大/最小值。

参考
    可访问以下网址获取该指标的详细说明

    | http://www.fmlabs.com/reference/TR.htm
    | http://www.fmlabs.com/reference/ATR.htm
    | http://www.equis.com/Customer/Resources/TAAZ/?c=3&p=35
    | http://www.linnsoft.com/tour/techind/trueRange.htm
    | http://stockcharts.com/education/IndicatorAnalysis/indic_ATR.html

另见
    关于移动平均选项，参考EMA、SMA；参考DX，其也使用真实范围；关于其它波动性衡量指标，参考chaikinVolatility

范例
::

    data(ttrc)
    atr <- ATR(ttrc[,c("High","Low","Close")], n=14)

