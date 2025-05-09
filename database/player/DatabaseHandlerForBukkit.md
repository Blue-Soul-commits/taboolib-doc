# DatabaseHandlerForBukkit

## 基本信息
- 类名和包路径: taboolib.expansion.DatabaseHandlerForBukkit (文件名)
- 基本用途: 为Bukkit平台的Player对象提供数据容器操作的扩展函数
- 类型: 工具类文件（包含扩展函数）
- 所属模块: database-player

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> 无

### 扩展函数
> Player.getDataContainer(): DataContainer -> 获取玩家的数据容器
> Player.setupDataContainer(usernameMode: Boolean): Unit -> 为玩家设置数据容器
> Player.releaseDataContainer(): Unit -> 释放玩家的数据容器
> Player.getAutoDataContainer(): AutoDataContainer -> 获取玩家的自动数据容器
> Player.releaseAutoDataContainer(): Unit -> 释放玩家的自动数据容器

## 实现细节
- 所有方法都是对Bukkit平台Player对象的扩展
- 内部通过adaptPlayer函数将Bukkit的Player转换为通用的ProxyPlayer
- 然后调用DatabaseHandler中定义的相应方法
- 对于自动数据容器相关方法，直接使用玩家的UUID调用相应的扩展函数

## 使用场景
> 在Bukkit/Spigot插件中需要操作玩家数据
> 需要在Bukkit环境中使用TabooLib的数据容器功能
> 作为DatabaseHandler的Bukkit平台适配层

## 注意事项
> 使用前必须确保已经通过DatabaseHandler设置了数据库
> 这些扩展函数只是对DatabaseHandler中函数的封装，实际实现在DatabaseHandler中
> 在多线程环境下使用时需要注意线程安全问题
