# SharedCoolingAbility
- 知乎链接:https://zhuanlan.zhihu.com/p/32216887423/edit
- 案例链接:https://github.com/hbdjzwl/SharedCoolingTest  (插件支持4.27~5.5,Demo是5.5的版本)

在常规游戏中共享CD还是会经常会使用到的。比如魔兽世界的技能会有一个1秒的公共CD，某些游戏的同类药品、特殊道具再使用后会进入一个公共CD。一些MOBA或者RTS游戏也会遇见。

![Cooling_0](https://github.com/hbdjzwl/ImageLibrary/blob/main/SharedCoolingAbilityImage/Cooling_0.png)

SharedCoolingAbility是一款简洁式开箱即用支持单机、联机的共享冷却插件，不需要你写一行代码，也不会耦合你的项目代码，只需要在自己的AbilitySystemComponent类继承一个接口和继承自共享冷却Ability即可实现公共CD。不管你是项目使用还是插件使用都非常的便捷。

![Cooling_1](https://github.com/hbdjzwl/ImageLibrary/blob/main/SharedCoolingAbilityImage/Cooling_1.png)

## 配置起来也极为方便

- 左图: 只需要在对应的GA类中配置相同的Tag与自定义时间
- 右图: 如果需要UI监听冷却的回调则使用下图右侧的两个Tag事件

![Cooling_4](https://github.com/hbdjzwl/ImageLibrary/blob/main/SharedCoolingAbilityImage/Cooling_4.png)



## 插件使用方法
### 1.打开插件
![Cooling_5](https://raw.githubusercontent.com/hbdjzwl/ImageLibrary/refs/heads/main/SharedCoolingAbilityImage/Cooling_5%20.png?token=GHSAT0AAAAAAC6P4UIWDD5FSVF3UB2RZF3EZ7YTUMQ)

### 2.继承接口
- 方法一：直接使用插件里UASC_SharedCoolingComponent。
- 方法二：自定义AbilitySystemComponent然后继承自ISharedCoolingnterface。
  
![Cooling_6](https://github.com/hbdjzwl/ImageLibrary/blob/main/SharedCoolingAbilityImage/Cooling_6.png)

> 如果你的项目已经用了AbilitySystemComponent，那么直接将你的AbilitySystemComponent继承自ISharedCoolingInterface即可。
如果你要在自己的项目中使用ISharedCoolingInterface，要记得添加插件的模块，步骤4会讲到。

### 3.创建GA
创建继承自GA_SharedCoolingBase的类都可以使用共享CD的功能。

![Cooling_7](https://github.com/hbdjzwl/ImageLibrary/blob/main/SharedCoolingAbilityImage/Cooling_7.png)

### 5.配置GA的冷却Tag

![Cooling_8](https://github.com/hbdjzwl/ImageLibrary/blob/main/SharedCoolingAbilityImage/Cooling_8.png)

#### 参数讲解:
- bEnableSharedCooling ：配置共享冷却参数的开关。
- SharedCoolingTime : 是一个Map数组，Key是冷却的Tag，Value是共享冷却的时间。 【提问: 上图中A和B的时间不同是为什么】
当GA_Shared_A激活时诱发的CD.SharedCooling.1会让其他拥有同Tag的GA进入10秒的冷却。
当GA_Shared_B激活时诱发的CD.SharedCooling.1会让其他拥有同Tag的GA进入20秒的冷却。
虽然是相同的Tag，但是不同的GA激活时候诱发CD的持续时间却不同。
- bSelfActivateDontSharedCoolDefaultConfig : 如果为true,当前激活GA的技能是不会被共享CD限制，其他拥有这个Tag的GA会进入冷却。（通俗来讲就是约束别人，不约束自己。）
- EventNotifyPlicy: 事件通知策略，当CD开始或结束时发起一个Event，可以是只通知客户端、或只通知服务端、也可以是双端都通知。（比如客户端接收到CD的通知，更新UI层面的表示）
  ![Cooling_3](https://github.com/hbdjzwl/ImageLibrary/blob/main/SharedCoolingAbilityImage/Cooling_3.png)
