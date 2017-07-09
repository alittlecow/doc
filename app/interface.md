## app
### 1. 开启设备接口
**接口地址**：http://.../device/openDevice

#### 请求参数
```javascript
{
    "userId":"1",    //用户id
    "deviceId":"00001"  //设备id
}
```
#### 响应参数
```javascript
{
    "result":"success",
    "message":""
}
```

### 2. 关闭设备接口
**接口地址**：http://.../device/closeDevice

#### 请求参数
```javascript
{
    "userId":"1",    //用户id
    "deviceId":"00001"  //设备id
}
```
#### 响应参数
```javascript
{
    "result":"success",
    "message":"",
    "data":{
    	"money":"10.00"//需要支付的费用（元）,
   	 "goodsId":"00001" //当前使用产生的商品id
    }
    
}
```
### 3. 支付订单接口
**接口地址**：http://.../pay/payGoods

#### 请求参数
```javascript
{
    "userId":"1",    //用户id
    "goodsId":"00001"  //支付的商品id
}
```
#### 响应参数
```javascript
{
    "result":"success",
    "message":""
}
```


### 4.个人账户余额查询接口
**接口地址**：http://.../account/queryUserAccount

#### 请求参数
```javascript
{
    "userId":"1"    //用户id
}
```
#### 响应参数
```javascript
{
    "result":"success",
    "message":"",
    "data":{
   	 "money":"10.00"//账户余额（元）
    }
}
```

### 5.个人账户流水查询接口
**接口地址**：http://.../account/queryUserAccountHistory

#### 请求参数
```javascript
{
    "userId":"1"    //用户id,
    "beginTime":"2017-07-07 00:00:00"    //查询开始时间,
    "endTime":"2017-07-07 00:00:00"    //查询结束时间，
    "pageNo":"1",//页码
    "onePageNum":"10"//每页数量
}
```
#### 响应参数
```javascript
{
    "result":"success",
    "message":"",
    "pageNo":"1",//页码
    "pages":"10" //总页数
    "data":[
    {
        "adjustType":"1"//调整类型（10 用户淘宝充值  11用户支付宝充值 1 用户消费 21用户退款 31 分销商结算）,
        "createAt":"2017-07-07 00:00:00"//流水创建时间，
        "adjustMoeny":"500"//调整金额（元）
    },{
   	 "adjustType":"1"//调整类型（10 用户淘宝充值  11用户支付宝充值 1 用户消费 21用户退款 31 分销商结算）,
        "createAt":"2017-07-07 00:00:00"//流水创建时间，
        "adjustMoeny":"500"//调整金额（元）
    }
    ]
}
```

### 6.分销商提现申请接口
**接口地址**：http://.../settlment/applaySettlement

#### 请求参数
```javascript
{
    "userId":"1"    //用户id,
    "moeny":"5000"//分销商申请提现金额（元）
}
```
#### 响应参数
```javascript
{
    "result":"success",
    "message":""
}
```

### 7.分销商提现确认到账接口


**接口地址**：http://.../settlment/confirmSettlement

#### 请求参数
```javascript
{
    "userId":"1"    //用户id,
    "settlementId":"5"//提现单id
}
```
#### 响应参数
```javascript
{
    "result":"success",
    "message":"",
}
```
### 8.分销商提现订单查询接口


**接口地址**：http://.../settlment/querySettlementList

#### 请求参数
```javascript
{
    "userId":"1"，    //用户id
    "status":"5"//提现单状态,
    "startTime":"2017-09-09 00:00:00",
    "endTime":"2017-09-09 00:00:00",
    "pageNo":"1",//页码
	"onePageNum":"10"//每页数量
}
```
#### 响应参数
```javascript
{
    "result":"success",
    "message":"",
    "pageNo":"1",//页码
	"pages":"10" //总页数
    "data":[
    {
        "id":"1",//提现单id
        "status":"5",//结算单状态(分销商申请，总公司确认，总公司打款，分销商收款确认)
        "moeny":"1000",//分销商申请提现金额（元）
        "createAt":"2017-07-07 00:00:00",//创建时间
        "adminConfirmAt":"2017-07-07 00:00:00",//总公司确认时间
        "delearConfirmAt":"2017-07-07 00:00:00",//分销商确认收款时间
    },
    {
        "id":"1",//提现单id
        "status":"5",//结算单状态(分销商申请，总公司确认，总公司打款，分销商收款确认)
        "moeny":"1000",//分销商申请提现金额（元）
        "createAt":"2017-07-07 00:00:00",//创建时间
        "adminConfirmAt":"2017-07-07 00:00:00",//总公司确认时间
        "delearConfirmAt":"2017-07-07 00:00:00",//分销商确认收款时间
    }
    ]
}
```
### 9.用户订单退款申请接口


**接口地址**：http://.../refund/refundOrder

#### 请求参数
```javascript
{
    "userId":"1"，    //用户id
    "orderId":"0003"//订单号,
}
```
#### 响应参数
```javascript
{
    "result":"success",
    "message":""
}
```

### 10.用户订单退款查询接口

**接口地址**：http://.../refund/queryRefundList

#### 请求参数
```javascript
{
    "userId":"1"，    //用户id
    "status":"5"//订单退款状态,
     "startTime":"2017-09-09 00:00:00",
	"endTime":"2017-09-09 00:00:00",
	"pageNo":"1",//页码
	"onePageNum":"10"//每页数量
}
```
#### 响应参数
```javascript
{
    "result":"success",
    "message":"",
	"pageNo":"1",//页码
	"pages":"10" //总页数
    "data":[
    {
        "id":"1",//退款订单号(主键)
        "status":"5",//退款单状态
        "moeny":"1000",//退款单金额（元）
        "applAt":"2017-07-07 00:00:00",//退款申请时间
        "refundAt":"2017-07-07 00:00:00"//退款完成时间
    },
    {
        "id":"1",//退款订单号(主键)
        "status":"5",//退款单状态
        "moeny":"1000",//退款单金额（元）
        "applAt":"2017-07-07 00:00:00",//退款申请时间
        "refundAt":"2017-07-07 00:00:00"//退款完成时间
    }
    ]
}
```

### 11.用户注册接口

**接口地址**：http://119.23.248.130:8080/user/regiestUser

#### 请求参数
```javascript
{
    "userName":"ppp"，    //用户名
    "password":"666666",//密码
    "sex":"1",//性别 (1男性 0女性)
    "birtyday":"1990-00-00",//生日
    "mobile":"13777770000",
    "email":"333@aa.com"//个人邮件
}
```
#### 响应参数
```javascript
{
    "result":"success",
    "message":""
}
```

### 12.用户登陆接口

**接口地址**：http://119.23.248.130:8080/user/regiestUser

#### 请求参数
```javascript
{
    "userName":"ppp"，    //用户名,（选择其一）
    "mobile":"13777770000",（选择其一）
    "password":"666666"//密码
}
```
#### 响应参数
```javascript
{
    "result":"success",
    "message":""
}
```

### 13.个人账户充值接口

**接口地址**：http://119.23.248.130:8080/user/recharge

#### 请求参数
```javascript
{
    "userId":"i"，    //用户id,
    "money":"100" //充值金额（元）
}
```
#### 响应参数
```javascript
{
    "result":"success",
    "message":""
}
```
### 14.设备修改接口
**接口地址**：http://119.23.248.130:8080/device/updateDevice

#### 请求参数
```javascript
{
    "deviceId":"1"，    //设备id,
    "isBreakDwon":"1" //1故障 0在线
}
```
#### 响应参数
```javascript
{
    "result":"success",
    "message":""
}
```
### 14.查询设备历史数据接口
**接口地址**：http://119.23.248.130:8080/device/queryDeviceDataList

#### 请求参数
```javascript
{
    "deviceId":"1"   //设备id,
    "userId":"1",   //用户id,
    "startTime":"2017-08-08 00:00:00",//起始查询时间
    "endTime":"2017-08-08 00:00:00"//结束查询时间，
    "pageNo":"1",//页码
	"onePageNum":"10"//每页数量
}
```
#### 响应参数
```javascript
{
    "result":"success",
    "message":"",
    "pageNo":"1",//页码
	"pages":"10" //总页数
    "data":[
    	{
        "reportTime":"2017-08-08 00:00:00",//上报时间
        "value":"555"//数值
        },
        {
        "reportTime":"2017-08-08 00:00:00",//上报时间
        "value":"555"//数值
        }
        ]
}
```





