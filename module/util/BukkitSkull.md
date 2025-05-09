# BukkitSkull
## 基本信息
- 类名和包路径: taboolib.platform.util.BukkitSkull
- 基本用途: 提供跨版本的Minecraft头颅纹理处理工具
- 类型: Kotlin单例对象
- 所属模块: bukkit-util

## 类结构
### 私有静态字段
> use12: Boolean -> 检测是否为1.12.1及以上版本(支持setOwningPlayer方法)
> use13: Boolean -> 检测是否为1.13及以上版本(扁平化后的版本)
> use18: Boolean -> 检测是否为1.18.2及以上版本(支持PlayerProfile API)
> JSON_PARSER: JsonParser -> 用于解析Base64编码的头颅纹理数据
> DEFAULT_HEAD: ItemStack -> 默认的玩家头颅物品
> getProfileMethod: Method -> 获取Property值的反射方法，兼容不同版本
> gameProfileMethod: Field? -> 用于从ResolvableProfile中获取GameProfile的反射字段(1.21.1+)

### 公开静态方法
> applySkull(item: ItemStack, headBase64: String): ItemStack -> 将头颅纹理应用到指定物品
> applySkull(headBase64: String, func: Function<ItemStack, ItemStack?>?): ItemStack -> 创建新头颅并应用纹理，支持自定义处理
> applySkull(headBase64: String): ItemStack -> 创建新头颅并应用纹理
> applySkull(item: ItemStack, headBase64: String, func: Function<ItemStack, ItemStack?>?): ItemStack -> 核心方法，支持自定义处理函数
> getSkullValue(meta: SkullMeta): String -> 获取头颅的Base64纹理数据

### 私有静态方法
> encodeTexture(input: String): String -> 将纹理ID编码为完整的Base64纹理字符串
> getTextureURLFromBase64(headBase64: String): String -> 从Base64编码的纹理数据中提取纹理URL

## 实现细节
- 使用反射和运行时检测来支持从1.8到1.21.1+的所有Minecraft版本
- 针对不同版本的Minecraft提供不同的头颅纹理应用方法:
  - 1.12.1以下版本使用meta.owner设置头颅所有者
  - 1.12.1-1.18.1版本使用meta.owningPlayer设置头颅所有者
  - 1.18.2+版本使用PlayerProfile API设置头颅纹理
  - 1.21.1+版本处理了CraftMetaSkull中profile类型变更为ResolvableProfile的情况
- 支持两种类型的头颅纹理输入:
  - 玩家名称(长度<=20): 直接设置头颅所有者
  - Base64编码的纹理数据: 通过不同版本的API应用自定义纹理
- 提供自定义处理函数接口，允许插件开发者实现自己的头颅处理逻辑(如SkinsRestorer集成)

## 使用场景
> 创建自定义头颅物品，用于GUI菜单、装饰或特殊物品
> 在跨版本插件中统一处理头颅纹理，无需关心底层API差异
> 从现有头颅中提取纹理数据，用于保存或复制
> 支持离线服务器中使用自定义皮肤的玩家头颅
> 与第三方皮肤插件集成，通过自定义处理函数扩展功能

## 注意事项
> headBase64参数既可以是完整的Base64编码纹理，也可以是纹理ID(60-100字符)
> 对于纹理ID，会自动转换为完整的Base64编码纹理
> 在处理无效的Base64数据时可能抛出异常，应进行适当的错误处理
> 反射操作可能在未来版本中失效，需要定期更新兼容性代码
> 使用HTTP URL而非HTTPS是为了兼容旧版本Minecraft的纹理系统
