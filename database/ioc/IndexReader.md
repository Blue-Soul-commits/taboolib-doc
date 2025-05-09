# IndexReader

## 基本信息
- 类名和包路径: taboolib.expansion.ioc.IndexReader
- 基本用途: 获取IOC容器中对象的唯一索引ID
- 类型: object (单例)
- 所属模块: database-ioc

## 类结构

### 公开静态方法
> getIndexId(instance: Any): String -> 获取对象的唯一索引ID

## 实现细节
- 使用反射获取对象的@Component注解信息
- 支持三种索引ID生成策略：
  1. 单例模式：使用类名+"_Singleton"作为ID
  2. 指定索引字段：使用对象指定字段的值作为ID
  3. 随机UUID：当无法获取索引时使用随机UUID作为备选

## 使用场景
> 为IOC容器中的对象生成唯一标识
> 在IOCReader和各种Linker中用于对象的存储和检索
> 确保数据对象在持久化存储中的唯一性

## 注意事项
> 如果对象没有@Component注解，将返回随机UUID
> 当指定的索引字段不存在或为null时，将返回随机UUID
> 单例模式的对象始终使用类名+"_Singleton"作为ID，忽略index属性

