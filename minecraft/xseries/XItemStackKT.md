# XItemStack 扩展函数
## 基本信息
- 类名和包路径: taboolib.library.xseries.XItemStack (扩展函数)
- 基本用途: 提供对 Bukkit ItemStack 的序列化、反序列化以及字符串转换为物品相关对象的扩展功能
- 类型: Kotlin 扩展函数集合
- 所属模块: platform-bukkit-impl

## 类结构
### 公开扩展方法
> ConfigurationSection.setItemStack(node: String, itemStack: ItemStack): Unit -> 将 ItemStack 序列化并保存到配置节点中
> ConfigurationSection.getItemStack(node: String): ItemStack? -> 从配置节点中反序列化 ItemStack 对象，使用默认的颜色转换
> ConfigurationSection.getItemStack(node: String, transfer: (String) -> String): ItemStack? -> 从配置节点中反序列化 ItemStack 对象，并应用自定义转换函数
> String.parseToMaterial(): Material -> 将字符串解析为 Material 对象
> String.parseToXMaterial(): XMaterial -> 将字符串解析为 XMaterial 对象
> String.parseToItemStack(): ItemStack -> 将字符串解析为 ItemStack 对象

## 实现细节
- 使用 XItemStack 类的 serialize 和 deserialize 方法实现物品的序列化和反序列化
- 默认的反序列化过程使用 colored() 函数处理文本颜色
- 字符串转换为物品相关对象时，如果无法匹配则默认返回 STONE 类型
- 所有字符串到物品的转换都通过 XMaterial 系统进行，以确保跨版本兼容性

## 使用场景
> 配置文件中保存和读取物品数据
> 从字符串标识符创建物品
> 跨版本兼容的物品处理

## 注意事项
> 所有字符串到物品的转换在失败时都会返回 STONE 类型，而不是抛出异常
> parseToItemStack() 方法在 XMaterial.parseItem() 返回 null 时会抛出 NPE，因为使用了非空断言(!!)
> 使用 getItemStack() 时，如果配置节点不存在会返回 null
