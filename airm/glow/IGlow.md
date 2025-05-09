# IGlow

## 基本信息
- 类名和包路径: top.maplex.arim.tools.glow.api.IGlow
- 基本用途: 提供发光效果的API接口，允许为实体和方块添加发光效果
- 类型: 具体类
- 所属模块: 发光效果工具模块

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> INSTANCE: GlowManager -> 发光效果管理器实例

### 类方法
> setGlowing(entity: Entity, receiver: Player, color: NamedTextColor?): Unit -> 设置或取消实体的发光效果
> setGlowing(block: Block, receiver: Player, color: NamedTextColor?, mode: BlockGlowMode): Unit -> 设置或取消方块的发光效果

## 实现细节
- 使用GlowManager实例作为内部实现，封装了底层的发光效果处理逻辑
- 对外提供简洁的API接口，通过相同方法名的重载支持实体和方块的发光设置
- 通过传入null颜色值来取消发光效果
- 实体发光和方块发光采用不同的处理机制，但对外接口统一
- 使用Adventure API的NamedTextColor来表示发光颜色

## 使用场景
> 在游戏中高亮显示特定实体，例如标记敌人、NPC或重要物品
> 使方块发光以指示位置、路径或特殊区域
> 创建视觉效果，如任务指示器、互动对象提示等
> 实现玩家独立可见的发光效果，不影响其他玩家的视觉体验

## 注意事项
> 发光效果仅对指定的观察者(receiver)可见，是玩家独立的视觉效果
> 目前不支持空气方块发光，如代码注释所示
> 方块发光需要指定发光模式(BlockGlowMode)，实体发光则不需要
