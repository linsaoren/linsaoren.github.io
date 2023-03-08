## requests

​		1.urllib模块

​		2.requests模块

### request模块

​	requests模块：python中原生的一款基于网络请求的模块，功能非常强大，简单便捷，效率极高。

​	作用：模拟浏览器发请求。

#### requests模块如何使用（编码流程）：

​		1.指定URL

​		2.发起一个http或者https请求

​		3.获取想要的数据

​		4.持久化存储（存储的响应数据，所爬取到的数据）

##### 环境的安装：

​		安装requests

##### 实战编码：

​		需求：爬取搜狗首页的页面数据

```python
import requests
if __name__ == "__main__":
    #step 1:指定URL
    url='https://www.sogou.com/'
    #step 2:发起请求
    #get方法会返回一个响应对象
    r = requests.get(url=url)
    #step 3:获取响应数据,text返回的是字符串形式的响应数据
    pagetext = r.text
    print(pagetext)
    #step 4:持久化存储,需要将pagetext存储
    with open('./sougou.html','w',encoding='utf-8') as fp:
        fp.write(pagetext)
    print("爬取数据结束！！！")
```

