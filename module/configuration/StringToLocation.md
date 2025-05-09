# SectionToLocation
## 基本信息
- 类名和包路径: taboolib.module.configuration.util.SectionToLocation
- 基本用途: 提供配置节点与位置信息(Location)之间的转换功能
- 类型: 文件 (包含扩展函数)
- 所属模块: basic-configuration

## 类结构
### 公开静态字段
> 无

### 公开静态方法
> ConfigurationSection.setLocation(path: String, location: Location) -> 将位置信息保存到配置节点
> ConfigurationSection.getLocation(path: String): Location? -> 从配置节点读取位置信息

### 类内可被访问字段
> 无

### 类方法
> 无

## 实现细节
- 提供了 ConfigurationSection 的两个扩展函数，用于位置信息的存取
- setLocation 函数将 Location 对象转换为包含世界名称和坐标信息的映射，并保存到配置节点
- getLocation 函数从配置节点读取世界名称和坐标信息，并构造 Location 对象
- 位置信息包含完整的六个参数：世界名称(world)、X坐标(x)、Y坐标(y)、Z坐标(z)、偏航角(yaw)和俯仰角(pitch)
- 使用 let 和安全调用操作符确保在配置节点不存在时返回 null

## 使用场景
> 在配置文件中保存和读取游戏中的位置信息
> 存储传送点、出生点等位置数据
> 记录建筑物、区域或其他游戏对象的位置
> 在插件之间共享位置数据

## 注意事项
> getLocation 在配置节点不存在时返回 null
> 使用的 Location 类来自 taboolib.common.util 包，不是 Bukkit 的 Location 类
> 偏航角(yaw)和俯仰角(pitch)在存储时是 Double 类型，读取时会转换为 Float 类型
> 世界名称可能为 null，取决于 Location 对象的构造

