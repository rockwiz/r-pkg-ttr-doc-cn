chaikinVolatility
=================

描述
    Chaikin波动性衡量交易范围的变动率，由Marc Chaikin发明

用法
::

    chaikinVolatility(HL, n=10, maType, ...)

参数
    :HL: 可强制转换成xts或matrix，包含最高-最低价序列的对象
    :n: 移动平均的期数
    :maType: 函数或字符串（要调用的函数名）
    :...: 其它要传递给maType函数的参数

说明
    chaikinVolatility将波动性定位为最高价和最低价之间差距的增长。

返回值
    一个HLC同类对象或（如果try.xts失败）包含集散量的向量

备注
    Chaikin波动性快速增加意味接近底部，慢速减少预示接近顶部。

参考
    可访问以下网址获取该指标的详细说明

    | http://www.fmlabs.com/reference/ChaikinVolatility.htm
    | http://www.equis.com/Customer/Resources/TAAZ/Default.aspx?c=3&p=120

另见
    关于移动平均选项，参考EMA、SMA；关于其它衡量波动性的指标，参考TR

范例
::

    data(ttrc)
    volatility <- chaikinVolatility(ttrc[,c("High","Low")])

