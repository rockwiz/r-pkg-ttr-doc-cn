GMMA
====

描述
    计算一个序列的Guppy多重移动平均

用法
::

    GMMA(x, short=c(3,5,8,10,12,15), long=c(30,35,40,45,50,60), maType)

参数
    :x: 可强制转换成xts或matrix的价格、成交量或其它序列
    :short: 短期向量
    :long: 长期向量
    :maType: (1) 函数或字符串（要调用的函数名），或者
             (2) 一个列表，包括同(1)一样的第一个分量和由命名（named）分量设定的附加参数

说明
    当“短期组”和“长期组”移动均线交叉时，Guppy多重移动平均给出趋势即将改变的信号。短期/长期移动均线高于长期/短期均线，意味上升/下跌趋势开始。

返回值
    一个x或price同类对象或（如果try.xts失败）包含GMMA值的向量

参考
    可访问以下网址获取该指标的详细说明

    | http://www.investopedia.com/terms/g/guppy-multiple-moving-average.asp

另见
    关于其它衡量趋势方向和强度的指标，参考aroon、CCI、ADX、VHF、TDI

范例
::

    data(ttrc)
    gmma <- GMMA(ttrc[,"Close"])

