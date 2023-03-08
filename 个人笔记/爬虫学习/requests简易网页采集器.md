## requests巩固深入介绍

​	**在搜狗当中录入关键字：**爬取关键字的页面的数据

​		**实战代码：**

```python
import requests
if __name__ == "__main__":
    #step 1:指定URL
    #step 2:发起请求
    #get方法会返回一个响应对象
    #step 3:获取响应数据,text返回的是字符串形式的响应数据
    #step 4:持久化存储,需要将pagetext存储


    #UA：User-Agent(请求载体的身份标识)
    #UA检测：门户网站的服务器会检测对应请求的载体身份标识为某一浏览器，
    #说明该请求是一个正常的请求。但是如果请求的身份标识，则该请求为不正常的请求(爬虫)
    #则服务器很有可能拒绝该次请求。
    #UA伪装(反爬策略)：让爬虫对应的请求载体的身份标识伪装成某一浏览器的身份标识
    #UA伪装：将对应的User-Agent封装到一个字典中
    headers ={
        'User-Agent':'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/108.0.0.0 Safari/537.36 Edg/108.0.1462.54'
    }
    url = 'https://www.sogou.com/web'
    # 处理URL携带的参数，把它设为一个动态值  :封装到字典中
    kw = input('enter a word:')
    #字典
    param = {
        'query':kw
    }
    r = requests.get(url=url,params=param,headers=headers)
    pagetext = r.text
    print(pagetext)
    fileNmae = kw+'.html'
    with open(fileNmae,'w',encoding='utf-8') as fp:
        fp.write(pagetext)
    print(fileNmae,"保存成功！！")
```





