# XParticle

## 基本信息
- 类名和包路径: taboolib.library.xseries.XParticle
- 基本用途: 提供跨版本的 Minecraft 粒子效果支持，特别是处理 Spigot 1.20.5 版本中的"奇偶校验更改"
- 类型: 枚举类
- 所属模块: TabooLib XSeries 库

## 类结构

### 公开静态字段
> REGISTRY: XRegistry<XParticle, Particle> -> 粒子效果的注册表，用于管理 XParticle 和 Bukkit Particle 之间的映射

### 公开静态方法
> of(particle: Particle): XParticle -> 根据 Bukkit 粒子效果获取对应的 XParticle
> of(particle: String): Optional<XParticle> -> 根据粒子效果名称获取对应的 XParticle

### 类内可被访问字段
> particle: Particle -> 存储对应的 Bukkit 粒子效果实例

### 类方法
> getNames(): String[] -> 返回粒子效果的名称数组
> get(): Particle -> 获取对应的 Bukkit 粒子效果
> friendlyName(): String -> 返回友好可读的粒子效果名称
> isSupported(): boolean -> 检查当前服务器版本是否支持该粒子效果
> or(other: XParticle): XParticle -> 如果当前粒子效果不受支持，则返回替代粒子效果

## 实现细节
- 使用 XRegistry 系统管理粒子效果的跨版本兼容性
- 通过注解（@XChange, @XMerge, @XInfo）标记版本变更和兼容性信息
- 内部使用 Data 静态类初始化注册表，避免循环依赖
- 支持通过名称或 Bukkit 粒子类型查找对应的 XParticle

## 使用场景
> 在不同 Minecraft 版本间创建一致的粒子效果
> 处理 Minecraft 1.20.5 版本中的粒子效果名称变更
> 在插件中使用粒子效果时提供向后兼容性

## 注意事项
> 某些粒子效果在特定版本中可能不可用，使用前应检查 isSupported() 方法
> 部分粒子效果（如 FOOTSTEP, ITEM_TAKE）已在 1.13 版本中移除，但为了兼容性仍保留在枚举中
> 使用 of() 方法获取 XParticle 实例，而不是直接使用枚举值，以确保跨版本兼容性

