# NMSMap

## 基本信息
- 类名和包路径: taboolib.module.nms.NMSMap
- 基本用途: 提供在 Minecraft 中创建和发送自定义地图画的功能
- 类型: 类和扩展函数
- 所属模块: bukkit-nms-legacy

## 类结构

### 扩展函数
> buildMap(url: String, hand: NMSMap.Hand = NMSMap.Hand.MAIN, width: Int = 128, height: Int = 128, builder: ItemBuilder.() -> Unit = {}): NMSMap -> 从 URL 字符串创建地图画（已废弃）
> buildMap(url: URL, hand: NMSMap.Hand = NMSMap.Hand.MAIN, width: Int = 128, height: Int = 128, builder: ItemBuilder.() -> Unit = {}): CompletableFuture<NMSMap> -> 从 URL 异步创建地图画（已废弃）
> buildMap(file: File, hand: NMSMap.Hand = NMSMap.Hand.MAIN, width: Int = 128, height: Int = 128, builder: ItemBuilder.() -> Unit = {}): NMSMap -> 从文件创建地图画（已废弃）
> buildMap(image: BufferedImage, hand: NMSMap.Hand = NMSMap.Hand.MAIN, width: Int = 128, height: Int = 128, builder: ItemBuilder.() -> Unit = {}): NMSMap -> 从图像对象创建地图画（已废弃）
> Player.sendMap(url: String, hand: NMSMap.Hand = NMSMap.Hand.MAIN, width: Int = 128, height: Int = 128, builder: ItemBuilder.() -> Unit = {}) -> 向玩家发送 URL 字符串地图画（已废弃）
> Player.sendMap(url: URL, hand: NMSMap.Hand = NMSMap.Hand.MAIN, width: Int = 128, height: Int = 128, builder: ItemBuilder.() -> Unit = {}) -> 向玩家发送 URL 地图画（已废弃）
> Player.sendMap(file: File, hand: NMSMap.Hand = NMSMap.Hand.MAIN, width: Int = 128, height: Int = 128, builder: ItemBuilder.() -> Unit = {}) -> 向玩家发送文件地图画（已废弃）
> Player.sendMap(image: BufferedImage, hand: NMSMap.Hand = NMSMap.Hand.MAIN, width: Int = 128, height: Int = 128, builder: ItemBuilder.() -> Unit = {}) -> 向玩家发送图像对象地图画（已废弃）
> BufferedImage.zoomed(width: Int = 128, height: Int = 128): BufferedImage -> 调整图像分辨率（已废弃）

### 类属性和方法
> NMSMap.Hand 枚举: MAIN, OFF -> 表示地图在主手还是副手显示
> image: BufferedImage -> 地图画的图像
> hand: Hand -> 地图显示的手
> builder: ItemBuilder.() -> Unit -> 物品构建器
> mapRenderer: MapRenderer -> 地图渲染器
> mapView: MapView -> 地图视图
> mapItem: ItemStack -> 地图物品
> sendTo(player: Player) -> 向玩家发送地图画
> getMainHandSlot(player: Player): Int -> 获取主手槽位

### 静态属性
> classPacketPlayOutSetSlot: Class<*> -> 设置物品槽数据包类
> classPacketPlayOutMap: Class<*> -> 地图数据包类
> classCraftItemStack: Class<*> -> CraftItemStack 类
> classMapIcon: Class<*> -> 地图图标类
> classMapData: Class<*> -> 地图数据类
> classMapId: Class<*> -> 地图 ID 类（1.20+ 兼容）

## 实现细节
- 所有扩展函数都标记为 @Deprecated，表示不再维护
- 支持从 URL、文件或 BufferedImage 创建地图画
- 使用 MapRenderer 在地图上绘制图像
- 通过发送数据包将地图显示在玩家的主手或副手
- 根据不同的 Minecraft 版本使用不同的数据包结构
- 支持 Minecraft 1.8 到 1.21+ 版本
- 使用反射获取和设置 NMS 类的属性和方法

## 使用场景
> 在游戏中显示自定义图像
> 创建自定义地图画
> 向玩家发送图像信息
> 实现自定义 UI 元素

## 注意事项
> 所有功能已标记为废弃，不再维护
> 从 URL 创建地图画会在主线程上执行 I/O 操作，应避免使用
> 地图最佳显示分辨率为 128x128
> 不同版本的 Minecraft 使用不同的数据包结构
> 1.21+ 版本中，地图 ID 和颜色补丁使用了 Optional 包装

