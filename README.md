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
- 这款智能录音app采用了百度的语音识别，文本纠错，新闻摘要和机器翻译技术来对app的功能进行加值和优化，在采用语音识别将语音转化为文本的同时，结合文本纠错技术，提高语音转化文本的准确率，除此之外，结合新闻摘要的技术，可自动提取录音文本的摘要，如果录音的语言为其他国家语言，则会利用文本翻译技术，将返回的文字内容进行文本翻译。

## 核心价值（最小可行性产品）
- 智能录音app以语音转写的功能为主，同时也提供了提取摘要和文本翻译的功能，这很大程度上解决了人们对录音内容进行整理的困难，提高了人们的工作效率。

## 用户痛点分析
- 今天老板开了个会议，精神状态不好先对会议内容进行了录音，晚上在对老板讲的内容进行笔记的时候，想找一段会议高潮的内容进行摘取，可以是拖了好久的播放进度条都没有找到那一段的位置。
- 今天开会缺席了，让同事录了段音发我，想快速地了解一下会议的大致内容主题是什么。
- 今天听了一个老外的讲座，半懂半不懂，录了个音，晚上回来整理的时候，想查阅某句话的意思，奈何听力不佳，无法准确拼写查阅。

## 可用API
1. 百度音频文件转写API/ Azure语音转文本API（分为批量听录和对话听录（适合对话交流的场景））
2. 百度文本纠错API/Azure必应拼写检查API
3. 百度新闻摘要API
4. 百度文本翻译API/ Azure文本翻译API
## 需求列表与人工智能API加值
标题  | 用户案例  | 重要程度|
|  ----  | ----  |  ---- |
音频文件转写  | 录音的内容进行笔记  | 很重要|
百新闻摘要  | 想快速地了解大致内容主题  | 重要|
文本翻译  | 想对外语录音进行翻译  | 重要|
## 人工智能概率性与用户痛点
- 录音太模糊，导致识别的准确率低
- 外语口语重，导致识别的准确率低
- 录音内容过于口语化，导致摘要的准确率低
## 产品功能结构图
![avatar](https://github.com/846626465/api-/blob/master/%E6%99%BA%E8%83%BD%E5%BD%95%E9%9F%B3app.png)

## API 产品使用关键AI或机器学习之API的输出入展示
- 语音转写
```
# -*- coding: utf-8 -*-
import os
import time
import threading
import ali_speech
from ali_speech.callbacks import SpeechTranscriberCallback
from ali_speech.constant import ASRFormat
from ali_speech.constant import ASRSampleRate
class MyCallback(SpeechTranscriberCallback):
    """
    构造函数的参数没有要求，可根据需要设置添加
    示例中的name参数可作为待识别的音频文件名，用于在多线程中进行区分
    """
    def __init__(self, name='default'):
        self._name = name
    def on_started(self, message):
        print('MyCallback.OnRecognitionStarted: %s' % message)
    def on_result_changed(self, message):
        print('MyCallback.OnRecognitionResultChanged: file: %s, task_id: %s, result: %s' % (
            self._name, message['header']['task_id'], message['payload']['result']))
    def on_sentence_begin(self, message):
        print('MyCallback.on_sentence_begin: file: %s, task_id: %s, sentence_id: %s, time: %s' % (
            self._name, message['header']['task_id'], message['payload']['index'], message['payload']['time']))
    def on_sentence_end(self, message):
        print('MyCallback.on_sentence_end: file: %s, task_id: %s, sentence_id: %s, time: %s, result: %s' % (
            self._name,
            message['header']['task_id'], message['payload']['index'],
            message['payload']['time'], message['payload']['result']))
    def on_completed(self, message):
        print('MyCallback.OnRecognitionCompleted: %s' % message)
    def on_task_failed(self, message):
        print('MyCallback.OnRecognitionTaskFailed-task_id:%s, status_text:%s' % (
            message['header']['task_id'], message['header']['status_text']))
    def on_channel_closed(self):
        print('MyCallback.OnRecognitionChannelClosed')
def process(client, appkey, token):
    audio_name = 'nls-sample-16k.wav'
    callback = MyCallback(audio_name)
    transcriber = client.create_transcriber(callback)
    transcriber.set_appkey(appkey)
    transcriber.set_token(token)
    transcriber.set_format(ASRFormat.PCM)
    transcriber.set_sample_rate(ASRSampleRate.SAMPLE_RATE_16K)
    transcriber.set_enable_intermediate_result(False)
    transcriber.set_enable_punctuation_prediction(True)
    transcriber.set_enable_inverse_text_normalization(True)
    try:
        ret = transcriber.start()
        if ret < 0:
            return ret
        print('sending audio...')
        with open(audio_name, 'rb') as f:
            audio = f.read(3200)
            while audio:
                ret = transcriber.send(audio)
                if ret < 0:
                    break
                time.sleep(0.1)
                audio = f.read(3200)
        transcriber.stop()
    except Exception as e:
        print(e)
    finally:
        transcriber.close()
def process_multithread(client, appkey, token, number):
    thread_list = []
    for i in range(0, number):
        thread = threading.Thread(target=process, args=(client, appkey, token))
        thread_list.append(thread)
        thread.start()
    for thread in thread_list:
        thread.join()
if __name__ == "__main__":
    client = ali_speech.NlsClient()
    # 设置输出日志信息的级别：DEBUG、INFO、WARNING、ERROR
    client.set_log_level('INFO')
    appkey = '您的appkey'
    token = '您的Token'
    process(client, appkey, token)
    # 多线程示例
    # process_multithread(client, appkey, token, 2)
```
