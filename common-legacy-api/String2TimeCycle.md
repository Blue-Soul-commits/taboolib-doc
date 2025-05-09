# String2TimeCycle
## 基本信息
- 类名和包路径: taboolib.common5.util.String2TimeCycle (Kotlin 扩展函数)
- 基本用途: 将字符串解析为 TimeCycle 对象，支持多种时间周期格式
- 类型: 扩展函数
- 所属模块: common5-legacy-api

## 类结构
### 公开静态方法
> String.parseTimeCycle(): TimeCycle -> 将字符串解析为 TimeCycle 对象

## 实现细节
- 通过空格分割输入字符串，获取时间周期类型和参数
- 支持四种时间周期类型：day、week、month 和毫秒值
- 对于 day 类型，解析小时和分钟参数
- 对于 week 和 month 类型，解析日期、小时和分钟参数
- 对于其他类型，将第一个参数解析为毫秒值
- 使用 Coerce.toInteger 进行类型转换，确保参数为整数
- 使用 getOrNull 安全获取可能不存在的参数，并提供默认值 0
- 最后调用 origin() 方法设置原始字符串

## 使用场景
> 解析配置文件中的时间周期设置
> 解析用户输入的时间周期命令
> 在需要定时任务或周期性事件的系统中使用

## 注意事项
> 输入字符串必须符合特定格式，否则可能导致解析错误
> day 格式：day [小时] [分钟]
> week 格式：week [星期几(0-6)] [小时] [分钟]
> month 格式：month [日期(1-31)] [小时] [分钟]
> 其他格式将尝试解析为毫秒值
