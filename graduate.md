 |  发布日期 | 2019-11-30 |
 | -- | -- |
| 项目名称| 智能毕业地图纪念册app|
| 项目现状| 迭代中|
| 项目的主人|陈彦华|
| 项目的设计师|陈彦华|
| 项目的开发者|陈彦华|  
| 项目头的测试者|陈彦华|

# 基于抖音微信平台下的毕业纪念册
## 价值主张
- 一句话版本：让回忆不仅停留在脑子里，而是举手可得的片段。
- 一分钟版本：毕业纪念册APP用户通过上传自己的毕业相册，可以使用人脸识别功能点击照片出现人脸的基本信息，方便多年后用户回忆起学生时代陌生又熟悉的人脸，同时联系方式的更新也可以方便用户联系昔日同学进行聚会聚餐；同时app获取相片地址，用户有幸在若干年后回到学校，打开纪念相册app，在校园内到达某个打卡点，便会自动弹出在此地所拍的照片。

## 市场需求：
毕业生对于不长不短的大学生活想要保存更多得以留恋的东西。

## 用户痛点：
- 纸质相册不易保留，有丢失与随着时间流逝泛黄劣化的缺点。
- 对于大量的相片无法全部保留在手机或电脑中，内存占用较大。
- 对于相册中的同学名字随着时间流逝无法记清，如要举办同学会也没有新的联系方式。
- 毕业后若干年有幸回到校园的毕业生对于校园某地是否有留念记忆不太清楚。

## 最小可行性产品（MVP）：
将毕业生的毕业纪念册整理成一个线上合集，毕业生可以上传自己想要保存的所有照片，并根据意愿上传自己的最新联系方式，纪念册app自动将相片中的毕业生的姓名与联系方式连接，并且自动获取照片拍摄的地点，把照片根据地理位置分散在校园地图内。运用地理围栏api，当用户有幸在若干年后回到学校，打开纪念相册app，在校园内到达某个打卡点，便会自动弹出在此地所拍的照片。

### 需求列表

 |  需求 | 所对应api |优先级|
 | -- | -- |--|
| 回忆相片中的人物 |人脸识别| 优先|
| 打卡回忆中的地点|地理围栏|优先|


### 目标用户

各年龄阶层的毕业学生

### API调试
1、高德地图——地理围栏
- 价值主张：地理围栏服务是一类HTTP接口，提供在服务端，增删改查地理围栏的功能，同时支持对于设备与围栏关系进行监控。
- 接口能力：检测目标地点与定位围栏距离。灵活运用在签到打卡类场景、共享单车类场景等。
输入
```
def lan(name):
    """创建围栏"""
    url = 'https://restapi.amap.com/v4/geofence/meta?key=d7cf77b9f8bd2ba4c4eac041f3f53275'
    params = {
        'key':key,
        "name": "测试围栏名称",
        "center": "113.6796784401,23.6330443988",
        "radius": "1000",
        "enable": "true",
        "valid_time": "2017-05-19",
        "repeat": "Mon,Tues,Wed,Thur,Fri,Sat,Sun",
        "time": "00:00,11:59;13:00,20:59",
        "desc": "测试围栏描述",
        "alert_condition": "enter;leave"    
    }
    response = requests.get(url,params=params)
    data = response.json()
    return data
```
输出
```
{'data': {'page_no': 1, 'page_size': 20, 'rs_list': [], 'total_record': 0},
 'errcode': 0,
 'errdetail': None,
 'errmsg': 'OK',
 'ext': None}
```

2、face++ ——人脸识别
- 价值主张：基于face在深度学习能力的人脸识别技术，提供人脸检测与属性分析、人脸搜索、人脸一比一的对比等能力。灵活应用于金融、泛安防、零售等行业场景，满足身份核验、人脸考勤、闸机通行等业务需求。
- 接口能力
人脸检测：检测图片中的人脸并标记出位置信息; 人脸关键点：展示人脸的核心关键点信息，及150个关键点信息。 人脸属性值：展示人脸属性信息，如年龄、性别等。 人脸质量信息：返回人脸各部分的遮挡、光照、模糊、完整度、置信度等信息。

输入
```
# -*- coding: utf-8 -*-
import urllib.request
import urllib.error
import time

http_url = 'https://api-cn.faceplusplus.com/facepp/v3/detect'
key = "liNAPS-__ZlQ8JhjP311Uy6LJSGV1Rht"
secret = "fKNaq_L4GrqLzfRkF0QBjcbvPQmon4FW"
filepath = r"C:\Users\Rakshasa\Desktop\timg (2).jpg"

boundary = '----------%s' % hex(int(time.time() * 1000))
data = []
data.append('--%s' % boundary)
data.append('Content-Disposition: form-data; name="%s"\r\n' % 'api_key')
data.append(key)
data.append('--%s' % boundary)
data.append('Content-Disposition: form-data; name="%s"\r\n' % 'api_secret')
data.append(secret)
data.append('--%s' % boundary)
fr = open(filepath, 'rb')
data.append('Content-Disposition: form-data; name="%s"; filename=" "' % 'image_file')
data.append('Content-Type: %s\r\n' % 'application/octet-stream')
data.append(fr.read())
fr.close()
data.append('--%s' % boundary)
data.append('Content-Disposition: form-data; name="%s"\r\n' % 'return_landmark')
data.append('1')
data.append('--%s' % boundary)
data.append('Content-Disposition: form-data; name="%s"\r\n' % 'return_attributes')
data.append(
    "gender,age,smiling,headpose,facequality,blur,eyestatus,emotion,ethnicity,beauty,mouthstatus,eyegaze,skinstatus")
data.append('--%s--\r\n' % boundary)

for i, d in enumerate(data):
    if isinstance(d, str):
        data[i] = d.encode('utf-8')

http_body = b'\r\n'.join(data)

# build http request
req = urllib.request.Request(url=http_url, data=http_body)

# header
req.add_header('Content-Type', 'multipart/form-data; boundary=%s' % boundary)

try:
    # post data to server
    resp = urllib.request.urlopen(req, timeout=5)
    # get response
    qrcont = resp.read()
    # if you want to load as json, you should decode first,
    # for example: json.loads(qrount.decode('utf-8'))
    print(qrcont.decode('utf-8'))
except urllib.error.HTTPError as e:
    print(e.read().decode('utf-8'))
```
输出
```
{"time_used": 376, "faces": [{"landmark": {"mouth_upper_lip_left_contour2": {"y": 195, "x": 688}, "mouth_upper_lip_top": {"y": 190, "x": 696}, "mouth_upper_lip_left_contour1": {"y": 192, "x": 693}, "left_eye_upper_left_quarter": {"y": 161, "x": 652}, "left_eyebrow_lower_middle": {"y": 155, "x": 649}, "mouth_upper_lip_left_contour3": {"y": 195, "x": 691}, "right_eye_top": {"y": 133, "x": 693}, "left_eye_bottom": {"y": 163, "x": 658}, "right_eyebrow_lower_left_quarter": {"y": 132, "x": 681}, "right_eye_pupil": {"y": 135, "x": 694}, "mouth_lower_lip_right_contour1": {"y": 186, "x": 707}, "mouth_lower_lip_right_contour3": {"y": 191, "x": 708}, "mouth_lower_lip_right_contour2": {"y": 185, "x": 712}, "contour_chin": {"y": 223, "x": 717}, "contour_left9": {"y": 225, "x": 706}, "left_eye_lower_right_quarter": {"y": 161, "x": 661}, "mouth_lower_lip_top": {"y": 192, "x": 699}, "right_eyebrow_upper_middle": {"y": 121, "x": 687}, "left_eyebrow_left_corner": {"y": 161, "x": 640}, "right_eye_bottom": {"y": 137, "x": 696}, "contour_left7": {"y": 215, "x": 687}, "contour_left6": {"y": 209, "x": 679}, "contour_left5": {"y": 202, "x": 671}, "contour_left4": {"y": 195, "x": 663}, "contour_left3": {"y": 187, "x": 656}, "contour_left2": {"y": 178, "x": 651}, "contour_left1": {"y": 170, "x": 646}, "left_eye_lower_left_quarter": {"y": 165, "x": 654}, "contour_right1": {"y": 114, "x": 736}, "contour_right3": {"y": 138, "x": 749}, "contour_right2": {"y": 126, "x": 743}, "mouth_left_corner": {"y": 198, "x": 685}, "contour_right4": {"y": 151, "x": 753}, "contour_right7": {"y": 192, "x": 749}, "right_eyebrow_left_corner": {"y": 138, "x": 672}, "nose_right": {"y": 166, "x": 699}, "nose_tip": {"y": 174, "x": 683}, "contour_right5": {"y": 165, "x": 755}, "nose_contour_lower_middle": {"y": 180, "x": 689}, "left_eyebrow_lower_left_quarter": {"y": 158, "x": 644}, "mouth_lower_lip_left_contour3": {"y": 199, "x": 695}, "right_eye_right_corner": {"y": 131, "x": 703}, "right_eye_lower_right_quarter": {"y": 134, "x": 700}, "mouth_upper_lip_right_contour2": {"y": 183, "x": 707}, "right_eyebrow_lower_right_quarter": {"y": 122, "x": 698}, "left_eye_left_corner": {"y": 165, "x": 651}, "mouth_right_corner": {"y": 178, "x": 715}, "mouth_upper_lip_right_contour3": {"y": 185, "x": 706}, "right_eye_lower_left_quarter": {"y": 140, "x": 692}, "left_eyebrow_right_corner": {"y": 150, "x": 660}, "left_eyebrow_lower_right_quarter": {"y": 153, "x": 654}, "right_eye_center": {"y": 136, "x": 695}, "nose_left": {"y": 181, "x": 674}, "mouth_lower_lip_left_contour1": {"y": 195, "x": 692}, "left_eye_upper_right_quarter": {"y": 157, "x": 660}, "right_eyebrow_lower_middle": {"y": 126, "x": 689}, "left_eye_top": {"y": 158, "x": 655}, "left_eye_center": {"y": 161, "x": 657}, "contour_left8": {"y": 221, "x": 696}, "contour_right9": {"y": 215, "x": 730}, "right_eye_left_corner": {"y": 141, "x": 687}, "mouth_lower_lip_bottom": {"y": 196, "x": 701}, "left_eyebrow_upper_left_quarter": {"y": 155, "x": 641}, "left_eye_pupil": {"y": 160, "x": 658}, "right_eyebrow_upper_left_quarter": {"y": 128, "x": 677}, "contour_right8": {"y": 204, "x": 741}, "right_eyebrow_right_corner": {"y": 119, "x": 708}, "right_eye_upper_left_quarter": {"y": 137, "x": 689}, "left_eyebrow_upper_middle": {"y": 150, "x": 646}, "right_eyebrow_upper_right_quarter": {"y": 118, "x": 697}, "nose_contour_left1": {"y": 155, "x": 665}, "nose_contour_left2": {"y": 173, "x": 673}, "mouth_upper_lip_right_contour1": {"y": 187, "x": 699}, "nose_contour_right1": {"y": 148, "x": 679}, "nose_contour_right2": {"y": 161, "x": 691}, "mouth_lower_lip_left_contour2": {"y": 199, "x": 690}, "contour_right6": {"y": 179, "x": 754}, "nose_contour_right3": {"y": 174, "x": 695}, "nose_contour_left3": {"y": 182, "x": 681}, "left_eye_right_corner": {"y": 158, "x": 664}, "left_eyebrow_upper_right_quarter": {"y": 148, "x": 653}, "right_eye_upper_right_quarter": {"y": 131, "x": 698}, "mouth_upper_lip_bottom": {"y": 192, "x": 698}}, "attributes": {"emotion": {"sadness": 0.052, "neutral": 15.88, "disgust": 1.449, "anger": 0.886, "surprise": 0.052, "fear": 0.052, "happiness": 81.628}, "beauty": {"female_score": 72.038, "male_score": 68.406}, "gender": {"value": "Male"}, "age": {"value": 24}, "mouthstatus": {"close": 98.566, "surgical_mask_or_respirator": 0.003, "open": 0.0, "other_occlusion": 1.43}, "glass": {"value": "Dark"}, "skinstatus": {"dark_circle": 48.757, "stain": 23.36, "acne": 32.08, "health": 0.612}, "headpose": {"yaw_angle": 17.214962, "pitch_angle": -1.4257063, "roll_angle": -29.179728}, "blur": {"blurness": {"threshold": 50.0, "value": 0.329}, "motionblur": {"threshold": 50.0, "value": 0.329}, "gaussianblur": {"threshold": 50.0, "value": 0.329}}, "smile": {"threshold": 50.0, "value": 82.427}, "eyestatus": {"left_eye_status": {"normal_glass_eye_open": 0.002, "no_glass_eye_close": 0.0, "occlusion": 0.0, "no_glass_eye_open": 0.0, "normal_glass_eye_close": 0.0, "dark_glasses": 99.998}, "right_eye_status": {"normal_glass_eye_open": 0.053, "no_glass_eye_close": 0.0, "occlusion": 0.002, "no_glass_eye_open": 0.001, "normal_glass_eye_close": 0.003, "dark_glasses": 99.941}}, "facequality": {"threshold": 70.1, "value": 40.746}, "ethnicity": {"value": "INDIA"}, "eyegaze": {"right_eye_gaze": {"position_x_coordinate": 0.528, "vector_z_component": 0.597, "vector_x_component": 0.308, "vector_y_component": -0.741, "position_y_coordinate": 0.368}, "left_eye_gaze": {"position_x_coordinate": 0.525, "vector_z_component": 0.862, "vector_x_component": 0.313, "vector_y_component": 0.4, "position_y_coordinate": 0.711}}}, "face_rectangle": {"width": 107, "top": 115, "left": 654, "height": 107}, "face_token": "400ee0597e9d38d8518826e7551acc3e"}, {"landmark": {"mouth_upper_lip_left_contour2": {"y": 263, "x": 316}, "mouth_upper_lip_top": {"y": 273, "x": 328}, "mouth_upper_lip_left_contour1": {"y": 270, "x": 325}, "left_eye_upper_left_quarter": {"y": 219, "x": 332}, "left_eyebrow_lower_middle": {"y": 213, "x": 341}, "mouth_upper_lip_left_contour3": {"y": 265, "x": 316}, "right_eye_top": {"y": 251, "x": 373}, "left_eye_bottom": {"y": 225, "x": 334}, "right_eyebrow_lower_left_quarter": {"y": 245, "x": 375}, "right_eye_pupil": {"y": 253, "x": 371}, "mouth_lower_lip_right_contour1": {"y": 286, "x": 332}, "mouth_lower_lip_right_contour3": {"y": 289, "x": 327}, "mouth_lower_lip_right_contour2": {"y": 289, "x": 335}, "contour_chin": {"y": 308, "x": 300}, "contour_left9": {"y": 298, "x": 290}, "left_eye_lower_right_quarter": {"y": 228, "x": 338}, "mouth_lower_lip_top": {"y": 281, "x": 321}, "right_eyebrow_upper_middle": {"y": 246, "x": 385}, "left_eyebrow_left_corner": {"y": 206, "x": 323}, "right_eye_bottom": {"y": 256, "x": 370}, "contour_left7": {"y": 273, "x": 281}, "contour_left6": {"y": 260, "x": 280}, "contour_left5": {"y": 248, "x": 281}, "contour_left4": {"y": 236, "x": 286}, "contour_left3": {"y": 224, "x": 292}, "contour_left2": {"y": 214, "x": 299}, "contour_left1": {"y": 204, "x": 307}, "left_eye_lower_left_quarter": {"y": 221, "x": 330}, "contour_right1": {"y": 268, "x": 385}, "contour_right3": {"y": 286, "x": 371}, "contour_right2": {"y": 277, "x": 378}, "mouth_left_corner": {"y": 256, "x": 306}, "contour_right4": {"y": 293, "x": 363}, "contour_right7": {"y": 308, "x": 333}, "right_eyebrow_left_corner": {"y": 239, "x": 368}, "nose_right": {"y": 268, "x": 352}, "nose_tip": {"y": 261, "x": 342}, "contour_right5": {"y": 300, "x": 354}, "nose_contour_lower_middle": {"y": 267, "x": 337}, "left_eyebrow_lower_left_quarter": {"y": 208, "x": 333}, "mouth_lower_lip_left_contour3": {"y": 276, "x": 310}, "right_eye_right_corner": {"y": 261, "x": 377}, "right_eye_lower_right_quarter": {"y": 258, "x": 373}, "mouth_upper_lip_right_contour2": {"y": 281, "x": 338}, "right_eyebrow_lower_right_quarter": {"y": 255, "x": 386}, "left_eye_left_corner": {"y": 218, "x": 326}, "mouth_right_corner": {"y": 287, "x": 344}, "mouth_upper_lip_right_contour3": {"y": 281, "x": 336}, "right_eye_lower_left_quarter": {"y": 252, "x": 366}, "left_eyebrow_right_corner": {"y": 227, "x": 356}, "left_eyebrow_lower_right_quarter": {"y": 221, "x": 348}, "right_eye_center": {"y": 254, "x": 371}, "nose_left": {"y": 249, "x": 329}, "mouth_lower_lip_left_contour1": {"y": 269, "x": 312}, "left_eye_upper_right_quarter": {"y": 226, "x": 340}, "right_eyebrow_lower_middle": {"y": 249, "x": 382}, "left_eye_top": {"y": 221, "x": 336}, "left_eye_center": {"y": 224, "x": 335}, "contour_left8": {"y": 286, "x": 285}, "contour_right9": {"y": 312, "x": 311}, "right_eye_left_corner": {"y": 249, "x": 363}, "mouth_lower_lip_bottom": {"y": 285, "x": 318}, "left_eyebrow_upper_left_quarter": {"y": 204, "x": 334}, "left_eye_pupil": {"y": 222, "x": 334}, "right_eyebrow_upper_left_quarter": {"y": 240, "x": 378}, "contour_right8": {"y": 310, "x": 323}, "right_eyebrow_right_corner": {"y": 262, "x": 389}, "right_eye_upper_left_quarter": {"y": 249, "x": 368}, "left_eyebrow_upper_middle": {"y": 209, "x": 344}, "right_eyebrow_upper_right_quarter": {"y": 253, "x": 390}, "nose_contour_left1": {"y": 235, "x": 349}, "nose_contour_left2": {"y": 246, "x": 337}, "mouth_upper_lip_right_contour1": {"y": 276, "x": 332}, "nose_contour_right1": {"y": 245, "x": 361}, "nose_contour_right2": {"y": 260, "x": 354}, "mouth_lower_lip_left_contour2": {"y": 266, "x": 307}, "contour_right6": {"y": 304, "x": 344}, "nose_contour_right3": {"y": 269, "x": 344}, "nose_contour_left3": {"y": 258, "x": 332}, "left_eye_right_corner": {"y": 231, "x": 342}, "left_eyebrow_upper_right_quarter": {"y": 217, "x": 352}, "right_eye_upper_right_quarter": {"y": 256, "x": 376}, "mouth_upper_lip_bottom": {"y": 275, "x": 326}}, "attributes": {"emotion": {"sadness": 0.0, "neutral": 0.0, "disgust": 0.011, "anger": 0.003, "surprise": 0.001, "fear": 0.001, "happiness": 99.983}, "beauty": {"female_score": 75.28, "male_score": 68.396}, "gender": {"value": "Male"}, "age": {"value": 30}, "mouthstatus": {"close": 0.0, "surgical_mask_or_respirator": 0.0, "open": 100.0, "other_occlusion": 0.0}, "glass": {"value": "None"}, "skinstatus": {"dark_circle": 6.983, "stain": 8.972, "acne": 9.367, "health": 4.801}, "headpose": {"yaw_angle": -3.921308, "pitch_angle": 4.374855, "roll_angle": 43.017323}, "blur": {"blurness": {"threshold": 50.0, "value": 0.035}, "motionblur": {"threshold": 50.0, "value": 0.035}, "gaussianblur": {"threshold": 50.0, "value": 0.035}}, "smile": {"threshold": 50.0, "value": 100.0}, "eyestatus": {"left_eye_status": {"normal_glass_eye_open": 0.041, "no_glass_eye_close": 0.0, "occlusion": 0.019, "no_glass_eye_open": 99.94, "normal_glass_eye_close": 0.0, "dark_glasses": 0.0}, "right_eye_status": {"normal_glass_eye_open": 0.0, "no_glass_eye_close": 0.0, "occlusion": 0.0, "no_glass_eye_open": 100.0, "normal_glass_eye_close": 0.0, "dark_glasses": 0.0}}, "facequality": {"threshold": 70.1, "value": 91.575}, "ethnicity": {"value": "INDIA"}, "eyegaze": {"right_eye_gaze": {"position_x_coordinate": 0.491, "vector_z_component": 0.996, "vector_x_component": -0.092, "vector_y_component": 0.013, "position_y_coordinate": 0.437}, "left_eye_gaze": {"position_x_coordinate": 0.421, "vector_z_component": 0.979, "vector_x_component": 0.069, "vector_y_component": 0.192, "position_y_coordinate": 0.444}}}, "face_rectangle": {"width": 105, "top": 209, "left": 272, "height": 105}, "face_token": "47b30ae0b7763354cd9cf8cea539edc8"}, {"landmark": {"mouth_upper_lip_left_contour2": {"y": 198, "x": 475}, "mouth_upper_lip_top": {"y": 198, "x": 483}, "mouth_upper_lip_left_contour1": {"y": 198, "x": 480}, "left_eye_upper_left_quarter": {"y": 158, "x": 456}, "left_eyebrow_lower_middle": {"y": 154, "x": 452}, "mouth_upper_lip_left_contour3": {"y": 200, "x": 478}, "right_eye_top": {"y": 155, "x": 495}, "left_eye_bottom": {"y": 161, "x": 459}, "right_eyebrow_lower_left_quarter": {"y": 152, "x": 487}, "right_eye_pupil": {"y": 156, "x": 495}, "mouth_lower_lip_right_contour1": {"y": 199, "x": 500}, "mouth_lower_lip_right_contour3": {"y": 206, "x": 498}, "mouth_lower_lip_right_contour2": {"y": 198, "x": 506}, "contour_chin": {"y": 232, "x": 495}, "contour_left9": {"y": 227, "x": 486}, "left_eye_lower_right_quarter": {"y": 160, "x": 463}, "mouth_lower_lip_top": {"y": 204, "x": 486}, "right_eyebrow_upper_middle": {"y": 146, "x": 495}, "left_eyebrow_left_corner": {"y": 151, "x": 445}, "right_eye_bottom": {"y": 157, "x": 496}, "contour_left7": {"y": 209, "x": 476}, "contour_left6": {"y": 202, "x": 470}, "contour_left5": {"y": 194, "x": 463}, "contour_left4": {"y": 186, "x": 457}, "contour_left3": {"y": 178, "x": 454}, "contour_left2": {"y": 169, "x": 452}, "contour_left1": {"y": 160, "x": 451}, "left_eye_lower_left_quarter": {"y": 160, "x": 456}, "contour_right1": {"y": 152, "x": 548}, "contour_right3": {"y": 176, "x": 550}, "contour_right2": {"y": 164, "x": 550}, "mouth_left_corner": {"y": 198, "x": 472}, "contour_right4": {"y": 187, "x": 548}, "contour_right7": {"y": 217, "x": 527}, "right_eyebrow_left_corner": {"y": 153, "x": 478}, "nose_right": {"y": 182, "x": 494}, "nose_tip": {"y": 190, "x": 473}, "contour_right5": {"y": 198, "x": 543}, "nose_contour_lower_middle": {"y": 194, "x": 477}, "left_eyebrow_lower_left_quarter": {"y": 153, "x": 448}, "mouth_lower_lip_left_contour3": {"y": 209, "x": 480}, "right_eye_right_corner": {"y": 155, "x": 504}, "right_eye_lower_right_quarter": {"y": 156, "x": 500}, "mouth_upper_lip_right_contour2": {"y": 193, "x": 498}, "right_eyebrow_lower_right_quarter": {"y": 149, "x": 505}, "left_eye_left_corner": {"y": 159, "x": 454}, "mouth_right_corner": {"y": 189, "x": 511}, "mouth_upper_lip_right_contour3": {"y": 196, "x": 498}, "right_eye_lower_left_quarter": {"y": 157, "x": 491}, "left_eyebrow_right_corner": {"y": 155, "x": 461}, "left_eyebrow_lower_right_quarter": {"y": 155, "x": 456}, "right_eye_center": {"y": 156, "x": 495}, "nose_left": {"y": 185, "x": 465}, "mouth_lower_lip_left_contour1": {"y": 202, "x": 478}, "left_eye_upper_right_quarter": {"y": 158, "x": 463}, "right_eyebrow_lower_middle": {"y": 150, "x": 496}, "left_eye_top": {"y": 157, "x": 459}, "left_eye_center": {"y": 159, "x": 459}, "contour_left8": {"y": 218, "x": 481}, "contour_right9": {"y": 231, "x": 507}, "right_eye_left_corner": {"y": 156, "x": 487}, "mouth_lower_lip_bottom": {"y": 210, "x": 488}, "left_eyebrow_upper_left_quarter": {"y": 150, "x": 449}, "left_eye_pupil": {"y": 159, "x": 460}, "right_eyebrow_upper_left_quarter": {"y": 148, "x": 486}, "contour_right8": {"y": 225, "x": 518}, "right_eyebrow_right_corner": {"y": 148, "x": 514}, "right_eye_upper_left_quarter": {"y": 155, "x": 491}, "left_eyebrow_upper_middle": {"y": 151, "x": 453}, "right_eyebrow_upper_right_quarter": {"y": 145, "x": 505}, "nose_contour_left1": {"y": 159, "x": 467}, "nose_contour_left2": {"y": 178, "x": 467}, "mouth_upper_lip_right_contour1": {"y": 196, "x": 486}, "nose_contour_right1": {"y": 158, "x": 482}, "nose_contour_right2": {"y": 175, "x": 489}, "mouth_lower_lip_left_contour2": {"y": 204, "x": 476}, "contour_right6": {"y": 208, "x": 535}, "nose_contour_right3": {"y": 190, "x": 487}, "nose_contour_left3": {"y": 191, "x": 470}, "left_eye_right_corner": {"y": 160, "x": 466}, "left_eyebrow_upper_right_quarter": {"y": 152, "x": 457}, "right_eye_upper_right_quarter": {"y": 154, "x": 500}, "mouth_upper_lip_bottom": {"y": 200, "x": 484}}, "attributes": {"emotion": {"sadness": 0.012, "neutral": 0.009, "disgust": 0.778, "anger": 0.031, "surprise": 0.002, "fear": 0.004, "happiness": 99.163}, "beauty": {"female_score": 59.976, "male_score": 52.16}, "gender": {"value": "Male"}, "age": {"value": 49}, "mouthstatus": {"close": 0.0, "surgical_mask_or_respirator": 0.041, "open": 99.07, "other_occlusion": 0.889}, "glass": {"value": "None"}, "skinstatus": {"dark_circle": 51.73, "stain": 7.009, "acne": 0.978, "health": 1.536}, "headpose": {"yaw_angle": 34.356274, "pitch_angle": 12.977315, "roll_angle": -21.322218}, "blur": {"blurness": {"threshold": 50.0, "value": 0.259}, "motionblur": {"threshold": 50.0, "value": 0.259}, "gaussianblur": {"threshold": 50.0, "value": 0.259}}, "smile": {"threshold": 50.0, "value": 99.996}, "eyestatus": {"left_eye_status": {"normal_glass_eye_open": 0.165, "no_glass_eye_close": 41.069, "occlusion": 0.479, "no_glass_eye_open": 58.265, "normal_glass_eye_close": 0.011, "dark_glasses": 0.011}, "right_eye_status": {"normal_glass_eye_open": 0.234, "no_glass_eye_close": 1.185, "occlusion": 93.162, "no_glass_eye_open": 5.365, "normal_glass_eye_close": 0.051, "dark_glasses": 0.004}}, "facequality": {"threshold": 70.1, "value": 0.006}, "ethnicity": {"value": "INDIA"}, "eyegaze": {"right_eye_gaze": {"position_x_coordinate": 0.525, "vector_z_component": 0.994, "vector_x_component": 0.111, "vector_y_component": 0.019, "position_y_coordinate": 0.457}, "left_eye_gaze": {"position_x_coordinate": 0.537, "vector_z_component": 0.914, "vector_x_component": 0.237, "vector_y_component": -0.328, "position_y_coordinate": 0.377}}}, "face_rectangle": {"width": 104, "top": 136, "left": 448, "height": 104}, "face_token": "07828d10788255eb9f0ea29b7a1ea85b"}], "image_id": "relU0rn/Ddf0EyCRpl8MSQ==", "request_id": "1568648123,d5660931-ec5a-4f8b-b44e-742e62492252", "face_num": 3}
```

### api出错率
概率性问题：
鉴于人脸识别准确率达97%，出错率在3%左右。高德地图api地理围栏准确率高达98%，出错率在2%~0.01%。
依据上述展示的概率性，app如出现概率性出错**对用户体验的负面影响并不会压过正面影响。**
### 功能说明
*   同学录整理    **人脸识别**对所拍摄照片与相册中过往图片中的人脸进行标签（性别、名字、心情、联系方式）。
*   校园回归打卡 **地理围栏api**+**地标识别**当用户有幸在若干年后回到学校 打开纪念相册app，在校园内到达某个打卡点，便会自动弹出在此地所拍的照片。
### 原型功能展示--人脸识别
![微信图片_20200110151946.png](https://upload-images.jianshu.io/upload_images/11043489-2fdfab9e5f35a967.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
### 原型功能展示--地理相册
![微信图片_20200110151451.png](https://upload-images.jianshu.io/upload_images/11043489-feeec6e725c76e70.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
