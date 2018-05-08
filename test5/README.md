
# 实验5：图书管理系统数据库设计与界面设计  
## 1.数据库表设计  
### 1.1读者表  
  
| 字段| 类型-长度 |可否为空| 主键|注释|  
|:-------:|:-------:|:-------:|:-------:|:-------:|  
|id|int(8)|否|key|借书卡号|  
|user_name|varchar(30)|否||姓名|  
|user_phonenum|int(11)|否||电话|  
|user_idcard|int(18)|否||身份证号|  
|user_Quota|short|否||图书限额|  
|user_usenum|short|否||已借图书数|  
### 1.2图书管理员表  
  
| 字段| 类型-长度 |可否为空| 主键|注释|  
|:-------:|:-------:|:-------:|:-------:|:-------:|  
|admin_id|int(8)|否|key|职工号|  
|admin_name|varchar(30)|否||姓名|  
|admin_phonenum|int(11)|否||电话|  
### 1.3图书种类  
  
| 字段| 类型-长度 |可否为空| 主键|注释|  
|:-------:|:-------:|:-------:|:-------:|:-------:|  
|book_name|varchar(30)|否|key|书名|  
|author|varchar(30)|是||作者|  
|press|varchar(30)|是||出版社|  
|release_date|date|是||出版日期|  
|total|short|否||馆藏总量|  
|surplus|short|否||可借数量|  
### 1.4图书  
| 字段| 类型-长度 |可否为空| 主键|注释|  
|:-------:|:-------:|:-------:|:-------:|:-------:|  
|identifier|int(8)|否|key|图书编号|  
|state|short|否||状态|  
### 1.5借书记录  
| 字段| 类型-长度 |可否为空| 主键|注释|  
|:-------:|:-------:|:-------:|:-------:|:-------:|  
|id|int(8)|否|key|借书卡号|  
|identifier|int(8)|否|key|图书编号|  
|borrow_num|int(8)|否||借书编号|  
|borrow_time|date|否||借书日期|  
|should_time|date|否||应还日期|  
|return_time|date|否||归还日期|  
### 1.6预定记录  
| 字段| 类型-长度 |可否为空| 主键|注释|  
|:-------:|:-------:|:-------:|:-------:|:-------:|  
|id|int(8)|否|key|借书卡号|  
|identifier|int(8)|否|key|图书编号|  
|reserve_num|int(8)|否||预定编号|  
|reserve_time|date|否||预定日期|  
### 1.7违规记录  
| 字段| 类型-长度 |可否为空| 主键|注释|  
|:-------:|:-------:|:-------:|:-------:|:-------:|  
|id|int(8)|否|key|借书卡号|  
|identifier|int(8)|否|key|图书编号|  
|irregularities_num|int(8)|否||违规编号|  
|rregularities_type|char(8)|否||违规类型|  
|fine|short|否||处罚金额|  
## 2界面及接口设计  
### 2.1 读者个人信息界面设计  
![](./xingxi.png '描述')  
#### 读者个人信息接口  
功能：用于获取读者的个人信息  
请求地址：  
请求方法：POST  
请求参数：  

|参数名称|必填|说明|  
|:-------:|:-------:|:-------:|  
|id|是|验证读者是否登录|  
返回实例  
{  
"status";true  
"id":"12345678",  
"user_name":"张奇",  
"user_phonenum":"17788887230",  
"user_idcard":"58944774555877458484",  
"user_Quota":"5",  
"user_usenum":"2",  
  
}  
返回参数说明：  

|参数名称|说明|  
|:-------:|:-------:|  
|status|bool类型，true表示正确的返回，false表示错误的返回|  
|id|读者借书卡号|  
|user_name|读者姓名|  
|user_phonenum|读者电话号码|  
|user_idcard|读者身份证号|  
|user_Quota|读者的图书限额|  
|user_usenum|读者已借图书数|  
### 2.2查找图书界面设计  
![](./chaxun.png '描述')  
#### 查找图书信息接口  
功能：用于获取图书信息  
请求地址：  
请求方法：POST  
请求参数：  

|参数名称|必填|说明|  
|:-------:|:-------:|:-------:|  
|id|否|验证读者是否登录|  
|book_name|否|读者所想要查询的图书名字,如果没有则返回所有图书|  
返回实例  
{  
"status";true  
“data”：[{  
  
"book_name":"疯狂android讲义",  
"author":"李刚",  
"press":"电子工业出版社  
"release_date":"2011年7月  
"total":"5",  
"surplus":"2",  
}  
....  
]  
  
  
}  
返回参数说明：  

|参数名称|说明|  
|:-------:|:-------:|  
|status|bool类型，true表示正确的返回，false表示错误的返回|  
|book_name|图书名|  
|author|作者|  
|press|出版社|  
|release_date|发行日期|  
|total|图书总量|  
|surplus|剩余库存|  
  
#### 2.3借书记录接口  
功能：用于获取读者的借阅信息  
请求地址：  
请求方法：POST  
请求参数：  

|参数名称|必填|说明|  
|:-------:|:-------:|:-------:|  
|borrow_num|是|借书编号|  
返回实例  
{  
"status";true，  
"id":"12345678",  
"identifier":"74842841",  
"borrow_num":"48714848",  
"borrow_time":"2017-6-6",  
"should_time":"2017-10-1",  
"return_time":"2017-8-8",  
  
}  
返回参数说明：  

|参数名称|说明|  
|:-------:|:-------:|  
|status|bool类型，true表示正确的返回，false表示错误的返回|  
|id|读者借书卡号|  
|identifier|图书编号|  
|borrow_num|借书编号|  
|borrow_time|借书日期|  
|should_time|应还日期|  
|return_time|实际归还日期|