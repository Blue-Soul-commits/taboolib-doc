# Vault
## 基本信息
- 类名和包路径: taboolib.platform.compat.Vault
- 基本用途: 提供与 Vault 插件集成的简化接口，用于经济和权限操作
- 类型: Kotlin 扩展函数和工具类文件
- 所属模块: bukkit-hook

## 类结构
### 公开静态字段
> isEconomySupported: Boolean -> 检查 Vault 经济系统是否可用
> isPermissionSupported: Boolean -> 检查 Vault 权限系统是否可用

### 公开静态方法
> 无

### 类内可被访问字段
> VaultService.economy: Economy? -> Vault 经济系统接口
> VaultService.permission: Permission? -> Vault 权限系统接口

### 类方法
> OfflinePlayer.getBalance(): Double -> 获取玩家余额
> OfflinePlayer.hasAccount(): Boolean -> 检查玩家是否有经济账户
> OfflinePlayer.createAccount(): Boolean -> 为玩家创建经济账户
> OfflinePlayer.depositBalance(amount: Double): EconomyResponse -> 向玩家账户存入金额
> OfflinePlayer.withdrawBalance(amount: Double): EconomyResponse -> 从玩家账户提取金额
> Player.checkPermission(permission: String): Boolean -> 检查玩家是否拥有指定权限
> Player.checkGroup(group: String): Boolean -> 检查玩家是否在指定权限组中
> Player.getGroups(): List<String> -> 获取玩家所在的所有权限组
> Player.getPrimaryGroup(): String -> 获取玩家的主权限组

## 实现细节
- 通过扩展函数简化 Vault API 的调用
- VaultService 对象在初始化时自动检测并获取 Vault 服务
- 提供 EconomyResponse 数据类封装经济操作的响应结果
- 使用非空断言操作符 (!!) 假设服务已可用，调用前应检查 isEconomySupported 和 isPermissionSupported

## 使用场景
> 需要操作服务器经济系统时（存款、取款、查询余额等）
> 需要检查或操作玩家权限和权限组时
> 需要与依赖 Vault 的其他插件集成时
> 简化插件开发中与 Vault 相关的代码

## 注意事项
> 使用经济相关函数前应先检查 isEconomySupported 是否为 true
> 使用权限相关函数前应先检查 isPermissionSupported 是否为 true
> 未检查服务可用性直接调用可能导致 NullPointerException
> 依赖服务器上已正确安装并配置 Vault 及其经济/权限提供者插件
