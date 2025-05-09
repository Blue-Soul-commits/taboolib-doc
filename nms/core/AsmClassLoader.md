# AsmClassLoader

## 基本信息
- 类名和包路径: taboolib.module.nms.AsmClassLoader
- 基本用途: 用于加载和定义动态生成的类字节码
- 类型: 单例对象（Kotlin object）
- 所属模块: bukkit-nms

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> createNewClass(name: String, arr: ByteArray): Class<*> -> 从字节数组创建新的类对象

### 类内可被访问字段
> 无类内可被访问字段

### 类方法
> findClass(name: String?): Class<*> -> 重写ClassLoader的findClass方法，尝试使用当前类的类加载器加载类

## 实现细节
- 继承自Java的ClassLoader类，父加载器设置为ClassAppender.getClassLoader()
- findClass方法首先尝试使用Class.forName加载类，如果失败则回退到父类的findClass方法
- createNewClass方法使用defineClass定义新的类，会将类名中的'/'替换为'.'
- 使用AsmClassLoader类的保护域(protectionDomain)来定义新类

## 使用场景
> 在NMS(Net.Minecraft.Server)相关操作中动态生成和加载类
> 在AsmClassTranslation中用于加载经过字节码转换后的类

## 注意事项
> 该类加载器主要用于内部实现，不建议直接在插件代码中使用
> 在使用createNewClass方法时，需要确保提供的字节码是有效的Java类字节码

