
---
title: Java正则表达式
---

#### 匹配{}及其中的内容
видеть на три {}аршина под землю{ \(землёй\)}
``` java
s.replaceAll("(\\{.*?})","");
видеть на три аршина под землю
```
#### Java手机号隐藏中间4位和邮箱隐藏，身份证隐藏
``` java
//隐藏手机号码中间四位
String phoneNumber = "13234567890";
String resultPhone= phoneNumber.replaceAll("(\\d{3})\\d{4}(\\d{4})","$1****$2");
System.out.println("隐藏后的手机号：" + resultPhone);
//隐藏邮箱
String email = "1234567@qq.com";
String resultEmail = email.replaceAll("(\\w?)(\\w+)(\\w)(@\\w+\\.[a-z]+(\\.[a-z]+)?)", "$1****$3$4");
System.out.println("隐藏后的邮箱：" + resultEmail);
//隐藏身份证
String idCard = "420116199302220456";
String resultIdCard = idCard.replaceAll("(\\d{4})\\d{10}(\\w{4})","$1*****$2");
System.out.println("隐藏后的身份证号：" + resultIdCard);
```
