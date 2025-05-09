# RemapTranslationTabooLib

## 基本信息
- 类名和包路径: taboolib.module.nms.remap.RemapTranslationTabooLib
- 基本用途: 专门用于在Paper 1.20.6+环境下转译TabooLib类的字节码重映射器
- 类型: 具体实现类
- 所属模块: bukkit-nms

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> descriptorCache: HashMap<String, String> -> 描述符缓存

### 类方法
> mapFieldName(owner: String, name: String, descriptor: String): String -> 重写Remapper的mapFieldName方法，将Spigot解混淆字段名转换为Mojang解混淆字段名
> mapMethodName(owner: String, name: String, descriptor: String): String -> 重写Remapper的mapMethodName方法，将Spigot解混淆方法名转换为Mojang解混淆方法名
> translate(key: String): String -> 重写RemapTranslation的translate方法，处理包名转换

## 实现细节
- 继承自RemapTranslation类，专门用于TabooLib类的转译
- 字段映射过程：
  1. 将内部名称转换为点分隔的类名
  2. 在Spigot映射中查找匹配的字段，获取其Mojang混淆名(obf)
  3. 将类名转换为Mojang解混淆名
  4. 在Paper映射中查找对应的Mojang解混淆字段名
- 方法映射过程类似，但需要额外判断方法描述符
- 与RemapTranslationLegacy不同，此实现不会进行父类检索，直接在当前类中查找映射

## 使用场景
> 在Paper 1.20.6+环境中专门用于转译TabooLib内部类
> 执行Spigot Deobf -> Mojang Obf -> Mojang Deobf的转换过程

## 注意事项
> 仅在Paper 1.20.6+环境中启用
> 与RemapTranslation的基本实现不同，此类会对字段名和方法名进行转换
> 不进行父类检索，避免不必要的性能开销
> 方法映射时需要考虑方法描述符的匹配

