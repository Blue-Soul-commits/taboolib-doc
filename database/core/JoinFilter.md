# JoinFilter

## 基本信息
- 类名和包路径: taboolib.module.database.JoinFilter
- 基本用途: 表示JOIN操作中ON条件的过滤器
- 类型: 类(Class)
- 所属模块: database

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> 继承自Filter类的所有字段

### 类方法
> on(criteria: Criteria): Unit -> 添加连接条件

### 继承方法(来自Filter)
> append(criteria: Criteria): Unit -> 追加过滤条件
> remove(vararg criteria: Criteria): Unit -> 移除过滤条件
> isEmpty(): Boolean -> 判断过滤条件是否为空
> isNotEmpty(): Boolean -> 判断过滤条件是否不为空

## 实现细节
- 继承自Filter类，专用于JOIN操作的ON条件
- 提供on方法作为append方法的语义化别名
- 复用Filter类的条件构建和管理功能

## 使用场景
> 在JOIN操作中定义表连接条件
> 在ActionSelect类的innerJoin/leftJoin/rightJoin方法中使用
> 处理表间关系的条件定义

## 注意事项
> on方法实际上是对append方法的封装，提供更符合SQL语义的API
> 可以添加多个on条件，它们之间是AND关系
> 支持Filter类的所有条件表达式和操作符
> 通常使用pre()函数引用被连接表的列
