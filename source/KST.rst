KST
===
描述
    确然指标（Know Sure Thing）是一张平滑、求和、变动率指标，由Martin Pring发明

用法
::

    KST(price, n=c(10,10,10,15), nROC=c(10,15,20,30), nSig=9,maType, wts=1:NROW(n), ...)

参数
    :price: 可强制转换成xts或matrix的价格序列
    :n: 计算移动平均时用到的期数向量
    :nROC: 计算ROC时用到的期数向量
    :nSig: 计算KST信号线时用到的期数向量
    :maType: (1) 函数或字符串（要调用的函数名），或者
             (2) 一个列表，包括同(1)一样的第一个分量和由命名（named）分量设定的附加参数
    :wts: 一个与n长度相同的各期权重向量（无需总和为1）
    :...: 第（1）种情况下，其它要传递给maType函数的参数

说明
    KST计算每天（周、月等）相对于若干时期的变动率，这些变动率用给定的移动平均平滑，然后乘以各自权重，再将得到的结果求和。

返回值
    一个price同类对象或（如果try.xts失败）包含KST值的向量

备注
    当KST向上/下穿越其移动均线时，发出看涨/看跌信号。因为KST倾向领先于价格运动，（需要）从价格中确认趋势。

    缺省参数是为日线KST设定的。也可通过以下参数设定长期KST：

    | n=c(9, 12, 18, 24)，此处期间为月，而非日，移动平均期数分别为6、6、6、9个月

参考
    可访问以下网址获取该指标的详细说明

    | http://www.pring.com/index.html
    | http://www.pring.com/movieweb/daily_kst.htm
    | http://www.pring.com/articles/article28.htm
    | http://www.pring.com/movieweb/KST_MCM.htm

另见
    关于移动平均选项，参考EMA、SMA；关于变动率函数，参考ROC；关于一般振荡器，参考MACD

范例
::

    data(ttrc)
    kst <- KST(ttrc[,"Close"])
    kst4MA <- KST(ttrc[,"Close"],
    maType=list(list(SMA),list(EMA),list(DEMA),list(WMA)))

