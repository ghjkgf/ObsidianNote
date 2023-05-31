pip install requests

r = requests.get(url,params,**kwargs)	
	13个:
	params,data,json,headers,cookies,auth,files,timeout,proxies,
	allow_redirects,stream,verify,cert
r.encoding = "utf-8"		;apparent_encoding	从内容推断出的编码格式
r.text		
r.status_code	检查状态

六种异常:
	ConnectionError
	HttpError
	URLRequired
	TooManyRedirects
	ConnectTimeout
	Timeout
	
raise_for_status()			//如果状态不是200,引发HTTPError异常

patch 与 put 的区别

伪装:
	1.  User-Agent
headers={'User-Agent':'Mozilla/5.0 (Windows NT 6.1; Win64; x64; rv:88.0) Gecko/20100101 Firefox/88.0'
,'referer':'https://bj.meituan.com/'}
r = requests.get(url,headers=headers)
	2.  referer
	3.proxies
proxies={'https':'101.236.54.97:8866'} 
	4. 减速
import time,random

for i in range(10):
    response = requests.get("https://waimai.meituan.com/",headers=headers，proxies=proxies)  #模拟请求url
    time.sleep(random.uniform(1.1,5.4))
	5 cookies
	cookies = ''
关键词
	r=requests.get('http://www.baidu.com/s',params=kv)
	
图片爬取
	url=
	root = 
	path = root+url.split('/')[-1]
	try:
		if not os.path.exists(root):
			os.mkdir(root)
		if not os.path.exists(path):
			r = requests.get(url)
			with open(path,'wb') as f:
				f.write(r.content)
				f.close()
				print("scuess")
		else:
			print("文件已存在")
	except:
		print("爬取失败")


ip查询(https://www.ip138.com/iplookup.asp?ip=124.71.180.39&action=2)









