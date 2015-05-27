runPercentRank
==============

描述
    This function computes a running/rolling percentage rank.

用法
::

    runPercentRank(x, n = 260, cumulative = FALSE, exact.multiplier = 0.5)

参数
    :x: Object coercible to xts or matrix.
    :n: Number of periods to use in the window or, if cumulative=TRUE, the number of obversations to use before the first result is returned.
    :cumulative: Logical, use from-inception calculation?
    :exact.multiplier: The weight applied to identical values in the window. See details.

说明
    The computation for a percentage rank can vary depending on the weight given to values in the window identical to the value being ranked. This weight can be set using the exact.multiplier argument which defaults to 0.5.

返回值
    A object of percent ranks over a n-period moving window of the same class as x and y or a vector (if try.xts fails).

备注
    It may be important to note that this computation is different from the one used in Microsoft Excel’s PERCENTRANK formula. Excel’s computation is rather strange and gives inconsistent results as it uses interpolation to rank values that are not found within the lookback window.

参考
    The following site(s) were used to code/document this indicator:

    http://en.wikipedia.org/wiki/Percentile_rank

.. TODO
