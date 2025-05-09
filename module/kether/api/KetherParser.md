# KetherParser

## 基本信息
- 类名和包路径: taboolib.module.kether.KetherParser
- 基本用途: 用于标记Kether脚本动作解析器的注解，定义动作名称、命名空间和共享属性
- 类型: 注解类
- 所属模块: kether

## 类结构
### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> value: Array<String> -> 定义动作解析器支持的名称数组
> release: Array<String> -> 定义需要释放的动作名称数组，默认为空数组
> namespace: String -> 定义动作所属的命名空间，默认为"kether"
> shared: Boolean -> 定义该解析器是否为共享解析器，默认为false

### 类方法
> 无

## 实现细节
- KetherParser是一个注解类，使用@Target指定可以应用于类和函数
- 使用@Retention(AnnotationRetention.RUNTIME)指定注解在运行时可用
- 该注解主要用于标记Kether脚本的动作解析器，指定其支持的动作名称和属性
- 通过value参数定义解析器可以处理的动作名称列表
- namespace参数用于将动作分组到不同的命名空间中

## 使用场景
> 标记类或函数作为Kether脚本的动作解析器
> 定义动作解析器支持的动作名称和别名
> 指定动作所属的命名空间，用于组织和区分不同来源的动作
> 通过shared属性指定解析器是否可以被其他模块共享使用

## 注意事项
> 通常应用于实现ActionParser接口的类或返回ActionParser的工厂方法
> 动作名称应该是唯一的，以避免在同一命名空间中发生冲突
> 共享解析器(shared=true)可能被其他模块使用，应确保其稳定性和向后兼容性
> 命名空间用于避免不同模块间的动作名称冲突，默认为"kether"