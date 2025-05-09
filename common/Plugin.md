# Plugin
## 基本信息
- 类名和包路径: taboolib.common.platform.Plugin
- 基本用途: TabooLib 插件的抽象基类
- 类型: 抽象类
- 所属模块: Common
---
## 类结构
### 公开静态字段
> instance: Plugin -> 插件实例

### 公开静态方法
> getInstance(): Plugin -> 获取插件实例
> setInstance(instance: Plugin): void -> 设置插件实例

### 类内可被访问字段
> (无额外字段)

### 类方法
> onLoad(): void -> 当加载插件时调用
> onEnable(): void -> 当启用插件时调用
> onActive(): void -> 当服务器启动完成时调用
> onDisable(): void -> 当卸载插件时调用
> nativeJarFile(): File -> 重定向插件文件
> nativeDataFolder(): File -> 重定向插件目录
---
## 实现细节
> 定义了插件生命周期方法，与 LifeCycle 对应
> 提供了单例模式的实例访问
> 允许重定向插件文件和目录路径
---
## 使用场景
> 作为 TabooLib 插件的主类
> 实现插件的生命周期管理

## 注意事项
> 所有基于TabooLib开发的，必须继承Plugin
> 插件实例只能设置一次，多次设置会抛出异常
> 生命周期方法默认为空实现，需要子类重写