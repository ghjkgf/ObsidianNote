### 使用 HttpClient
```java     报错
String url = "http://localhost:9088/etl/common/getHisChargeDic";  
Map<String, String[]> paramMap = request.getParameterMap();  
  
CloseableHttpClient httpClient = HttpClientBuilder.create().build();  
HttpPost httpPost = new HttpPost(url);  
  
// 将参数转换为字符串，并设置到请求体中  
String requestBody = convertParamMapToString(paramMap);  
httpPost.setEntity(new StringEntity(requestBody));  
  
// 发送请求并获取响应  
HttpResponse response = null;  
try {  
    response = httpClient.execute(httpPost);  
} catch (Exception e) {  
    throw new RuntimeException(e);  
}

private static String convertParamMapToString(Map<String, String[]> paramMap) {  
    StringBuilder stringBuilder = new StringBuilder();  
    for (Map.Entry<String, String[]> entry : paramMap.entrySet()) {  
        String key = entry.getKey();  
        String[] values = entry.getValue();  
        for (String value : values) {  
            stringBuilder.append(key).append("=").append(value).append("&");  
        }  
    }  
    return stringBuilder.toString();  
}
```

### webclient
```xml
<dependency>  
    <groupId>org.springframework.boot</groupId>  
    <artifactId>spring-boot-starter-webflux</artifactId>  
</dependency>
```
```java
// 调用methodB  
String url = "http://localhost:9088/etl/common/getHisChargeDic";
// 将request.getParameterMap()转换成MultiValueMap  
MultiValueMap<String, String> formData = new LinkedMultiValueMap<>();  
Map<String, String[]> parameterMap = request.getParameterMap();  
for (Map.Entry<String, String[]> entry : parameterMap.entrySet()) {  
    formData.put(entry.getKey(), Arrays.asList(entry.getValue()));  
}  
  
// 创建WebClient对象  
WebClient webClient = WebClient.create();  
  
// 发送POST请求  
webClient.post()  
        .uri(url)  
        .bodyValue(formData)  
        .retrieve()  
        .bodyToMono(String.class)  
        .block();  
  
// JSONObject jsonObject = new JSONObject(paraMap);  
// HttpUtils.doPost(url,);  
  
// ResponseEntity<String> responseEntity = restTemplate.postForEntity(url,null,);  
// String responseBody = responseEntity.getBody();
```

HttpServletRequest的parameterMap只有在进行
request.getParameterMap();
操作后才会 赋上值 ? 为什么