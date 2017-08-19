




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
    "password":"666666"//用户密码
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
### 找回密码接口

**接口地址**：http://119.23.248.130:8080/api/app/user/getBackPassword

#### 请求参数
```javascript
{
    "password":"123456h",
    "mobile":"13776540000"  //前端先进行短信校验
}
```
#### 响应参数
```javascript
{
 "code":0,
  "msg":""
}
```


    "code":0,
    "msg":""
}
```
### 用户修改密码接口

**接口地址**：http://119.23.248.130:8080/api/app/user/resetPassword

#### 请求参数
```javascript
{
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
    "username":"ppp"，    //用户名
    "sex":"1",//性别 (1男性 0女性)
    "birthday":"1990-00-00",//生日
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
     "username":"ppp"，    //用户名
    "sex":"1",//性别 (1男性 0女性)
    "birtyday":"1990-00-00",//生日
    "email":"333@aa.com"//个人邮件
    }
}
```



### 消费菜单接口(商品查询接口)
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
###  门店消费订单生成接口
**接口地址**：http://.../api/app/order/consumeorder

#### 请求参数
```javascript
{
    "token":"1" ,  //token
    "deviceId" : "001"
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


###  ID卡充值 订单生成接口
**接口地址**：http://.../api/app/order/cardrecharge

#### 请求参数
```javascript
{
    "goodsId":"3" ,  //商品id
    "code":"0001"//充值卡号
   

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


###  账户充值 订单生成接口
**接口地址**：http://.../api/app/order/accountrecharge

#### 请求参数
```javascript
{
    "goodsId":"2"   //商品id
   

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
    "code": 0,
    "data": {
        "id": "1000002069833279",
        "userId": 17,
        "balance": 800,
        "createTime": "2017-08-16 16:50:03",
        "updateTime": "2017-08-16 18:36:20"
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
        "adjustType": 0,//调整类型（10用户充值  11 分成结算  20 ID卡充值 21 使用设备  22 提现）
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




### ID卡绑定接口

**接口地址**：http://.../api/app/card/bind

#### 请求参数
```javascript
{
	 
   "code" : "001", //卡号码
	"cardHoldName":"pengxiao2", //持卡人姓名
	"cardHoldPhone" : "13776540148" //持卡人姓名
}
```
#### 响应参数
```javascript
{
 	"code":"0",
    "msg":""
}
```


### ID卡详情接口

**接口地址**：http://.../api/app/card/info

#### 请求参数
```javascript
{
 	"token":"1111", //token
    "code":"HH001", //卡号
}
```
#### 响应参数
```javascript
{
    "code":0,
    "data":{
        "id":"db3b8e9e9fca408ba0192583f9a66512",
        "userId":2,
        "code":"SX0072", //卡号
        "count":0, //剩余次数
        "createTime":"2017-07-25 21:56:11",
        "lastUseTime":null
    }
}
```
### ID卡使用记录接口

**接口地址**：http://.../api/app/card/rechargerecord

#### 请求参数
```javascript
{
    "code":"001",
	"startTime":"2017-07-01", //开始时间
	"endTime":"2017-09-01"  //结束时间
     "page":"1",  //页码
    "limit":"1"//每页数量
}
```
#### 响应参数
```javascript
{
  "code": 0,
  "data": {
    "totalCount": 1,
    "limit": 10,
    "totalPage": 1,
    "page": 1,
    "list": [
      {
        "id": "1",
       
        "code": "001",
        "count": 10,
        "type": 1, //1设备使用 2充值 
        "payType": "1", //0支付宝 1微信 2银联 3个人账户
        "createTime": "2017-07-25 22:30:35",
        "adjustCount": null
      }
    ]
  }
}
```
### 银行卡列表

**接口地址**：http://.../userbankcard/list
**根据的登录信息查询分页的银行卡列表
#### 请求参数
```javascript
{
  
    "page":"1",  //页码
    "limit":"1"//每页数量
}
```
#### 响应参数
```javascript
{
  "code": 0,
  "page": {
    "totalCount": 1,
    "limit": 10,
    "totalPage": 1,
    "page": 1,
    "list": [
      {
        "id": "1",
        "status": 2,//状态预留字段
        "userId": "SX002",//用户id
        "bankFullName": "中国银行",//银行全名
        "cardType": 1,//卡类型 DE代表借记卡，CR代表信用卡，其他值为非法
        "accountType": "1",//账户类型 区分对公和对私 P代表私户，C代表公户，其他值为非法
        "accountNo": "2017-07-25 22:30:35",//收款方的银行卡号
        " accountName": null//收款方的姓名或者单位名
      }
    ]
  }
}
```
### 银行卡详情
**接口地址**：http://.../userbankcard/info/{id}
* 展示银行卡详情
#### 请求参数
```javascript
{
 
}
```
#### 响应参数
```javascript
{
  "code": 0,
  "page":
  {
        "id": "1",//银行卡id
        "status": 2,//状态预留字段
        "userId": "SX002",//用户id
        "bankFullName": "中国银行",//银行全名
        "cardType": "CR",//卡类型 DE代表借记卡，CR代表信用卡，其他值为非法
        "accountType": "P",//账户类型 区分对公和对私 P代表私户，C代表公户，其他值为非法
        "accountNo": "20170725223035",//收款方的银行卡号
        "accountName": null//收款方的姓名或者单位名
  }
}
```
### 账户实名认证
**接口地址**：http://.../accountinfo/auth
* 用于账户实名认证
#### 请求参数
```javascript
{
        "idNo": "320113199807141310",//身份证号必填
         "name":"王五",//真实姓名必填
         "cardNo":"1234644",//银行卡号必填
         "mobile":"13950721447"//手机号码选填
}
```
#### 响应参数
```javascript
{
  "code": 0,
}
```

### 提现列表

**接口地址**：http://.../accountenchashment/list
**根据的登录信息查询分页的提现订单列表
#### 请求参数
```javascript
{
  
    "page":"1",  //页码
    "limit":"1"//每页数量
}
```
#### 响应参数
```javascript
{
  "code": 0,
  "page": {
    "totalCount": 1,
    "limit": 10,
    "totalPage": 1,
    "page": 1,
    "list": [
      {
        "id": "1",//提现订单主键
        "status": 1,	//0提现中，1提现成功
        "payAt":"2017-06-09 12:30:59",
        "totalFee":"222",//int类型金额以分为单位的金额
        "userId": "SX002",//用户id
        "bankFullName": "中国银行",//银行全名
        "cardType": "DE",//卡类型 DE代表借记卡，CR代表信用卡，其他值为非法
        "accountType": "1",//账户类型 区分对公和对私 P代表私户，C代表公户，其他值为非法
        "accountNo": "20170725223035",//收款方的银行卡号
        "accountName": null//收款方的姓名或者单位名
        "createAt": null//创建时间
      }
    ]
  }
}
```
### 新建提现订单

**接口地址**：http://.../accountenchashment/save
**根据的登录信息查询分页的提现订单列表
#### 请求参数
```javascript
{
        "totalFee":"222",//int类型金额以分为单位的金额
        "userId": "SX002",//用户id
        "bankFullName": "中国银行",//银行全名
        "cardType": "DE",//卡类型 DE代表借记卡，CR代表信用卡，其他值为非法
        "accountType": "1",//账户类型 区分对公和对私 P代表私户，C代表公户，其他值为非法
        "accountNo": "20170725223035",//收款方的银行卡号
        "accountName": null//收款方的姓名或者单位名
}
```
#### 响应参数
```javascript
{
  "code": 0
}
```





