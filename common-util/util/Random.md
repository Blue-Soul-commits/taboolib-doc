# RandomUtil

## 基本信息
- 类名和包路径: taboolib.common.util.RandomUtil
- 基本用途: 提供线程安全的随机数生成工具
- 类型: Kotlin工具函数文件
- 所属模块: common-util

## 函数
> random(): Random -> 创建线程安全的随机数生成器
> random(v: Double): Boolean -> 根据概率返回布尔值
> random(v: Int): Int -> 生成0到v-1之间的随机整数
> random(num1: Int, num2: Int): Int -> 生成num1到num2之间的随机整数(包含边界)
> random(num1: Double, num2: Double): Double -> 生成num1到num2之间的随机浮点数
> randomDouble(): Double -> 生成0到1之间的随机浮点数

## 实现细节
- 所有函数都使用`ThreadLocalRandom.current()`作为随机数源，确保线程安全
- 整数范围随机使用`min`和`max`函数确保参数顺序正确
- 对于整数范围随机，结果包含两个边界值
- 对于浮点数范围随机，特殊处理min等于max的情况
- `randomDouble()`是`random().nextDouble()`的简便方法

## 使用场景
> 需要线程安全的随机数生成
> 游戏中的随机事件和掉落物品
> 模拟概率事件
> 生成随机范围内的数值
> 随机算法实现

## 注意事项
> `random(v: Int)`生成的是0到v-1之间的整数，不包含v
> `random(num1: Int, num2: Int)`生成的整数包含两个边界值
> `random(v: Double)`中v应该在0到1之间，表示概率
> 所有函数都是线程安全的，适合在并发环境中使用
> 这些函数不是加密安全的，不应用于安全敏感场景
