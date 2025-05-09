# VisitorGroup

## 基本信息
- 类名和包路径: taboolib.common.inject.VisitorGroup
- 基本用途: 管理具有相同优先级的类访问器(ClassVisitor)集合
- 类型: 实体类(Entity Class)
- 所属模块: TabooLib 注入模块

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> priority: byte -> 访问器组的优先级
> list: List<ClassVisitor> -> 存储访问器的线程安全列表

### 类方法
> VisitorGroup(priority: byte): Constructor -> 创建指定优先级的访问器组
> getAll(): List<ClassVisitor> -> 获取所有依赖注入接口
> get(lifeCycle: LifeCycle): List<ClassVisitor> -> 通过生命周期获取所有依赖注入接口
> getPriority(): byte -> 获取优先级
> toString(): String -> 返回访问器组的字符串表示

## 实现细节
- 使用 CopyOnWriteArrayList 存储访问器，确保线程安全
- 优先级通过构造函数设置，并且不可变
- 提供按生命周期过滤访问器的功能
- 当 lifeCycle 为 null 时，返回所有访问器

## 使用场景
> 在 ClassVisitorHandler 中按优先级组织访问器
> 在依赖注入过程中按生命周期筛选访问器
> 管理具有相同优先级的多个访问器

## 注意事项
> 访问器列表是线程安全的，可以在多线程环境中安全使用
> 按生命周期获取访问器时会创建新的列表，不会修改原始列表
> 优先级一旦设置不可更改
> 通过 getAll() 获取的列表可以直接添加新的访问器
