# PlayerOperator

## 基本信息
- 类名和包路径: taboolib.module.kether.PlayerOperator
- 基本用途: 用于操作玩家属性的工具类，提供读取和写入功能，支持增加、减少、修改等操作方法
- 类型: 类
- 所属模块: kether

## 类结构
### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> reader: Reader? -> 负责从玩家读取属性值的函数包装类，可为空
> writer: Writer? -> 负责将属性值写入玩家的函数包装类，可为空
> usable: Array<Method> -> 当前操作符支持的操作方法数组，默认支持增加、减少、修改

### 类方法
> 无

## 实现细节
- PlayerOperator类是Kether脚本中操作玩家属性的核心类
- 包含两个内部类Reader和Writer，分别封装了读取和写入玩家属性的函数
- Reader接收一个lambda函数，该函数接收ProxyPlayer参数并返回任意类型的属性值
- Writer接收一个lambda函数，该函数接收ProxyPlayer、操作方法和要写入的值作为参数
- 定义了Method枚举，表示可能的操作方法：增加(INCREASE)、减少(DECREASE)、修改(MODIFY)和无操作(NONE)
- 默认支持增加、减少和修改三种操作方法

## 使用场景
> 在Kether脚本中读取或修改玩家的属性值
> 提供统一的玩家属性操作接口，支持不同的操作方法
> 用于实现玩家属性的增加、减少或直接设置等功能
> 配合其他Kether脚本组件，实现复杂的玩家属性操作逻辑

## 注意事项
> reader和writer字段可为空，使用前应检查是否已初始化
> 使用前应确认所需的操作方法是否在usable数组中
> 该类使用ProxyPlayer而非直接使用Bukkit Player，保证了跨平台兼容性
> 操作方法的实际行为由Writer实现决定，需确保实现符合操作方法的语义
