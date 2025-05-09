# NoteBlockMusic

## 基本信息
- 类名和包路径: taboolib.library.xseries.NoteBlockMusic
- 基本用途: 为 Minecraft 编写音乐脚本，无需使用红石或建筑物来制作音乐
- 类型: 工具类
- 所属模块: platform-bukkit-impl

## 类结构

### 公开静态字段
> INSTRUMENTS: Map<String, Instrument> -> 乐器快捷方式列表，包含完整名称的缓存
> INSTRUMENT_TO_SOUND: Map<Instrument, XSound> -> 乐器到 XSound 的映射

### 公开静态方法
> getSoundFromInstrument(instrument: Instrument): XSound -> 从乐器获取对应的 XSound
> getNoteTone(ch: char): Note.Tone -> 从字符获取音符音调
> testMusic(player: Player): CompletableFuture<Void> -> 播放预先编写的测试音乐脚本
> fromFile(player: Player, location: Supplier<Location>, path: Path): CompletableFuture<Void> -> 从文件播放音乐
> playMusic(player: Player, location: Supplier<Location>, script: String): CompletableFuture<Void> -> 播放音乐脚本
> parseInstructions(script: CharSequence): Sequence -> 解析指令序列
> parseNote(note: String): Note -> 解析 Minecraft Note 及其 Tone
> noteToPitch(note: Note): float -> 将音符转换为音高
> playAscendingNote(plugin: Plugin, player: Player, playTo: Entity, instrument: Instrument, ascendLevel: int, delay: int): BukkitTask -> 以升序形式播放乐器音符

### 类内可被访问字段
> 无公开实例字段（类为 final 且构造函数为私有）

### 类方法
> 私有构造函数 NoteBlockMusic() -> 防止实例化
> sleep(fermata: long): void -> 处理指令延迟的方法
> isDigit(ch: char): boolean -> 检查字符是否为英文数字

## 实现细节
- 使用 CompletableFuture 异步处理音乐脚本，避免阻塞主线程
- 支持复杂的音乐脚本格式，包括乐器、音调、重复次数和延迟
- 提供了音符解析功能，支持自然音、升音和降音
- 包含内部类 InstructionBuilder 用于解析音乐脚本
- 包含内部类 Sound 和 Sequence 用于表示音乐指令
- 包含内部类 Instruction 作为音乐指令的抽象基类

## 使用场景
> 在 Minecraft 中创建自定义音乐，无需使用红石或音符盒
> 通过简单的文本脚本创建复杂的音乐序列
> 为玩家提供交互式音乐体验

## 注意事项
> 音乐脚本应在异步线程中处理，避免阻塞主线程
> 不要在脚本处理过程中使用阻塞方法如 join() 或 get()
> 音乐脚本格式需要遵循特定语法，包括乐器、音调、重复和延迟
