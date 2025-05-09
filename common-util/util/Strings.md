# Strings
## 基本信息
- 类名和包路径: taboolib.common.util.Strings
- 基本用途: 提供字符串处理和比较的实用工具方法
- 类型: 工具类
- 所属模块: common-util

## 类结构
### 公开静态方法
> similarDegree(strA: String, strB: String): double -> 计算两段文本的相似度，返回值范围为 0.0~1.0

### 类内可被访问字段
> 无公开字段

### 类方法
> bytesToHexString(bytes: byte[]): String -> 将字节数组转换为十六进制字符串表示
> max(strA: String, strB: String): String -> 返回两个字符串中长度较大的那个
> min(strA: String, strB: String): String -> 返回两个字符串中长度较小的那个
> removeSign(str: String): String -> 移除字符串中的非字母、非数字、非汉字字符
> charReg(charValue: char): boolean -> 判断字符是否为字母、数字或汉字
> longestCommonSubstring(strA: String, strB: String): String -> 计算两个字符串的最长公共子序列

## 实现细节
- `similarDegree` 方法通过计算两个字符串的最长公共子序列长度与较长字符串长度的比值来衡量相似度
- 在计算相似度前，会先移除字符串中的特殊字符，只保留字母、数字和汉字
- 使用动态规划算法实现最长公共子序列的计算
- 提供了字节数组到十六进制字符串的转换功能，但当前在公开方法中未使用

## 使用场景
> 需要比较两段文本相似程度时，如模糊搜索、文本匹配等
> 在自然语言处理中评估文本的相似性
> 在搜索引擎或推荐系统中用于计算文本相似度

## 注意事项
> `similarDegree` 方法在计算过程中可能抛出异常，但会捕获并返回 0
> 相似度计算会忽略所有非字母、非数字、非汉字的字符
> 汉字范围定义为 0x4E00 到 0x9FA5
> `bytesToHexString` 方法虽然实现了但未在公开方法中使用，可能是为了未来扩展或其他模块使用