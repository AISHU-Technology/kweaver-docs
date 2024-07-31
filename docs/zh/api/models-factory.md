# 一、模型工厂
## 1、大模型接入管理
### 1.1、获取大模型列表

```
GET  /api/model-factory/v1/llm/page
```

请求参数：

| 序号 | 字段名称 | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明                                                     |
| :--- | :------- | :------- | -------- | :------- | ---- | :----------------------------------------------------------- |
| 1    | page     | int      | query    | 是       |      | 页码                                                         |
| 2    | size     | int      | query    | 是       |      | 每页数量                                                     |
| 3    | order    | string   | query    | 否       | 4    | 默认按从新至旧排序，接受参数为：'desc'（从新到旧），'asc'（从旧到新） |
| 4    | name     | string   | query    | 否       | 100  | 对LLM进行模糊搜索，不填此参数则返回所有                      |
| 5    | rule     | string   | query    | 否       | 11   | 默认按照更新时间排序，接受参数为：'update_time'（按LLM更新时间排序），'create_time'（按LLM创建时间排序）,'model_name'（按LLM名称排序）" |
| 6    | series   | string   | query    | 否       | 50   | 对LLM模型进行筛选，接参数为：‘all’（默认所有供应商），‘openai‘（openai模型），'aishu_baichuan'（本地部署模型） |

请求示例：

```
page=5&size=10&order=desc&name=baichuan-llm&rule=update_time&series=openai
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 字段说明       |
| :--- | -------- | :------- | :------------- |
| 1    | total    | int      | 回复信息的个数 |
| 2    | data     | list     | 回复的信息     |

| 序号 | 字段名称     | 字段类型  | 字段说明                   |
| :--- | ------------ | :-------- | :------------------------- |
| 1    | model_id     | string    | 模型id                     |
| 2    | model_series | string    | 模型归属的供应商           |
| 3    | model_name   | string    | 模型的名称（用户修改后的） |
| 4    | model        | string    | 本身的模型名称             |
| 5    | model_api    | string    | 目前返回null               |
| 6    | create_time  | timestamp | 创建时间                   |
| 7    | create_by    | string    | 创建人                     |
| 8    | update_time  | timestamp | 更新时间                   |
| 9    | update_by    | string    | 更新人                     |

响应示例：

```json
{
    "res": {
        "total": 2,
        "data": [
            {
                "model_id": "1234567890123456789",
                "model_name": "这是一个名称",
                "model_series": "openai",
                "model": "gpt-35-turbo-16k",
                "model_api": "",
                "create_time": "1682870400",
                "create_by": "zhang",
                "update_time": "1682870400",
                "update_by": "li"
            },
            {
                "model_id": "8452567890123456542",
                "model_name": "这是一个名称",
                "model_series": "aishu-baichuan",
                "model": "gpt-35-turbo-16k",
                "model_api": "",
                "create_time": "1682870400",
                "create_by": "zhang",
                "update_time": "1682870400",
                "update_by": "li"
            },
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
    "ErrorCode": "ModelFactory.Mydb.DataBase.ParameterError",
    "Description": "数据库连接失败",
    "Solution": "请核对数据库的连接参数.",
    "ErrorDetails": "数据库登录信息错误",
    "ErrorLink": ""
}
```

### 1.2、新增大模型-参数获取

```
GET  /api/model-factory/v1/llm/param
```

请求参数：无

请求示例：无

响应参数：

| 序号 | 字段名称 | 字段类型 | 字段说明                               |
| :--- | -------- | :------- | :------------------------------------- |
| 1    | openai   | string   | 系列名称中的一种，另一种是本地部署模型 |

| 序号 | 字段名称 | 字段类型 | 字段说明     |
| :--- | -------- | :------- | :----------- |
| 3    | title    | string   | 模型系列名称 |
| 4    | icon     | string   | 前端配置信息 |
| 5    | formData | list     | 参数数据     |

| 序号 | 字段名称    | 字段类型     | 字段说明                                                     |
| :--- | :---------- | :----------- | :----------------------------------------------------------- |
| 1    | field       | string       | 参数名称                                                     |
| 2    | component   | string       | 前端输入框的类型：输入框(input) \| 文本框(textarea) \| 下拉框(selector) \| 单选(radio) \| 多选(checkbox) |
| 3    | type        | string       | 输入框支持的数据类型：字符串(string) \| 数值(number) \| 布尔(boolean) \| 数组(array) \| 字典或对象(object) |
| 4    | label       | object       | 参数在前端展示的标签名称                                     |
| 5    | placeholder | object       | 缺醒水印                                                     |
| 6    | rules       | list<object> | 校验信息                                                     |

| 序号 | 字段名称 | 字段类型 | 字段说明             |
| :--- | -------- | :------- | :------------------- |
| 1    | required | boolean  | 是否必填             |
| 2    | max      | int      | 最大长度，或者最大值 |
| 3    | pattern  | string   | 正则化校验规则       |
| 4    | message  | object   | 违反约束提示信息     |

响应示例：

```json
{
    'res': [
        {
            'openai': {
                'title': 'OpenAI',
                'icon': '<svg t="1698303912304" class="icon" viewBox="0 0 1024 1024"/2000/svg"... ',
                'formData': [
                    {
                        'field': 'name',
                        'component': 'input',
                        'type': 'string',
                        'label': {
                            'zh-CN': '模型名称',
                            'en-US': 'Model name'
                        },
                        'placeholder': {
                            'zh-CN': '请输入',
                            'en-US': 'Please enter'
                        },
                        'rules': [
                            {
                                'required': True,
                                'message': {
                                    'zh-CN': '此项不允许为空',
                                    'en-US': 'The value cannot be null'}
                            },
                            {
                                'max': 50,
                                'message': {
                                    'zh-CN': '最多50个字符',
                                    'en-US': 'Enter up to 50 characters'}
                            },
                            {
                                'pattern': '^[\\\\s\u4e00-\u9fa5a-zA-Z0-9!-~？！，、；。……：“”‘’（）｛｝《》【】～￥—·]+$',
                                'message': {
                                    'zh-CN': '仅支持输入中英文、数字及键盘上的特殊字符号',
                                    'en-US': 'Only support Chinese and English, numbers and special characters on the keyboard'
                                }
                            }
                        ]
                    }
                ]
            }
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
    "ErrorCode": "ModelFactory.Mydb.DataBase.ParameterError",
    "Description": "数据库连接失败",
    "Solution": "请核对数据库的连接参数.",
    "ErrorDetails": "数据库登录信息错误",
    "ErrorLink": ""
}
```

### 1.3、测试大模型

```
POST  /api/model-factory/v1/llm/test
```

请求参数：

第一种测试方式，新增测试

| 序号 | 字段名称     | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明                                                     |
| :--- | :----------- | :------- | -------- | :------- | ---- | :----------------------------------------------------------- |
| 1    | model_series | string   | body     | 是       | 50   | 模型系列类型，例如：openai，本地部署模型                     |
| 2    | model_config | object   | body     | 是       |      | 当前模型的配置信息，模型系列不同，所需参数不同，例如openai需要api_key，api_model，具体参数参考示例 |

请求示例：

```json
openai：api_key, api_model
{  
     "model_series": "openai",
     "model_config": {
        "api_key": 56pf5cd7654c4oe9a9dd36059198a152,
        "api_model": "gpt-35-turbo-16k"
    }
}
本地部署模型：api_base, api_key, api_model
{
    "model_series": "本地部署模型",
    "model_config": {
        "api_base": "http://0.0.0.0:8000/v1",
        "api_type": "openai",
        "api_model": "baichuan2" 
    }      
}
```

第二种测试方式，数据保存到数据库后的测试

| 序号 | 字段名称 | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明 |
| :--- | :------- | :------- | -------- | :------- | ---- | :------- |
| 1    | model_id | string   | body     | 是       | 50   | 模型id   |

请求示例：

```json
{
     "model_id": "1561231354612313546"
}
```

响应参数：

| 序号 | 字段名称   | 字段类型 | 字段说明                                 |
| :--- | ---------- | :------- | :--------------------------------------- |
| 1    | status     | boolean  | 验证的状态：True，False                  |
| 2    | model_type | string   | 验证成功后返回的模型类型，验证失败为空值 |

响应示例：

```json
{
    "res":
        {
            "status": True,
            "model_type": "chat"
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
    "ErrorCode": "ModelFactory.ConnectController.LLMTest.ParameterError",
    "Description": "当前参数不符合输入规则",
    "Solution": "请修改输入信息.",
    "ErrorDetails": "",
    "ErrorLink": ""
}
```

### 1.4、新增大模型-数据保存

```
POST  /api/model-factory/v1/llm/add
```

请求参数：

| 序号 | 字段名称     | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明                                       |
| :--- | :----------- | :------- | -------- | :------- | ---- | :--------------------------------------------- |
| 1    | model_series | string   | body     | 是       | 50   | 模型系列供应商：openai，aishu-baichuan         |
| 2    | model_type   | string   | body     | 是       | 50   | 模型类型：chat，completion                     |
| 3    | model_config | object   | body     | 是       |      | 当前模型的配置信息，模型系列不同，所需参数不同 |
| 4    | model_name   | string   | body     | 是       | 100  | 模型名称                                       |

请求示例：

```json
openai：api_key, api_model
{  
     "model_series": "openai",
     "model_type": "chat",
     "model_config": {
        "api_key": 56pf5cd7654c4oe9a9dd36059198a152,
        "api_model": "gpt-35-turbo-16k"
    },
    "model_name": "test_name"
}
aishu-baichuan：api_base, api_key, api_model
{
    "model_series": "aishu-baichuan",
    "model_type": "chat",
    "model_config": {
        "api_base": "http://0.0.0.0:8000/v1",
        "api_type": "openai",
        "api_model": "baichuan2" 
    },
    "model_name": "test_name"
}
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 字段说明     |
| :--- | -------- | :------- | :----------- |
| 1    | res      | boolean  | 模型保存结果 |

响应示例：

```json
{
    "res": True
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
    "ErrorCode": "ModelFactory.ConnectController.LLMAdd.ParameterError",
    "Description": "参数校验异常",
    "Solution": "请核对输入信息.",
    "ErrorDetails": "输入参数不能为空",
    "ErrorLink": ""
}
```

### 1.5、删除大模型

```
POST  /api/model-factory/v1/llm/delete
```

请求参数：

| 序号 | 字段名称 | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明 |
| :--- | :------- | :------- | -------- | :------- | ---- | :------- |
| 1    | model_id | string   | body     | 是       | 50   | 模型id   |

请求示例：

```json
{
    "model_id": "1234567890123456789"
}
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 字段说明     |
| :--- | -------- | :------- | :----------- |
| 1    | res      | boolean  | 模型删除结果 |

响应示例：

```json
{
    "res": True
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
    "ErrorCode": "ModelFactory.ConnectController.LLMRemove.ParameterError",
    "Description": "输入参数异常",
    "Solution": "请核对输入信息.",
    "ErrorDetails": "当前模型不存在",
    "ErrorLink": ""
}
```

### 1.6、查看大模型

```
GET  /api/model-factory/v1/llm/detail
```

请求参数：

| 序号 | 字段名称 | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明 |
| :--- | :------- | :------- | -------- | :------- | ---- | :------- |
| 1    | model_id | string   | query    | 是       | 50   | 模型id   |

请求示例：

```
model_id=1234567890123456789
```

响应参数：

| 序号 | 字段名称     | 字段类型 | 字段说明                                           |
| :--- | ------------ | :------- | :------------------------------------------------- |
| 1    | model_id     | string   | 模型id                                             |
| 2    | model_series | string   | 模型的供应商名称：aishu-baichuan、openai           |
| 3    | model_name   | string   | 模型名称（不是model，model和model_name都代表名称） |
| 4    | model_url    | string   | 模型url                                            |
| 5    | model_config | object   | 模型的配置信息，模型系列不同，配置参数不同         |

响应示例：

```json
{
    "res":
        {
            "model_id": "1234567890123456789",
            "model_series": "aishu-baichuan",
            "model_name": "模型名称",
            "model_config": {
                "api_base": "http://0.0.0.0:8000/v1",
                "api_type": "openai",
                "api_model": "baichuan2"
            },
            "model_url": "/api/model-factory/v1/llm-used/1234567890123456789"
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
    "ErrorCode": "ModelFactory.Mydb.DataBase.ParameterError",
    "Description": "数据库连接失败",
    "Solution": "请核对数据库的连接参数.",
    "ErrorDetails": "数据库登录信息错误",
    "ErrorLink": ""
}
```

### 1.7、修改大模型配置

```
POST  /api/factory/v1/llm/edit
```

请求参数：

| 序号 | 字段名称       | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明                                   |
| :--- | :------------- | :------- | -------- | :------- | ---- | :----------------------------------------- |
| 1    | model_id       | string   | body     | 是       | 50   | 模型id                                     |
| 2    | model_series   | string   | body     | 是       | 50   | 模型的供应商名称：aishu-baichuan、openai   |
| 3    | model_name     | string   | body     | 是       | 100  | 模型名称                                   |
| 4    | model_describe | string   | body     | 否       | 255  | 模型的描述                                 |
| 5    | model_config   | object   | body     | 是       |      | 模型的配置信息，模型系列不同，配置参数不同 |

请求示例：

```json
{
    "model_id":"1234567890123456789",
    "model_series": "aishu-baichuan",
    "model_name": "这是一个名字",
    "model_config": {
        "api_base": "http://0.0.0.0:8000/v1",
        "api_type": "openai",
        "api_model": "baichuan2" 
    }
}
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 字段说明             |
| :--- | :------- | :------- | :------------------- |
| 1    | res      | boolean  | 模型修改后保存的状态 |

响应示例：

```json
{
    "res": True
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
    "ErrorCode": "ModelFactory.Mydb.DataBase.ParameterError",
    "Description": "数据库连接失败",
    "Solution": "请核对数据库的连接参数.",
    "ErrorDetails": "数据库登录信息错误",
    "ErrorLink": ""
}
```
### 1.8、URL调用接口

```
POST  /api/model-factory/v1/llm/used/{llm_id}
```

请求参数：

| 序号 | 字段名称          | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明                       |
| :--- | :---------------- | :------- | -------- | :------- | ---- | :----------------------------- |
| 1    | llm_id            | string   | path     | 是       | 50   | 当前模型的唯一标识符，路径参数 |
| 2    | ai_system         | string   | body     | 否       |      |                                |
| 3    | ai_user           | string   | body     | 否       |      |                                |
| 4    | ai_assistant      | string   | body     | 否       |      |                                |
| 5    | ai_history        | list     | body     | 否       |      |                                |
| 6    | top_p             | float    | body     | 否       |      |                                |
| 7    | temperature       | float    | body     | 否       |      |                                |
| 8    | max_token         | int      | body     | 否       |      |                                |
| 9    | frequency_penalty | float    | body     | 否       |      |                                |
| 10   | presence_penalty  | float    | body     | 否       |      |                                |

请求示例：

```json
{
  "ai_system": "大模型输入中的system",
  "ai_user": "大模型输入中的user",
  "ai_assistant": "大模型输入中的assistant",
  "ai_history": [
    {
      "role": "ai",
      "message": "历史信息中assistant内容"
    },
    {
      "role": "human",
      "message": "历史信息中user内容"
    }
  ],
  "top_p": "float",
  "temperature": "float",
  "max_token": "integer",
  "frequency_penalty": "float",
  "presence_penalty": "float"
}
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 字段说明                 |
| :--- | :------- | :------- | :----------------------- |
| 1    | res      | object   | 大模型被调用后的返回结果 |

响应示例：

```json
{
  "res": {
    "time": "这里是花费时间",
    "token_len": "这里是token长度",
    "data": "这是大模型回复的结果"
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
    "ErrorCode": "ModelFactory.Mydb.DataBase.ParameterError",
    "Description": "数据库连接失败",
    "Solution": "请核对数据库的连接参数.",
    "ErrorDetails": "数据库登录信息错误",
    "ErrorLink": ""
}
```
## 2、提示词工程管理
### 2.1、获取提示词项目列表

```
GET  /api/model-factory/v1/prompt/item/list
```

请求参数：

| 序号 | 字段名称         | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明                                   |
| :--- | :--------------- | :------- | -------- | :------- | ---- | :----------------------------------------- |
| 1    | prompt_item_name | string   | query    | 否       | 50   | 对提示词进行模糊搜索，不填此参数则返回所有 |

请求示例：

```
prompt_item_name=AnyShare
```

响应参数：

| 序号 | 字段名称    | 字段类型 | 字段说明           |
| :--- | ----------- | :------- | :----------------- |
| 1    | total       | int      | 总个数             |
| 2    | searchTotal | int      | 满足搜索条件的个数 |
| 3    | data        | list     | 返回的数据         |

| 序号 | 字段名称          | 字段类型  | 字段说明                  |
| :--- | ----------------- | :-------- | :------------------------ |
| 1    | prompt_item_id    | string    | 提示词项目id              |
| 2    | prompt_item_name  | string    | 提示词项目名称            |
| 3    | prompt_item_types | list      | 提示词项目的分类          |
| 4    | create_time       | timestamp | 创建时间                  |
| 5    | create_by         | string    | 创建人                    |
| 6    | update_time       | timestamp | 更新时间                  |
| 7    | update_by         | string    | 最终操作人                |
| 8    | is_built_in       | boolean   | true为内置，false为自定义 |

响应示例：

```json
{
    "res": {
        "total": 10,
        "searchTotal": 2,
        "data": [
            {
                "prompt_item_id": "1723544272822734848",
                "prompt_item_name": "这是一个名称",
                "prompt_item_types": [{"id":"1723544272822734846","name":"未分类"},{"id":"1723599586070761472","name":"分类1"}],
                "create_time": "2023-11-10 17：01：02",
                "create_by": "zhang",
                "update_time": "2023-11-10 17：01：02",
                "update_by": "li",
                "is_built_in": True
            },
            {
                "prompt_item_id": "1723580620199825408",
                "prompt_item_name": "这是一个名称",
                "prompt_item_types": [{"id":"1723580620199825408","name":"未分类"},{"id":"1724352803725512704","name":"分类1"}],
                "create_time": "2023-11-10 17：01：02",
                "create_by": "zhang",
                "update_time": "2023-11-10 17：01：02",
                "update_by": "li",
                "is_built_in": True
            },
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
    "ErrorCode": "ModelFactory.Mydb.DataBase.ParameterError",
    "Description": "数据库连接失败",
    "Solution": "请核对数据库的连接参数.",
    "ErrorDetails": "数据库登录信息错误",
    "ErrorLink": ""
}
```

### 2.2、新建提示词项目

```
POST  /api/model-factory/v1/prompt/item/add
```

请求参数：

| 序号 | 字段名称         | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明       |
| :--- | :--------------- | :------- | -------- | :------- | ---- | :------------- |
| 1    | prompt_item_name | string   | body     | 是       | 50   | 提示词项目名称 |

请求示例：

```json
{    
    "prompt_item_name": "这是一个名称"
}
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 字段说明     |
| :--- | :------- | :------- | :----------- |
| 1    | res      | string   | 提示词项目id |

响应示例：

```json
{    
     "res": "1729316851575558145"
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
    "ErrorCode": "ModelFactory.PromptController.PromptItemAdd.ParameterError",
    "Description": "参数校验异常",
    "Solution": "请核对输入信息.",
    "ErrorDetails": "输入参数不能为空",
    "ErrorLink": ""
}
```

### 2.3、编辑提示词项目

```
POST  /api/model-factory/v1/prompt/item/edit
```

请求参数：

| 序号 | 字段名称         | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明       |
| :--- | :--------------- | :------- | -------- | :------- | ---- | :------------- |
| 1    | prompt_item_id   | string   | body     | 是       | 50   | 提示词项目id   |
| 2    | prompt_item_name | string   | body     | 是       | 50   | 提示词项目名称 |

请求示例：

```json
{    
    "prompt_item_id": "1234567890123456789",
   "prompt_item_name": "修改后的项目名称"
}
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 字段说明           |
| :--- | :------- | :------- | :----------------- |
| 1    | res      | boolean  | 提示词项目编辑结果 |

响应示例：

```json
{
    "res": True
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
    "ErrorCode": "ModelFactory.PromptController.PromptItemEdit.ParameterError",
    "Description": "参数校验异常",
    "Solution": "请核对输入信息.",
    "ErrorDetails": "输入参数不能为空",
    "ErrorLink": ""
}
```

### 2.4、新建提示词分组

```
POST  /api/model-factory/v1/prompt/type/add
```

请求参数：

| 序号 | 字段名称         | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明           |
| :--- | :--------------- | :------- | -------- | :------- | ---- | :----------------- |
| 1    | prompt_item_id   | string   | body     | 是       | 50   | 提示词项目id       |
| 2    | prompt_item_type | string   | body     | 是       | 50   | 提示词项目分组名称 |

请求示例：

```json
{    
    "prompt_item_id": "1234567890123456789",
   "prompt_item_type": "这是项目下面的分组"
}
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 字段说明     |
| :--- | :------- | :------- | :----------- |
| 1    | res      | string   | 提示词分组id |

响应示例：

```json
{    
     "res": "1729318067554619392"
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
    "ErrorCode": "ModelFactory.PromptController.PromptTypeAdd.ParameterError",
    "Description": "参数校验异常",
    "Solution": "请核对输入信息.",
    "ErrorDetails": "输入参数不能为空",
    "ErrorLink": ""
}
```

### 2.5、编辑提示词分组

```
POST  /api/model-factory/v1/prompt/type/edit
```

请求参数：

| 序号 | 字段名称            | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明           |
| :--- | :------------------ | :------- | -------- | :------- | ---- | :----------------- |
| 1    | prompt_item_type    | string   | body     | 是       | 50   | 提示词项目分组名称 |
| 2    | prompt_item_type_id | string   | body     | 是       | 50   | 提示词项目分组id   |

请求示例：

```json
{    
    "prompt_item_type_id":"4563468769898",
   "prompt_item_type": "这是一个修改后的分组名称"
}
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 字段说明           |
| :--- | :------- | :------- | :----------------- |
| 1    | res      | boolean  | 提示词分类保存结果 |

响应示例：

```json
{
    "res": True
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
    "ErrorCode": "ModelFactory.PromptController.PromptTypeEdit.ParameterError",
    "Description": "参数校验异常",
    "Solution": "请核对输入信息.",
    "ErrorDetails": "输入参数不能为空",
    "ErrorLink": ""
}
```

### 2.6、获取提示词列表

```
GET  /api/model-factory/v1/prompt/page
```

请求参数：

| 序号 | 字段名称            | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明                                                     |
| :--- | :------------------ | :------- | -------- | :------- | ---- | :----------------------------------------------------------- |
| 1    | prompt_item_id      | string   | query    | 否       | 50   | 提示词项目id                                                 |
| 2    | prompt_item_type_id | string   | query    | 否       | 50   | 提示词项目分类id                                             |
| 3    | page                | int      | query    | 是       |      | 页码                                                         |
| 4    | size                | int      | query    | 是       |      | 每页数量                                                     |
| 5    | order               | string   | query    | 否       | 4    | 默认按从新至旧排序，接受参数为：'desc'（从新到旧），'asc'（从旧到新） |
| 6    | prompt_name         | string   | query    | 否       | 50   | 对提示词进行模糊搜索，不填此参数则返回所有                   |
| 7    | rule                | string   | query    | 否       | 11   | 默认按照更新时间排序，接受参数为：'update_time'（按提示词更新时间排序），'create_time'（按提示词创建时间排序）,'prompt_name'（按提示词名称排序） |
| 8    | deploy              | string   | query    | 否       | 4    | 对提示词发布状态进行筛选，接受参数为：‘all’（默认所有），‘yes'（已发布），‘no‘（未发布），当前版本不存在未发布 |
| 9    | prompt_type         | string   | query    | 否       | 10   | 对提示词类型进行筛选，接受参数为：‘all’（默认所有），’chat'（对话型），'completion'（文本生成型） |

请求示例：

```
prompt_item_id=1234567890123456789&prompt_item_type_id=2134567890123456742&page=5&size=10&order=desc&prompt_name=阅读理解&rule=update_time&deploy=all&prompt_type=all
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 字段说明       |
| :--- | -------- | :------- | :------------- |
| 1    | total    | int      | 回复信息的个数 |
| 2    | data     | list     | 回复的信息     |

| 序号 | 字段名称            | 字段类型  | 字段说明                            |
| :--- | :------------------ | :-------- | :---------------------------------- |
| 1    | prompt_item_id      | string    | 提示词项目id                        |
| 2    | prompt_item_name    | string    | 提示词项目名称                      |
| 3    | prompt_item_type_id | string    | 提示词项目分类id                    |
| 4    | prompt_item_type    | string    | 提示词项目分类                      |
| 5    | prompt_id           | string    | 提示词id                            |
| 6    | prompt_service_id   | string    | 提示词服务id，供外部调用            |
| 7    | prompt_name         | string    | 提示词名称                          |
| 8    | prompt_type         | string    | 提示词类型                          |
| 9    | model_name          | string    | 选择的模型名称                      |
| 10   | prompt_desc         | string    | 提示词的描述                        |
| 11   | prompt_deploy       | string    | 发布状态                            |
| 12   | create_time         | timestamp | 创建时间                            |
| 13   | create_by           | string    | 创建人                              |
| 14   | update_time         | timestamp | 最终操作时间                        |
| 15   | update_by           | string    | 操作人                              |
| 16   | icon                | string    | 颜色配置                            |
| 17   | model_id            | string    | 模型id                              |
| 18   | model_series        | string    | 模型系列                            |
| 19   | is_built_in         | boolean   | 是否内置，true为内置，false为自定义 |
| 20   | messages            | string    | 提示词内容                          |
| 21   | variables           | list      | 提示词变量列表                      |
| 22   | model_para          | object    | 提示词对应模型变量                  |

响应示例：

```json
{
    "res": {
        "total": 2,
        "data": [
            {
                "prompt_item_id": "1234567890123456789",
                "prompt_item_name": "zxy",
                "prompt_item_type_id": "4563468769898",
                "prompt_item_type": "2",
                "prompt_id": "1730158255189135360",
                "prompt_service_id": "ad-mf-01",
                "prompt_name": "这是一个名称",
                "prompt_type": "对话型",
                "model_name": "gpt-35-turbo-16k",
                "model_id": "5823-58-4594-34543",
                "icon": "1",
                "model_series": "openai",
                "prompt_desc": "这是一个描述",
                "prompt_deploy": "已发布",
                "create_time": "1682870400",
                "create_by": "zhang",
                "update_time": "1682870400",
                "update_by": "li"
            },
            {
                "prompt_item_id": "1234567890123456789",
                "prompt_item_name": "zxy",
                "prompt_item_type_id": "4563468769898",
                "prompt_item_type": "2",
                "prompt_id": "1730158255189135360",
                "prompt_service_id": "ad-mf-01",
                "prompt_name": "这是一个名称",
                "prompt_type": "对话型",
                "model_name": "gpt-35-turbo-16k",
                "model_id": "5823-58-4594-34543",
                "icon": "1",
                "model_series": "openai",
                "prompt_desc": "这是一个描述",
                "prompt_deploy": "已发布",
                "create_time": "1682870400",
                "create_by": "zhang",
                "update_time": "1682870400",
                "update_by": "li"
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
    "ErrorCode": "ModelFactory.Mydb.DataBase.ParameterError",
    "Description": "数据库连接失败",
    "Solution": "请核对数据库的连接参数.",
    "ErrorDetails": "数据库登录信息错误",
    "ErrorLink": ""
}
```

### 2.7、新增提示词-数据保存

```
POST  /api/model-factory/v1/prompt/add
```

请求参数：

| 序号 | 字段名称            | 字段类型     | 参数位置 | 是否必须 | 长度 | 字段说明                    |
| :--- | :------------------ | :----------- | -------- | :------- | ---- | :-------------------------- |
| 1    | prompt_item_id      | string       | body     | 是       | 50   | 提示词项目id                |
| 2    | prompt_item_type_id | string       | body     | 是       | 50   | 提示词项目分类id            |
| 3    | prompt_service_id   | string       | body     | 是       | 50   | 提示词业务id                |
| 4    | prompt_name         | string       | body     | 是       | 50   | 提示词名称                  |
| 5    | prompt_desc         | string       | body     | 否       | 255  | 提示词描述                  |
| 6    | prompt_type         | string       | body     | 是       | 50   | 提示词类型                  |
| 7    | model_id            | string       | body     | 否       | 50   | 选择的模型名称id            |
| 8    | icon                | string       | body     | 是       | 50   | 颜色配置，暂定颜色按0-9排序 |
| 9    | model_para          | object       | body     | 否       |      | 模型参数                    |
| 10   | messages            | string       | body     | 是       | 5000 | 提示词文本                  |
| 11   | variables           | list<object> | body     | 否       |      | 提示词变量                  |
| 12   | opening_remarks     | string       | body     | 否       | 150  | 对话开场白                  |

请求示例：

```json
{
    "prompt_item_id": "1724651974907006976",
    "prompt_item_type_id": "1724651974948950016",
    "prompt_service_id": "ad-mf-01",
    "prompt_name": "这w",
    "prompt_desc": "这是一个描述",
    "model_id": "1724630864333246464",
    "prompt_type": "chat",
    "icon": "1",
    "model_para": {
        "temperature": 1,
        "top_p": 1,
        "presence_penalty": 0,
        "frequency_penalty": 0,
        "max_tokens": 16
    },
    "messages": "你是谁{{var1}}{{var2}}",
    "variables": [
        {
            "var_name": "var1",
            "optional": false,
            "field_type": "text",
            "max_len": 48
        },
        {
            "var_name": "var2",
            "field_name": "xxx",
            "optional": "True",
            "field_type": "textarea"
        }
    ],
    "opening_remarks": ""
}
```

响应参数：

| 序号 | 字段名称  | 字段类型 | 字段说明 |
| :--- | :-------- | :------- | :------- |
| 1    | prompt_id | string   | 提示词id |

响应示例：

```json
{
    "res": {
        "prompt_id":"58340898798050654"
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
    "ErrorCode": "ModelFactory.PromptController.PromptAdd.ParameterError",
    "Description": "参数校验异常",
    "Solution": "请核对输入信息.",
    "ErrorDetails": "输入参数不能为空",
    "ErrorLink": ""
}
```

### 2.8、获取大模型列表

```
GET  /api/model-factory/v1/prompt/llm/list
```

请求参数：

| 序号 | 字段名称 | 字段类型 | 字段位置 | 是否必须 | 长度 | 字段说明 |
| :--- | :------- | :------- | -------- | :------- | ---- | :------- |
| 1    | types    | string   | query    | 是       | 50   | 模型类型 |

请求示例：

```
types=chat
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 字段说明       |
| :--- | -------- | :------- | :------------- |
| 1    | total    | int      | 回复信息的个数 |
| 2    | data     | list     | 回复的信息     |

| 序号 | 字段名称     | 字段类型 | 字段说明     |
| :--- | :----------- | :------- | :----------- |
| 1    | model_id     | string   | 模型id       |
| 2    | model_series | string   | 模型的供应商 |
| 3    | model_type   | string   | 模型类型     |
| 4    | model_name   | string   | 模型的名称   |
| 5    | model        | string   | 模型本身名称 |
| 6    | model_config | object   | 模型配置     |
| 7    | model_para   | object   | 模型参数     |

响应示例：

```json
{
    "res": {
        "total": 3,
        "data": [
            {
                "model": "gpt-35-turbo-16k",
                "model_id": "1730157481000308736",
                "model_type": "chat",
                "model_name": "gpt-35-turbo-16k",
                "model_series": "openai",
                "model_config": {
                    "api_key": "16ff5cd7654c4ae9a9dd36059198a15d",
                    "api_model": "gpt-35-turbo-16k"
                },
                "model_para": {
                    "top_p": [
                        0,
                        1,
                        1
                    ],
                    "max_tokens": [
                        10,
                        16384,
                        10000
                    ],
                    "temperature": [
                        0,
                        2,
                        1
                    ],
                    "presence_penalty": [
                        -2,
                        2,
                        0
                    ],
                    "frequency_penalty": [
                        -2,
                        2,
                        0
                    ]
                }
            },
            {
                "model": "text-davinci-002",
                "model_id": "1730157481021280256",
                "model_type": "completion",
                "model_name": "text-davinci-002",
                "model_series": "openai",
                "model_config": {
                    "api_key": "16ff5cd7654c4ae9a9dd36059198a15d",
                    "api_model": "text-davinci-002"
                },
                "model_para": {
                    "top_p": [
                        0,
                        1,
                        1
                    ],
                    "max_tokens": [
                        10,
                        4097,
                        1000
                    ],
                    "temperature": [
                        0,
                        2,
                        1
                    ],
                    "presence_penalty": [
                        -2,
                        2,
                        0
                    ],
                    "frequency_penalty": [
                        -2,
                        2,
                        0
                    ]
                }
            },
            {
                "model": "baichuan2",
                "model_id": "1730426029798985728",
                "model_type": "chat",
                "model_name": "0-baichuan2",
                "model_series": "aishu-baichuan",
                "model_config": {
                    "api_model": "baichuan2",
                    "api_base": "http://10.4.24.55:8301/v1",
                    "api_type": "openai"
                },
                "model_para": {
                    "top_p": [
                        0,
                        1,
                        1
                    ],
                    "max_tokens": [
                        10,
                        4096,
                        1000
                    ],
                    "temperature": [
                        0,
                        2,
                        1
                    ],
                    "presence_penalty": [
                        -2,
                        2,
                        0
                    ],
                    "frequency_penalty": [
                        -2,
                        2,
                        0
                    ]
                }
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
    "ErrorCode": "ModelFactory.Mydb.DataBase.ParameterError",
    "Description": "数据库连接失败",
    "Solution": "请核对数据库的连接参数.",
    "ErrorDetails": "数据库登录信息错误",
    "ErrorLink": ""
}
```

### 2.9、编辑提示词名称

```
POST  /api/factory/v1/prompt/edit_name
```

请求参数：

| 序号 | 字段名称            | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明                   |
| :--- | :------------------ | :------- | -------- | :------- | ---- | :------------------------- |
| 1    | prompt_id           | string   | body     | 是       | 50   | 提示词id                   |
| 2    | prompt_name         | string   | body     | 是       | 50   | 提示词名称                 |
| 3    | model_id            | string   | body     | 否       | 50   | 选择的模型id               |
| 4    | icon                | string   | body     | 是       | 50   | 颜色配置                   |
| 5    | prompt_desc         | string   | body     | 否       | 255  | 提示词描述                 |
| 6    | prompt_item_type_id | string   | body     | 是       | 50   | 提示词分组id，用于修改分组 |
| 7    | prompt_item_id      | string   | body     | 是       | 50   | 提示词项目id，用于修改项目 |

请求示例：

```json
{
    "prompt_item_id": "1730157652002082817",
    "prompt_item_type_id": "1730157652002082818",
    "prompt_name": "一个名字",
    "model_id": "1730157481000308736",
    "icon": "5",
    "prompt_desc": "",
    "prompt_id": "1730486697692631040"
}
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 字段说明                   |
| :--- | :------- | :------- | :------------------------- |
| 1    | res      | boolean  | 提示词名称修改后保存的状态 |

响应示例：

```json
{
    "res": True
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
    "ErrorCode": "ModelFactory.Mydb.DataBase.ParameterError",
    "Description": "数据库连接失败",
    "Solution": "请核对数据库的连接参数.",
    "ErrorDetails": "数据库登录信息错误",
    "ErrorLink": ""
}
```

### 2.10、获取提示词模板列表

```
GET  /api/model-factory/v1/prompt/template/list
```

请求参数：

| 序号 | 字段名称    | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明                                       |
| :--- | :---------- | :------- | -------- | :------- | ---- | :--------------------------------------------- |
| 1    | prompt_name | string   | query    | 否       | 50   | 对提示词模板进行模糊搜索，不填此参数则返回所有 |
| 2    | prompt_type | string   | query    | 是       | 50   | 提示词类型                                     |

请求示例：

```json
prompt_name=阅读理解&prompt_type=chat
```

响应参数：

| 序号 | 字段名称 | 字段类型     | 字段说明       |
| :--- | -------- | :----------- | :------------- |
| 1    | total    | int          | 回复信息的个数 |
| 2    | data     | list<object> | 回复的信息     |

| 序号 | 字段名称        | 字段类型     | 字段说明     |
| :--- | :-------------- | :----------- | :----------- |
| 1    | prompt_id       | string       | 提示词id     |
| 2    | prompt_name     | string       | 提示词名称   |
| 3    | prompt_type     | string       | 提示词类型   |
| 4    | prompt_desc     | string       | 提示词的描述 |
| 5    | messages        | string       | 提示词文本   |
| 6    | variables       | list<object> | 提示词变量   |
| 7    | input           | string       | 变量样例     |
| 8    | opening_remarks | string       | 对话开场白   |
| 9    | icon            | string       | 颜色配置     |

响应示例：

```json
{
    "res": {
        "total": 5,
        "data": [
            {
                "icon": "",
                "prompt_id": "1730157481377796096",
                "messages": "我想让你担任{{role}}面试官。我将成为候选人，您将向我询问面试问题。我希望你只作为面试官回答。不要一次写出所有的问题。我希望你只对我进行采访。问我问题，等待我的回答。不要写解释。像面试官一样一个一个问我，等我回答。\n",
                "prompt_name": "担任面试官",
                "prompt_type": "chat",
                "prompt_desc": "进行面试",
                "opening_remarks": "",
                "input": "{'request': 'Android开发工程师'}",
                "variables": [
                    {
                        "var_name": "role",
                        "field_name": "role",
                        "optional": false,
                        "field_type": "textarea"
                    }
                ]
            },
            {
                "icon": "",
                "prompt_id": "1730157481394573312",
                "messages": "我希望您能够充当代码解释器，澄清代码的语法和语义。代码是\n",
                "prompt_name": "代码解释器",
                "prompt_type": "chat",
                "prompt_desc": "阐明代码的语法和语义",
                "opening_remarks": "",
                "input": "{}",
                "variables": []
            },
            {
                "icon": "",
                "prompt_id": "1730157481407156224",
                "messages": "你可以重新组织和输出混乱复杂的会议记录，并根据当前状态、遇到的问题和提出的解决方案撰写会议纪要。你只负责会议记录方面的问题，不回答其他。\n",
                "prompt_name": "会议纪要",
                "prompt_type": "chat",
                "prompt_desc": "帮你重新组织和输出混乱复杂的会议纪要",
                "opening_remarks": "",
                "input": "{}",
                "variables": []
            },
            {
                "icon": "",
                "prompt_id": "1730157481423933440",
                "messages": "我希望你扮演一个新闻内容撰写的记者角色，根据用户提供的关键信息，如新闻主题、摘要、背景信息、内容框架或其他要求，输出新闻稿件内容。你仅提供新闻内容稿件撰写的请求服务。\n",
                "prompt_name": "新闻内容撰写",
                "prompt_type": "chat",
                "prompt_desc": "生成新闻稿件",
                "opening_remarks": "",
                "input": "{}",
                "variables": []
            },
            {
                "icon": "",
                "prompt_id": "1730157481440710656",
                "messages": "我需要为一个关于{{topic}}的项目写一份项目计划。请帮助我根据以下内容起草本项目书：项目背景、目标、预期成果、实施步骤、时间表、预算和风险评估。\n",
                "prompt_name": "项目计划书撰写",
                "prompt_type": "chat",
                "prompt_desc": "撰写项目计划",
                "opening_remarks": "",
                "input": "{'topic': '保护环境'}",
                "variables": [
                    {
                        "var_name": "topic",
                        "field_name": "topic",
                        "optional": false,
                        "field_type": "textarea"
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
    "ErrorCode": "ModelFactory.Mydb.DataBase.ParameterError",
    "Description": "数据库连接失败",
    "Solution": "请核对数据库的连接参数.",
    "ErrorDetails": "数据库登录信息错误",
    "ErrorLink": ""
}
```

### 2.11、查看提示词

```
GET  /api/model-factory/v1/prompt/{prompt_id}
```

请求参数：

| 序号 | 字段名称  | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明 |
| :--- | :-------- | :------- | -------- | :------- | ---- | :------- |
| 1    | prompt_id | string   | path     | 是       | 50   | 提示词id |

请求示例：

```
1730486697692631040
```

响应参数：

| 序号 | 字段名称            | 字段类型 | 字段说明         |
| :--- | :------------------ | :------- | :--------------- |
| 1    | prompt_name         | string   | 提示词名称       |
| 2    | model_name          | string   | 模型名称         |
| 3    | model_id            | string   | 模型id           |
| 4    | model_para          | object   | 模型参数         |
| 5    | messages            | string   | 提示词文本       |
| 6    | variables           | string   | 提示词变量       |
| 7    | opening_remarks     | string   | 对话开场白       |
| 8    | prompt_item_id      | string   | 提示词项目id     |
| 9    | prompt_item_name    | string   | 提示词项目名称   |
| 10   | prompt_item_type_id | string   | 提示词项目分类id |
| 11   | prompt_item_type    | string   | 提示词项目分类   |
| 12   | prompt_service_id   | string   | 提示词业务id     |
| 13   | prompt_id           | string   | 提示词id         |
| 14   | prompt_type         | string   | 提示词类型       |
| 15   | prompt_desc         | string   | 提示词的描述     |
| 19   | prompt_deploy       | string   | 发布状态         |
| 17   | icon                | string   | 颜色配置         |
| 18   | model_series        | string   | 模型系列         |

响应示例：

```json
{
    "res": {
        "prompt_id": "1730486697692631040",
        "prompt_name": "一个名字",
        "model_id": "1730157481000308736",
        "model_name": "gpt-35-turbo-16k",
        "prompt_item_id": "1730157652002082817",
        "prompt_service_id": "1730486653476278272",
        "prompt_item_name": "zkn0",
        "prompt_item_type_id": "1730157652002082818",
        "prompt_item_type": "默认分组",
        "messages": "我想让你担任{{role}}面试官。我将成为候选人，您将向我询问面试问题。我希望你只作为面试官回答。不要一次写出所有的问题。我希望你只对我进行采访。问我问题，等待我的回答。不要写解释。像面试官一样一个一个问我，等我回答。\n",
        "opening_remarks": "",
        "variables": [
            {
                "var_name": "role",
                "field_name": "role",
                "optional": false,
                "field_type": "textarea"
            }
        ],
        "prompt_type": "chat",
        "prompt_desc": "",
        "prompt_deploy": true,
        "model_series": "openai",
        "icon": "5",
        "model_para": {
            "top_p": 1,
            "max_tokens": 10000,
            "temperature": 1,
            "presence_penalty": 0,
            "frequency_penalty": 0
        }
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
    "ErrorCode": "ModelFactory.Mydb.DataBase.ParameterError",
    "Description": "数据库连接失败",
    "Solution": "请核对数据库的连接参数.",
    "ErrorDetails": "数据库登录信息错误",
    "ErrorLink": ""
}
```

### 2.12、编辑提示词

```
POST  /api/factory/v1/prompt/edit
```

请求参数：

| 序号 | 字段名称        | 字段类型     | 参数位置 | 是否必须 | 长度 | 字段说明   |
| :--- | :-------------- | :----------- | -------- | :------- | ---- | :--------- |
| 1    | prompt_id       | string       | body     | 是       | 50   | 提示词id   |
| 2    | model_para      | object       | body     | 否       |      | 模型参数   |
| 3    | messages        | string       | body     | 是       | 5000 | 提示词文本 |
| 4    | variables       | list<object> | body     | 否       |      | 提示词变量 |
| 5    | opening_remarks | string       | body     | 否       | 150  | 对话开场白 |
| 6    | model_id        | string       | body     | 否       | 50   | 模型id     |

请求示例：

```json
{
    "prompt_id": "1730486697692631040",
    "model_id": "1730157481000308736",
    "model_para": {
        "top_p": 1,
        "max_tokens": 10000,
        "temperature": 1,
        "presence_penalty": 0,
        "frequency_penalty": 0
    },
    "messages": "我想让你担任{{role}}面试官。我将成为候选人，您将向我询问面试问题。我希望你只作为面试官回答。不要一次写出所有的问题。我希望你只对我进行采访。问我问题，等待我的回答。不要写解释。像面试官一样一个一个问我，等我回答。\n",
    "variables": [
        {
            "var_name": "role",
            "field_name": "role",
            "optional": false,
            "field_type": "textarea"
        }
    ],
    "opening_remarks": ""
}
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 字段说明               |
| :--- | :------- | :------- | :--------------------- |
| 1    | res      | boolean  | 提示词修改后保存的状态 |

响应示例：

```json
{
    "res": True
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
    "ErrorCode": "ModelFactory.Mydb.DataBase.ParameterError",
    "Description": "数据库连接失败",
    "Solution": "请核对数据库的连接参数.",
    "ErrorDetails": "数据库登录信息错误",
    "ErrorLink": ""
}
```

### 2.13、发布提示词

```
POST  /api/model-factory/v1/prompt/deploy
```

请求参数：

| 序号 | 字段名称  | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明 |
| :--- | :-------- | :------- | -------- | :------- | ---- | :------- |
| 1    | prompt_id | string   | body     | 是       | 50   | 提示词id |

请求示例：

```json
{
   "prompt_id": "1723933405655207936"
}
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 字段说明 |
| :--- | :------- | :------- | :------- |
| 1    | res      | boolean  | 发布结果 |

响应示例：

```json
{
    "res": True
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
    "ErrorCode": "ModelFactory.Mydb.DataBase.ParameterError",
    "Description": "数据库连接失败",
    "Solution": "请核对数据库的连接参数.",
    "ErrorDetails": "数据库登录信息错误",
    "ErrorLink": ""
}
```

### 2.14、取消发布提示词

```
POST  /api/model-factory/v1/prompt/undeploy
```

请求参数：

| 序号 | 字段名称  | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明 |
| :--- | :-------- | :------- | -------- | :------- | ---- | :------- |
| 1    | prompt_id | string   | body     | 是       | 50   | 提示词id |

请求示例：

```json
{
   "prompt_id": "1723933405655207936"
}
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 字段说明 |
| :--- | :------- | :------- | :------- |
| 1    | res      | boolean  | 发布结果 |

响应示例：

```json
{
    "res": True
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
    "ErrorCode": "ModelFactory.Mydb.DataBase.ParameterError",
    "Description": "数据库连接失败",
    "Solution": "请核对数据库的连接参数.",
    "ErrorDetails": "数据库登录信息错误",
    "ErrorLink": ""
}
```

### 2.15、运行提示词

```
POST  /api/model-factory/v1/prompt/run
```

请求参数：

| 序号 | 字段名称    | 字段类型     | 参数位置 | 是否必须 | 长度 | 字段说明               |
| :--- | :---------- | :----------- | -------- | :------- | ---- | :--------------------- |
| 1    | model_id    | string       | body     | 是       | 50   | 选择的模型id           |
| 2    | model_para  | object       | body     | 是       |      | 模型参数               |
| 3    | messages    | string       | body     | 是       | 5000 | 提示词文本             |
| 4    | variables   | list<object> | body     | 否       |      | 变量                   |
| 5    | inputs      | object       | body     | 否       |      | 输入的变量值           |
| 6    | history_dia | list<object> | body     | 否       |      | 对话型提示词的聊天记录 |

请求示例：

```json
{
    "model_id": "1724639729225437184",
    "model_para": {
        "temperature": 1,
        "top_p": 1,
        "presence_penalty": 0,
        "frequency_penalty": 0,
        "max_tokens": 200
    },
    "messages": "请将以下内容翻译成{{language}}：{{text}}",
    "variables": [
        {
            "var_name": "language",
            "field_name": "language",
            "optional": false,
            "field_type": "text",
            "max_len": 48
        },
        {
            "var_name": "text",
            "field_name": "text",
            "optional": true,
            "field_type": "textarea"
        }
    ],
    "inputs": {
        "language": "英文",
        "text": "西瓜"
    },
    "history_dia": [
        {
            "role": "human",
            "message": "你好"
        },
        {
            "role": "ai",
            "message": "你好,您有什么问题?"
        }
    ]
}
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 字段说明               |
| :--- | :------- | :------- | :--------------------- |
| 1    | res      | object   | 提示词运行后的返回结果 |

响应示例：

```json
{
  "res": {
    "time": "这里是花费时间",
    "token_len": "这里是token长度",
    "data": "这是大模型回复的结果"
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
    "ErrorCode": "ModelFactory.Mydb.DataBase.ParameterError",
    "Description": "数据库连接失败",
    "Solution": "请核对数据库的连接参数.",
    "ErrorDetails": "数据库登录信息错误",
    "ErrorLink": ""
}
```

### 2.16、运行提示词-流式返回

```
POST  /api/model-factory/v1/prompt/run_stream
```

请求参数：

| 序号 | 字段名称    | 字段类型     | 参数位置 | 是否必须 | 长度 | 字段说明               |
| :--- | :---------- | :----------- | -------- | :------- | ---- | :--------------------- |
| 1    | model_id    | string       | body     | 是       | 50   | 选择的模型id           |
| 2    | model_para  | object       | body     | 是       |      | 模型参数               |
| 3    | messages    | string       | body     | 是       | 5000 | 提示词文本             |
| 4    | variables   | list<object> | body     | 否       |      | 变量                   |
| 5    | inputs      | object       | body     | 否       |      | 输入的变量值           |
| 6    | history_dia | list<object> | body     | 否       |      | 对话型提示词的聊天记录 |

请求示例：

```json
{
    "model_id": "1724639729225437184",
    "model_para": {
        "temperature": 1,
        "top_p": 1,
        "presence_penalty": 0,
        "frequency_penalty": 0,
        "max_tokens": 200
    },
    "messages": "请将以下内容翻译成{{language}}：{{text}}",
    "variables": [
        {
            "var_name": "language",
            "field_name": "language",
            "optional": false,
            "field_type": "text",
            "max_len": 48
        },
        {
            "var_name": "text",
            "field_name": "text",
            "optional": true,
            "field_type": "textarea"
        }
    ],
    "inputs": {
        "language": "英文",
        "text": "西瓜"
    },
    "history_dia": [
        {
            "role": "human",
            "message": "你好"
        },
        {
            "role": "ai",
            "message": "你好,您有什么问题?"
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
    "ErrorCode": "ModelFactory.Mydb.DataBase.ParameterError",
    "Description": "数据库连接失败",
    "Solution": "请核对数据库的连接参数.",
    "ErrorDetails": "数据库登录信息错误",
    "ErrorLink": ""
}
```

### 2.17、调用提示词

```
POST  /api/model-factory/v1/prompt/{service_id}/used
```

请求参数：

| 序号 | 字段名称    | 字段类型     | 参数位置 | 是否必须 | 长度 | 字段说明               |
| :--- | :---------- | :----------- | -------- | :------- | ---- | :--------------------- |
| 1    | service_id  | string       | path     | 是       | 50   | 提示词id               |
| 2    | inputs      | object       | body     | 否       |      | 输入的变量             |
| 3    | history_dia | list<object> | body     | 否       |      | 对话型提示词的聊天记录 |

请求示例：

```json

{
    "inputs": {
        "var1": "变量值1",
        "var2": "变量值2",
        "var3": "变量值3",
        "var4": "变量值4"
    },
    "history_dia": [
        {
            "role": "human",
            "message": "你好"
        },
        {
            "role": "ai",
            "message": "你好,您有什么问题?"
        }
    ]
}
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 字段说明               |
| :--- | :------- | :------- | :--------------------- |
| 1    | res      | object   | 提示词调用后的返回结果 |

响应示例：

```json
{
  "res": {
    "time": "这里是花费时间",
    "token_len": "这里是token长度",
    "data": "这是大模型回复的结果"
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
    "ErrorCode": "ModelFactory.Mydb.DataBase.ParameterError",
    "Description": "数据库连接失败",
    "Solution": "请核对数据库的连接参数.",
    "ErrorDetails": "数据库登录信息错误",
    "ErrorLink": ""
}
```

### 2.18、查看代码

```
GET /api/model-factory/v1/prompt/code
```

请求参数：

| 序号 | 字段名称  | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明 |
| :--- | :-------- | :------- | -------- | :------- | ---- | :------- |
| 1    | model_id  | string   | query    | 是       | 50   | 大模型id |
| 2    | prompt_id | string   | query    | 否       | 50   | 提示词id |

请求示例：

```
model_id=1723933405655207936&prompt_id=353467867978094
```

响应参数：

| 序号 | 字段名称          | 字段类型 | 字段说明      |
| :--- | :---------------- | :------- | :------------ |
| 1    | model_series      | string   | 模型系列      |
| 2    | model_type        | string   | 模型类型      |
| 3    | model_config      | object   | 模型配置      |
| 4    | prompt_deploy_url | string   | 提示词部署url |

响应示例：

```json
{
    "res": {               
         "model_series": "aishu-baichuan",
         "model_type": "chat",
         "model_config": {
                 "api_base": "http://10.4.29.18:8301/v1",
                 "api_type": "openai",
                 "api_model": "baichuan2"
           },
         "prompt_deploy_url":/api/model-factory/v1/prompt-used/1725466658891501568
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
    "ErrorCode": "ModelFactory.Mydb.DataBase.ParameterError",
    "Description": "数据库连接失败",
    "Solution": "请核对数据库的连接参数.",
    "ErrorDetails": "数据库登录信息错误",
    "ErrorLink": ""
}
```

### 2.20、删除提示词

```
POST /api/model-factory/v1/prompt/delete
```

请求参数：

| 序号 | 字段名称       | 字段类型     | 参数位置 | 是否必须 | 长度 | 字段说明     |
| :--- | :------------- | :----------- | -------- | :------- | ---- | :----------- |
| 1    | prompt_id      | string       | body     | 是       | 50   | 提示词id     |
| 2    | item_id        | string       | body     | 是       | 50   | 提示词项目id |
| 3    | type_id        | string       | body     | 是       | 50   | 提示词分类id |
| 4    | prompt_id_list | list<string> | body     | 是       | 50   | 提示词id列表 |

请求示例：

```json
每次传一个，传哪个删哪个，不能同时传两个以上的参数
{
    "item_id": "1726432304638857216"
}
{
    "type_id": "1725039792120532992"
}
{
    "prompt_id": "1725048681922695168"
}
{
    "prompt_id_list": ["1725048681922695168"]
}
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 字段说明         |
| :--- | :------- | :------- | :--------------- |
| 1    | res      | boolean  | 删除后的返回结果 |

响应示例：

```json
{
    "res": True
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
    "ErrorCode": "ModelFactory.Mydb.DataBase.ParameterError",
    "Description": "数据库连接失败",
    "Solution": "请核对数据库的连接参数.",
    "ErrorDetails": "数据库登录信息错误",
    "ErrorLink": ""
}
```

### 2.21、获取服务id

```
GET /api/model-factory/v1/get_id
```

请求参数：无

请求示例：无

响应参数：

| 序号 | 字段名称 | 字段类型 | 字段说明 |
| :--- | :------- | :------- | :------- |
| 1    | res      | string   | 服务id   |

响应示例：

```json
{
    "res": "4654525652235413544"
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
    "ErrorCode": "ModelFactory.PromptController.GetId.Error",
    "Description": "系统内部错误",
    "Solution": "请联系系统管理员.",
    "ErrorDetails": "获取服务id失败",
    "ErrorLink": ""
}
```

### 2.22、移动提示词

```
POST /api/model-factory/v1/prompt/move
```

请求参数：

| 序号 | 字段名称            | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明                   |
| :--- | :------------------ | :------- | -------- | :------- | ---- | :------------------------- |
| 1    | prompt_id           | string   | body     | 是       | 50   | 提示词id                   |
| 2    | prompt_item_type_id | string   | body     | 是       | 50   | 提示词分类id               |
| 3    | prompt_item_id      | string   | body     | 是       | 50   | 提示词项目id，用于修改项目 |

请求示例：

```json
{
    "prompt_id": "1726432304638857216",
    "prompt_item_type_id": "1725039792120532992",
    "prompt_item_id": "1725039792120532992",
}
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 字段说明 |
| :--- | :------- | :------- | :------- |
| 1    | res      | boolean  | 状态     |

响应示例：

```json
{
    "res": True
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
    "ErrorCode": "ModelFactory.Mydb.DataBase.ParameterError",
    "Description": "数据库连接失败",
    "Solution": "请核对数据库的连接参数.",
    "ErrorDetails": "数据库登录信息错误",
    "ErrorLink": ""
}
```

### 2.23、使用创建的提示词模板调用大模型

```
POST  /api/model-factory/v1/prompt/template/run
```

请求参数：

| 序号 | 字段名称    | 字段类型     | 参数位置 | 是否必须 | 长度 | 字段说明               |
| :--- | :---------- | :----------- | -------- | :------- | ---- | :--------------------- |
| 1    | inputs      | object       | body     | 否       |      | 输入的变量值           |
| 2    | prompt_id   | string       | body     | 是       | 50   | 提示词文本id           |
| 3    | history_dia | list<object> | body     | 否       |      | 对话型提示词的聊天记录 |
| 4    | model_para  | object       | body     | 是       |      | 模型参数               |
| 5    | model_name  | string       | body     | 是       | 100  | 选择使用的模型名称     |

请求示例：

```json
{
    "model_name": "AIshu-Reader-14B-v1.0",
    "model_para": {
        "temperature": 1,
        "top_p": 1,
        "presence_penalty": 0,
        "frequency_penalty": 0,
        "max_tokens": 200
    },
    "prompt_id": "1742737183012832489",
    "inputs": {
        "language": "英文",
        "text": "西瓜"
    },
    "history_dia": [
        {
            "role": "human",
            "message": "你好"
        },
        {
            "role": "ai",
            "message": "你好,您有什么问题?"
        }
    ]
}
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 字段说明 |
| :--- | :------- | :------- | :------- |
| 1    | res      | object   | 返回结果 |

响应示例：

```json
{
  "res": {
    "time": "这里是花费时间",
    "token_len": "这里是token长度",
    "data": "这是大模型回复的结果"
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
    "ErrorCode": "ModelFactory.Mydb.DataBase.ParameterError",
    "Description": "数据库连接失败",
    "Solution": "请核对数据库的连接参数.",
    "ErrorDetails": "数据库登录信息错误",
    "ErrorLink": ""
}
```

### 2.24、提示词管理内编辑接口

```
POST  /api/model-factory/v1/prompt/template/edit
```

请求参数：

| 序号 | 字段名称            | 字段类型     | 参数位置 | 是否必须 | 长度 | 字段说明                   |
| :--- | :------------------ | :----------- | -------- | :------- | ---- | :------------------------- |
| 1    | prompt_id           | string       | body     | 是       | 50   | 提示词id                   |
| 2    | prompt_name         | string       | body     | 是       | 50   | 提示词名称                 |
| 3    | messages            | string       | body     | 是       | 5000 | 提示词文本                 |
| 4    | variables           | list<object> | body     | 否       |      | 提示词变量                 |
| 5    | opening_remarks     | string       | body     | 否       | 150  | 对话开场白                 |
| 4    | icon                | string       | body     | 是       | 50   | 颜色配置                   |
| 5    | prompt_desc         | string       | body     | 否       | 255  | 提示词描述                 |
| 6    | prompt_item_type_id | string       | body     | 是       | 50   | 提示词分组id，用于修改分组 |
| 7    | prompt_item_id      | string       | body     | 是       | 50   | 提示词项目id，用于修改项目 |

请求示例：

```json
{
    "prompt_id": "1730486697692631040",
    "prompt_name": "test",
    "messages": "我想让你担任{{role}}面试官。我将成为候选人，您将向我询问面试问题。我希望你只作为面试官回答。不要一次写出所有的问题。我希望你只对我进行采访。问我问题，等待我的回答。不要写解释。像面试官一样一个一个问我，等我回答。\n",
    "variables": [
        {
            "var_name": "role",
            "field_name": "role",
            "optional": false,
            "field_type": "textarea"
        }
    ],
    "opening_remarks": "",
    "icon": "1",
    "prompt_desc": "描述",
    "prompt_item_type_id": "174832508430248590",
    "prompt_item_id": "1707217346845982754"
}
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 字段说明               |
| :--- | :------- | :------- | :--------------------- |
| 1    | res      | boolean  | 提示词修改后保存的状态 |

响应示例：

```json
{
    "res": True
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
    "ErrorCode": "ModelFactory.Mydb.DataBase.ParameterError",
    "Description": "数据库连接失败",
    "Solution": "请核对数据库的连接参数.",
    "ErrorDetails": "数据库登录信息错误",
    "ErrorLink": ""
}
```

### 2.25、批量创建提示词接口

```
POST  /api/model-factory/v1/prompt/batch_add
```

请求参数：

| 序号 | 字段名称              | 字段类型     | 参数位置 | 是否必须 | 长度 | 字段说明             |
| :--- | :-------------------- | :----------- | -------- | :------- | ---- | :------------------- |
| 1    | prompt_item_name      | string       | body     | 是       | 50   | 提示词项目名称       |
| 2    | prompt_item_type_name | string       | body     | 是       | 50   | 提示词分组名称       |
| 3    | prompt_list           | list<object> | body     | 是       |      | 需要创建的提示词列表 |

请求示例：

```json
[
    {
    	"prompt_item_name": "test",
    	"prompt_item_type_name": "分组1",
        "prompt_list": [
            {
             "prompt_name": "这w111",
             "prompt_desc": "这是一个描述",
             "prompt_type": "chat",
             "icon": "1",
             "messages": "{'base': '你是一个爱数的翻译机器人，你需要根据用户的要求，对输入文本进行翻译。\n要求：\n', 'language': '·将文本翻译为{{language}}；\n', 'style': '·将文本翻译为{{style}}风格；\n', 'text': '按照上述要求对文本：{{text}}进行翻译。'}",
            "variables": [
                {
                "var_name": "var1",
                "optional": false,
                "field_type": "text",
                "max_len": 48
                },
                {
                "var_name": "var2",
                "field_name": "xxx",
                "optional": "True",
                "field_type": "textarea"
                }
            ],
            "opening_remarks": ""
           },
           {
            "prompt_name": "这w22222222",
            "prompt_desc": "这是一个描述",
            "prompt_type": "chat",
            "icon": "1",
            "messages": "{'base': '你是一个爱数的翻译机器人，你需要根据用户的要求，对输入文本进行翻译。\n要求：\n', 'language': '·将文本翻译为{{language}}；\n', 'style': '·将文本翻译为{{style}}风格；\n', 'text': '按照上述要求对文本：{{text}}进行翻译。'}",
            "variables": [
            	{
                "var_name": "var1",
                "optional": false,
                "field_type": "text",
                "max_len": 48
                },
                {
                "var_name": "var2",
                "field_name": "xxx",
                "optional": "True",
                "field_type": "textarea"
                }
            ],
            "opening_remarks": ""
          }
        ]
    },
    ......
]
```

响应参数：

| 序号 | 字段名称 | 字段类型     | 字段说明     |
| :--- | :------- | :----------- | :----------- |
| 1    | res      | list<object> | 模型保存结果 |

响应示例：

```json
{
    "res": [
        {
            "prompt_item_name": "test",
            "prompt_item_type_name": "分组1",
            "ptompt_list": {
                "name1": "8392378493872948923",
                "name2": "2349023849023840899"
            }
        },
        {
            "prompt_item_name": "test",
            "prompt_item_type_name": "分组2",
            "ptompt_list": {
                "name1": "8392378493872948923",
                "name2": "2349023849023840899"
            }
        },
        {
            "prompt_item_name": "test",
            "prompt_item_type_name": "分组3",
            "ptompt_list": {
                "name1": "8392378493872948923",
                "name2": "2349023849023840899"
            }
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
    "ErrorCode": "ModelFactory.Mydb.DataBase.ParameterError",
    "Description": "数据库连接失败",
    "Solution": "请核对数据库的连接参数.",
    "ErrorDetails": "数据库登录信息错误",
    "ErrorLink": ""
}
```
