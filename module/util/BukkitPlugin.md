# BukkitPlugin
## 基本信息
- 类名和包路径: taboolib.platform.util.BukkitPlugin
- 基本用途: 提供对Bukkit平台插件实例的全局访问点
- 类型: Kotlin属性
- 所属模块: bukkit-util

## 类结构
### 公开静态字段
> bukkitPlugin: taboolib.platform.BukkitPlugin -> 获取TabooLib在Bukkit平台的插件实例

## 实现细节
- 使用顶层属性提供对BukkitPlugin.getInstance()的简便访问
- BukkitPlugin是TabooLib在Bukkit平台的主要实现类，继承自JavaPlugin
- 该属性是一个全局访问点，可以在任何导入了该包的代码中使用
- 底层使用了BukkitPlugin类中的静态getInstance()方法获取单例实例

## 使用场景
> 获取插件实例以访问Bukkit API需要的Plugin对象
> 访问插件的数据文件夹、配置文件等资源
> 注册事件、命令或调度任务时需要提供插件实例
> 在无法直接访问插件实例的工具类或静态方法中使用

## 注意事项
> 该属性只能在Bukkit平台环境下使用，在其他平台会抛出ClassNotFoundException
> 在TabooLib的生命周期LOAD阶段之前使用可能会返回null
> 应避免在静态初始化块中过早访问此属性
> 这是一个平台特定的工具，在编写跨平台代码时应使用taboolib.common.platform.function包中的API
