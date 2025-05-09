# PlayerScoreboard

## 基本信息
- 类名和包路径: taboolib.module.nms.type.PlayerScoreboard
- 基本用途: 管理玩家记分板信息的缓存和操作
- 类型: 类
- 所属模块: bukkit-nms-stable

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> nmsScoreboard: NMSScoreboard -> 记分板工具，通过 nmsProxy 获取
> currentTitle: String -> 当前记分板标题
> currentContent: HashMap<Int, String> -> 当前记分板内容，键为行号，值为内容
> prefix: String -> 当前前缀
> suffix: String -> 当前后缀
> color: ChatColorFormat -> 当前队伍颜色
> isDeleted: Boolean -> 记分板是否被删除
> isCreated: Boolean -> 队伍是否被创建

### 类方法
> sendTitle(title: String): Unit -> 设置记分板标题
> sendContent(lines: List<String>): Unit -> 设置记分板内容
> setPrefix(prefix: String, target: Player?): Unit -> 设置前缀
> clearPrefix(target: Player?): Unit -> 清空前缀
> setSuffix(suffix: String, target: Player?): Unit -> 设置后缀
> clearSuffix(target: Player?): Unit -> 清空后缀
> setColor(color: ChatColorFormat, target: Player?): Unit -> 设置颜色

## 实现细节
- 使用 `nmsProxy<NMSScoreboard>()` 获取 NMS 记分板操作接口的实现
- 在初始化时自动设置记分板，展示记分板，并设置初始标题
- 维护记分板的状态信息，包括标题、内容、前缀、后缀和颜色
- 通过比较当前值和新值来避免不必要的更新
- 当记分板被删除时，会在下次设置内容时重新创建

## 使用场景
> 在玩家加入服务器时创建和管理记分板
> 通过扩展函数 `Player.sendScoreboard()` 间接使用
> 设置玩家名称前缀和后缀
> 设置队伍颜色

## 注意事项
> `target` 参数表示接收数据包的玩家，为 null 时向所有玩家发送
> `isCreated` 和 `isDeleted` 标志用于跟踪记分板的状态
> 在调用 `updateTeam` 方法时，使用 `!isCreated` 作为 `createTeam` 参数，确保首次调用时创建队伍
> 记分板内容的更新会清除并重新填充 `currentContent` 映射
