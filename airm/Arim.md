# Arim

## 基本信息
- 类名和包路径: top.maplex.arim.Arim
- 基本用途: Arim工具库的核心入口类，提供对各种工具模块的访问
- 类型: 单例对象(object)
- 所属模块: 核心模块

## 类结构

### 公开静态字段
> evaluator: ConditionEvaluator -> 条件表达式求值器
> fixedCalculator: FixedCalculator -> 固定算数表达式计算器
> variableCalculator: VariableCalculator -> 变量计算器
> itemMatch: ItemMatch -> 物品匹配工具
> entityMatch: EntityMatch -> 实体匹配工具
> glow: IGlow -> 生物&方块发光工具
> weightRandom: WeightRandom -> 权重随机工具
> itemManager: ItemManager -> 物品管理器

## 实现细节
- 所有工具类都使用懒加载(lazy)方式初始化，仅在首次使用时创建实例
- 部分工具（如folderReader和tabooLegacyStyleCommandHelper）需要通过扩展函数使用

## 使用场景
> 作为统一入口访问各种工具模块
> 在插件开发中获取Arim提供的各种工具功能
