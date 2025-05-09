# Version
## 基本信息
- 类名和包路径: taboolib.common.util.Version
- 基本用途: 解析、存储和比较版本号
- 类型: 工具类
- 所属模块: common-util

## 类结构
### 公开静态方法
> 无公开静态方法（除内部异常类）

### 类内可被访问字段
> source: String -> 原始版本字符串
> version: int[] -> 解析后的版本号数组

### 类方法
> Version(source: String) -> 构造函数，解析版本字符串
> isBefore(version: Version): boolean -> 判断当前版本是否小于指定版本
> isAfter(version: Version): boolean -> 判断当前版本是否大于指定版本
> getSource(): String -> 获取原始版本字符串
> isLegacy(): boolean -> 判断是否为旧版本格式（两段式）
> getVersion(): int[] -> 获取版本号数组
> equals(o: Object): boolean -> 判断两个版本是否相等
> hashCode(): int -> 获取哈希码
> toString(): String -> 获取字符串表示
> compareTo(o: Version): int -> 比较两个版本的大小

### 内部类
> VersionFormatException -> 版本格式异常，当版本格式不符合要求时抛出

## 实现细节
- 版本号解析支持两种格式：
  - 两段式（如 "1.0"）：存储为 [-1, 1, 0]
  - 三段式（如 "1.0.0"）：存储为 [1, 0, 0]
- 版本号可以包含破折号或空格后的额外信息（如 "1.0.0-SNAPSHOT"），但比较时只考虑数字部分
- 版本比较采用逐段比较的方式，先比较主版本号，再比较次版本号，最后比较修订版本号
- 当版本格式不符合要求时（既不是两段式也不是三段式），会抛出 VersionFormatException 异常

## 使用场景
> 软件版本管理和比较
> 依赖版本检查
> 兼容性判断
> 更新检测

## 注意事项
> 只支持两段式和三段式版本号，不支持更多段的版本号
> 两段式版本号被视为旧版本格式，主版本号固定为 -1
> 版本号中只能包含数字和点，额外信息需要用破折号或空格分隔
> 比较时只考虑数字部分，忽略额外信息
