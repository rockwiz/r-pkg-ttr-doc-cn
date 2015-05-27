BBands
======

描述
    布林带是一种比较一段时期内证券波动性和价格水平的方法，由John Bollinger发明

用法
::

    BBands(HLC, n=20, maType, sd=2, ...)

参数
    :HLC: 可强制转换成xts或matrix，包含最高-最低-收盘价序列的对象
    :n: 移动平均的期数
    :maType: 函数或字符串（要调用的函数名）
    :sd: 要使用的标准差数值
    :...: 其它要传给maType函数的参数

说明
    布林带包含三条线：

    * 中线通常是典型价格20天简单移动平均（SMA），上线和下线分布是移动平均加上和减去标准差倍数（通常为2）的值。
    * 中线经常用典型价格计算，但是如果仅提供单变量序列（如收盘价、加权收盘价、中位价等），那么将用该序列替代之。

返回值
    一个HLC或matrix（如果try.xts失败）同类，包含以下列的对象

    :dn: 布林带下线
    :ma: 中线，即移动平均线（参见备注）
    :up: 序列的真实最高价
    :pctB: 序列的真实最低价

备注
    使用其它非简单移动平均（SMA）将导致移动平均计算和标准差计算不一致。因为按定义，滚动标准差使用简单移动平均。

参考
    可访问以下网址获取该指标的详细说明

    | http://www.fmlabs.com/reference/Bollinger.htm
    | http://www.fmlabs.com/reference/BollingerWidth.htm
    | http://www.equis.com/Customer/Resources/TAAZ/?c=3&p=36
    | http://www.linnsoft.com/tour/techind/bb.htm
    | http://stockcharts.com/education/IndicatorAnalysis/indic_Bbands.html
    | http://stockcharts.com/education/IndicatorAnalysis/indic_BBWidth.htm

    关于布林带的原理和使用，请参阅拙作《K线图形态和常用技术指标使用手册》（P183）

另见
    关于移动平均选项，参考EMA、SMA

范例
::

    ## 下面列子显示了使用高-低-收价格序列和仅用收盘价序列
    ## 计算布林带的不同
    data(ttrc)
    bbands.HLC <- BBands( ttrc[,c("High","Low","Close")] )
    bbands.close <- BBands( ttrc[,"Close"] )

