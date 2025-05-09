# Annotations 
## 基本信息 
- 类名和包路径: taboolib.expansion.Annotations
- 基本用途: 提供数据库持久化对象映射的注解，用于标记实体类的字段属性
- 类型: 注解类
- 所属模块: module/database/database-ptc-object

## 类结构 

### 注解类列表

> @Id: 无参数 -> 标记字段为主键，只能有一个主键字段
> @Key: 无参数 -> 标记字段为索引键，用于建立数据库索引
> @UniqueKey: 无参数 -> 标记字段为唯一索引键
> @NotNull: 无参数 -> 标记字段不允许为空
> @Length(value: Int = 64): 注解 -> 设置字段长度，默认值为64
> @Alias(value: String): 注解 -> 设置字段的别名，用于数据库列名映射

## 实现细节
- 所有注解均设置为运行时保留（@Retention(AnnotationRetention.RUNTIME)）
- 这些注解被用于 AnalyzedClassMember 类解析实体类成员属性
- @Id 注解标记的字段会被识别为主键（isPrimary 属性）
- @Alias 注解允许开发者为字段指定自定义的数据库列名
- 没有使用 @Alias 注解的字段名会通过 toColumnName() 方法转换为下划线格式（如 userName 转为 user_name）

## 使用场景 
> 定义数据库实体类时对字段进行标记
> 通过 TabooLib 的持久化框架将 Kotlin 数据类映射到数据库表
> 自定义数据库列名和属性

## 注意事项 
> @Id 注解只能用于一个字段，如果在同一个类中多次使用会抛出异常
> 如果不使用 @Alias 注解，字段名将按照驼峰转下划线的规则映射到数据库列
> @Length 注解主要用于字符串类型字段的长度定义

