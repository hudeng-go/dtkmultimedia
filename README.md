# dframework
------------
基于Qt5的开发模板库。

## 特性
1. 使用cmake进行项目管理。
2. 支持编译为debian包。

## 使用方式
1. 克隆本仓库；
2. 配置项目名称：
```shell
bash config.sh -n <name>
```
3. 修改其他配置文件, 例如：README.md

## 风格指南
本风格指南遵循[deepin开源风格指南](https://github.com/linuxdeepin/deepin-styleguide)，在其基础上进行细化拆分，形成适用于开发库的风格指南。

### 基本约定
1. 库必须基于Qt5。
2. 库必须声明命名空间。

### 项目目录规范
 **目录**           | **描述**
------------------|---------------------------------------------------------
 .github/         | github相关文件，一般用来存储工作流
 .reuse/          | license声明文件，项目中应使用reuse工具进行license声明
 .gitignore       | git黑名单，用来过滤不需要推送到仓库中的文件
 .clang-format    | 格式化声明文件，使用该文件进行格式化代码，以保持格式统一性
 README.md        | 项目概述文档
 LICENSE          | 许可协议文件，该文件给github这种仓库使用，项目应使用reuse工具，但协议必须统一，一般为LGPL-v3
 CMakeLists.txt   | 项目文件可放置在最外层
 [debian/]        | debian打包所需文件
 docs/            | 存放文档相关内容，目前作为doxygen生成文档目录
 include/         | 公共头文件目录，所有需要开放的头文件均应放置在此目录
 LINCENSES/       | 许可协议目录，存放该项目所有的许可协议
 misc/            | 存放项目独立的资源或配置文件，如.service .conf .in等
 src/             | 存放源码文件，如 .h .cpp
 [qml/]           | 专门存放qml源码文件，如 .qml
 [translations/ ] | 存放本地化相关文件，如 .ts
 [3rdparty/]      | 存放第三方库或组件。**请注意，如果仓库内包含对应项目，请使用仓库内的版本，不允许另行提供版本包含至项目内**
 [tests/]         | 单元测试相关代码存放目录
 [tools/]         | 小工具存放目录
 [examples/]      | 示例存放目录

### 命名约定

#### 通用规则
1. 尽可能使用描述性的命名，尽可能使用全单词组合的命名，务必不要使用缩写或简写。

#### 项目命名
项目应该使用全小写的命名方式，单词使用-进行连接，对于仅仅对DBus进行封装的项目，应使用name-qt5的方式进行命名，如：power-qt5；若是对其他开源库进行二次封装，应使用d_name_的方式进行命名：如dpower。

#### 文件命名
1. 源文件需使用单词组合并且全小写，如：powermanager.h，必要时，可使用加下划线组合的方式，如：powermanager\_p.h；当该源文件为dde实现，则需以d_name_的方式进行命名：如dpowermanager.h
2. 配置文件应使用项目名+后缀名进行命名，如：power-qt5.conf 或者 dpower.conf

#### 其他命名
参考[deepin开源风格指南](https://github.com/linuxdeepin/deepin-styleguide)<br>
值得注意的有两点：
1. 命名空间的首字母必须为‘D’，如：DTest。
2. 类名应声明为两种类型，并且第二种类型继承自第一种类型，若没有第二种类型，则只使用第一种类型即可：
    1. 封装上游的接口：其类名应该是一个通用的名称，如：Test。
    2. dde实现的接口：其类名应是一个以‘D’开头的名称，如：DTest。
