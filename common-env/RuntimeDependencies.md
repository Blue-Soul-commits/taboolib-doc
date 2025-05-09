# RuntimeDependencies  
## 基本信息  
- 类名和包路径: taboolib.common.env.RuntimeDependencies  
- 基本用途: 用于在类上声明多个RuntimeDependency注解  
- 类型: 注解  
- 所属模块: common-env  
---
## 类结构  
### 公开静态方法  
> value(): RuntimeDependency[] -> 获取RuntimeDependency注解数组  
---
## 实现细节  
- 目标为ElementType.TYPE，即可以应用于类、接口、枚举等类型  
- 保留策略为RetentionPolicy.RUNTIME，即在运行时可通过反射获取  
---
## 使用场景  
> 当需要声明多个运行时依赖时使用  
---
## 注意事项  
> 此注解是容器注解，自动用于处理多个@RuntimeDependency注解