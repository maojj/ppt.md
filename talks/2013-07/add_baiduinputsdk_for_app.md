#【iOS】应用内使用百度输入法

=====
## 主要内容

1. 简介
1. 使用方法

=====

### 百度输入法SDK简介

简介见[官方网站](http://developer.baidu.com/wiki/index.php?title=%E5%B8%AE%E5%8A%A9%E6%96%87%E6%A1%A3%E9%A6%96%E9%A1%B5/%E7%99%BE%E5%BA%A6%E6%89%8B%E6%9C%BA%E8%BE%93%E5%85%A5%E6%B3%95SDK%EF%BC%88iOS%E7%89%88%EF%BC%89)

=====
### 使用百度输入法
* 百度输入法官网文档较旧，且缺图，另外有些注意事项，故自己写了个
* 新建一个项目，或者打开原项目（这里以一个新项目BaiduInputDemo为例示范）

=====
### 将BaiduInputSDK目录copy到工程目录下
* 注意事项：拷贝文件时，可能有.svn目录需要清理，清理命令:
```
find . -name .svn | xargs rm -rf
```

=====
### 添加SDK头文件和静态库
* 导入sdk目录下BI_开头的5个.h文件，并添加输入法静态库

=====
### 添加sdk所需的framework

AudioToolbox.framework
libz.dylib
Addressbook.framework （可不要）
SystemConfiguration.framework

=====
* 点击工程跟目录 -〉选中Target -〉Build Phrases-〉Link Binary With Libraries->“+”，在”choose frameworks and libraries to add”中搜索并添加

=====
###  添加资源文件（注意这步）

* 选中所有需要添加的词库（raw），皮肤文件以及图片资源，并选择”Create folder reference for any added folders”,（切记） click Add 添加选中的资源



=====
### 使用SDK

``` objective-c
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions
{
    // other code
    BIUnzipSkinFiles();
    BI_RootViewSDK *sdk = [BI_RootViewSDKcreate:nil];
    returnYES;
}
```


