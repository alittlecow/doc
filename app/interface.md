


## app
- [用户注册接口](#用户注册接口)
- [用户登陆接口](#用户登陆接口)
- [用户登出接口](#用户登出接口)
- [设备修改接口](#设备修改接口)
- [开启设备接口](#开启设备接口)
- [关闭设备接口](#关闭设备接口)
- [查询设备历史数据接口](#查询设备历史数据接口)
- [订单生成接口](#订单生成接口)
- [个人账户余额查询接口](#个人账户余额查询接口)
- [个人账户余额支付接口](#个人账户余额支付接口)
- [个人账户流水查询接口](#个人账户流水查询接口)
- [个人账户充值接口](#个人账户充值接口)
- [用户订单退款申请接口](#用户订单退款申请接口)
- [用户订单退款查询接口](#用户订单退款查询接口)
- [分销商提现申请接口](#分销商提现申请接口)
- [分销商提现确认到账接口](#分销商提现确认到账接口)
- [分销商提现订单查询接口](#分销商提现订单查询接口)


###  订单生成接口
**接口地址**：http://.../api/app/order/create

#### 请求参数
```javascript
{
    "goodsId":"1"   //商品id
}
```
#### 响应参数
```javascript
{
    {
  "code": 0,
  "data": {
    "orderId": "a9b1ae11cd544501a9505a0fa7ed1ab0"
  }
}
}
```

### 消费菜单接口
**接口地址**：http://.../api/app/goods/list

#### 请求参数
```javascript
{
    "type":"1",   //商品类型 1设备使用次数（单位：次）2账户充值（单位：元
    "page":"1",  //页码
    "limit":"1"//每页数量

}
```
#### 响应参数
```javascript
{
    "code": 0,
         "data": {
        "totalCount": 2,  //总数量
        "limit": 1,			//每页数量
        "totalPage": 2,  //总页数
        "page": 2,   //当前页码
        "list": [
          {
            "id": "38fea234d4a74742a37a1bfd2e2d99a6",
            "name": "10次 50元",
            "type": 1,
            "value": 10,
            "money": 50
          }
        ]
  }
}
```


###账户充值接口
**接口地址**：http://.../account/recharge
>
#### 请求参数
```javascript
{
    "token":"1",    //用户token
    "money":"10"  //充值金额（元）
}
```
#### 响应参数
```javascript
{
    "result":"success",
    "message":"" ,
    "data":{
    	"orderId":"00002" //返回的订单id
    }
}
```
###个人账户余额支付接口
**接口地址**：http://.../account/pay

#### 请求参数
```javascript
{
    "orderId":"1"    //订单id,
     "token":"1",    //用户token

}
```
#### 响应参数
```javascript
{
    "result":"success",
    "message":""
    }
}
```

### 个人账户余额查询接口

**接口地址**：http://.../account/queryUserAccount

#### 请求参数
```javascript
{
     "token":"1",    //用户token
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

### 个人账户流水查询接口
**接口地址**：http://.../account/queryUserAccountHistory

#### 请求参数
```javascript
{
    "token":"1",    //用户token
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
        "adjustType":"1"//调整类型（0用户充值  1用户消费  2分成结算）,
        "createAt":"2017-07-07 00:00:00"//流水创建时间，
        "adjustMoeny":"500"//调整金额（元）
    },{
   	 "adjustType":"1"//调整类型（0用户充值  1用户消费  2分成结算）,
        "createAt":"2017-07-07 00:00:00"//流水创建时间，
        "adjustMoeny":"500"//调整金额（元）
    }
    ]
}
```

### 分销商提现申请接口
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

### 分销商提现确认到账接口


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
### 分销商提现订单查询接口


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

###用户个人信息修改接口
**接口地址**：http://119.23.248.130:8080/api/app/user/update

#### 请求参数
```javascript
{
	"token":"1111"，  
    "userName":"ppp"，    //用户名
    "sex":"1",//性别 (1男性 0女性)
    "birtyday":"1990-00-00",//生日
    "email":"333@aa.com"//个人邮件
}
```
#### 响应参数
```javascript
{
    "code": 0,
    "msg":""
}
```
###用户个人信息查询接口
**接口地址**：http://119.23.248.130:8080/api/app/user/info

#### 请求参数
```javascript
{
    "token":"1111"，  
}
```
#### 响应参数
```javascript
{
    "code": 0,
    "msg":""
}
```

### 用户注册接口

**接口地址**：http://119.23.248.130:8080/api/app/user/register

#### 请求参数
```javascript
{
    "mobile":"13777770000",
   "password":"a123456",
    "verifyCode":"666666"//手机验证码
}
```
#### 响应参数
```javascript
{
    "code":"0",//0表示成功
    "msg":""
}
```

### 用户登陆接口

**接口地址**：http://119.23.248.130:8080/api/app/user/login

#### 请求参数
```javascript
{
    "mobile":"13777770000",
    "passowrd":"666666"//手机验证码
}
```
#### 响应参数
```javascript
{
   "code": 0,
  "expire": 43200,//失效时间
  "token": "f46501e02921cff81ec8bffcf5e22af0"
}
```

### 用户修改密码接口

**接口地址**：http://119.23.248.130:8080/api/app/user/resetPassword

#### 请求参数
```javascript
{
    "mobile":"13777770000",
    "password":"123456h",
    "newPassword":"1sfsdf"
}
```
#### 响应参数
```javascript
{
 "code":0,
  "msg":""
}
```
### 用户登出接口

**接口地址**：http://119.23.248.130:8080/api/app/user/logout

#### 请求参数
```javascript
{
    "token":"1"
}
```
#### 响应参数
```javascript
{
    "code":0,
    "msg":""
}
```


### 个人账户充值接口

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
### 15.设备修改接口
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
### 查询设备历史数据接口
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





