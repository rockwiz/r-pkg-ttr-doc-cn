chaikinAD
=========

描述
    Chaikin集散量（即，累计/派发值）衡量一支证券在一段时间内累计的资金流量，其原理与能量潮（OBV）类似，由Marc Chaikin发明

用法
::

    chaikinAD(HLC, volume)

参数
    :HLC: 可强制转换成xts或matrix，包含最高-最低-收盘价序列的对象
    :volume: 与HLC对应的成交量向量或矩阵

说明
    chaikinAD与OBV类似，不同之处在于当收盘价高于/低于昨收时，OBV将今日成交量乘以+1/-1再累加，
    而chaikinAD将今日成交量乘以收盘价位值（Close Location Value，CLV）再累加。

返回值
    一个HLC同类对象或（如果try.xts失败）包含集散量的向量

备注
    Chaikin集散量通过寻找指标相对价格运动的背离来解释。

参考
    可访问以下网址获取该指标的详细说明

    | http://www.fmlabs.com/reference/AccumDist.htm
    | http://www.equis.com/Customer/Resources/TAAZ/?c=3&p=27
    | http://www.linnsoft.com/tour/techind/acc_dis.htm
    | http://stockcharts.com/education/IndicatorAnalysis/indic_AccumDistLine.html

另见
    参见OBV和CLV

范例
::

    data(ttrc)
    ad <- chaikinAD(ttrc[,c("High","Low","Close")], ttrc[,"Volume"])

