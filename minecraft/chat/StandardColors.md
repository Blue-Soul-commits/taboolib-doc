# StandardColors
## 基本信息
- 类名和包路径: taboolib.module.chat.StandardColors
- 基本用途: 提供Minecraft标准颜色的枚举，支持中英文颜色名称的转换和匹配
- 类型: 枚举类
- 所属模块: minecraft-chat

## 类结构
### 公开静态字段
> BLACK: StandardColors -> 黑色，对应ChatColor.BLACK
> DARK_BLUE: StandardColors -> 深蓝色，对应ChatColor.DARK_BLUE
> DARK_GREEN: StandardColors -> 深绿色，对应ChatColor.DARK_GREEN
> DARK_AQUA: StandardColors -> 深青色，对应ChatColor.DARK_AQUA
> DARK_RED: StandardColors -> 深红色，对应ChatColor.DARK_RED
> DARK_PURPLE: StandardColors -> 深紫色，对应ChatColor.DARK_PURPLE
> GOLD: StandardColors -> 金色，对应ChatColor.GOLD
> GRAY: StandardColors -> 灰色，对应ChatColor.GRAY
> DARK_GRAY: StandardColors -> 深灰色，对应ChatColor.DARK_GRAY
> BLUE: StandardColors -> 蓝色，对应ChatColor.BLUE
> GREEN: StandardColors -> 绿色，对应ChatColor.GREEN
> AQUA: StandardColors -> 青色，对应ChatColor.AQUA
> RED: StandardColors -> 红色，对应ChatColor.RED
> LIGHT_PURPLE: StandardColors -> 浅紫色，对应ChatColor.LIGHT_PURPLE
> YELLOW: StandardColors -> 黄色，对应ChatColor.YELLOW
> WHITE: StandardColors -> 白色，对应ChatColor.WHITE
> RESET: StandardColors -> 重置颜色，对应ChatColor.RESET

### 公开静态方法
> match(in: String): Optional<StandardColors> -> 根据颜色名称（英文或中文）匹配对应的StandardColors枚举值

### 类内可被访问字段
> display: String -> 颜色的中文名称
> chatColor: ChatColor -> 对应的Bukkit ChatColor对象

### 类方法
> getDisplay(): String -> 获取颜色的中文名称
> toChatColor(): ChatColor -> 获取对应的Bukkit ChatColor对象

## 实现细节
- 每个枚举值都包含两个属性：中文名称(display)和对应的ChatColor对象(chatColor)
- match方法通过遍历所有枚举值，比较输入字符串与枚举名称（英文）或中文名称是否匹配（忽略大小写）
- 如果找到匹配的颜色，返回包含该颜色的Optional对象；否则返回空的Optional对象
- 支持通过英文名称（如"RED"）或中文名称（如"红"）来匹配颜色

## 使用场景
> 在需要支持中英文颜色名称的聊天消息系统中使用
> 与HexColor类配合，实现更丰富的颜色表达方式
> 在ComponentText接口的实现中，用于设置文本组件的颜色
> 在国际化插件中，提供一致的颜色名称映射

## 注意事项
> 使用match方法时，返回的是Optional对象，需要进行适当的空值处理
> 中文名称是简化的单字表示（如"红"代表红色），便于用户输入
> 在不同的Minecraft版本中，ChatColor的实现可能有所不同，但StandardColors提供了一致的接口

