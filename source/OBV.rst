OBV
===

描述
    能量潮（On Balance Volume ，OBV）衡量流入或流出一支证券的资金，与Chaikin集散量类似（Chaikin AD）

用法
::

    OBV(price, volume)

参数
    :price: 可强制转换成xts或matrix的价格序列
    :volume: 与price对应的成交量序列，可强制转换成xts或matrix

说明
    OBV根据证券价格每天收于较高/较低水平，加入（减去）当天的成交量进行总和累积。

返回值
    一个price和volume同类对象或（如果try.xts失败）包含OBV值的向量

备注
    OBV经常用来和当前证券的价格图比较，来寻找背离/确认。

参考
    可访问以下网址获取该指标的详细说明

    | http://www.fmlabs.com/reference/OBV.htm
    | http://www.equis.com/Customer/Resources/TAAZ?c=3&p=82
    | http://linnsoft.com/tour/techind/obVol.htm
    | http://stockcharts.com/education/IndicatorAnalysis/indic-obv.htm

另见
    chaikinAD.

范例
::

    data(ttrc)
    obv <- OBV(ttrc[,"Close"], ttrc[,"Volume"])

