四大组件
 Downloader
 PageProcessor
 Scheduler
 Pipeline
 
 Request是对Url地址的一层封装,一个request对应一个url地址,是pageprocessor与downloader交互的载体
 
 Page代表了从Downloader下载到的一个页面(html,json,其他文本格式)
 
 ResultItems相当于一个Map,保存PageProcessor处理的结果,供Pipeline使用

爬取动态数据
https://blog.csdn.net/ITarmi/article/details/119808997

和selenium结合使用
https://www.jianshu.com/p/929db7dc8f77