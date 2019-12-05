---
title: Android PopupWindow showAsDropDown 7.0上无效
---

Android PopupWindow showAsDropDown 7.0上无效

``` java
 if (Build.VERSION.SDK_INT >= 24) {
    Rect rect = new Rect();
    view.getGlobalVisibleRect(rect);
    int h = view.getResources().getDisplayMetrics().heightPixels - rect.bottom;
    mPopupWindow.setHeight(h);
}
mPopupWindow.showAsDropDown(view);
```
