# ChatColorFormat

## 基本信息
- 类名和包路径: taboolib.module.nms.type.ChatColorFormat
- 基本用途: 提供记分板颜色格式的枚举定义
- 类型: 枚举类
- 所属模块: bukkit-nms-stable

## 类结构

### 公开静态字段
> BLACK: ChatColorFormat -> 黑色
> DARK_BLUE: ChatColorFormat -> 深蓝色
> DARK_GREEN: ChatColorFormat -> 深绿色
> DARK_AQUA: ChatColorFormat -> 深青色
> DARK_RED: ChatColorFormat -> 深红色
> DARK_PURPLE: ChatColorFormat -> 深紫色
> GOLD: ChatColorFormat -> 金色
> GRAY: ChatColorFormat -> 灰色
> DARK_GRAY: ChatColorFormat -> 深灰色
> BLUE: ChatColorFormat -> 蓝色
> GREEN: ChatColorFormat -> 绿色
> AQUA: ChatColorFormat -> 青色
> RED: ChatColorFormat -> 红色
> LIGHT_PURPLE: ChatColorFormat -> 淡紫色
> YELLOW: ChatColorFormat -> 黄色
> WHITE: ChatColorFormat -> 白色
> OBFUSCATED: ChatColorFormat -> 随机字符效果
> BOLD: ChatColorFormat -> 粗体效果
> STRIKETHROUGH: ChatColorFormat -> 删除线效果
> UNDERLINE: ChatColorFormat -> 下划线效果
> ITALIC: ChatColorFormat -> 斜体效果
> RESET: ChatColorFormat -> 重置所有格式

### 公开静态方法
> 无

### 类内可被访问字段
> 无

### 类方法
> 无

## 实现细节
- 重新定义了一个枚举类，因为原版的 ChatColor 不是枚举类
- 包含了所有 Minecraft 支持的颜色和格式化代码
- 枚举值名称与 Minecraft 的 EnumChatFormat 保持一致

## 使用场景
> 在设置记分板队伍颜色时使用
> 在 NMS 包装中用于转换颜色格式
> 在 PlayerScoreboard 类中用于设置队伍颜色

## 注意事项
> 枚举值的名称必须与 Minecraft 的 EnumChatFormat 保持一致，以确保正确转换
> 在不同版本的 Minecraft 中，颜色格式的实现可能有所不同，但枚举名称保持一致