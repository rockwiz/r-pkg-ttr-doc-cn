stockSymbols
============
描述
    从互联网上获取投资数据

用法
::

    getYahooData(symbol, start, end, freq="daily", type="price",adjust=TRUE, quiet=FALSE)
    stockSymbols(exchange=c("AMEX","NASDAQ","NYSE"), sort.by=c("Exchange","Symbol"), quiet=FALSE)

参数
    :symbol: 雅虎财经网站上的证券代码
    :start: 数值，期望数据的第一天，格式为YYYYMMDD。缺省为序列的第一天
    :end: 数值，期望数据的最后一天，格式为YYYYMMDD。缺省为序列的最后一天
    :freq: 期望数据频率。"daily", "weekly", "monthly"之一
    :type: 返回数据类型，"price"或"split"。 type="split"将返回分拆和分红数据
    :adjust: 逻辑值，如果为TRUE，则开、高、低、收价格将为分红和分拆调整，成交量将为分拆调整
    :quiet: 逻辑值，如果为TRUE，状态信息将打印输出到控制台
    :exchange: 字符向量，证券交易所在交易所
    :sort.by: 返回数据排序列字符向量，必须为"Name"、"Symbol"、"Market.Cap"或"Exchange"之一，或其组合

说明
    getYahooData从雅虎财经网站抓取单个证券数据 ，它也根据股票分拆和分红调整股价，根据分拆调整成交量。

    stockSymbols从nasdaq.com网站抓取证券代码，并调整代码以与从雅虎财经网站的一致。

返回值
    getYahooData返回包含以下列的xts对象：

    :Date: 交易日期，以CCYYMMDD格式
    :Open: 开盘价
    :High: 最高价
    :Low: 最低价
    :Close: 收盘价
    :Volume: 成交量
    :stockSymbols: 返回包含指定交易所所有上市交易代码字符向量。

备注
    stockSymbols 返回的代码也许不是用getYahooData获取数据所需的格式。

    getYahooData仅通过日线数据测试，不知道该函数是否能正确地调整其它频率数据。

范例
::

    ## 以下范例需联网运行

    ibm <- getYahooData("IBM", 19990404, 20050607)
    nyse.symbols <- stockSymbols("NYSE")

