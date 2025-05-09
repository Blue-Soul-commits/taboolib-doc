# Order

## 基本信息
- 类名和包路径: taboolib.module.database.Order
- 基本用途: 定义SQL查询结果的排序规则
- 类型: 类(Class)
- 所属模块: database

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> row: String -> 要排序的列名
> type: Type -> 排序类型(ASC或DESC)
> castType: String? -> 列类型转换，默认为null

### 类方法
> 无

### 内部类/枚举
> Type: 排序类型枚举
>   - ASC: 升序
>   - DESC: 降序

## 实现细节
- 实现Attributes接口，提供query属性生成排序SQL语句
- 支持通过castType对列进行类型转换后再排序
- 使用asFormattedColumnName()确保列名格式正确

## 使用场景
> 在SQL查询中指定结果集的排序方式
> 在ActionSelect类中用于添加ORDER BY子句
> 支持对列进行类型转换后排序，解决类型不匹配问题

## 注意事项
> castType用于解决字符串排序为数字等类型转换需求
> 使用DSL模式设置castType更加清晰
> 默认排序类型为ASC(升序)
