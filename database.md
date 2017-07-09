### 表结构设计


### 1. 用户表 user

   | 字段名称                    | type           | 备注  |
    |:---------------------------:|:--------------:|:-----:|
    | id                     | bigint | 用户id(主键) |
    | user_name                   | varchar(32) | 用户名     |
    | real_name                   | varchar(32) | 姓名（真实姓名）     |
    | password                    | varchar(32) |  密码（MD5加密）        |
    | mobile                      | varchar(32) | 手机号码 |
    | email                       | varchar(32) | 邮箱 |
    | sex                        | tinyint |性别 (1男性 0女性)|
    | birthday                   | datetime | 出生年月      |
    | role_id                    | varchar |  1普通用户 2管理员 3经销商 4财务人员 |
    
### 2.账户信息表 account_info   

   | 字段名称                    | type           | 备注  |
    |:---------------------------:|:--------------:|:-----:|
    |account_id                   |varchar（32）         |账户id   |
    |user_id                    |varchar（32）        |用户id   |
    |balance                      |decimal(11,2)         |账户余额|
    |create_at                    |datetime         |账户创建时间|
    |update_at                    |datetime         |账户更新时间|
    
    
### 2. 计费规则表 pay_rule
    | 字段名称                    | type           | 备注  |
    |:---------------------------:|:--------------:|:-----:|
    | id                     | bigint | 主键 |
    | fee                   | decimal(11,2) | 收费规则（元/每分钟） |
    
### 3. 充值优惠策略 charge_policy
    | 字段名称                    | type           | 备注  |
    |:---------------------------:|:--------------:|:-----:|
    | id                     | bigint | 主键 |
    | base_value                   | decimal(11,2) | 充值金额     |
    | add_value                     | decimal(11,2) | 赠送金额 |
    | is_enable                     |  tinyint | 是否生效（1是 0未生效） |
    
### 1. 推送消息表 push_message
    | 字段名称                    | type           | 备注  |
    |:---------------------------:|:--------------:|:-----:|
    | id                     | bigint | 主键 |
    | type                     | int | 类别（0 健康文章，1充值优惠活动，2广告） |
    | title                   | varchar（64） | 标题     |
    | content                    | varchar（516） | 内容 |
  

### 2. 角色表 role

   | 字段名称                    | type           | 备注  |
    |:---------------------------:|:--------------:|:-----:|
    | id                     | varchar | 角色id(主键) |
    | role_name                   | varchar | 角色名称(普通用户，分销商，总公司)       |
    
    
### 3.设备表 device 

   | 字段名称                    | type           | 备注  |
    |:---------------------------:|:--------------:|:-----:|  
    | device_id                    | varchar（32） |  设备id(主键)        |
    | code                    | varchar（32） |  设备的编码      |
    | use_status                    | tinyint |  设备使用状态（0未使用，1使用中） |
    | is_breakdown                    | tinyint |  1故障 0在线 |
    | total_money                  | decimal(11,2) |  设备使用产生的总金额 |
    | total_time                  | bigint |  使用的总时间（秒）
    
### 3.设备绑定表 device_bind 

   | 字段名称                    | type           | 备注  |
    |:---------------------------:|:--------------:|:-----:|  
    | id                   | varchar(32) |  id        |
    | device_id                    | varchar(32) |  设备id        |
    | dealer_id                    | varchar(32) |  经销商表 |
    | bind_time                    | datetime |  绑定时间 |

   
    
### 4. 设备终端信息表 device_terminal (去掉)

   | 字段名称                    | type           | 备注  |
    |:---------------------------:|:--------------:|:-----:|
    | device_id                     | varchar | 设备id(主键) |
    | *device_type*                     | *varchar* | *设备类型（方便以后扩张设备，如果只有一种设备可以去掉）* |
    | delivery_time                   | datetime |  设备交付时间        |
    | *device_sn*                   | *varchar* | *设备序列号码（保留）*         |
    | *device_batch_no*                     | *varchar* | 设备出厂批次号（保留） |
    | *operation_status*                   | *varchar* | *设备状态如：出厂，返修等（保留）*         |
    | *is_demo*                     | *varchar* | *是否是样机（保留）* |

 
### 5.设备实时状态表 device_status（去掉）

   | 字段名称                    | type           | 备注  |
    |:---------------------------:|:--------------:|:-----:|
    | device_id                     | varchar | 设备id(主键) |
    | ...                     | ... | ... |


### 6.设备历史状态表 device_status_histroy

   | 字段名称                    | type           | 备注  |
    |:---------------------------:|:--------------:|:-----:|
    | id                     | varchar（32） | 历史表(主键) |
    | type                     | tinyint | 1app用户 2Id卡用户|
    | user_id                     | varchar（32） | 用户id |
    | device_id                     | varchar（32） | 设备id |
    | report_time                     | datetime | 上报时间 |
    | value                     | ... | 数值 |
    | create_time                     | datetime | 创建时间 |
    
### 6.id卡使用表 

   | 字段名称                    | type           | 备注  |
    |:---------------------------:|:--------------:|:-----:|
    | id                     | bingint | 主键)|
    | count                     | int | 剩余次数 默认为0 |
    | device_id                     | varchar | 设备id |
    | report_time                     | datetime | 上报时间 |
    | value                     | ... | 数值 |
    | create_time                     | datetime | 创建时间 |


### 7.分销商信息表 dealer_info

   | 字段名称                    | type           | 备注  |
    |:---------------------------:|:--------------:|:-----:|
    | id                     | varchar(32) | 分销商id(主键)     |
    | user_id                   | varchar（32） | 分销商用户id关联user表 |
    | address               | varchar（128） | 联系地址 |
    | rate                   | decimal（11,2） | 分成比例 |
    | is_withdraw                   | tinyint | 是否允许提现（1允许 0不允许） |
    
    
    
### 8.商品表 goods
  **设备的一次使用抽象成一个商品**

   | 字段名称                    | type           | 备注  |
    |:---------------------------:|:--------------:|:-----:|
    | goods_id                     | varchar | 商品id(主键)     |
    | device_id                   | varchar | 设备id |
    | user_id                   | varchar | 设备当前使用者id |
    | start_time                   | datetime | 使用开始时间 |
    | end_time                | datetime |  使用结束时间        |
    | cost_money                | decimal |  设备使用产生的费用        |


### 9.订单表 order

   | 字段名称                    | type           | 备注  |
    |:---------------------------:|:--------------:|:-----:|
    | order_id                     | varchar | 订单id(主键)     |
    | user_id                   | varchar | 消费者id关联user表 |
    | create_at                | datetime |  订单创建时间        |
    | pay_at          | datetime | 订单发起支付时间         |
    | pay_type          | varchar | 支付类型（0 支付宝 1微信 2银联） |
    | dealer_id               | varchar | 分销商id  |
    | trans_id                   | varchar | 交易流水号 |
    | goods_id                   | varchar | 一次交易的商品id |
    | order_money                   | varchar | 订单金额 |
    | status                   | varchar | 订单状态（待支付，支付中，支付完成...） |
    | *status_msg*                | *varchar* |  *状态描述信息（保留）*        |
    | *memo*          | *varchar* | *订单备注（保留*）|
    | is_deleted          | varchar | 订单是否删除（删除订单不在所有订单里展示） |
    | refund_id               | varchar | 退款单id关联refund_order表 |
    
### 10.订单日志表 order_log

   | 字段名称                    | type           | 备注  |
    |:---------------------------:|:--------------:|:-----:|
    | log_id                     | varchar | 日志id(主键)     |
    | order_id                   | varchar | 订单id关联订单表 |
    | old_status                | varchar |  旧状态        |
    | new_status          | varchar | 新状态         |
    | create_at          | datetime | 创建时间 |
    | create_by                     | varchar | 创建人    |
    | memo                   | varchar | 备注 |

### 11.退款订单表 refund_order

   | 字段名称                    | type           | 备注  |
    |:---------------------------:|:--------------:|:-----:|
    | refund_order                     | varchar | 退款订单号(主键)     |
    | apply_at                   | varchar | 退款申请时间 |
    | apply_memo                   | varchar | 退款申请备注 |
    | apply_reason                   | varchar | 退款申请原因 |
    | status                | varchar |  退款单状态        |
    | refund_at          | datetime | 退款时间         |
    | refuse_reason          | varchar | 拒绝退款原因 |
    | refuse_memo                     | varchar | 拒绝退款备注    |
    | is_cancel                   | varchar | 订单是否取消 |

### 12.分销商结算单表 account_settlement    

   | 字段名称                    | type           | 备注  |
    |:---------------------------:|:--------------:|:-----:|
    |settlement_id    |varchar    | 结算单号id（主键）|
    |dealer_id        |varchar    |    分销商id|
    |status |varchar  |结算单状态(分销商申请，总公司确认，总公司打款，分销商收款确认)|
    |actual_money      |varchar  |实际时间|
    |plan_money      |varchar  | 计划金额（分成前的费用）|
    |create_at          |datetime  |创建时间|
    |dealer_confirm_at  |datetime|分销商确认收款时间|
    |admin_confirm_at  |datetime|总公司确认时间|
    |admin_confirm_by  |varchar|总公司确认人|
    
    

    
    

  
### 15.账户交易流水 account_transaction_history

   | 字段名称                    | type           | 备注  |
    |:---------------------------:|:--------------:|:-----:|
    |id                       |varchar（32）      |流水id（主键）|
    |account_id             |varchar（32）     |账户id关联account_info表       |
    |before_adjust_money          |decimal（11,2）  |调整前金额           |
    |adjust_money                 |decimal（11,2         |调整金额          |
    |after_adjust_money           |decimal（11,2   |调整后金额         |
    |adjust_type                  |tinyint          |调整类型（0  用户充值 1 用户消费 2用户退款 3 分销商结算）          |
    |create_at                   |datetime           |流水创建时间          |
    |order_id                    |varchar（32）|订单id（用户充值： 充值订单id， 用户消费：订单id，用户退款：退款id，分销商结算：结算单id）|
   

### 15.管理员账户交易流水 root_account_transaction_history
|:---------------------------:|:--------------:|:-----:|
    |id                       |varchar（32）      |流水id（主键）|
    |before_adjust_money          |decimal（11,2）  |调整前金额           |
    |adjust_money                 |decimal（11,2)        |调整金额          |
    |after_adjust_money           |decimal（11,2) |调整后金额         |
    |adjust_type                  |tinyint          |调整类型（0  用户充值 1 用户消费 2用户退款 3 分销商结算）          |
    |create_at                   |datetime           |流水创建时间          |
    |order_id                    |varchar（32）|订单id（用户充值： 充值订单id， 用户消费：订单id，用户退款：退款id，分销商结算：结算单id）|
  
   



    



    



