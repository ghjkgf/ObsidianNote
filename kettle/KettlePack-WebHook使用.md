## 一、WebHook 简介

KettlePack WebHook 功能是任务执行中或执行后，自动回调（Post）一个在KettlePack中设定的http地址。

包含以下钩子（事件）：

> - 任务执行结果
> - 异常任务告警
> - 关键字告警



---





## 二、第三方支持

> 你可以在第三方平台接收来自KettlePack 的通知
>
> 目前 KettlePack WebHook 支持 钉钉机器人、企业微信机器人、[PushPlus](http://www.pushplus.plus) 
>
> `WebHook签名类型` 只对 `自定义WebHook` 有效，对 `第三方WebHook` 时无效，KP会根据所填URL判断是自定义还是第三方



### 钉钉机器人

1. 在钉钉中进入 群设置 -> 智能群助手 -> 添加机器人

2. 添加自定义机器人

   ![](http://kettlepack.congjing.net/download/webhook/images/webhook-dingtalk-1.png)

3. 输入机器人名字：KettlePack 

   ![](http://kettlepack.congjing.net/download/webhook/images/webhook-dingtalk-2.png)

4. 复制Webhook地址填至KP的`URL` ；

   ```
   https://oapi.dingtalk.com/robot/send?access_token=xxxx
   ```
   
5. 安全设置中选择 `加签`，将 `SEC开头的字符串` 复制并填至KP的 `密码或签名密钥`

   ![](http://kettlepack.congjing.net/download/webhook/images/webhook-dingtalk-3.png)

6. KettlePack中设置

   ![](http://kettlepack.congjing.net/download/webhook/images/webhook-dingtalk-kp.png)

---

### 企业微信机器人

1. 进入企业微信群 -> 添加群机器人 -> 新创建一个机器人 

2. 输入机器人名称，并添加

   ![](http://kettlepack.congjing.net/download/webhook/images/webhook-wxwork-1.png)

3. 复制Webhook地址并填至KP的 `URL`

    ```
    https://qyapi.weixin.qq.com/cgi-bin/webhook/send?key=xxxx
    ```

4. KettlePack中设置

   ![](http://kettlepack.congjing.net/download/webhook/images/webhook-wxwork-kp.png)

---



### PushPlus

发送渠道(channel) 为微信公众号（wechat）

1. 访问PushPlus，并微信扫码登录

2. KP的 `URL` 填入 ```http://www.pushplus.plus/send```

3. 密码或签名密钥中填入你的token

   ![](http://kettlepack.congjing.net/download/webhook/images/webhook-pushplus-1.png)

4. KettlePack中设置

   

   ![](http://kettlepack.congjing.net/download/webhook/images/webhook-pushplus-kp.png)



---





## 三、自定义WebHook


> - 适用于用户自己开发Server端
>
> - 此部分内容参考了 [Gitee](https://gitee.com/help/categories/40) 、 [钉钉](https://open.dingtalk.com/document/robots/customize-robot-security-settings) 的WebHook接入规范



### 添加WebHook



####  参数说明

- URL: 接收 WebHook 数据的 http 地址。KettlePack 将发送 Post 请求到这个地址
- 钩子（事件）: 用户在 KettlePack 上可触发的 WebHook，支持添加多个钩子
- WebHook 密码/签名密钥：用于 WebHook 鉴权的方式，可通过 `WebHook 密码` 进行鉴权，或通过 `签名密钥` 生成请求签名进行鉴权，防止 URL 被恶意请求。
   - 密码: 可为空；KettlePack 将会在 Post 数据中携带这个密码。注意， **密码是明文**
   - 签名密钥: 参见下面的【WebHook 签名验证及算法】



---





### WebHook 推送数据格式说明

用户可以通过自建服务接收来自 KettlePack WebHook 的消息，相关 WebHook 推送数据格式的说明如下：

#### Request Headers

WebHook request headers 包含以下一些关键数据

```

Content-Type: application/json   # 默认为 application/json

User-Agent: kettlepack-hook   # 固定为 kettlepack-hook，可用于标识为来自 kettlepack 的请求

KettlePack-Token: password/sign   # 用户新建 WebHook 时提供的密码或根据提供的签名密钥计算后的签名

KettlePack-Timestamp: 1641782810979   # 触发 WebHook 的时间戳

KettlePack-Event: test/task_record/error_alarm/keyword_alarm   # 标识触发的钩子类型

```

---



### WebHook 签名验证及算法




####  WebHook 签名介绍

KettlePack WebHook 支持通过密钥进行安全验证。

用户通过配置不公开的 WebHook 密钥，在请求时对请求内容签名，服务端在收到请求后以同样的密钥进行签名验证，以确认收到的请求完整且可信任。整个过程 WebHook 密钥只存在于 KettlePack 和服务端，不在网络传输中暴露。

> 相比密码验证的方式，签名验证可以有效避免在网络传输过程中 WebHook 密码泄露带来的安全问题。



#### WebHook 签名校验算法（参考）

如果 WebHook 使用了签名方式，在请求目标时会在当次请求头中加入名为 `KettlePack-Token`，值为生成的签名内容。其签名实现算法如下：


#####  签名参数说明

| 参数      | 说明                   |
| --------- | ---------------------- |
| timestamp | 当前时间戳，单位：毫秒 |
| secret    | 签名密钥               |

- Step1：把 `timestamp+"\n"+密钥` 当做签名字符串，使用HmacSHA256算法计算签名。
- Setp2：对上述得到的结果进行 Base64 encode。

  


#####  签名计算示例代码

签名计算代码示例（Java）

```java
String stringToSign = timestamp + "\n" + secret;
Mac mac = Mac.getInstance("HmacSHA256");
mac.init(new SecretKeySpec(secret.getBytes("UTF-8"), "HmacSHA256"));
byte[] signData = mac.doFinal(stringToSign.getBytes("UTF-8"));
return new String(Base64.encodeBase64(signData);
```





---



### WebHook 推送数据类型说明



#### 字段说明 

| 字段      | 数据类型 | 说明                                                         |
| --------- | -------- | ------------------------------------------------------------ |
| hook_id   | String   | 钩子ID（kp_webhook.id）                                      |
| hook_type | String   | 钩子类型（test / task_record / error_alarm / keyword_alarm） |
| hook_name | String   | 名称（kp_webhook.hook_name）                                 |
| sign      | String   | 签名（详见签名算法）                                         |
| password  | String   | 密码（明文）                                                 |
| timestamp | Long     | 时间戳（毫秒）                                               |
| content   | 钩子对象 | 见下面钩子对象说明                                           |

#### 钩子对象字段说明 

| 钩子字段             | 数据类型 | 说明                                                 |
| -------------------- | :------: | ---------------------------------------------------- |
| keyword_id           |  String  | 关键字ID（kp_alarm_keyword.id）；`关键字告警`特有    |
| keyword              |  String  | 关键字（kp_alarm_keyword.keyword）；`关键字告警`特有 |
| record_id            |  String  | 执行记录ID（kp_task_record.id）                      |
| task_type            |  String  | 任务类型（job / trans）                              |
| task_type_desc       |  String  | 任务类型说明                                         |
| task_id              |  String  | 任务ID（kp_trans.id 或 kp_job.id）                   |
| task_name            |  String  | 任务名称                                             |
| task_path            |  String  | 任务路径                                             |
| task_cron            |  String  | cron表达式                                           |
| record_status        |  Integer | 任务状态                                             |
| record_status_desc   |  String  | 任务状态说明                                         |
| start_time           |  String  | 开始时间（yyyy-MM-dd HH:mm:ss）                      |
| stop_time            |  String  | 结束时间（yyyy-MM-dd HH:mm:ss）                      |
| category_id          |  String  | 分类ID（kp_category.id）                             |
| category_name        |  String  | 分类名称                                             |
| resource_type        |  String  | 资源类型（file / rep）                               |
| resource_type_desc   |  String  | 资源类型描述                                         |
| repository_id        |  String  | 资源库ID（kp_repository.id）                         |
| repository_type      |  String  | 资源库类型（fileRep / dbRep）                        |
| repository_type_desc |  String  | 资源库类型描述                                       |
| repository_name      |  String  | 资源库名称                                           |
| log_level            |  String  | 日志级别                                             |
| log_level_desc       |  String  | 日志级别描述                                         |
| log_file_path        |  String  | 日志路径                                             |
| run_config           |  String  | 执行方式（local / remote）                           |
| run_config_desc      |  String  | 执行方式描述                                         |
| remote_server        |  String  | Carte服务ID（kp_carte.id）                           |
| remote_server_name   |  String  | Carte服务名称                                        |
| log_content          |  String  | 日志内容                                             |


---



### WebHook 推送数据示例

####  任务执行结果 / 异常任务告警

> 此两个钩子内容(content)一致

```json
{
  "hook_id": "745b93cfd80949c8a56095f43f1346f3",
  "hook_type": "task_record",
  "hook_name": "xxx",
  "sign": "sJBE5147Mdh0uW95UKi4NRikMZmgTenGl2bx023Rseo=",
  "password": "",
  "timestamp": 1641793525917,
  "content": {
    "record_id": "318075b05f254eb8affe8f03b7eed5ee",
    "task_type": "job",
    "task_type_desc": "作业",
    "task_id": "1373fccea65aad9872a419fbd7288841",
    "task_name": "script.kjb",
    "task_path": "/script.kjb",
    "task_cron": "0 * * * * ? *",
    "record_status": 0,
    "record_status_desc": "失败",
    "start_time": "2022-01-10 13:45:23",
    "stop_time": "2022-01-10 13:45:25",
    "category_id": "",
    "category_name": "",
    "resource_type": "file",
    "resource_type_desc": "本地文件",
    "repository_id": "",
    "repository_type": "",
    "repository_type_desc": "",
    "repository_name": "",
    "log_level": "Basic",
    "log_level_desc": "基本日志",
    "log_file_path": "D:/CongJing/kettle-pack/logs/job/1373fccea65aad9872a419fbd7288841/20220110134523610_318075b05f254eb8affe8f03b7eed5ee.log",
    "run_config": "remote",
    "run_config_desc": "Carte服务",
    "remote_server": "eaf27055866ba48e4d787f9760041265",
    "remote_server_name": "s10-8088",
    "log_content": "Carte服务连接失败！\r\norg.pentaho.di.core.exception.KettleException: \r\norg.apache.http.conn.HttpHostConnectException: Connect to 192.168.190.10:8088 [/192.168.190.10] failed: Connection refused: connect\r\nConnect to 192.168.190.10:8088 [/192.168.190.10] failed: Connection refused: connect\r\n"
  }
}
```



#### 关键字告警  

> 相比 `任务执行结果` / `异常任务告警` 两个钩子多了 `keyword_id` 和 `keyword`

```json
{
  "hook_id": "745b93cfd80949c8a56095f43f1346f3",
  "hook_type":"keyword_alarm",
  "hook_name": "xxx",
  "sign": "1KJ5LZ+ZdGvbIomKOHk7GtczqKS+jTf3+O6T3LeiLso=",
  "password": "",
  "timestamp": 1641793841552,
  "content": {
    "keyword_id": "761bc00f0711e0d53f616b3ad83fe4aa",
    "keyword": "Connection refused",
    "record_id": "69efbe0471dc4b51b87133a0b3b7b2eb",
    "task_type": "job",
    "task_type_desc": "作业",
    "task_id": "1373fccea65aad9872a419fbd7288841",
    "task_name": "script.kjb",
    "task_path": "/script.kjb",
    "task_cron": "0 * * * * ? *",
    "record_status": 0,
    "record_status_desc": "失败",
    "start_time": "2022-01-10 13:50:39",
    "stop_time": "2022-01-10 13:50:41",
    "category_id": "",
    "category_name": "",
    "resource_type": "file",
    "resource_type_desc": "本地文件",
    "repository_id": "",
    "repository_type": "",
    "repository_type_desc": "",
    "repository_name": "",
    "log_level": "Basic",
    "log_level_desc": "基本日志",
    "log_file_path": "D:/CongJing/kettle-pack/logs/job/1373fccea65aad9872a419fbd7288841/20220110135039277_69efbe0471dc4b51b87133a0b3b7b2eb.log",
    "run_config": "remote",
    "run_config_desc": "Carte服务",
    "remote_server": "eaf27055866ba48e4d787f9760041265",
    "remote_server_name": "s10-8088",
    "log_content": "Carte服务连接失败！\r\norg.pentaho.di.core.exception.KettleException: \r\norg.apache.http.conn.HttpHostConnectException: Connect to 192.168.190.10:8088 [/192.168.190.10] failed: Connection refused: connect\r\nConnect to 192.168.190.10:8088 [/192.168.190.10] failed: Connection refused: connect\r\n"
  }
}
```



---



### WebHook 测试

> - 推荐使用 [webhook.site](https://webhook.site/) 进行测试，可直观的看到整个钩子请求的内容
> - 在`URL`中填写你 webhook.site 的地址
> - 选填 `密码` 或 `WebHook密钥` 

1. KettlePack设置

![](http://kettlepack.congjing.net/download/webhook/images/webhook-site-kp.png)

2. webhook.site显示

![](http://kettlepack.congjing.net/download/webhook/images/webhook-site-test.png)



*by MJP 20220112*



