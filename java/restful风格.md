地址栏只用斜线分隔 
安全
高效,支持缓存
@RequestMapping(value="",method="")
```
@RequestMapping("/test/{a}/{b}")  
public String testRestful(@PathVariable int a,@PathVariable int b, Model model)
```
组合注解
	- @GetMapping
	- @PostMapping
	- @PutMapping
	- @DeleteMapping
	- @PatchMapping