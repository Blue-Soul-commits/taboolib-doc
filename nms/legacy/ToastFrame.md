# ToastFrame

## 基本信息
- 类名和包路径: taboolib.module.nms.type.ToastFrame
- 基本用途: 定义 Minecraft 中成就提示（Toast）的框架类型
- 类型: 枚举类
- 所属模块: bukkit-nms-legacy

## 类结构

### 枚举值
> TASK -> 条目，普通成就框架
> GOAL -> 目标，中等难度成就框架
> CHALLENGE -> 挑战，高难度成就框架

## 实现细节
- 简单的枚举类，定义了三种成就框架类型
- 没有额外的方法或属性
- 用于 NMSToast 相关操作中指定成就提示的框架样式

## 使用场景
> 在发送虚拟成就提示时指定框架类型
> 在创建 Toast 对象时指定框架类型
> 用于控制成就提示在客户端的显示样式

## 注意事项
> 不同的框架类型在游戏中有不同的视觉效果：
  - TASK: 普通白色框架
  - GOAL: 绿色框架
  - CHALLENGE: 紫色框架