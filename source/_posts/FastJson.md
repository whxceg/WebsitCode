---
title: FastJson常用问题
---

### 1、JSON TypeReference 复杂类型转换

``` java
List<T> list = JSON.parseObject(json, new TypeReference<List<T>>() {});
String[] array = JSON.parseObject(json, new TypeReference<String[]>() {});
```
### 2、不同字段名映射到同一字段

``` java
@JSONField(alternateNames = {"Code","XXCode"})
public void setCode(String code) {
    Code = code;
}
```
