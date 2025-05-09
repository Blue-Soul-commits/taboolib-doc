# PlayerFakeOpNMS
## 基本信息
- 类名和包路径: taboolib.expansion.PlayerFakeOpNMS
- 基本用途: 提供创建玩家假OP权限代理对象的功能
- 类型: 抽象类
- 所属模块: bukkit-fake-op

## 类结构
### 公开静态字段
> INSTANCE: PlayerFakeOpNMS -> 单例实例，通过 nmsProxy 懒加载获取

### 公开静态方法
> 无

### 类内可被访问字段
> 无

### 类方法
> playerFakeOp(player: Player): Player -> 获取指定玩家的假OP代理对象

## 实现细节
- 使用 @Inject 注解标记为自动注入类
- 使用 @RuntimeDependency 注解声明运行时依赖 ByteBuddy 库
- 通过 nmsProxy 获取适配当前 Minecraft 版本的实现类实例
- 使用 ByteBuddy 库创建代理对象，修改权限相关方法的返回值

## 使用场景
> 需要临时赋予玩家 OP 权限但不想真正设置为 OP 的情况
> 在执行某些需要 OP 权限的命令或操作时使用
> 在插件开发中测试需要 OP 权限的功能

## 注意事项
> 返回的代理对象仅修改了 isOp()、hasPermission(String) 和 hasPermission(Permission) 三个方法
> 代理对象不会真正修改玩家在服务器中的权限状态
> 代理对象仅在当前上下文中有效，不会持久化
> 依赖 ByteBuddy 库实现，确保正确加载依赖
