# NMSEntity

## 基本信息
- 类名和包路径: taboolib.module.nms.NMSEntity
- 基本用途: 提供跨版本的实体生成和语言文件节点获取功能
- 类型: 抽象类
- 所属模块: bukkit-nms-stable

## 类结构

### 公开静态字段
> instance: NMSEntity -> 通过 nmsProxy 懒加载的单例实例

### 公开静态方法
> 无

### 类内可被访问字段
> 无

### 类方法
> spawnEntity<T : Entity>(location: Location, entity: Class<T>, callback: Consumer<T>): T -> 在指定位置生成实体，并在生成前执行回调函数
> getLanguageKey(entity: Entity): MinecraftLanguage.LanguageKey -> 获取实体的语言文件节点

## 实现细节
- 使用 `nmsProxy<NMSEntity>()` 创建代理实例，实际实现类为 `NMSEntityImpl`
- 通过 `unsafeLazy` 延迟初始化单例实例
- 提供两个扩展函数简化使用：`Location.spawnEntity()` 和 `Entity.getLanguageKey()`
- 实现类 `NMSEntityImpl` 根据不同的 Minecraft 版本使用不同的方法生成实体和获取语言文件节点
- 对村民实体进行特殊处理，根据不同版本获取其职业相关的语言文件节点
- 支持从 1.8 到 1.21 版本的 Minecraft

## 使用场景
> 在需要生成实体并在生成前进行配置时使用
> 在需要获取实体的本地化名称时使用
> 在插件开发中需要跨版本兼容时使用

## 注意事项
> 不同版本的 Minecraft 对实体的处理方式不同，特别是村民和马匹等特殊实体
> 在 1.19.3 及以上版本中，可以使用 Bukkit 的 Translatable 接口简化操作
> 对于村民实体，需要根据不同版本获取其职业信息
> 在低版本（1.8-1.12）中，某些实体（如马和村民）的处理方式特别复杂
