# BookBuilder
## 基本信息
- 类名和包路径: taboolib.platform.util.BookBuilder
- 基本用途: 用于构建和发送书本物品给玩家，支持普通文本和原始JSON文本
- 类型: Kotlin类，继承自ItemBuilder
- 所属模块: bukkit-util

## 类结构
### 公开静态方法
> buildBook(builder: BookBuilder.() -> Unit = {}): ItemStack -> 构建一本书并返回ItemStack对象
> Player.sendBook(builder: BookBuilder.() -> Unit = {}): Unit -> 构建一本书并发送给玩家
> Player.sendBook(itemStack: ItemStack): Unit -> 发送一本书给玩家

### 类内可被访问字段
> title: String -> 书本标题，默认为"untitled"
> author: String -> 书本作者，默认为"untitled"
> bookPages: ArrayList<Text> -> 书本页面集合

### 类方法
> write(text: String): Unit -> 添加普通文本页面
> write(text: Source): Unit -> 添加Source对象页面，转换为原始JSON
> write(text: RawMessage): Unit -> 添加RawMessage对象页面，转换为原始JSON
> writeRaw(text: String): Unit -> 添加原始JSON文本页面
> build(): ItemStack -> 构建并返回书本物品

## 实现细节
- 继承自ItemBuilder类，默认材质为WRITTEN_BOOK
- 使用内部Text类存储页面内容，区分普通文本和原始JSON文本
- 通过反射机制实现跨版本兼容，支持不同版本的Minecraft服务端
- 使用unsafeLazy延迟加载NMS和OBC类，减少启动时的类加载开销
- 发送书本时会尝试使用Player.openBook方法，如果不存在则回退到使用NMS方法

## 使用场景
> 创建包含富文本的书本物品
> 向玩家发送包含交互元素的书本界面
> 制作游戏内的帮助文档或教程

## 注意事项
> 文件头部有@file:Suppress("DEPRECATION")注解，表明使用了一些已过时的API
> 代码中有"NOTICE 无需兼容 Paper 1.20.5"的注释，表明不需要为Paper 1.20.5版本做特殊处理
> 使用了反射机制访问Minecraft内部类，可能在未来版本中失效
> 原始JSON文本需要符合Minecraft的JSON文本格式规范