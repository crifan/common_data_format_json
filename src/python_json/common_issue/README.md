# 常见问题

此处整理Python处理json期间，遇到的一些问题。

## Python处理ISODate的json

问题：

[python读取json文件时遇到ISOdate，会报错，怎么处理能够读取数据，新手小白一枚-CSDN论坛](https://bbs.csdn.net/topics/397512829)

```json
{
  "createtime" : ISODate("2020-06-24T06:29:33.473Z"),
  "updatetime" : ISODate("2020-07-09T02:23:04.553Z")
}
{
  "createtime" : ISODate("2020-06-24T06:38:15.86Z"),
  "updatetime" : ISODate("2020-07-09T02:35:42.092Z")
}
{
  "createtime" : ISODate("2020-06-24T07:00:33.919Z"),
  "updatetime" : ISODate("2020-08-14T07:01:36.704Z")
}
```

解答：

你这个json数据=json格式的字符串，不合法 = 不符合JSON的语法


具体有3点
1. 最外层缺少中`括号`=`[]`
2. 每个dict字典之间缺少`逗号=``,`
3. 每个dict字典内部有多余的ISODate-》需要改为字符串本身

比如 应该 可以 改为：

```json
[
  {
    "createtime": "2020-06-24T06:29:33.473Z",
    "updatetime": "2020-07-09T02:23:04.553Z"
  },
  {
    "createtime": "2020-06-24T06:38:15.86Z",
    "updatetime": "2020-07-09T02:35:42.092Z"
  },
  {
    "createtime": "2020-06-24T07:00:33.919Z",
    "updatetime": "2020-08-14T07:01:36.704Z"
  }
]
```

才能被正确解析

不过此处的时间是字符串，想要转换为Datetime的对象

需要先了解

[ISO 8601 - 维基百科，自由的百科全书](https://zh.wikipedia.org/wiki/ISO_8601)

[ISO 8601 - Wikipedia](https://en.wikipedia.org/wiki/ISO_8601)

[Date and Time Formats](https://www.w3.org/TR/NOTE-datetime)

格式：

>   Complete date plus hours, minutes, seconds and a decimal fraction of a
second
>
>      YYYY-MM-DDThh:mm:ss.sTZD (eg 1997-07-16T19:20:30.45+01:00)

举例

```bash
1994-11-05T13:15:30Z
```

---

TODO：

加上Python代码

演示如何把上述 ISO 8601的日期时间的字符串

```bash
"2020-06-24T06:38:15.86Z”
"2020-07-09T02:35:42.092Z"
```

转换为 Datetime 对象
