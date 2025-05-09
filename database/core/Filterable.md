# Filterable

## 基本信息
- 类名和包路径: taboolib.module.database.Filterable
- 基本用途: 提供SQL查询条件过滤功能的抽象基类
- 类型: 抽象类(Abstract Class)
- 所属模块: database

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> 无

### 类方法
> append(criteria: Criteria): Unit -> 追加一个过滤标准
> remove(vararg criteria: Criteria): Unit -> 移除过滤标准
> Criteria.or(other: Criteria): Criteria -> 创建OR条件
> Criteria.and(other: Criteria): Criteria -> 创建AND条件
> String.inside(value: Array<Any>): Criteria -> 创建IN条件
> String.between(value: Pair<Any, Any>): Criteria -> 创建BETWEEN条件
> String.eq(value: Any?): Criteria -> 创建等于条件
> String.lt(value: Any): Criteria -> 创建小于条件
> String.lte(value: Any): Criteria -> 创建小于等于条件
> String.gt(value: Any): Criteria -> 创建大于条件
> String.gte(value: Any): Criteria -> 创建大于等于条件
> String.like(value: Any): Criteria -> 创建模糊匹配条件
> not(func: Criteria): Criteria -> 创建否定条件
> or(func: Filter.() -> Unit): Criteria -> 创建OR组合条件
> and(func: Filter.() -> Unit): Criteria -> 创建AND组合条件
> pre(any: Any): PreValue -> 创建非占位符的固定文本值

## 实现细节
- 定义了内部数据类 `Criteria` 用于表示过滤条件
- 提供了丰富的中缀函数(infix function)用于构建SQL条件表达式
- 使用 `unwrap` 和 `unwrapArray` 方法处理参数值，支持占位符和非占位符值
- 支持条件的组合，如AND、OR、NOT等
- 提供了向下兼容的类型别名：WhereExecutor、WhereData、Where

## 使用场景
> 在数据库查询中构建WHERE条件
> 在ActionFilterable子类中用于过滤数据
> 在复杂查询中组合多个条件表达式

## 注意事项
> append和remove方法在基类中是空实现，子类需要根据需要重写
> 使用pre()方法可以创建非占位符的固定文本值，适用于表连接等场景
> 条件组合时注意优先级，可能需要使用括号明确分组