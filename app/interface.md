


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




### 消费菜单接口（个人账户充值接口）
**接口地址**：http://.../api/app/goods/list

#### 请求参数
```javascript
{
    "type":"1",   //商品类型 1设备使用次数（单位：次 ID卡充值和门店消费时使用）2账户充值（单位：元
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
###  (账户充值  门店消费)订单生成接口
**接口地址**：http://.../api/app/order/create

#### 请求参数
```javascript
{
    "goodsId":"1" ,  //商品id
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

###个人账户余额支付接口
**接口地址**：http://.../api/app/account/pay

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
    "code":0,
    "msg":""
    }
}
```

### 个人账户余额查询接口

**接口地址**：http://.../app/api/account/info

#### 请求参数
```javascript
{
     "token":"1",    //用户token
}
```
#### 响应参数
```javascript
{
    "code":"success",
    "message":"",
    "data":{
   	 "money":"10.00"//账户余额（元）
    }
}
```

### 个人账户流水查询接口
**接口地址**：http://.../api/app/account/history

#### 请求参数
```javascript
{
    "token":"1",    //用户token
    "beginTime":"2017-07-07 00:00:00"    //查询开始时间,
    "endTime":"2017-07-07 00:00:00"    //查询结束时间，
    "page":"1",  //页码
    "limit":"1"//每页数量
}
```
#### 响应参数
```javascript
{
  "code": 0,
  "data": {
    "totalCount": 2,
    "limit": 10,
    "totalPage": 1,
    "page": 1,
    "list": [
      {
        "id": "75c25b2e50eb4b42b3575d104142e39e",
        "accountId": "2",
        "beforeAdjustMoney": 9748.85,
        "adjustMoney": -50.23,
        "afterAdjustMoney": 9698.62,
        "adjustType": 0,//调整类型（0用户充值  1用户消费  2分成结算 3提现）
        "createTime": "2017-07-15 00:21:02",
        "orderId": "bb8e5a91dd3c4ffbbb16325d309d5c8c"
      },
      {
        "id": "1f80b02a114044bfa1f2f114c9366905",
        "accountId": "2",
        "beforeAdjustMoney": 9799.08,
        "adjustMoney": -50.23,
        "afterAdjustMoney": 9748.85,
        "adjustType": 0,
        "createTime": "2017-07-15 00:19:36",
        "orderId": "bb8e5a91dd3c4ffbbb16325d309d5c8c"
      }
    ]
  }
}

```

### 用户注册接口

**接口地址**：http://119.23.248.130:8080/api/app/user/register

#### 请求参数
```javascript
{
    "mobile":"13777770000",
   "password":"a123456",
    "verifyCode":"666666"//手机验证码(前端验证先不不用填写)
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
    "passowrd":"666666"//用户密码
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
    "token":"1111",
}
```
#### 响应参数
```javascript
{
    "code": 0,
    "msg":"",
    "data":{
     "userName":"ppp"，    //用户名
    "sex":"1",//性别 (1男性 0女性)
    "birtyday":"1990-00-00",//生日
    "email":"333@aa.com"//个人邮件
    }
}
```









