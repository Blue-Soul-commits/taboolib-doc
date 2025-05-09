# ConfigMigrator
## 基本信息
- 类名和包路径: taboolib.module.configuration.ConfigMigrator
- 基本用途: 提供配置映射的扁平化和差异比较功能
- 类型: 文件 (包含扩展函数和 Update 类)
- 所属模块: basic-configuration

## 类结构
### 公开静态字段
> 无

### 公开静态方法
> Map<String, Any?>.flatten(): Map<String, Any?> -> 将嵌套的映射扁平化为单层映射
> Map<String, Any?>.contrastAs(target: Map<String, Any?>): Set<Update> -> 计算两个映射之间的差异

### 类内可被访问字段
> 无

### 类方法
#### Update 类
> compareTo(other: Update): Int -> 比较两个 Update 对象，用于排序

## 实现细节
- 提供了 Map<String, Any?> 类型的扩展函数，用于配置映射的处理
- flatten() 函数将嵌套的映射结构扁平化，使用点号连接键名
- contrastAs() 函数计算源映射与目标映射之间的差异，返回 Update 对象集合
- Update 类表示配置差异，包含类型、节点路径和值信息
- Update.Type 枚举定义了三种差异类型：ADD（添加）、MODIFY（修改）和 DELETE（删除）
- Update 类实现了 Comparable 接口，按节点路径字典序排序

## 使用场景
> 配置文件迁移和更新
> 比较两个配置版本之间的差异
> 将嵌套的配置结构转换为扁平结构
> 在配置更新过程中保留用户自定义值

## 注意事项
> flatten() 函数使用点号连接键名，可能与原始配置中包含点号的键冲突
> contrastAs() 函数在比较值时使用 != 操作符，对于复杂对象可能需要自定义比较逻辑
> 返回的 Update 集合是按节点路径排序的 TreeSet
> 函数使用了 @Suppress("UNCHECKED_CAST") 注解，在处理复杂映射时需要注意类型安全

