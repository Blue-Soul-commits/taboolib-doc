# ItemSkull

## 基本信息
- 类名和包路径: taboolib.platform.util.ItemSkull
- 基本用途: 提供Bukkit头颅物品的扩展功能，用于获取头颅的Base64编码和皮肤URL
- 类型: Kotlin扩展函数文件
- 所属模块: bukkit-util

## 类结构

### 公开静态字段
> pattern: Pattern -> 用于匹配头颅皮肤URL的正则表达式模式

### 公开静态方法
> SkullMeta.getSkullValue(): String? -> 获取头颅的Base64编码值，如果为空则返回null
> SkullMeta.getSkinUrl(): String? -> 获取头颅皮肤的URL，如果无法获取则返回null

## 实现细节
- 使用正则表达式Pattern.compile("(http://.*?)\"")来匹配头颅皮肤中的URL
- 通过BukkitSkull工具类获取头颅的原始Base64编码值
- 使用Base64解码和UTF-8编码将头颅数据转换为可读的JSON字符串
- 从JSON字符串中提取皮肤URL
- 使用Kotlin的takeIf函数确保只返回非空的Base64值

## 使用场景
> 需要获取玩家头颅的皮肤信息时
> 开发自定义头颅系统时
> 需要复制或比较头颅皮肤时
> 实现头颅皮肤URL提取功能时
> 开发头颅收藏或管理插件时

## 注意事项
> 头颅的Base64编码包含完整的皮肤数据，可能较长
> 皮肤URL通常指向Minecraft官方纹理服务器(textures.minecraft.net)
> 在某些服务器环境下，可能无法获取到完整的头颅数据
> 该功能依赖于BukkitSkull工具类的实现
> 正则表达式只匹配http://开头的URL，不支持https://
