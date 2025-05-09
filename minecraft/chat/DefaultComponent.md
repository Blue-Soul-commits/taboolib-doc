# DefaultComponent
## 基本信息
- 类名和包路径: taboolib.module.chat.impl.DefaultComponent
- 基本用途: ComponentText接口的默认实现，提供完整的聊天组件功能
- 类型: 类
- 所属模块: minecraft-chat

## 类结构
### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> left: ArrayList<BaseComponent> -> 存储已处理完成的组件
> latest: ArrayList<BaseComponent> -> 存储当前正在处理的组件
> component: BaseComponent -> 计算属性，根据left和latest的状态返回适当的组件

### 类方法
> flush(): Unit -> 将latest中的组件移动到left中，并清空latest
> toRawMessage(): String -> 将组件转换为原始JSON格式的消息字符串
> toLegacyText(): String -> 将组件转换为带颜色代码的传统文本格式
> toPlainText(): String -> 将组件转换为不带任何格式的纯文本
> broadcast(): Unit -> 将消息广播给所有在线玩家
> sendTo(sender: ProxyCommandSender): Unit -> 将消息发送给指定的命令发送者
> newLine(): ComponentText -> 添加换行符
> plusAssign(text: String): Unit -> 重载+=运算符，添加文本
> plusAssign(other: ComponentText): Unit -> 重载+=运算符，添加其他组件
> append(text: String): ComponentText -> 添加文本
> append(other: ComponentText): ComponentText -> 添加其他组件
> appendTranslation(text: String, vararg obj: Any): ComponentText -> 添加翻译文本
> appendTranslation(text: String, obj: List<Any>): ComponentText -> 添加翻译文本(列表参数版本)
> appendKeybind(key: String): ComponentText -> 添加按键文本
> appendScore(name: String, objective: String): ComponentText -> 添加分数文本
> appendSelector(selector: String): ComponentText -> 添加选择器文本
> hoverText(text: String): ComponentText -> 设置悬停文本
> hoverText(text: List<String>): ComponentText -> 设置多行悬停文本
> hoverText(text: ComponentText): ComponentText -> 设置组件悬停文本
> hoverItem(id: String, nbt: String): ComponentText -> 设置悬停物品
> hoverEntity(id: String, type: String?, name: String?): ComponentText -> 设置悬停实体
> hoverEntity(id: String, type: String?, name: ComponentText?): ComponentText -> 设置悬停实体(组件名称版本)
> click(action: ClickAction, value: String): ComponentText -> 设置点击动作
> clickOpenURL(url: String): ComponentText -> 设置点击打开URL
> clickOpenFile(file: String): ComponentText -> 设置点击打开文件
> clickRunCommand(command: String): ComponentText -> 设置点击执行命令
> clickSuggestCommand(command: String): ComponentText -> 设置点击建议命令
> clickChangePage(page: Int): ComponentText -> 设置点击切换页面
> clickCopyToClipboard(text: String): ComponentText -> 设置点击复制到剪贴板
> clickInsertText(text: String): ComponentText -> 设置点击插入文本
> decoration(decoration: Decoration): ComponentText -> 应用文本装饰
> undecoration(decoration: Decoration): ComponentText -> 移除特定文本装饰
> undecoration(): ComponentText -> 移除所有文本装饰
> bold(): ComponentText -> 设置粗体
> unbold(): ComponentText -> 移除粗体
> italic(): ComponentText -> 设置斜体
> unitalic(): ComponentText -> 移除斜体
> underline(): ComponentText -> 设置下划线
> ununderline(): ComponentText -> 移除下划线
> strikethrough(): ComponentText -> 设置删除线
> unstrikethrough(): ComponentText -> 移除删除线
> obfuscated(): ComponentText -> 设置混淆效果
> unobfuscated(): ComponentText -> 移除混淆效果
> font(font: String): ComponentText -> 设置字体
> unfont(): ComponentText -> 移除字体
> color(color: StandardColors): ComponentText -> 设置标准颜色
> color(color: Color): ComponentText -> 设置RGB颜色
> uncolor(): ComponentText -> 移除颜色
> toSpigotObject(): BaseComponent -> 转换为Spigot的BaseComponent对象
> toLegacyRawMessage(): RawMessage -> 转换为TabooLib的RawMessage对象
> toString(): String -> 重写toString方法，返回原始JSON格式

## 实现细节
- DefaultComponent实现了ComponentText接口，提供了完整的聊天组件功能
- 使用两个ArrayList分别存储已处理完成的组件(left)和当前正在处理的组件(latest)
- 通过flush()方法将latest中的组件移动到left中，实现组件的分段处理
- 初始化时应用RESET颜色，确保组件有一个干净的起点
- 提供了丰富的方法来设置组件的文本内容、样式、颜色和交互行为
- 对不同版本的Minecraft API进行了兼容处理，使用try-catch捕获可能的错误
- 实现了Source接口的方法，支持将组件广播给所有玩家或发送给特定玩家
- 重载了+=运算符，提供了更简洁的组件拼接语法

## 使用场景
> 作为TabooLib聊天模块的核心实现类，提供完整的聊天组件功能
> 在需要创建复杂聊天消息的插件中使用，支持颜色、样式和交互
> 与Components工厂类配合，构建各种类型的聊天组件
> 在需要发送JSON格式聊天消息的场景中使用，支持现代Minecraft的所有聊天功能

## 注意事项
> 某些方法(如hoverEntity)在旧版本Minecraft中可能不受支持
> 使用append(other: ComponentText)方法时，other必须是DefaultComponent类型，否则会抛出异常
> 使用hoverText(text: ComponentText)方法时，text必须是DefaultComponent类型，否则会抛出错误
> 组件的处理采用了缓冲区模式，修改样式只影响latest中的组件，调用flush()后才会应用到整个组件
> 在不同版本的Minecraft中，某些API可能有所不同，类中使用try-catch处理了这些差异
