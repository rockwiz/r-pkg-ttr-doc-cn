runSum
======

描述
    各种用于分析经过多期移动窗口数据的函数

用法
::

    runSum(x, n=10, cumulative=FALSE)
    runMin(x, n=10, cumulative=FALSE)
    runMax(x, n=10, cumulative=FALSE)
    runMean(x, n=10, cumulative=FALSE)
    runMedian(x, n=10, non.unique="mean", cumulative=FALSE)
    runCov(x, y, n=10, use="all.obs", sample=TRUE, cumulative=FALSE)
    runCor(x, y, n=10, use="all.obs", sample=TRUE, cumulative=FALSE)
    runVar(x, y=NULL, n=10, sample=TRUE, cumulative=FALSE)
    runSD(x, n=10, sample=TRUE, cumulative=FALSE)
    runMAD(x, n=10, center=NULL, stat="median",
    constant=1.4826, non.unique="mean", cumulative=FALSE)

参数
    :x: 可强制转换成xts或matrix的对象
    :y: 可强制转换成xts或matrix的对象
    :n: 窗口中要用的期数，或者，如果cumulative=TRUE，第一个结果返回前的观测值数量
    :cumulative: 逻辑值，用from-inception计算？
    :sample: 逻辑值，如果为TRUE，样本协方差（分母为n-1）
    :use: 目前，仅实现了"all.obs"
    :non.unique: “mean”、“max”或“min”之一。为均分样本的两个中间值计算各自统计量
    :center: 用来衡量中心化趋势的值，围绕它计算偏差。缺省（NULL）使用中位数（median）
    :stat: 要计算的统计量，“median”或“mean”之一，例如中位数绝对偏差、平均值绝对偏差
    :constant: 用来近似标准差的比例因子

返回值
    一个x和y同类对象或（如果try.xts失败）一个向量：

    :runSum: 返回n期窗口总和
    :runMin: 返回n期窗口最小值
    :runMax: 返回n期窗口最大值
    :runMean: 返回n期窗口平均值
    :runMedian: 返回n期窗口中位数
    :runCov: 返回n期窗口协方差
    :runCor: 返回n期窗口相关系数
    :runVar: 返回n期窗口方差
    :runSD: 返回n期窗口标准差
    :runMAD: 返回n期窗口median/mean绝对偏差
