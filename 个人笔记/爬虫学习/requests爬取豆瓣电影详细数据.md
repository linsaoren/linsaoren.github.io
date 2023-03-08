## requests爬取豆瓣电影详细数据

### 实战代码：

```python
import requests
import json
if __name__ == "__main__":
    #UA伪装
    headers ={
        'User-Agent':'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/108.0.0.0 Safari/537.36 Edg/108.0.1462.54'
    }
    #导入URL
    url = 'https://movie.douban.com/j/chart/top_list'
    param = {
        'type':'24',
        'interval_id':'100:90',
        'acting':'',
        'start':'1',#开始的位置（从哪里哪里开始）
        'limit':'20',#结束的位置（一次请求取出的东西）
    }
    #发起请求
    r = requests.get(url = url,params=param,headers=headers)
    #获取响应数据
    listdata = r.json()
    #持久化存储
    fp = open('./douban.json','w',encoding='utf-8')
    json.dump(listdata,fp=fp,ensure_ascii=False)
    print("爬取结束！！！")

```

