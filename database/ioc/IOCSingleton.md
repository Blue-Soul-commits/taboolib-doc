# IOCSingleton

## 基本信息
- 类名和包路径: taboolib.expansion.ioc.linker.IOCSingleton
- 基本用途: 提供单例模式的IOC容器连接器
- 类型: class
- 所属模块: database-ioc

## 类结构

### 类内可被访问字段
> dataType: Class<*> -> 单例对象的类型
> ioc: ConcurrentHashMap<String, Any> -> 存储数据的实际容器，通过unsafeLazy加载
> database: IOCDatabase -> 数据持久化接口，默认使用IOCDatabaseYaml

### 主要方法
> getId(): String -> 获取单例对象的唯一ID
> set(data: Any): Unit -> 设置单例对象
> get(): Any? -> 获取单例对象
> remove(): Unit -> 移除单例对象

## 实现细节
- 使用类名加"_Singleton"后缀作为单例对象的唯一ID
- 通过unsafeLazy延迟初始化，确保只在首次访问时创建
- 通过IOCReader.dataMap获取或创建数据存储
- 通过IOCReader.databaseMap获取或创建数据库接口
- linkedIOCSingleton函数提供了类型安全的创建方式

## 使用场景
> 需要全局单例对象的场景
> 需要持久化存储的单例对象
> 需要在多个地方访问同一个对象实例
> 适用于配置类、管理器类等全局唯一的对象

## 注意事项
> 推荐在目标类上使用@Component(singleton = true)注解
> 如果目标类没有singleton = true标记，会输出警告信息
> 单例对象在IOCReader.write()方法中自动保存
> 每个类型只能有一个单例实例
