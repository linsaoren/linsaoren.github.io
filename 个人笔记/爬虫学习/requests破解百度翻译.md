## requests破解百度翻译

### 查询其url、请求方式、以及响应数据的形式（按F12）

#### 实战代码：

```python
# post请求（携带了参数）
# 响应数据是一组json数据
import requests
import json
if __name__ == "__main__":
    #UA伪装
    headers = {
        'User-Agent':'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/108.0.0.0 Safari/537.36 Edg/108.0.1462.54'
    }
    #指定URL
    url = 'https://fanyi.baidu.com/sug'
    #post 请求参数处理 ， 同get请求的一致
    k = input('enter a word:')
    data = {
        'kw': k
    }
    #请求发送
    r = requests.post(url = url, data = data , headers = headers)
    #获取响应数据
    r.json()  #直接返回的是一个obj（对象）,如果确认服务器响应数据是json类型的才可以使用json（）
    #可以在抓包工具那里看是不是json数据
    dogobj = r.json()
    print(dogobj)
    #进行持久化存储(直接存到json文本当中)
    fileName = k+'.json'
    fp = open(fileName,'w',encoding='utf-8')
    json.dump(dogobj,fp=fp,ensure_ascii=False)
    print("数据爬取结束!!!!!")

```

