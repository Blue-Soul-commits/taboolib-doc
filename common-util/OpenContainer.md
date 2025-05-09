# OpenContainer

## 基本信息
- 类名和包路径: taboolib.common.OpenContainer
- 基本用途: 定义一个插件容器接口，用于跨插件API调用
- 类型: 接口
- 所属模块: common

## 类结构
### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> 无

### 类方法
> isValid(): Boolean -> 检查容器是否有效，即OpenAPI是否可用
> getName(): String -> 获取插件名称
> call(name: String, args: Object[]): OpenResult -> 调用指定名称的API，传入参数数组，返回调用结果

## 实现细节
- 这是一个接口，需要由具体的插件容器实现
- 提供了三个核心方法用于插件间通信
- `call` 方法返回 `OpenResult` 对象，表示API调用的结果

## 使用场景
> 作为插件容器的抽象接口，用于实现跨插件的API调用
> 在TabooLib框架中用于管理和访问不同插件提供的功能
> 允许插件暴露自己的API给其他插件使用，而不需要直接依赖

## 注意事项
> 实现类需要确保 `isValid()` 方法正确反映容器状态
> `call` 方法应当处理异常情况，避免因API调用错误导致整个插件崩溃
> 返回的 `OpenResult` 应当包含足够的信息，让调用者了解API调用是否成功
