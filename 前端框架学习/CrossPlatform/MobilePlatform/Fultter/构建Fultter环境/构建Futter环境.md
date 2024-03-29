# 安装和环境配置

#### 安装

按照官方文档给的教程安装**Fultter**，以及  **Android Studio**，和对应的虚拟机以及插件。

#### 在中国网络环境下使用 Flutter

使用Fultter镜像时，把镜像环境变量按照文档配置，建议使用清华镜像，另外两个镜像在我的命令行里会报禁止访问。

\flutter\packages\flutter_tools\lib\srchttp_host_validator.dart 这个文件内的链接也要配置国内源，否则执行时会报错。

#### 运行

Flutter配置Gradle国内镜像，如果不为flutter配置Gradle国内镜像，则运行程序到虚拟设备上时会报错网络链接不上

https://juejin.cn/post/7299346813261676544

#### Flutter配置Gradle镜像，解决国内下载慢问题

##### 未优化之前

程序运行时会卡在`Running Gradle task 'assembleDebug'...`如下提示信息

```dart
dart复制代码Flutter assets will be downloaded from https://storage.flutter-io.cn. Make sure you trust this source!
Launching lib\main.dart on sdk gphone64 x86 64 in debug mode...
Running Gradle task 'assembleDebug'...
```

此时Gradle正在下载gradle构建工具以及相关依赖库，由于官方gradle默认配置的依赖下载服务器处于国外，国内用户访问非常缓慢，常常一个依赖下载就要花半天时间，好在国内有阿里、清华等镜像源，我们可以配置镜像代理加快依赖的下载

##### 优化步骤

###### 修改build.gradle

进入项目目录的`android/build.gradle`，修改为如下，注意不要注释掉`google()`和`mavenCentral()`，因为部分依赖可能镜像源没有，`gradle`找不到的话会报错

```gradle
gradle复制代码buildscript {
    ext.kotlin_version = '1.7.10'
    repositories {
        maven { url 'https://maven.aliyun.com/repository/public/' }
        maven { url 'https://maven.aliyun.com/repository/spring/'}
        maven { url 'https://maven.aliyun.com/repository/google/'}
        maven { url 'https://maven.aliyun.com/repository/gradle-plugin/'}
        maven { url 'https://maven.aliyun.com/repository/spring-plugin/'}
        maven { url 'https://maven.aliyun.com/repository/grails-core/'}
        maven { url 'https://maven.aliyun.com/repository/apache-snapshots/'}
        google()
        mavenCentral()
    }

    dependencies {
        classpath 'com.android.tools.build:gradle:7.3.0'
        classpath "org.jetbrains.kotlin:kotlin-gradle-plugin:$kotlin_version"
    }
}

allprojects {
    repositories {
        maven { url 'https://maven.aliyun.com/repository/public/' }
        maven { url 'https://maven.aliyun.com/repository/spring/'}
        maven { url 'https://maven.aliyun.com/repository/google/'}
        maven { url 'https://maven.aliyun.com/repository/gradle-plugin/'}
        maven { url 'https://maven.aliyun.com/repository/spring-plugin/'}
        maven { url 'https://maven.aliyun.com/repository/grails-core/'}
        maven { url 'https://maven.aliyun.com/repository/apache-snapshots/'}
        google()
        mavenCentral()
    }
}

rootProject.buildDir = '../build'
subprojects {
    project.buildDir = "${rootProject.buildDir}/${project.name}"
}
subprojects {
    project.evaluationDependsOn(':app')
}

tasks.register("clean", Delete) {
    delete rootProject.buildDir
}
```

###### 修改gradle-wrapper.properties

进入`android/wrapper/gradle-wrapper.properties`文件

`distributionUrl`的值用镜像源替代，需要注意的是后面的gradle版本需要和替换镜像源前的`gradle`版本一致

```gradle
gradle复制代码distributionBase=GRADLE_USER_HOME
distributionPath=wrapper/dists
zipStoreBase=GRADLE_USER_HOME
zipStorePath=wrapper/dists
distributionUrl=https\://mirrors.cloud.tencent.com/gradle/gradle-7.5-all.zip
```

作者：易秋
链接：https://juejin.cn/post/7299346813261676544
来源：稀土掘金
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。