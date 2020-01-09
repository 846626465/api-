# 目录
- [智能记录助手](#智能记录助手)
- [价值主张设计](#价值主张设计)
    - [20*20ppt文档下载区](#20*20ppt文档下载区)
    - [需求描述](#需求描述)
    - [加值宣言](#加值宣言)
    - [核心价值](#核心价值)
    - [目标](#目标)
    - [用户](#用户)
    - [需求列表与人工智能API加值](#需求列表与人工智能API加值)
    - [具体应用场景](#具体应用场景)
    - [用户痛点分析](#用户痛点分析)
- [原型设计](#原型设计)
    - [使用者交互与设计](#使用者交互与设计)
    - [交互及界面设计](#交互及界面设计)
    - [产品结构图](#产品结构图)
    - [功能结构图](#功能结构图)
    - [信息结构图](#信息结构图)
- [API运用可行性展示](#API运用可行性展示)
    - [可用API](#可用API)
    - [使用水平](#使用水平)
        - [语音识别API使用测试](#音识别API使用测试)
        - [文本纠错API使用测试](#文本纠错API使用测试)
        - [文字识别API使用测试](#文字识别API使用测试)
        - [文本翻译API使用测试](#文本翻译API使用测试)
    - [API使用比较分析](#API使用比较分析)
        - [语音识别API使用比较分析](#语音识别API使用比较分析)
        - [文本纠错API使用比较分析](#文本纠错API使用比较分析)
        - [文字识别API使用比较分析](#文字识别API使用比较分析)
        - [文本翻译API使用比较分析](#文本翻译API使用比较分析)
    - [总结](#总结)
- [人工智能概率性](#人工智能概率性)
- [使用后风险报告](#使用后风险报告)
# 智能记录助手
发布日期 | 2019年12月4日|
|  ----  | ----  |
|产品名称  | 智能记录助手|
|文件现状  | 未完成|
|文件的主人  | 李铮|
|领头的设计师  | 李铮|
|领头的开发者  | 李铮|
|迭代版本  | 1.0|
# 价值主张设计
## [20*20ppt文档下载区](https://raw.githubusercontent.com/846626465/api-/master/%E6%99%BA%E8%83%BD%E8%AE%B0%E5%BD%95%E5%8A%A9%E6%89%8B.pptx)
## 需求描述
- 相信很多人在参加一些重要会议、讲座、课堂等情景下，都会用到录音或者是拍照将听到的，看到的内容记录下来，后期再对记录下来的内容进行整理笔记，如果有一款产品，可以直接对录音文件，照片文件进行语音识别和文字识别，返回文字内容，并且提供翻译的功能，想应会受到很多人的欢迎。
## 加值宣言
- 这款智能记录助手产品采用了语音转写，文本纠错，文字识别和机器翻译API技术来对产品的功能进行加值和优化，来提高用户记录的效率。
- **主要**
    - 运用了语音转写API技术，用户可以通过选择想要转写的音频，智能记录助手会给用户返回音频对应的文本内容。
    - 运用了文字识别API技术，用户可选择上传图片来进行图像文字提取，也可以通过智能记录助手拍照实时返回文字内容。
- **辅助**
    - 利用文本纠错API技术来对用户编辑的笔记进行文本纠错，从而提高用户的使用体验和工作效率。
    - 利用机器翻译API技术来对返回的文本内容进行文本的翻译，辅助用户进行笔记整理。
## 核心价值
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
计算机视觉API  | 用户想提取出图片内的文本信息 | 重要|
文本纠错API  | 相对自己编辑笔记的错误进行纠正  | 次重要|
文本翻译API  | 用户想对外语录音进行翻译  | 次重要|
## 具体应用场景
- 场景一：小明今天老板开了个会议，精神状态不好先对会议内容进行了录音，晚上在对老板讲的内容进笔记的时候，将会议音频导入智能记录助手转换为文本信息，并且直接在软件内进行文字编辑、整理重要内容，最后保存在智能记录助手的笔记本中。
- 场景二：小明今天这堂课老师的ppt内容不错，上课的时候拍了很多照片，课后把图片导入智能记录助手中，快速地提取出了图片中的文字内容，节省了不少手动敲打的时间。
- 场景三：小明今天听了一个老外的讲座，半懂半不懂，录了个音，晚上回来整理的时候，将讲座音频导入智能记录助手转换为文本信息后，点击了其附属的一个翻译的功能，大致了解了讲座的具体内容。
- 场景四：小明在对音转文本进行编辑的时候，出现了错别字，文本纠错功能自动为其打上了下划线提示，最后小明及时对其进行了更正。
# 原型设计
## 使用者交互与设计
- [原型文档展示](http://nfunm042.gitee.io/new-api)
- [原型文档下载区](https://gitee.com/NFUNM042/new-api.git)
## 交互及界面设计
- 录音主页面
- ![录音主页面](https://github.com/846626465/api-/blob/master/%E5%8E%9F%E5%9E%8B%E5%9B%BE/luyin.png)
- 图像识别主页面
- ![图像识别主页面](https://github.com/846626465/api-/blob/master/%E5%8E%9F%E5%9E%8B%E5%9B%BE/tuxiang.png)
- 录音转文本功能模块
- ![录音转文本功能模块](https://github.com/846626465/api-/blob/master/%E5%8E%9F%E5%9E%8B%E5%9B%BE/ypzx.png)
- 翻译功能模块
- ![翻译功能模块](https://github.com/846626465/api-/blob/master/%E5%8E%9F%E5%9E%8B%E5%9B%BE/fanyi.png)
## 产品结构图
- ![产品结构](https://github.com/846626465/api-/blob/master/原型图/产品结构图.png)
## 功能结构图
- ![产品结构](https://github.com/846626465/api-/blob/master/原型图/产品功能结构图.png)
## 信息结构图
- ![产品结构](https://github.com/846626465/api-/blob/master/原型图/产品信息结构.png)
# API运用可行性展示
## 可用API
1. 百度音频文件转写API/ 讯飞语音转文本API
2. 百度文本纠错API/聚合文本纠错API/Azure必应拼写检查API
3. 通用文字识别API/Azure计算机视觉API
4. 百度文本翻译API/讯飞文本翻译API
## 使用水平
### 语音识别API使用测试
1. 讯飞开发平台-语音识别API
- 接口描述：语音转写（Long Form ASR）基于深度全序列卷积神经网络，将长段音频（5小时以内）数据转换成文本数据，为信息处理和数据挖掘提供基础。
- 接口地址：http://api.xfyun.cn/v1/service/v1/iat
- 请求方式:POST
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
- 请求方式:POST
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
### 文本纠错API使用测试
1. 百度开发平台-文本纠错API
- 接口描述：识别输入文本中有错误的片段，提示错误并给出正确的文本结果。支持短文本、长文本、语音等内容的错误识别，纠错是搜索引擎、语音识别、内容审查等功能更好运行的基础模块之一。
- 接口地址：https://aip.baidubce.com/rpc/2.0/nlp/v1/ecnet
- 请求方式:POST
- 输入：
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
- 输出：
```
原文： 汽车形式在这条道路上
纠错后： 汽车行驶在这条道路上
Score： 0.982835
```
- 分析：当尝试输入文本为英文时，百度的文本纠错API无法识别，中文文本纠错置信度较高。
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
- 分析：当尝试输入文本为中文时，Azure必应拼写检查API无法识别，英文文本纠错置信度较高。
3. 聚合数据-文本纠错API
- 接口描述：向远程服务上传整段语音进行识别 ，输入音频文件，输出文本信息。
- 接口地址：http://apis.juhe.cn/ecnetAnti/index
- 请求方式：POST/GET
- 在线功能测试
- ![聚合数据](https://github.com/846626465/api-/blob/master/%E6%95%B0%E6%8D%AE%E8%81%9A%E5%90%88-%E6%96%87%E6%9C%AC%E7%BA%A0%E9%94%99.png)

### 文字识别API使用测试
1. Azure开发平台-计算机视觉API
- 接口描述：可以使用计算机视觉读取 API 将印刷文本和手写文本从图像中提取到计算机可读的字符流。 该读取 API 使用最新的模型，适用于各种表面和背景（如收据、海报、名片、信件和白板）上的文本。 目前，英语是唯一受支持的语言。
- 请求方式：POST/GET
- 输入：
```
import requests
import time
# If you are using a Jupyter notebook, uncomment the following line.
# %matplotlib inline
import matplotlib.pyplot as plt
from matplotlib.patches import Polygon
from PIL import Image
from io import BytesIO
import os,sys
# Add your Computer Vision subscription key and endpoint to your environment variables.
if 'COMPUTER_VISION_SUBSCRIPTION_KEY' in os.environ:
    subscription_key = os.environ['COMPUTER_VISION_SUBSCRIPTION_KEY']
else:
    print("\nSet the COMPUTER_VISION_SUBSCRIPTION_KEY environment variable.\n**Restart your shell or IDE for changes to take effect.**")
    sys.exit()

if 'COMPUTER_VISION_ENDPOINT' in os.environ:
    endpoint = os.environ['COMPUTER_VISION_ENDPOINT']

text_recognition_url = endpoint + "vision/v2.0/read/core/asyncBatchAnalyze"

# Set image_url to the URL of an image that you want to analyze.
image_url = "http://n1.itc.cn/img8/wb/smccloud/recom/2015/10/08/144428390443326171.JPEG"

headers = {'Ocp-Apim-Subscription-Key': subscription_key}
data = {'url': image_url}
response = requests.post(
    text_recognition_url, headers=headers, json=data)
response.raise_for_status()

# Extracting text requires two API calls: One call to submit the
# image for processing, the other to retrieve the text found in the image.

# Holds the URI used to retrieve the recognized text.
operation_url = response.headers["Operation-Location"]

# The recognized text isn't immediately available, so poll to wait for completion.
analysis = {}
poll = True
while (poll):
    response_final = requests.get(
        response.headers["Operation-Location"], headers=headers)
    analysis = response_final.json()
    print(analysis)
    time.sleep(1)
    if ("recognitionResults" in analysis):
        poll = False
    if ("status" in analysis and analysis['status'] == 'Failed'):
        poll = False

polygons = []
if ("recognitionResults" in analysis):
    # Extract the recognized text, with bounding boxes.
    polygons = [(line["boundingBox"], line["text"])
                for line in analysis["recognitionResults"][0]["lines"]]

# Display the image and overlay it with the extracted text.
plt.figure(figsize=(15, 15))
image = Image.open(BytesIO(requests.get(image_url).content))
ax = plt.imshow(image)
for polygon in polygons:
    vertices = [(polygon[0][i], polygon[0][i+1])
                for i in range(0, len(polygon[0]), 2)]
    text = polygon[1]
    patch = Polygon(vertices, closed=True, fill=False, linewidth=2, color='y')
    ax.axes.add_patch(patch)
    plt.text(vertices[0][0], vertices[0][1], text, fontsize=20, va="top")

```
- 输出：
![Azure](https://github.com/846626465/api-/blob/master/Azure%E6%96%87%E6%9C%AC%E8%AF%86%E5%88%AB.png)

2. 百度开发平台-通用文字识别API
- 接口描述：基于业界领先的深度学习技术，提供多场景、多语种、高精度的整图文字检测和识别服务
- 接口地址：https://aip.baidubce.com/rest/2.0/ocr/v1/general_basic
- HTTP方法: POST
- 输入中文图片：
- ![百度](https://github.com/846626465/api-/blob/master/demo3.png)
- 输入代码：
```
import urllib3,base64
from urllib.parse import urlencode
access_token='24.f533ed26aae0977637847fc313219a89.2592000.1579694332.282335-18092334'
http=urllib3.PoolManager()
url='https://aip.baidubce.com/rest/2.0/ocr/v1/general?access_token='+access_token
f = open('D:/demo3.png','rb')
#参数image：图像base64编码
img = base64.b64encode(f.read())
params={'image':img}
#对base64数据进行urlencode处理
params=urlencode(params)
request=http.request('POST', 
                      url,
                      body=params,
                      headers={'Content-Type':'application/x-www-form-urlencoded'})

#对返回的byte字节进行处理。Python3输出位串，而不是可读的字符串，需要进行转换
result = str(request.data,'utf-8')
print(result)
```
- 输出：
```
('{"log_id": 3132648805747643351, "words_result_num": 7, "words_result": '
 '[{"location": {"width": 415, "top": 336, "left": 492, "height": 53}, '
 '"words": "Ihttp://www.baidu.comm"}, {"location": {"width": 576, "top": 355, '
 '"left": 540, "height": 93}, "words": "北京市海淀区上地十街10号100085"}, {"location": '
 '{"width": 897, "top": 377, "left": 553, "height": 124}, "words": "No. 10 '
 'Shangdi 10th Street, Haidian District, Beijing 100085"}, {"location": '
 '{"width": 427, "top": 472, "left": 643, "height": 66}, "words": '
 '"+8610-5292888"}, {"location": {"width": 173, "top": 451, "left": 1052, '
 '"height": 49}, "words": "86105992"}, {"location": {"width": 77, "top": 444, '
 '"left": 1222, "height": 34}, "words": "0900"}, {"location": {"width": 77, '
 '"top": 504, "left": 564, "height": 39}, "words": "Tel:"}]}')
```
- 输入中文图片：
- ![百度](https://github.com/846626465/api-/blob/master/demo4.png)
- 输入代码：
```
import urllib3,base64
from urllib.parse import urlencode
access_token='24.f533ed26aae0977637847fc313219a89.2592000.1579694332.282335-18092334'
http=urllib3.PoolManager()
url='https://aip.baidubce.com/rest/2.0/ocr/v1/general?access_token='+access_token
f = open('D:/demo4.png','rb')
#参数image：图像base64编码
img = base64.b64encode(f.read())
params={'image':img}
#对base64数据进行urlencode处理
params=urlencode(params)
request=http.request('POST', 
                      url,
                      body=params,
                      headers={'Content-Type':'application/x-www-form-urlencoded'})
#对返回的byte字节进行处理。Python3输出位串，而不是可读的字符串，需要进行转换
result = str(request.data,'utf-8')
print(result)
```
- 输出：
```
('{"log_id": 302204267115462231, "words_result_num": 11, "words_result": '
 '[{"location": {"width": 746, "top": 171, "left": 429, "height": 57}, '
 '"words": "ACKNOWLEDGEMENTS"}, {"location": {"width": 818, "top": 345, '
 '"left": 392, "height": 46}, "words": "We would like to thank all the '
 'designers and"}, {"location": {"width": 812, "top": 395, "left": 397, '
 '"height": 40}, "words": "contributors who have been involved in the"}, '
 '{"location": {"width": 819, "top": 443, "left": 393, "height": 51}, "words": '
 '"production of this book; their contributions"}, {"location": {"width": 816, '
 '"top": 495, "left": 394, "height": 41}, "words": "have been indispensable to '
 'its creation. We"}, {"location": {"width": 816, "top": 546, "left": 395, '
 '"height": 40}, "words": "would also like to express our gratitude to all"}, '
 '{"location": {"width": 826, "top": 593, "left": 390, "height": 52}, "words": '
 '"the producers for their invaluable opinions"}, {"location": {"width": 826, '
 '"top": 644, "left": 391, "height": 51}, "words": "and assistance throughout '
 'this project And to"}, {"location": {"width": 825, "top": 696, "left": 391, '
 '"height": 40}, "words": "the many others whose names are not credited"}, '
 '{"location": {"width": 821, "top": 746, "left": 395, "height": 41}, "words": '
 '"but have made specific input in this book, we"}, {"location": {"width": '
 '697, "top": 795, "left": 388, "height": 52}, "words": "thank you for your '
 'continuous support"}]}')
```



### 文本翻译API使用测试

1. 百度开发平台-文本翻译API
- 接口描述：支持28种语言实时互译，覆盖中、英、日、韩、西、法、泰、阿、俄、葡、德、意、荷、芬、丹等；同时支持28种语言的语言检测。
- HTTP方法: POST
- 输入：
```
import requests
import json
import hashlib
def md5_sign(s):
    return hashlib.md5(s.encode('utf8')).hexdigest()
def baidu_fanyi(q):
    url = "https://fanyi-api.baidu.com/api/trans/vip/translate"
    f = 'en'
    to = 'zh'
    appid = '20191223000369109'   # 自己申请
    salt = '1435660288'
    key = 'vfIEwz7sPIfIpikth_St'  # 自己申请
    finial_str = '%s%s%s%s' % (appid, q, salt, key)
    sign = md5_sign(finial_str)
    params = {
        'q': q,
        'from': f,
        'to': to,
        'appid': appid,
        'salt': salt,
        'sign': sign,
    }
    res_json = requests.get(url, params=params).json()
    res = res_json
    print(res)
if __name__ == '__main__':
    baidu_fanyi('the ones who love us never really leave us')
```
- 英文翻译中文输出：
```
{'from': 'en', 'to': 'zh', 'trans_result': [{'src': 'the ones who love us never really leave us', 'dst': '爱我们的人永远不会离开我们'}]}
```
- 中文转英文输出：
```
{'from': 'zh', 'to': 'en', 'trans_result': [{'src': '爱我们的人永远不会离开我们', 'dst': 'Those who love us will never leave us'}]}
```
2. 讯飞开发平台-文本翻译API
- 接口描述：机器翻译，基于讯飞自主研发的机器翻译引擎，已经支持包括英、日、法、西、俄等10多种语言(其中维语、藏语暂不对外提供)，效果更优质，已在讯飞翻译机上应用并取得优异成绩，详细请参照 语种列表 。通过调用该接口，将源语种文字转化为目标语种文字。
- HTTP方法: POST

- 输入：
```
# -*- coding:utf-8 -*-
import requests
import datetime
import hashlib
import base64
import hmac
import json

class get_result(object):
    def __init__(self,host):
        self.APPID = "5dff9ca8"
        self.APIKey= "846559d4c446aa4eeccf6e0a7e11bf2e"
        self.Secret = "f33d82fa4752d1ffa2d8d67b7c6993c1"
        
        # 以下为POST请求
        self.Host = host
        self.RequestUri = "/v2/ots"
        self.url="https://"+host+self.RequestUri
        self.HttpMethod = "POST"
        self.Algorithm = "hmac-sha256"
        self.HttpProto = "HTTP/1.1"

        # 设置当前时间
        curTime_utc = datetime.datetime.utcnow()
        self.Date = self.httpdate(curTime_utc)
        self.Text="the ones who love us never really leave us"
        self.BusinessArgs={
                "from": "en",
                "to": "zh",
            }
    def hashlib_256(self, res):
        m = hashlib.sha256(bytes(res.encode(encoding='utf-8'))).digest()
        result = "SHA-256=" + base64.b64encode(m).decode(encoding='utf-8')
        return result
    def httpdate(self, dt):
        """
        Return a string representation of a date according to RFC 1123
        (HTTP/1.1).

        The supplied date must be in UTC.

        """
        weekday = ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"][dt.weekday()]
        month = ["Jan", "Feb", "Mar", "Apr", "May", "Jun", "Jul", "Aug", "Sep",
                 "Oct", "Nov", "Dec"][dt.month - 1]
        return "%s, %02d %s %04d %02d:%02d:%02d GMT" % (weekday, dt.day, month,
                                                        dt.year, dt.hour, dt.minute, dt.second)
    def generateSignature(self, digest):
        signatureStr = "host: " + self.Host + "\n"
        signatureStr += "date: " + self.Date + "\n"
        signatureStr += self.HttpMethod + " " + self.RequestUri \
                        + " " + self.HttpProto + "\n"
        signatureStr += "digest: " + digest
        signature = hmac.new(bytes(self.Secret.encode(encoding='utf-8')),
                             bytes(signatureStr.encode(encoding='utf-8')),
                             digestmod=hashlib.sha256).digest()
        result = base64.b64encode(signature)
        return result.decode(encoding='utf-8')
    def init_header(self, data):
        digest = self.hashlib_256(data)
        sign = self.generateSignature(digest)
        authHeader = 'api_key="%s", algorithm="%s", ' \
                     'headers="host date request-line digest", ' \
                     'signature="%s"' \
                     % (self.APIKey, self.Algorithm, sign)
        headers = {
            "Content-Type": "application/json",
            "Accept": "application/json",
            "Method": "POST",
            "Host": self.Host,
            "Date": self.Date,
            "Digest": digest,
            "Authorization": authHeader
        }
        return headers
    def get_body(self):
        content = str(base64.b64encode(self.Text.encode('utf-8')), 'utf-8')
        postdata = {
            "common": {"app_id": self.APPID},
            "business": self.BusinessArgs,
            "data": {
                "text": content,
            }
        }
        body = json.dumps(postdata)
        return body
    def call_url(self):
        if self.APPID == '' or self.APIKey == '' or self.Secret == '':
            print('Appid 或APIKey 或APISecret 为空！请打开demo代码，填写相关信息。')
        else:
            code = 0
            body=self.get_body()
            headers=self.init_header(body)
            #print(self.url)
            response = requests.post(self.url, data=body, headers=headers,timeout=8)
            status_code = response.status_code
            #print(response.content)
            if status_code!=200:
                print("Http请求失败，状态码：" + str(status_code) + "，错误信息：" + response.text)
                print("请根据错误信息检查代码，接口文档：https://www.xfyun.cn/doc/nlp/niutrans/API.html")
            else:
                respData = json.loads(response.text)
                print(respData)
                code = str(respData["code"])
                if code!='0':
                    print("请前往https://www.xfyun.cn/document/error-code?code=" + code + "查询解决办法")
if __name__ == '__main__':
    host = "ntrans.xfyun.cn"
    gClass=get_result(host)
    gClass.call_url()

```
- 输出：
```
{'code': 0, 'data': {'result': {'from': 'en', 'to': 'zh', 'trans_result': {'dst': '爱我们的人从未真正离开我们', 'src': 'the ones who love us never really leave us'}}}, 'message': 'success', 'sid': 'ots000830f0@dx16f334b43c8a11c902'}
```
## API使用比较分析
### 语音识别API使用比较分析
对比项  | 讯飞语音转写API  | 百度语音转写API|
|  ----  | ----  |  ---- |
效率  | 速度快  | 速度慢|
精确度 | 断句效果更好 | 断句效果不太好|
性价比 | 4.9-9.90元/小时 | 1.15-2.20元/小时|
### 文字识别API使用比较分析
对比项  | Azure计算机视觉API | 百度通用文字识别API |
|  ----  | ----  |  ---- |
功能  | 可将印刷文本和手写文本从图像中提取到计算机可读的字符流，只支持的英语  | 对图片中的文字进行检测和识别，支持中、英、法、俄、西、葡、德、意、日、韩、中英混合等多语种识别，同时支持中、英、日、韩四语种的类型检测 |
精确度 | 识别精度高 | 识别精度高 |
性价比 | 0.0012元/每次 | 0.0025-0.005元/次|
### 文本翻译API使用比较分析
对比项  | 百度文本翻译API | 讯飞文本翻译API |
|  ----  | ----  |  ---- |
功能  | 支持28种语言实时互译  | 支持包括英、日、法、西、俄等10多种语言 |
精确度 | 识别精度高 | 识别精度高 |
性价比 | 49元/百万字符 | 45元/百万字符|
### 文本纠错API使用比较分析
对比项  | 百度文本纠错API  | Azure必应拼写检查API| 聚合文本纠错API |
|  ----  | ----  |  ---- |  ---- |
功能  | 仅支持中文，支持错别字、短文本、长文本、语音识别结果等多种文本内容识别与纠正  | 仅支持英文，可纠正拼写错误和识别姓名、断字、品牌名和俚语|  仅支持中文，其他功能未说明 |
精确度 | 识别精度高 | 识别精度高 |  效果一般 |
字节量 | 上限511字节 | 无标明上限 |  上限400字节 |
性价比 | 0.0025元/每次 | 0.0035元/每次|  0.0067元/次 |
### 总结
- 语音转写API在投资条件允许的情况下，可优先考虑讯飞语音转写API，价格更高，效果更好。
- 文本纠错API在纠错中文文本的时候推荐使用百度文本纠错API，在纠错英文文本的时候推荐使用Azure必应拼写检查API，性价比较高。
- 文字识别API鉴于Azure的语言受限，建议考虑百度通用文字识别API。
- 文本翻译API，经济条件允许的情况下，优先考虑百度文本翻译API，因为其提供的翻译语种更为全面。

## 人工智能概率性
- 文本纠错API存在着部分无法识别的文本错误。
- 录音转写API在声音嘈杂的情况下可能无法精确识别语音内容。
- 图片识别API在图片画质较低的情况，会无法准确识别图片的文字内容。
## API使用后风险报告
- 讯飞语音识别错误情况处理方式：
1. 通过机器学习等提高语音识别的准确率。
2. 建立用户个人的语音库。
3. 向api提供商签署合同，错误数过多，要求赔偿，如果不将错误率控制在一定范围则另寻其他api提供商。
- 百度通用文字识别错误情况处理方式：

1. 通过机器图像学习，用户协助方式等提高图片文章识别率。
2. 向api提供商签署合同，错误数过多，要求赔偿，如果不将错误率控制在一定范围则另寻其他api提供商。

- 百度语法分析错误情况处理方式：

1. 提供用户手动改正的窗口，学习用户改正后的正确结果，提高语法分析的准确率。

2. 向api提供商签署合同，错误数过多，要求赔偿，如果不将错误率控制在一定范围则另寻其他api提供商。
