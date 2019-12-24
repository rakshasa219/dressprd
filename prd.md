  |  发布日期 | 2019-12-01 |
 | -- | -- |
 |  app名称 | 轻账本 |
 |  文件现状 | 进行中 |
 |  文件的主人 | 陈彦华|
 |  领头的设计师 | 陈彦华 |
 |  领头的开发者 | 陈彦华 |
 |  领头的测试者 | 陈彦华  |
### 目录
|1|2|
|:-:|:-:|
|[市场背景](#chapter1) |[产品架构图](#chapter12)|
|[核心价值](#chapter3) |[信息架构图](#chapter20)|
|[加值宣言](#chapter5) |[功能流程图](#chapter13)|
|[目的](#chapter4) |[原型展示](#chapter14)|
|[产品背景](#chapter2) |[API检测](#chapter15)|
|[产品目标](#chapter6) |[使用对比分析](#chapter16)|
|[目标用户](#chapter7) |[使用风险报告](#chapter17)|
|[用户痛点](#chapter10) |-|
|[用户需求](#chapter8) |-|
|[场景假设](#chapter9) |-|
|[人工智能出错率与解决方法](#chapter11) |[清单](#chapter22)|

## <h3 id="chapter1">市场背景： </h3>
- 经过调查，发现市面上受欢迎程度较高的记账app比如“口袋记账”、“鲨鱼记账”、“Timi记账”、“挖财记账理财”、“随手记”等专业记账app页面精致功能分类完整但无一不例外需要进行手动记账；同时调查发现各app软件商店评价均居于前位的“网易有钱”虽然实现了最少化手动记账，采取关联所有线上支付平台进行自动记账，但对于线下交易仍旧需要手动输入记账；基于现状，现将采用腾讯语音识别技术以及百度文字识别技术以及讯飞自然语言处理技术实现一张图片或一句话解决日常记账需求。
## <h3 id="chapter2">产品背景： </h3>
- 目前绝大多数人采用的记账方式有两种：手写记账以及设备记账，移动设备的便捷性使设备记账成为用户记账首选，而基于设备记账的app又分为以下几种：以“鲨鱼记账”为首的手动记账app；以“网易有钱”为主的关联线上支付平台自动记账+手动记账app；另外经过调查发现市面上已经出现语音记账app--“有鱼记账”、“多多记账”，也有类似拍照识别记账app--“懒得记账”，其中经过产品试用发现语音识别置入记账app功能已经成熟，但是文字识别虽然有成品但是发展不完善，app体验较差，如果可以有一个记账产品兼顾语音识别与文字识别功能，那么可以让用户在3秒钟内便可轻松记账，这也许可以快速提高用户的生活效率。

##  <h3 id="chapter3">核心价值：（最小可行性产品）： </h3>
着眼于用户的最基本需求，解决用户不想在记账上花费太多时间，又能准确全面记录日常消费资金流通情况。

##  <h3 id="chapter4">目的：</h3>
做一个让无需“动手”的记账app——轻账本

##  <h3 id="chapter5">加值宣言：</h3>
- **腾讯开发平台的短语音识别api的加值:**
> 将60秒以内的语音精准识别为文字。
- **讯飞平台NPL关键词提取api的加值：**
> 把文本中包含的信息进行结构化处理，并将提取的信息以统一形式集成在一起。
- **百度开发平台的票据文字识别api的加值：**

|api名称|api加值宣言|是否为当前目标|
|:---:|:---:|:---:|
|**通用票据识别api**|针对票据字体做了专项优化的通用文字识别版本，支持对医疗票据、银行兑票、购物小票等各类票据的票面内容进行识别|√|
|*火车票识别api*|持对红、蓝火车票的8个关键字段进行结构化识别，包括车票号码、始发站、目的站、车次、日期、票价、席别、姓名|/|
|*出租车票识别api*|识别全国各大城市出租车票的6个关键字段，包括发票号码、代码、车号、日期、时间、金额|/|
| *银行回单识别api*|对各大银行的收付款回单关键字段进行结构化识别，包括：收/付款人户名、账号、开户银行、交易日期、大小写金额、流水号|/|
|*增值税发票识别api*|对增值税普票或专票所有30个字段进行结构化识别，包括发票基本信息、销售方及购买方信息、商品信息、价税信息|/|

##  <h3 id="chapter6">产品目标：</h3>
**前期目标**：
- **拍下购物票据，app自动识别金额和消费内容并抽取关键词加入账本。**
- **说出今天的消费行程，app自定识别金额和消费内容并抽取关键词加入账本。**
- *app自动储存用户拍摄票据以及语音识别结果作为账目备注以协助用户进行对账。*
- *每日记账提醒*

**后期目标**：（目前不做，后续考虑加入专业版轻账本）
- 拍下火车票/出租车票据，app自动识别金额和消费内容并进行分类加入账本。
- 拍下增值税发票，app自动识别银行账户和金额以及消费内容并进行分类加入账本。
- 拍下发票，app自动识别银行账户和金额以及消费内容并进行分类加入账本。
-拍下银行回单，app自动识别银行账户和金额以及消费内容并进行分类加入账本。

##  <h3 id="chapter7">目标用户：</h3>
学生党、购物狂、白领、月光族、理财小白、懒惰人群
##  <h3 id="chapter10">用户痛点：</h3>
- 想要记账学会理财，对于繁琐的记账流程感到烦躁。
- 线下交易/现金交易记账流程繁琐。
- 工作/学习繁忙，无法抽出多余时间细致记账。
- 积攒太多票据，整理难度大。
- 对记过的账目仅看金额和分类无法记起自己支出/收入的具体物品/事件。
- 支出/收入后总是健忘于应该及时记账。
##  <h3 id="chapter8">用户需求:（使用的人工智能要反映到需求列表中）</h3>
| 用户案例	| 对应标题	| 重要程度 |
| :--: | :--: | :--: |
| 用户想拍摄票据小票获取记账信息	|[通用票据识别](https://ai.baidu.com/tech/ocr_receipts/receipt) 	| 重要 |
| 用户想用一句话进行记账	|[短语音识别](https://ai.baidu.com/tech/speech/asr);[关键词提取](https://www.xfyun.cn/services/keyword-extraction)| 重要 |

##  <h3 id="chapter9">场景假设:</h3>
1. 经过一番疯狂的购物狂欢，小红苦恼自己到底花了多少钱，面对一堆票据无从下手，她发现了轻账本，点开app，将票据一一拍摄上传，app自动识别了小红购买的所有产品类别以及数额，将识别出来的信息自动整理成了账本。
2. 小红正准备入睡，突然想起今天在路上随手花了80块钱现金买花忘记记账，没有票据也没有线上支付记录，又懒得进行手动记账，她点开轻账本app，长按语音记账，“今天在街边花了80块钱买了一束花”，app将她的话识别成了文字并抽取重要信息进行记账。
##  <h3 id="chapter11">人工智能概率性与解决方法:</h3>
##### **概率性问题**：
- 鉴于腾讯2017年推出叮当智能助手以及人工智能“小微”均宣布语音识别准确率达97%，出错率在3%左右。百度票据识别技术针对各类票据特定的字体、打印样式进行优化，综合场景下字段准确率高达98%，其中增值税发票、出租车票四要素准确率高达99.9%，出错率在2%~0.01%。
- 依据上述展示的概率性，app如出现概率性出错对用户体验的负面影响并不会压过正面影响，为此app对于概率性出错也提供以下解决方法。
##### 解决方法
- app可提供修改功能进行手动修改识别差错的文字/数字。
- app提醒用户控制以下环境/自我变量的情况下再次进行识别：
语音识别差错：适当的音量/平稳的语速/安静的环境/
票据识别差错：适当的光线/开启相机防手抖模式/
##  <h3 id="chapter12">功能架构图</h3>
![功能架构.png](https://upload-images.jianshu.io/upload_images/11043489-29dca8a3aac24d25.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
##  <h3 id="chapter20">信息架构图</h3>
![信息架构.png](https://upload-images.jianshu.io/upload_images/11043489-e35004021b26d949.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
##  <h3 id="chapter13">功能流程图</h3>
![功能流程](https://upload-images.jianshu.io/upload_images/11043489-cb2384f1f346bad9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
##  <h3 id="chapter14">产品原型展示</h3>
- [原型展示页](http://nfunm171043007.gitee.io/apiiii)
**首页模块**
![首页](https://upload-images.jianshu.io/upload_images/11043489-a6df514d67009cc6.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
**常规记账模块**
![常规记账.png](https://upload-images.jianshu.io/upload_images/11043489-3d8b7783af08ab2e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
**拍照记账模块**
![图片授权.png](https://upload-images.jianshu.io/upload_images/11043489-3e02e2e2a341d0a3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![图库导入.png](https://upload-images.jianshu.io/upload_images/11043489-aa2565ed23b7cb24.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![拍照导入.png](https://upload-images.jianshu.io/upload_images/11043489-c7d2dd1f325685fc.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
**语音记账模块**
![语音.png](https://upload-images.jianshu.io/upload_images/11043489-707d7160bd25b5f9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
**其他页面原型（个人中心/统计）**
![个人中心.png](https://upload-images.jianshu.io/upload_images/11043489-ac49dd1d810ab3fb.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![统计.png](https://upload-images.jianshu.io/upload_images/11043489-b18c26efecd36631.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
## <h3 id="chapter15">API检测 </h3>

###### 百度开发平台通用票据api测试
【输入图片】
![微信图片_20191223235443.jpg](https://upload-images.jianshu.io/upload_images/11043489-de2a432e24cf5926.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
###### **输入代码**
``` 
from aip import AipOcr
APP_ID = '18093616'
API_KEY = 'mA1kFgYjS4iToYQ7Xt4C5T44'
SECRET_KEY = 'Cgy2XqwVoZXkXjYKuIBhPdyA2CeazK9M'
client = AipOcr(APP_ID, API_KEY, SECRET_KEY)
def get_file_content(filePath):
    with open(filePath, 'rb') as fp:
        return fp.read()
image = get_file_content('test1.jpg')
client.receipt(image);
options = {}
options["recognize_granularity"] = "big"
options["probability"] = "flase"
options["accuracy"] = "normal"
options["detect_direction"] = "true"
client.receipt(image, options)
``` 
###### **返回结果**
``` {'log_id': 3909369693688673272,
 'direction': 0,
 'words_result_num': 12,
 'words_result': [{'location': {'width': 461,
    'top': 189,
    'left': 160,
    'height': 52},
   'words': '2019/12/2318:02:02'},
  {'location': {'width': 763, 'top': 247, 'left': 155, 'height': 59},
   'words': '收银员:123机号:53单号:10901'},
  {'location': {'width': 752, 'top': 366, 'left': 148, 'height': 61},
   'words': '商品名称数量单价金额'},
  {'location': {'width': 536, 'top': 483, 'left': 423, 'height': 54},
   'words': '0.0977.006.90'},
  {'location': {'width': 59, 'top': 487, 'left': 137, 'height': 251},
   'words': '瘦肉'},
  {'location': {'width': 67, 'top': 488, 'left': 186, 'height': 246},
   'words': '去皮莴笋'},
  {'location': {'width': 668, 'top': 542, 'left': 294, 'height': 59},
   'words': '鱿鱼筒'},
  {'location': {'width': 547, 'top': 604, 'left': 422, 'height': 57},
   'words': '豆干'},
  {'location': {'width': 549, 'top': 669, 'left': 421, 'height': 57},
   'words': '件数:0.52金额:16.40元'},
  {'location': {'width': 439, 'top': 866, 'left': 126, 'height': 64},
   'words': '现金:16.40元'},
  {'location': {'width': 343, 'top': 929, 'left': 133, 'height': 65},
   'words': '找回:0元'}]}
```
###### 腾讯云短语音识别api测试
###### **输入代码**
```
# -*- coding: utf-8 -*-
from tencentcloud.common import credential
from tencentcloud.common.profile.client_profile import ClientProfile
from tencentcloud.common.profile.http_profile import HttpProfile
from tencentcloud.common.exception.tencent_cloud_sdk_exception import TencentCloudSDKException 
from tencentcloud.asr.v20190614 import asr_client, models 
import base64

#音频 URL 方式
try: 
    #此处<Your SecretId><Your SecretKey>需要替换成客户自己的账号信息
    cred = credential.Credential("AKIDpVDingzo7GG4e3afdMp57xb2EEzVmCUd", "81iCSY4WjpjTyDE1jCh2DDm7IK6yhGfq") 
    httpProfile = HttpProfile()
    httpProfile.endpoint = "asr.tencentcloudapi.com"
    clientProfile = ClientProfile()
    clientProfile.httpProfile = httpProfile
    clientProfile.signMethod = "TC3-HMAC-SHA256"  
    client = asr_client.AsrClient(cred, "ap-shanghai", clientProfile) 
    req = models.CreateRecTaskRequest()
    params = {"EngineModelType":"16k_0","ChannelNum":1,"ResTextFormat":0,"SourceType":0,"Url":"https://gitee.com/NFUNM171043007/APP_design_final/raw/master/语音输入.wav"}
    req._deserialize(params)
    resp = client.CreateRecTask(req) 
    print(resp.to_json_string()) 
    #windows 系统使用下面一行替换上面一行
    #print(resp.to_json_string().decode('UTF-8').encode('GBK') )

except TencentCloudSDKException as err: 
    print(err)
from tencentcloud.common import credential
from tencentcloud.common.profile.client_profile import ClientProfile
from tencentcloud.common.profile.http_profile import HttpProfile
from tencentcloud.common.exception.tencent_cloud_sdk_exception import TencentCloudSDKException 
from tencentcloud.asr.v20190614 import asr_client, models 
try: 
    #此处<Your SecretId><Your SecretKey>需要替换成客户自己的账号信息
    cred = credential.Credential("AKIDpVDingzo7GG4e3afdMp57xb2EEzVmCUd", "81iCSY4WjpjTyDE1jCh2DDm7IK6yhGfq") 
    httpProfile = HttpProfile()
    httpProfile.endpoint = "asr.tencentcloudapi.com"

    clientProfile = ClientProfile()
    clientProfile.httpProfile = httpProfile
    client = asr_client.AsrClient(cred, "ap-shanghai", clientProfile) 

    req = models.DescribeTaskStatusRequest()
    params = '{"TaskId":607348989}'
    req.from_json_string(params)

    resp = client.DescribeTaskStatus(req) 
    print(resp.to_json_string()) 

except TencentCloudSDKException as err: 
    print(err) 
```
###### **返回结果**
```
{"Data": {"TaskId": 607348989, "Status": 2, "StatusStr": "success", "Result": "[0:0.000,0:4.350]  今天买了一打啤酒花了，36块钱。\n", "ErrorMsg": ""}, "RequestId": "e46f00c3-c064-4c3d-a376-033ad7ae08e7"}
```
###### 讯飞开发平台关键词提取api测试
###### **输入代码**
```
# -*- coding: UTF-8 -*-
import time
import urllib.request
import urllib.parse
import json
import hashlib
import base64
url ="http://ltpapi.xfyun.cn/v1/ke"
x_appid = "5dfd94cc"
api_key = "7dd7c436b4698f8d1914eceee82e23bf"
#语言文本
TEXT="今天买了一打啤酒花了36块钱。"
def main():
    body = urllib.parse.urlencode({'text': TEXT}).encode('utf-8')
    param = {"type": "dependent"}
    x_param = base64.b64encode(json.dumps(param).replace(' ', '').encode('utf-8'))
    x_time = str(int(time.time()))
    x_checksum = hashlib.md5(api_key.encode('utf-8') + str(x_time).encode('utf-8') + x_param).hexdigest()
    x_header = {'X-Appid': x_appid,
                'X-CurTime': x_time,
                'X-Param': x_param,
                'X-CheckSum': x_checksum}
    req = urllib.request.Request(url, body, x_header)
    result = urllib.request.urlopen(req)
    result = result.read()
    print(result.decode('utf-8'))
    return
if __name__ == '__main__':
    main()
```
###### **返回结果**
```
{
	    "code": "0",
	    "data": {
	        "ke": [
	            {
	                "score": "0.680",
	                "word": "啤酒
	            },
	            {
	                "score": "0.525",
	                "word": "今天"
	            },
	            {
	                "score": "0.500",
	                "word": "36"
	            },
	  
	        ]
	    },
	    "desc": "success",
	    "sid": "ltp00000001@dx4a810f1a863f000100"
```
## <h3 id="chapter16">使用对比分析 </h3>
由于针对购物小票的票据api目前只在百度开发平台有比较完整成熟的api调用，关键词抽取api也只在科大讯飞平台找到比较完整成熟的api调用，所以针对api使用做的对比仅限于语音识别api,参与测试的平台有：**腾讯云**、**百度云**、**科大讯飞**。

---
**三家平台语音api基于同一个输入源测试结果页：[点击查看](http://nfunm171043007.gitee.io/appdesignprd/)**
**语音文件：[“语音输入.wav”](https://gitee.com/NFUNM171043007/APP_design_final/raw/master/%E8%AF%AD%E9%9F%B3%E8%BE%93%E5%85%A5.wav)**
**语音内容：【今天买了一打啤酒，花了36块钱。】**
---
- 从测试结果来看，可以明显发现百度语音识别api的测试结果与源文件语音内容大相径庭。![百度云语音识别测试结果](https://upload-images.jianshu.io/upload_images/11043489-b226c3b6354c7c54.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
- 讯飞语音识别针对语音基础框架可以识别出来，但对于语音断句、单字读音识别较为敏感。![讯飞语音识别测试结果](https://upload-images.jianshu.io/upload_images/11043489-b1864350810a73cc.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
- 腾讯语音识别词语、语义、句式均识别准确，即使断句方面稍有差错，但相较于科大讯飞和百度语音识别结果，腾讯语音识别在各方面都略胜一筹。![腾讯云语音识别测试结果](https://upload-images.jianshu.io/upload_images/11043489-eb395865a1c201d7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

---
## <h3 id="chapter17">使用风险报告 </h3>
- 语音api价格方面分析，同单位下（服务量均为100万次），价格费用**讯飞＞百度＞腾讯**

|平台名称|服务包量(预付费)|总价|单价/次|
|:-:|:-:|:-:|:-:|
|百度|100万次|3000|3元/次|
|腾讯|100万次|1800|1.8元/次|
|讯飞|100万次|4000|4元/次|
- 免费额度力度方面，**百度＞讯飞＞腾讯**

|平台名称|免费包服务量|限期|
|:-:|:-:|:-:|
|百度|不限次|不限|
|腾讯|1.5万次|每月|
|讯飞|5万|90天|
---
至此可以列出一个表格进行顺位排位
|平台名称|api测试准确排名(准确到不准确)|价格排名(从低到高)|免费额度排名(力度从大到小)|总计(总计越小,性价比越高)|
|:-:|:-:|:-:|:-:|:-:|
|百度|3|2|1|6|
|腾讯|1|1|3|5|
|讯飞|2|3|2|7|
- 综上所示，我选择了腾讯api作为我的app语音识别api调用平台。
---
## <h3 id="chapter22">清单 </h3>
- **[原型展示页](http://nfunm171043007.gitee.io/apiiii)**
- **[原型发布github页](https://github.com/rakshasa219/apiiii)**
- **三家平台语音api基于同一个输入源测试结果页：[点击查看](http://nfunm171043007.gitee.io/appdesignprd/)**
- **语音文件：[“语音输入.wav”](https://gitee.com/NFUNM171043007/APP_design_final/raw/master/%E8%AF%AD%E9%9F%B3%E8%BE%93%E5%85%A5.wav)**
