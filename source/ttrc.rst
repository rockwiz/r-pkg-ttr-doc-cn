ttrc
====

描述
    开盘、最高、最低、收盘价和成交量从1985年1月2日到2006年12月31日的历史数据

用法
::

    data(ttrc)

格式
    ========== ============== ======== ======== ======== ======== ======== ========
    日期:       Class ’Date’   5480     5481     5482     5485     5486     ...
    开盘:       num            3.18     3.09     3.11     3.09     3.10     ...
    最高:       num            3.18     3.15     3.12     3.12     3.12     ...
    最低:       num            3.08     3.09     3.08     3.07     3.08     ...
    收盘:       num            3.08     3.11     3.09     3.10     3.11     ...
    成交量:      num           1870906  3099506  2274157  2086758  2166348  ...
    ========== ============== ======== ======== ======== ======== ======== ========

说明
提供这些数据是为举例时无需连接互联网，它们不代表真实证券。

源
    随机生成。

范例
::

    data(ttrc)
    plot(tail(ttrc[,"Close"],100), type="l")


