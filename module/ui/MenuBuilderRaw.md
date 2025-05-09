# MenuSourceExtensions

## 基本信息
- 类名和包路径: taboolib.module.ui.MenuSourceExtensions
- 基本用途: 提供TabooLib菜单系统与Source消息系统的集成扩展函数
- 类型: Kotlin扩展函数文件
- 所属模块: bukkit-ui

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法（以Kotlin扩展函数形式提供）

### 类内可被访问字段
> 无类内可被访问字段

### 类方法
> buildMenu<T : Menu>(title: Source, builder: T.() -> Unit): Inventory -> 使用Source作为标题构建菜单的扩展函数
> HumanEntity.openMenu<T : Menu>(title: Source, builder: T.() -> Unit): Unit -> 为HumanEntity提供的扩展函数，使用Source作为标题打开菜单

## 实现细节
- MenuSourceExtensions.kt文件包含Kotlin扩展函数，为TabooLib菜单系统提供与Source消息系统的集成
- 两个扩展函数都是内联函数（inline），可以减少Lambda表达式的开销
- 函数内部调用了相应的非Source版本函数，将Source通过toRawMessage()转换为原始字符串
- 使用泛型参数T并限制为Menu类型的子类，支持不同类型的菜单构建

## 使用场景
> 在需要使用TabooLib消息系统（Source）作为菜单标题时使用
> 在国际化菜单中，使用Source对象获取当前语言环境下的菜单标题
> 在需要复杂文本处理（如颜色、格式化）的菜单标题中使用

## 注意事项
> 这些扩展函数依赖taboolib.module.chat.Source类，确保相关依赖可用
> 函数内部使用toRawMessage()方法将Source转换为原始字符串，确保Source实例能正确转换
> 这些函数是对现有buildMenu和openMenu函数的扩展，提供了更便捷的Source集成
> 内联函数可能会增加编译后代码的大小，但减少了运行时开销