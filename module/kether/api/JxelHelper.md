# JexlHelper

## 基本信息
- 类名和包路径: taboolib.expansion.JexlHelper (文件名，非类名)
- 基本用途: Apache JEXL表达式引擎的辅助工具，提供简化的JEXL表达式编译和使用接口
- 类型: 工具函数和扩展函数集合
- 所属模块: script-jexl

## 类结构
### 公开静态字段
> defaultJexlCompiler: JexlCompiler -> 默认的JEXL编译器实例，懒加载

### 公开静态方法
> String.compileToScript(compiler: JexlCompiler = defaultJexlCompiler): JexlScript -> 将字符串编译为JEXL脚本
> String.compileToExpression(compiler: JexlCompiler = defaultJexlCompiler): JexlExpression -> 将字符串编译为JEXL表达式

### 类内可被访问字段
> 无

### 类方法
> 无（文件中只包含扩展函数和全局变量）

## 实现细节
- 文件使用@Inject注解标记为自动注入
- 使用@RuntimeDependency声明对Apache Commons JEXL3的依赖
- 指定了版本3.2.1，并使用特殊的重定位规则(!org.apache.commons.jexl3 -> !org.apache.commons.jexl3_3_2_1)
- 通过unsafeLazy委托创建默认的JexlCompiler实例，延迟初始化
- 为String类提供两个扩展函数，分别用于编译JEXL脚本和表达式
- 默认使用全局defaultJexlCompiler，但也允许传入自定义的编译器实例

## 使用场景
> 在TabooLib环境中简化JEXL表达式的使用
> 提供字符串到JEXL脚本/表达式的快速转换
> 支持动态评估数学和逻辑表达式
> 作为脚本模块的基础功能，为其他模块提供表达式支持

## 注意事项
> 依赖Apache Commons JEXL3库，会自动下载并重定位
> 使用unsafeLazy延迟初始化编译器，避免不必要的资源消耗
> JexlCompiler实例是线程安全的，可以在多个线程间共享
> 文件级注解@Inject确保在TabooLib环境中自动加载
> 重定位规则使用感叹号前缀(!org.apache.commons.jexl3)，这是TabooLib特有的语法
