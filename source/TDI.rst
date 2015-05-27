TDI
===

描述
    趋势探测指数（Trend Detection Index，TDI）试图发觉趋势的开始和终结，由M.H. Pee.发明

用法
::

    TDI(price, n=20, multiple=2)

参数
    :price: 可强制转换成xts或matrix价格序列
    :n: 要使用的期数
    :multiple: 要使用的倍数因子（2）

说明
    TDI是（1）n天动量和的绝对值，减去（2）n天动量绝对值的和乘以倍数因子的值，减去（3）n天动量的绝对值。

    即：TDI=（1）-[（2）-（3）]

    方向指数是过去n天动量和，详细说明参见“参考”链接

返回值
    一个price同类对象或（如果try.xts失败）包含以下列的矩阵：

    :tdi: 趋势探测指数
    :di: 方向指标

备注
    正/负TDI值给出趋势/盘整信号，一个正/负方向指标给出上升/下跌趋势信号。即，当TDI和方向指标均为正时买入，当TDI为正而方向指标为负时卖出。

参考
    可访问以下网址获取该指标的详细说明
    | http://www.linnsoft.com/tour/techind/tdi.htm

另见
    参考aroon、CCI、ADX、VHF和GMMA，了解其它衡量趋势方向/强度指标

范例
::

    data(ttrc)
    tdi <- TDI(ttrc[,"Close"], n=30)

