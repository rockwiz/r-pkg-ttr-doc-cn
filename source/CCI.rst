CCI
===

描述
    商品通道指数（Commodity Channel Index，CCI）试图发觉趋势的开始和终结

用法
::

    CCI(HLC, n=20, maType, c=0.015, ...)

参数
    :HLC: 可强制转换成xts或matrix，包含最高-最低-收盘价序列的对象
    :n: 移动平均的期数
    :maType: 函数或字符串（要调用的函数名）
    :c: 用于平均偏差的常数
    :...: 其它要传给maType函数的参数

说明
    CCI将当前价格与过去n期平均价格关联起来，其值经常落在+100和-100通道之间。一个基本的CCI交易系统：如果CCI上升至+100以上或下降到-100以下，则买入或卖出；如果下降到+100以下或上升至-100以上，则卖出或买入。

返回值
    一个HLC同类对象或（如果try.xts失败）包含CCI值的向量

备注
    如果HLC是一个高-低-收价矩阵（High-Low-Close matrix），那么计算典型价格；如果HLC是一个向量，那么使用那些值代替典型价格。

参考
    可访问以下网址获取该指标的详细说明

    | http://www.fmlabs.com/reference/CCI.htm
    | http://www.equis.com/Customer/Resources/TAAZ/?c=3&p=42
    | http://www.linnsoft.com/tour/techind/cci.htm
    | http://stockcharts.com/education/IndicatorAnalysis/indic_CCI.html

    关于CCI的原理和使用，请参阅拙作《K线图形态和常用技术指标使用手册》（P）

另见
    关于移动平均选项，参考EMA、SMA；关于其它衡量趋势方向和强度指标，参考aroon、ADX、TDI、VHF、GMMA

范例
::

    data(ttrc)
    cci <- CCI(ttrc[,c("High","Low","Close")])

