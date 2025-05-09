# PlayerSelectLocaleEvent
## 基本信息
- 类名和包路径: taboolib.module.lang.event.PlayerSelectLocaleEvent
- 基本用途: 表示玩家选择或更改语言区域设置的事件
- 类型: 类
- 所属模块: minecraft-i18n

## 类结构
### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> player: ProxyPlayer -> 选择语言区域的玩家
> locale: String -> 玩家选择的语言区域代码，可修改

### 类方法
> 无额外方法（仅继承自InternalEvent的方法）

## 实现细节
- PlayerSelectLocaleEvent继承自InternalEvent，是TabooLib内部事件系统的一部分
- 事件包含两个主要属性：player（玩家对象）和locale（语言区域代码）
- locale属性是可变的（var），允许事件处理器修改玩家的语言选择
- 作为InternalEvent的子类，可以通过TabooLib的事件系统进行监听和处理
- 事件在玩家选择或更改语言区域设置时触发

## 使用场景
> 监听玩家语言选择变化，实现多语言支持
> 根据玩家语言偏好自动调整游戏内容的显示语言
> 强制设置特定玩家的语言，覆盖其默认选择
> 收集服务器玩家的语言偏好统计
> 与TabooLib的国际化(i18n)模块配合，提供完整的多语言支持

## 注意事项
> 修改locale属性会影响玩家实际使用的语言设置
> 语言代码通常遵循ISO标准，如"zh_CN"、"en_US"等
> 作为InternalEvent，需要使用TabooLib的事件系统进行监听，而非Bukkit事件系统
> 事件可能在玩家首次加入服务器或通过命令/UI更改语言设置时触发
> 处理此事件时应考虑服务器是否支持玩家选择的语言

