MFI
===

描述
    资金流量指数（Money Flow Index）是一段时间内正资金流和负资金流的比率
用法
::

    MFI(HLC, volume, n=14)

参数
    :HLC: 可强制转换成xts或matrix，包含最高-最低-收盘价序列的对象
    :volume: 与HLC对应的成交量向量或矩阵
    :n: 要计算的期数

说明
    MFI是价格和成交量的乘积。今天的价格高于/低于昨天的价格，产生正/负的资金流。MFI通过将过去n期正资金流除以负资金流计算而来，
    其范围在0和100之间。MFI通常用典型价格计算，但如果是提供一个单变量序列（如收盘价、加权收盘价、中位价等），那么就用那些值替代。

返回值
    一个HLC和volume同类对象或（如果try.xts失败）一个包含MFI值的向量

备注
    MFI和价格之间的背离可以看做一个反转指示。另外，高于/低于80/20意味市场顶部/底部。

参考
    可访问以下网址获取该指标的详细说明

    | http://www.fmlabs.com/reference/default.htm?url=MoneyFlowIndex.htm
    | http://www.linnsoft.com/tour/techind/mfi.htm
    | http://stockcharts.com/school/doku.php?id=chart_school:technical_indicators:money_flow_index_mfi

    关于MFI的原理和使用，请参阅拙作《K线图形态和常用技术指标使用手册》（P189）

另见
    OBV和CMF

范例
::

    data(ttrc)
    mfi <- MFI(ttrc[,c("High","Low","Close")], ttrc[,"Volume"])


