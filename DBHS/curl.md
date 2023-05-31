1.  -X/--request：指定 HTTP 请求方法，默认为 GET 方法。
2.  -H/--header：指定请求头，可以多次使用该选项添加多个请求头。
3.  -d/--data：指定请求体数据，常用于 POST 和 PUT 方法。可以使用 @ 符号指定文件路径或直接指定字符串。
4.  -i/--include：显示响应头。
5.  -o/--output：将响应保存到文件。
6.  -L/--location：跟随重定向。
7.  -u/--user：指定用户名和密码。
8.  -c/--cookie：发送 Cookie。
9.  -b/--cookie-jar：保存 Cookie。
10.  -k/--insecure：忽略 SSL 证书验证。

https://www.ruanyifeng.com/blog/2019/09/curl-reference.html
使用-d/-F 可以省略 -X POST
