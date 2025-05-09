# ConvertResult
## 基本信息
- 类名和包路径: taboolib.module.configuration.ConvertResult
- 基本用途: 表示配置值转换操作的结果，包括成功、失败和跳过三种状态
- 类型: 密封类 (Sealed Class)
- 所属模块: basic-configuration

## 类结构
### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> isSuccessful: Boolean -> 表示转换操作是否成功

### 类方法
> 无

## 实现细节
- 这是一个密封类 (Sealed Class)，限制了子类的类型和数量
- 包含三个子类/对象，分别表示不同的转换结果状态：
  - Success: 表示转换成功，包含转换后的值
  - Failure: 表示转换失败，可以包含异常信息
  - Skip: 表示跳过转换，是一个单例对象

## 使用场景
> 在配置值转换过程中表示转换结果
> 在类型转换器中返回转换状态
> 处理配置值转换的错误和异常情况
> 实现转换链，允许多个转换器尝试转换同一个值

## 注意事项
> Success 是唯一 isSuccessful 为 true 的子类
> Failure 和 Skip 都表示转换未成功，但原因不同
> Failure 可以包含异常信息，用于调试和错误处理
> Skip 通常表示当前转换器不适用于该值，应尝试下一个转换器
