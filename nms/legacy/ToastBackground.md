# ToastBackground

## 基本信息
- 类名和包路径: taboolib.module.nms.type.ToastBackground
- 基本用途: 定义 Minecraft 中成就提示（Toast）的背景图片
- 类型: 枚举类
- 所属模块: bukkit-nms-legacy

## 类结构

### 枚举值
> ADVENTURE -> 冒险背景，对应冒险主题的成就背景
> END -> 末地之路背景，对应末地主题的成就背景

### 属性
> url: String -> 背景图片的资源路径

## 实现细节
- 枚举类，定义了两种成就背景类型
- 每个枚举值都包含一个 url 属性，指向 Minecraft 资源包中的纹理路径
- 用于 NMSToast 相关操作中指定成就提示的背景图片

## 使用场景
> 在发送虚拟成就提示时指定背景图片
> 在创建 Toast 对象时指定背景图片
> 用于控制成就提示在客户端的显示样式

## 注意事项
> 不同的背景类型在游戏中有不同的视觉效果：
  - ADVENTURE: 冒险主题背景，带有探险地图样式
  - END: 末地主题背景，带有末地星空样式
> 在 Minecraft 1.20.2 及以上版本中，sendToast 方法不再可用
> url 属性使用 Minecraft 命名空间格式的资源路径
