# RemoteQuest

## 基本信息
- 类名和包路径: taboolib.module.kether.RemoteQuest
- 基本用途: Kether脚本引擎的远程脚本封装类，实现跨插件/容器访问Quest对象
- 类型: 类及内部类
- 所属模块: kether

## 类结构
### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> remote: OpenContainer -> 远程容器实例，用于进行跨容器通信
> source: Any -> 远程Quest对象的原始引用

### 类方法
> getId(): String -> 获取脚本的唯一标识符
> getBlock(label: String): Optional<Quest.Block> -> 根据标签获取特定的脚本块
> getBlocks(): Map<String, Quest.Block> -> 获取脚本中所有的块
> blockOf(action: ParsedAction<*>): Optional<Quest.Block> -> 查找包含特定动作的块

## 实现细节
- RemoteQuest实现了Quest接口，封装了对远程Quest对象的操作
- 所有方法通过反射调用远程源对象的对应方法(invokeMethod)
- 内部类RemoteBlock实现了Quest.Block接口，封装远程Block对象
- 远程方法调用时使用remap=false，避免字段名映射带来的问题
- 创建ParsedAction时使用StandardChannel.REMOTE_CREATE_PARSED_ACTION通道
- 使用当前插件ID(pluginId)作为来源标识
- 对远程返回的对象进行适当包装，如将远程Block包装为RemoteBlock

## 使用场景
> 跨插件访问和操作Kether脚本
> 在不同ClassLoader环境下共享脚本对象
> 实现模块化的脚本系统，一个插件可以使用其他插件的脚本
> 与RemoteQuestAction配合，构建完整的远程脚本执行系统

## 注意事项
> 大量使用反射调用，可能存在性能开销
> 依赖远程容器的可用性，如果远程容器不可用则操作失败
> 使用getProperty和invokeMethod进行反射操作，需要确保远程对象结构稳定
> 内部类RemoteBlock的所有方法也使用反射实现，同样存在上述问题
> 复杂对象(如ParsedAction)需要特殊处理，确保跨容器正确传递
