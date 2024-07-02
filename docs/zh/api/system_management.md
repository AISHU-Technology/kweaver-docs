# 一、系统管理
##  1、菜单管理
### 1.1、获取菜单列表

```
GET  /api/eventStats/v1/menu/list
```

请求参数：

| 序号 | 字段名称 | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明                                               |
| :--- | :------- | :------- | :------- | :------- | ---- | :----------------------------------------------------- |
| 1    | pid      | string   | query    | 否       | 20   | 父资源，pid>=0，默认0不使用                            |
| 2    | isTree   | int      | query    | 是       |      | 是否以树形结构返回，1-是，2-否                         |
| 3    | menuType | int      | query    | 否       |      | 1-菜单 2-按钮 3-所有                                 |
| 4    | key      | string   | query    | 否       | 255  | 模糊查询中英文名称及菜单编码                           |
| 5    | page     | int      | query    | 是       |      | 第几页，page>0                                         |
| 6    | size     | int      | query    | 是       |      | 当前页显示数量，size>0 \| size=-1（size=-1时查询所有） |

请求示例：

```
pid=124124124124&isTree=1&menuType=1&key=menu&page=5&size=10
```

响应参数：

| 序号 | 字段名称 | 字段类型     | 字段说明 |
| :--- | -------- | :----------- | :------- |
| 1    | total    | int          | 总个数   |
| 2    | data     | list<object> | 具体结果 |

| 序号 | 字段名称     | 字段类型     | 字段说明                       |
| :--- | ------------ | :----------- | :----------------------------- |
| 1    | id           | string       | 菜单id                         |
| 2    | cName        | string       | 中文名称                       |
| 3    | eName        | string       | 英文名称                       |
| 4    | code         | string       | 菜单编码                       |
| 5    | icon         | string       | 默认图标                       |
| 6    | selectedIcon | string       | 选中图标                       |
| 7    | path         | string       | 绝对路径                       |
| 8    | component    | string       | 组件路径                       |
| 9    | menuType     | int          | 菜单类型 （1-菜单 2-按钮）      |
| 10   | pid          | string       | 父菜单id                       |
| 11   | sortOrder    | int          | 排序数值                       |
| 11   | visible      | int          | 是否显示（0-显示 1-不显示） |
| 12   | createTime   | string       | 创建时间                       |
| 13   | updateTime   | string       | 修改时间                       |
| 14   | delFlag      | int          | 删除标识（0-未删除 1-已删除）  |
| 15   | children     | list<object> | 下级菜单列表                   |

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
                "visible": 0,
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
                        "visible": 0,
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

### 1.2、获取指定菜单详情

```
GET  /api/eventStats/v1/menu
```

请求参数：

| 序号 | 字段名称 | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明 |
| :--- | :------- | :------- | :------- | :------- | ---- | :------- |
| 1    | id       | string   | query    | 是       | 20   | 菜单id   |

请求示例：

```
id=124124124124
```

响应参数：

| 序号 | 字段名称     | 字段类型     | 字段说明                       |
| :--- | ------------ | :----------- | :----------------------------- |
| 1    | id           | string       | 菜单id                         |
| 2    | cName        | string       | 中文名称                       |
| 3    | eName        | string       | 英文名称                       |
| 4    | code         | string       | 菜单编码                       |
| 5    | icon         | string       | 默认图标                       |
| 6    | selectedIcon | string       | 选中图标                       |
| 7    | path         | string       | 绝对路径                       |
| 8    | component    | string       | 组件路径                       |
| 9    | menuType     | int          | 菜单类型 （1-菜单 2-按钮） |
| 10   | pid          | string       | 父菜单id                       |
| 11   | sortOrder    | int          | 排序数值                       |
| 12   | visible      | int          | 是否显示（0-显示 1-不显示）    |
| 13   | createTime   | string       | 创建时间                       |
| 14   | updateTime   | string       | 修改时间                       |
| 15   | delFlag      | int          | 删除标识（0-未删除 1-已删除）  |
| 16   | children     | list<object> | 下级菜单列表                   |

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

### 1.3、新建菜单

```
POST  /api/eventStats/v1/menu/add
```

请求参数：

| 序号 | 字段名称     | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明                       |
| :--- | ------------ | :------- | -------- | -------- | ---- | :----------------------------- |
| 1    | cName        | string   | body     | 是       | 128  | 中文名称                       |
| 2    | eName        | string   | body     | 是       | 128  | 英文名称                       |
| 3    | code         | string   | body     | 是       | 255  | 菜单编码                       |
| 4    | icon         | string   | body     | 否       | 128  | 默认图标                       |
| 5    | selectedIcon | string   | body     | 否       | 128  | 选中图标                       |
| 6    | path         | string   | body     | 否       | 128  | 绝对路径                       |
| 7    | component    | string   | body     | 否       | 255  | 组件路径                       |
| 8    | menuType     | int      | body     | 是       |      | 菜单类型 （1-菜单 2-按钮） |
| 9    | pid          | string   | body     | 否       | 20   | 父菜单id                       |
| 10   | sortOrder    | int      | body     | 否       |      | 排序数值                       |
| 11   | visible      | int      | body     | 否       |      | 是否显示（0-显示 1-不显示）    |

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

### 1.4、修改菜单

```
POST  /api/eventStats/v1/menu/update
```

请求参数：

| 序号 | 字段名称     | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明                       |
| :--- | ------------ | :------- | -------- | -------- | ---- | :----------------------------- |
| 1    | id           | string   | body     | 是       | 20   | 菜单id                         |
| 2    | cName        | string   | body     | 是       | 128  | 中文名称                       |
| 3    | eName        | string   | body     | 是       | 128  | 英文名称                       |
| 4    | icon         | string   | body     | 否       | 128  | 默认图标                       |
| 5    | selectedIcon | string   | body     | 否       | 128  | 选中图标                       |
| 6    | path         | string   | body     | 否       | 128  | 绝对路径                       |
| 7    | component    | string   | body     | 否       | 255  | 组件路径                       |
| 8    | menuType     | int      | body     | 是       |      | 菜单类型 （1-菜单 2-按钮） |
| 9    | pid          | string   | body     | 否       | 20   | 父菜单id                       |
| 10   | sortOrder    | int      | body     | 否       |      | 排序数值                       |
| 11   | visible      | int      | body     | 否       |      | 是否显示（0-显示 1-不显示）    |

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

### 1.5、删除菜单

```
POST  /api/eventStats/v1/menu/delete
```

请求参数：

| 序号 | 字段名称 | 字段类型     | 参数位置 | 是否必须 | 长度 | 字段说明   |
| :--- | -------- | :----------- | -------- | -------- | ---- | :--------- |
| 1    | ids      | list<string> | body     | 是       | 20   | 菜单id列表 |

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
### 1.6、获取菜单树

```
GET  /api/eventStats/v1/menu/tree
```

请求参数：

| 序号 | 字段名称 | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明              |
| :--- | :------- | :------- | :------- | :------- | ---- | :-------------------- |
| 1    | pid      | string   | query    | 否       | 20   | 父资源，pid>=0，默认0 |

请求示例：

```
/api/eventStats/v1/menu/tree?pid=124124124124
```

响应参数：

| 序号 | 字段名称     | 字段类型     | 字段说明                      |
| :--- | ------------ | :----------- | :---------------------------- |
| 1    | id           | string       | 菜单id                        |
| 2    | cName        | string       | 中文名称                      |
| 3    | eName        | string       | 英文名称                      |
| 4    | code         | string       | 菜单编码                      |
| 5    | icon         | string       | 默认图标                      |
| 6    | selectedIcon | string       | 选中图标                      |
| 7    | path         | string       | 绝对路径                      |
| 8    | component    | string       | 组件路径                      |
| 9    | menuType     | int          | 菜单类型 （1-菜单 2-按钮）    |
| 10   | pid          | string       | 父菜单id                      |
| 11   | sortOrder    | int          | 排序数值                      |
| 11   | visible      | int          | 是否显示（0-显示 1-不显示）   |
| 12   | createTime   | string       | 创建时间                      |
| 13   | updateTime   | string       | 修改时间                      |
| 14   | delFlag      | int          | 删除标识（0-未删除 1-已删除） |
| 15   | children     | list<object> | 下级菜单列表                  |

响应示例：

```json
{
    "res": [              
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

## 2、字典管理
### 2.1、获取字典列表

```
GET  /api/eventStats/v1/dict/list
```

请求参数：

| 序号 | 字段名称 | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明                                              |
| :--- | -------- | :------- | -------- | -------- | ---- | :---------------------------------------------------- |
| 1    | key      | string   | query    | 否       | 150  | 模糊查询                                              |
| 2    | page     | int      | query    | 是       |      | 第几页，page>0                                        |
| 3    | size     | int      | query    | 是       |      | 当前页显示数量，size>0 \|size=-1（size=-1时查询所有） |

请求示例：

```
key=dict&page=1&size=-1
```

响应参数：

| 序号 | 字段名称 | 字段类型     | 字段说明 |
| :--- | -------- | :----------- | :------- |
| 1    | total    | int          | 总个数   |
| 2    | data     | list<object> | 具体结果 |

| 序号 | 字段名称   | 字段类型 | 字段说明 |
| :--- | ---------- | :------- | :------- |
| 1    | id         | string   | 字典id   |
| 2    | cName      | string   | 中文名称 |
| 3    | eName      | string   | 英文名称 |
| 4    | remark     | string   | 描述     |
| 5    | dictType   | string   | 字典类型 |
| 6    | createBy   | string   | 创建人   |
| 7    | updateBy   | string   | 修改人   |
| 8    | createTime | string   | 创建时间 |
| 9    | updateTime | string   | 修改时间 |

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

### 2.2、获取指定字典详情

```
GET  /api/eventStats/v1/dict
```

请求参数：

| 序号 | 字段名称 | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明 |
| :--- | -------- | :------- | -------- | -------- | ---- | :------- |
| 1    | id       | string   | query    | 是       | 20   | 字典id   |

请求示例：

```
id=2342352354
```

响应参数：

| 序号 | 字段名称   | 字段类型 | 字段说明 |
| :--- | ---------- | :------- | :------- |
| 1    | id         | string   | 字典id   |
| 2    | cName      | string   | 中文名称 |
| 3    | eName      | string   | 英文名称 |
| 4    | remark     | string   | 描述     |
| 5    | dictType   | string   | 字典类型 |
| 6    | createBy   | string   | 创建人   |
| 7    | updateBy   | string   | 修改人   |
| 8    | createTime | string   | 创建时间 |
| 9    | updateTime | string   | 修改时间 |

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

### 2.3、新建字典

```
POST  /api/eventStats/v1/dict/add
```

请求参数：

| 序号 | 字段名称 | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明 |
| :--- | :------- | :------- | :------- | :------- | ---- | :------- |
| 1    | userId   | string   | header   | 是       | 50   | 用户id   |
| 2    | cName    | string   | body     | 是       | 100  | 中文名称 |
| 3    | eName    | string   | body     | 是       | 150  | 英文名称 |
| 4    | remark   | string   | body     | 否       | 255  | 描述     |
| 5    | dictType | string   | body     | 是       | 50   | 字典类型 |

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

### 2.4、修改字典

```
POST  /api/eventStats/v1/dict/update
```

请求参数：

| 序号 | 字段名称 | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明 |
| :--- | :------- | :------- | :------- | :------- | ---- | :------- |
| 1    | userId   | string   | header   | 是       | 50   | 用户id   |
| 2    | id       | string   | body     | 是       | 20   | 字典id   |
| 3    | cName    | string   | body     | 是       | 100  | 中文名称 |
| 4    | eName    | string   | body     | 是       | 150  | 英文名称 |
| 5    | remark   | string   | body     | 否       | 255  | 描述     |

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

### 2.5、删除字典

```
POST  /api/eventStats/v1/dict/delete
```

请求参数：

| 序号 | 字段名称 | 字段类型     | 参数位置 | 是否必须 | 长度 | 字段说明   |
| :--- | :------- | :----------- | :------- | :------- | ---- | :--------- |
| 1    | userId   | string       | header   | 是       | 50   | 用户id     |
| 2    | ids      | list<string> | body     | 是       | 20   | 字典id列表 |

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

### 2.6、获取指定字典下的字典值列表

```
GET  /api/eventStats/v1/dict/itemList
```

请求参数：

| 序号 | 字段名称   | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明                                              |
| :--- | ---------- | :------- | -------- | -------- | ---- | :---------------------------------------------------- |
| 1    | fieldType  | int      | query    | 是       |      | 1-字典id  2-字典类型                                  |
| 2    | fieldValue | string   | query    | 是       | 50   | 字典id或字典类型                                      |
| 3    | key        | string   | query    | 否       | 150  | 模糊查询                                              |
| 4    | page       | int      | query    | 是       |      | 第几页，page>0                                        |
| 5    | size       | int      | query    | 是       |      | 当前页显示数量，size>0 \|size=-1（size=-1时查询所有） |

请求示例：

```
fieldType=1&fieldValue=xxx&key=dict&page=1&size=-1
```

响应参数：

| 序号 | 字段名称 | 字段类型     | 字段说明 |
| :--- | -------- | :----------- | :------- |
| 1    | total    | int          | 总个数   |
| 2    | data     | list<object> | 具体结果 |

| 序号 | 字段名称   | 字段类型 | 字段说明 |
| :--- | ---------- | :------- | :------- |
| 1    | id         | string   | 字典id   |
| 2    | cName      | string   | 中文名称 |
| 3    | eName      | string   | 英文名称 |
| 4    | remark     | string   | 描述     |
| 5    | dictId     | string   | 字典id   |
| 6    | itemValue  | string   | 数据值   |
| 7    | createBy   | string   | 创建人   |
| 8    | updateBy   | string   | 修改人   |
| 9    | createTime | string   | 创建时间 |
| 10   | updateTime | string   | 修改时间 |

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

### 2.7、获取指定字典值详情

```
GET  /api/eventStats/v1/dict/item
```

请求参数：

| 序号 | 字段名称 | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明 |
| :--- | -------- | :------- | -------- | -------- | ---- | :------- |
| 1    | id       | string   | query    | 是       | 20   | 字典值id |

请求示例：

```
id=2342352354
```

响应参数：

| 序号 | 字段名称   | 字段类型 | 字段说明 |
| :--- | ---------- | :------- | :------- |
| 1    | id         | string   | 字典id   |
| 2    | cName      | string   | 中文名称 |
| 3    | eName      | string   | 英文名称 |
| 4    | remark     | string   | 描述     |
| 5    | dictId     | string   | 字典id   |
| 6    | itemValue  | string   | 数据值   |
| 7    | createBy   | string   | 创建人   |
| 8    | updateBy   | string   | 修改人   |
| 9    | createTime | string   | 创建时间 |
| 10   | updateTime | string   | 修改时间 |

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

### 2.8、新建字典值

```
POST  /api/eventStats/v1/dict/addItem
```

请求参数：

| 序号 | 字段名称  | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明 |
| :--- | :-------- | :------- | :------- | :------- | ---- | :------- |
| 1    | userId    | string   | header   | 是       | 50   | 用户id   |
| 2    | cName     | string   | body     | 是       | 100  | 中文名称 |
| 3    | eName     | string   | body     | 是       | 150  | 英文名称 |
| 4    | remark    | string   | body     | 否       | 255  | 描述     |
| 5    | dictId    | string   | body     | 是       | 20   | 字典id   |
| 6    | itemValue | string   | body     | 否       | 100  | 数据值   |

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

### 2.9、修改字典值

```
POST  /api/eventStats/v1/dict/updateItem
```

请求参数：

| 序号 | 字段名称  | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明 |
| :--- | :-------- | :------- | :------- | :------- | ---- | :------- |
| 1    | userId    | string   | header   | 是       | 50   | 用户id   |
| 2    | id        | string   | body     | 是       | 20   | 字典值id |
| 3    | cName     | string   | body     | 是       | 100  | 中文名称 |
| 4    | eName     | string   | body     | 是       | 150  | 英文名称 |
| 5    | remark    | string   | body     | 否       | 255  | 描述     |
| 6    | itemValue | string   | body     | 否       | 100  | 数据值   |

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

### 2.10、删除字典值

```
POST  /api/eventStats/v1/dict/deleteItem
```

请求参数：

| 序号 | 字段名称 | 字段类型     | 参数位置 | 是否必须 | 长度 | 字段说明     |
| :--- | :------- | :----------- | :------- | :------- | ---- | :----------- |
| 1    | userId   | string       | header   | 是       | 50   | 用户id       |
| 2    | ids      | list<string> | body     | 是       | 20   | 字典值id列表 |

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
