
#### 用户接口
1.[用户注册接口](#用户注册接口)
2.[找回密码接口](#找回密码接口)


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

###用户登陆接口

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
  "cardNum": 1, //id卡数量
  "code": 0,
  "role": 6, //角色id
  "balance": 800, //账户余额
  "expire": 2592000,
  "token": "ed5dbd8f222e6a9cd9d069936ce3a332"
}
```

###用户登出接口

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
###找回密码接口

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
### 用户实名认证接口   
####请求参数
**接口地址** : http://localhost:8081/api/app/user/auth
```
{
	"realName":"彭逍",
	"idCard":"511323199009091176"
}
```
####响应参数
```
{
  "code":0,
  "msg":""
}
```
### 免费体验接口   
####请求参数
**接口地址** : http://localhost:8081/api/app/order/freeuse
```
{
	"code":"10003b"  //设备编码  体验前需要先实名认证
}
```
####响应参数
```
{
    "msg": "免费体验次数已经用完",
    "code": 500
}
```
### 消费菜单接口(商品查询接口)
**接口地址**：http://.../api/app/goods/list

#### 请求参数
```javascript
{
  "type":"1",   //商品类型 1设备使用次数（单位：次 ID卡充值和门店消费时使用）2账户充值（单位：元)  3设备押金
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
        "money": 50      //价格
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
  "deviceId" : "001"  //设备需要存在     
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
  "code": 0,
  "data": {
    "orderId": "a9b1ae11cd544501a9505a0fa7ed1ab0"
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

###  押金缴纳 订单生成接口
**接口地址**：http://localhost:8081/api/app/order/deposit

#### 请求参数
```javascript
{
	"num":10   //缴纳数量
}
```
#### 响应参数
```javascript
{
    "code": 0,
    "data": {
        "orderId": "120170829164357000001"
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
    "id": "1000002069833279",  //账户id
    "userId": 17,
    "balance": 800,   //余额
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
        "id": "1000001428748560",
        "accountId": "1000002069833279",
        "beforeAdjustMoney": 1000,
        "adjustMoney": -100,
        "afterAdjustMoney": 900,
        "adjustType": 1,  //调整类型  用户充值 10 分成结算 11  ID卡充值 20  使用设备 21 提现 22
        "createTime": "2017-08-16 18:28:07",
        "orderId": "120170816182453000001"
      },
      {
        "id": "1000001088119627",
        "accountId": "1000002069833279",
        "beforeAdjustMoney": 900,
        "adjustMoney": -100,
        "afterAdjustMoney": 800,
        "adjustType": 1,
        "createTime": "2017-08-16 18:36:20",
        "orderId": "120170816182453000001"
      }
    ]
  }
}

```
### ID卡激活接口
**接口地址**：http://localhost:8080/api/app/card/active
#### 请求参数
```javascript
{
  "code" : "001",  //卡后
  "cardHoldName":"pengxiao", //持卡人姓名
  "cardHoldPhone" : "13776540149"  //持卡人号码
}
```
#### 响应参数
```javascript
{

  "code":"0",
  "msg":""
}
```

### 卡绑定接口

**接口地址**：http://.../api/app/card/bind

#### 请求参数
```javascript
{
  "code":"HH001", //卡号
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

  "code": 0,
  "data": {
    "id": "0",
    "isActive": 1,  //是否激活
    "merchantId": "10", //商户id
    "code": "001",
    "count": null,
    "createTime": null,
    "lastUseTime": null,  //最近使用时间
    "cardHoldName": "pengxiao",
    "cardHoldPhone": "13776540149",
    "isBind": 1, //是否绑定
    "userId": 17
  }
}
```

### 用户id卡查询接口

**接口地址**：http://localhost:8080/api/app/card/mycard

#### 请求参数
```javascript
{
  "token":"1111" //token

}
```
#### 响应参数
```javascript
{

  "code": 0,
  "data": {
    "id": "0",
    "isActive": 1,
    "merchantId": "10",
    "code": "001",
    "count": null,
    "createTime": null,
    "lastUseTime": null,
    "cardHoldName": "pengxiao",
    "cardHoldPhone": "13776540149",
    "isBind": 0,
    "userId": 17
  }
}
```

### ID卡使用记录接口

**接口地址**：http://localhost:8080/api/app/card/history

#### 请求参数
```javascript
{
  "token":"1111", //token
  "code":"001",
  "startTime":"2017-07-01",
  "endTime":"2017-09-01",
  "page":"1",  //页码
  "limit":"1"//每页数量
}
```
#### 响应参数
```javascript

{

  "code": 0,
  "data": {
    "totalCount": 4,
    "limit": 10,
    "totalPage": 1,
    "page": 1,
    "list": [
      {
        "id": "1",
        "code": "001",
        "count": 10,
        "type": 1,
        "payType": "1",
        "createTime": "2017-07-25 22:30:35",
        "adjustCount": null
      },
      {
        "id": "ff503f9b18c34aba925cc994f64e48d6",
        "code": "001",
        "count": 98,
        "type": 1,
        "payType": null,
        "createTime": "2017-07-27 23:08:15",
        "adjustCount": null
      },
      {
        "id": "a4812b01431143998da1f9b853e41636",
        "code": "001",
        "count": 97,
        "type": 1,
        "payType": null,
        "createTime": "2017-07-27 23:11:40",
        "adjustCount": 1
      },
      {
        "id": "25c40515be8c4fce88266fbe4d91f34e",
        "code": "001",
        "count": 96,
        "type": 1,
        "payType": null,
        "createTime": "2017-07-27 23:11:55",
        "adjustCount": 1
      }
    ]
  }
}
```


### 银行卡列表

**接口地址**:http://.../userbankcard/list

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
* 根据的登录信息查询分页的提现订单列表
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
* 根据的登录信息查询分页的提现订单列表
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
