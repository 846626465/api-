# 智能录音app
发布日期 | 2019年12月4日|
|  ----  | ----  |
|产品名称  | 智能录音app|
|文件现状  | 未完成|
|文件的主人  | 李铮|
|领头的设计师  | 李铮|
|领头的开发者  | 李铮|
|迭代版本  | 1.0|
## 需求描述
- 相信很多人在参加一些重要会议、讲座等情景下，都会下意识使用手机进行录音，后期再对录音内容进行重听，摘取重要内容进行笔记。如果有一款产品，可以直接对录音文件进行语音识别，返回文字内容，并且可以保存云端，相应会受到很多人的欢迎。

## 加值宣言
- 这款智能录音app采用了百度的语音转写，文本纠错，新闻摘要和机器翻译API技术来对app的功能进行加值和优化，在采用语音转写将语音转化为文本的同时，结合文本纠错技术，提高语音转化文本的准确率，除此之外，结合新闻摘要的技术，可自动提取录音文本的摘要，如果录音的语言为其他国家语言，则会利用文本翻译技术，将返回的文字内容进行文本翻译。

## 核心价值（最小可行性产品）
- 提供给用户基本的语音转写服务。

## 用户
学生、工作党、会议记录者、记者

## 用户痛点分析
- 今天老板开了个会议，精神状态不好先对会议内容进行了录音，晚上在对老板讲的内容进行笔记的时候，想找一段会议高潮的内容进行摘取，可以是拖了好久的播放进度条都没有找到那一段的位置。
- 今天开会缺席了，让同事录了段音发我，想快速地了解一下会议的大致内容主题是什么。
- 今天听了一个老外的讲座，半懂半不懂，录了个音，晚上回来整理的时候，想查阅某句话的意思，奈何听力不佳，无法准确拼写查阅。


## 可用API
1. 百度音频文件转写API/ Azure语音转文本API
2. 百度文本纠错API/Azure必应拼写检查API
3. 百度新闻摘要API
4. 百度文本翻译API/ Azure文本翻译API

## 需求列表与人工智能API加值
标题  | 用户案例  | 重要程度|
|  ----  | ----  |  ---- |
音频文件转写  | 用户想对录音的内容进行笔记  | 重要|
百度文本纠错API  | 用户感觉转写的表达结果不准确 | 重要|
百新闻摘要  | 用户想快速地了解大致内容主题  | 次重要|
文本翻译  | 用户想对外语录音进行翻译  | 次重要|

## API运用可行性展示：
### API1.使用水平
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
### API2.使用比较分析
- 小结

对比项  | 百度语音转写API  | 讯飞语音转写API|
|  ----  | ----  |  ---- |
效率  | 速度快  | 速度慢|
精确度 | 断句效果更好 | 断句效果不太好|
性价比 | 1.15-2.20元/小时 | 4.9-9.90元/小时|


