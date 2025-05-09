# AsmClassTranslation

## 基本信息
- 类名和包路径: taboolib.module.nms.AsmClassTranslation
- 基本用途: 提供类字节码转译功能，将类文件转换为适应当前Minecraft环境的格式
- 类型: 具体实现类
- 所属模块: bukkit-nms

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> source: String -> 要转译的类的全限定名

### 类方法
> createNewClass(): Class<*> -> 创建转译后的类实例

## 实现细节
- 转译过程：
  1. 从类加载器中获取目标类的字节码
  2. 计算字节码的摘要值用于缓存标识
  3. 尝试从缓存中读取已转译的类
  4. 如果缓存不存在，则进行转译：
     - 创建ClassReader读取原始字节码
     - 创建ClassWriter用于生成新字节码
     - 根据运行环境选择合适的Remapper实现
     - 使用ClassRemapper进行字节码转换
     - 将转换后的字节码保存到缓存
     - 使用AsmClassLoader加载转换后的类
  5. 返回转译后的类实例

## 使用场景
> 在nmsProxy方法中用于创建NMS代理类
> 处理TabooLib类和插件类的字节码转换，使其适应不同版本的Minecraft环境

## 注意事项
> 方法使用@Synchronized注解确保线程安全
> 根据运行环境和目标类选择不同的转换器：
  - 在Paper环境下，TabooLib类使用RemapTranslationTabooLib
  - 在Paper环境下，其他类使用RemapTranslation
  - 在非Paper环境下，使用RemapTranslationLegacy
> 使用缓存机制提高性能，避免重复转译

