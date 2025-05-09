# TabooLibLegacyStyleCommandHelper

## 基本信息
- 类名和包路径: top.maplex.arim.tools.commandhelper.TabooLibLegacyStyleCommandHelper
- 基本用途: 为TabooLib命令系统提供传统风格的命令帮助系统
- 类型: 工具类
- 所属模块: Arim命令工具模块

## 类结构
### 公开静态字段
> BRACES: VariableReader -> 花括号变量读取器 { }
> DOUBLE_BRACES: VariableReader -> 双花括号变量读取器 {{ }}
> PERCENT: VariableReader -> 百分号变量读取器 % %
> AREA_START: Regex -> 区域开始标记正则表达式
> AREA_END: Regex -> 区域结束标记正则表达式

### 公开静态方法
> createTabooLegacyStyleCommandHelper(commandType: String = "main", main: Boolean = commandType == "main"): Unit -> 为命令组件创建传统风格的帮助系统
> variables(reader: VariableReader = VariableReaders.BRACES, func: VariableFunction): List<String> -> 处理变量替换
> variable(key: String, value: Collection<String>, reader: VariableReader = VariableReaders.BRACES): List<String> -> 替换指定键的变量

### 类内可访问字段
> VariableFunction: interface -> 变量转换函数接口

## 实现细节
- 使用TabooLib的命令系统扩展功能
- 支持多语言系统
- 实现了变量替换和嵌套变量处理
- 提供完整的命令错误处理机制

## 使用场景
> 需要为插件添加命令帮助系统时
> 需要处理命令参数错误提示时
> 需要自定义命令帮助信息格式时

## 注意事项
> 需要配置对应的语言文件
> 命令帮助系统依赖于TabooLib的命令系统
> 变量替换系统支持嵌套变量

## 使用实例
> 创建命令帮助系统
```kotlin
command("example") {
    createTabooLegacyStyleCommandHelper()
    
    literal("test1") {
        execute<ProxyCommandSender> { sender, _, _ ->
            // 命令逻辑
        }
    }
}
```

> 配置语言文件
```yaml
command-helper:
  - '&7'
  - '  &f&l{pluginId} &7v{pluginVersion}'
  - '&7'
  - '  &7命令: &f/{command} &8\[...\]'
  - '  &7参数:'
  - '{subCommands}'
  - '&7'

command-sub:
  - '    &8- [&f{name}](h=/{command} {name} {usage}&8- &7{description};suggest=/{command} {name})'
  - '      &7{description}'
```
