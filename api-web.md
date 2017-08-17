# eyes-world api for web

## 注册

#### 注册

* router
  * /signup

* request
```js
// POST
{
    "userName": String,
    "password": String
}
```

* respond
```js
{
    "success": Boolean
}
```

#### 验证用户名是否存在

* router
  * /signup/{userName}

* request

* respond
```js
{
    "nameUsed": Boolean
}
```
true---可以使用
false---不可用使用，已经重名
## 登录

----
### 电视获取二维码url及marker

* router
  * /login/tv/getqr  GET
  
* request


* respond
```js
    {
        "qrPath":String,
        "marker":String
    }
```

---
### 手机发送marker

* router
  * /login/phone/sendmarker  POST

* request
  * ?marker=...
  
* response
  * 200

---
###  电视登录

* router
  * /login/tv/login
  
* request
  * ?marker=...
  
* response
  *  200

---



## 上传

### 景点图片上传

* router
  * /upload/uploadPhoto/spots/{provinceName}/{cityName}  POST

* request

  * ?albumName=...&photoName=...&photoDesc=...


* respond
```js
  * {respond:Boolean}
```
### 高校图片上传

* router
  */upload/uploadPhoto/college/{provinceName}  POST

* request

  * ?albumName=...&photoName=...&photoDesc=...


* respond
```js
  * {respond:Boolean}
```

## 图片评论

### 获取评论
* router
  */api//user/works/{photoName}/comment  GET


* response
```js
[{
	"commentId":Integer,
    "userName": String,
    "comment": String,
    "modificationTime": Number
}, ...]
```
```js
例子：
[{"commentId":9,
"username":"Mike",
"content":"评论内容1",
"modificationTime":2017},
{"commentId":10,
"username":"Liky",
"content":"评论内容2",
"modificationTime":2017}]
```

### 是否可删除图片评论（用户自己发的评论才可以删除）

* router
  * /api/user/works/{commentId}/deletable
  
* respond
```js
  * {respond:Boolean} 
```
true---可删除
false---不可删除


### 删除图片评论

* router
  * /api/user/works/{commentId}/commentDelete  
  
* respond
```js
  * {respond:Boolean}
```