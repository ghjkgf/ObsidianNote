**使用 XMLHttpRequest 方法获取 JSON**

API（或叫应用程序编程接口）是计算机用来互相通信的工具。
大部分 web APIs 以 JSON 格式传输数据。 JSON 是 JavaScript Object Notation 的简写。
JSON 是由 API 以`bytes` 形式传输的，你的程序以`string`接受它。 它们能转换成为 JavaScript 对象，但默认情况下它们不是 JavaScript 对象。 `JSON.parse`方法解析字符串并构造它描述的 JavaScript 对象。
```js
<script>

 document.addEventListener('DOMContentLoaded', function(){

	 document.getElementById('getMessage').onclick = function(){

		const req = new XMLHttpRequest();

		req.open("GET",'/json/cats.json',true);   //2:url; 3:true表示异步
						
		req.send();

		req.onload = function(){

		const json = JSON.parse(req.responseText);

		document.getElementsByClassName('message')[0].innerHTML = JSON.stringify(json);

		};

	 };

 });

</script>
```
第二种方法:采用fetch()
```js
fetch('/json/cats.json')
    .then(response => response.json())
    .then(data => {
        document.getElementById('message').innerHTML = JSON.stringify(data);
    })
```
使用foreach将json数据输出到 html 里
```js
let html = "";
json.forEach(function(val) {
  const keys = Object.keys(val);
  html += "<div class = 'cat'>";
  keys.forEach(function(key) {
    html += "<strong>" + key + "</strong>: " + val[key] + "<br>";
  });
  html += "</div><br>";
});
```
过滤
```js
json = json.filter(function(val) {
  return (val.id !== 1);
});
```
根据地理位置数据找到用户的 GPS 坐标
```js
if (navigator.geolocation){
  navigator.geolocation.getCurrentPosition(function(position) {
    document.getElementById('data').innerHTML="latitude: " + position.coords.latitude + "<br>longitude: " + position.coords.longitude;
  });
}
```
发送数据
	将数据发送到外部资源，只要该资源支持 AJAX 请求并且你知道 URL。

	JavaScript 的`XMLHttpRequest`方法也用于将数据发布到服务器。
```js
const xhr = new XMLHttpRequest();
xhr.open('POST', url, true);
xhr.setRequestHeader('Content-Type', 'application/json; charset=UTF-8');
xhr.onreadystatechange = function () {
  if (xhr.readyState === 4 && xhr.status === 201){
    const serverResponse = JSON.parse(xhr.response);
    document.getElementsByClassName('message')[0].textContent = serverResponse.userName + serverResponse.suffix;
  }
};
const body = JSON.stringify({ userName: userName, suffix: ' loves cats!' });
xhr.send(body);
```