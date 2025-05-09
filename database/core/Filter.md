# Filter
## 基本信息
- 类名和包路径: taboolib.module.database.Filter
- 基本用途: 提供SQL查询中的过滤条件管理
- 类型: 开放类
- 所属模块: database

## 类结构
### 类内可被访问字段
> criteria: ArrayList<Criteria> -> 存储过滤标准的集合

### 类方法
> query: String -> 获取组合后的SQL查询条件语句，使用AND连接所有条件
> elements: List<Any> -> 获取所有过滤条件中的参数值
> append(criteria: Criteria): Unit -> 追加一个过滤标准
> remove(vararg criteria: Criteria): Unit -> 移除指定的过滤标准
> isEmpty(): Boolean -> 判断过滤标准是否为空
> isNotEmpty(): Boolean -> 判断过滤标准是否不为空

## 实现细节
- 继承自`Filterable`类，实现了`Attributes`接口
- 通过`criteria`列表存储所有过滤条件
- `query`属性将所有条件用" AND "连接，形成完整的WHERE子句
- `elements`属性递归收集所有条件中的参数值，用于预处理语句
- 使用本地函数`Criteria.push()`递归处理嵌套条件

## 使用场景
> 构建数据库查询的WHERE子句
> 在ActionSelect、ActionUpdate、ActionDelete等操作中使用
> 支持复杂的条件组合，如AND、OR等逻辑操作

## 注意事项
> 过滤条件的组合默认使用AND逻辑
> 复杂条件组合需要使用Filterable中提供的and/or方法
