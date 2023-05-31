BeautifulSoup方法的第一个参数如何传递文件(本地/http),open方法一直报错

4种解析器
	'html.parser'		bs自带的

pip install lxml
	'lxml','xml'
	
pip install html5lib
	'html5lib'
	
五类基本元素  bs4.element.
	相同的标签只能获取第一个符合要求的标签
	Tag
	Name
	Attributes 
	NavigableString >和<间的内容,可以跨越中间的标签对
	Comment	.string 会输出没有注释符号的文本
	
遍历标签树
	.contents  返回列表
	.children
	.descendants
	.parent(s)
	.next_sibling(s)
	.previous_sibling(s)
	
prettify()			更好的显示

 查找方法    find_all
 参数:
 	name	标签名
	attrs	属性值
	recursive	默认true
	string	检索字符串域
soup.find_all()可缩写为soup()
<tag>.find_all()           <tag>()
	
