## 简介

本代码演示了从某接口里拿取指定格式(如二维数组)数据转化为cvs文件的过程。

网上找的第三方node-csv之类的工具都没有使用成功，故而自己写了份demo。

## 启动过程

```
# 启动api.json的访问服务，路径为localhost:8094/api.json
npm run dev
# 运行转化脚本，第三个参数为api的请求地址，第四个参数为欲保存的文件名
node client.js /api.json test.csv
```

## 原理

把如下二维数组

```
[
    [
        1493078400,
        10000
    ],
    [
        1493078401,
        10001
    ],
    [
        1493078402,
        10002
    ],
    [
        1493078403,
        10003
    ],
    [
        1493078404,
        10004
    ]
]
```

转化为如下的字符串并写入文件中，保存成csv后缀格式的文件。就可以生成表格

```
date,price
1493078400,10000
1493078401,10001
1493078402,10002
1493078403,10003
1493078404,10004
```

## 附上csv标准格式

1. CSV的全称是叫Comma Separated Value 
2. CSV的MIME类型是text/csv 
3. CSV文件中的每一行数据，作为一行记录，每一行数据后面跟着(回车+换行符)即CRLF，但有些资料中也提到了单个CR或者LF均可，但标准rfc文档中用到的是CR+LF 
4. 每行数据中，每个字段之间均必须用半角逗号comma进行分隔，这也是为什么叫Comma Separated的来由。且每行的最后一个字段后应该只有CRLF,不应该再有逗号 
5. 最后一行后面可以不加CRLF 
6. 在逗号分隔开的每个字段中，前面的空白和后面的空白会被忽略，但单个字段内部的空白会被保留，类似于Java中的trim方法
7. 如果存在转义字符则需要用双引号来包裹，常见转义字符有逗号，引号，回车换行符。


## 参考

[CSV标准格式](http://blog.csdn.net/zlzlei/article/details/9236403)
