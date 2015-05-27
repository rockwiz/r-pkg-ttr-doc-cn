ADX
===

描述
    平均趋向指标，一种常用的趋势衡量指标。与趋向指数（DMI）一样，由威尔斯・威尔德（Welles Wilder）发明

用法
::

    ADX(HLC, n=14, maType, ...)

参数
    :HLC: 可强制转换成xts或matrix，包含最高价-最低价-收盘价序列的对象
    :n: 用于DX计算的期数（非ADX计算）
    :maType: 函数或字符串（要调用的函数名）
    :...: 其它要传给maType函数的参数

说明
    DIp/DIn（正/负）是涨/跌真实范围的百分比。

返回值
    一个HLC或matrix（如果try.xts失败）同类，包含以下列的对象

    :DIp: 正趋向指数
    :DIn: 负趋向指数
    :DX: 趋向指数
    :ADX: 平均趋向指数（趋势强度）

备注
    当DX/ADX发出强劲趋势信号时，+/-DI 穿越-/+DI 产生一个买入/卖出信号。高/低DX预示强/弱趋势。DX通常用移动平均来平滑（如，ADX）

参考
    可访问以下网址获取该指标的详细说明

    | http://www.fmlabs.com/reference/DI.htm
    | http://www.fmlabs.com/reference/DX.htm
    | http://www.fmlabs.com/reference/ADX.htm
    | http://www.fmlabs.com/reference/ADXR.htm
    | http://www.equis.com/Customer/Resources/TAAZ/Default.aspx?c=3&p=49
    | http://linnsoft.com/tour/techind/dirInd.htm
    | http://linnsoft.com/tour/techind/adx.htm
    | http://linnsoft.com/tour/techind/adxr.htm
    | http://stockcharts.com/education/IndicatorAnalysis/indic_ADX.html

    也可参考拙作《K线图形态和常用技术指标使用手册》（P217），了解相关指标DMI的介绍

另见
    移动平均选项，参考EMA、SMA等指标及其提示部分。DX计算使用 ATR。其它衡量趋势方向/强弱的指标，如aroon、CCI、TDI、VHF、GMMA。

范例
::

    data(ttrc)
    dmi.adx <- ADX(ttrc[,c("High","Low","Close")])


