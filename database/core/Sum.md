# Sum

## 基本信息
- 类名和包路径: taboolib.module.database.Sum
- 基本用途: 表示SQL SUM聚合函数的操作类
- 类型: 类(Class)
- 所属模块: database

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> row: String -> 要求和的列名
> asRow: String -> 结果列的别名
> truncate: Int -> 截断小数位数，默认为-1(不截断)

## 实现细节
- 实现Attributes接口，提供query属性生成SUM SQL语句
- 支持TRUNCATE函数截断小数位数
- 使用asFormattedColumnName()确保列名格式正确
- 生成的SQL包含AS子句，为结果指定别名

## 使用场景
> 在SQL查询中计算列值的总和
> 在ActionSelect类中通过sum方法创建和使用
> 数据统计和报表生成

## 注意事项
> truncate属性用于控制小数位数，仅当值大于等于0时生效
> TRUNCATE函数会直接截断小数，不进行四舍五入
> 对非数值列使用SUM可能导致错误或意外结果
> 结果别名(asRow)在后续查询中可以引用
