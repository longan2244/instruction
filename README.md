# 本接口采用 常规返回方式
{

msg ：”xxxx“

status：0/1 0：失败 1：成功

data 数据源

}

在以后每一次（/api/xxxx) 都需要设置	‘Authorization’："tokens"
# 用户相关
## 正则表达式
```
{
  Remail: { //邮箱
    test: /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/,
    msg: '邮箱格式不正确'
  },
  Rusername: {//4到16位 用户名
    test: /^[\w-]{4,16}$/,
    msg: '用户名格式不正确'
  },
  Rpassword: {//4到16位 密码
    test: /^[\w-]{4,16}$/,
    msg: '密码格式不正确'
  },
  Rkami:108
}
```
## 注册(/register) POST请求
```
用户名 ：username

密码：password

邮箱：email
```
## 登录（/login） POST请求
```
用户名 ：username

密码：password

返回 一个token

"data": {
        "tokens": "Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6InVzZXIiLCJlbWFpbCI6IjEyMzQ1NkBxcS5jb20iLCJwYXNzd29yZCI6IiQyYSQxMCRuU1c0RnloZk1DU3d4SGRFRW9nUzgucEZkcEptVXpXN1h5bTgwaWpFRFUueGlQSDZ1SlRpVyIsImNyZWF0ZV90aW1lIjoiMTY3NjEyODkxNDYyOSIsImlkIjo4LCJtb255IjoiMCIsIlJPT1QiOiIwIiwiaWF0IjoxNjc2MTMwMTE3LCJleHAiOjE2NzYyMTY1MTd9.9vQUqTfIXodfjrYZUM0CBBt6nL429pZDZsIfPG_pGEY"
        }
	
	请将tokens保存到本地存储
```
## 卡密充值（/api/user/usekami）post请求
```
用户名 ：username

卡密 ：kami

```
## 请求car状态 （/api/user/carstate） post请求
```
卡号：access_cardno

access_token ：access_token
```
# 管理员相关
···测试账号：user···

···测试密码：user···
## 管理员登录
与普通用户登录一致 后台自动判断是否为管理员
## 生成卡密（/api/admin/createkami） post请求
```
生成多少张：create_count

每一张多少钱：create_money （整数 不要带小数点）

```
## 查询用户信息 (/api/admin/userinfo) post 请求
```
 用户信息 ： id （可选）

  //如果不传id将列出所有的用户
```
## 通过管理员修改用户密码（/api/admin/updatepassword） post请求
```
旧密码：oldpassword

新的密码 ：newpassword

用户id：userid
```
## 通过管理员修改用户余额（/api/admin/updatemoney） post请求
```
用户id ：userid
想修改的余额 ：money
```
..........
