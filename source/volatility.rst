volatility
==========

描述
    精选波动性估计/指标

用法
::

    volatility(OHLC, n=10, calc="close", N=260, ...)

参数
    :OHLC: 可强制转换成xts或matrix，包含开-高-低-收价格序列（或者仅收盘价，如果calc="close"）的对象
    :n: 用于波动性估计的期数
    :calc: 估计数的计算（类型）
    :N: 每年期数
    :...: 传入其它方法或从其它方法传出的参数

说明
    收-对-收波动 （收盘价）：用收盘价-对-收盘价计算历史波动性

    OHLC波动：Garman和Klass（garman.klass），估计历史波动性的Garman和Klass估算器假设零漂移布朗运动和无开盘跳空（即今开=昨收）。该估算器的效率7.4倍于收盘-对-收盘估算器。

    高-低波动性：Parkinson （parkinson），估计历史波动性的Parkinson公式完全基于高-低价格。

    OHLC波动性：Rogers and Satchell（rogers.satchell），Roger和Satchell历史波动估算器允许非零漂移，但假设无开盘跳空。

    OHLC波动性：Garman和Klass – 杨和张（gk.yz），该估算器是Garman和Klass 估算器的改进版本，它允许开盘跳空。

    OHLC波动性：杨和张（yang.zhang），杨和张历史波动估算器有最小的估计误差，并与漂移和开盘跳空无关。它可以解释为Rogers和Satchell 估算器、收-开波动、开-收波动的加权平均。

返回值
    一个OHLC同类对象或（如果try.xts失败）包含选择的波动性估计数的向量

参考
    可访问以下网址获取该指标的详细说明

    Close-to-Close Volatility (close):

    | http://www.sitmo.com/eq/172

    OHLC Volatility: Garman Klass (garman.klass):

    | http://www.sitmo.com/eq/402

    High-Low Volatility: Parkinson (parkinson):

    | http://www.sitmo.com/eq/173

    OHLC Volatility: Rogers Satchell (rogers.satchell):

    | http://www.sitmo.com/eq/414

    OHLC Volatility: Garman Klass - Yang Zhang (gk.yz):

    | http://www.sitmo.com/eq/409

    OHLC Volatility: Yang Zhang (yang.zhang):

    | http://www.sitmo.com/eq/417

另见
    参考TR和chaikinVolatility等其它衡量波动性的指标

范例
::

    data(ttrc)
    ohlc <- ttrc[,c("Open","High","Low","Close")]
    vClose <- volatility(ohlc, calc="close")
    vGK <- volatility(ohlc, calc="garman")
    vParkinson <- volatility(ohlc, calc="parkinson")
    vRS <- volatility(ohlc, calc="rogers")

