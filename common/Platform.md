# Platform
## 基本信息
- 类名和包路径: taboolib.common.platform.Platform
- 基本用途: 定义和检测不同的运行平台
- 类型: 枚举
- 所属模块: Common
---
## 类结构
### 公开静态字段
> BUKKIT: Platform -> Bukkit 平台
> BUNGEE: Platform -> Bungee 平台
> VELOCITY: Platform -> Velocity 平台
> AFYBROKER: Platform -> AfyBroker 平台
> APPLICATION: Platform -> 应用程序平台
> CURRENT: Platform -> 当前运行平台

### 公开静态方法
> minecraft(): Platform[] -> 获取属于 Minecraft 的平台类型

### 类内可被访问字段
> key: String -> 平台标识符
> checkClass: String -> 用于检测平台的类

### 类方法
> key(): String -> 获取平台标识符
> checkClass(): String -> 获取检测类
---
## 实现细节
> 通过检查特定类是否存在来确定当前运行平台
> CURRENT 字段在类加载时自动初始化为当前平台
> APPLICATION 平台作为默认平台，当其他平台检测失败时使用
---
## 使用场景
> 检测当前运行环境
> 针对不同平台执行特定代码
> 配合 PlatformSide 注解使用
---
## 注意事项
> Minecraft 相关平台包括：BUKKIT、BUNGEE、VELOCITY、AFYBROKER
> 如果找不到对应的检测类，将默认为 APPLICATION 平台