#### 个人账户充值流程

```
APP充值请求-->生成待支付订单 -->返回待支付订单ID

```

####个人账户支付流程
```
APP请求支付订单-->检查订单状态-->检查账户余额-->账户扣款-->记录用户账户历史-->更改订单状态-->记录总账户流水
```


####支付订单处理流程
```
APP根据orderId向beecloud发起请求-->检查支付状态（成功）-->记录总账户流水-->
```
```
设备按时间使用类型: 修改订单表-->开启设备（时间如何控制？）-->分销商账户充值-->记录分销商账户流水
```
```
ID卡使用类型: 修改订单表-->根据goods增加相应次数
```
```
账户充值类型: 修改订单表-->个人账户充值-->记录用户账户历史
```


支付成功回调
1.修改订单表状态 2.业务逻辑（todo）
即时结算：
id卡充值和设备使用订单：
2.1.计算门店和分销商的分成金额，修改个人账户，记录个人账户流水
个人账户充值订单
：修改个人账户，记录个人账户流水

分销商/门店管理员 提现
新增：（目前不开放给普通用户）
1.个人银行卡绑定接口
2.个人银行卡列表查询接口
3.提现业务接口（提现的手续费用由用户自己承担） 修改个人账户，记录流水
4.提现回调接口（修改提现表状态）






