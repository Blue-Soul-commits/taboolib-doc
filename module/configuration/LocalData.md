# LocalData
## 基本信息
- 类名和包路径: taboolib.module.configuration.LocalData
- 基本用途: 提供临时数据文件的创建和自动保存功能
- 类型: 对象 (Object) 和顶层函数
- 所属模块: basic-configuration

## 类结构
### 公开静态字段
> 无

### 公开静态方法
> createTempData(path: String, saveTime: Long = 1200, type: Type? = null): Configuration -> 创建一个临时的本地数据文件
> createLocal(path: String, saveTime: Long = 1200, type: Type? = null): Configuration -> 创建一个临时的本地数据文件（已废弃）

### 类内可被访问字段
> init: Boolean -> 是否为初始状态（私有变量）
> fileMap: ConcurrentHashMap<String, Configuration> -> 存储临时数据文件的映射（私有变量）

### 类方法
> saveAll() -> 保存所有临时数据文件

## 实现细节
- 使用 ConcurrentHashMap 存储临时数据文件，确保线程安全
- 在首次创建临时数据文件时，启动一个异步定时任务，定期保存所有数据
- 在插件禁用时（DISABLE 生命周期），自动保存所有临时数据文件
- 支持指定数据文件的类型，如果未指定则根据文件扩展名自动识别
- 如果请求的临时数据文件已存在，则返回缓存的实例，避免重复加载

## 使用场景
> 存储插件运行时的临时数据
> 需要定期自动保存的数据文件
> 多个组件共享访问同一个数据文件
> 在插件禁用时确保数据被保存

## 注意事项
> 默认的自动保存时间为 1200 ticks（约 60 秒）
> 临时数据文件存储在插件的数据文件夹中
> createLocal 函数已被废弃，应使用 createTempData 代替
> 所有临时数据文件会在插件禁用时自动保存
