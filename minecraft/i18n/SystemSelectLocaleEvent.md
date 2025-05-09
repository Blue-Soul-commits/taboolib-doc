# SystemSelectLocaleEvent
## 基本信息
- 类名和包路径: taboolib.module.lang.event.SystemSelectLocaleEvent
- 基本用途: 表示系统级别的语言区域设置变更事件
- 类型: 类
- 所属模块: minecraft-i18n

## 类结构
### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> locale: String -> 系统选择的语言区域代码，可修改

### 类方法
> 无额外方法（仅继承自InternalEvent的方法）

## 实现细节
- SystemSelectLocaleEvent继承自InternalEvent，是TabooLib内部事件系统的一部分
- 事件包含一个主要属性：locale（语言区域代码），该属性是可变的（var）
- 作为InternalEvent的子类，可以通过TabooLib的事件系统进行监听和处理
- 与PlayerSelectLocaleEvent不同，此事件针对的是系统级别的语言设置，而非特定玩家
- 事件在系统语言设置发生变化时触发，可能是由配置更改、服务器启动或管理命令引起

## 使用场景
> 监听系统默认语言的变更，调整全局消息的显示语言
> 在服务器启动时设置默认语言环境
> 根据系统语言自动加载对应的语言资源文件
> 实现管理员通过命令更改服务器全局语言的功能
> 与TabooLib的国际化(i18n)模块配合，提供完整的多语言支持系统

## 注意事项
> 修改locale属性会影响系统默认使用的语言设置，可能影响所有未指定个人语言偏好的用户
> 语言代码通常遵循ISO标准，如"zh_CN"、"en_US"等
> 作为InternalEvent，需要使用TabooLib的事件系统进行监听，而非Bukkit事件系统
> 处理此事件时应考虑是否需要重新加载或更新已加载的语言资源
> 系统语言变更可能需要通知在线玩家，特别是那些使用系统默认语言的玩家

