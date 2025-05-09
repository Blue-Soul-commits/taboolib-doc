# Component

## 基本信息
- 类名和包路径: taboolib.expansion.ioc.annotation.Component
- 基本用途: 标记类为IOC容器管理的组件
- 类型: annotation class
- 所属模块: database-ioc

## 类结构

### 类内可被访问字段
> function: String -> 指定序列化工具选择器，默认为"Gson"
> index: String -> 指定数据索引ID，默认为"null"
> singleton: Boolean -> 是否为单例模式，默认为false

## 实现细节
- 使用@Retention(AnnotationRetention.RUNTIME)确保注解在运行时可用
- 提供三个可配置参数用于控制组件的行为

## 使用场景
> 标记数据类为IOC容器管理的组件
> 配置数据类的序列化方式
> 定义数据类的索引字段
> 设置数据类为单例模式

## 注意事项
> index参数应指定为数据类中的一个字段名，用于确保数据唯一性
> 推荐使用String类型作为数据ID
> 单例模式的ID将由IOC容器自动分配
