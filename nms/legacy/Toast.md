# Toast

## 基本信息
- 类名和包路径: taboolib.module.nms.type.Toast
- 基本用途: 表示 Minecraft 中的成就提示（Toast）信息
- 类型: 数据类
- 所属模块: bukkit-nms-legacy

## 类结构

### 属性
> material: Material -> 物品材质，用于显示在成就提示中的图标
> message: String -> 消息内容，显示在成就提示中的文本
> frame: ToastFrame -> 框架类型，决定成就提示的视觉样式

## 实现细节
- 简单的数据类，用于封装成就提示的基本信息
- 没有额外的方法，仅包含三个属性
- 作为 NMSToast 相关操作的参数和返回值

## 使用场景
> 在发送虚拟成就提示时作为缓存
> 在创建自定义成就提示时封装必要信息
> 用于存储和传递成就提示的配置

## 注意事项
> 在 Minecraft 1.20.2 及以上版本中，相关的 sendToast 方法不再可用
> material 属性决定了成就提示中显示的图标
> message 属性是成就提示中显示的文本内容
> frame 属性决定了成就提示的框架样式（普通、目标或挑战）
