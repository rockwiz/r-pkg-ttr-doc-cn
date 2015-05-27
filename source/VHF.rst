VHF
===

描述
    垂直水平滤子（Vertical Horizontal Filter，VHF）试图发觉趋势的开始和终结，由Adam White发明

用法
::

    VHF(price, n=28)

参数
    :price: 可强制转换成xts或matrix，包含一个收盘价序列或一个最高-最低-收盘价序列的对象
    :n: 期数

说明
    VHF通过将n期将最高的最高价减去n期最低的最低价，并将结果除以n期收盘滚动求和计算而来。

返回值
    一个HLC同类对象或（如果try.xts失败）一个包含VHF值的向量

备注
    如果参数给的是收盘价，函数仅使用该序列计算最大/最小值（缺省）；如果提供的是最高-最低-收盘（HLC）价格序列，则利用最高/最低价计算最大/最小值（增加了灵活性）。

参考
    可访问以下网址获取该指标的详细说明

    | http://www.equis.com/Customer/Resources/TAAZ?c=3&p=119

另见
    参考aroon、CCI、ADX、TDI、GMMA等其它衡量趋势方向/强度的指标

范例
::

    data(ttrc)
    vhf.close <- VHF(ttrc[,"Close"])
    vhf.hilow <- VHF(ttrc[,c("High","Low","Close")])

