# FolderReader

## 基本信息
- 类名和包路径: top.maplex.arim.tools.folderreader.FolderReader
- 基本用途: 读取文件夹中的配置文件并进行批量操作
- 类型: 数据类(data class)及工具函数
- 所属模块: 文件夹读取工具模块

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> readFolderWalkConfig(file: File, action: FolderReader.() -> Unit): Unit -> 读取指定文件夹下的配置文件并执行操作
> releaseResourceFolderAndRead(path: String, action: FolderReader.() -> Unit): Unit -> 释放插件资源文件夹并读取其中的配置文件

### 类内可被访问字段
> file: File -> 要读取的文件夹
> readTypes: MutableList<Type> -> 要读取的配置文件类型列表
> filter: MutableList<File.() -> Boolean> -> 文件筛选条件列表

### 类方法
> setReadType(vararg type: Type): Unit -> 设置要读取的配置文件类型
> addFilter(filter: File.() -> Boolean): Unit -> 添加文件筛选条件
> clearFilter(): Unit -> 清除所有文件筛选条件
> walk(action: Configuration.() -> Unit): Unit -> 遍历所有符合条件的配置文件并执行操作

## 实现细节
- 使用Kotlin data class设计，方便构建和操作
- 默认读取YAML类型的配置文件
- 支持自定义文件筛选条件，可以添加多个过滤器
- 使用TabooLib的Configuration系统处理配置文件
- 通过函数式编程接口提供灵活的操作方式
- 提供了两种主要使用方式：普通文件夹读取和插件资源文件夹释放并读取

## 使用场景
> 批量读取和处理插件配置文件目录下的所有配置文件
> 在插件初始化时释放并读取资源文件夹中的默认配置
> 当需要遍历处理多个类似结构的配置文件时，例如技能、物品、怪物等定义文件

## 注意事项
> 默认只读取YAML格式的配置文件，如需读取其他格式需调用setReadType方法
> 文件筛选条件是累加的，所有条件都必须满足才会处理该文件
> 使用walk方法时会遍历文件夹及其所有子文件夹