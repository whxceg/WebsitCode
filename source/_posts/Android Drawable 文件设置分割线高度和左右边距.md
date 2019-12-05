---
title: Android Drawable 文件设置分割线高度和左右边距
---

1.在shape里设置padding无效代码如下。

``` xml
<?xml version="1.0" encoding="UTF-8"?>
<shape xmlns:android="http://schemas.android.com/apk/res/android">
    <padding
        android:left="10dp"
        android:right="10dp" />
    <size android:height="1dp" />
    <solid android:color="@color/CF1F0F0" />
</shape>
```
2.解决办法
使用layer-list
``` xml
<?xml version="1.0" encoding="UTF-8"?>
<layer-list xmlns:android="http://schemas.android.com/apk/res/android">
    <item android:left="10dp">
        <shape>
            <size android:height="1px" />
            <solid android:color="@color/CF1F0F0" />
        </shape>
    </item>
</layer-list>
```
使用inset
``` xml
<?xml version="1.0" encoding="UTF-8"?>
<inset xmlns:android="http://schemas.android.com/apk/res/android"
    android:insetLeft="10dp"
    android:insetRight="10dp">
    <shape>
        <size android:height="10dp" />
        <solid android:color="@color/CF1F0F0" />
    </shape>
</inset>
```
