# PrimitiveLoader

## 基本信息
- 类名和包路径: taboolib.common.PrimitiveLoader
- 基本用途: TabooLib 的依赖加载器，负责下载和加载依赖项
- 类型: 工具类
- 所属模块: Common
---
## 类结构

### 公开静态字段
> TABOOLIB_GROUP: String -> TabooLib 的 Maven 组 ID
> TABOOLIB_PACKAGE_NAME: String -> TabooLib 的包名
> TABOOPROJECT_GROUP: String -> TabooProject 的 Maven 组 ID
> ASM_GROUP: String -> ASM 的 Maven 组 ID
> JR_GROUP: String -> JarRelocator 的 Maven 组 ID
> projectPackageName: String -> 项目包名

### 公开静态方法
> init(): void -> 初始化各模块
> getCacheFile(): File -> 获取缓存路径
> getLibraryFile(): File -> 获取依赖库保存路径

### 类内可被访问字段
> (无额外字段)

### 类方法
> load(repo: String, group: String, name: String, version: String, isIsolated: boolean, isExternal: boolean, relocate: List<String[]>): boolean -> 从仓库下载模块并加载
> loadAll(): void -> 加载完整模块
> loadFile(file: File, isIsolated: boolean, isExternal: boolean, relocate: List<String[]>, forceRelocate: boolean): void -> 加载文件
> deepHashCode(array: List<String[]>): int -> 计算深层哈希码
---
## 实现细节
> 支持从多个仓库下载依赖
> 支持对加载的 JAR 包进行重定向，避免依赖冲突
> 使用 SHA-1 哈希验证下载文件的完整性
> 在开发模式下提供强制下载选项
---
## 使用场景
> 加载 TabooLib 模块和第三方依赖
> 在隔离模式下启动 Kotlin 环境
> 下载和验证依赖库
---
## 注意事项
> 必须在 IsolatedClassLoader 中运行 init() 方法
> 依赖 JarRelocator 进行 JAR 包重定向
> 在开发模式下可能会强制下载依赖