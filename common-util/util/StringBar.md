# StringBar

## 基本信息
- 类名和包路径: taboolib.common.util.StringBar
- 基本用途: 提供进度条生成工具
- 类型: Kotlin工具函数文件
- 所属模块: common-util

## 函数
> buildStringBarWith(template: String, value: Double, length: Int, reverse: Boolean, builder: (index: Int, code: String) -> String): String -> 基于模板构建自定义进度条
> buildStringBar(value: Double, length: Int, reverse: Boolean, builder: (index: Int, state: Boolean) -> String): String -> 构建基础进度条
> parseTemplate(template: String): Triple<String, String, String> -> 解析进度条模板

## 实现细节
### buildStringBarWith
- 接收模板字符串，格式为"prefix(body)suffix"
- 使用`parseTemplate`函数解析模板
- 调用`buildStringBar`构建进度条
- 根据索引位置决定使用前缀、主体或后缀字符
- 支持自定义构建函数进一步处理每个字符

### buildStringBar
- 核心进度条生成函数
- 支持正向或反向构建进度条
- 使用`joinToString`连接所有字符
- 根据当前索引和进度值决定每个位置是否填充
- 通过builder函数允许完全自定义每个位置的字符

### parseTemplate
- 解析模板字符串为三部分：前缀、主体和后缀
- 使用`split`函数按"("和")"分割字符串
- 验证模板格式是否正确
- 返回包含三个部分的Triple对象

## 使用场景
> 显示下载或上传进度
> 游戏中的血条、能量条等UI元素
> 命令行工具中的进度指示
> 自定义进度显示格式
> 需要特殊样式或颜色的进度条

## 注意事项
> 模板必须遵循"prefix(body)suffix"格式
> value参数应在0.0到1.0之间，表示进度百分比
> length参数决定进度条的总长度
> reverse参数控制进度条的填充方向
> 当value为0时，所有位置都不填充
