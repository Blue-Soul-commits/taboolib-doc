# Slots

## 基本信息
- 类名和包路径: taboolib.platform.util.Slots
- 基本用途: 提供 Minecraft 物品栏槽位索引的常量集合，便于界面设计和物品放置
- 类型: 工具类
- 所属模块: taboolib.platform.util

## 类结构

### 公开静态字段
> CENTER: List<Integer> -> 物品栏中心区域的槽位索引集合
> BORDER: List<Integer> -> 物品栏边框区域的槽位索引集合
> LINE_1: List<Integer> -> 物品栏第1行的所有槽位索引
> LINE_2: List<Integer> -> 物品栏第2行的所有槽位索引
> LINE_3: List<Integer> -> 物品栏第3行的所有槽位索引
> LINE_4: List<Integer> -> 物品栏第4行的所有槽位索引
> LINE_5: List<Integer> -> 物品栏第5行的所有槽位索引
> LINE_6: List<Integer> -> 物品栏第6行的所有槽位索引
> LINE_1_LEFT: Integer -> 物品栏第1行左侧槽位索引 (0)
> LINE_1_MIDDLE: Integer -> 物品栏第1行中间槽位索引 (4)
> LINE_1_RIGHT: Integer -> 物品栏第1行右侧槽位索引 (8)
> LINE_2_LEFT: Integer -> 物品栏第2行左侧槽位索引 (9)
> LINE_2_MIDDLE: Integer -> 物品栏第2行中间槽位索引 (13)
> LINE_2_RIGHT: Integer -> 物品栏第2行右侧槽位索引 (17)
> LINE_3_LEFT: Integer -> 物品栏第3行左侧槽位索引 (18)
> LINE_3_MIDDLE: Integer -> 物品栏第3行中间槽位索引 (22)
> LINE_3_RIGHT: Integer -> 物品栏第3行右侧槽位索引 (26)
> LINE_4_LEFT: Integer -> 物品栏第4行左侧槽位索引 (27)
> LINE_4_MIDDLE: Integer -> 物品栏第4行中间槽位索引 (31)
> LINE_4_RIGHT: Integer -> 物品栏第4行右侧槽位索引 (35)
> LINE_5_LEFT: Integer -> 物品栏第5行左侧槽位索引 (36)
> LINE_5_MIDDLE: Integer -> 物品栏第5行中间槽位索引 (40)
> LINE_5_RIGHT: Integer -> 物品栏第5行右侧槽位索引 (44)
> LINE_6_LEFT: Integer -> 物品栏第6行左侧槽位索引 (45)
> LINE_6_MIDDLE: Integer -> 物品栏第6行中间槽位索引 (49)
> LINE_6_RIGHT: Integer -> 物品栏第6行右侧槽位索引 (53)

### 公开静态方法
> 无

### 类内可被访问字段
> 无

### 类方法
> of(slots: int...): List<Integer> -> 私有工具方法，将整数数组转换为整数列表

## 实现细节
- 基于标准的 6×9 物品栏布局定义了常用的槽位索引常量
- 使用私有的 of 方法将整数数组转换为 List<Integer> 类型
- CENTER 常量定义了物品栏中心 4×7 的区域，通常用于放置主要内容
- BORDER 常量定义了物品栏边缘的所有槽位，通常用于装饰或边框
- 提供了每一行的完整槽位列表（LINE_1 到 LINE_6）
- 为每一行提供了左侧、中间和右侧的特定槽位索引

## 使用场景
> 创建自定义 GUI 界面时快速引用常用槽位
> 在物品栏边框放置装饰性物品
> 在物品栏中心区域放置功能性物品
> 在特定行或特定位置放置重要按钮或信息
> 批量设置或清除特定区域的物品

## 注意事项
> 槽位索引基于 0-53 的范围，对应标准的 6×9 物品栏
> 使用这些常量可以提高代码可读性，避免硬编码槽位索引
> 这些常量适用于 Chest 类型的物品栏，其他类型物品栏可能有不同的布局
> 所有常量都是不可变的 List 或 Integer，不应尝试修改其内容
