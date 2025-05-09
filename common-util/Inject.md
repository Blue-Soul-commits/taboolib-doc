# Inject

## 基本信息
- 类名和包路径: taboolib.common.Inject
- 基本用途: 标记 TabooLib 自己的类，使其能被 ClassVisitor 扫描到
- 类型: 注解（Annotation）
- 所属模块: common

## 类结构
### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> 无

### 类方法
> 无

## 实现细节
- 这是一个运行时（RUNTIME）注解，可以通过反射在运行时获取
- 只能应用于类型（TYPE）元素，即类、接口、枚举等
- 没有任何属性或方法，仅作为标记使用

## 使用场景
> 在 TabooLib 框架内部类上添加此注解，使其能被 ClassVisitor 扫描并处理
> 用于控制哪些类会被 TabooLib 的类访问器处理，避免扫描所有类

## 注意事项
> 只有标记了 @Inject 的 TabooLib 内部类才会被 ClassVisitor 扫描到
> 此注解仅用于 TabooLib 内部类，不应在用户代码中使用
