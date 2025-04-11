# SharedCoolingAbility
知乎链接:https://zhuanlan.zhihu.com/p/32216887423/edit

在常规游戏中共享CD还是会经常会使用到的。比如魔兽世界的技能会有一个1秒的公共CD，某些游戏的同类药品、特殊道具再使用后会进入一个公共CD。一些MOBA或者RTS游戏也会遇见。

![Cooling_0](https://github.com/hbdjzwl/ImageLibrary/blob/main/SharedCoolingAbilityImage/Cooling_0.png)

SharedCoolingAbility是一款简洁式开箱即用支持单机、联机的共享冷却插件，不需要你写一行代码，也不会耦合你的项目代码，只需要在自己的AbilitySystemComponent类继承一个接口和继承自共享冷却Ability即可实现公共CD。不管你是项目使用还是插件使用都非常的便捷。

![Cooling_1](https://github.com/hbdjzwl/ImageLibrary/blob/main/SharedCoolingAbilityImage/Cooling_1.png)

## 使用起来也极为方便

- 左图: 只需要在对应的GA类中配置相同的Tag与自定义时间
- 右图: 如果需要UI监听冷却的回调则使用下图右侧的两个Tag事件

![Cooling_4](https://github.com/hbdjzwl/ImageLibrary/blob/main/SharedCoolingAbilityImage/Cooling_4.png)
