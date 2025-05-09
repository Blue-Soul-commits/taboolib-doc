# RemapHelper

## 基本信息
- 类名和包路径: taboolib.module.nms.remap.RemapHelper
- 基本用途: 提供方法描述符相关的辅助功能，用于检查方法参数和返回值类型的匹配
- 类型: 单例对象(object)
- 所属模块: bukkit-nms

## 类结构

### 私有静态字段
> descriptorTypeCacheMap: ConcurrentHashMap<String, Array<Class<*>>> -> 缓存方法描述符对应的参数类型
> autoboxing: Boolean -> 是否支持自动装箱/拆箱(Java 1.5+)

### 公开静态方法
> checkParameterType(check: String, to: String): Boolean -> 检查两个方法描述符的参数类型是否匹配
> checkReturnType(check: String, to: String): Boolean -> 检查两个方法描述符的返回值类型是否匹配
> checkParameterType(check: Array<Any?>, to: String): Boolean -> 检查参数实例与方法描述符的参数类型是否匹配
> getParameterTypes(descriptor: String): Array<Class<*>> -> 获取方法描述符中的参数类型

## 实现细节
- 使用ConcurrentHashMap缓存方法描述符对应的参数类型，避免重复解析
- 利用ClassHelper.isAssignable方法判断类型是否可分配，支持自动装箱/拆箱
- 使用ASM的Type类解析方法描述符，获取参数类型和返回值类型

## 使用场景
> 在RemapReflex子类中用于检查方法参数类型是否匹配
> 在RemapTranslation子类中用于比较方法描述符
> 在字节码转换过程中判断方法是否匹配

## 注意事项
> 使用缓存提高性能，避免重复解析方法描述符
> 支持自动装箱/拆箱，适应Java 1.5+环境
> 与Reflex的判断方式不同，此实现是反向判断(检查类可分配给目标类)

