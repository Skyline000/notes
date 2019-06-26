# POST / GET

Use command `curl`

Some parameter examples 

```text
-X/--request [GET|POST|PUT|DELETE|…]  使用指定的http method發出 http request
-H/--header                           設定request裡的header
-i/--include                          顯示response的header
-d/--data                             設定 http parameters 
-v/--verbose                          輸出比較多的訊息
-u/--user                             使用者帳號、密碼
-b/--cookie                           cookie  
```



**GET/POST/PUT/DELETE使用方式** 

-X 後面加 http method

```text
curl -X GET "http://www.rest.com/api/users"
curl -X POST "http://www.rest.com/api/users"
curl -X PUT "http://www.rest.com/api/users"
curl -X DELETE "http://www.rest.com/api/users"
```



**HEADER**

```text
curl -v -i -H "Content-Type: application/json" http://www.example.com/users
```



**Add HTTP Parameter**

Use `-d` and `&` or multiple `-d`

```text
# 使用`&`串接多個參數
curl -X POST -d "param1=value1&param2=value2"
# 也可使用多個`-d`，效果同上
curl -X POST -d "param1=value1" -d "param2=value2"
curl -X POST -d "param1=a 0space"     
# "a space" url encode後空白字元會編碼成'%20'為"a%20space"，編碼後的參數可以直接使用
curl -X POST -d "param1=a%20space"     
```



**POST JSON**

```text
curl http://www.example.com?modifier=kent -X PUT -i -H "Content-Type:application/json" -H "Accept:application/json" -d '{"boolean" : false, "foo" : "bar"}'
# 不加"Accept:application/json"也可以
curl http://www.example.com?modifier=kent -X PUT -i -H "Content-Type:application/json" -d '{"boolean" : false, "foo" : "bar"}'
```



Reference: [http://blog.kent-chiu.com/2013/08/14/testing-rest-with-curl-command.html](http://blog.kent-chiu.com/2013/08/14/testing-rest-with-curl-command.html)

