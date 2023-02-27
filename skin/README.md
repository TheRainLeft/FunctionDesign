### 一、简单说明
    
````    
   （一）三种解锁方式：
   
    1、背包道具解锁，走背包道具的使用模块解锁，框架内实现道具使用MFA
    
    2、达到指定等级解锁皮肤，走奖励系统，框架内实现奖励系统发奖MFA
    
    3、功能解锁：例如玩家成为军团长或者某对应职位解锁相应皮肤，采取抛事件的方式，有对应解锁皮肤需求的功能抛事件

````
````
    (二）接口实现：
    
    1、对应解锁功能方法
    
    2、客户端获取皮肤信息
    
    3、更换穿戴皮肤
    
    4、皮肤升星
    
    5、buff叠加
    
    6、获取属性
````

### 二、配置
1. 在`skin_info`中配置相关的皮肤

   ```erlang
   %% 皮肤配置
   %% {skin_info, 皮肤Id, 皮肤类型, 时效时间}
   %% 时效时间 0-永久，MFA为对用功能解锁时效
   {[gateway], zm_config,
    [skin_info,
   	 [
   		 {skin_info, 65001, castle, 0},
   		 {skin_info, 65002, chat, 86400},
   		 {skin_info, 65003, march, {M, F, A}}
   	 ], keypos2
    ]
   }.
   ```

1. 在`skin_action`中配置相关的皮肤
   ```erlang
   %% {skin_action, 皮肤类型MA, 获取MA, 解锁MA，升星MA，皮肤穿戴MA，获取属性MA}
   {[gateway], zm_config,
    [skin_action,
   	 [
   		 {skin_action, castle, {skin_common, []}, {skin_common, []}, {skin_common, []}, {skin_common, []}, {skin_common, []}},
   		 {skin_action, chat, {skin_common, []}, {skin_common, []}, {skin_common, []}, {skin_common, []}, {skin_common, []}},
   		 {skin_action, march, {skin_common, []}, {skin_common, []}, {skin_common, []}, {skin_common, []}, {skin_common, []}}
   	 ], keypos2
    ]
   }.
   ```