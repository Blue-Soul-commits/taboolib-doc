# RemapReflexSpigot

## 基本信息
- 类名和包路径: taboolib.module.nms.remap.RemapReflexSpigot
- 基本用途: 为Spigot/Bukkit服务器环境提供反射重映射功能
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
> field(name: String, field: String): String -> 将Spigot环境下的解混淆字段名映射为Mojang混淆字段名
> method(name: String, method: String, vararg parameter: Any?): String -> 将Spigot环境下的解混淆方法名映射为Mojang混淆方法名

## 实现细节
- 继承自RemapReflex抽象类，实现了field和method方法
- 字段映射过程：
  1. 仅在通用版本(isUniversal为true，即1.17+)中进行处理
  2. 首先检查缓存
  3. 在Spigot映射中查找字段的Mojang混淆名
  4. 保存映射结果到缓存
- 方法映射过程：
  1. 仅在major >= 10 (即1.18+)中进行处理
  2. 首先检查缓存
  3. 在Spigot映射中查找方法的Mojang混淆名，同时考虑方法参数类型
  4. 保存映射结果到缓存

## 使用场景
> 在Spigot/Bukkit服务器环境中处理NMS类的反射访问
> 当插件使用解混淆名称访问服务器内部类时，提供名称转换

## 注意事项
> 字段映射仅在Minecraft 1.17+版本中启用
> 方法映射仅在Minecraft 1.18+版本中启用
> 与RemapReflexPaper不同，此类只进行单向映射(Spigot解混淆名 -> Mojang混淆名)

