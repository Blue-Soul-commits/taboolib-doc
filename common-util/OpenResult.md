# OpenResult

## 基本信息
- 类名和包路径: taboolib.common.OpenResult
- 基本用途: 表示OpenAPI调用的结果，包含成功/失败状态和返回值
- 类型: 数据类
- 所属模块: common

## 类结构
### 公开静态字段
> 无

### 公开静态方法
> successful(): OpenResult -> 创建一个成功的结果，没有返回值
> successful(value: Object): OpenResult -> 创建一个成功的结果，包含指定返回值
> failed(): OpenResult -> 创建一个失败的结果，没有返回值
> cast(source: Object): OpenResult -> 从其他插件的OpenResult对象转换为当前插件的OpenResult对象

### 类内可被访问字段
> successful: boolean -> 表示操作是否成功
> value: Object -> 操作的返回值

### 类方法
> OpenResult(successful: boolean, value: Object) -> 构造函数，创建一个结果对象
> isSuccessful(): boolean -> 检查操作是否成功
> isFailed(): boolean -> 检查操作是否失败
> getValue(): Object -> 获取操作的返回值

## 实现细节
- 使用不可变字段存储操作结果状态和返回值
- 提供静态工厂方法简化对象创建
- 使用Reflex库实现跨插件对象转换功能

## 使用场景
> 作为OpenAPI调用的返回值，表示API调用的结果
> 在插件间传递API调用结果
> 在OpenListener实现中返回处理结果

## 注意事项
> 对象一旦创建，状态和返回值不可更改
> 返回值可以为null，调用者需要处理空值情况
> cast方法依赖于Reflex库，用于处理跨插件通信时的对象转换
