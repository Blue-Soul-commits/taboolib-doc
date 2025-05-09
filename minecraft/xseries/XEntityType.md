# XEntityType

## 基本信息
- 类名和包路径: taboolib.library.xseries.XEntityType
- 基本用途: 提供跨版本的 Minecraft 实体类型枚举，解决不同版本 EntityType 命名差异问题
- 类型: 枚举类
- 所属模块: platform-bukkit-impl (TabooLib XSeries 库)

## 类结构

### 公开静态字段
> REGISTRY: XRegistry<XEntityType, EntityType> -> 实体类型注册表，用于管理 XEntityType 与 Bukkit EntityType 的映射关系

### 公开静态方法
> getValues(): Collection<XEntityType> -> 获取所有可用的 XEntityType 值
> of(entity: Entity): XEntityType -> 根据 Bukkit Entity 对象获取对应的 XEntityType
> of(entityType: EntityType): XEntityType -> 根据 Bukkit EntityType 获取对应的 XEntityType
> of(entityType: String): Optional<XEntityType> -> 根据实体类型名称获取对应的 XEntityType，返回 Optional

### 类内可被访问字段
> entityType: EntityType -> 当前 XEntityType 对应的 Bukkit EntityType

### 类方法
> friendlyName(): String -> 获取实体类型的友好名称，例如 "ZOMBIE_VILLAGER" 转换为 "Zombie Villager"
> isSupported(): boolean -> 检查当前服务器版本是否支持此实体类型
> or(other: XEntityType): XEntityType -> 如果当前实体类型不受支持，则返回替代实体类型
> getNames(): String[] -> 获取实体类型的所有可能名称
> get(): EntityType -> 获取对应的 Bukkit EntityType

## 实现细节
- 使用 XRegistry 系统管理不同版本的实体类型映射
- 通过构造函数中的别名参数支持不同版本的实体类型名称
- 使用 @XChange 和 @XInfo 注解标记版本变更和实体信息
- 内部使用 Data 静态类初始化注册表，避免循环依赖

## 使用场景
> 需要在不同 Minecraft 版本间兼容实体类型时使用
> 当需要通过字符串名称获取实体类型时使用
> 在插件配置中使用实体类型名称时，可以通过此类进行解析和验证

## 注意事项
> 某些实体类型在特定版本中可能不存在，使用前应检查 isSupported() 方法
> 使用 @XChange 注解标记的实体类型表示在特定版本中发生了命名变更
> 使用 @XInfo 和 @Deprecated 标记的实体类型可能在未来版本中被移除

