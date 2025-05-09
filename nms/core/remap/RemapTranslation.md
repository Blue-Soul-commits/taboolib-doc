# RemapTranslation

## 基本信息
- 类名和包路径: taboolib.module.nms.remap.RemapTranslation
- 基本用途: 提供ASM字节码重映射功能，主要处理包名转换和类型映射
- 类型: 开放类
- 所属模块: bukkit-nms

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> obc1: Regex -> 匹配带版本号的CraftBukkit包路径的正则表达式
> obc2: String -> 当前Minecraft版本的CraftBukkit包路径
> obc3: String -> 无版本号的CraftBukkit包路径

### 类方法
> mapType(internalName: String): String -> 重写Remapper的mapType方法，处理类型映射
> map(internalName: String): String -> 重写Remapper的map方法，处理内部名称映射
> translate(key: String): String -> 包名转换方法，处理不同环境下的包路径转换
> findParents(owner: String): Set<String> -> 获取类的所有父类和接口

## 实现细节
- 继承自org.objectweb.asm.commons.Remapper类，用于ASM字节码转换
- 包名转换逻辑：
  1. 处理CraftBukkit包路径，根据环境决定是否移除版本号
  2. 在通用版本(isUniversal为true)环境下，将低版本包名替换为高版本包名
  3. 在非通用版本环境下，为Minecraft类添加版本号
- findParents方法通过递归获取类的所有父类和接口，用于处理继承关系中的映射

## 使用场景
> 在Paper 1.20.5+环境中用于转译插件本体里的类
> 移除包名中的跨版本信息(如v1_20_R3)
> 作为基类被RemapTranslationTabooLib和其他子类继承

## 注意事项
> 此实现不会对函数名和字段名进行检索转译，避免Paper对插件本体的转译失效
> 与RemapTranslationTabooLib不同，此类主要处理包名转换
> 在不同的Minecraft版本和服务器实现(Bukkit/Spigot/Paper)中有不同的行为

