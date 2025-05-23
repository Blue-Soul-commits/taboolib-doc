# LightType

## 基本信息
- 类名和包路径: taboolib.module.nms.type.LightType
- 基本用途: 定义 Minecraft 中的光照类型
- 类型: 枚举类
- 所属模块: bukkit-nms-legacy

## 类结构

### 枚举值
> SKY -> 天空光照
> BLOCK -> 方块光照
> ALL -> 同时包含天空和方块光照

## 实现细节
- 简单的枚举类，定义了三种光照类型
- 没有额外的方法或属性
- 用于 NMSLight 相关操作中指定光照类型

## 使用场景
> 在创建或删除光源时指定光照类型
> 在获取或设置光照等级时指定光照类型
> 在更新区块光照时指定要更新的光照类型

## 注意事项
> SKY 类型仅在有天空的维度中有效（主世界、末地）
> BLOCK 类型在所有维度中都有效
> ALL 类型会同时处理 SKY 和 BLOCK 两种光照