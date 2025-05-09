# NMSParticle

## 基本信息
- 类名和包路径: taboolib.module.nms.NMSParticle
- 基本用途: 提供跨版本的粒子效果数据包创建功能
- 类型: 抽象类
- 所属模块: bukkit-nms-stable

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> 无

### 类方法
> createParticlePacket(particle: Particle, location: Location, offset: Vector, speed: Double, count: Int, data: Any?): Any -> 创建粒子效果数据包

## 实现细节
- 使用 `nmsProxy<NMSParticle>()` 创建代理实例，实际实现类为 `NMSParticleImpl`
- 提供扩展函数 `Particle.createPacket()` 简化使用
- 实现类 `NMSParticleImpl` 根据不同的 Minecraft 版本使用不同的方法创建粒子效果数据包
- 支持从 1.8 到 1.21 版本的 Minecraft
- 对于 1.12 以上版本，使用 `ParticleParam` 系统
- 对于 1.21.2 以上版本，使用 `createParticleParam` 方法
- 对于 1.21.1 以下版本，使用 `toNMS` 方法
- 对于 1.12 以下版本，直接使用粒子枚举

## 使用场景
> 在需要创建粒子效果数据包并发送给玩家时使用
> 在需要自定义粒子效果的位置、偏移、速度、数量和数据时使用
> 在插件开发中需要跨版本兼容时使用

## 注意事项
> 不同版本的 Minecraft 对粒子效果的处理方式不同
> 在 1.21.2+ 版本中，使用 `createParticleParam` 方法
> 在 1.13-1.21.1 版本中，使用 `toNMS` 方法
> 在 1.12 及以下版本中，直接使用粒子枚举
> 如果提供了粒子数据，但数据类型与粒子要求的数据类型不匹配，会抛出错误
