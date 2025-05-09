# CommandStructure

## 基本信息
- 类名和包路径: taboolib.common.platform.command.CommandStructure
- 基本用途: 定义命令结构，包含命令名称、别名、描述、用法、权限等信息
- 类型: 数据类
- 所属模块: TabooLib 平台命令模块

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> name: String -> 命令名称（小写形式）
> aliases: List<String> -> 命令别名列表
> description: String -> 命令描述
> usage: String -> 命令用法
> permission: String -> 命令所需权限
> permissionMessage: String -> 权限不足时显示的消息
> permissionDefault: PermissionDefault -> 默认权限设置
> permissionChildren: Map<String, PermissionDefault> -> 子权限映射表
> newParser: Boolean -> 是否使用新解析器

### 类方法
> 无额外类方法

## 实现细节
- 构造函数接收命令的所有属性，并将命令名称转换为小写形式存储
- 命令名称在构造时会被转换为小写，以确保命令名称的一致性
- 使用 PermissionDefault 枚举类型来定义权限默认值

## 使用场景
> 用于定义和注册 TabooLib 平台的命令结构
> 在命令系统中作为命令的元数据容器

## 注意事项
> 命令名称会被自动转换为小写，确保命令名称的一致性
> permissionChildren 用于定义子权限，可以为命令的子功能设置不同的权限
