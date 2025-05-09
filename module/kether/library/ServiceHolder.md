# ServiceHolder

## 基本信息
- 类名和包路径: taboolib.library.kether.ServiceHolder
- 基本用途: 提供全局访问点，管理 Kether 脚本引擎的服务实例
- 类型: 工具类
- 所属模块: minecraft-kether

## 类结构
### 私有静态字段
> questServiceInstance: QuestService<?> -> 存储全局唯一的 QuestService 实例

### 公开静态方法
> setQuestServiceInstance(QuestService<?> service): void -> 设置全局 QuestService 实例
> getQuestServiceInstance(): QuestService<?> -> 获取全局 QuestService 实例

## 实现细节
- 使用静态字段存储全局唯一的 QuestService 实例，实现单例模式
- 在 Kether 脚本引擎初始化时，通过 setQuestServiceInstance 方法注册服务实例
- QuestService.instance() 静态方法内部通过 ServiceHolder 获取全局服务实例

## 使用场景
> 作为脚本服务的全局访问点
> 在插件初始化时注册 QuestService 实现类
> 在不同模块间共享同一个 QuestService 实例

## 注意事项
> 服务实例通常在应用启动时设置，之后不应再次修改
> 如果未设置服务实例，调用 getQuestServiceInstance 会返回 null
> 主要实现类是 ScriptService，它在初始化时会注册自身到 ServiceHolder
