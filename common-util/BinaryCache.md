# BinaryCache

## 基本信息
- 类名和包路径: taboolib.common.BinaryCache
- 基本用途: 提供二进制数据的缓存机制
- 类型: Kotlin单例对象
- 所属模块: common

## 类结构
### 公开静态字段
> primarySrcVersion: String -> 当前运行的JAR文件的摘要值

### 公开静态方法
> read<T>(name: String, version: String, block: (bytes: ByteArray) -> T): T? -> 从缓存中读取数据
> save(name: String, version: String, bytes: ByteArray): Unit -> 将字节数组保存到缓存
> save(name: String, version: String, block: () -> ByteArray): Unit -> 将函数返回的字节数组保存到缓存
> drop(name: String): Unit -> 删除指定名称的缓存
> getCacheFile(): File -> 获取缓存目录

### 类内可被访问字段
> 无

### 类方法
> 无

## 实现细节
- `primarySrcVersion`通过计算当前类所在JAR文件的摘要值来唯一标识版本
- 缓存文件存储在`cache/taboolib/{groupId}/binary/`目录下
- 每个缓存项由两个文件组成：数据文件(.cache)和版本文件(.cache.sha1)
- 在开发模式下会跳过缓存读取，确保始终使用最新数据
- 使用版本比对确保缓存数据与当前代码版本匹配

## 使用场景
> 缓存反射分析结果，避免重复解析类文件
> 缓存编译结果，提高启动速度
> 缓存序列化数据，减少序列化开销
> 缓存资源处理结果，避免重复处理

## 注意事项
> 在开发模式下缓存读取会被禁用
> 缓存版本不匹配时会重新生成缓存
> 缓存操作可能抛出异常，已内部处理并记录日志
> 缓存目录结构依赖于项目的groupId
