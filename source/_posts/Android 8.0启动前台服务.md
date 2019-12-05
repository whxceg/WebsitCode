---
title: Android 8.0启动服务
---

Android 8.0不允许创建后台服务，启动服务可以使用系统兼容方法

``` java
ContextCompat.startForegroundService(context, intent);
```

应用必须在创建服务后的五秒内调用该服务的 startForeground() 函数，否则会出现ANR。

``` java
  @Override
    public void onCreate() {
        super.onCreate();
        if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.O) {
            NotificationChannel channel = new NotificationChannel("PLAYER", "播放器", NotificationManager.IMPORTANCE_MIN);
            NotificationManager manager = (NotificationManager) getSystemService(Context.NOTIFICATION_SERVICE);
            manager.createNotificationChannel(channel);
            NotificationCompat.Builder builder = new NotificationCompat.Builder(this, "PLAYER");
            startForeground(1, builder.build());
        }
    }
```

注意通知的级别

| 用户通知级别   |Android8.0及以上 |Android7.0及以下 |	
| ------------  | ------------    | ------------    |
|紧急级别（发出通知声音并显示为提示通知）   |  IMPORTANCE_HIGH	| PRIORITY_HIGH或者PRIORITY_MAX |
|高级别（发出通知声音并且通知栏有通知）	  |  IMPORTANCE_DEFAULT	| PRIORITY_DEFAULT |
|中等级别（没有通知声音但通知栏有通知）	  |  IMPORTANCE_LOW	| PRIORITY_LOW |
|低级别（没有通知声音也不会出现在状态栏上）  |	IMPORTANCE_MIN	| PRIORITY_MIN | 
