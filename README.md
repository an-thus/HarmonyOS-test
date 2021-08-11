# HarmonyOS学习
HarmonyOS是一款面向万物互联时代的、全新的分布式操作系统。
在传统的单设备系统能力基础上，HarmonyOS提出了基于同一套系统能力、适配多种终端形态的分布式理念，能够支持手机、平板、智能穿戴、智慧屏、车机等多种终端设备，提供全场景（移动办公、运动健康、社交通信、媒体娱乐等）业务能力。

# 用户应用程序
在HarmonyOS上运行的应用，有两种形态：
传统方式的需要安装的应用。
提供特定功能，免安装的应用（即原子化服务）。

# 用户应用程序包结构
HarmonyOS的用户应用程序包以APP Pack（Application Package）形式发布，它是由一个或多个HAP（HarmonyOS Ability Package）以及描述每个HAP属性的pack.info组成。HAP是Ability的部署包，HarmonyOS应用代码围绕Ability组件展开。
一个HAP是由代码、资源、第三方库及应用配置文件组成的模块包，可分为entry和feature两种模块类型。
entry：应用的主模块。一个APP中，对于同一设备类型必须有且只有一个entry类型的HAP，可独立安装运行。
feature：应用的动态特性模块。一个APP可以包含一个或多个feature类型的HAP，也可以不含。只有包含Ability的HAP才能够独立运行。

# Ability
Ability是应用所具备的能力的抽象，一个应用可以包含一个或多个Ability。Ability分为两种类型：FA（Feature Ability）和PA（Particle Ability）。FA/PA是应用的基本组成单元，能够实现特定的业务功能。FA有UI界面，而PA无UI界面。
FA支持Page Ability：
Page模板是FA唯一支持的模板，用于提供与用户交互的能力。一个Page实例可以包含一组相关页面，每个页面用一个AbilitySlice实例表示。

PA支持Service Ability和Data Ability：
Service模板：用于提供后台运行任务的能力。
Data模板：用于对外部提供统一的数据访问抽象。

# 库文件
库文件是应用依赖的第三方代码（例如so、jar、bin、har等二进制文件），存放在libs目录。

# 资源文件
应用的资源文件（字符串、图片、音频等）存放于resources目录下。

# 配置文件
配置文件 (config.json) 是应用的Ability信息，用于声明应用的Ability，以及应用所需权限等信息。

# pack.info
描述应用软件包中每个HAP的属性，由IDE编译生成，应用市场根据该文件进行拆包和HAP的分类存储。HAP的具体属性包括：
delivery-with-install: 表示该HAP是否支持随应用安装。“true”表示支持随应用安装；“false”表示不支持随应用安装。
name：HAP文件名。
module-type：模块类型，entry或feature。
device-type：表示支持该HAP运行的设备类型。

# HAR
HAR（HarmonyOS Ability Resources）可以提供构建应用所需的所有内容，包括源代码、资源文件和config.json文件。HAR不同于HAP，HAR不能独立安装运行在设备上，只能作为应用模块的依赖项被引用。
