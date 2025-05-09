# ClickAction
## 基本信息
- 类名和包路径: taboolib.module.chat.ClickAction
- 基本用途: 定义聊天组件点击时可执行的动作类型
- 类型: 枚举类
- 所属模块: minecraft-chat

## 类结构
### 公开静态字段
> OPEN_URL: ClickAction -> 打开URL链接
> OPEN_FILE: ClickAction -> 打开文件
> RUN_COMMAND: ClickAction -> 执行命令
> SUGGEST_COMMAND: ClickAction -> 在聊天框中填入命令
> CHANGE_PAGE: ClickAction -> 切换书本页面
> COPY_TO_CLIPBOARD: ClickAction -> 复制内容到剪贴板
> INSERTION: ClickAction -> 在聊天框中插入文本

### 公开静态方法
> values(): Array<ClickAction> -> 返回包含所有枚举常量的数组
> valueOf(name: String): ClickAction -> 返回指定名称的枚举常量

### 类内可被访问字段
> 无额外字段

### 类方法
> 无额外方法

## 实现细节
- ClickAction枚举定义了Minecraft聊天组件支持的七种点击动作类型
- 每个枚举值对应一种特定的交互行为
- 作为Kotlin枚举类，自动提供values()和valueOf(String)方法
- 这些动作类型与Minecraft聊天组件系统的点击事件直接对应

## 使用场景
> 在ComponentText接口的实现中，用于设置文本点击时的行为
> 创建可交互的聊天消息，如可点击的链接、命令按钮等
> 构建具有复杂交互功能的书本内容
> 与其他聊天组件接口配合，实现丰富的用户交互体验

## 注意事项
> 不同的Minecraft版本对点击动作的支持可能有所不同
> OPEN_FILE动作在客户端可能受到安全限制
> COPY_TO_CLIPBOARD动作在较旧的Minecraft版本中可能不受支持
> 使用RUN_COMMAND时，执行的命令将以玩家身份运行，受权限限制
> CHANGE_PAGE动作仅在书本界面中有效

