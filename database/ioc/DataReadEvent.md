# DataReadEvent

## 基本信息
- 类名和包路径: taboolib.expansion.ioc.event.DataReadEvent
- 基本用途: 在IOC容器读取数据类时触发的事件
- 类型: class
- 所属模块: database-ioc

## 类结构

### 类内可被访问字段
> data: Class<*> -> 正在被读取的数据类
> iocDatabase: IOCDatabase -> 用于读取数据的数据库实例

## 实现细节
- 继承自CancelableInternalEvent，支持取消操作
- 允许在事件处理过程中修改使用的数据库实例
- 通过callIf()方法可以同时调用事件并获取是否被取消的结果

## 使用场景
> 为特定数据类指定自定义数据库实现
> 在数据读取前拦截或修改读取行为
> 监控数据类的读取过程

## 注意事项
> 事件可以被取消，取消后数据类将不会被IOC容器管理
> 可以通过修改iocDatabase字段来更改数据存储方式
> 事件在IOCReader.readRegister方法中被触发

