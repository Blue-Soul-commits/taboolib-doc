# XSound
## 基本信息
- 类名和包路径: taboolib.library.xseries.XSound
- 基本用途: 提供跨Minecraft版本的声音支持，解决不同版本声音ID变化的兼容性问题
- 类型: 枚举类
- 所属模块: platform-bukkit-impl

## 类结构
### 公开静态字段
> REGISTRY: XRegistry<XSound, Sound> -> 声音注册表，用于管理XSound与Bukkit Sound的映射关系
> MUSIC: Set<XSound> -> 包含所有被标记为"音乐"的声音集合
> DEFAULT_VOLUME: float -> 默认音量值(1.0f)
> DEFAULT_PITCH: float -> 默认音调值(1.0f)
> NAMESPACED_SOUND_PATTERN: Pattern -> 用于验证命名空间声音格式的正则表达式
> RECORD_PATTERN: Pattern -> 用于解析声音记录字符串的正则表达式

### 公开静态方法
> of(Sound bukkit): XSound -> 通过Bukkit Sound对象获取对应的XSound
> of(String bukkit): Optional<XSound> -> 通过声音名称获取对应的XSound
> getValues(): Collection<XSound> -> 获取所有XSound值的集合
> parse(String sound): Record -> 从字符串解析声音配置
> play(String sound, Consumer<SoundPlayer> soundPlayer): Record -> 便捷方法，解析并播放声音
> stopMusic(Player player): void -> 停止播放给定玩家的所有音乐

### 类内可被访问字段
> 无特殊字段，主要是继承自XModule的字段

### 类方法
> stopSound(Player player): void -> 停止为指定玩家播放此声音
> play(Entity entity): void -> 为实体播放声音
> play(Location location): void -> 在指定位置播放声音
> play(Entity entity, float volume, float pitch): void -> 为实体播放指定音量和音调的声音
> play(Location location, float volume, float pitch): void -> 在指定位置播放指定音量和音调的声音
> record(): Record -> 创建此声音的Record对象

## 实现细节
- 使用XRegistry系统管理声音映射，支持跨版本兼容
- 通过注解(@XChange, @XMerge, @XInfo)标记声音的版本变更信息
- 提供SoundPlayer和Record内部类处理声音播放的细节
- 支持三种播放方法级别(SUPPORTED_METHOD_LEVEL)，根据服务器版本自动选择
- 支持从字符串配置解析声音，格式为"[~]Sound@Category, [Volume], [Pitch]"

## 使用场景
> 在插件中播放声音，无需担心Minecraft版本差异
> 从配置文件中加载声音设置
> 为特定玩家或位置播放声音
> 控制声音的音量、音调和播放范围

## 注意事项
> 音量范围: 0.0-∞，1.0为正常音量，大于1.0的值会增加声音可被听到的距离
> 音调范围: 0.5-2.0，1.0为正常音调，影响声音播放速度
> 线程安全，但不建议在异步任务中频繁调用Player#playSound

