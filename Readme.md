# CHINA ID(中国大陆身份证)

[![Build Status](https://travis-ci.org/sleagon/chinaid.svg?branch=master)](https://travis-ci.org/sleagon/chinaid)

> 校验、解析中国大陆身份证号

## 身份证号校验

```go
package main
import (
    "log"
    "github.com/sleagon/chinaid"
)

func main() {
    id := chinaid.IDCard("420683199006041237")
    result := id.Valid()
    log.Println(">>>>", result)
}
```


## 身份证信息解析

```go
package main
import (
    "log"
    "github.com/sleagon/chinaid"
)

func main() {
    id := chinaid.IDCard("420683199006041237")
    result, err := id.Decode()
    if err != nil {
        log.Println("非法身份证号")
        return
    }
    log.Println(">>>>", result)
}
```

## 结果示例

```json
{
    "sex":       1,
    "code":      420683,
    "district":  "枣阳市",
    "city":      "襄阳市",
    "province":  "湖北省",
    "birthday":  "1990-06-04T00:00:00Z"
}
```

## 地域映射

身份证里的地域码往地域转换的映射表来自[中华人民共和国民政部][1]官网，本项目里目前用的版本是2018年5月更新的版本，后续会不定期更新。

## 依赖示例

> dep

```yml
[[constraint]]
   name = "github.com/sleagon/chinaid"
   version = "0.2"
```

[1]: http://www.mca.gov.cn/