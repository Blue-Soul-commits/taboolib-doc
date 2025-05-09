# RemapReflexPaper

## 基本信息
- 类名和包路径: taboolib.module.nms.remap.RemapReflexPaper
- 基本用途: 为Paper 1.20.6+服务器环境提供反射重映射功能
- 类型: 具体实现类
- 所属模块: bukkit-nms

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> 继承自RemapReflex的所有字段

### 类方法
> field(name: String, field: String): String -> 将Spigot环境下的字段名映射为Paper环境下的字段名
> method(name: String, method: String, vararg parameter: Any?): String -> 将Spigot环境下的方法名映射为Paper环境下的方法名
> matchName(name: String): Pair<String?, String?> -> 尝试匹配类名，返回Spigot名称和Mojang名称的对
> translate(key: String): String -> 将Spigot类名转换为Mojang类名

## 实现细节
- 继承自RemapReflex抽象类，实现了field和method方法
- 字段映射过程：
  1. 首先检查缓存
  2. 使用matchName获取Spigot和Mojang的类名
  3. 在Spigot映射中查找原始字段的Mojang混淆名(obf)
  4. 在Paper映射中查找对应的Mojang解混淆名(deobf)
  5. 保存映射结果到缓存
- 方法映射过程类似，但需要额外考虑方法参数类型
- matchName方法通过双向查找确定类名来源，解决无法确认名称来自哪种对照表的问题

## 使用场景
> 在Paper 1.20.6+服务器环境中处理NMS类的反射访问
> 当插件使用Spigot风格的API访问Paper服务器时，提供名称转换

## 注意事项
> 仅在Paper 1.20.6+环境中启用
> 处理了Paper服务器使用Mojang映射而插件可能使用Spigot映射的情况
> 通过matchName方法解决了无法确认名称来源的问题

