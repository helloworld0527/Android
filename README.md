# Android
## 组员名单
> 陈耀文 许翔 阮庭珅 刘一哲 杨檬瑞
## 流程图
![流程图](https://github.com/helloworld0527/Android/blob/master/%E6%96%87%E6%A1%A3/%E6%96%87%E6%A1%A3/%E6%B5%81%E7%A8%8B%E5%9B%BE.png)
## 类设计
![](https://github.com/helloworld0527/Android/blob/master/%E6%96%87%E6%A1%A3/%E6%96%87%E6%A1%A3/AndoridClass.png)
![](https://github.com/helloworld0527/Android/blob/master/%E6%96%87%E6%A1%A3/%E6%96%87%E6%A1%A3/ServerClass.png)
## 接口设计
### 1 人脸识别模块
    接口类型:本地接口
    功能说明:人脸识别模块主要包含了人脸识别以及人脸相似度检测以及人脸上传等功能，还有多人图片中目标检测功能。
#### 1.1 人脸识别接口
    接口地址: http://47.98.246.49:8080/android/ GradeBeautyFromBase64
    接口说明: 通过与百度进行对接，进行人脸检测，获得人脸信息。
    字符格式: base64字符串
    接收参数: avart
    返回格式: Json格式
    返回信息: 
             //正确信息示例
             {
             result : 
    {
    "face_num":1,
    "face_list":[{"face_shape":{"probability":0.63,"type":"heart"},
    "beauty":31.27,
    "liveness":{"livemapscore":1},
    "angle":{"roll":4.07,"pitch":25.51,"yaw":16.69},
    "face_token":"57bee60eafe8fb267b521908a46967b1",
    "location":{"top":634.22,"left":510.83,"rotation":1,"width":121,"height":119},
    "face_probability":1,"age":26}]}
              log_id : 5520115895599
              error_msg : SUCCESS
              cached : 0
              error_code : 0
              timestamp : 1573280856
    }
    //错误信息示例
             {
     result : null
              log_id : 3500145101001
              error_msg : pic not has face
              cached : 0
              error_code : 222202
              timestamp : 1573458463

#### 1.2 人脸相似度判定接口
    接口地址: http://47.98.246.49:8080/android/ FindSimilarFace
    接口说明: 通过与百度进行对接，在百度人脸库中，寻找与人脸最相似的人脸图片，并返回该人信息。
    字符格式: base64字符串
    接收参数: avart
    返回格式: Json格式
    返回信息: 
    //成功信息示例
             {
      result : {"face_token":"3328bc59b672437196388a8d9392bf46",
    "user_list":[{"score":65.635482788086,"group_id":"star_male_neidi","user_id":"9bb0d4e1_c00a_4ed4_8f08_cbeadc111fc2","user_info":"寇占文"}]}
     log_id : 3599656584652
     error_msg : SUCCESS
     cached : 0
     error_code : 0
     timestamp : 1573625892
             }
              //失败信息示例
             {
     result : null
              log_id : 3500145101001
              error_msg : pic not has face
              cached : 0
              error_code : 222202
              timestamp : 1573458463
              }
#### 1.3 人脸上传接口
    接口地址: http://47.98.246.49:8080/android/uploadUserPicBybase64
    接口说明: 将人脸上传到百度人脸库。
    字符格式: base64字符串
    接收参数: avart,uid
    返回格式: Json格式
    返回信息: 
    //信息示例
      {
     log_id : 3599656584652
          error_msg : SUCCESS
          face_Token : dsfdsgfdhfghsdfdsgfddfgdf0sdasdas
          error_code : 0
          timestamp : 1573625892
          }
    //上传信息失败示例
             {
     result : null
              log_id : 3500145101001
              error_msg : pic not has face
              cached : 0
              error_code : 222202
              timestamp : 1573458463
              }
#### 1.4 人群目标检测接口
    接口地址: http://47.98.246.49:8080/android/FindSevFace
    接口说明: 对人群中进行检测，将已在百度人脸库的目标检测出来，并显示其相关信息
    字符格式: base64字符串
    接收参数: avart
    返回格式: Json格式
    返回信息: 
    //成功信息示例
             {
        Result:{
    "face_num":2,"
    face_list":[{"face_token":"a7a53e29cf6556b8e7227fd66538cb7d","location":{"top":136.99,"left":73.57,"rotation":9,"width":62,"height":55},"user_list":[{"score":95.148643493652,"group_id":"Xos","user_id":"Liuyz","user_info":""}]},
    {"face_token":"4283fb09231d73786d27387224b0be67","location":{"top":153.41,"left":411.54,"rotation":-9,"width":58,"height":51},"user_list":[{"score":90.677284240723,"group_id":"Xos","user_id":"ChenYW","user_info":""}]}]}
         log_id : 9925754555999
         error_msg : SUCCESS
         cached : 0
         error_code : 0
         timestamp : 1573733971
    }
              //失败信息示例
             {
     result : null
              log_id : 3500145101001
              error_msg : pic not has face
              cached : 0
              error_code : 222202
              timestamp : 1573458463
          }
### 2 物体识别模块
    接口类型: RESTFul网络接口设计
    功能说明: 能够对菜品、车辆、植物、Logo等进行识别，并获得信息。
#### 2.1 菜品识别接口
    接口地址: https://aip.baidubce.com/rest/2.0/image-classify/v2/dish
    接口说明: 通过与百度进行对接，进行菜品检测，获得菜品信息。
    字符格式: base64字符串
    接收参数: avart
    返回格式: Json格式
    返回信息: 
    //示例
             {
             log_id : 4844594466129179279
             result_num : 5
             result : [{"calorie":"260","has_calorie":true,"name":"猪蹄","probability":"0.116462"},{"calorie":"318","has_calorie":true,"name":"糖醋排骨","probability":"0.10912"},{"calorie":"175","has_calorie":true,"name":"三杯鸡","probability":"0.0924444"},{"has_calorie":false,"name":"话梅猪手","probability":"0.0533611"},{"calorie":"197","has_calorie":true,"name":"宫保鸡丁","probability":"0.0328945"}]
             }
#### 2.2 logo识别接口
    接口地址: https://aip.baidubce.com/rest/2.0/image-classify/v2/logo
    接口说明: 通过与百度进行对接，进行logo检测，获得logo信息。
    字符格式: base64字符串
    接收参数: avart
    返回格式: Json格式
    返回信息: 
    //信息示例
             {
             log_id : 6649713117077845263
             result_num : 2
             result : [{"name":"丝格丽","probability":0.43510013222694,"location":{"width":183,"top":103,"left":208,"height":166},"type":1},{"name":"美国司沃康","probability":0.19139737876274,"location":{"width":177,"top":276,"left":210,"height":35},"type":1}]
              }
#### 2.3 车辆识别接口
    接口地址: https://aip.baidubce.com/rest/2.0/image-classify/v1/car
    接口说明: 通过与百度进行对接，进行车辆检测，获得车辆信息。
    字符格式: base64字符串
    接收参数: avart
    返回格式: Json格式
    返回信息: 
    //信息示例
    {
       log_id : 5053792215950224239
    location_result :{"width":788.5726318359375,"top":106.1950225830078,"height":396.6568603515625,"left":13.60648155212402}
       result : [{"score":0.9995930790901184,"name":"奥迪R8","year":"2007-2017"},{"score":1.704681053524837E-4,"name":"布加迪Chiron","year":"2018"},{"score":5.463857087306678E-5,"name":"NobleM15","year":"无年份信息"},{"score":3.679461951833218E-5,"name":"奥迪RS7","year":"2014-2016"},{"score":2.635523742355872E-5,"name":"奥迪RS4","year":"2018"}]
       color_result : 蓝色
           }
#### 2.4 植物识别接口
    接口地址: https://aip.baidubce.com/rest/2.0/image-classify/v1/plant接口说明: 通过与百度进行对接，进行植物检测，获得植物信息。
    字符格式: base64字符串
    接收参数: avart
    返回格式: Json格式
    返回信息: 
    //信息示例
             {
             log_id : 2156773978763979439
             result : [{"score":0.14000000059605,"name":"马兜铃"},{"score":0.089646860957146,"name":"贝壳花"},{"score":0.059999998658895,"name":"北马兜铃"},{"score":0.059999998658895,"name":"辣椒"},{"score":0.043586805462837,"name":"臭菘"}]
    log_id : 3599656584652
    error_msg : SUCCESS
    cached : 0
    error_code : 0
    timestamp : 1573625892
             }
### 3 自然语言识别模块
    接口类型: RESTFul网络接口设计
    功能说明: 能够对图片中的文字进行读取，并转换成文字，显示出来
#### 3.1 自然语言识别接口
    接口地址: https://aip.baidubce.com/rest/2.0/ocr/v1/general_basic
    接口说明: 识别图片中的文字信息
    字符格式: base64字符串
    接收参数: avart
    返回格式: Json格式
    返回信息: 
    //信息示例
             {
             log_id : 5833022606917974127
             words_result_num : 5
             words_result : [{"words":"于夏情期望失望"},{"words":"者认为之有些什么"},{"words":"么把"},{"words":"星"},{"words":"又导后的天形"}]
