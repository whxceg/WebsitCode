
---
title: Gradle将依赖库的proguard-rules.pro文件打包进aar
---

#### Gradle将依赖库的proguard-rules.pro文件打包进aar
``` gradle
defaultConfig {
     minSdkVersion 19
     targetSdkVersion 26
     versionCode 1
     versionName "1.0"
     // 配置此参数，方可将混淆文件打包进aar
     consumerProguardFiles 'proguard-rules.pro'
 }
```

