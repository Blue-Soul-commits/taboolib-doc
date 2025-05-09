# FileWatcher

## 基本信息
- 类名和包路径: taboolib.common5.FileWatcher
- 基本用途: 提供文件和目录变动监听功能，当文件或目录发生变化时执行指定操作
- 类型: 单例工具类
- 所属模块: common-legacy-api

## 类结构

### 公开静态字段
> INSTANCE: FileWatcher -> 文件监听器单例实例，默认检查间隔为500毫秒

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> executorService: ScheduledExecutorService -> 定时执行服务，用于定期检查文件变动
> fileListenerMap: Map<File, FileListener> -> 当前已注册的文件监听器列表
> watchService: WatchService -> 共享的 WatchService 实例，用于监听文件系统事件

### 类方法
> FileWatcher(interval: int): constructor -> 创建文件监听器实例，指定检查间隔时间（毫秒）
> addSimpleListener(file: File, runnable: Consumer<File>): void -> 添加简单的文件监听器
> addSimpleListener(file: File, runnable: Consumer<File>, runImmediately: boolean): void -> 添加简单的文件监听器，可选是否立即执行一次
> removeListener(file: File): void -> 移除文件的监听器
> release(): void -> 释放资源，关闭监听服务

## 实现细节
- 使用 Java NIO 的 WatchService 实现文件系统事件监听
- 采用单例模式设计，通过 INSTANCE 静态字段提供全局访问点
- 使用 ScheduledExecutorService 定期轮询 WatchService 获取文件变动事件
- 内部使用 FileListener 类管理每个被监听文件的具体监听逻辑
- 支持监听文件和目录，对目录监听会触发其内所有文件的变动事件
- 在 TabooLib 禁用阶段自动释放资源，防止内存泄漏

## 使用场景
> 监听配置文件变动，实现配置热重载功能
> 监听数据文件变化，自动更新内存中的数据
> 监听插件目录下的脚本文件，实现脚本热更新
> 实现文件同步或备份功能，当文件变化时自动执行同步操作

## 注意事项
> 监听器在 TabooLib 禁用时会自动释放，无需手动关闭
> 对于高频变动的文件，可能会触发多次回调，需要在回调中自行处理去重逻辑
> 文件监听基于操作系统的文件系统事件，在不同操作系统上可能有细微差异
> 监听大量文件可能会消耗较多系统资源，应适当控制监听文件数量