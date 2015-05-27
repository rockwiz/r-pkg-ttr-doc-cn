rollSFM
=======

描述
    Various functions to analyze data over a moving window of periods.

用法
::

    rollSFM(Ra, Rb, n = 60)

参数
    :Ra: Object coercible to xts or matrix, containing the excess return for an individual security
    :Rb: Object coercible to xts or matrix, containing the market / benchmark return
    :n: Number of periods to use in the window

说明
    A object of the same class as Ra (and Rb?) or a vector (if try.xts fails).

    rollSFM returns single-factor model parameters and R-squared over a n-period moving window.


参考
    The following site(s) were used to code/document this indicator:

    http://en.wikipedia.org/wiki/Simple_linear_regression

.. TODO
