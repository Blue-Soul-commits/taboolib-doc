# PermissionDefault

## 基本信息
- 类名和包路径: taboolib.common.platform.command.PermissionDefault
- 基本用途: 定义权限的默认状态枚举
- 类型: 枚举类
- 所属模块: TabooLib 平台命令模块

## 类结构

### 公开静态字段
> TRUE: PermissionDefault -> 默认允许所有人使用
> FALSE: PermissionDefault -> 默认禁止所有人使用
> OP: PermissionDefault -> 默认仅允许管理员使用
> NOT_OP: PermissionDefault -> 默认仅允许非管理员使用

### 公开静态方法
> values(): Array<PermissionDefault> -> 返回包含所有枚举值的数组（由编译器自动生成）
> valueOf(name: String): PermissionDefault -> 返回指定名称的枚举常量（由编译器自动生成）

### 类内可被访问字段
> 无额外字段

### 类方法
> 无额外方法

## 实现细节
- 简单的枚举类，定义了四种权限默认状态
- 由 Kotlin 编译器自动生成标准枚举方法如 values() 和 valueOf()

## 使用场景
> 在命令或权限系统中定义默认的权限状态
> 用于 CommandStructure 中设置命令的默认权限
> 用于权限节点的定义和管理

## 注意事项
> TRUE 和 FALSE 是绝对的允许和禁止，不受玩家身份影响
> OP 和 NOT_OP 是基于玩家身份（是否为管理员）的条件性权限