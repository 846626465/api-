# 智能记录助手
发布日期 | 2019年12月4日|
|  ----  | ----  |
|产品名称  | 智能记录助手|
|文件现状  | 未完成|
|文件的主人  | 李铮|
|领头的设计师  | 李铮|
|领头的开发者  | 李铮|
|迭代版本  | 1.0|
# 价值主张
## 需求描述
- 相信很多人在参加一些重要会议、讲座、课堂等情景下，都会用到录音或者是拍照将听到的，看到的内容记录下来，后期再对记录下来的内容进行整理笔记，如果有一款产品，可以直接对录音文件，照片文件进行语音识别和文字识别，返回文字内容，并且提供翻译的功能，想应会受到很多人的欢迎。

## 加值宣言
- 这款智能记录助手产品采用了语音转写，文本纠错，文字识别和机器翻译API技术来对产品的功能进行加值和优化，来提高用户记录的效率。
- 主要
    - 运用了语音转写API技术，用户可以通过选择想要转写的音频，智能记录助手会给用户返回音频对应的文本内容。
    - 运用了文字识别API技术，用户可选择上传图片来进行图像文字提取，也可以通过智能记录助手拍照实时返回文字内容。
- 辅助
    - 利用文本纠错API技术来对用户编辑的笔记进行文本纠错，从而提高用户的使用体验和工作效率。
    - 利用机器翻译API技术来对返回的文本内容进行文本的翻译，辅助用户进行笔记整理。


## 核心价值（最小可行性产品）
- 提供给用户基本的语音转写和图像文本提取服务。

## 目标

一个为用户提供轻记录、便整理功能的智能记录助手。

## 用户
学生、工作党、会议记录者、记者、新闻编辑者
## 用户痛点分析
- 场景一：用户想快速地了解一段录音的内容。
- 场景二：用户想将录音的内容转换成文本内容进行笔记整理。
- 场景三：用户想快速地摘取出图片的文字信息。
- 场景四：用户想对录音的内容进行一个文本上的翻译。
- 场景五：相对自己编辑笔记的时候出现的错误进行纠正。

## 需求列表与人工智能API加值
标题  | 用户案例  | 重要程度|
|  ----  | ----  |  ---- |
音频文件转写API  | 用户想对录音的内容进行笔记  | 重要|
文字识别API  | 用户想提取出图片内的文本信息 | 重要|
文本纠错API  | 相对自己编辑笔记的错误进行纠正  | 次重要|
文本翻译API  | 用户想对外语录音进行翻译  | 次重要|

### 具体应用场景
- 场景一：小明今天老板开了个会议，精神状态不好先对会议内容进行了录音，晚上在对老板讲的内容进笔记的时候，将会议音频导入智能记录助手转换为文本信息，并且直接在软件内进行文字编辑、整理重要内容，最后保存在智能记录助手的笔记本中。
- 场景二：小明今天这堂课老师的ppt内容不错，上课的时候拍了很多照片，课后把图片导入智能记录助手中，快速地提取出了图片中的文字内容，节省了不少手动敲打的时间。
- 场景三：小明今天听了一个老外的讲座，半懂半不懂，录了个音，晚上回来整理的时候，将讲座音频导入智能记录助手转换为文本信息后，点击了其附属的一个翻译的功能，大致了解了讲座的具体内容。
- 场景四：小明在对音转文本进行编辑的时候，出现了错别字，文本纠错功能自动为其打上了下划线提示，最后小明及时对其进行了更正。

# 原型
## 使用者交互与设计（axure产品原型）
- 原型文档展示
- 原型文档下载区
## 交互及界面设计
- 首页
- 个人页
- 产品结构图
- 功能结构图
- 信息结构图
- 产品流程图
## API运用可行性展示：

### 可用API
1. 百度音频文件转写API/ 讯飞语音转文本API
2. 百度文本纠错API/聚合文本纠错API/Azure必应拼写检查API
3. 百度文字识别API/Azure识别API
4. 百度文本翻译API/ Azure文本翻译API

### API1.使用水平
#### 语音识别API使用测试
1. 讯飞开发平台-语音识别API
- 接口描述：语音转写（Long Form ASR）基于深度全序列卷积神经网络，将长段音频（5小时以内）数据转换成文本数据，为信息处理和数据挖掘提供基础。
- 接口地址：http://api.xfyun.cn/v1/service/v1/iat
- 请求方式:POST  http[s]://raasr.xfyun.cn/api/prepare
- 输入：
```
#!/usr/bin/python
# -*- coding: UTF-8 -*-
import urllib.request
import time
import urllib
import json
import hashlib
import base64
from urllib import parse

def main():
    f = open("AUDIO_PATH", 'rb')
    file_content = f.read()
    base64_audio = base64.b64encode(file_content)
    body = parse.urlencode({'audio': base64_audio})

    url = 'http://api.xfyun.cn/v1/service/v1/iat'
    api_key = 'API_KEY'
    param = {"engine_type":"sms16k","aue":"raw"}

    x_appid = 'APPID'
    json_str = json.dumps(param).replace(' ', '')
    print('json_str:{}'.format(json_str))
    x_param = base64.b64encode(bytes(json_str, 'ascii'))
    x_time = int(int(round(time.time() * 1000)) / 1000)
    x_checksum_str = api_key + str( x_time ) + str(x_param)[2:-1]
    print('x_checksum_str:[{}]'.format(x_checksum_str))
    x_checksum = hashlib.md5(x_checksum_str.encode(encoding='ascii')).hexdigest()
    print('x_checksum:{}'.format(x_checksum))
    x_header = {'X-Appid': x_appid,
                'X-CurTime': x_time,
                'X-Param': x_param,
                'X-CheckSum': x_checksum}

    start_time = time.time()
    req = urllib.request.Request(url, bytes(body, 'ascii'), x_header)
    result = urllib.request.urlopen(req)
    result = result.read()
    print( "used time: {}s".format( round( time.time() - start_time, 2 ) ) )
    print('result:'+str(result.decode(encoding='UTF8')))
    return

if __name__ == '__main__':
    main() 
```
- 输出：
```
json_str:{"engine_type":"sms16k","aue":"raw"}

used time: 0.82s
result:{"code":"0","data":"特别是跨省区电网超计划用电，不仅损害自己，也损害别人，损害电网，损害国家。","desc":"success","sid":"zat006392f7@ch6b010ed8627f3d3700"}
```

2. 百度AI平台-语音识别API
- 接口描述：向远程服务上传整段语音进行识别 ，输入音频文件，输出文本信息。
- 接口地址以及SDK调用：AipSpeech是语音识别的Python SDK客户端，为使用语音识别的开发人员提供了一系列的交互方法。 
- 输入：
```
#先pip install baidu-aip
from aip import AipSpeech
import time

APP_ID = 'APP_ID'
API_KEY = 'API_KEY'
SECRET_KEY = 'SECRET_KEY'

client = AipSpeech(APP_ID, API_KEY, SECRET_KEY)

def get_file_content(filePath):
    with open(filePath, 'rb') as fp:
        return fp.read()

# 识别本地文件
start_time = time.time()
ret = client.asr(get_file_content('./aideo_files/A2_58.wav'), 'pcm', 16000, {
    'dev_pid': 1537,
})
used_time = time.time() - start_time

print( "used time: {}s".format( round( time.time() - start_time, 2 ) ) )
print('ret:{}'.format(ret))
```
- 输出：
```
used time: 8.18s
ret:{'corpus_no': '6592465378279780417', 'err_msg': 'success.', 'err_no': 0, 'result':
['特别是跨省区电网超计划用电，不仅损害自己也损害别人损害电网损害国家，'], 'sn': '148955205071534927957'}

```
#### 语音识别API使用比较分析
- 小结

对比项  | 讯飞语音转写API  | 百度语音转写API|
|  ----  | ----  |  ---- |
效率  | 速度快  | 速度慢|
精确度 | 断句效果更好 | 断句效果不太好|
性价比 | 1.15-2.20元/小时 | 4.9-9.90元/小时|

#### 文本纠错API使用测试
1. 百度开发平台-文本纠错API
- 接口描述：识别输入文本中有错误的片段，提示错误并给出正确的文本结果。支持短文本、长文本、语音等内容的错误识别，纠错是搜索引擎、语音识别、内容审查等功能更好运行的基础模块之一。
- 接口地址：https://aip.baidubce.com/rpc/2.0/nlp/v1/ecnet
- HTTP方法: POST
输入：
```
# -*- coding: utf-8 -*-

import urllib
import json
#client_id 为官网获取的AK， client_secret 为官网获取的SK
client_id = '为官网获取的AK'
client_secret ='为官网获取的SK'

#获取token
def get_token():
    host = 'https://aip.baidubce.com/oauth/2.0/token?grant_type=client_credentials&client_id=' + client_id + '&client_secret=' + client_secret
    request = urllib.request.Request(host)
    request.add_header('Content-Type', 'application/json; charset=UTF-8')
    response = urllib.request.urlopen(request)
    token_content = response.read()
    if token_content:
        token_info = json.loads(token_content)
        token_key = token_info['access_token']
    return token_key


def txt_correction(content):
    print('原文：', content)
    token = get_token()
    url = 'https://aip.baidubce.com/rpc/2.0/nlp/v1/ecnet'
    params = dict()
    params['text'] = content
    params = json.dumps(params).encode('utf-8')
    access_token = token
    url = url + "?access_token=" + access_token
    request = urllib.request.Request(url=url, data=params)
    request.add_header('Content-Type', 'application/json')
    response = urllib.request.urlopen(request)
    content = response.read()
    if content:
        content = content.decode('GB2312')
        data = json.loads(content)

        item = data['item']
        print('纠错后：', item['correct_query'])
        print('Score：', item['score'])


txt_correction('汽车形式在这条道路上')
```
输出：
```
原文： 汽车形式在这条道路上
纠错后： 汽车行驶在这条道路上
Score： 0.982835
```
2. Azure-必应拼写检查API
- 功能描述：帮助用户更正拼写错误、识别姓名、 品牌名和俚语之间的不同之处，并在键入的同时理解同音异义词。
- 输入：
```
import requests
import json
api_key = "511910090b83442793ddded0f2d70cd4"
example_text = "Hollo, wrld" # the text to be spell-checked
endpoint = "https://api.cognitive.microsoft.com/bing/v7.0/SpellCheck"
data = {'text': example_text}
params = {
    'mkt':'zh-cn',
    'mode':'proof'
    }
headers = {
    'Content-Type': 'application/x-www-form-urlencoded',
    'Ocp-Apim-Subscription-Key': api_key,
    }
response = requests.post(endpoint, headers=headers, params=params, data=data)
json_response = response.json()
print(json.dumps(json_response, indent=4))
```
- 输出：
```
{
   "_type": "SpellCheck",
   "flaggedTokens": [
      {
         "offset": 0,
         "token": "Hollo",
         "type": "UnknownToken",
         "suggestions": [
            {
               "suggestion": "Hello",
               "score": 0.9115257530801
            },
            {
               "suggestion": "Hollow",
               "score": 0.858039839213461
            },
            {
               "suggestion": "Hallo",
               "score": 0.597385084464481
            }
         ]
      },
      {
         "offset": 7,
         "token": "wrld",
         "type": "UnknownToken",
         "suggestions": [
            {
               "suggestion": "world",
               "score": 0.9115257530801
            }
         ]
      }
   ]
}
```
3. 聚合数据-文本纠错API
- 接口描述：向远程服务上传整段语音进行识别 ，输入音频文件，输出文本信息。
- 接口地址：http://apis.juhe.cn/ecnetAnti/index
- 请求方式：POST/GET
- 输入：
- 输出：
```
{
	"reason":"success",
	"result":{
		"text":"汽车形式在这条道路上",
		"data":[
			{
				"ori":"汽车形式",
				"correct":"汽车行驶",
				"start_pos":1,
				"end_pos":4
			}
		],
		"score":0.982835
	},
	"error_code":0
}
```
#### 文本纠错API使用比较分析
- 小结

对比项  | 百度文本纠错API  | Azure必应拼写检查API| 聚合文本纠错API |
|  ----  | ----  |  ---- |  ---- |
功能  | 仅支持中文，支持错别字、短文本、长文本、语音识别结果等多种文本内容识别与纠正  | 仅支持英文，可纠正拼写错误和识别姓名、断字、 品牌名和俚语|  仅支持中文，其他功能未说明 |
精确度 | 识别精度高 | 识别精度高 |  效果一般 |
字节量 | 上限511字节 | 无标明上限 |  上限400字节 |
性价比 | 0.0025元/每次 | 0.0035元/每次|  0.0067元/次 |
