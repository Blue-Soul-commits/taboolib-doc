# PlayerFakeOpNMSImpl
## 基本信息
- 类名和包路径: taboolib.expansion.PlayerFakeOpNMSImpl
- 基本用途: 实现 PlayerFakeOpNMS 抽象类，提供创建玩家假OP权限代理对象的具体实现
- 类型: 实现类
- 所属模块: bukkit-fake-op

## 类结构
### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> playerFakeOpUtil: PlayerFakeOpUtil -> 工具类实例，用于创建代理对象

### 类方法
> playerFakeOp(player: Player): Player -> 实现抽象方法，创建玩家的假OP代理对象

## 实现细节
- 继承 PlayerFakeOpNMS 抽象类，实现其 playerFakeOp 方法
- 使用 ByteBuddy 库动态生成 CraftPlayer 的子类，重写权限相关方法
- 内部类 PlayerFakeOpUtil 负责具体的代理对象创建逻辑
- 代理对象保留原始 CraftPlayer 对象的引用，并将大部分方法调用转发给原始对象
- 重写 isOp()、hasPermission(String) 和 hasPermission(Permission) 方法，使其始终返回 true

## 使用场景
> 在 Bukkit/Spigot 服务器环境中临时赋予玩家 OP 权限
> 在需要执行特权操作但不想真正设置玩家为 OP 的情况下使用
> 在插件开发中测试需要 OP 权限的功能

## 注意事项
> 使用了 ByteBuddy 库进行运行时类生成，确保正确加载依赖
> 代理对象仅在内存中有效，不会修改玩家在服务器中的实际权限状态
> 使用了反射和类加载技术，在某些安全管理器环境下可能受限

