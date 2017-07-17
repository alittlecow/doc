## web端接口


###订单
~~### 支付订单接口~~
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

###账户

**接口地址**：hhttp://localhost:8083/account/list

#### 请求参数
```javascript
{
    "token":"1",    //令牌
    "pageNo":"1"  //
    "onePageNum","10",
    "beginTime","2017-09-23",
    "endTime","2017-09-01"
}
```
#### 响应参数
```javascript
{
  "result": "success",
  "message": "",
  "totalRecordNum": 2,
  "pages": 1,
  "pageNo": 1,
  "data": [
    {
      "id": "1",
      "userId": "1",
      "createTime": "2017-07-14 23:43:45",
      "updateTime": "2017-07-15 00:21:02",
      "money": 9698.62
    },
    {
      "id": "8a7e35011471428b98dcdfcdb2846dc0",
      "userId": "f515478e004b4ddd865b4d9ef41b4fd9",
      "createTime": "2017-07-15 20:24:40",
      "updateTime": "2017-07-15 23:27:20",
      "money": 99900.2
    }
  ]
}
```



### 账户余额查询接口

**接口地址**：http://.../account/queryAccountById

#### 请求参数
```javascript
{
     "id":"1",    //账户id
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

### 商品列表查询

**接口地址**：http://.../account/queryAccountById

#### 请求参数
```javascript
{
     "token":"1",    //令牌
     "type":"1",    //类型
    "pageNo":"1"  //
    "onePageNum","10",
    "beginTime","2017-09-23",
    "endTime","2017-09-01"
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


