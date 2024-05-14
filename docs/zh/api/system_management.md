# 一、系统管理

## 1、获取菜单列表

```
GET  /api/eventStats/v1/menu/list
```

请求参数：

| 序号 | 字段名称 | 字段类型 | 参数位置 | 是否必须 | 字段说明                                               |
| :--- | :------- | :------- | :------- | :------- | :----------------------------------------------------- |
| 1    | pid      | string   | query    | 否       | 父资源，pid>=0，默认0不使用                            |
| 2    | isTree   | int      | query    | 是       | 是否以树形结构返回，1-是，2-否                         |
| 3    | menuType | int      | query    | 否       | 1-系统类 2-业务类 3-所有                               |
| 4    | key      | string   | query    | 否       | 模糊查询中英文名称及菜单编码                           |
| 5    | page     | int      | query    | 是       | 第几页，page>0                                         |
| 6    | size     | int      | query    | 是       | 当前页显示数量，size>0 \| size=-1（size=-1时查询所有） |

请求示例：

```
pid=124124124124&isTree=1&menuType=1&key=menu&page=5&size=10
```

响应参数：

| 序号 | 字段名称 |       |              | 字段类型     | 字段说明                       |
| :--- | :------- | ----- | ------------ | :----------- | :----------------------------- |
| 1    | res      |       |              | list         | 响应结果                       |
| 2    |          | total |              | int          | 总个数                         |
| 3    |          | data  |              | list<object> | 具体结果                       |
| 4    |          |       | id           | string       | 菜单id                         |
| 5    |          |       | cName        | string       | 中文名称                       |
| 6    |          |       | eName        | string       | 英文名称                       |
| 7    |          |       | code         | string       | 菜单编码                       |
| 8    |          |       | icon         | string       | 默认图标                       |
| 9    |          |       | selectedIcon | string       | 选中图标                       |
| 10   |          |       | path         | string       | 绝对路径                       |
| 11   |          |       | component    | string       | 组件路径                       |
| 12   |          |       | menuType     | int          | 菜单类型 （1-系统类 2-业务类） |
| 13   |          |       | pid          | string       | 父菜单id                       |
| 14   |          |       | sortOrder    | int          | 排序数值                       |
| 15   |          |       | visible      | int          | 是否显示（1-显示 2-不显示）    |
| 16   |          |       | createTime   | string       | 创建时间                       |
| 17   |          |       | updateTime   | string       | 修改时间                       |
| 18   |          |       | delFlag      | int          | 删除标识（0-未删除 1-已删除）  |
| 19   |          |       | children     | list<object> | 下级菜单列表                   |

响应示例：

```json
{
    "res": {
        "total": 50,
        "data": [              
           {          
                "id": "1",
                "cName": "知识网络",
                "eName": "knowledge network",
                "code": "kn",
                "icon":"xxx",
                "selectedIcon":"xxx",
                "path": "绝对路径",
                "component": "组件路径",
                "menuType":1,
                "pid":0,
                "sortOrder":0,
                "visible": 1,
                "createTime": "2024-05-14 00:00:00",
                "updateTime": "2024-05-14 00:00:00",
                "delFlag": 0,
                "children": [
                     {
                        "id": "2",
                        "cName": "知识网络",
                        "eName": "knowledge network",
                        "code": "kn",
                        "icon":"xxx",
                        "selectedIcon":"xxx",
                        "path": "绝对路径",
                        "component": "组件路径",
                        "menuType":1,
                        "pid":1,
                        "sortOrder":0,
                        "visible": 1,
                        "createTime": "2024-05-14 00:00:00",
                        "updateTime": "2024-05-14 00:00:00",
                		"delFlag": 0,
                        "children": []
                     }
                 ]  
           }
        ]
    }
}
```

异常返回参数：

| 序号 | 参数         | 含义         |
| :--- | :----------- | :----------- |
| 1    | ErrorCode    | 错误码       |
| 2    | Description  | 错误描述     |
| 3    | Solution     | 错误处理建议 |
| 4    | ErrorDetails | 错误细节     |
| 5    | ErrorLink    | 错误信息地址 |

异常返回示例：

```json
{
    "ErrorCode": "EventStats.Common.ParameterError",
    "Description":  "Parameter error",
    "Solution": "",
    "ErrorDetails"：[],
    "ErrorLink": ""
}
```

## 2、获取指定菜单详情

```
GET  /api/eventStats/v1/menu
```

请求参数：

| 序号 | 字段名称 | 字段类型 | 参数位置 | 是否必须 | 字段说明 |
| :--- | :------- | :------- | :------- | :------- | :------- |
| 1    | id       | string   | query    | 是       | 菜单id   |

请求示例：

```
id=124124124124
```

响应参数：

| 序号 | 字段名称 |              | 字段类型     | 字段说明                       |
| :--- | :------- | ------------ | :----------- | :----------------------------- |
| 1    | res      |              | list         | 响应结果                       |
| 4    |          | id           | string       | 菜单id                         |
| 5    |          | cName        | string       | 中文名称                       |
| 6    |          | eName        | string       | 英文名称                       |
| 7    |          | code         | string       | 菜单编码                       |
| 8    |          | icon         | string       | 默认图标                       |
| 9    |          | selectedIcon | string       | 选中图标                       |
| 10   |          | path         | string       | 绝对路径                       |
| 11   |          | component    | string       | 组件路径                       |
| 12   |          | menuType     | int          | 菜单类型 （1-系统类 2-业务类） |
| 13   |          | pid          | string       | 父菜单id                       |
| 14   |          | sortOrder    | int          | 排序数值                       |
| 15   |          | visible      | int          | 是否显示（0-显示 1-不显示）    |
| 16   |          | createTime   | string       | 创建时间                       |
| 17   |          | updateTime   | string       | 修改时间                       |
| 18   |          | delFlag      | int          | 删除标识（0-未删除 1-已删除）  |
| 19   |          | children     | list<object> | 下级菜单列表                   |

响应示例：

```json
{
    "res": {          
        "id": "1",
        "cName": "知识网络",
        "eName": "knowledge network",
        "code": "kn",
        "icon":"xxx",
        "selectedIcon":"xxx",
        "path": "绝对路径",
        "component": "组件路径",
        "menuType":1,
        "pid":0,
        "sortOrder":0,
        "visible": 1,
        "createTime": "2024-05-14 00:00:00",
        "updateTime": "2024-05-14 00:00:00",
        "delFlag": 0,
        "children": []  
    }
}
```

异常返回参数：

| 序号 | 参数         | 含义         |
| :--- | :----------- | :----------- |
| 1    | ErrorCode    | 错误码       |
| 2    | Description  | 错误描述     |
| 3    | Solution     | 错误处理建议 |
| 4    | ErrorDetails | 错误细节     |
| 5    | ErrorLink    | 错误信息地址 |

异常返回示例：

```json
{
    "ErrorCode": "EventStats.Common.ParameterError",
    "Description":  "Parameter error",
    "Solution": "",
    "ErrorDetails"：[],
    "ErrorLink": ""
}
```

## 3、新建菜单

```
POST  /api/eventStats/v1/menu/add
```

请求参数：

| 序号 | 字段名称     | 字段类型 | 参数位置 | 是否必须 | 字段说明                       |
| :--- | ------------ | :------- | -------- | -------- | :----------------------------- |
| 1    | cName        | string   | body     | 是       | 中文名称                       |
| 2    | eName        | string   | body     | 是       | 英文名称                       |
| 3    | code         | string   | body     | 是       | 菜单编码                       |
| 4    | icon         | string   | body     | 否       | 默认图标                       |
| 5    | selectedIcon | string   | body     | 否       | 选中图标                       |
| 6    | path         | string   | body     | 否       | 绝对路径                       |
| 7    | component    | string   | body     | 否       | 组件路径                       |
| 8    | menuType     | int      | body     | 是       | 菜单类型 （1-系统类 2-业务类） |
| 9    | pid          | string   | body     | 否       | 父菜单id                       |
| 10   | sortOrder    | int      | body     | 否       | 排序数值                       |
| 11   | visible      | int      | body     | 否       | 是否显示（0-显示 1-不显示）    |

请求示例：

```json
{         
    "cName": "知识网络",
    "eName": "knowledge network",
    "code": "kn",
    "icon":"xxx",
    "selectedIcon":"xxx",
    "path": "绝对路径",
    "component": "组件路径",
    "menuType":1,
    "pid":0,
    "sortOrder":0,
    "visible": 1
}
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 字段说明     |
| :--- | :------- | :------- | :----------- |
| 1    | res      | string   | 创建成功结果 |

响应示例：

```json
{
  "res": "OK"
}
```

异常返回参数：

| 序号 | 参数         | 含义         |
| :--- | :----------- | :----------- |
| 1    | ErrorCode    | 错误码       |
| 2    | Description  | 错误描述     |
| 3    | Solution     | 错误处理建议 |
| 4    | ErrorDetails | 错误细节     |
| 5    | ErrorLink    | 错误信息地址 |

异常返回示例：

```json
{
    "ErrorCode": "EventStats.Common.ParameterError",
    "Description":  "Parameter error",
    "Solution": "",
    "ErrorDetails"：[],
    "ErrorLink": ""
}
```

## 4、修改菜单

```
POST  /api/eventStats/v1/menu/update
```

请求参数：

| 序号 | 字段名称     | 字段类型 | 参数位置 | 是否必须 | 字段说明                       |
| :--- | ------------ | :------- | -------- | -------- | :----------------------------- |
| 1    | id           | string   | body     | 是       | 菜单id                         |
| 2    | cName        | string   | body     | 是       | 中文名称                       |
| 3    | eName        | string   | body     | 是       | 英文名称                       |
| 4    | icon         | string   | body     | 否       | 默认图标                       |
| 5    | selectedIcon | string   | body     | 否       | 选中图标                       |
| 6    | path         | string   | body     | 否       | 绝对路径                       |
| 7    | component    | string   | body     | 否       | 组件路径                       |
| 8    | menuType     | int      | body     | 是       | 菜单类型 （1-系统类 2-业务类） |
| 9    | pid          | string   | body     | 否       | 父菜单id                       |
| 10   | sortOrder    | int      | body     | 否       | 排序数值                       |
| 11   | visible      | int      | body     | 否       | 是否显示（0-显示 1-不显示）    |

请求示例：

```json
{         
    "id": "2342125125",
    "cName": "知识网络",
    "eName": "knowledge network",
    "icon":"xxx",
    "selectedIcon":"xxx",
    "path": "绝对路径",
    "component": "组件路径",
    "menuType":1,
    "pid":0,
    "sortOrder":0,
    "visible": 1
}
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 字段说明     |
| :--- | :------- | :------- | :----------- |
| 1    | res      | string   | 修改成功结果 |

响应示例：

```json
{
  "res": "OK"
}
```

异常返回参数：

| 序号 | 参数         | 含义         |
| :--- | :----------- | :----------- |
| 1    | ErrorCode    | 错误码       |
| 2    | Description  | 错误描述     |
| 3    | Solution     | 错误处理建议 |
| 4    | ErrorDetails | 错误细节     |
| 5    | ErrorLink    | 错误信息地址 |

异常返回示例：

```json
{
    "ErrorCode": "EventStats.Common.ParameterError",
    "Description":  "Parameter error",
    "Solution": "",
    "ErrorDetails"：[],
    "ErrorLink": ""
}
```

## 5、删除菜单

```
POST  /api/eventStats/v1/menu/delete
```

请求参数：

| 序号 | 字段名称 | 字段类型     | 参数位置 | 是否必须 | 字段说明   |
| :--- | -------- | :----------- | -------- | -------- | :--------- |
| 1    | ids      | list<string> | body     | 是       | 菜单id列表 |

请求示例：

```json
{         
    "ids": ["2342125125"]
}
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 字段说明     |
| :--- | :------- | :------- | :----------- |
| 1    | res      | string   | 删除成功结果 |

响应示例：

```json
{
  "res": "OK"
}
```

异常返回参数：

| 序号 | 参数         | 含义         |
| :--- | :----------- | :----------- |
| 1    | ErrorCode    | 错误码       |
| 2    | Description  | 错误描述     |
| 3    | Solution     | 错误处理建议 |
| 4    | ErrorDetails | 错误细节     |
| 5    | ErrorLink    | 错误信息地址 |

异常返回示例：

```json
{
    "ErrorCode": "EventStats.Common.ParameterError",
    "Description":  "Parameter error",
    "Solution": "",
    "ErrorDetails"：[],
    "ErrorLink": ""
}
```

## 6、获取字典列表

```
GET  /api/eventStats/v1/dict/list
```

请求参数：

| 序号 | 字段名称 | 字段类型 | 参数位置 | 是否必须 | 字段说明                                              |
| :--- | -------- | :------- | -------- | -------- | :---------------------------------------------------- |
| 1    | key      | string   | query    | 否       | 模糊查询                                              |
| 2    | page     | int      | query    | 是       | 第几页，page>0                                        |
| 3    | size     | int      | query    | 是       | 当前页显示数量，size>0 \|size=-1（size=-1时查询所有） |

请求示例：

```
key=dict&page=1&size=-1
```

响应参数：

| 序号 | 字段名称 |       |            | 字段类型     | 字段说明 |
| :--- | :------- | ----- | ---------- | :----------- | :------- |
| 1    | res      |       |            | string       | 响应结果 |
| 2    |          | total |            | int          | 总个数   |
| 3    |          | data  |            | list<object> | 具体结果 |
| 4    |          |       | id         | string       | 字典id   |
| 5    |          |       | cName      | string       | 中文名称 |
| 6    |          |       | eName      | string       | 英文名称 |
| 7    |          |       | remark     | string       | 描述     |
| 8    |          |       | dictType   | string       | 字典类型 |
| 9    |          |       | createBy   | string       | 创建人   |
| 10   |          |       | updateBy   | string       | 修改人   |
| 11   |          |       | createTime | string       | 创建时间 |
| 12   |          |       | updateTime | string       | 修改时间 |

响应示例：

```json
{
    "res": {
        "total": 3,
        "data": [
            {
                "id": "7152263200732143616",
                "cName": "日志类型",
                "eName": "log type",
                "remark": "xxx",
                "dictType": "log_type",
                "createBy":"1",
                "updateBy":"1",
                "createTime":"2023-12-29 17:14:55",
                "updateTime":"2023-12-29 17:14:55"
 
         	},
            ...
        ]
    }
}
```

异常返回参数：

| 序号 | 参数         | 含义         |
| :--- | :----------- | :----------- |
| 1    | ErrorCode    | 错误码       |
| 2    | Description  | 错误描述     |
| 3    | Solution     | 错误处理建议 |
| 4    | ErrorDetails | 错误细节     |
| 5    | ErrorLink    | 错误信息地址 |

异常返回示例：

```json
{
    "ErrorCode": "EventStats.Common.ParameterError",
    "Description":  "Parameter error",
    "Solution": "",
    "ErrorDetails"：[],
    "ErrorLink": ""
}
```

## 7、获取指定字典详情

```
GET  /api/eventStats/v1/dict
```

请求参数：

| 序号 | 字段名称 | 字段类型 | 参数位置 | 是否必须 | 字段说明 |
| :--- | -------- | :------- | -------- | -------- | :------- |
| 1    | id       | string   | query    | 是       | 字典id   |

请求示例：

```
id=2342352354
```

响应参数：

| 序号 | 字段名称 |            | 字段类型 | 字段说明 |
| :--- | :------- | ---------- | :------- | :------- |
| 1    | res      |            | string   | 响应结果 |
| 2    |          | id         | string   | 字典id   |
| 3    |          | cName      | string   | 中文名称 |
| 4    |          | eName      | string   | 英文名称 |
| 5    |          | remark     | string   | 描述     |
| 6    |          | dictType   | string   | 字典类型 |
| 7    |          | createBy   | string   | 创建人   |
| 8    |          | updateBy   | string   | 修改人   |
| 9    |          | createTime | string   | 创建时间 |
| 10   |          | updateTime | string   | 修改时间 |

响应示例：

```json
{
    "res": {
        "id": "7152263200732143616",
        "cName": "日志类型",
        "eName": "log type",
        "remark": "xxx",
        "dictType": "log_type",
        "createBy":"1",
        "updateBy":"1",
        "createTime":"2023-12-29 17:14:55",
        "updateTime":"2023-12-29 17:14:55"
    }
}
```

异常返回参数：

| 序号 | 参数         | 含义         |
| :--- | :----------- | :----------- |
| 1    | ErrorCode    | 错误码       |
| 2    | Description  | 错误描述     |
| 3    | Solution     | 错误处理建议 |
| 4    | ErrorDetails | 错误细节     |
| 5    | ErrorLink    | 错误信息地址 |

异常返回示例：

```json
{
    "ErrorCode": "EventStats.Common.ParameterError",
    "Description":  "Parameter error",
    "Solution": "",
    "ErrorDetails"：[],
    "ErrorLink": ""
}
```

## 8、新建字典

```
POST  /api/eventStats/v1/dict/add
```

请求参数：

| 序号 | 字段名称 | 字段类型 | 参数位置 | 是否必须 | 字段说明 |
| :--- | :------- | :------- | :------- | :------- | :------- |
| 1    | userId   | string   | header   | 是       | 用户id   |
| 2    | cName    | string   | body     | 是       | 中文名称 |
| 3    | eName    | string   | body     | 是       | 英文名称 |
| 4    | remark   | string   | body     | 否       | 描述     |
| 5    | dictType | string   | body     | 是       | 字典类型 |

请求示例：

```json
{
    "cName": "日志类型",
    "eName": "log type",
    "remark": "xxx",
    "dictType": "log_type"
}
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 字段说明 |
| :--- | :------- | :------- | :------- |
| 1    | res      | string   | 响应结果 |

响应示例：

```json
{
    "res": "OK"
}
```

异常返回参数：

| 序号 | 参数         | 含义         |
| :--- | :----------- | :----------- |
| 1    | ErrorCode    | 错误码       |
| 2    | Description  | 错误描述     |
| 3    | Solution     | 错误处理建议 |
| 4    | ErrorDetails | 错误细节     |
| 5    | ErrorLink    | 错误信息地址 |

异常返回示例：

```json
{
    "ErrorCode": "EventStats.Common.ParameterError",
    "Description":  "Parameter error",
    "Solution": "",
    "ErrorDetails"：[],
    "ErrorLink": ""
}
```

## 9、修改字典

```
POST  /api/eventStats/v1/dict/update
```

请求参数：

| 序号 | 字段名称 | 字段类型 | 参数位置 | 是否必须 | 字段说明 |
| :--- | :------- | :------- | :------- | :------- | :------- |
| 1    | userId   | string   | header   | 是       | 用户id   |
| 2    | id       | string   | body     | 是       | 字典id   |
| 3    | cName    | string   | body     | 是       | 中文名称 |
| 4    | eName    | string   | body     | 是       | 英文名称 |
| 5    | remark   | string   | body     | 否       | 描述     |

请求示例：

```json
{
    "id": "34235235252"
    "cName": "日志类型",
    "eName": "log type",
    "remark": "xxx"
}
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 字段说明 |
| :--- | :------- | :------- | :------- |
| 1    | res      | string   | 响应结果 |

响应示例：

```json
{
    "res": "OK"
}
```

异常返回参数：

| 序号 | 参数         | 含义         |
| :--- | :----------- | :----------- |
| 1    | ErrorCode    | 错误码       |
| 2    | Description  | 错误描述     |
| 3    | Solution     | 错误处理建议 |
| 4    | ErrorDetails | 错误细节     |
| 5    | ErrorLink    | 错误信息地址 |

异常返回示例：

```json
{
    "ErrorCode": "EventStats.Common.ParameterError",
    "Description":  "Parameter error",
    "Solution": "",
    "ErrorDetails"：[],
    "ErrorLink": ""
}
```

## 10、删除字典

```
POST  /api/eventStats/v1/dict/delete
```

请求参数：

| 序号 | 字段名称 | 字段类型     | 参数位置 | 是否必须 | 字段说明   |
| :--- | :------- | :----------- | :------- | :------- | :--------- |
| 1    | userId   | string       | header   | 是       | 用户id     |
| 2    | ids      | list<string> | body     | 是       | 字典id列表 |

请求示例：

```json
{
    "ids": ["34235235252"]
}
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 字段说明 |
| :--- | :------- | :------- | :------- |
| 1    | res      | string   | 响应结果 |

响应示例：

```json
{
    "res": "OK"
}
```

异常返回参数：

| 序号 | 参数         | 含义         |
| :--- | :----------- | :----------- |
| 1    | ErrorCode    | 错误码       |
| 2    | Description  | 错误描述     |
| 3    | Solution     | 错误处理建议 |
| 4    | ErrorDetails | 错误细节     |
| 5    | ErrorLink    | 错误信息地址 |

异常返回示例：

```json
{
    "ErrorCode": "EventStats.Common.ParameterError",
    "Description":  "Parameter error",
    "Solution": "",
    "ErrorDetails"：[],
    "ErrorLink": ""
}
```

## 11、获取指定字典下的字典值列表

```
GET  /api/eventStats/v1/dict/itemList
```

请求参数：

| 序号 | 字段名称   | 字段类型 | 参数位置 | 是否必须 | 字段说明                                              |
| :--- | ---------- | :------- | -------- | -------- | :---------------------------------------------------- |
| 1    | fieldType  | int      | query    | 是       | 1-字典id  2-字典类型                                  |
| 2    | fieldValue | string   | query    | 是       | 字典id或字典类型                                      |
| 3    | key        | string   | query    | 否       | 模糊查询                                              |
| 4    | page       | int      | query    | 是       | 第几页，page>0                                        |
| 5    | size       | int      | query    | 是       | 当前页显示数量，size>0 \|size=-1（size=-1时查询所有） |

请求示例：

```
fieldType=1&fieldValue=xxx&key=dict&page=1&size=-1
```

响应参数：

| 序号 | 字段名称 |       |            | 字段类型     | 字段说明 |
| :--- | :------- | ----- | ---------- | :----------- | :------- |
| 1    | res      |       |            | string       | 响应结果 |
| 2    |          | total |            | int          | 总个数   |
| 3    |          | data  |            | list<object> | 具体结果 |
| 4    |          |       | id         | string       | 字典id   |
| 5    |          |       | cName      | string       | 中文名称 |
| 6    |          |       | eName      | string       | 英文名称 |
| 7    |          |       | remark     | string       | 描述     |
| 8    |          |       | dictId     | string       | 字典id   |
| 9    |          |       | itemValue  | string       | 数据值   |
| 10   |          |       | createBy   | string       | 创建人   |
| 11   |          |       | updateBy   | string       | 修改人   |
| 12   |          |       | createTime | string       | 创建时间 |
| 13   |          |       | updateTime | string       | 修改时间 |

响应示例：

```json
{
    "res": {
        "total": 3,
        "data": [
            {                
                "id": "7152263200732143616",
                "cName": "日志异常",
                "eName": "log error",
                "remark": "xxx",
                "dictId": "715226320073213463",
                "itemValue": "log error",
                "createBy":"1",
                "updateBy":"1", 
              	"createTime":"2023-12-29 17:14:55",
                "updateTime":"2023-12-29 17:14:55"
         	},
            ...
        ]
    }
}
```

异常返回参数：

| 序号 | 参数         | 含义         |
| :--- | :----------- | :----------- |
| 1    | ErrorCode    | 错误码       |
| 2    | Description  | 错误描述     |
| 3    | Solution     | 错误处理建议 |
| 4    | ErrorDetails | 错误细节     |
| 5    | ErrorLink    | 错误信息地址 |

异常返回示例：

```json
{
    "ErrorCode": "EventStats.Common.ParameterError",
    "Description":  "Parameter error",
    "Solution": "",
    "ErrorDetails"：[],
    "ErrorLink": ""
}
```

## 12、获取指定字典值详情

```
GET  /api/eventStats/v1/dict/item
```

请求参数：

| 序号 | 字段名称 | 字段类型 | 参数位置 | 是否必须 | 字段说明 |
| :--- | -------- | :------- | -------- | -------- | :------- |
| 1    | id       | string   | query    | 是       | 字典值id |

请求示例：

```
id=2342352354
```

响应参数：

| 序号 | 字段名称 |            | 字段类型 | 字段说明 |
| :--- | :------- | ---------- | :------- | :------- |
| 1    | res      |            | string   | 响应结果 |
| 2    |          | id         | string   | 字典id   |
| 3    |          | cName      | string   | 中文名称 |
| 4    |          | eName      | string   | 英文名称 |
| 5    |          | remark     | string   | 描述     |
| 6    |          | dictId     | string   | 字典id   |
| 7    |          | itemValue  | string   | 数据值   |
| 8    |          | createBy   | string   | 创建人   |
| 9    |          | updateBy   | string   | 修改人   |
| 10   |          | createTime | string   | 创建时间 |
| 11   |          | updateTime | string   | 修改时间 |

响应示例：

```json
{
    "res": {
        "itemId": "7152263200732143616",
        "cName": "日志异常",
        "eName": "log error",
        "remark": "日志的字典值-日志异常",
        "dictId": "7152263200732143615",
        "itemValue": "log error",
        "createBy":"1",
        "updateBy":"1",
        "createTime":"2023-12-29 17:14:55",
        "updateTime":"2023-12-29 17:14:55"
    }
}
```

异常返回参数：

| 序号 | 参数         | 含义         |
| :--- | :----------- | :----------- |
| 1    | ErrorCode    | 错误码       |
| 2    | Description  | 错误描述     |
| 3    | Solution     | 错误处理建议 |
| 4    | ErrorDetails | 错误细节     |
| 5    | ErrorLink    | 错误信息地址 |

异常返回示例：

```json
{
    "ErrorCode": "EventStats.Common.ParameterError",
    "Description":  "Parameter error",
    "Solution": "",
    "ErrorDetails"：[],
    "ErrorLink": ""
}
```

## 13、新建字典值

```
POST  /api/eventStats/v1/dict/addItem
```

请求参数：

| 序号 | 字段名称  | 字段类型 | 参数位置 | 是否必须 | 字段说明 |
| :--- | :-------- | :------- | :------- | :------- | :------- |
| 1    | userId    | string   | header   | 是       | 用户id   |
| 2    | cName     | string   | body     | 是       | 中文名称 |
| 3    | eName     | string   | body     | 是       | 英文名称 |
| 4    | remark    | string   | body     | 否       | 描述     |
| 5    | dictId    | string   | body     | 是       | 字典id   |
| 6    | itemValue | string   | body     | 否       | 数据值   |

请求示例：

```json
{
    "cName": "日志类型",
    "eName": "log type",
    "remark": "xxx",
    "dictId": "2342352354",
    "itemValue": "error"
}
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 字段说明 |
| :--- | :------- | :------- | :------- |
| 1    | res      | string   | 响应结果 |

响应示例：

```json
{
    "res": "OK"
}
```

异常返回参数：

| 序号 | 参数         | 含义         |
| :--- | :----------- | :----------- |
| 1    | ErrorCode    | 错误码       |
| 2    | Description  | 错误描述     |
| 3    | Solution     | 错误处理建议 |
| 4    | ErrorDetails | 错误细节     |
| 5    | ErrorLink    | 错误信息地址 |

异常返回示例：

```json
{
    "ErrorCode": "EventStats.Common.ParameterError",
    "Description":  "Parameter error",
    "Solution": "",
    "ErrorDetails"：[],
    "ErrorLink": ""
}
```

## 14、修改字典值

```
POST  /api/eventStats/v1/dict/updateItem
```

请求参数：

| 序号 | 字段名称  | 字段类型 | 参数位置 | 是否必须 | 字段说明 |
| :--- | :-------- | :------- | :------- | :------- | :------- |
| 1    | userId    | string   | header   | 是       | 用户id   |
| 2    | id        | string   | body     | 是       | 字典值id |
| 3    | cName     | string   | body     | 是       | 中文名称 |
| 4    | eName     | string   | body     | 是       | 英文名称 |
| 5    | remark    | string   | body     | 否       | 描述     |
| 6    | itemValue | string   | body     | 否       | 数据值   |

请求示例：

```json
{
    "id": "34235235252"
    "cName": "日志类型",
    "eName": "log type",
    "remark": "xxx",
    "itemValue": "error"
}
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 字段说明 |
| :--- | :------- | :------- | :------- |
| 1    | res      | string   | 响应结果 |

响应示例：

```json
{
    "res": "OK"
}
```

异常返回参数：

| 序号 | 参数         | 含义         |
| :--- | :----------- | :----------- |
| 1    | ErrorCode    | 错误码       |
| 2    | Description  | 错误描述     |
| 3    | Solution     | 错误处理建议 |
| 4    | ErrorDetails | 错误细节     |
| 5    | ErrorLink    | 错误信息地址 |

异常返回示例：

```json
{
    "ErrorCode": "EventStats.Common.ParameterError",
    "Description":  "Parameter error",
    "Solution": "",
    "ErrorDetails"：[],
    "ErrorLink": ""
}
```

## 15、删除字典值

```
POST  /api/eventStats/v1/dict/deleteItem
```

请求参数：

| 序号 | 字段名称 | 字段类型     | 参数位置 | 是否必须 | 字段说明     |
| :--- | :------- | :----------- | :------- | :------- | :----------- |
| 1    | userId   | string       | header   | 是       | 用户id       |
| 2    | ids      | list<string> | body     | 是       | 字典值id列表 |

请求示例：

```json
{
    "ids": ["34235235252"]
}
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 字段说明 |
| :--- | :------- | :------- | :------- |
| 1    | res      | string   | 响应结果 |

响应示例：

```json
{
    "res": "OK"
}
```

异常返回参数：

| 序号 | 参数         | 含义         |
| :--- | :----------- | :----------- |
| 1    | ErrorCode    | 错误码       |
| 2    | Description  | 错误描述     |
| 3    | Solution     | 错误处理建议 |
| 4    | ErrorDetails | 错误细节     |
| 5    | ErrorLink    | 错误信息地址 |

异常返回示例：

```json
{
    "ErrorCode": "EventStats.Common.ParameterError",
    "Description":  "Parameter error",
    "Solution": "",
    "ErrorDetails"：[],
    "ErrorLink": ""
}
```

## 16、获取首页事件

```
GET  /api/eventStats/v1/event_log/getHomeEventList/{modType}
```

请求参数：

| 序号 | 字段名称 | 字段类型 | 参数位置 | 是否必须 | 字段说明                               |
| :--- | -------- | :------- | -------- | -------- | :------------------------------------- |
| 1    | userId   | string   | header   | 是       | 用户id (通过全局header传递,或者cookie) |
| 2    | modType  | int      | body     | 是       | 模块类型（1-模型工厂、2-知识网络...）  |

请求示例：

```
modType=1
```

响应参数：

| 序号 | 字段名称 |      |            | 字段类型     | 字段说明 |
| :--- | :------- | ---- | ---------- | :----------- | :------- |
| 1    | res      |      |            | string       | 响应结果 |
| 3    |          | data |            | list<object> | 具体结果 |
| 5    |          |      | title      | string       | 标题     |
| 6    |          |      | remark     | string       | 描述     |
| 12   |          |      | createTime | string       | 创建时间 |

响应示例：

```json
{
    "res": {
        "data": [
            {
                "title": "document",
                "remark": "北京大学统一日志管理案例解读-V1.0.pptx",
                "createTime": "2024-12-05 10:50:2",
            },
            ...
        ]
    }
}
```

异常返回参数：

| 序号 | 参数         | 含义         |
| :--- | :----------- | :----------- |
| 1    | ErrorCode    | 错误码       |
| 2    | Description  | 错误描述     |
| 3    | Solution     | 错误处理建议 |
| 4    | ErrorDetails | 错误细节     |
| 5    | ErrorLink    | 错误信息地址 |

异常返回示例：

```json
{
    "ErrorCode": "EventStats.Common.ParameterError",
    "Description":  "Parameter error",
    "Solution": "",
    "ErrorDetails"：[],
    "ErrorLink": ""
}
```

## 17、埋点事件

```
POST  /api/eventStats/v1/event_log/add
```

请求参数：

| 序号 | 字段名称 | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明                               |
| :--- | :------- | :------- | -------- | :------- | :--- | :------------------------------------- |
| 1    | userId   | string   | header   | 是       |      | 用户id (通过全局header传递,或者cookie) |
| 2    | modType  | int      | body     | 是       | 1    | 模块类型（1-模型工厂、2-知识网络）     |
| 3    | title    | string   | body     | 是       | 50   | 标题/名称                              |
| 4    | path     | string   | body     | 是       | 150  | 路径                                   |
| 5    | remark   | string   | body     | 是       | 255  | 描述                                   |
| 6    | method   | string   | body     | 否       | 10   | 请求方式 GET、POST、PUT                |

请求示例：

```json
{
    "modType": 1,
    "title": "document",
    "path": "xxx",
    "remark": "北京大学统一日志管理案例解读-V1.0.pptx",
    "method": "GET",
}
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 字段说明 |
| :--- | :------- | :------- | :------- |
| 1    | res      | string   | 响应结果 |

响应示例：

```json
{
    "res": "OK"
}
```

异常返回参数：

| 序号 | 参数         | 含义         |
| :--- | :----------- | :----------- |
| 1    | ErrorCode    | 错误码       |
| 2    | Description  | 错误描述     |
| 3    | Solution     | 错误处理建议 |
| 4    | ErrorDetails | 错误细节     |
| 5    | ErrorLink    | 错误信息地址 |

异常返回示例：

```json
{
    "ErrorCode": "EventStats.Common.ParameterError",
    "Description":  "Parameter error",
    "Solution": "",
    "ErrorDetails"：[],
    "ErrorLink": ""
}
```

