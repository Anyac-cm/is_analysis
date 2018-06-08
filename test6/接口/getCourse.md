# 接口：getStudents  [返回](../README.md)
用例： [课程列表](../用例/课程列表.md)


- 功能：
    返回所有课程的列表。

- API请求地址：
   接口基本地址/v1/api/getCourse

- 请求方式 ：
    GET

- 请求参数说明:
    无

- 返回实例：

        {
            "status": true,
            "info": null,
            "total": 23,
            "data": [
                {"course_id": "100001",
                "course_name": "高等数学",
                "learnHours": "56",
                "college":"信工学院",
               	},
                {
                ...其他课程
                }
            ]
        }

- 返回参数说明：

  |参数名称|说明|
  |:---------:|:--------------------------------------------------------|
  |status|bool类型，true表示正确的返回，false表示有错误|
  |info|返回结果说明信息|
  |total|返回课程人数|
  |data|所有课程的数组|
  |course_id|课程id|
  |course_name|课程名字|
  |learnHours|学时|
  |college|开课学院|
 