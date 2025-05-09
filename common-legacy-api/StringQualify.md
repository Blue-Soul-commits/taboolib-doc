# 文本效果工具函数
## 基本信息
- 类名和包路径: taboolib.common5.util (Kotlin 扩展函数和工具函数)
- 基本用途: 提供文本特效和进度条生成功能
- 类型: 扩展函数和工具函数
- 所属模块: common5-legacy-api

## 类结构
### 公开静态方法
> String.printed(separator: String = ""): List<String> -> 将字符串转换为打印机特效序列
> createBar(empty: String, fill: String, length: Int, percent: Double): String -> 生成百分比进度条

## 实现细节
- String.printed 函数:
  - 逐字符处理输入字符串，跳过 Minecraft 颜色代码 (§)
  - 生成一系列逐渐增长的字符串，模拟打字机效果
  - 可选择在奇数位置添加分隔符，增强视觉效果
  - 如果提供了分隔符且字符串长度为偶数，会在最后添加完整字符串

- createBar 函数:
  - 使用 Kotlin 的区间和 joinToString 创建指定长度的字符串
  - 根据百分比值决定使用填充字符还是空字符
  - 处理特殊情况如 NaN 或 0 百分比
  - 通过比较当前位置与总长度的比例来确定填充状态

## 使用场景
> 游戏中的文字动画效果，如对话框文字逐字显示
> 聊天消息的特殊显示效果
> 显示加载进度、血量条、经验条等进度指示器
> 命令行界面中的进度显示
> 游戏UI中的各种进度条元素

## 注意事项
> printed 函数会跳过 Minecraft 颜色代码 (§)，保持颜色代码的完整性
> printed 函数的分隔符参数可用于创建闪烁或其他特殊效果
> createBar 函数在百分比为 NaN 或 0 时会返回全空字符
> 进度条长度应适中，过长可能影响显示效果和性能
