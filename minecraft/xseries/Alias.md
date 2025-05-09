# Alias
## 基本信息
- 类名和包路径: taboolib.library.xseries.Alias
- 基本用途: 为XSeries库中的类提供类型别名，简化代码使用
- 类型: Kotlin类型别名文件
- 所属模块: TabooLib XSeries 库

## 类结构
### 公开类型别名
> XMaterialUtil<T>: XTag<T> -> 为XTag类提供别名，用于材料分类和标签系统
> ProxyParticle: XParticle -> 为XParticle类提供别名，用于粒子效果处理

## 实现细节
- 使用Kotlin的typealias关键字定义类型别名
- 不包含任何实际实现代码，仅提供类型引用

## 使用场景
> 当需要使用XTag进行材料分类时，可以使用更直观的XMaterial名称
> 当处理粒子效果时，可以使用ProxyParticle作为XParticle的替代名称

## 注意事项
> 类型别名仅在Kotlin代码中有效，在Java代码中需使用原始类名
> 类型别名不会创建新的类型，只是原类型的引用

