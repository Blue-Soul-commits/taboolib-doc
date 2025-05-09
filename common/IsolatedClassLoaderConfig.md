# IsolatedClassLoaderConfig
## 基本信息
- 类名和包路径: taboolib.common.classloader.IsolatedClassLoaderConfig
- 基本用途: IsolatedClassLoader 的配置接口
- 类型: 接口
- 所属模块: Common
---
## 类结构
### 公开静态字段
> (无静态字段)

### 公开静态方法
> (无静态方法)

### 类内可被访问字段
> (无字段)

### 类方法
> excludedClasses(): Set -> 获取需要排除的类名集合
> excludedPackages(): Set -> 获取需要排除的包名集合
---
## 实现细节
> 提供默认实现返回空集合
> 通过 Java SPI 机制加载配置实现
---
## 使用场景
> 自定义 IsolatedClassLoader 的排除规则
> 通过 ServiceLoader 配置类加载器行为
---
## 注意事项
> 实现类需要通过 META-INF/services 注册才能被发现
> 返回的集合不应为 null