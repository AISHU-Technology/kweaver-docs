# 一、知识网络
## 1、知识网络管理
### 1.1、获取知识网络列表

```
GET  /api/builder/v1/knw/page
```

请求参数：

| 序号 | 字段名称 | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明                                        |
| :--- | :------- | :------- | -------- | :------- | ---- | :---------------------------------------------- |
| 1    | size     | int      | query    | 是       |      | 分页大小                                        |
| 2    | page     | int      | query    | 是       |      | 页码，1开始                                     |
| 3    | rule     | string   | query    | 是       | 20   | 排序条件,（intelligence_score, create，update） |
| 4    | order    | string   | query    | 是       | 4    | 排序顺序 (desc，asc)                            |

请求示例：

```
page=5&size=10&order=desc&rule=create
```

响应参数：

| 序号 | 字段名称 | 字段类型     | 字段说明 |
| :--- | -------- | :----------- | :------- |
| 1    | count    | int          | 总个数   |
| 2    | df       | list<object> | 具体信息 |

| 序号 | 字段名称           | 字段类型 | 字段说明                   |
| :--- | ------------------ | :------- | :------------------------- |
| 1    | color              | string   | 知识网络颜色               |
| 2    | create_time        | string   | 创建时间                   |
| 4    | create_by          | string   | 创建用户id                 |
| 5    | creator_name       | string   | 创建用户名称               |
| 6    | update_by          | string   | 最终操作人id               |
| 7    | group_column       | int      |                            |
| 8    | id                 | int      | 知识网络id                 |
| 9    | identify_id        | string   | 知识网络唯一id             |
| 10   | intelligence_score | string   | 领域知识值                 |
| 11   | knw_description    | string   | 知识网络描述               |
| 12   | knw_name           | string   | 知识网络名称               |
| 14   | operator_name      | string   | 最终操作人名称             |
| 15   | update_time        | string   | 更新时间                   |
| 16   | to_be_uploaded     | int      | 知识图谱是否需要上传的开关 |

响应示例：

```json
{
  "res": {
    "count": 1,
    "df": [
      {
        "color": "icon-color-110",
        "create_time": "2022-09-15 15:05:20",
        "create_by": "9d753e00-34c4-11ed-81e4-dad875ec6ee2",
        "creator_name": "test",
        "update_by": "853ba1db-4e37-11eb-a57d-0242ac190002",
        "group_column": 1,
        "id": 1,
        "identify_id": "c2c3e452-34c4-11ed-84c8-6ea0325d6f93",
        "intelligence_score":"34.67",
        "knw_description": "",
        "knw_name": "test",
        "operator_name": "test",
        "update_time": "2022-09-19 10:24:31",
        "to_be_uploaded": 0
      }
    ]
  }
}
```

### 1.2、根据名称分页查询知识网络

```
GET  /api/builder/v1/knw/page_by_name
```

请求参数：

| 序号 | 字段名称 | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明                           |
| :--- | :------- | :------- | -------- | :------- | ---- | :--------------------------------- |
| 1    | knw_name | string   | query    | 是       | 50   | 知识网络名称                       |
| 2    | page     | int      | query    | 是       |      | 页面                               |
| 3    | size     | int      | query    | 是       |      | 每页条数                           |
| 4    | order    | string   | query    | 是       | 4    | desc asc按时间升序降序             |
| 5    | rule     | string   | query    | 是       | 6    | create按创建时间、update按更新时间 |

请求示例：

```
knw_name=xxx&page=5&size=10&order=desc&rule=create
```

响应参数：

| 序号 | 字段名称 | 字段类型     | 字段说明 |
| :--- | -------- | :----------- | :------- |
| 1    | total    | int          | 总个数   |
| 2    | df       | list<object> | 具体信息 |

| 序号 | 字段名称           | 字段类型 | 字段说明                             |
| :--- | ------------------ | :------- | :----------------------------------- |
| 1    | color              | string   | 知识网络颜色                         |
| 2    | create_time        | string   | 创建时间                             |
| 4    | create_by          | string   | 创建用户id                           |
| 5    | creator_name       | string   | 创建用户名称                         |
| 6    | update_by          | string   | 最终操作人id                         |
| 7    | group_column       | int      |                                      |
| 8    | id                 | int      | 知识网络id                           |
| 9    | identify_id        | string   | 知识网络唯一id                       |
| 10   | intelligence_score | string   | 领域知识值                           |
| 11   | knw_description    | string   | 知识网络描述                         |
| 12   | knw_name           | string   | 知识网络名称                         |
| 14   | operator_name      | string   | 最终操作人名称                       |
| 15   | update_time        | string   | 更新时间                             |
| 16   | to_be_uploaded     | int      | 新增字段。知识图谱是否需要上传的开关 |

响应示例：

```json
{
  "res": {
    "count": 1,
    "df": [
      {
        "color": "icon-color-110",
        "create_time": "2022-09-15 15:05:20",
        "create_by": "9d753e00-34c4-11ed-81e4-dad875ec6ee2",
        "creator_name": "test",
        "update_by": "853ba1db-4e37-11eb-a57d-0242ac190002",
        "group_column": 1,
        "id": 1,
        "identify_id": "c2c3e452-34c4-11ed-84c8-6ea0325d6f93",
        "intelligence_score":"34.67",
        "knw_description": "",
        "knw_name": "test",
        "operator_name": "test",
        "update_time": "2022-09-19 10:24:31",
        "to_be_uploaded": 0
      }
    ]
  }
}
```

### 1.3、 新建知识网络

```
POST  /api/builder/v1/knw/add
```

请求参数：

| 序号 | 字段名称       | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明                             |
| :--- | :------------- | :------- | -------- | :------- | ---- | :----------------------------------- |
| 1    | knw_name       | string   | body     | 是       | 50   | 知识网络名称                         |
| 2    | knw_des        | string   | body     | 否       | 200  | 知识网络描述                         |
| 3    | knw_color      | string   | body     | 是       | 50   | 知识网络颜色                         |
| 4    | to_be_uploaded | int      | body     | 否       |      | 该知识网络是否需要上传0: 关闭1: 开启 |

请求示例：

```json
{
	"knw_name":"xxx",
    "knw_des":"xxx",
    "knw_color":"#126EE3",
    "to_be_uploaded":0
}
```

响应参数：

| 序号 | 字段名称  | 字段类型 | 字段说明     |
| :--- | --------- | :------- | :----------- |
| 1    | tcodeotal | int      | 状态码       |
| 2    | data      | int      | 创建的网络id |
| 3    | message   | string   | success      |

响应示例：

```json
{
    "code": 200,
    "data": 9,
    "message": "success"
}
```

### 1.4、 编辑知识网络

```
POST  /api/builder/v1/knw/edit
```

请求参数：

| 序号 | 字段名称       | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明                             |
| :--- | :------------- | :------- | -------- | :------- | ---- | :----------------------------------- |
| 1    | knw_id         | int      | body     | 是       |      | 知识网络id                           |
| 2    | knw_name       | string   | body     | 是       | 50   | 知识网络名称                         |
| 3    | knw_des        | string   | body     | 否       | 200  | 知识网络描述                         |
| 4    | knw_color      | string   | body     | 是       | 50   | 知识网络颜色                         |
| 5    | to_be_uploaded | int      | body     | 否       |      | 该知识网络是否需要上传0: 关闭1: 开启 |

请求示例：

```json
{
	"knw_id":1,
	"knw_name":"xxx",
    "knw_des":"xxx",
    "knw_color":"#126EE3",
    "to_be_uploaded":0
}
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 字段说明         |
| :--- | :------- | :------- | :--------------- |
| 1    | res      | string   | 返回的结果字符串 |

响应示例：

```json
{
    "res": "edit knowledge network success"
}
```

### 1.5、 删除知识网络

```
POST  /api/builder/v1/knw/delete
```

请求参数：

| 序号 | 字段名称 | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明   |
| :--- | :------- | :------- | -------- | :------- | ---- | :--------- |
| 1    | knw_id   | int      | body     | 是       |      | 知识网络id |

请求示例：

```json
{
	"knw_id":1
}
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 字段说明         |
| :--- | :------- | :------- | :--------------- |
| 1    | res      | string   | 返回的结果字符串 |

响应示例：

```json
{
    "res": "delete knoledge network success"
}
```

### 1.6、 根据知识网络获取图谱列表

```
GET  /api/builder/v1/knw/graph/page
```

请求参数：

| 序号 | 字段名称 | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明                                                     |
| :--- | :------- | :------- | -------- | :------- | ---- | :----------------------------------------------------------- |
| 1    | knw_id   | int      | query    | 是       |      | 知识网络id（传 -1 返回全部的知识图谱）                       |
| 2    | page     | int      | query    | 是       |      | 页码                                                         |
| 3    | size     | int      | query    | 是       |      | 每页数量                                                     |
| 4    | order    | string   | query    | 是       | 4    | desc（从新到旧排序）asc（从旧到新排序）                      |
| 5    | name     | string   | query    | 是       | 100  | 对图谱名称模糊搜索                                           |
| 6    | rule     | string   | query    | 是       | 6    | 默认按更新时间排序update（按更新时间排序）create（按创建时间排序）name（按图谱名称排序） |
| 7    | filter   | string   | query    | 否       | 20   | 可选值：all(默认)，upload，export，running_success           |

请求示例：

```
/api/builder/v1/knw/graph/page?knw_id=1&page=1&size=20&order=desc&name&rule=create
```

响应参数：

| 序号 | 字段名称 | 字段类型     | 是否必须 | 字段说明 |
| :--- | :------- | :----------- | :------- | :------- |
| 1    | count    | int          | 是       | 总数     |
| 2    | df       | list<object> | 是       | 分页信息 |

| 序号 | 字段名称       | 字段类型 | 是否必须 | 字段说明                                   |
| :--- | :------------- | :------- | :------- | :----------------------------------------- |
| 1    | id             | int      | 是       | 图谱ID                                     |
| 2    | create_time    | string   | 是       | 创建时间                                   |
| 3    | export         | boolean  | 是       | 是否可以导出                               |
| 4    | graph_db_name  | string   | 是       | 图数据库DB名                               |
| 5    | is_import      | boolean  | 是       | 是否为导入的图谱                           |
| 6    | kgDesc         | string   | 是       | 图谱描述                                   |
| 7    | knowledge_type | string   | 是       | 知识类型                                   |
| 8    | name           | string   | 是       | 图谱名称                                   |
| 9    | otl_id         | string   | 是       | 本体id                                     |
| 10   | rabbitmqDs     | int      | 是       | 是否使用rabbitmq数据源。1为使用，0为未使用 |
| 11   | status         | string   | 是       | 图谱状态                                   |
| 12   | step_num       | int      | 是       | 图谱配置流程到了第几步                     |
| 13   | taskstatus     | string   | 是       | 任务运行状态                               |
| 14   | updateTime     | string   | 是       | 更新时间                                   |
| 15   | knw_id         | int      | 是       | 知识网络id                                 |

响应示例：

```json
{
    "res": {
        "count": 4,
        "df": [
            {
                "id": 1,
                "create_time": "2023-09-13 11:11:11",
                "export": true,
                "graph_db_name": "xxxxxxxxxx",
                "is_import": false,
                "kgDesc": "",
                "knowledge_type": "kg",
                "name": "test",
                "otl_id": "7",
                "rabbitmqDs": 0,
                "status": "normal",
                "step_num": 4,
                "taskstatus": "normal",
                "updateTime": "2023-09-13 11:11:11",
                "knw_id": 1
        	},
            ...
        ]
    }
}
```

## 2、知识图谱管理

### 2.1、执行图谱构建任务

```
POST  /api/builder/v1/task/add/{graph_id}
```

请求参数：

| 序号 | 字段名称  | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明         |
| :--- | :-------- | :------- | -------- | :------- | ---- | :--------------- |
| 1    | graph_id  | int      | path     | 是       |      | 图谱id           |
| 2    | task_type | string   | body     | 是       | 10   | 全量构建（full）增量构建（increment） |

请求示例：

```
/api/builder/v1/task/add/121
{
	"task_type":"full"
}
```

响应参数：

| 序号 | 字段名称      | 字段类型 | 字段说明           |
| :--- | :------------ | :------- | :----------------- |
| 1    | graph_task_id | string   | 任务id(非celeryid) |

响应示例：

```json
{
    "res": {
         "graph_task_id": 11
    }
}
```

### 2.2、执行图谱分批构建任务

```
POST  /api/builder/v1/task/batch_add/{graph_id}
```

请求参数：

| 序号 | 字段名称     | 字段类型  | 字段位置 | 是否必须 | 长度 | 字段说明                                                     |
| ---- | :----------- | :-------- | :------- | :------- | ---- | :----------------------------------------------------------- |
| 1    | graph_id     | int       | path     | 是       |      | 图谱id                                                       |
| 2    | subgraph_ids | list<int> | body     | 是       |      | 子图配置id列表                                               |
| 3    | write_mode   | string    | body     | 是       | 10   | 在一次分组运行中多个组之间相同的类执行的写入模式（skip: 跳过   overwrite: 重新运行） |
| 4    | flag         | string    | body     | 是       | 5    | 构建方式  （full：全量构建，默认   increment：增量构建）     |

请求示例：

```
/api/builder/v1/task/batch_add/121
{
	"subgraph_ids":[1],
	"write_mode":"skip",
	"flag":"full"
}
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 字段说明 |
| :--- | :------- | :------- | :------- |
| 1    | res      | string   | 执行结果 |

响应示例：

```json
{
    "res": "8d1a0716-53c9-4476-bf9e-d9d8f9ba16a7 start running success"
}
```

### 2.3、删除图谱构建任务

```
POST  /api/builder/v1/task/delete/{graph_id}
```

请求参数：

| 序号 | 字段名称 | 字段类型  | 字段位置 | 是否必须 | 长度 | 字段说明       |
| ---- | :------- | :-------- | :------- | :------- | ---- | :------------- |
| 1    | graph_id | int       | path     | 是       |      | 图谱id         |
| 2    | task_ids | list<int> | body     | 是       |      | 历史任务id列表 |

请求示例：

```
/api/builder/v1/task/delete/14
{
    "task_ids": [35, 36]
}
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 字段说明 |
| :--- | :------- | :------- | :------- |
| 1    | res      | string   | 执行结果 |

响应示例：

```json
{
    "res": "delete task success"
}
```

### 2.4、分页获取图谱构建任务列表

```
GET  /api/builder/v1/task/page/{graph_id}
```

请求参数：

| 序号 | 字段名称     | 字段类型 | 字段位置 | 是否必须 | 长度 | 字段说明                                                     |
| ---- | :----------- | :------- | :------- | :------- | ---- | :----------------------------------------------------------- |
| 1    | graph_id     | int      | path     | 是       |      | 图谱id                                                       |
| 2    | page         | int      | query    | 是       |      | 页数前端默认传1                                              |
| 3    | size         | int      | query    | 是       |      | 每页大小前端默认传20                                         |
| 4    | order        | string   | query    | 是       |      | 按id进行排序（desc/asc，前端默认传desc）                     |
| 5    | rule         | string   | query    | 是       |      | 排序字段（start_time/end_time)                               |
| 6    | status       | string   | query    | 是       | 100  | 任务状态，（normal, running, waiting, failed, stop, all，前端默认传all） |
| 7    | graph_name   | string   | query    | 是       | 100  | 图谱名称（前端默认传空）                                     |
| 8    | task_type    | string   | query    | 是       | 50   | 构建任务类型（all：返回全部，前端默认   full：全量构建   increment：增量构建） |
| 9    | trigger_type | string   | query    | 是       | 3    | 触发方式（all：返回全部，前端默认    0：手动触发    1：自动触发     2：实时触发） |

请求示例：

```
/api/builder/v1/task/page/17?page=1&size=10&order=asc&rule=start_time&status=all&graph_name=&task_type=all&trigger_type=all
```

响应参数：

| 序号 | 字段名称     | 字段类型     | 是否必须 | 字段说明     |
| :--- | :----------- | :----------- | :------- | :----------- |
| 1    | count        | int          | 是       | 任务总数     |
| 2    | df           | list<object> | 是       | 分页任务信息 |
| 3    | graph_status | string       | 是       | 图谱状态     |

| 序号 | 字段名称          | 字段类型     | 是否必须 | 字段说明                                                    |
| :--- | :---------------- | :----------- | :------- | :---------------------------------------------------------- |
| 1    | all_time          | string       | 是       | 总耗时                                                      |
| 2    | celery_task_id    | string       | 是       | celery任务id                                                |
| 3    | count_status      | int          | 是       | nebula实体和关系数量是否统计完成    0：未完成   1：统计完成 |
| 4    | create_by         | string       | 是       | 创建人userId                                                |
| 5    | edge              | string       | 是       | 关系类信息                                                  |
| 6    | edge_num          | int          | 是       | 关系类数量                                                  |
| 7    | edge_pro_num      | int          | 是       | 关系类属性信息                                              |
| 8    | effective_storage | bool         | 是       | 图数据库是否有效                                            |
| 9    | end_time          | string       | 是       | 任务结束时间                                                |
| 10   | entity            | string       | 是       | 实体类信息                                                  |
| 11   | entity_num        | int          | 是       | 实体类数量                                                  |
| 12   | entity_pro_num    | int          | 是       | 实体类属性数量                                              |
| 13   | error_report      | string       | 是       | 错误信息                                                    |
| 14   | extract_type      | string       | 是       | 抽取类型                                                    |
| 15   | files             | list<object> | 是       | 关联文件                                                    |
| 16   | graph_edge        | int          | 是       | 关系数量                                                    |
| 17   | graph_entity      | int          | 是       | 实体数量                                                    |
| 18   | graph_id          | int          | 是       | 知识图谱id                                                  |
| 19   | graph_name        | string       | 是       | 知识图谱名称                                                |
| 20   | kg_id             | int          | 是       | 知识图谱id                                                  |
| 21   | parent            | string       | 是       | 父任务的celery task id                                      |
| 22   | start_time        | string       | 是       | 任务开始时间                                                |
| 23   | subgraph_id       | int          | 是       | 子图id                                                      |
| 24   | task_id           | int          | 是       | 任务id                                                      |
| 25   | task_name         | string       | 是       | 任务名称                                                    |
| 26   | task_status       | string       | 是       | 任务状态                                                    |
| 27   | task_type         | string       | 是       | 任务类型                                                    |
| 28   | trigger_type      | int          | 是       | 任务触发方式                                                |

响应示例：

```json
{
    "res": {
        "count": 13,
        "df": [
            {
                "all_time": null,
                "celery_task_id": "6a6d3704-c61a-4ee9-bf60-134fe6c2ae1e",
                "count_status": 0,
                "create_by": null,
                "edge": "[{'edge_id': 8, 'name': 'account_2_account_role', 'description': '', 'alias': '3框', 'synonym': '', 'properties_index': [], 'default_tag': '', 'properties': [], 'relations': ['account', 'account_2_account_role', 'account_role'], 'colour': 'rgba(227,150,64,1)', 'shape': 'line', 'width': '0.25x', 'source_type': 'manual', 'index_default_switch': False, 'index_main_switch': False, 'model': ''}, {'edge_id': 7, 'name': 'account_2_async_tasks', 'description': '', 'alias': '2框', 'synonym': '', 'properties_index': [], 'default_tag': '', 'properties': [], 'relations': ['account', 'account_2_async_tasks', 'async_tasks'], 'colour': 'rgba(227,150,64,1)', 'shape': 'line', 'width': '0.25x', 'source_type': 'manual', 'index_default_switch': False, 'index_main_switch': False, 'model': ''}]",
                "edge_num": null,
                "edge_pro_num": null,
                "effective_storage": true,
                "end_time": null,
                "entity": "[{'entity_id': 4, 'name': 'async_tasks', 'description': '', 'alias': 'async_tasks', 'synonym': '', 'default_tag': 'id', 'properties_index': ['id'], 'primary_key': ['id'], 'vector_generation': [], 'properties': [{'name': 'id', 'description': '', 'alias': 'id', 'data_type': 'integer', 'synonym': ''}, {'name': 'task_type', 'description': '', 'alias': 'task_type', 'data_type': 'string', 'synonym': ''}, {'name': 'task_status', 'description': '', 'alias': 'task_status', 'data_type': 'string', 'synonym': ''}, {'name': 'task_name', 'description': '', 'alias': 'task_name', 'data_type': 'string', 'synonym': ''}, {'name': 'celery_task_id', 'description': '', 'alias': 'celery_task_id', 'data_type': 'string', 'synonym': ''}, {'name': 'relation_id', 'description': '', 'alias': 'relation_id', 'data_type': 'string', 'synonym': ''}, {'name': 'task_params', 'description': '', 'alias': 'task_params', 'data_type': 'string', 'synonym': ''}, {'name': 'result', 'description': '', 'alias': 'result', 'data_type': 'string', 'synonym': ''}, {'name': 'create_time', 'description': '', 'alias': 'create_time', 'data_type': 'datetime', 'synonym': ''}, {'name': 'finished_time', 'description': '', 'alias': 'finished_time', 'data_type': 'datetime', 'synonym': ''}], 'x': 706.3500516484272, 'y': 451.4230092967168, 'icon': '', 'shape': 'circle', 'size': '0.5x', 'fill_color': 'rgba(92,83,155,1)', 'stroke_color': 'rgba(92,83,155,1)', 'text_color': 'rgba(0,0,0,1)', 'text_position': 'top', 'text_width': 15, 'index_default_switch': False, 'index_main_switch': False, 'text_type': 'adaptive', 'source_type': 'automatic', 'model': '', 'task_id': '1', 'icon_color': '#ffffff'}, {'entity_id': 5, 'name': 'account_role', 'description': '', 'alias': 'account_role', 'synonym': '', 'default_tag': 'id', 'properties_index': ['id'], 'primary_key': ['id'], 'vector_generation': [], 'properties': [{'name': 'id', 'description': '', 'alias': 'id', 'data_type': 'integer', 'synonym': ''}, {'name': 'account_id', 'description': '', 'alias': 'account_id', 'data_type': 'string', 'synonym': ''}, {'name': 'role_id', 'description': '', 'alias': 'role_id', 'data_type': 'integer', 'synonym': ''}, {'name': 'created', 'description': '', 'alias': 'created', 'data_type': 'datetime', 'synonym': ''}, {'name': 'updated', 'description': '', 'alias': 'updated', 'data_type': 'datetime', 'synonym': ''}], 'x': 672.6638924541155, 'y': 696.1195006417407, 'icon': '', 'shape': 'circle', 'size': '0.5x', 'fill_color': 'rgba(216,112,122,1)', 'stroke_color': 'rgba(216,112,122,1)', 'text_color': 'rgba(0,0,0,1)', 'text_position': 'top', 'text_width': 15, 'index_default_switch': False, 'index_main_switch': False, 'text_type': 'adaptive', 'source_type': 'automatic', 'model': '', 'task_id': '1', 'icon_color': '#ffffff'}, {'entity_id': 6, 'name': 'account', 'description': '', 'alias': 'account', 'synonym': '', 'default_tag': 'id', 'properties_index': ['id'], 'primary_key': ['id'], 'vector_generation': [], 'properties': [{'name': 'id', 'description': '', 'alias': 'id', 'data_type': 'integer', 'synonym': ''}, {'name': 'username', 'description': '', 'alias': 'username', 'data_type': 'string', 'synonym': ''}, {'name': 'status', 'description': '', 'alias': 'status', 'data_type': 'integer', 'synonym': ''}, {'name': 'app_id', 'description': '', 'alias': 'app_id', 'data_type': 'string', 'synonym': ''}, {'name': 'account_id', 'description': '', 'alias': 'account_id', 'data_type': 'string', 'synonym': ''}, {'name': 'third_party_id', 'description': '', 'alias': 'third_party_id', 'data_type': 'string', 'synonym': ''}, {'name': 'source_type', 'description': '', 'alias': 'source_type', 'data_type': 'integer', 'synonym': ''}], 'x': 477.9860558974574, 'y': 594.4574900615426, 'icon': '', 'shape': 'circle', 'size': '0.5x', 'fill_color': 'rgba(227,150,64,1)', 'stroke_color': 'rgba(227,150,64,1)', 'text_color': 'rgba(0,0,0,1)', 'text_position': 'top', 'text_width': 15, 'index_default_switch': False, 'index_main_switch': False, 'text_type': 'adaptive', 'source_type': 'automatic', 'model': '', 'task_id': '1', 'icon_color': '#ffffff'}]",
                "entity_num": null,
                "entity_pro_num": null,
                "error_report": null,
                "extract_type": null,
                "files": null,
                "graph_edge": null,
                "graph_entity": null,
                "graph_id": 1,
                "graph_name": "hsq_mysql",
                "kg_id": 1,
                "parent": null,
                "start_time": "2023-12-19 14:38:46",
                "subgraph_id": 0,
                "task_id": 80,
                "task_name": "hsq_mysql",
                "task_status": "normal",
                "task_type": "full",
                "trigger_type": 0
            },
            ...
        ],
        "graph_status": "normal"
    }
}
```

### 2.5、终止图谱构建任务

```
POST  /api/builder/v1/task/stop
```

请求参数：

| 序号 | 字段名称 | 字段类型 | 字段位置 | 是否必须 | 长度 | 字段说明                                   |
| ---- | :------- | :------- | :------- | :------- | ---- | :----------------------------------------- |
| 1    | graph_id | int      | body     | 否       |      | 图谱id，传该参数表示终止该图谱下的所有任务 |
| 2    | task_id  | int      | body     | 否       |      | 历史任务id，传该参数表示终止该任务         |

请求示例：

```json
//传参只能为graph_id与task_id二者其一
{
    "graph_id": 17
}
//或者
{
    "task_id": 17
}
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 字段说明 |
| :--- | :------- | :------- | :------- |
| 1    | res      | string   | 执行结果 |

响应示例：

```json
{
  "res": "stop task success."
}
```

### 2.6、获取任务详情

```
GET  /api/builder/v1/task/detail/{task_id}
```

请求参数：

| 序号 | 字段名称    | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明                                           |
| :--- | :---------- | :------- | :------- | :------- | ---- | :------------------------------------------------- |
| 1    | task_id     | int      | path     | 是       |      | 任务id                                             |
| 2    | task_type   | string   | query    | 否       | 50   | 任务类型，可选值：entity, edge, model              |
| 3    | task_status | string   | query    | 否       | 50   | 任务状态，可选值：waiting, running, normal, failed |
| 4    | rule        | string   | query    | 否       | 10   | 排序字段，可选值：start_time, end_time             |
| 5    | order       | string   | query    | 否       | 4    | 排序顺序，可选值：asc, desc                        |
| 6    | page        | int      | query    | 否       |      | 第几页                                             |
| 7    | size        | int      | query    | 否       |      | 当前页显示数量                                     |

请求示例：

```
/api/builder/v1/task/17?page=1&size=10&order=asc&rule=start_time&task_status=running&task_type=model
```

响应参数：

| 序号 | 字段名称 | 字段类型     | 字段说明         |
| :--- | :------- | :----------- | :--------------- |
| 1    | count    | int          | 不分页的结果总数 |
| 2    | edge     | list<object> | 关系类本体信息   |
| 3    | tasks    | list<object> | 任务列表         |
| 4    | entity   | list<object> | 实体类本体信息   |

| 序号 | 字段名称       | 字段类型     | 字段说明                                           |
| :--- | :------------- | :----------- | :------------------------------------------------- |
| 1    | alias          | string       | 实体类显示名/关系类显示名                          |
| 2    | all_time       | string       | 总耗时                                             |
| 3    | end_time       | string       | 结束时间                                           |
| 4    | error_report   | string       | 失败原因                                           |
| 5    | extract_type   | string       | 抽取类型                                           |
| 6    | files          | list<object> | 关联文件                                           |
| 7    | id             | int          | 任务id                                             |
| 8    | name           | string       | 实体类名/关系类名/模型名                           |
| 9    | relation       | list<string> | 起点、终点，例: [personName, Address]              |
| 10   | relation_alias | list<string> | 起点别名、终点别名，例:[人物名称, 居住地址]        |
| 11   | start_time     | string       | 开始时间                                           |
| 12   | task_status    | string       | 任务状态，可选值：waiting, running, normal, failed |
| 13   | task_type      | string       | 任务类型，可选值：entity, edge, model              |

| 序号 | 字段名称 | 字段类型     | 字段说明     |
| :--- | :------- | :----------- | :----------- |
| 1    | ds_id    | int          | 数据源id     |
| 2    | ds_name  | string       | 数据源名称   |
| 3    | ds_path  | string       | 数据源路径   |
| 4    | files    | list<object> | 关联文件列表 |

| 序号 | 字段名称    | 字段类型 | 字段说明                                                     |
| :--- | :---------- | :------- | :----------------------------------------------------------- |
| 1    | file_name   | string   | 对mysql、hive：表名对SQLserver、KingbaseES、postgreSQL: 模式名/表名对AS：文件名，例："user.csv"SQL抽取时，为SQL数据文件名称 |
| 2    | file_path   | string   | 对数据库：数据库名对AS：文件路径，例："部门文档库1/csv/user.csv" |
| 3    | file_source | string   | 数据源类型为mysql、hive、clickhouse：数据表<br />数据源类型为sqlserver、kingbesees、postgresql： 模式/数据表<br />SQL抽取时，为SQL语句 |
| 4    | file_type   | string   | 仅对模型抽取才返回file：文件dir：文件夹                      |

响应示例：

```json
{
    "res": {
        "count": 1
        "edge": [
            {
                "alias": "3框",
                "colour": "rgba(227,150,64,1)",
                "default_tag": "",
                "description": "",
                "edge_id": 8,
                "index_default_switch": false,
                "index_main_switch": false,
                "model": "",
                "name": "account_2_account_role",
                "properties": [],
                "properties_index": [],
                "relations": [
                    "account",
                    "account_2_account_role",
                    "account_role"
                ],
                "shape": "line",
                "source_type": "manual",
                "synonym": "",
                "width": "0.25x"
            },
            ...
        ],
        "entity": [
            {
                "alias": "account",
                "default_tag": "id",
                "description": "",
                "entity_id": 6,
                "fill_color": "rgba(227,150,64,1)",
                "icon": "",
                "icon_color": "#ffffff",
                "index_default_switch": false,
                "index_main_switch": false,
                "model": "",
                "name": "account",
                "primary_key": [
                    "id"
                ],
                "properties": [
                    {
                        "alias": "id",
                        "data_type": "integer",
                        "description": "",
                        "name": "id",
                        "synonym": ""
                    },
                    {
                        "alias": "username",
                        "data_type": "string",
                        "description": "",
                        "name": "username",
                        "synonym": ""
                    },
                    ...
                ],
                "properties_index": [
                    "id"
                ],
                "shape": "circle",
                "size": "0.5x",
                "source_type": "automatic",
                "stroke_color": "rgba(227,150,64,1)",
                "synonym": "",
                "task_id": "1",
                "text_color": "rgba(0,0,0,1)",
                "text_position": "top",
                "text_type": "adaptive",
                "text_width": 15,
                "vector_generation": [],
                "x": 477.9860558974574,
                "y": 594.4574900615426
            },
            ...
        ],
        "tasks": [
            {
                "alias": "account",
                "all_time": "00:00:00",
                "end_time": "2023-12-18 14:20:35",
                "error_report": null,
                "extract_type": "standardExtraction",
                "files": [
                    {
                        "ds_id": 1,
                        "ds_name": "mysql255",
                        "ds_path": "anydata",
                        "files": [
                            {
                                "file_name": "account",
                                "file_path": "anydata",
                                "file_source": "account"
                            }
                        ]
                    }
                ],
                "id": 68,
                "name": "account",
                "relation": null,
                "relation_alias": null,
                "start_time": "2023-12-18 14:20:35",
                "task_status": "normal",
                "task_type": "entity"
            },
            ...
        ]
    }
}
```

### 2.7、创建图谱

```
POST  /api/builder/v1/graph/add
```

请求参数：

| 序号 | 字段名称      | 字段类型 | 字段位置 | 是否必须 | 长度 | 字段说明             |
| ---- | :------------ | :------- | :------- | :------- | ---- | :------------------- |
| 1    | graph_step    | string   | body     | 是       |      | 创建步骤             |
| 2    | knw_id        | int      | body     | 是       |      | 知识网络id           |
| 3    | graph_process | object   | body     | 是       |      | 流程中具体的配置信息 |

请求示例：

```json
{
    "graph_step": "graph_baseInfo",
    "knw_id": 1,
    "graph_process": {
        "graph_name": "图谱名称",
        "graph_des": ""
    }
}
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 字段说明 |
| :--- | :------- | :------- | :------- |
| 1    | graph_id | int      | 图谱id   |
| 2    | res      | string   | 创建成功 |

响应示例：

```json
{
  "graph_id": 1,
  "res": "7 success."
}
```

### 2.8、查询图谱数据库连接信息

```
GET  /api/builder/v1/graph/graph_db
```

响应参数：

| 序号 | 字段名称 | 字段类型     | 字段说明 |
| :--- | :------- | :----------- | :------- |
| 1    | df       | list<pbject> | 执行结果 |

响应示例：

```json
{
    "res": {
        "df": [
            {
                "ip": "10.2.196.58"               
            }
        ]
    }
}
```

### 2.9、查询图谱

```
GET  /api/builder/v1/graph/{graph_id}
```

请求参数：

| 序号 | 字段名称 | 字段类型 | 字段位置 | 是否必须 | 长度 | 字段说明 |
| ---- | :------- | :------- | :------- | :------- | ---- | :------- |
| 1    | graph_id | int      | path     | 是       |      | 图谱id   |

请求示例：

```
/api/builder/v1/graph/1
```

响应示例：

```json
{
    "res": {
        "id": 2,
        "create_by": "",
        "create_time": "2024-04-02 11:01:58",
        "update_by": "",
        "update_time": "2024-05-22 13:59:59",
        "graph_name": "test",
        "graph_baseInfo": {
            "graph_Name": "test",
            "graph_des": "",
            "graphDBAddress": "nebula-graphd",
            "graph_mongo_Name": "mongoDB-1",
            "graph_DBName": "u5ed7e5baf09d11eeb7110242ac130010-5"
        },
        "graph_ds": [
            {
                "id": 3,
                "create_by": "",
                "create_time": "2024-04-02 11:02:41",
                "update_by": "",
                "update_time": "2024-06-06 11:32:05",
                "ds_name": "kom",
                "data_type": "structured",
                "data_source": "mysql",
                "ds_user": "root",
                "ds_password": "RWlzb29fMTIz",
                "ds_address": "10.239.20.148",
                "ds_port": 3306,
                "ds_path": "kom",
                "extract_type": "standardExtraction",
                "ds_auth": "",
                "vhost": "",
                "queue": "",
                "json_schema": "",
                "knw_id": 1,
                "connect_type": ""
            }
        ],
        "graph_otl": [
            {
                "id": 2,
                "create_by": "",
                "create_time": "2024-04-02 11:01:58",
                "update_by": "",
                "update_time": "2024-04-02 18:10:25",
                "ontology_name": "",
                "ontology_des": "",
                "otl_status": "available",
                "entity": [
                    {
                        "entity_id": 10,
                        "name": "a",
                        "description": "",
                        "alias": "a",
                        "synonym": "",
                        "default_tag": "b",
                        "properties_index": [
                            "a",
                            "b"
                        ],
                        "primary_key": [
                            "a",
                            "b"
                        ],
                        "vector_generation": [
                            "a",
                            "b"
                        ],
                        "properties": [
                            {
                                "name": "a",
                                "description": "",
                                "alias": "a",
                                "data_type": "string",
                                "synonym": ""
                            },
                            {
                                "name": "b",
                                "description": "",
                                "alias": "b",
                                "data_type": "string",
                                "synonym": ""
                            }
                        ],
                        "x": 960,
                        "y": 414.5,
                        "icon": "empty",
                        "shape": "circle",
                        "size": "0.5x",
                        "fill_color": "rgba(234,198,0,1)",
                        "stroke_color": "rgba(101,60,63,1)",
                        "text_color": "rgba(0,0,0,1)",
                        "text_position": "top",
                        "text_width": 15,
                        "index_default_switch": false,
                        "index_main_switch": true,
                        "text_type": "adaptive",
                        "source_type": "manual",
                        "model": "",
                        "task_id": "",
                        "icon_color": "#ffffff"
                    }
                ],
                "edge": [],
                "used_task": [],
                "all_task": [],
                "identify_id": null,
                "knw_id": 1,
                "domain": "[]",
                "otl_temp": "[]",
                "canvas": {}
            }
        ],
        "graph_KMap": {
            "entity": [
                {
                    "name": "a",
                    "entity_type": "12345_17",
                    "x": 960,
                    "y": 414.5,
                    "property_map": [
                        {
                            "entity_prop": "规范1",
                            "otl_prop": "b"
                        },
                        {
                            "entity_prop": "asc1",
                            "otl_prop": "a"
                        }
                    ],
                    "alias": "a",
                    "icon": "empty",
                    "shape": "circle",
                    "size": "0.5x",
                    "fill_color": "rgba(234,198,0,1)",
                    "stroke_color": "rgba(101,60,63,1)",
                    "text_color": "rgba(0,0,0,1)",
                    "icon_color": "#ffffff",
                    "text_position": "top",
                    "text_width": 15,
                    "text_type": "adaptive",
                    "default_tag": "b",
                    "primary_key": [
                        "a",
                        "b"
                    ],
                    "source_type": "manual",
                    "model": ""
                }
            ],
            "edge": [],
            "files": [
                {
                    "ds_id": 3,
                    "data_source": "mysql",
                    "ds_path": "kom",
                    "extract_type": "standardExtraction",
                    "extract_rules": [
                        {
                            "entity_type": "12345_17",
                            "property": [
                                {
                                    "column_name": "asc1",
                                    "property_field": "asc1"
                                },
                                {
                                    "column_name": "规范1",
                                    "property_field": "规范1"
                                }
                            ]
                        }
                    ],
                    "files": [
                        {
                            "file_name": "12345?",
                            "file_path": "kom",
                            "file_source": "12345?"
                        }
                    ],
                    "x": 0,
                    "y": 0,
                    "ds_name": "kom"
                }
            ]
        },
        "rabbitmq_ds": 0,
        "step_num": 4,
        "is_upload": 0,
        "KDB_name": "u5ed7e5baf09d11eeb7110242ac130010-5",
        "KDB_name_temp": "u5ed7e5baf09d11eeb7110242ac130010-4",
        "kg_data_volume": 1,
        "status": "normal",
        "graph_update_time": null,
        "knw_id": 1,
        "graph_used_ds": [
            {
                "id": 3,
                "create_by": "",
                "create_time": "2024-04-02 11:02:41",
                "update_by": "",
                "update_time": "2024-06-06 11:32:05",
                "ds_name": "kom",
                "data_type": "structured",
                "data_source": "mysql",
                "ds_user": "root",
                "ds_password": "RWlzb29fMTIz",
                "ds_address": "10.239.20.148",
                "ds_port": 3306,
                "ds_path": "kom",
                "extract_type": "standardExtraction",
                "ds_auth": "",
                "vhost": "",
                "queue": "",
                "json_schema": "",
                "knw_id": 1,
                "connect_type": ""
            }
        ]
    }
}
```

### 2.10、保存并退出接口

```
POST  /api/builder/v1/graph/save_no_check
```

请求参数：

| 序号 | 字段名称       | 字段类型  | 字段位置 | 是否必须 | 长度 | 字段说明     |
| :--- | :------------- | :-------- | -------- | :------- | ---- | :----------- |
| 1    | graph_id       | int       | body     | 是       |      | 图谱ID       |
| 2    | graph_baseInfo | object    | body     | 是       |      | 图谱基本信息 |
| 3    | graph_ds       | list<int> | body     | 是       |      | 数据源id     |
| 4    | graph_KMap     | object    | body     | 是       |      | 映射信息     |
| 5    | graph_otl      | object    | body     | 是       |      | 本体信息     |

请求示例：

```json
{
    "graph_id": 1,
    "graph_baseInfo": {
        "graph_des": "",
        "graph_name": "test"
    },
    "graph_ds": [1, 2],
    "graph_KMap": {
        "edge": [],
        "entity": [],
        "files": []
    },
    "graph_otl": {
        "edge": [],
        "entity": [],
        "id": 1,
        "ontology_des": "",
        "ontology_id": "1",
        "ontology_name": "",
        "used_task": [1, 2]
    }
}
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 字段说明 |
| :--- | :------- | :------- | :------- |
| 1    | res      | string   | 执行结果 |

响应示例：

```json
{
    "res": "Exit save graph 1"
}
```

### 2.11、根据图谱id返回数据源列表

```
GET  /api/builder/v1/graph/ds/list
```

请求参数：

| 序号 | 字段名称 | 字段类型 | 字段位置 | 是否必须 | 长度 | 字段说明                     |
| :--- | :------- | :------- | -------- | :------- | ---- | :--------------------------- |
| 1    | id       | int      | query    | 是       |      | 图谱id                       |
| 2    | type     | string   | query    | 是       | 8    | 流程标识【filter，unfilter】 |

请求示例：

```
/api/builder/v1/graph/ds/list?id=1&type=filter
```

响应参数：

| 序号 | 字段名称 | 字段类型     | 字段说明       |
| :--- | :------- | :----------- | :------------- |
| 1    | count    | int          | 数据源总个数   |
| 2    | df       | list<object> | 数据源具体信息 |

| 序号 | 字段名称     | 字段类型 | 字段说明   |
| ---- | :----------- | :------- | :--------- |
| 1    | create_time  | string   | 创建时间   |
| 2    | create_by    | string   | 创建用户   |
| 3    | data_type    | string   | 数据类型   |
| 4    | data_source  | string   | 数据源类型 |
| 5    | ds_address   | string   | 地址       |
| 6    | ds_password  | string   | 密码       |
| 7    | ds_path      | string   | 数据库路径 |
| 8    | ds_port      | int      | 端口       |
| 9    | ds_user      | string   | 用户名     |
| 10   | ds_name      | string   | 数据源名称 |
| 11   | extract_type | string   | 抽取类型   |
| 12   | id           | int      | 数据源id   |
| 13   | knw_id       | int      | 知识网络id |
| 14   | update_time  | string   | 修改时间   |
| 15   | update_by    | string   | 修改用户   |
| 16   | connect_type | string   | 连接方式   |

响应示例：

```json
{
    "res": {
        "count": 1,
        "df": [{
            "create_time": "2023-02-06 04:19:55",
            "create_by": "11c9a837-82e7-45c7-9533-00309a1dba5d",
            "data_type": "structured",
            "data_source": "mysql",                  
            "ds_address": "10.4.107.112",
            "ds_password": "ZWlzb28uY29tMTIz",
            "ds_path": "anydata",
            "ds_port": 3320,
            "ds_user": "root",
            "ds_name": "\u672c\u673amysql",
            "extract_type": "standardExtraction",
            "id": 1,
            "knw_id": 1,
            "update_time": "2023-02-06 04:19:55",
            "update_by": "11c9a837-82e7-45c7-9533-00309a1dba5d",
            "connect_type":"odbc"                   
        }]
    }
}
```

### 2.12、获取图谱下的数据源或本体

```
POST  /api/builder/v1/graph/query
```

请求参数：

| 序号 | 字段名称 | 字段类型  | 字段位置 | 是否必须 | 长度 | 字段说明             |
| :--- | :------- | :-------- | -------- | :------- | ---- | :------------------- |
| 1    | graph_id | list<int> | body     | 是       |      | 图谱id               |
| 2    | type     | int       | body     | 是       |      | 1：本体    2：数据源 |

请求示例：

```json
{
    "graph_id":[1,2],
    "type":1
}
```

响应参数：

| 序号 | 字段名称 | 字段类型  | 字段说明             |
| :--- | :------- | :-------- | :------------------- |
| 1    | res      | list<int> | 数据源或本体  id列表 |

响应示例：

```json
{
    "res": [
        2
    ]
}
```

### 2.13、根据图谱id查询图谱名称和描述

```
POST  /api/builder/v1/graph/info/simple
```

请求参数：

| 序号 | 字段名称 | 字段类型  | 字段位置 | 是否必须 | 长度 | 字段说明 |
| :--- | :------- | :-------- | -------- | :------- | ---- | :------- |
| 1    | graph_id | list<int> | body     | 是       |      | 图谱id   |

请求示例：

```json
{  
    "graph_id":[1,2]   
}
```

响应参数：

| 序号 | 字段名称   | 字段类型 | 字段说明 |
| :--- | :--------- | :------- | :------- |
| 1    | id         | int      | 图谱id   |
| 2    | graph_name | string   | 图谱名称 |
| 3    | graph_des  | string   | 图谱描述 |

响应示例：

```json
{
    "res": [
        {
            “id”: 2,
            "graph_name": "xxx",
            "graph_des": "xxxxx"
        },
        ...
    ]
}
```

### 2.14、批量删除图谱

```
POST  /api/builder/v1/graph/delete
```

请求参数：

| 序号 | 字段名称  | 字段类型  | 字段位置 | 是否必须 | 长度 | 字段说明 |
| :--- | :-------- | :-------- | -------- | :------- | ---- | :------- |
| 1    | knw_id    | int       | body     | 是       |      | 网络id   |
| 2    | graph_ids | list<int> | body     | 是       |      | 图谱id   |

请求示例：

```json
{
    "knw_id":1,   
    "graph_ids":[1,2]   
}
```

响应参数：

| 序号 | 字段名称 | 字段类型  | 字段说明   |
| :--- | :------- | :-------- | :--------- |
| 1    | state    | string    | 删除成功   |
| 2    | graph_id | list<int> | 图谱id列表 |

响应示例：

```json
{
    "res": "success",
    "graph_id": [1]

}
```

### 2.15、通过图谱id获取数据源接口

```
GET  /api/builder/v1/graph/ds/{graph_id}
```

请求参数：

| 序号 | 字段名称 | 字段类型 | 字段位置 | 是否必须 | 长度 | 字段说明                  |
| :--- | :------- | :------- | -------- | :------- | ---- | :------------------------ |
| 1    | graph_id | int      | path     | 是       |      | 图谱id                    |
| 2    | page     | int      | query    | 是       |      | 页号                      |
| 3    | size     | int      | query    | 是       |      | 每页个数                  |
| 4    | order    | string   | query    | 是       | 6    | 排序方式（ascend，deend） |

请求示例：

```
/api/builder/v1/graph/ds/1?page=1&size=1&order=descend
```

响应参数：

| 序号 | 字段名称 | 字段类型     | 字段说明       |
| :--- | :------- | :----------- | :------------- |
| 1    | count    | int          | 数据源总个数   |
| 2    | df       | list<object> | 数据源具体信息 |

| 序号 | 字段名称     | 字段类型 | 字段说明   |
| ---- | :----------- | :------- | :--------- |
| 1    | create_time  | string   | 创建时间   |
| 2    | create_by    | string   | 创建用户   |
| 3    | data_type    | string   | 数据类型   |
| 4    | data_source  | string   | 数据源类型 |
| 5    | ds_address   | string   | 地址       |
| 6    | ds_password  | string   | 密码       |
| 7    | ds_path      | string   | 数据库路径 |
| 8    | ds_port      | int      | 端口       |
| 9    | ds_user      | string   | 用户名     |
| 10   | ds_name      | string   | 数据源名称 |
| 11   | extract_type | string   | 抽取类型   |
| 12   | id           | int      | 数据源id   |
| 13   | knw_id       | int      | 知识网络id |
| 14   | update_time  | string   | 修改时间   |
| 15   | update_by    | string   | 修改用户   |
| 16   | connect_type | string   | 连接方式   |

响应示例：

```json
{
    "res": {
        "count": 1,
        "df": [{
            "create_time": "2023-02-06 04:19:55",
            "create_by": "11c9a837-82e7-45c7-9533-00309a1dba5d",
            "data_type": "structured",
            "data_source": "mysql",                  
            "ds_address": "10.4.107.112",
            "ds_password": "ZWlzb28uY29tMTIz",
            "ds_path": "anydata",
            "ds_port": 3320,
            "ds_user": "root",
            "ds_name": "\u672c\u673amysql",
            "extract_type": "standardExtraction",
            "id": 1,
            "knw_id": 1,
            "update_time": "2023-02-06 04:19:55",
            "update_by": "11c9a837-82e7-45c7-9533-00309a1dba5d",
            "connect_type":"odbc"                   
        }]
    }
}
```

### 2.16、图谱导出接口

```
POST  /api/builder/v1/graph/output
```

请求参数：

| 序号 | 字段名称 | 字段类型 | 字段位置 | 是否必须 | 长度 | 字段说明     |
| :--- | :------- | :------- | -------- | :------- | ---- | :----------- |
| 1    | id       | int      | body     | 是       |      | 导出的图谱id |

请求示例：

```json
{
	"id": 1
}
```

响应示例：

```json
xxx.json
```

### 2.17、图谱导入接口

注意：该接口为form-data传参

```
POST  /api/builder/v1/graph/input
```

请求参数：

| 序号 | 字段名称  | 字段类型 | 字段位置 | 是否必须 | 长度 | 字段说明                                                     |
| ---- | :-------- | :------- | :------- | :------- | ---- | :----------------------------------------------------------- |
| 1    | knw_id    | int      | body     | 是       |      | 知识网络id，上传内部调用时不需要传递本参数，前端调用时需要传递 |
| 2    | file      | file     | body     | 是       |      | 上传的数据文件（只能是单个文件）                             |
| 3    | ds_id_map | object   | body     | 否       |      | 新旧数据源ID映射                                             |
| 4    | rename    | string   | body     | 否       |      | 导入图谱重命名，不填或填空为原图谱名                         |
| 5    | graph_id  | int      | body     | 否       |      | 被覆盖的图谱id，若传该值，则忽略rename                       |

请求示例：

```
"knw_id":1,
"file":xxx.json,
"ds_id_map":{"24": 1,"25": 2},
"rename":"",
"graph_id":1
```

响应参数：

| 序号 | 字段名称 | 字段类型  | 是否必须 | 字段说明 |
| :--- | :------- | :-------- | :------- | :------- |
| 1    | graph_id | list<int> | 是       | 图谱id   |

响应示例：

```json
{
    "graph_id": [1]
}
```

### 2.19、获取图谱信息

```
GET  /api/builder/v1/graph/info/basic
```

请求参数：

| 序号 | 字段名称 | 字段类型     | 字段位置 | 是否必须 | 长度 | 字段说明         |
| :--- | :------- | :----------- | -------- | :------- | ---- | :--------------- |
| 1    | graph_id | int          | query    | 是       |      | 图谱id           |
| 2    | is_all   | bool         | query    | 否       |      | 是否返回所有字段 |
| 3    | key      | list<string> | query    | 否       |      | 需要获取的字段   |

请求示例：

```
/api/builder/v1/graph/info/basic?graph_id=1&is_all=true
```

响应参数：

| 序号 | 字段名称        | 字段类型 | 是否必须 | 字段说明               |
| :--- | :-------------- | :------- | :------- | :--------------------- |
| 1    | create_time     | string   | 是       | 创建时间               |
| 2    | ds              | string   | 是       | 数据源id               |
| 3    | error_result    | object   | 是       | 错误信息               |
| 4    | export          | boolean  | 是       | 是否可以导出           |
| 5    | graph_des       | string   | 是       | 图谱描述               |
| 6    | graphdb_address | string   | 是       | 图数据库地址           |
| 7    | graphdb_dbname  | string   | 是       | 图数据库DB名           |
| 8    | graphdb_type    | string   | 是       | 图数据库类型           |
| 9    | id              | int      | 是       | 图谱ID                 |
| 10   | is_import       | boolean  | 是       | 是否为导入的图谱       |
| 11   | kmap            | string   | 是       | 映射信息               |
| 12   | knowledge_type  | string   | 是       | 知识类型               |
| 13   | mongo_name      | string   | 是       | mongo名称              |
| 14   | name            | string   | 是       | 图谱名称               |
| 15   | otl             | string   | 是       | 本体id                 |
| 16   | status          | string   | 是       | 图谱状态               |
| 17   | step_num        | int      | 是       | 图谱配置流程到了第几步 |
| 18   | task_status     | string   | 是       | 任务运行状态           |
| 19   | update_time     | string   | 是       | 更新时间               |

响应示例：

```json
{
    "res": {
        "create_time": "2023-09-09 11:11:11",
        "ds": "[2, 3]",
        "error_result": {},
        "export": false,
        "graph_des": "",
        "graphdb_address": "10.1.1.1",
        "graph_dbname": "ub3a54sdf90932kafhioa23di-9",
        "graphdb_type": "nebulaGraph",
        "id": 1,
        "is_import": false,
        "kmap": "{}",
        "knowledge_type": "kg",
        "mongo_name": "mongoDB-5",
        "name": "test",
        "otl": "7", 
        "status": "normal", 
        "step_num": "4", 
        "task_status": "normal", 
        "update_time": "2023-09-09 11:11:11"
    }
}
```

### 2.20、获取本体信息接口

```
GET  /api/builder/v1/graph/info/onto
```

请求参数：

| 序号 | 字段名称           | 字段类型 | 字段位置 | 是否必须 | 长度 | 字段说明                    |
| :--- | :----------------- | :------- | -------- | :------- | ---- | :-------------------------- |
| 1    | graph_id           | int      | query    | 是       |      | 图谱id                      |
| 2    | compensation_cache | boolean  | query    | 否       |      | 是否补偿缓存，默认值为false |

请求示例：

```
/api/builder/v1/graph/info/onto?graph_id=1
```

响应参数：

| 序号 | 字段名称 | 字段类型     | 是否必须 | 字段说明     |
| ---- | :------- | :----------- | :------- | :----------- |
| 1    | db_name  | string       | 是       | 图数据库名称 |
| 2    | entity   | list<object> | 是       | 点的相关信息 |
| 3    | edge     | list<object> | 是       | 边的相关信息 |

| 序号 | 字段名称      | 字段类型 | 是否必须 | 字段说明                                                     |
| ---- | :------------ | :------- | :------- | :----------------------------------------------------------- |
| 1    | alias         | string   | 是       | 实体类别名                                                   |
| 2    | color         | string   | 是       | 实体类颜色（暂时保留该字段，图分析会调用该接口获取本体信息） |
| 3    | default_tag   | string   | 是       | 默认展示的属性                                               |
| 4    | entity_id     | int      | 是       | 实体类id                                                     |
| 5    | fill_color    | string   | 是       | 填充颜色                                                     |
| 6    | icon          | string   | 是       | 实体类图标                                                   |
| 7    | icon_color    | string   | 是       | 图标颜色                                                     |
| 8    | name          | string   | 是       | 实体类名                                                     |
| 9    | properties    | object   | 是       | 属性                                                         |
| 10   | shape         | string   | 是       | 实体类形状                                                   |
| 11   | size          | string   | 是       | 大小                                                         |
| 12   | stroke_color  | string   | 是       | 描边颜色                                                     |
| 13   | text_color    | string   | 是       | 文字颜色                                                     |
| 14   | text_position | string   | 是       | 文字位置                                                     |
| 15   | text_width    | int      | 是       | 文字宽度                                                     |
| 16   | x             | float    | 是       | 实体类坐标                                                   |
| 17   | y             | float    | 是       | 实体类坐标                                                   |

| 序号 | 字段名称   | 字段类型  | 是否必须 | 字段说明       |
| ---- | :--------- | :-------- | :------- | :------------- |
| 1    | alias      | string    | 是       | 关系类别名     |
| 2    | color      | string    | 是       | 关系类颜色     |
| 3    | edge_id    | int       | 是       | 关系类id       |
| 4    | name       | string    | 是       | 关系类名       |
| 5    | properties | object    | 是       | 属性           |
| 6    | relation   | list<int> | 是       | 点边之间的关系 |
| 7    | shape      | string    | 是       | 形状           |
| 8    | width      | string    | 是       | 宽             |

响应示例：

```json
{
    "res": {
        "db_name": "u7f7e1d70f0d411ee8e7f0242ac13000f-2",
        "edge": [
            {
                "alias": "1231_2_4",
                "color": "rgba(240,227,79,1)",
                "edge_id": 6,
                "name": "1231_2_4",
                "properties": [],
                "relation": [
                    "1231",
                    "1231_2_4",
                    "4"
                ],
                "shape": "line",
                "width": "0.25x"
            },
            ...
        ],
        "entity": [
            {
                "alias": "4",
                "color": "rgba(217,83,76,1)",
                "default_tag": "4",
                "entity_id": 5,
                "fill_color": "rgba(217,83,76,1)",
                "icon": "empty",
                "icon_color": "#ffffff",
                "name": "4",
                "properties": [],
                "shape": "circle",
                "size": "0.5x",
                "stroke_color": "rgba(217,83,76,1)",
                "text_color": "rgba(0,0,0,1)",
                "text_position": "top",
                "text_type": "adaptive",
                "text_width": 15,
                "x": 963,
                "y": 274.25
            },
            ...
        ]
    }
}
```

### 2.21、获取图谱的数量信息

```
GET  /api/builder/v1/graph/info/count
```

请求参数：

| 序号 | 字段名称 | 字段类型 | 字段位置 | 是否必须 | 长度 | 字段说明 |
| :--- | :------- | :------- | -------- | :------- | ---- | :------- |
| 1    | graph_id | int      | query    | 是       |      | 图谱id   |

请求示例：

```
/api/builder/v1/graph/info/count?graph_id=1
```

响应参数：

| 序号 | 字段名称     | 字段类型     | 是否必须 | 字段说明     |
| ---- | :----------- | :----------- | :------- | :----------- |
| 1    | edge         | list<object> | 是       | 边的相关信息 |
| 2    | edge_count   | int          | 是       | 边的总数     |
| 3    | entity       | list<object> | 是       | 点的相关信息 |
| 4    | entity_count | int          | 是       | 点的总数     |

| 序号 | 字段名称    | 字段类型 | 是否必须 | 字段说明                          |
| ---- | :---------- | :------- | :------- | :-------------------------------- |
| 1    | name        | string   | 是       | 实体类名/关系类名                 |
| 2    | count       | int      | 是       | 实体类的实体总数/关系类的关系总数 |
| 3    | prop_number | int      | 是       | 属性数量                          |

响应示例：

```json
{
    "res": {
        "edge": [
            {
                "count": 427,
                "name": "chapter2text"
                "prop_number":3,
            }
        ],
        "edge_count": 1986,
        "entity": [
            {
                "count": 31,
                "name": "chapter",
                "prop_number":4,
            }
        ],
        "entity_count": 836
    }
}
```

### 2.22、获取图谱中的点或边的配置详情

```
GET  /api/builder/v1/graph/info/detail
```

请求参数：

| 序号 | 字段名称 | 字段类型 | 字段位置 | 是否必须 | 长度 | 字段说明            |
| ---- | :------- | :------- | -------- | :------- | ---- | :------------------ |
| 1    | graph_id | int      | query    | 是       |      | 图谱id（kgconfid）  |
| 2    | type     | string   | query    | 是       |      | 点/边   entity/edge |
| 3    | name     | string   | query    | 是       |      | 点/边的名字         |

请求示例：

```
/api/builder/v1/graph/info/detail?graph_id=1&type=entity&name=xxx
```

响应参数：

| 序号 | 字段名称   | 字段类型     | 是否必须 | 字段说明 |
| ---- | :--------- | :----------- | :------- | :------- |
| 1    | indexes    | list<object> | 是       | 索引信息 |
| 2    | properties | list<object> | 是       | 属性信息 |

| 序号 | 字段名称   | 字段类型     | 是否必须 | 字段说明 |
| ---- | :--------- | :----------- | :------- | :------- |
| 1    | name       | string       | 是       | 索引名   |
| 2    | properties | list<object> | 是       | 索引属性 |
| 3    | type       | string       | 是       | 索引类型 |

| 序号 | 字段名称 | 字段类型 | 是否必须 | 字段说明 |
| ---- | :------- | :------- | :------- | :------- |
| 1    | alias    | string   | 是       | 属性别名 |
| 2    | name     | string   | 是       | 属性名   |
| 3    | type     | string   | 是       | 属性类型 |

响应示例：

```json
{
    "res": {
        "indexes": [
            {
                "name": "u4d1b761a01f811edb7079af371d61d07_industry_info",
                "properties": [
                	{
                		 "alias":"data",
                		 "name":"data"
                	}
                ],
                "type": "FULLTEXT"
            },
            {
                "name": "industry_info_industry_name",
                "properties": [
                	{
                		 "alias":"data",
                		 "name":"data"
                	}
                ],
                "type": "NEBULA_NATIVE_INDEX"
            }
        ],
        "properties": [
            {
                "alias":"data",
                "name":"data",
                "type": "string"
            }
        ]
    }
}
```

### 2.23、新增子图配置

```
POST  /api/builder/v1/graph/subgraph/add
```

请求参数：

| 序号 | 字段名称    | 字段类型     | 参数位置 | 是否必须 | 长度 | 字段说明                                  |
| ---- | :---------- | :----------- | :------- | :------- | ---- | :---------------------------------------- |
| 1    | name        | string       | body     | 是       | 100  | 子图配置名称，不能为“未分组”、“ungrouped” |
| 2    | entity      | list<object> | body     | 是       |      | 实体类信息                                |
| 3    | edge        | list<object> | body     | 是       |      | 边类信息                                  |
| 4    | ontology_id | int          | body     | 是       |      | 本体id                                    |
| 5    | graph_id    | int          | body     | 是       |      | 图谱id                                    |

请求示例：

```json
{
  "edge": [],
  "entity": [],
  "graph_id": 1,
  "name": "subgraph_name_2",
  "ontology_id": 1
}
```

响应参数：

| 序号 | 字段名称    | 字段类型 | 是否必须 | 字段说明 |
| ---- | :---------- | :------- | :------- | :------- |
| 1    | message     | string   | 是       | 创建成功 |
| 2    | subgraph_id | int      | 是       | 子图id   |

响应示例：

```json
{
    "res":{
        "message": "create subgraph 1 success.",
        "subgraph_id": 1
    } 
}
```

### 2.24、编辑子图配置

```
POST  /api/builder/v1/graph/subgraph/edit/{graph_id}
```

请求参数：

| 序号 | 字段名称    | 字段类型     | 参数位置 | 是否必须 | 长度 | 字段说明                                  |
| :--- | :---------- | :----------- | :------- | :------- | ---- | :---------------------------------------- |
| 1    | graph_id    | int          | path     | 是       |      | 图谱id                                    |
| 2    | subgraph_id | int          | body     | 是       |      | 子图配置id                                |
| 3    | name        | string       | body     | 是       | 100  | 子图配置名称，不能为“未分组”、“ungrouped” |
| 4    | entity      | list<object> | body     | 否       |      | 实体类信息                                |
| 5    | edge        | list<object> | body     | 否       |      | 边类信息                                  |

请求示例：

```json
/api/builder/v1/graph/subgraph/edit/1
[
    {
      "edge": [{'edge_id': 8, 'name': 'account_2_account_role', 'description': '', 'alias': '3框', 'synonym': '', 'properties_index': [], 'default_tag': '', 'properties': [], 'relations': ['account', 'account_2_account_role', 'account_role'], 'colour': 'rgba(227,150,64,1)', 'shape': 'line', 'width': '0.25x', 'source_type': 'manual', 'index_default_switch': False, 'index_main_switch': False, 'model': ''}, {'edge_id': 7, 'name': 'account_2_async_tasks', 'description': '', 'alias': '2框', 'synonym': '', 'properties_index': [], 'default_tag': '', 'properties': [], 'relations': ['account', 'account_2_async_tasks', 'async_tasks'], 'colour': 'rgba(227,150,64,1)', 'shape': 'line', 'width': '0.25x', 'source_type': 'manual', 'index_default_switch': False, 'index_main_switch': False, 'model': ''}],
      "entity": [{'entity_id': 4, 'name': 'async_tasks', 'description': '', 'alias': 'async_tasks', 'synonym': '', 'default_tag': 'id', 'properties_index': ['id'], 'primary_key': ['id'], 'vector_generation': [], 'properties': [{'name': 'id', 'description': '', 'alias': 'id', 'data_type': 'integer', 'synonym': ''}, {'name': 'task_type', 'description': '', 'alias': 'task_type', 'data_type': 'string', 'synonym': ''}, {'name': 'task_status', 'description': '', 'alias': 'task_status', 'data_type': 'string', 'synonym': ''}, {'name': 'task_name', 'description': '', 'alias': 'task_name', 'data_type': 'string', 'synonym': ''}, {'name': 'celery_task_id', 'description': '', 'alias': 'celery_task_id', 'data_type': 'string', 'synonym': ''}, {'name': 'relation_id', 'description': '', 'alias': 'relation_id', 'data_type': 'string', 'synonym': ''}, {'name': 'task_params', 'description': '', 'alias': 'task_params', 'data_type': 'string', 'synonym': ''}, {'name': 'result', 'description': '', 'alias': 'result', 'data_type': 'string', 'synonym': ''}, {'name': 'create_time', 'description': '', 'alias': 'create_time', 'data_type': 'datetime', 'synonym': ''}, {'name': 'update_time', 'description': '', 'alias': 'update_time', 'data_type': 'datetime', 'synonym': ''}], 'x': 706.3500516484272, 'y': 451.4230092967168, 'icon': '', 'shape': 'circle', 'size': '0.5x', 'fill_color': 'rgba(92,83,155,1)', 'stroke_color': 'rgba(92,83,155,1)', 'text_color': 'rgba(0,0,0,1)', 'text_position': 'top', 'text_width': 15, 'index_default_switch': False, 'index_main_switch': False, 'text_type': 'adaptive', 'source_type': 'automatic', 'model': '', 'task_id': '1', 'icon_color': '#ffffff'}, {'entity_id': 5, 'name': 'account_role', 'description': '', 'alias': 'account_role', 'synonym': '', 'default_tag': 'id', 'properties_index': ['id'], 'primary_key': ['id'], 'vector_generation': [], 'properties': [{'name': 'id', 'description': '', 'alias': 'id', 'data_type': 'integer', 'synonym': ''}, {'name': 'account_id', 'description': '', 'alias': 'account_id', 'data_type': 'string', 'synonym': ''}, {'name': 'role_id', 'description': '', 'alias': 'role_id', 'data_type': 'integer', 'synonym': ''}, {'name': 'created', 'description': '', 'alias': 'created', 'data_type': 'datetime', 'synonym': ''}, {'name': 'updated', 'description': '', 'alias': 'updated', 'data_type': 'datetime', 'synonym': ''}], 'x': 672.6638924541155, 'y': 696.1195006417407, 'icon': '', 'shape': 'circle', 'size': '0.5x', 'fill_color': 'rgba(216,112,122,1)', 'stroke_color': 'rgba(216,112,122,1)', 'text_color': 'rgba(0,0,0,1)', 'text_position': 'top', 'text_width': 15, 'index_default_switch': False, 'index_main_switch': False, 'text_type': 'adaptive', 'source_type': 'automatic', 'model': '', 'task_id': '1', 'icon_color': '#ffffff'}, {'entity_id': 6, 'name': 'account', 'description': '', 'alias': 'account', 'synonym': '', 'default_tag': 'id', 'properties_index': ['id'], 'primary_key': ['id'], 'vector_generation': [], 'properties': [{'name': 'id', 'description': '', 'alias': 'id', 'data_type': 'integer', 'synonym': ''}, {'name': 'username', 'description': '', 'alias': 'username', 'data_type': 'string', 'synonym': ''}, {'name': 'status', 'description': '', 'alias': 'status', 'data_type': 'integer', 'synonym': ''}, {'name': 'app_id', 'description': '', 'alias': 'app_id', 'data_type': 'string', 'synonym': ''}, {'name': 'account_id', 'description': '', 'alias': 'account_id', 'data_type': 'string', 'synonym': ''}, {'name': 'third_party_id', 'description': '', 'alias': 'third_party_id', 'data_type': 'string', 'synonym': ''}, {'name': 'source_type', 'description': '', 'alias': 'source_type', 'data_type': 'integer', 'synonym': ''}], 'x': 477.9860558974574, 'y': 594.4574900615426, 'icon': '', 'shape': 'circle', 'size': '0.5x', 'fill_color': 'rgba(227,150,64,1)', 'stroke_color': 'rgba(227,150,64,1)', 'text_color': 'rgba(0,0,0,1)', 'text_position': 'top', 'text_width': 15, 'index_default_switch': False, 'index_main_switch': False, 'text_type': 'adaptive', 'source_type': 'automatic', 'model': '', 'task_id': '1', 'icon_color': '#ffffff'}],
      "name": "subgraph_name_2",
      "subgraph_id": 1
    }
]
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 是否必须 | 字段说明 |
| ---- | :------- | :------- | :------- | :------- |
| 1    | res      | string   | 是       | 编辑成功 |

响应示例：

```json
{
    "res": {
        "res": "edit subgraph [45] success. "
    }
}
```

### 2.25、子图保存不校验接口

```
POST  /api/builder/v1/graph/subgraph/save_no_check/{graph_id}
```

请求参数：

| 序号 | 字段名称    | 字段类型     | 参数位置 | 是否必须 | 长度 | 字段说明                                  |
| :--- | :---------- | :----------- | :------- | :------- | ---- | :---------------------------------------- |
| 1    | graph_id    | int          | path     | 是       |      | 图谱id                                    |
| 2    | subgraph_id | int          | body     | 是       |      | 子图配置id                                |
| 3    | name        | string       | body     | 是       | 100  | 子图配置名称，不能为“未分组”、“ungrouped” |
| 4    | entity      | list<object> | body     | 否       |      | 实体类信息                                |
| 5    | edge        | list<object> | body     | 否       |      | 边类信息                                  |

请求示例：

```json
/api/builder/v1/graph/subgraph/save_no_check/1
[
    {
      "edge": [{'edge_id': 8, 'name': 'account_2_account_role', 'description': '', 'alias': '3框', 'synonym': '', 'properties_index': [], 'default_tag': '', 'properties': [], 'relations': ['account', 'account_2_account_role', 'account_role'], 'colour': 'rgba(227,150,64,1)', 'shape': 'line', 'width': '0.25x', 'source_type': 'manual', 'index_default_switch': False, 'index_main_switch': False, 'model': ''}, {'edge_id': 7, 'name': 'account_2_async_tasks', 'description': '', 'alias': '2框', 'synonym': '', 'properties_index': [], 'default_tag': '', 'properties': [], 'relations': ['account', 'account_2_async_tasks', 'async_tasks'], 'colour': 'rgba(227,150,64,1)', 'shape': 'line', 'width': '0.25x', 'source_type': 'manual', 'index_default_switch': False, 'index_main_switch': False, 'model': ''}],
      "entity": [{'entity_id': 4, 'name': 'async_tasks', 'description': '', 'alias': 'async_tasks', 'synonym': '', 'default_tag': 'id', 'properties_index': ['id'], 'primary_key': ['id'], 'vector_generation': [], 'properties': [{'name': 'id', 'description': '', 'alias': 'id', 'data_type': 'integer', 'synonym': ''}, {'name': 'task_type', 'description': '', 'alias': 'task_type', 'data_type': 'string', 'synonym': ''}, {'name': 'task_status', 'description': '', 'alias': 'task_status', 'data_type': 'string', 'synonym': ''}, {'name': 'task_name', 'description': '', 'alias': 'task_name', 'data_type': 'string', 'synonym': ''}, {'name': 'celery_task_id', 'description': '', 'alias': 'celery_task_id', 'data_type': 'string', 'synonym': ''}, {'name': 'relation_id', 'description': '', 'alias': 'relation_id', 'data_type': 'string', 'synonym': ''}, {'name': 'task_params', 'description': '', 'alias': 'task_params', 'data_type': 'string', 'synonym': ''}, {'name': 'result', 'description': '', 'alias': 'result', 'data_type': 'string', 'synonym': ''}, {'name': 'create_time', 'description': '', 'alias': 'create_time', 'data_type': 'datetime', 'synonym': ''}, {'name': 'update_time', 'description': '', 'alias': 'update_time', 'data_type': 'datetime', 'synonym': ''}], 'x': 706.3500516484272, 'y': 451.4230092967168, 'icon': '', 'shape': 'circle', 'size': '0.5x', 'fill_color': 'rgba(92,83,155,1)', 'stroke_color': 'rgba(92,83,155,1)', 'text_color': 'rgba(0,0,0,1)', 'text_position': 'top', 'text_width': 15, 'index_default_switch': False, 'index_main_switch': False, 'text_type': 'adaptive', 'source_type': 'automatic', 'model': '', 'task_id': '1', 'icon_color': '#ffffff'}, {'entity_id': 5, 'name': 'account_role', 'description': '', 'alias': 'account_role', 'synonym': '', 'default_tag': 'id', 'properties_index': ['id'], 'primary_key': ['id'], 'vector_generation': [], 'properties': [{'name': 'id', 'description': '', 'alias': 'id', 'data_type': 'integer', 'synonym': ''}, {'name': 'account_id', 'description': '', 'alias': 'account_id', 'data_type': 'string', 'synonym': ''}, {'name': 'role_id', 'description': '', 'alias': 'role_id', 'data_type': 'integer', 'synonym': ''}, {'name': 'created', 'description': '', 'alias': 'created', 'data_type': 'datetime', 'synonym': ''}, {'name': 'updated', 'description': '', 'alias': 'updated', 'data_type': 'datetime', 'synonym': ''}], 'x': 672.6638924541155, 'y': 696.1195006417407, 'icon': '', 'shape': 'circle', 'size': '0.5x', 'fill_color': 'rgba(216,112,122,1)', 'stroke_color': 'rgba(216,112,122,1)', 'text_color': 'rgba(0,0,0,1)', 'text_position': 'top', 'text_width': 15, 'index_default_switch': False, 'index_main_switch': False, 'text_type': 'adaptive', 'source_type': 'automatic', 'model': '', 'task_id': '1', 'icon_color': '#ffffff'}, {'entity_id': 6, 'name': 'account', 'description': '', 'alias': 'account', 'synonym': '', 'default_tag': 'id', 'properties_index': ['id'], 'primary_key': ['id'], 'vector_generation': [], 'properties': [{'name': 'id', 'description': '', 'alias': 'id', 'data_type': 'integer', 'synonym': ''}, {'name': 'username', 'description': '', 'alias': 'username', 'data_type': 'string', 'synonym': ''}, {'name': 'status', 'description': '', 'alias': 'status', 'data_type': 'integer', 'synonym': ''}, {'name': 'app_id', 'description': '', 'alias': 'app_id', 'data_type': 'string', 'synonym': ''}, {'name': 'account_id', 'description': '', 'alias': 'account_id', 'data_type': 'string', 'synonym': ''}, {'name': 'third_party_id', 'description': '', 'alias': 'third_party_id', 'data_type': 'string', 'synonym': ''}, {'name': 'source_type', 'description': '', 'alias': 'source_type', 'data_type': 'integer', 'synonym': ''}], 'x': 477.9860558974574, 'y': 594.4574900615426, 'icon': '', 'shape': 'circle', 'size': '0.5x', 'fill_color': 'rgba(227,150,64,1)', 'stroke_color': 'rgba(227,150,64,1)', 'text_color': 'rgba(0,0,0,1)', 'text_position': 'top', 'text_width': 15, 'index_default_switch': False, 'index_main_switch': False, 'text_type': 'adaptive', 'source_type': 'automatic', 'model': '', 'task_id': '1', 'icon_color': '#ffffff'}],
      "name": "subgraph_name_2",
      "subgraph_id": 1
    }
]
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 是否必须 | 字段说明 |
| ---- | :------- | :------- | :------- | :------- |
| 1    | res      | string   | 是       | 保存成功 |

响应示例：

```json
{
    "res": {
        "res": "save subgraph [1] success. "
    }
}
```

### 2.26、查询子图列表

```
GET  /api/builder/v1/graph/subgraph/list
```

请求参数：

| 序号 | 字段名称      | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明                                                     |
| ---- | :------------ | :------- | :------- | :------- | ---- | :----------------------------------------------------------- |
| 1    | graph_id      | int      | query    | 是       |      | 图谱id                                                       |
| 2    | subgraph_name | string   | query    | 是       | 50   | 搜索子图的关键字前端默认传空                                 |
| 3    | return_all    | boolean  | query    | 否       |      | False（默认）：仅返回id、name、实体类数量、边类数量的信息<br />True：额外返回实体类配置信息、边类配置信息 |

请求示例：

```
/api/builder/v1/graph/subgraph/list?graph_id=1&subgraph_name=&return_all=True
```

响应参数：

| 序号 | 字段名称   | 字段类型     | 是否必须 | 字段说明     |
| ---- | :--------- | :----------- | :------- | :----------- |
| 1    | edge       | list<object> | 是       | 边的相关信息 |
| 2    | edge_num   | int          | 是       | 边的总数     |
| 3    | entity     | list<object> | 是       | 点的相关信息 |
| 4    | entity_num | int          | 是       | 点的总数     |
| 5    | name       | string       | 是       | 子图名称     |
| 6    | id         | int          | 是       | 子图id       |

响应示例：

```json
{
    "res":[{
          "edge": [{'edge_id': 8, 'name': 'account_2_account_role', 'description': '', 'alias': '3框', 'synonym': '', 'properties_index': [], 'default_tag': '', 'properties': [], 'relations': ['account', 'account_2_account_role', 'account_role'], 'colour': 'rgba(227,150,64,1)', 'shape': 'line', 'width': '0.25x', 'source_type': 'manual', 'index_default_switch': False, 'index_main_switch': False, 'model': ''}, {'edge_id': 7, 'name': 'account_2_async_tasks', 'description': '', 'alias': '2框', 'synonym': '', 'properties_index': [], 'default_tag': '', 'properties': [], 'relations': ['account', 'account_2_async_tasks', 'async_tasks'], 'colour': 'rgba(227,150,64,1)', 'shape': 'line', 'width': '0.25x', 'source_type': 'manual', 'index_default_switch': False, 'index_main_switch': False, 'model': ''}],
          "entity": [{'entity_id': 4, 'name': 'async_tasks', 'description': '', 'alias': 'async_tasks', 'synonym': '', 'default_tag': 'id', 'properties_index': ['id'], 'primary_key': ['id'], 'vector_generation': [], 'properties': [{'name': 'id', 'description': '', 'alias': 'id', 'data_type': 'integer', 'synonym': ''}, {'name': 'task_type', 'description': '', 'alias': 'task_type', 'data_type': 'string', 'synonym': ''}, {'name': 'task_status', 'description': '', 'alias': 'task_status', 'data_type': 'string', 'synonym': ''}, {'name': 'task_name', 'description': '', 'alias': 'task_name', 'data_type': 'string', 'synonym': ''}, {'name': 'celery_task_id', 'description': '', 'alias': 'celery_task_id', 'data_type': 'string', 'synonym': ''}, {'name': 'relation_id', 'description': '', 'alias': 'relation_id', 'data_type': 'string', 'synonym': ''}, {'name': 'task_params', 'description': '', 'alias': 'task_params', 'data_type': 'string', 'synonym': ''}, {'name': 'result', 'description': '', 'alias': 'result', 'data_type': 'string', 'synonym': ''}, {'name': 'create_time', 'description': '', 'alias': 'create_time', 'data_type': 'datetime', 'synonym': ''}, {'name': 'finished_time', 'description': '', 'alias': 'finished_time', 'data_type': 'datetime', 'synonym': ''}], 'x': 706.3500516484272, 'y': 451.4230092967168, 'icon': '', 'shape': 'circle', 'size': '0.5x', 'fill_color': 'rgba(92,83,155,1)', 'stroke_color': 'rgba(92,83,155,1)', 'text_color': 'rgba(0,0,0,1)', 'text_position': 'top', 'text_width': 15, 'index_default_switch': False, 'index_main_switch': False, 'text_type': 'adaptive', 'source_type': 'automatic', 'model': '', 'task_id': '1', 'icon_color': '#ffffff'}, {'entity_id': 5, 'name': 'account_role', 'description': '', 'alias': 'account_role', 'synonym': '', 'default_tag': 'id', 'properties_index': ['id'], 'primary_key': ['id'], 'vector_generation': [], 'properties': [{'name': 'id', 'description': '', 'alias': 'id', 'data_type': 'integer', 'synonym': ''}, {'name': 'account_id', 'description': '', 'alias': 'account_id', 'data_type': 'string', 'synonym': ''}, {'name': 'role_id', 'description': '', 'alias': 'role_id', 'data_type': 'integer', 'synonym': ''}, {'name': 'created', 'description': '', 'alias': 'created', 'data_type': 'datetime', 'synonym': ''}, {'name': 'updated', 'description': '', 'alias': 'updated', 'data_type': 'datetime', 'synonym': ''}], 'x': 672.6638924541155, 'y': 696.1195006417407, 'icon': '', 'shape': 'circle', 'size': '0.5x', 'fill_color': 'rgba(216,112,122,1)', 'stroke_color': 'rgba(216,112,122,1)', 'text_color': 'rgba(0,0,0,1)', 'text_position': 'top', 'text_width': 15, 'index_default_switch': False, 'index_main_switch': False, 'text_type': 'adaptive', 'source_type': 'automatic', 'model': '', 'task_id': '1', 'icon_color': '#ffffff'}, {'entity_id': 6, 'name': 'account', 'description': '', 'alias': 'account', 'synonym': '', 'default_tag': 'id', 'properties_index': ['id'], 'primary_key': ['id'], 'vector_generation': [], 'properties': [{'name': 'id', 'description': '', 'alias': 'id', 'data_type': 'integer', 'synonym': ''}, {'name': 'username', 'description': '', 'alias': 'username', 'data_type': 'string', 'synonym': ''}, {'name': 'status', 'description': '', 'alias': 'status', 'data_type': 'integer', 'synonym': ''}, {'name': 'app_id', 'description': '', 'alias': 'app_id', 'data_type': 'string', 'synonym': ''}, {'name': 'account_id', 'description': '', 'alias': 'account_id', 'data_type': 'string', 'synonym': ''}, {'name': 'third_party_id', 'description': '', 'alias': 'third_party_id', 'data_type': 'string', 'synonym': ''}, {'name': 'source_type', 'description': '', 'alias': 'source_type', 'data_type': 'integer', 'synonym': ''}], 'x': 477.9860558974574, 'y': 594.4574900615426, 'icon': '', 'shape': 'circle', 'size': '0.5x', 'fill_color': 'rgba(227,150,64,1)', 'stroke_color': 'rgba(227,150,64,1)', 'text_color': 'rgba(0,0,0,1)', 'text_position': 'top', 'text_width': 15, 'index_default_switch': False, 'index_main_switch': False, 'text_type': 'adaptive', 'source_type': 'automatic', 'model': '', 'task_id': '1', 'icon_color': '#ffffff'}],
          "name": "subgraph_name_2",
          "edge_num": 1,
          "entity_num": 2,
          "id": 1
        }
    ]
}
```

### 2.27、根据子图ID获取子图配置

```
GET  /api/builder/v1/graph/subgraph/{subgraph_id}
```

请求参数：

| 序号 | 字段名称    | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明 |
| ---- | :---------- | :------- | :------- | :------- | ---- | :------- |
| 1    | subgraph_id | int      | path     | 是       |      | 子图id   |

请求示例：

```
/api/builder/v1/graph/subgraph/1
```

响应参数：

| 序号 | 字段名称   | 字段类型     | 是否必须 | 字段说明     |
| ---- | :--------- | :----------- | :------- | :----------- |
| 1    | edge       | list<object> | 是       | 边的相关信息 |
| 2    | edge_num   | int          | 是       | 边的总数     |
| 3    | entity     | list<object> | 是       | 点的相关信息 |
| 4    | entity_num | int          | 是       | 点的总数     |
| 5    | name       | string       | 是       | 子图名称     |
| 6    | id         | int          | 是       | 子图id       |

响应示例：

```json
{
    "res": {
          "edge": [],
          "entity": [{'entity_id': 4, 'name': 'async_tasks', 'description': '', 'alias': 'async_tasks', 'synonym': '', 'default_tag': 'id', 'properties_index': ['id'], 'primary_key': ['id'], 'vector_generation': [], 'properties': [{'name': 'id', 'description': '', 'alias': 'id', 'data_type': 'integer', 'synonym': ''}, {'name': 'task_type', 'description': '', 'alias': 'task_type', 'data_type': 'string', 'synonym': ''}, {'name': 'task_status', 'description': '', 'alias': 'task_status', 'data_type': 'string', 'synonym': ''}, {'name': 'task_name', 'description': '', 'alias': 'task_name', 'data_type': 'string', 'synonym': ''}, {'name': 'celery_task_id', 'description': '', 'alias': 'celery_task_id', 'data_type': 'string', 'synonym': ''}, {'name': 'relation_id', 'description': '', 'alias': 'relation_id', 'data_type': 'string', 'synonym': ''}, {'name': 'task_params', 'description': '', 'alias': 'task_params', 'data_type': 'string', 'synonym': ''}, {'name': 'result', 'description': '', 'alias': 'result', 'data_type': 'string', 'synonym': ''}, {'name': 'create_time', 'description': '', 'alias': 'create_time', 'data_type': 'datetime', 'synonym': ''}, {'name': 'update_time', 'description': '', 'alias': 'update_time', 'data_type': 'datetime', 'synonym': ''}], 'x': 706.3500516484272, 'y': 451.4230092967168, 'icon': '', 'shape': 'circle', 'size': '0.5x', 'fill_color': 'rgba(92,83,155,1)', 'stroke_color': 'rgba(92,83,155,1)', 'text_color': 'rgba(0,0,0,1)', 'text_position': 'top', 'text_width': 15, 'index_default_switch': False, 'index_main_switch': False, 'text_type': 'adaptive', 'source_type': 'automatic', 'model': '', 'task_id': '1', 'icon_color': '#ffffff'}, {'entity_id': 5, 'name': 'account_role', 'description': '', 'alias': 'account_role', 'synonym': '', 'default_tag': 'id', 'properties_index': ['id'], 'primary_key': ['id'], 'vector_generation': [], 'properties': [{'name': 'id', 'description': '', 'alias': 'id', 'data_type': 'integer', 'synonym': ''}, {'name': 'account_id', 'description': '', 'alias': 'account_id', 'data_type': 'string', 'synonym': ''}, {'name': 'role_id', 'description': '', 'alias': 'role_id', 'data_type': 'integer', 'synonym': ''}, {'name': 'created', 'description': '', 'alias': 'created', 'data_type': 'datetime', 'synonym': ''}, {'name': 'updated', 'description': '', 'alias': 'updated', 'data_type': 'datetime', 'synonym': ''}], 'x': 672.6638924541155, 'y': 696.1195006417407, 'icon': '', 'shape': 'circle', 'size': '0.5x', 'fill_color': 'rgba(216,112,122,1)', 'stroke_color': 'rgba(216,112,122,1)', 'text_color': 'rgba(0,0,0,1)', 'text_position': 'top', 'text_width': 15, 'index_default_switch': False, 'index_main_switch': False, 'text_type': 'adaptive', 'source_type': 'automatic', 'model': '', 'task_id': '1', 'icon_color': '#ffffff'}, {'entity_id': 6, 'name': 'account', 'description': '', 'alias': 'account', 'synonym': '', 'default_tag': 'id', 'properties_index': ['id'], 'primary_key': ['id'], 'vector_generation': [], 'properties': [{'name': 'id', 'description': '', 'alias': 'id', 'data_type': 'integer', 'synonym': ''}, {'name': 'username', 'description': '', 'alias': 'username', 'data_type': 'string', 'synonym': ''}, {'name': 'status', 'description': '', 'alias': 'status', 'data_type': 'integer', 'synonym': ''}, {'name': 'app_id', 'description': '', 'alias': 'app_id', 'data_type': 'string', 'synonym': ''}, {'name': 'account_id', 'description': '', 'alias': 'account_id', 'data_type': 'string', 'synonym': ''}, {'name': 'third_party_id', 'description': '', 'alias': 'third_party_id', 'data_type': 'string', 'synonym': ''}, {'name': 'source_type', 'description': '', 'alias': 'source_type', 'data_type': 'integer', 'synonym': ''}], 'x': 477.9860558974574, 'y': 594.4574900615426, 'icon': '', 'shape': 'circle', 'size': '0.5x', 'fill_color': 'rgba(227,150,64,1)', 'stroke_color': 'rgba(227,150,64,1)', 'text_color': 'rgba(0,0,0,1)', 'text_position': 'top', 'text_width': 15, 'index_default_switch': False, 'index_main_switch': False, 'text_type': 'adaptive', 'source_type': 'automatic', 'model': '', 'task_id': '1', 'icon_color': '#ffffff'}],
          "name": "subgraph_name_2",
          "edge_num": 0,
          "entity_num": 2,
          "id": 1
    }
}
```

### 2.28、批量删除子图配置接口

```
POST  /api/builder/v1/graph/subgraph/delete
```

请求参数：

| 序号 | 字段名称     | 字段类型  | 参数位置 | 是否必须 | 长度 | 字段说明   |
| ---- | :----------- | :-------- | :------- | :------- | ---- | :--------- |
| 1    | graph_id     | int       | body     | 是       |      | 图谱id     |
| 2    | subgraph_ids | list<int> | body     | 是       |      | 子图id列表 |

请求示例：

```json
{
    "graph_id": 1,
    "subgraph_ids": [41]
}
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 是否必须 | 字段说明 |
| ---- | :------- | :------- | :------- | :------- |
| 1    | res      | string   | 是       | 成功     |

响应示例：

```json
{
    "res": {
        "res": "delete subgraph [41] success"
    }
}
```

### 2.29、基于点批量删除关系

```
POST  /api/builder/v1/graph/data/batch_del_relation
```

请求参数：

| 序号 | 字段名称      | 字段类型     | 参数位置 | 是否必须 | 长度 | 字段说明                                                     |
| ---- | :------------ | :----------- | -------- | :------- | ---- | :----------------------------------------------------------- |
| 1    | graph_id      | int          | body     | 是       |      | 图谱id                                                       |
| 2    | vertex_name   | string       | body     | 是       |      | 需要批量删除关系的起始点或终点实体类名                       |
| 3    | relation_name | list<object> | body     | 是       |      | 需要批量删除的关系的关系类名，支持传多个                     |
| 4    | vertex_data   | object       | body     | 是       |      | 删除该关系起始点或者终点的融合属性值或者vid，vid使用参数_vid传递，例如：{"vid":123}代表使用vid删除，{"name":爱数}则代表使用融合属性删除 |

| 序号 | 字段名称  | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明                                                     |
| ---- | :-------- | :------- | -------- | :------- | ---- | :----------------------------------------------------------- |
| 1    | name      | string   | body     | 是       |      | 关系类名                                                     |
| 2    | direction | string   | body     | 是       |      | 方向（可选值：out: 删除出边    in: 删除进边    both: 删除出边和进边） |

请求示例：

```json
{
    "graph_id": 1,
    "vertex_name": "person",
    "relation_name": [
        {
            "name": "xxx",
            "direction": "both"
        }
    ],
    "vertex_data": {
        "name": "xxx"
    },
}
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 是否必须 | 字段说明 |
| ---- | :------- | :------- | :------- | :------- |
| 1    | res      | string   | 是       | 成功     |

响应示例：

```
{
    "res": "success"
}
```

### 2.30、编辑图谱

```
POST  /api/builder/v1/graph/edit/{graphid}
```

请求参数：

| 序号 | 字段名称      | 字段类型 | 字段位置 | 是否必须 | 长度 | 字段说明             |
| ---- | :------------ | :------- | :------- | :------- | ---- | :------------------- |
| 1    | graphid       | int      | path     | 是       |      | 图谱id               |
| 2    | graph_step    | string   | body     | 是       |      | 创建步骤             |
| 3    | knw_id        | int      | body     | 是       |      | 知识网络id           |
| 4    | graph_process | object   | body     | 是       |      | 流程中具体的配置信息 |

请求示例：

```json
{
    "graph_step": "graph_baseInfo",
    "knw_id": 1,
    "graph_process": {
        "graph_name": "图谱名称",
        "graph_des": ""
    }
}
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 字段说明 |
| :--- | :------- | :------- | :------- |
| 2    | res      | string   | 成功     |

响应示例：

```json
{
    "res": "update graph success"
}
```

### 2.31、提交重建索引任务

```
POST  /api/builder/v1/fulltext_index/{KDB_name}
```

请求参数：

| 序号 | 字段名称 | 字段类型 | 字段位置 | 是否必须 | 长度 | 字段说明           |
| ---- | :------- | :------- | :------- | :------- | ---- | :----------------- |
| 1    | KDB_name | string   | path     | 是       |      | 图数据库space name |

请求示例：

```
/api/builder/v1/fulltext_index/u34bb613cdbf411eca482ea21cd616bd0
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 字段说明 |
| :--- | :------- | :------- | :------- |
| 2    | res      | string   | 成功     |

响应示例：

```json
{
    "res": "rebuild fulltext task started."
}
```

### 2.32、查看重建索引任务状态

```
GET  /api/builder/v1/fulltext_index/{KDB_name}
```

请求参数：

| 序号 | 字段名称 | 字段类型 | 字段位置 | 是否必须 | 长度 | 字段说明           |
| ---- | :------- | :------- | :------- | :------- | ---- | :----------------- |
| 1    | KDB_name | string   | path     | 是       |      | 图数据库space name |

请求示例：

```
/api/builder/v1/fulltextindex/u34bb613cdbf411eca482ea21cd616bd0
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 字段说明 |
| :--- | :------- | :------- | :------- |
| 2    | res      | string   | 成功     |

响应示例：

```json
//重建索引任务已完成
{
    "res": "rebuild fulltext task finished."
}
//重建索引任务仍在运行
{
    "res": "rebuild fulltext task still running."
}
```

### 2.33、增加定时任务

```
POST  /api/builder/v1/timer/add/{graph_id}
```

请求参数：

| 序号 | 字段名称  | 字段类型  | 字段位置 | 是否必须 | 长度 | 字段说明                                                     |
| :--- | :-------- | :-------- | -------- | :------- | ---- | :----------------------------------------------------------- |
| 1    | graph_id  | int       | path     | 是       |      | 图谱id                                                       |
| 2    | task_type | string    | body     | 是       | 20   | 构建任务类型（full，increment）                              |
| 3    | cycle     | string    | body     | 是       | 20   | 有效值为one,day,week,month，one：执行一次，day：每天执行，week：每周执行，month：每月执行 |
| 4    | datetime  | string    | body     | 是       | 20   | 只执行一次的传递参数为具体日期如：'2021-12-20 15:54'，每天，每周，每月传递小时分钟形如：'16:40' |
| 5    | enabled   | int       | body     | 否       |      | 任务开关，开启：1，关闭：0，默认开启                         |
| 6    | date_list | list<int> | body     | 是       |      | 表示周几/几号执行，list内容为int，每周页面有效值为1~7，元素个数不能大于7，每月页面有效值为1~31如[1，4]，元素个数不能大于31，依次代表周一到周日或者1~31号，一次执行和每天执行页面传递空列表即可，传递其它值会直接丢弃掉 |

请求示例：

```json
/api/builder/v1/timer/add/1
{
    "task_type": "increment",
    "cycle":"month",
    "datetime":"17:20",
    "date_list":[1,2,3,4,5],
    "enabled":1
}
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 是否必须 | 字段说明 |
| :--- | :------- | :------- | :------- | :------- |
| 1    | state    | string   | 是       | 成功     |

返回样例：

```json
{
    "state": "success"
}
```

### 2.34、编辑定时任务

```
POST  /api/builder/v1/timer/edit/{graph_id}
```

请求参数：

| 序号 | 字段名称  | 字段类型  | 字段位置 | 是否必须 | 长度 | 字段说明                                                     |
| :--- | :-------- | :-------- | -------- | :------- | ---- | :----------------------------------------------------------- |
| 1    | graph_id  | int       | path     | 是       |      | 图谱id                                                       |
| 2    | task_id   | string    | body     | 是       | 255  | 定时任务id                                                   |
| 3    | task_type | string    | body     | 是       | 20   | 构建任务类型（full，increment）                              |
| 4    | cycle     | string    | body     | 是       | 20   | 有效值为one,day,week,month，one：执行一次，day：每天执行，week：每周执行，month：每月执行 |
| 5    | datetime  | string    | body     | 是       | 20   | 只执行一次的传递参数为具体日期如：'2021-12-20 15:54'，每天，每周，每月传递小时分钟形如：'16:40' |
| 6    | enabled   | int       | body     | 否       |      | 任务开关，开启：1，关闭：0，默认开启                         |
| 7    | date_list | list<int> | body     | 是       |      | 表示周几/几号执行，list内容为int，每周页面有效值为1~7，元素个数不能大于7，每月页面有效值为1~31如[1，4]，元素个数不能大于31，依次代表周一到周日或者1~31号，一次执行和每天执行页面传递空列表即可，传递其它值会直接丢弃掉 |

请求示例：

```json
/api/builder/v1/timer/update/1
{
    "task_type": "increment",
    "cycle":"week",
    "datetime":"17:02",
    "task_id":"edfeca62-77f8-11ec-9513-4281da722808",
    "enabled":1,
    "date_list":[1]
}
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 是否必须 | 字段说明 |
| :--- | :------- | :------- | :------- | :------- |
| 1    | state    | string   | 是       | 成功     |

返回样例：

```json
{
    "state": "success"
}
```

### 2.35、批量删除定时任务

```
POST  /api/builder/v1/timer/delete/{graph_id}
```

请求参数：

| 序号 | 字段名称 | 字段类型     | 字段位置 | 是否必须 | 长度 | 字段说明       |
| :--- | :------- | :----------- | -------- | :------- | ---- | :------------- |
| 1    | graph_id | int          | path     | 是       |      | 图谱id         |
| 2    | task_id  | list<string> | body     | 是       |      | 定时任务id列表 |

请求示例：

```json
/api/builder/v1/timer/delete/1
{
    "task_id":["xxx","4bfc6d8e-68ab-11ec-b9d3-005056ba834d"]
}
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 是否必须 | 字段说明 |
| :--- | :------- | :------- | :------- | :------- |
| 1    | state    | string   | 是       | 成功     |

返回样例：

```json
{
    "state": "success"
}
```

### 2.36、分页获取定时任务

```
GET  /api/builder/v1/timer/page
```

请求参数：

| 序号 | 字段名称 | 字段类型 | 字段位置 | 是否必须 | 长度 | 字段说明                                                     |
| :--- | :------- | :------- | -------- | :------- | ---- | :----------------------------------------------------------- |
| 1    | graph_id | int      | query    | 是       |      | 图谱id                                                       |
| 2    | page     | int      | query    | 是       |      | 第几页                                                       |
| 3    | size     | int      | query    | 是       |      | 每页显示数量                                                 |
| 4    | order    | string   | query    | 是       |      | 有效值为ascend和descend，ascend：按照更改时间升序（从旧到新）展示，descend：按照更改时间倒序（从新到旧）展示 |

请求示例：

```
/api/builder/v1/timer?graph_id=1&page=1&size=20&order=descend
```

响应参数：

| 序号 | 字段名称 | 字段类型     | 是否必须 | 字段说明     |
| :--- | :------- | :----------- | :------- | :----------- |
| 1    | count    | int          | 是       | 返回任务总数 |
| 2    | search   | list<object> | 是       | 返回当页数据 |

| 序号 | 字段名称    | 字段类型  | 是否必须 | 字段说明                                                     |
| :--- | :---------- | :-------- | :------- | :----------------------------------------------------------- |
| 1    | task_id     | string    | 是       | 定时任务id                                                   |
| 2    | task_type   | string    | 是       | 构建任务类型（full，increment）                              |
| 3    | cycle       | string    | 是       | 有效值为one,day,week,month，one：执行一次，day：每天执行，week：每周执行，month：每月执行 |
| 4    | datetime    | string    | 是       | 只执行一次的传递参数为具体日期如：'2021-12-20 15:54'，每天，每周，每月返回小时分钟形如：'16:40' |
| 5    | date_list   | list<int> | 是       | cycle值为week时表示周列表，cycle为month时表示几号的列表，执行一次和每天执行返回空列表 |
| 6    | enabled     | int       | 是       | 任务开关，开启：1，关闭：0                                   |
| 7    | update_by   | string    | 是       | 编辑者name                                                   |
| 8    | create_time | string    | 是       | 任务创建时间                                                 |
| 9    | update_time | string    | 是       | 任务编辑时间                                                 |

返回样例：

```json
{
  "count": 1,
  "search": [
    {
        "task_id": "2172ed06-5e2f-11ec-aedb-b07b2527ffc3",
        "cycle" : "week",
        "datetime": "16:40",
        "date_list": [1,2,7],
        "enabled": 1,
        "update_by": "admin",       
        "create_time": "2021-12-16 13:10:20",
        "update_time": "2021-12-16 13:10:20",
        "task_type":"full"
    }
  ]
}
```

### 2.37、获取定时任务详情

```
GET  /api/builder/v1/timer/info
```

请求参数：

| 序号 | 字段名称 | 字段类型 | 字段位置 | 是否必须 | 长度 | 字段说明   |
| :--- | :------- | :------- | -------- | :------- | ---- | :--------- |
| 1    | graph_id | int      | query    | 是       |      | 图谱id     |
| 2    | task_id  | string   | query    | 是       | 255  | 定时任务id |

请求示例：

```
/api/builder/v1/timer/info?graph_id=1&task_id=2172ed06-5e2f-11ec-aedb-b07b2527ffc3
```

响应参数：

| 序号 | 字段名称  | 字段类型  | 是否必须 | 字段说明                                                     |
| :--- | :-------- | :-------- | :------- | :----------------------------------------------------------- |
| 1    | task_id   | string    | 是       | 定时任务id                                                   |
| 2    | task_type | string    | 是       | 构建任务类型（full，increment）                              |
| 3    | cycle     | string    | 是       | 有效值为one,day,week,month，one：执行一次，day：每天执行，week：每周执行，month：每月执行 |
| 4    | datetime  | string    | 是       | 只执行一次的传递参数为具体日期如：'2021-12-20 15:54'，每天，每周，每月返回小时分钟形如：'16:40' |
| 5    | date_list | list<int> | 是       | cycle值为week时表示周列表，cycle为month时表示几号的列表，执行一次和每天执行返回空列表 |
| 6    | enabled   | int       | 是       | 任务开关，开启：1，关闭：0                                   |

返回样例：

```json
{        
      "task_id": "2172ed06-5e2f-11ec-aedb-b07b2527ffc3",
      "task_type": "full",
      "cycle": "day",
      "datetime": "2021-12-20 15:54",
      "date_list": [],      
      "enabled": 1
 }
```

### 2.38、定时任务开关

```
POST  /api/builder/v1/timer/switch/{graph_id}
```

请求参数：

| 序号 | 字段名称 | 字段类型 | 字段位置 | 是否必须 | 长度 | 字段说明                   |
| :--- | :------- | :------- | -------- | :------- | ---- | :------------------------- |
| 1    | graph_id | int      | path     | 是       |      | 图谱id                     |
| 2    | task_id  | string   | body     | 是       | 255  | 定时任务id                 |
| 3    | enabled  | int      | body     | 是       |      | 任务开关，开启：1，关闭：0 |

请求示例：

```json
/api/builder/v1/timer/switch/1
{
    "task_id":"ce29686e-7352-11ec-8b53-005056ba834d",
    "enabled":1
}
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 是否必须 | 字段说明 |
| :--- | :------- | :------- | :------- | :------- |
| 1    | state    | string   | 是       | 成功     |

返回样例：

```json
{
    "state": "success"
}
```

### 2.39、新增画布

```
POST  /api/graph/v1/canvases/add
```

请求参数：

| 序号 | 字段名称    | 字段类型 | 字段位置 | 是否必须 | 长度 | 字段说明                    |
| :--- | :---------- | :------- | -------- | :------- | ---- | :-------------------------- |
| 1    | knw_id      | int      | body     | 是       |      | 所属知识网络id              |
| 2    | kg_id       | int      | body     | 是       |      | 知识图谱id                  |
| 3    | canvas_name | string   | body     | 是       | 50   | 画布名                      |
| 4    | canvas_info | string   | body     | 否       | 255  | 画布描述                    |
| 5    | canvas_body | string   | body     | 是       |      | 画布内容，长度上限2^32 字符 |

请求示例：

```json
{
    "knw_id":1,
    "kg_id":1,
    "canvas_name":"xxx",
    "canvas_info":"xxx",
    "canvas_body":"xxx",
}
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 是否必须 | 字段说明 |
| :--- | :------- | :------- | :------- | :------- |
| 1    | res      | int      | 是       | 画布id   |

返回样例：

```json
{
    "res": 21
}
```

### 2.40、更新画布

```
POST  /api/graph/v1/canvases/update/{c_id}
```

请求参数：

只修改请求体传入的内容

| 序号 | 字段名称    | 字段类型 | 字段位置 | 是否必须 | 长度 | 字段说明                    |
| :--- | :---------- | :------- | -------- | :------- | ---- | :-------------------------- |
| 1    | c_id        | int      | path     | 是       |      | 画布id                      |
| 2    | knw_id      | int      | body     | 否       |      | 所属知识网络id              |
| 3    | kg_id       | int      | body     | 否       |      | 知识图谱id                  |
| 4    | canvas_name | string   | body     | 否       | 50   | 画布名                      |
| 5    | canvas_info | string   | body     | 否       | 255  | 画布描述                    |
| 6    | canvas_body | string   | body     | 否       |      | 画布内容，长度上限2^32 字符 |

请求示例：

```json
/api/graph/v1/canvases/update/1
{
    "knw_id":1,
    "kg_id":1,
    "canvas_name":"xxx",
    "canvas_info":"xxx",
    "canvas_body":"xxx",
}
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 是否必须 | 字段说明                          |
| :--- | :------- | :------- | :------- | :-------------------------------- |
| 1    | res      | int      | 是       | 被修改的画布id，没有找到画布返回0 |

返回样例：

```json
{
    "res": 1
}
```

### 2.41、删除画布

```
POST  /api/graph/v1/canvases/delete/{c_id}
```

请求参数：

| 序号 | 字段名称 | 字段类型 | 字段位置 | 是否必须 | 长度 | 字段说明 |
| :--- | :------- | :------- | -------- | :------- | ---- | :------- |
| 1    | c_id     | int      | path     | 是       |      | 画布id   |

请求示例：

```
/api/graph/v1/canvases/delete/1
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 是否必须 | 字段说明                        |
| :--- | :------- | :------- | :------- | :------------------------------ |
| 1    | res      | int      | 是       | 被删除的画布id，没找到画布返回0 |

返回样例：

```json
{
    "res": 1
}
```

### 2.42、批量删除画布

```
POST  /api/graph/v1/canvases/delete
```

请求参数：

| 序号 | 字段名称 | 字段类型  | 字段位置 | 是否必须 | 长度 | 字段说明   |
| :--- | :------- | :-------- | -------- | :------- | ---- | :--------- |
| 1    | c_ids    | list<int> | body     | 是       |      | 画布id列表 |

请求示例：

```json
{
    "c_ids":[1,2,3]
}
```

响应参数：

| 序号 | 字段名称 | 字段类型  | 是否必须 | 字段说明                                             |
| :--- | :------- | :-------- | :------- | :--------------------------------------------------- |
| 1    | res      | list<int> | 是       | 被删除的画布id列表，没找到画布或者传的参数为空返回[] |

返回样例：

```json
{
    "res": [1,2]
}
```

### 2.43、获取画布列表

```
GET  /api/graph/v1/canvases/knws/{knw_id}
```

请求参数：

| 序号 | 字段名称    | 字段类型 | 字段位置 | 是否必须 | 长度 | 字段说明                     |
| :--- | :---------- | :------- | -------- | :------- | ---- | :--------------------------- |
| 1    | knw_id      | int      | path     | 是       |      | 知识网络id                   |
| 2    | kg_id       | int      | query    | 是       |      | 图谱id                       |
| 3    | query       | string   | query    | 否       |      | 搜索关键字                   |
| 4    | order_field | string   | query    | 否       |      | 排序字段，默认update_time    |
| 5    | order_type  | string   | query    | 否       |      | 排序方式，asc/desc，默认desc |
| 6    | page        | int      | query    | 否       |      | 页数，默认1                  |
| 7    | size        | int      | query    | 否       |      | 每页数量，默认20             |

请求示例：

```
/api/graph/v1/canvases/knws/1?kg_id=2&query=&order_field=update_time&order_type=asc&page=1&size=10
```

响应参数：

| 序号 | 字段名称 | 字段类型     | 是否必须 | 字段说明     |
| :--- | :------- | :----------- | :------- | :----------- |
| 1    | count    | int          | 是       | 结果总数量   |
| 2    | canvases | list<object> | 是       | 画布结果列表 |

| 序号 | 字段名称    | 字段类型 | 是否必须 | 字段说明                                                     |
| :--- | :---------- | :------- | :------- | :----------------------------------------------------------- |
| 1    | c_id        | int      | 是       | 画布id                                                       |
| 2    | knw_id      | int      | 是       | 所属知识网络                                                 |
| 3    | kg          | object   | 是       | 知识图谱信息，包括id和图谱名，图谱被删除则id为0，图谱名为“--” |
| 4    | canvas_name | string   | 是       | 画布名                                                       |
| 5    | canvas_info | string   | 是       | 画布描述                                                     |
| 7    | create_time | string   | 是       | 创建时间                                                     |
| 9    | update_time | string   | 是       | 最后修改时间                                                 |

返回样例：

```json
{
    "res": {
        "count": 8,
        "canvases": [
            {
                "c_id": 12,
                "knw_id": 1,
                "canvas_name": "xxxxxxxx",
                "canvas_info": "画布描述画布描述画布描述",
                "kg": {
                    "kg_id": 1,
                    "name": "产业图谱"
                },
                "create_time": "2023-01-04 17:27:06",
                "update_time": "2023-01-04 17:27:06",
                "canvas_body": "--"
            },
            {
                "c_id": 11,
                "knw_id": 1,
                "canvas_name": "xxxx",
                "canvas_info": "画布描述画布描述画布描述",
                "kg": {
                    "kg_id": 1,
                    "name": "工艺图谱"
                },
                "create_time": "2023-01-04 17:13:19",
                "update_time": "2023-01-04 17:13:19",
                "canvas_body": "--"
            }
        ]
    }
}
```

### 2.44、获取指定画布的信息

```
GET  /api/graph/v1/canvases/{c_id}
```

请求参数：

| 序号 | 字段名称 | 字段类型 | 字段位置 | 是否必须 | 长度 | 字段说明 |
| :--- | :------- | :------- | -------- | :------- | ---- | :------- |
| 1    | c_id     | int      | path     | 是       |      | 画布id   |

请求示例：

```
/api/graph/v1/canvases/1
```

响应参数：

| 序号 | 字段名称    | 字段类型 | 是否必须 | 字段说明                                                     |
| :--- | :---------- | :------- | :------- | :----------------------------------------------------------- |
| 1    | c_id        | int      | 是       | 画布id                                                       |
| 2    | knw_id      | int      | 是       | 所属知识网络                                                 |
| 3    | kg          | object   | 是       | 知识图谱信息，包括id和图谱名，图谱被删除时id为0，图谱名为"--" |
| 4    | canvas_name | string   | 是       | 画布名                                                       |
| 5    | canvas_info | string   | 是       | 画布描述                                                     |
| 7    | create_time | string   | 是       | 创建时间                                                     |
| 9    | update_time | string   | 是       | 最后修改时间                                                 |
| 10   | canvas_body | string   | 是       | 画布内容                                                     |

返回样例：

```json
{
    "res": {
        "c_id": 3,
        "knw_id": 1,
        "canvas_name": "name",
        "canvas_info": "info",
        "kg": {
            "kg_id": 0,
            "name": "--"
        },
        "create_time": "2022-12-21 11:20:46",
        "update_time": "2022-12-21 11:21:30",
        "canvas_body": "body"
    }
}
```

### 2.45、全文检索

```
POST  /api/graph/v1/basic-search/kgs/{kg_id}/full-text
```

请求参数：

| 序号 | 字段名称      | 字段类型 | 字段位置 | 是否必须 | 长度 | 字段说明                                              |
| :--- | :------------ | :------- | -------- | :------- | ---- | :---------------------------------------------------- |
| 1    | kg_id         | int      | path     | 是       |      | 图谱id                                                |
| 2    | matching_num  | int      | body     | 是       |      | 匹配数量，默认500                                     |
| 3    | matching_rule | string   | body     | 是       |      | 匹配规则（completeness：完全匹配，portion：部分匹配） |
| 4    | page          | int      | body     | 是       |      | 分页                                                  |
| 5    | size          | int      | body     | 是       |      | 每页数量，size=0取全部                                |
| 6    | query         | string   | body     | 是       |      | 查询关键词                                            |
| 7    | search_config | object   | body     | 否       |      | 筛选条件                                              |

请求示例：

```json
/api/graph/v1/basic-search/kgs/1/full-text
{
    "matching_num":1,
    "matching_rule":"completeness",
    "page":1,
    "size":10,
    "query":"",
    "search_config":{}
}
```

响应参数：

| 序号 | 字段名称 | 字段类型     | 字段说明 |
| :--- | :------- | :----------- | :------- |
| 1    | nodes    | list<object> | 点集合   |

| 序号 | 字段名称         | 字段类型     | 字段说明     |
| :--- | :--------------- | :----------- | :----------- |
| 1    | id               | string       | 唯一标识id   |
| 2    | alias            | string       | 显示名       |
| 3    | color            | string       | 点颜色       |
| 4    | class_name       | string       | 点类型       |
| 5    | icon             | string       | 点图标       |
| 6    | default_property | object       | 默认显示属性 |
| 7    | tags             | list<string> | 所属tag列表  |
| 8    | properties       | object       | 属性列表     |

| 序号 | 字段名称 | 字段类型 | 字段说明   |
| :--- | :------- | :------- | :--------- |
| 1    | alias    | string   | 属性显示名 |
| 2    | name     | string   | 属性名     |
| 3    | value    | string   | 属性值     |

| 序号 | 字段名称 | 字段类型     | 字段说明            |
| :--- | :------- | :----------- | :------------------ |
| 1    | tag      | string       | tag类型名           |
| 2    | props    | list<object> | 具体tag下的属性列表 |

| 序号 | 字段名称 | 字段类型 | 字段说明           |
| :--- | :------- | :------- | :----------------- |
| 1    | alias    | string   | 属性显示名         |
| 2    | name     | string   | 属性名             |
| 3    | value    | string   | 属性值             |
| 4    | type     | string   | 属性类型           |
| 5    | disabled | boolean  | 是否显示           |
| 6    | checked  | boolean  | 是否为默认展示属性 |

返回样例：

```json
{
    "res": {
        "nodes": [
            {
                "id": "26d012de31025f24c210f4b10b00b8c2",
                "alias": "a",
                "color": "rgba(234,198,0,1)",
                "class_name": "a",
                "icon": "empty",
                "default_property": {
                    "alias": "b",
                    "name": "b",
                    "value": ""
                },
                "tags": [
                    "a"
                ],
                "properties": [
                    {
                        "tag": "a",
                        "props": [
                            {
                                "alias": "a",
                                "name": "a",
                                "value": "修改",
                                "type": "string",
                                "disabled": false,
                                "checked": false
                            },
                            {
                                "alias": "b",
                                "name": "b",
                                "value": "__NULL__",
                                "type": "string",
                                "disabled": false,
                                "checked": false
                            }
                        ]
                    }
                ]
            }
        ]
    }
}
```

### 2.46、vid搜索

```
POST  /api/graph/v1/basic-search/kgs/{kg_id}/vid
```

请求参数：

| 序号 | 字段名称      | 字段类型     | 字段位置 | 是否必须 | 长度 | 字段说明               |
| :--- | :------------ | :----------- | -------- | :------- | ---- | :--------------------- |
| 1    | kg_id         | int          | path     | 是       |      | 图谱id                 |
| 2    | page          | int          | body     | 是       |      | 分页                   |
| 3    | size          | int          | body     | 是       |      | 每页数量，size=0取全部 |
| 4    | vids          | list<string> | body     | 是       |      | 实体id列表             |
| 5    | search_config | object       | body     | 否       |      | 筛选条件               |

请求示例：

```json
/api/graph/v1/basic-search/kgs/1/vid
{
    "page":1,
    "size":10,
    "vids":["xxx"],
    "search_config":{}
}
```

响应参数：

| 序号 | 字段名称 | 字段类型     | 字段说明 |
| :--- | :------- | :----------- | :------- |
| 1    | nodes    | list<object> | 点集合   |

| 序号 | 字段名称         | 字段类型     | 字段说明     |
| :--- | :--------------- | :----------- | :----------- |
| 1    | id               | string       | 唯一标识id   |
| 2    | alias            | string       | 显示名       |
| 3    | color            | string       | 点颜色       |
| 4    | class_name       | string       | 点类型       |
| 5    | icon             | string       | 点图标       |
| 6    | default_property | object       | 默认显示属性 |
| 7    | tags             | list<string> | 所属tag列表  |
| 8    | properties       | object       | 属性列表     |

| 序号 | 字段名称 | 字段类型 | 字段说明   |
| :--- | :------- | :------- | :--------- |
| 1    | alias    | string   | 属性显示名 |
| 2    | name     | string   | 属性名     |
| 3    | value    | string   | 属性值     |

| 序号 | 字段名称 | 字段类型     | 字段说明            |
| :--- | :------- | :----------- | :------------------ |
| 1    | tag      | string       | tag类型名           |
| 2    | props    | list<object> | 具体tag下的属性列表 |

| 序号 | 字段名称 | 字段类型 | 字段说明           |
| :--- | :------- | :------- | :----------------- |
| 1    | alias    | string   | 属性显示名         |
| 2    | name     | string   | 属性名             |
| 3    | value    | string   | 属性值             |
| 4    | type     | string   | 属性类型           |
| 5    | disabled | boolean  | 是否显示           |
| 6    | checked  | boolean  | 是否为默认展示属性 |

返回样例：

```json
{
    "res": {
        "nodes": [
            {
                "id": "26d012de31025f24c210f4b10b00b8c2",
                "alias": "a",
                "color": "rgba(234,198,0,1)",
                "class_name": "a",
                "icon": "empty",
                "default_property": {
                    "alias": "b",
                    "name": "b",
                    "value": ""
                },
                "tags": [
                    "a"
                ],
                "properties": [
                    {
                        "tag": "a",
                        "props": [
                            {
                                "alias": "a",
                                "name": "a",
                                "value": "修改",
                                "type": "string",
                                "disabled": false,
                                "checked": false
                            },
                            {
                                "alias": "b",
                                "name": "b",
                                "value": "__NULL__",
                                "type": "string",
                                "disabled": false,
                                "checked": false
                            }
                        ]
                    }
                ]
            }
        ]
    }
}
```

### 2.47、搜索边

```
POST  /api/graph/v1/basic-search/kgs/{kg_id}/edges
```

请求参数：

| 序号 | 字段名称 | 字段类型     | 字段位置 | 是否必须 | 长度 | 字段说明                                         |
| :--- | :------- | :----------- | -------- | :------- | ---- | :----------------------------------------------- |
| 1    | kg_id    | int          | path     | 是       |      | 图谱id                                           |
| 2    | edges    | list<object> | body     | 否       |      | 标准的查边的方法                                 |
| 3    | eids     | list<string> | body     | 否       |      | eid列表，eid是边的信息进行组合得到的边的唯一标识 |

| 序号 | 字段名称 | 字段类型 | 字段位置 | 是否必须 | 长度 | 字段说明 |
| :--- | :------- | :------- | -------- | :------- | ---- | :------- |
| 1    | src_id   | int      | body     | 是       |      | 起点id   |
| 2    | dst_id   | int      | body     | 是       |      | 终点id   |
| 3    | type     | string   | body     | 是       |      | 边类型   |

请求示例：

```json
/api/graph/v1/basic-search/kgs/1/edges
{
    "eids":[
        "xxxx",
        "xxxxx",
	],
    "edges":[
        {
            "src_id":"123",
            "dst_id":"456,
            "type":"abc"       
        },
        {
            "src_id":"qqq",
            "dst_id":"www,
            "type":"abc"       
        }
	]
}
```

响应参数：

| 序号 | 字段名称    | 字段类型     | 字段说明     |
| :--- | :---------- | :----------- | :----------- |
| 1    | edges       | list<object> | 关系结果列表 |
| 2    | edges_count | int          | 关系结果数量 |

| 序号 | 字段名称   | 字段类型     | 字段说明 |
| :--- | :--------- | :----------- | :------- |
| 1    | id         | string       | 唯一标识 |
| 2    | alias      | string       | 显示名   |
| 3    | color      | string       | 颜色     |
| 4    | class_name | string       | 实体类型 |
| 5    | source     | string       | 起点id   |
| 6    | target     | string       | 终点id   |
| 7    | properties | list<object> | 属性列表 |

| 序号 | 字段名称 | 字段类型 | 字段说明           |
| :--- | :------- | :------- | :----------------- |
| 1    | alias    | string   | 属性显示名         |
| 2    | name     | string   | 属性名             |
| 3    | value    | string   | 属性值             |
| 4    | type     | string   | 属性类型           |
| 5    | disabled | boolean  | 是否显示           |
| 6    | checked  | boolean  | 是否为默认展示属性 |

返回样例：

```json
{
    "res": {
        "edges_count": 1,
        "edges": [
            {
                "id": "product:\"23a6ab0789d88caa0123e77088a8bc36\"->\"5033c4a8d9f4b3810a78081903d615e2\"",
                "alias": "产出",
                "color": "#68798E",
                "class_name": "product",
                "source": "23a6ab0789d88caa0123e77088a8bc36",
                "target": "5033c4a8d9f4b3810a78081903d615e2",
                "properties": [
                    {
                        "alias": "production",
                        "name": "production",
                        "value": "__NULL__",
                        "type": "null",
                        "disabled": false,
                        "checked": false
                    },
                    {
                        "alias": "name",
                        "name": "name",
                        "value": "1",
                        "type": "string",
                        "disabled": false,
                        "checked": false
                    }
                ]
            } 
        ]
    }
}
```

### 2.48、自定义查询

```
POST  /api/graph/v1/custom-search/kgs/{kg_id}
```

请求参数：

| 序号 | 字段名称   | 字段类型     | 字段位置 | 是否必须 | 长度 | 字段说明 |
| :--- | :--------- | :----------- | -------- | :------- | ---- | :------- |
| 1    | kg_id      | int          | path     | 是       |      | 图谱id   |
| 2    | statements | list<string> | body     | 是       |      | 查询语句 |

请求示例：

```json
/api/graph/v1/custom-search/kgs/1
{
    "statement":["xxx"]
}
```

响应参数：

| 序号 | 字段名称     | 字段类型     | 字段说明                 |
| :--- | :----------- | :----------- | :----------------------- |
| 1    | edges        | list<object> | 边集合                   |
| 2    | error        | object       | 错误信息                 |
| 3    | nodes        | list<object> | 点集合                   |
| 4    | nodes_detail | object       | 对于边或者路径中点的补充 |
| 5    | paths        | object       | 路径集合                 |
| 6    | statement    | string       | 查询语句                 |
| 7    | texts        | list<object> | 文本解析列表             |

返回样例：

```json
{
    "res": [
        {
            "nodes": [
                {
                    "id": "fdd9ecbe5d6bd712ad6fa13949788cbe",
                    "alias": "企业",
                    "color": "#5889C4",
                    "class_name": "enterprise",
                    "icon": "",
                    "default_property": {
                        "name": "name",
                        "value": "xx",
                        "alias": "企业名称"
                    },
                    "tags": [
                        "enterprise"
                    ],
                    "properties": [
                        {
                            "tag": "enterprise",
                            "props": [
                                {
                                    "name": "enterprise_nature",
                                    "value": "p01,p07",
                                    "alias": "xx",
                                    "type": "string",
                                    "disabled": false,
                                    "checked": false
                                }
                            ]
                        }
                    ]
                }
            ],
            "edges": [
                {
                    "id": "enterprise_2_zone:fdd9ecbe5d6bd712ad6fa13949788cbe-49689ca0f48bfddc3e2877ad2d177360",
                    "alias": "xx",
                    "color": "#5889C4",
                    "class_name": "enterprise_2_zone",
                    "source": "fdd9ecbe5d6bd712ad6fa13949788cbe",
                    "target": "49689ca0f48bfddc3e2877ad2d177360",
                    "properties": []
                }
            ],
            "paths": [
                {
                    "nodes": [
                        {
                            "id": "fdd9ecbe5d6bd712ad6fa13949788cbe"
                        }
                    ]
                }
            ],
            "statement": "match p=()-[e:enterprise_2_zone]->() return p limit 2",
            "error": {
                "ErrorCode": "EngineServer.EngineCoreErr",
                "Description": "EngineCoreErr调用失败",
                "Solution": "请检查详细信息，联系开发人员",
                "ErrorDetails": [
                    {
                        "detail": "SyntaxError: syntax error near `lmit'"
                    }
                ]
            },
            "nodes_detail":{}
        }
    ]
}
```

### 2.49、两点间路径探索

```
POST  /api/graph/v1/graph-explore/kgs/{kg_id}/paths
```

请求参数：

| 序号 | 字段名称      | 字段类型     | 字段位置 | 是否必须 | 长度 | 字段说明                                                     |
| :--- | :------------ | :----------- | -------- | :------- | ---- | :----------------------------------------------------------- |
| 1    | kg_id         | int          | path     | 是       |      | 图谱id                                                       |
| 2    | default_value | string       | body     | 否       |      | 属性默认值                                                   |
| 3    | direction     | string       | body     | 是       |      | 路径方向，单选positive（正向）, reverse（反向）, bidirect（双向） |
| 4    | edges         | string       | body     | 否       |      | 关系类型，仅当选择最短路径且为weight_property时必选          |
| 5    | filters       | list<object> | body     | 否       |      | 条件规则                                                     |
| 6    | limit         | int          | body     | 否       |      | 路径结果总数量,默认无上限                                    |
| 7    | path_decision | string       | body     | 否       |      | 最短路径决策依据，单选path_depth, weight_property, 只有选择path_type为最短路径时必选 |
| 8    | path_type     | int          | body     | 是       |      | 路径类型，单选0，1，2，分别表示全部路径，最短路径，无环路径  |
| 9    | property      | string       | body     | 否       |      | 权重属性，权重计算时使用，当选择最短路径且weight_property时，必选且只能选择一种，此属性是字段edges中边类型中的一种 |
| 10   | source        | string       | body     | 是       |      | 起始点vid                                                    |
| 11   | steps         | int          | body     | 否       |      | 路径最长深度，默认为5                                        |
| 12   | target        | string       | body     | 是       |      | 终点vid                                                      |

请求示例：

```json
/api/graph/v1/graph-explore/kgs/1/paths
{
    "direction":"positive",
    "path_type":1,
    "source":"xxx",
    "target":"xxx",
}
```

响应参数：

| 序号 | 字段名称 | 字段类型     | 字段说明 |
| :--- | :------- | :----------- | :------- |
| 1    | edges    | list<object> | 边集合   |
| 2    | nodes    | list<object> | 点集合   |
| 3    | paths    | object       | 路径集合 |

返回样例：

```json
{
    "res": {
        "nodes": [
            {
                "id": "e77e6d221df33f50de791b3cf7aa1f2b",
                "alias": "company_1",
                "color": "#d9534c",
                "class_name": "company_1",
                "icon": "",
                "default_property": {
                    "name": "id",
                    "value": "1",
                    "alias": "id"
                },
                "tags": [
                    "company_1"
                ],
                "properties": [
                    {
                        "tag": "company_1",
                        "props": [
                            {
                                "name": "name",
                                "value": "爱数",
                                "alias": "name",
                                "type": "string",
                                "disabled": false,
                                "checked": false
                            }
                        ]
                    }
                ]
            }
        ],
        "edges": [
            {
                "id": "company_1_2_company:e77e6d221df33f50de791b3cf7aa1f2b-f917b87bb193c96198efb7b0e14400f0",
                "alias": "company_1_2_company",
                "color": "#d9534c",
                "class_name": "company_1_2_company",
                "source": "e77e6d221df33f50de791b3cf7aa1f2b",
                "target": "f917b87bb193c96198efb7b0e14400f0",
                "properties": []
            }
        ],
        "paths": [
            {
                "nodes": [
                    "e77e6d221df33f50de791b3cf7aa1f2b",
                    "f917b87bb193c96198efb7b0e14400f0"
                ],
                "edges": [
                    "company_1_2_company:e77e6d221df33f50de791b3cf7aa1f2b-f917b87bb193c96198efb7b0e14400f0"
                ]
            }
        ]
    }
}
```

### 2.50、邻居查询

```
POST  /api/graph/v1/graph-explore/kgs/{kg_id}/neighbors
```

请求参数：

| 序号 | 字段名称  | 字段类型     | 字段位置 | 是否必须 | 长度 | 字段说明                                                     |
| :--- | :-------- | :----------- | -------- | :------- | ---- | :----------------------------------------------------------- |
| 1    | kg_id     | int          | path     | 是       |      | 图谱id                                                       |
| 2    | vids      | list<string> | body     | 是       |      | 起点列表                                                     |
| 3    | direction | string       | body     | 否       |      | 边的方向[positive, reverse, bidirect]正向，反向，双向，为空默认正向 |
| 4    | filters   | list<object> | body     | 否       |      | 过滤条件列表                                                 |
| 5    | steps     | int          | body     | 否       |      | 最大跳数，默认1                                              |

请求示例：

```json
/api/graph/v1/graph-explore/kgs/1/neighbors
{
    "vids":["xxx"],
    "direction":"xxx",
    "filters":{},
    "steps":1,
}
```

响应参数：

| 序号 | 字段名称    | 字段类型     | 字段说明     |
| :--- | :---------- | :----------- | :----------- |
| 1    | edges       | list<object> | 关系结果列表 |
| 2    | nodes_count | int          | 关系结果数量 |
| 3    | nodes       | list<object> | 实体结果列表 |
| 4    | nodes_count | int          | 实体结果数量 |

返回样例：

```json
{
    "res": {
        "nodes_count": 1,
        "edges_count": 1,
        "nodes": [
            {
                "id": "7437bced980a69a59282167991f5a0d5",
                "alias": "反应",
                "color": "#E39640",
                "class_name": "reaction",
                "icon": "",
                "default_property": {
                    "name": "name",
                    "value": "name",
                    "alias": "反应300"
                },
                "tags": [
                    "reaction"
                ],
                "properties": [
                    {
                        "tag": "reaction",
                        "props": [
                            {
                                "name": "reaction_temp_lower",
                                "value": "__NULL__",
                                "alias": "reaction_temp_lower",
                                "type": "null",
                                "disabled": false,
                                "checked": false
                            }
                        ]
                    }
                ]
            }
        ],
        "edges": [
            {
                "id": "chemical_2_reaction:893d733bdcd336a4f28997da42862fd0->f89aabcb95b2b3466fd5c20f8a506999",
                "alias": "参与",
                "color": "#BBD273",
                "class_name": "chemical_2_reaction",
                "source": "893d733bdcd336a4f28997da42862fd0",
                "target": "f89aabcb95b2b3466fd5c20f8a506999",
                "properties": [
                    {
                        "name": "stoichiometric_ratio",
                        "value": "1.0",
                        "alias": "stoichiometric_ratio",
                        "type": "float",
                        "disabled": false,
                        "checked": false
                    }
                ]
            }
        ]
    }
}
```

### 2.51、统计点的进出边

```
POST  /api/graph/v1/graph-explore/kgs/{kg_id}/expandv
```

请求参数：

| 序号 | 字段名称 | 字段类型 | 字段位置 | 是否必须 | 长度 | 字段说明 |
| :--- | :------- | :------- | -------- | :------- | ---- | :------- |
| 1    | kg_id    | int      | path     | 是       |      | 图谱id   |
| 2    | vid      | string   | body     | 是       |      |          |

请求示例：

```json
/api/graph/v1/graph-explore/kgs/1/expandv
{
    "vids":"xxx"
}
```

响应参数：

| 序号 | 字段名称 | 字段类型     | 字段说明 |
| :--- | :------- | :----------- | :------- |
| 1    | id       | string       |          |
| 2    | out_e    | list<object> | 出边     |
| 3    | in_e     | list<object> | 进边     |

| 序号 | 字段名称   | 字段类型 | 字段说明 |
| :--- | :--------- | :------- | :------- |
| 1    | alias      | string   | 显示名   |
| 2    | color      | string   | 颜色     |
| 3    | count      | int      | 数量     |
| 4    | edge_class | string   | 关系类型 |

返回样例：

```json
{
    "res": {
        "id": "5fd46f18655447c9c0e799bfac326dca",
        "out_e": [
            {
                "edge_class": "product",
                "count": 1,
                "color": "#68798E",
                "alias": "产出"
            }
        ],
        "in_e": [
            {
                "edge_class": "involve",
                "count": 2,
                "color": "#5C539B",
                "alias": "参与消耗"
            }
        ]
    }
}
```

## 3、本体库管理

### 3.1、根据本体id获取本体信息

```
GET  /api/builder/v1/onto/{otl_id}
```

请求参数：

| 序号 | 字段名称 | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明 |
| :--- | :------- | :------- | -------- | :------- | ---- | :------- |
| 1    | otl_id   | int      | path     | 是       |      | 本体id   |

请求示例：

```
/api/builder/v1/onto/121
```

响应参数：

| 序号 | 字段名称      | 字段类型     | 字段说明                   |
| :--- | :------------ | :----------- | :------------------------- |
| 1    | id            | int          | 本体id                     |
| 2    | ontology_name | string       | 本体名称                   |
| 3    | ontology_des  | string       | 本体描述                   |
| 4    | entity        | list         | 实体类信息                 |
| 5    | edge          | list         | 关系类信息                 |
| 6    | used_task     | list<int>    | 已经被渲染过的本体相关任务 |
| 7    | all_task      | list<int>    | 本体相关的所有相关任务     |
| 8    | otl_temp      | list<object> | 本体草稿                   |
| 9    | identify_id   | string       | 本体唯一id                 |
| 10   | knw_id        | int          | 知识网络id                 |
| 11   | domain        | list<string> | 本体所属领域               |
| 12   | create_by     | string       | 本体创建者uuid             |
| 13   | create_time   | string       | 本体创建时间               |
| 14   | update_by     | string       | 本体更新uuid               |
| 15   | update_time   | string       | 本体更新时间               |
| 16   | canvas        | object       | 画布信息                   |
| 17   | otl_status    | string       | 状态                       |

响应示例：

```json
{
    "res": {
        "id": 1,
        "ontology_name": "test",
        "ontology_des": "test des",
        "entity": [],
        "edge": [],
        "used_task": [1,2],
        "all_task": [1,2],
        "otl_temp": [],
        "identify_id": "cc744aed-4aa1-43f1-9b2a-cebb7640f01f",
        "knw_id": 1,
        "domain": ["domain11", "domain22"],
        "create_by": "d52cce80-a285-47dd-a6b7-025572bc1cf9",
        "create_time": "2023-05-25 10:54:49",
        "update_by": "d52cce80-a285-47dd-a6b7-025572bc1cf9",
        "update_time": "2023-05-25 10:54:49",
        "canvas": {
            "background_color":"white",
            "background_image":"point"
        },
        "otl_status": "pending"
    }
}
```

### 3.2、获取本体列表

```
GET  /api/builder/v1/onto/page
```

请求参数：

| 序号 | 字段名称 | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明                                                     |
| ---- | :------- | :------- | :------- | :------- | ---- | :----------------------------------------------------------- |
| 1    | knw_id   | int      | query    | 是       |      | 知识网络id                                                   |
| 2    | page     | int      | query    | 是       |      | 页数。-1表示所有                                             |
| 3    | size     | int      | query    | 是       |      | 每页个数                                                     |
| 4    | rule     | string   | query    | 是       | 6    | 排序规则。可选值：name: 按名称排序create: 按创建时间排序update: 按更新时间排序 |
| 5    | order    | string   | query    | 是       | 4    | 顺序。可选值：asc desc                                       |
| 6    | search   | string   | query    | 否       | 50   | 按名称搜索                                                   |
| 7    | filter   | string   | query    | 否       | 6    | 可选值：import: 用于流程三导入本体。过滤掉没有正式保存版本的本体。 |

请求示例：

```
/api/builder/v1/onto/page?knw_id=2&page=1&size=10&rule=create&order=desc
```

响应参数：

| 序号 | 字段名称 | 字段类型     | 字段说明       |
| :--- | :------- | :----------- | :------------- |
| 1    | count    | int          | 本体列表数量   |
| 2    | otls     | list<object> | 返回的本体列表 |

| 序号 | 字段名称         | 字段类型     | 字段说明                                                     |
| :--- | :--------------- | :----------- | :----------------------------------------------------------- |
| 1    | otl_id           | int          | 本体id                                                       |
| 2    | ontology_name    | string       | 本体名称                                                     |
| 3    | ontology_des     | string       | 本体描述                                                     |
| 4    | domain           | list<string> | 领域                                                         |
| 5    | entity_num       | int          | 实体类数量                                                   |
| 6    | edge_num         | int          | 关系类数量                                                   |
| 7    | is_temp          | boolean      | True：草稿(ontology_table的otl_temp不为空)False：正式版      |
| 8    | saved            | boolean      | True：有过正式保存的版本（ontology_table的entity不为空）False：无正式保存的版本 |
| 9    | create_user_name | string       | 创建人名称                                                   |
| 10   | create_time      | string       | 创建时间                                                     |
| 11   | update_user_name | string       | 最终操作人名称                                               |
| 12   | update_time      | string       | 最终操作时间                                                 |

响应示例：

```json
{
    "res": {
        "count": 10,
        "otls":[
            {
                "otl_id": 1,
                "ontology_name": "test_otl",
                "ontology_des": "test",
                "domain": ["domain11", "domain22"],
                "entity_num": 10,
                "edge_num": 10,
                "is_temp": false,
                "saved": false,
                "create_user_name": "tom",
                "create_time": "2023-05-29 11:02:52",
                "update_user_name": "tom",
                "update_time": "2023-05-29 11:02:52"
            },
            ......
        ]
    }
}
```

### 3.3、下载本体样例文件

```
POST  /api/builder/v1/onto/template
```

请求参数：

| 序号 | 字段名称 | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明  |
| ---- | :------- | :------- | :------- | :------- | ---- | :-------- |
| 1    | format   | string   | body     | 是       | 4    | xlsx json |

请求示例：

```json
{
    "format":"xlsx"
}
```

响应示例：

```
本体模板.xlsx
本体模板.json
```

### 3.4、创建本体

```
POST  /api/builder/v1/onto/add
```

请求参数：

| 序号 | 字段名称      | 字段类型     | 参数位置 | 是否必须 | 长度 | 字段说明                                                     |
| :--- | :------------ | :----------- | :------- | :------- | ---- | :----------------------------------------------------------- |
| 1    | ontology_name | string       | body     | 是       | 50   | 本体名                                                       |
| 2    | ontology_des  | string       | body     | 否       | 150  | 本体描述                                                     |
| 3    | domain        | list<string> | body     | 否       |      | 本体所属领域                                                 |
| 4    | knw_id        | int          | body     | 是       |      | 知识网络id                                                   |
| 5    | entity        | list         | body     | 是       |      | 实体类信息                                                   |
| 6    | edge          | list         | body     | 是       |      | 关系类信息                                                   |
| 7    | temp_save     | boolean      | body     | 否       |      | True: 保存为草稿False（默认）: 正式保存                      |
| 8    | used_task     | list<int>    | body     | 是       |      | 预测实体类的任务id列表（记录下来，下次再进入的时候前端就不会从任务列表再次导入实体类） |
| 9    | copy_from     | int          | body     | 否       |      | 仅复制本体时传该参数，表示被复制的本体id                     |
| 10   | canvas        | object       | body     | 是       |      | 画布样式                                                     |

| 序号 | 字段名称         | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明                                                     |
| :--- | :--------------- | :------- | -------- | :------- | ---- | :----------------------------------------------------------- |
| 1    | background_color | string   | body     | 是       | 10   | 画布背景颜色。可选值：white：白色light_grey：浅灰色grey：灰色light_blue：浅蓝色blue：蓝色 |
| 2    | background_image | string   | body     | 是       | 5    | 画布背景图案。可选值：empty：无背景point：点状net：网格状    |

请求示例：

```json
{
    "ontology_name": "test_otl",
    "ontology_des": "test",
    "domain": ["domain11", "domain22"],
    "knw_id": 10,
    "entity": [],
    "edge": [],
    "temp_save": false,
    "used_task": [],
    "canvas": {
        "background_color":"white",
        "background_image":"point"
    },
}
```

响应参数：

| 序号 | 字段名称    | 字段类型 | 是否必须 | 字段说明 |
| :--- | :---------- | :------- | :------- | :------- |
| 1    | ontology_id | string   | 是       | 本体id   |

响应示例：

```json
{
    "res":{
        "ontology_id": 1
    }
}
```

### 3.5、编辑本体

```
POST  /api/builder/v1/onto/edit/{otl_id}
```

请求参数：

| 序号 | 字段名称      | 字段类型     | 参数位置 | 是否必须 | 长度 | 字段说明                                                     |
| :--- | :------------ | :----------- | :------- | :------- | ---- | :----------------------------------------------------------- |
| 1    | otl_id        | int          | path     | 是       |      | 本体id                                                       |
| 2    | ontology_name | string       | body     | 是       | 50   | 本体名称                                                     |
| 3    | ontology_des  | string       | body     | 否       | 150  | 本体描述                                                     |
| 4    | domain        | list<string> | body     | 否       |      | 本体所属领域                                                 |
| 5    | entity        | list<object> | body     | 是       |      | 实体类信息                                                   |
| 6    | edge          | list<object> | body     | 是       |      | 关系类信息                                                   |
| 7    | temp_save     | boolean      | body     | 否       |      | True：保存为草稿  False(默认)：正式保存                      |
| 8    | cover         | boolean      | body     | 否       |      | True: 从流程三保存至本体库时选择覆盖保存  False(默认)        |
| 9    | used_task     | list<int>    | body     | 是       |      | 预测实体类的任务id列表（记录下来，下次再进入的时候前端就不会从任务列表再次导入实体类） |
| 10   | canvas        | object       | body     | 是       |      | 画布样式                                                     |

| 序号 | 字段名称         | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明                                                     |
| :--- | :--------------- | :------- | -------- | :------- | ---- | :----------------------------------------------------------- |
| 1    | background_color | string   | body     | 是       | 10   | 画布背景颜色。可选值：white：白色light_grey：浅灰色grey：灰色light_blue：浅蓝色blue：蓝色 |
| 2    | background_image | string   | body     | 是       | 5    | 画布背景图案。可选值：empty：无背景point：点状net：网格状    |

请求示例：

```json
{
    "otl_id": 1,
    "ontology_name": "test_otl",
    "ontology_des": "test",
    "domain": ["domain11", "domain22"],
    "entity": [],
    "edge": [],
    "temp_save": false,
    "used_task": [],
    "canvas": {
        "background_color":"white",
        "background_image":"point"
    },
}
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 是否必须 | 字段说明         |
| :--- | :------- | :------- | :------- | :--------------- |
| 1    | res      | string   | 是       | 返回的结果字符串 |

响应示例：

```json
{
    "res": "edit success !"
}
```

### 3.6、更改本体名称等基本信息

```
POST  /api/builder/v1/onto/edit_name/{otl_id}
```

请求参数：

| 序号 | 字段名称      | 字段类型     | 参数位置 | 是否必须 | 长度 | 字段说明     |
| ---- | :------------ | :----------- | :------- | :------- | ---- | :----------- |
| 1    | otl_id        | int          | path     | 是       |      | 本体id       |
| 2    | ontology_name | string       | body     | 是       | 50   | 本体名       |
| 3    | ontology_des  | string       | body     | 否       | 150  | 本体描述     |
| 4    | domain        | list<string> | body     | 否       |      | 本体所属领域 |

请求示例：

```json
{
    "otl_id": 1,
    "ontology_name": "test_otl",
    "ontology_des": "test",
    "domain": ["domain11", "domain22"]
}
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 是否必须 | 字段说明         |
| :--- | :------- | :------- | :------- | :--------------- |
| 1    | res      | string   | 是       | 返回的结果字符串 |

响应示例：

```json
{
    "res": "edit success !"
}
```

### 3.7、删除本体

```
POST  /api/builder/v1/onto/delete
```

请求参数：

| 序号 | 字段名称 | 字段类型  | 参数位置 | 是否必须 | 长度 | 字段说明   |
| ---- | :------- | :-------- | :------- | :------- | ---- | :--------- |
| 1    | otl_ids  | list<int> | body     | 是       |      | 本体列表   |
| 2    | knw_id   | int       | body     | 是       |      | 知识网络id |

请求示例：

```json
{
    "otl_ids": [3],
    "knw_id": 1,
}
```

响应参数：

| 序号 | 字段名称 | 字段类型  | 是否必须 | 字段说明     |
| :--- | :------- | :-------- | :------- | :----------- |
| 1    | otl_ids  | list<int> | 是       | 删除的本体id |

响应示例：

```json
{
    "res": {
        "otl_ids": [1,2,3]
    }
}
```

### 3.8、根据数据源名获取数据表

```
GET  /api/builder/v1/onto/ds_table/list
```

请求参数：

| 序号 | 字段名称    | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明                                                     |
| :--- | :---------- | :------- | -------- | :------- | ---- | :----------------------------------------------------------- |
| 1    | ds_id       | int      | query    | 是       |      | 数据源id                                                     |
| 2    | data_source | string   | query    | 是       | 20   | 数据源类型（mysql、hive、sqlserver、kingbasees、postgresql、clickhouse等） |

请求示例：

```
/api/builder/v1/onto/ds_table/list?ds_id=1&data_source=mysql
```

响应参数：

| 序号 | 字段名 | 字段类型  | 字段说明                                                     |
| :--- | :----- | :-------- | :----------------------------------------------------------- |
| 1    | count  | int       | 返回数据总数                                                 |
| 2    | output | list/dict | 如果数据源类型为 mysql、hive ，返回结果为表名list <br />如果数据源类型为 SQLserver、KingbaseES、postgreSQL 返回结果为{"模式名"：["表名1", "表名2"]，...... } |

响应示例：

```json
//数据源类型为mysql、hive、clickhouse
{
    "count": 100,
    "output": ["表名1", "表名2", "表名3", ......]
}

//数据源类型为SQLserver、KingbaseES、postgreSQL
{
    "count": 100,
    "output": {
        "模式1": ["表名1", "表名2", "表名3", ......],
    	"模式2": ["表名1", "表名2", "表名3", ......],
        "模式3": ["表名1", "表名2", "表名3", ......],
    }
}
```

### 3.9、数据源预览接口

```
GET  /api/builder/v1/onto/preview_data
```

请求参数：

| 序号 | 字段名称    | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明                                                     |
| :--- | :---------- | :------- | -------- | :------- | ---- | :----------------------------------------------------------- |
| 1    | data_source | string   | query    | 是       | 20   | 数据源类型（mysql、hive、sqlserver、kingbasees、postgresql、clickhouse等） |
| 2    | name        | string   | query    | 是       |      | 数据源类型为mysql、hive、clickhouse：数据表<br />数据源类型为sqlserver、kingbesees、postgresql： 模式/数据表 |
| 3    | ds_id       | int      | query    | 是       |      | 数据源ID                                                     |

请求示例：

```
/api/builder/v1/onto/preview_data?data_source=mysql&name=xxx&ds_id=1
```

响应参数：

| 序号 | 字段名称 | 字段类型     | 是否必须 | 字段说明 |
| :--- | :------- | :----------- | :------- | :------- |
| 1    | content  | list<list>   | 是       | 预览结果 |
| 2    | property | list<string> | 是       | 属性列表 |

响应示例：

```json
{
    "res": {
        "content": [
            ["id", "name", "age", "time"],
            ["1", "tom", "5", "15:13"],
            ["2", "jerry", "15", "15:23"],
            ["3", "jack", "25", "15:33"],
            ["4", "curry", "35", "15:43"]
        ],
        "property": ["id", "name", "age", "time"]
    }
}
```

### 3.10、数据抽取接口

```
POST  /api/builder/v1/onto/autogen_schema
```

请求参数：

| 序号 | 字段名称     | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明                                                     |
| :--- | :----------- | :------- | -------- | :------- | ---- | :----------------------------------------------------------- |
| 1    | graph_id     | int      | body     | 是       |      | 图谱配置id                                                   |
| 2    | ds_id        | string   | body     | 是       |      | 数据源id                                                     |
| 3    | data_source  | string   | body     | 是       | 20   | 数据源类型（mysql、hive、sqlserver、kingbasees、postgresql、clickhouse等） |
| 4    | file         | string   | body     | 是       |      | 对mysql、hive、clickhouse：表名<br />对SQLserver、KingbaseES、postgreSQL: 模式名/表名 |
| 5    | extract_type | string   | body     | 是       |      | 抽取类型（labelExtraction：标注抽取    standardExtraction：标准抽取） |

请求示例：

```json
//数据源为hive、mysql、clickhouse
{
  "graph_id": 1,
  "ds_id": "4",
  "data_source": "hive",
  "file_list": ["comment_hascreator_person"],
  "extract_type": "standardExtraction"
}
//数据源为SQLserver、KingbaseES、postgreSQL
{
  "graph_id": 1,
  "ds_id": "12",
  "data_source": "sqlserver",
  "file_list": ["public/table1", "public/table2", "kom/table1"],
  "extract_type": "standardExtraction"
}
```

响应参数：

| 序号 | 字段名称                 | 字段类型     | 字段说明   |
| ---- | :----------------------- | :----------- | :--------- |
| 1    | entity_list              | list<list>   | 实体列表。 |
| 2    | entity_main_table_dict   | list<object> | 实体所属表 |
| 3    | entity_property_dict     | list<object> | 实体属性表 |
| 4    | entity_relation_set      | list         | 三元组     |
| 5    | extract_type             | string       | 抽取类型   |
| 6    | relation_main_table_dict | list         | 关系所属表 |
| 7    | relation_property_dict   | list         | 关系属性表 |

| 序号 | 字段名称   | 字段类型   | 字段说明                                                     |
| ---- | :--------- | :--------- | :----------------------------------------------------------- |
| 1    | entity     | string     | 实体名                                                       |
| 2    | main_table | list<list> | 对mysql、hive、clickhouse：表名<br />对SQLserver、KingbaseES、postgreSQL: 模式名/表名 |

| 序号 | 字段名称    | 字段类型     | 字段说明           |
| ---- | :---------- | :----------- | :----------------- |
| 1    | entity      | string       | 实体名             |
| 2    | property    | list<list>   | [属性名, 属性类型] |
| 3    | column_name | list<string> | 原数据列名         |

响应示例：

```json
{
  "res": {
    "entity_list": [["sub_industry_info", "sub_industry_info"]],
    "entity_main_table_dict": [
      {
        "entity": "sub_industry_info",
        "main_table": [
          [
            "432908423908590432"
          ]
        ]
      }
    ],
    "entity_property_dict": [
      {
        "column_name": [
          "sub_industry_id",
          "subindustry_name",
          "industry_status",
          "industry_level"
        ],
        "entity": "sub_industry_info",
        "property": [
          ["sub_industry_id", "string"],
          ["subindustry_name", "string"],
          ["industry_status", "string"],
          ["industry_level", "string"]
        ]
      }
    ],
    "entity_relation_set": [],
    "extract_type": "标准抽取",
    "relation_main_table_dict": [],
    "relation_property_dict": []
  }
}
```

### 3.11、根据图谱id返回本体信息

```
GET  /api/builder/v1/onto/kg/{kg_id}
```

请求参数：

| 序号 | 字段名称 | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明 |
| :--- | :------- | :------- | :------- | :------- | ---- | :------- |
| 1    | kg_id    | int      | path     | 是       |      | 图谱id   |

请求示例：

```
/api/builder/v1/onto/kg/1
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 字段说明         |
| ---- | :------- | :------- | :--------------- |
| 1    | res      | object   | 返回的结果字符串 |

响应示例：

```json
{
    "res": {
        "all_task": [],
        "canvas": {},
        "create_time": "2024-04-02 17:36:35",
        "create_by": "",
        "domain": [],
        "edge": [],
        "entity": [
            {
                "alias": "www",
                "default_tag": "dada",
                "description": "",
                "entity_id": 14,
                "fill_color": "rgba(88,137,196,1)",
                "icon": "empty",
                "icon_color": "#ffffff",
                "index_default_switch": false,
                "index_main_switch": true,
                "model": "",
                "name": "aaa",
                "primary_key": [
                    "rest",
                    "dada"
                ],
                "properties": [
                    {
                        "alias": "rest",
                        "data_type": "string",
                        "description": "",
                        "name": "rest",
                        "synonym": ""
                    },
                    {
                        "alias": "dada",
                        "data_type": "string",
                        "description": "",
                        "name": "dada",
                        "synonym": ""
                    }
                ],
                "properties_index": [
                    "rest",
                    "dada"
                ],
                "shape": "circle",
                "size": "0.5x",
                "source_type": "manual",
                "stroke_color": "rgba(88,137,196,1)",
                "synonym": "",
                "task_id": "",
                "text_color": "rgba(0,0,0,1)",
                "text_position": "top",
                "text_type": "adaptive",
                "text_width": 15,
                "vector_generation": [
                    "rest",
                    "dada"
                ],
                "x": 663,
                "y": 410.5
            }
        ],
        "id": 4,
        "identify_id": null,
        "knw_id": 1,
        "ontology_des": "",
        "ontology_name": "",
        "otl_status": "available",
        "otl_temp": [],
        "update_time": "2024-06-14 15:34:55",
        "update_by": "",
        "used_task": []
    }
}
```

### 3.12、根据数据源预测本体

```
POST  /api/builder/v1/onto/task/build
```

请求参数：

| 序号 | 字段名称    | 字段类型 | 字段位置 | 是否必须 | 长度 | 字段说明                                                     |
| ---- | :---------- | :------- | :------- | :------- | ---- | :----------------------------------------------------------- |
| 1    | ontology_id | int      | body     | 是       |      | 本体id                                                       |
| 2    | file_list   | list     | body     | 是       |      | 抽取的数据列表<br />mysql、hive、clickhouse：[表名]<br />SQLserver、KingbaseES、postgreSQL : ["模式/表名"，...... ] |
| 3    | postfix     | string   | body     | 是       |      | 传""                                                         |
| 4    | ds_id       | int      | body     | 是       |      | 数据源ID                                                     |

请求示例：

```json
{  
    "ontology_id": 1, 
    "file_list": ["v1"],
    "postfix": "",
    "ds_id": 1
}
```

响应参数：

| 序号 | 字段名称       | 字段类型 | 字段说明     |
| :--- | :------------- | :------- | :----------- |
| 1    | celery_task_id | string   | celery任务id |
| 2    | ontology_id    | int      | 本体id       |

响应示例：

```json
{
    "celery_task_id": "ff1a19evb-9192-4bb4-8dff-901c83941d09",
    "ontology_id": 12
}
```

### 3.13、获取本体任务信息接口

```
POST  /api/builder/v1/onto/task/page
```

请求参数：

| 序号 | 字段名称    | 字段类型  | 字段位置 | 是否必须 | 长度 | 字段说明         |
| :--- | :---------- | :-------- | -------- | :------- | ---- | :--------------- |
| 1    | page        | int       | body     | 是       |      | 页号             |
| 2    | size        | int       | body     | 是       |      | 每页个数         |
| 3    | ontology_id | int       | body     | 是       |      | 本体ID           |
| 4    | used_task   | list<int> | body     | 是       |      | 使用到的任务列表 |

请求示例：

```json
{ 
    "page": 1, 
    "size": 20, 
    "ontology_id": 1, 
    "used_task": [1] 
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
        "all_task_status": "finished",
        "result_info": {
            "result_count": 1,
            "results": [{
                "data_source": {
                    "create_time": "2023-02-06 04:19:55",
                    "create_by": "11c9a837-82e7-45c7-9533-00309a1dba5d",
                    "data_type": "structured",
                    "data_source": "mysql",             
                    "ds_address": "10.4.107.112",
                    "ds_auth": null,
                    "ds_password": "ZWlzb28uY29tMTIz",
                    "ds_path": "anydata",
                    "ds_port": 3320,
                    "ds_user": "root",
                    "ds_name": "\u672c\u673amysql",
                    "extract_type": "standardExtraction",
                    "file_type": "",
                    "id": 1,
                    "json_schema": "",
                    "knw_id": 1,
                    "queue": "",
                    "update_time": "2023-02-06 04:19:55",
                    "update_by": "11c9a837-82e7-45c7-9533-00309a1dba5d",
                    "vhost": "",
                    "connect_type":"odbc"             
                },
                "result": {
                    "entity_list": [
                        ["version", "version"]
                    ],
                    "entity_main_table_dict": [{
                        "entity": "version",
                        "main_table": ["version"]
                    }],
                    "entity_property_dict": [{
                        "column_name": ["id", "manager_version", "builder_version", "engine_version", "dataio_version", "rbac_version", "data_auth_version"],
                        "entity": "version",
                        "property": [
                            {"alias":"id","data_type":"string","description":"","name":"id","synonym":""},{"alias":"manager_version","data_type":"string","description":"","name":"manager_version","synonym":""},{"alias":"builder_version","data_type":"string","description":"","name":"builder_version","synonym":""},{"alias":"engine_version","data_type":"string","description":"","name":"engine_version","synonym":""},{"alias":"dataio_version","data_type":"string","description":"","name":"dataio_version","synonym":""},{"alias":"rbac_version","data_type":"string","description":"","name":"rbac_version","synonym":""},               {"alias":"data_auth_version","data_type":"string","description":"","name":"data_auth_version","synonym":""}
                        ]
                    }],
                    "entity_relation_set": [],
                    "extract_type": "\u6807\u51c6\u62bd\u53d6",
                    "relation_main_table_dict": [],
                    "relation_property_dict": []
                },
                "task_id": 7
            }]
        },
        "task_info": {
            "task_count": 1,
            "tasks": [{
                "celery_task_id": "4e3ba355-d08f-4569-8069-4e517916d2fa",
                "task_id": 7,
                "task_name": "version",
                "task_status": "finished",
                "task_type": "table"
            }]
        }
    }
}
```

### 3.14、删除任务

```
POST  /api/builder/v1/onto/task/delete
```

请求参数：

| 序号 | 字段名称  | 字段类型  | 字段位置 | 是否必须 | 长度 | 字段说明   |
| :--- | :-------- | :-------- | -------- | :------- | ---- | :--------- |
| 1    | task_list | list<int> | body     | 是       |      | 任务id列表 |

请求示例：

```json
{
    “task_list”：[256,257]
}
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 字段说明 |
| :--- | :------- | :------- | :------- |
| 1    | res      | string   | 返回结果 |

响应示例：

```json
{
    "res": "delete task list success"
}
```

### 3.15、获取预测文件状态

```
GET  /api/builder/v1/onto/task_files/page
```

请求参数：

| 序号 | 字段名称 | 字段类型 | 字段位置 | 是否必须 | 长度 | 字段说明 |
| :--- | :------- | :------- | -------- | :------- | ---- | :------- |
| 1    | task_id  | int      | query    | 是       |      | 任务id   |
| 2    | page     | int      | query    | 是       |      | 页号     |
| 3    | size     | int      | query    | 是       |      | 每页个数 |

请求示例：

```
/api/builder/v1/onto/task_files/page?task_id=43&page=1&size=2
```

响应参数：

| 序号 | 字段名称    | 字段类型   | 字段说明     |
| :--- | :---------- | :--------- | :----------- |
| 1    | task_id     | int        | 任务id       |
| 2    | ontology_id | int        | 本体id       |
| 3    | files       | string     | 数据状态信息 |
| 4    | task_status | string     | 任务状态     |
| 5    | error_code  | string/int | 错误码       |

响应示例：

```json
{
    "res": {
        "result": {
            "task_id": 43,
            "ontology_id": 1,
            "files": "[["film","DataBase","MySQL数据源","success"]]",
            "task_status": "finished",
            "error_code":""
        }
    }
}
//或者
{
    "res": {
        "result": {
            "task_id": 43,
            "ontology_id": 1,
            "files": "",
            "task_status": "failed",
            "error_code":500006
        }
    }
}
```

### 3.16、退出不保存删除本体相关的所有的任务

```
DELETE  /api/builder/v1/onto/task/batch_delete
```

请求参数：

| 序号 | 字段名称    | 字段类型 | 字段位置 | 是否必须 | 长度 | 字段说明                                                     |
| :--- | :---------- | :------- | -------- | :------- | ---- | :----------------------------------------------------------- |
| 1    | ontology_id | int      | query    | 是       |      | 本体id                                                       |
| 2    | state       | string   | query    | 是       | 10   | edit：编辑不保存 （删除部分任务）notedit：新建不保存（删除所有任务） |

请求示例：

```
/api/builder/v1/task/onto/deletealltask?ontology_id=32&state=notedit
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 字段说明 |
| :--- | :------- | :------- | :------- |
| 1    | res      | string   | 返回结果 |

响应示例：

```json
{
    "res": "delete all task of ontology_id 1 success"
}
```

### 3.17、本体入口一键导入时数据源列表

```
GET  /api/builder/v1/onto/ds/list
```

请求参数：

| 序号 | 字段名称 | 字段类型 | 字段位置 | 是否必须 | 长度 | 字段说明 |
| :--- | :------- | :------- | -------- | :------- | ---- | :------- |
|      |          |          |          |          |      |          |

请求示例：

```

```

响应参数：

| 序号 | 字段名称 | 字段类型     | 字段说明       |
| :--- | :------- | :----------- | :------------- |
| 1    | count    | int          | 数据源总个数   |
| 2    | df       | list<object> | 数据源具体信息 |

| 序号 | 字段名称     | 字段类型 | 字段说明   |
| ---- | :----------- | :------- | :--------- |
| 1    | create_time  | string   | 创建时间   |
| 2    | create_by    | string   | 创建用户   |
| 3    | data_type    | string   | 数据类型   |
| 4    | data_source  | string   | 数据源类型 |
| 5    | ds_address   | string   | 地址       |
| 6    | ds_password  | string   | 密码       |
| 7    | ds_path      | string   | 数据库路径 |
| 8    | ds_port      | int      | 端口       |
| 9    | ds_user      | string   | 用户名     |
| 10   | ds_name      | string   | 数据源名称 |
| 11   | extract_type | string   | 抽取类型   |
| 12   | id           | int      | 数据源id   |
| 13   | knw_id       | int      | 知识网络id |
| 14   | update_time  | string   | 修改时间   |
| 15   | update_by    | string   | 修改用户   |
| 16   | connect_type | string   | 连接方式   |

响应示例：

```json
{
    "res": {
        "count": 1,
        "df": [{
            "create_time": "2023-02-06 04:19:55",
            "create_by": "11c9a837-82e7-45c7-9533-00309a1dba5d",
            "data_type": "structured",
            "data_source": "mysql",                  
            "ds_address": "10.4.107.112",
            "ds_password": "ZWlzb28uY29tMTIz",
            "ds_path": "anydata",
            "ds_port": 3320,
            "ds_user": "root",
            "ds_name": "\u672c\u673amysql",
            "extract_type": "standardExtraction",
            "id": 1,
            "knw_id": 1,
            "update_time": "2023-02-06 04:19:55",
            "update_by": "11c9a837-82e7-45c7-9533-00309a1dba5d",
            "connect_type":"odbc"                   
        }]
    }
}
```

### 3.18、导出本体文件

```
POST  /api/builder/v1/onto/export
```

请求参数：

| 序号 | 字段名称 | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明               |
| ---- | :------- | :------- | :------- | :------- | ---- | :--------------------- |
| 1    | otl_id   | int      | body     | 是       |      | 本体id                 |
| 2    | format   | string   | body     | 是       | 4    | 导出格式（xlsx、json） |

请求示例：

```json
{
    "otl_id":1,
    "format":"xlsx"
}
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 字段说明 |
| :--- | :------- | :------- | :------- |
| 1    | res      | string   | 返回结果 |

响应示例：

```json
本体模板.xlsx
本体模板.json
```

### 3.19、sql抽取接口

```
POST  /api/builder/v1/onto/sql/extract
```

请求参数：

| 序号 | 字段名称 | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明 |
| :--- | :------- | :------- | -------- | :------- | ---- | :------- |
| 1    | ds_id    | int      | body     | 是       |      | 数据源id |
| 2    | sql      | string   | body     | 是       |      | sql语句  |
| 3    | sql_name | string   | body     | 是       |      | sql名称  |

请求示例：

```json
{
    "ds_id":1,
    "sql":"xxx",
    "sql_name":"xxx"
}
```

响应参数：

| 序号 | 字段名称     | 字段类型     | 是否必须 | 字段说明                                          |
| :--- | :----------- | :----------- | :------- | :------------------------------------------------ |
| 1    | ds_id        | int          | 是       | 数据源id                                          |
| 2    | ds_name      | string       | 是       | 数据源名称                                        |
| 3    | data_source  | string       | 是       | 数据源类型                                        |
| 4    | ds_path      | string       | 是       | 数据库名                                          |
| 5    | extract_type | string       | 是       | 抽取类型                                          |
| 6    | file_name    | string       | 是       | sql名称                                           |
| 7    | file_path    | string       | 是       | 数据库名                                          |
| 8    | file_source  | string       | 是       | sql查询语句                                       |
| 9    | file_type    | string       | 是       | file：文件      dir：文件夹（仅对模型抽取有意义） |
| 10   | property     | list<object> | 是       | 属性列表                                          |
| 11   | content      | list<list>   | 是       | 预览数据                                          |

响应示例：

```json
{
    "res": {
        "ds_id": 1,
        "ds_name": "name",
        "data_source": "mysql",
        "ds_path": "anydata",
        "extract_type": "sqlExtraction",
        "file_name": "sql_1",
        "file_path": "anydata",
        "file_source": "select * from a join b on a.id=b.a_id",
        "file_type": "",
        "property": [
            {
                "column_name": "a.id",
                "field": "aid",
                "type": "int"
            },
            {
                "column_name": "name",
                "field": "name",
                "type": "string"
            }
        ]
        "content": [
            ["a.id", "name", "age", "time"],
            ["1", "tom", "5", "15:13"],
            ["2", "jerry", "15", "15:23"],
            ["3", "jack", "25", "15:33"],
            ["4", "curry", "35", "15:43"]
        ]
    }
}
```

### 3.20、sql预览数据接口

```
POST  /api/builder/v1/onto/sql/preview_data
```

请求参数：

| 序号 | 字段名称 | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明 |
| :--- | :------- | :------- | -------- | :------- | ---- | :------- |
| 1    | ds_id    | int      | body     | 是       |      | 数据源id |
| 2    | sql      | string   | body     | 是       |      | sql语句  |

请求示例：

```json
{
    "ds_id":1,
    "sql":"xxx"
}
```

响应参数：

| 序号 | 字段名称 | 字段类型     | 是否必须 | 字段说明 |
| :--- | :------- | :----------- | :------- | :------- |
| 1    | content  | list<list>   | 是       | 预览数据 |
| 2    | property | list<string> | 是       | 属性列表 |

响应示例：

```json

{
    "res": {
        "content": [
            ["id", "name", "age", "time"],
            ["1", "tom", "5", "15:13"],
            ["2", "jerry", "15", "15:23"],
            ["3", "jack", "25", "15:33"],
            ["4", "curry", "35", "15:43"]
        ],
        "property": ["id", "name", "age", "time"]
    }
}
```

### 3.21、获取向量服务状态

```
GET  /api/builder/v1/onto/vector/service_status
```

请求参数：

| 序号 | 字段名称 | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明 |
| :--- | :------- | :------- | -------- | :------- | ---- | :------- |
|      |          |          |          |          |      |          |

请求示例：

```json

```

响应参数：

| 序号 | 字段名称 | 字段类型 | 是否必须 | 字段说明 |
| :--- | :------- | :------- | :------- | :------- |
| 1    | res      | string   | 是       | 返回结果 |

响应示例：

```json
//向量服务配置正常：
{
    "res": "success"
}
//向量服务未配置：
{
    "res": "Vector service not configured"
}
//向量服务异常：
{
    "res": "Vector Service Exception"
}

```

## 4、术语库管理
### 4.1、获取术语库列表

```
GET  /api/builder/v1/taxonomy/page
```

请求参数：

| 序号 | 字段名称 | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明                                                     |
| ---- | :------- | :------- | :------- | :------- | ---- | :----------------------------------------------------------- |
| 1    | knw_id   | int      | query    | 是       |      | 知识网络id                                                   |
| 2    | page     | int      | query    | 是       |      | 第几页                                                       |
| 3    | size     | int      | query    | 是       |      | 每页个数                                                     |
| 4    | rule     | string   | query    | 是       | 11   | 排序字段，可选值  update_time：更新时间  create_time：创建时间  name：术语库名称 |
| 5    | order    | string   | query    | 是       | 4    | 排序顺序，可选值：asc：升序desc：降序                        |
| 6    | name     | string   | query    | 否       | 100  | 搜索术语库名称                                               |

请求示例：

```
knw_id=1&page=1&size=20&rule=create_time&order=asc&name=xxx
```

响应参数：

| 序号 | 字段名称   | 字段类型     | 字段说明         |
| :--- | :--------- | :----------- | :--------------- |
| 1    | count      | int          | 不分页的结果总数 |
| 2    | taxonomies | list<object> | 术语库列表       |

| 序号 | 字段名称         | 字段类型 | 字段说明   |
| :--- | :--------------- | :------- | :--------- |
| 1    | id               | int      | 术语库id   |
| 2    | name             | string   | 术语库名称 |
| 3    | description      | string   | 术语库描述 |
| 4    | default_language | string   | 默认语言   |
| 5    | word_num         | int      | 术语数量   |
| 6    | create_by        | string   | 创建人id   |
| 7    | create_user_name | string   | 创建人名称 |
| 8    | create_time      | string   | 创建时间   |
| 9    | update_by        | string   | 更新人id   |
| 10   | update_user_name | string   | 更新人名称 |
| 11   | update_time      | string   | 更新时间   |

响应示例：

```json
{
    "res": {
        "count": 1,
        "taxonomies": [
            {
                "create_time": "2023-10-26 16:59:41",
                "create_by": "ef7eb926-4c52-11ee-ab5c-ba117504d52f",
                "create_user_name": "mia",
                "default_language": "zh_CN",
                "description": null,
                "id": 23,
                "name": "test",
                "update_time": "2023-10-30 14:59:44",
                "update_by": "ef7eb926-4c52-11ee-ab5c-ba117504d52f",
                "update_user_name": "mia",
                "word_num": 12
            }
        ]
    }
}
```

### 4.2、创建术语库

```
POST  /api/builder/v1/taxonomy/add
```

请求参数：

| 序号 | 字段名称         | 字段类型 | 字段位置 | 是否必须 | 长度 | 字段说明                                                   |
| ---- | :--------------- | :------- | :------- | :------- | ---- | :--------------------------------------------------------- |
| 1    | knw_id           | int      | body     | 是       |      | 知识网络id                                                 |
| 2    | name             | string   | body     | 是       | 100  | 术语库名称                                                 |
| 3    | default_language | string   | body     | 是       | 10   | 默认语言，可选值：zh_CN：中文简体 zh_TW：中文繁体 en：英文 |
| 4    | description      | string   | body     | 否       | 300  | 描述                                                       |

请求示例：

```json
{
    "knw_id": 23,
    "name": "test",
    "default_language": "zh_CN",
    "description": "xxxx",
}
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 是否必须 | 字段说明 |
| :--- | :------- | :------- | :------- | :------- |
| 1    | res      | int      | 是       | 术语库id |

响应示例：

```json
{
    "res": 4
}
```

### 4.3、编辑术语库

```
POST  /api/builder/v1/taxonomy/edit/{taxonomy_id}
```

请求参数：

| 序号 | 字段名称         | 字段类型 | 字段位置 | 是否必须 | 长度 | 字段说明                                                   |
| ---- | :--------------- | :------- | :------- | :------- | ---- | :--------------------------------------------------------- |
| 1    | taxonomy_id      | int      | path     | 是       |      | 术语库id                                                   |
| 2    | name             | string   | body     | 是       | 100  | 术语库名称                                                 |
| 3    | default_language | string   | body     | 是       | 10   | 默认语言，可选值：zh_CN：中文简体 zh_TW：中文繁体 en：英文 |
| 4    | description      | string   | body     | 否       | 300  | 描述                                                       |

请求示例：

```json
{
    "taxonomy_id": 23,
    "name": "test",
    "default_language": "zh_CN",
    "description": "xxxx",
}
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 是否必须 | 字段说明         |
| :--- | :------- | :------- | :------- | :--------------- |
| 1    | res      | string   | 是       | 返回的结果字符串 |

响应示例：

```json
{
    "res": "success"
}
```

### 4.4、删除术语库

```
POST  /api/builder/v1/taxonomy/delete
```

请求参数：

| 序号 | 字段名称     | 字段类型  | 字段位置 | 是否必需 | 长度 | 字段说明     |
| ---- | :----------- | :-------- | :------- | :------- | ---- | :----------- |
| 1    | taxonomy_ids | list<int> | body     | 是       |      | 术语库id列表 |

请求示例：

```json
{
    "taxonomy_ids": [23]
}
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 是否必须 | 字段说明                   |
| :--- | :------- | :------- | :------- | :------------------------- |
| 1    | res      | string   | 是       | 删除术语库的id组成的字符串 |

响应示例：

```json
{
    "res": {
        "error": [],
        "res": "29"
    }
}
```

### 4.5、添加词

```
POST  /api/builder/v1/taxonomy/{taxonomy_id}/add_word
```

请求参数：

| 序号 | 字段名称    | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明                                             |
| ---- | :---------- | :------- | :------- | :------- | ---- | :--------------------------------------------------- |
| 1    | taxonomy_id | int      | path     | 是       |      | 术语库id                                             |
| 2    | parent      | string   | body     | 否       | 50   | 父级词的id，若不传该参数，则将新建的词添加至顶级     |
| 3    | name        | string   | body     | 是       | 100  | 名称                                                 |
| 4    | language    | string   | body     | 是       | 10   | 语言，可选值：zh_CN：中文简体zh_TW：中文繁体en：英文 |

请求示例：

```json
//在顶级添加词：
{
    "name": "词2",
    "language": "zh_CN"
}
//在某词的下级添加词：
{
    "parent": "9287401c64be11eebc6e005056baa089",
    "name": "词2",
    "language": "zh_CN"
}
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 是否必须 | 字段说明 |
| :--- | :------- | :------- | :------- | :------- |
| 1    | res      | string   | 是       | 词的id   |

响应示例：

```json
{
    "res": "4fdbecc75d9f11ee84dd005056baa089"
}
```

### 4.6、编辑词的基本信息

```
POST  /api/builder/v1/taxonomy/{taxonomy_id}/word/{word_id}/label
```

请求参数：

| 序号 | 字段名称    | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明                                             |
| :--- | ----------- | :------- | :------- | :------- | ---- | :--------------------------------------------------- |
| 1    | taxonomy_id | int      | path     | 是       |      | 术语库id                                             |
| 2    | word_id     | string   | path     | 是       | 50   | 词的id                                               |
| 3    | action      | string   | body     | 是       | 6    | 可选值：add：新增update：更新remove：删除            |
| 4    | language    | string   | body     | 是       | 10   | 语言，可选值：zh_CN：中文简体zh_TW：中文繁体en：英文 |
| 5    | label       | object   | body     | 否       | 6    | 若action为add或update，则label为必传                 |

| 序号 | 字段名称    | 字段类型     | 参数位置 | 是否必须 | 长度 | 字段说明 |
| :--- | :---------- | :----------- | :------- | :------- | ---- | :------- |
| 1    | name        | string       | body     | 是       | 100  | 翻译     |
| 2    | description | string       | body     | 是       | 300  | 描述     |
| 3    | synonym     | list<string> | body     | 是       |      | 同义词   |

请求示例：

```json
/api/builder/v1/taxonomy/9/word/9287401c64be11eebc6e005056baa089/label
{
    "action": "update",
    "language": "zh_CN",
    "label": {
        "name": "词1_1",
        "description": "",
        "synonym": []
    }
}
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 是否必须 | 字段说明         |
| :--- | :------- | :------- | :------- | :--------------- |
| 1    | res      | string   | 是       | 返回的结果字符串 |

响应示例：

```json
{
    "res": "success"
}
```

### 4.7、移动词的层级

```
POST  /api/builder/v1/taxonomy/{taxonomy_id}/word/{word_id}/level
```

请求参数：

| 序号 | 字段名称    | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明                                     |
| ---- | :---------- | :------- | :------- | :------- | ---- | :------------------------------------------- |
| 1    | taxonomy_id | int      | path     | 是       |      | 术语库id                                     |
| 2    | word_id     | string   | path     | 是       | 50   | 词的id                                       |
| 3    | parent      | string   | body     | 是       | 50   | 新的父级词的id。若为'root'，表示移动至顶级。 |

请求示例：

```json
/api/builder/v1/taxonomy/8/word/81537e265d9f11ee8d03005056baa089/level
{
    "parent": "root"
}
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 是否必须 | 字段说明         |
| :--- | :------- | :------- | :------- | :--------------- |
| 1    | res      | string   | 是       | 返回的结果字符串 |

响应示例：

```json
{
    "res": "success"
}
```

### 4.8、获取术语库的顶级词

```
GET  /api/builder/v1/taxonomy/{taxonomy_id}/top_word
```

请求参数：

| 序号 | 字段名称    | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明 |
| ---- | :---------- | :------- | :------- | :------- | ---- | :------- |
| 1    | taxonomy_id | int      | path     | 是       |      | 术语库id |

请求示例：

```
/api/builder/v1/taxonomy/1/top_word
```

响应参数：

| 序号 | 字段名称 | 字段类型      | 字段说明     |
| :--- | :------- | :------------ | :----------- |
| 1    | id       | string        | 词的id       |
| 2    | label    | list <object> | 词的基本信息 |
| 3    | level    | object        | 层级信息     |

| 序号 | 字段名称     | 字段类型     | 字段说明     |
| :--- | :----------- | :----------- | :----------- |
| 1    | name         | string       | 翻译         |
| 2    | description  | string       | 描述         |
| 3    | synonym      | list<string> | 同义词       |
| 4    | language     | string       | 语言         |
| 5    | parent_count | int          | 父级词的个数 |
| 6    | child_count  | int          | 子级词的个数 |

响应示例：

```json
{
    "res": [
        {
            "id": "9287401c64be11eebc6e005056baa089",
            "label": [
                {
                    "description": "",
                    "language": "zh_CN",
                    "name": "词1_1",
                    "synonym": []
                }
            ],
            "level": {
                "child_count": 1,
                "parent_count": 0
            }
        },
        {
            "id": "word1",
            "label": [
                {
                    "description": "",
                    "language": "zh_CN",
                    "name": "name",
                    "synonym": []
                }
            ],
            "level": {
                "child_count": 0,
                "parent_count": 0
            }
        }
    ]
}
```

### 4.9、获取词的下级

```
GET  /api/builder/v1/taxonomy/{taxonomy_id}/word/{word_ids}/subclass
```

请求参数：

| 序号 | 字段名称    | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明                    |
| ---- | :---------- | :------- | :------- | :------- | ---- | :-------------------------- |
| 1    | taxonomy_id | int      | path     | 是       |      | 术语库id                    |
| 2    | word_ids    | string   | path     | 是       |      | 词的id列表，例：word1,word2 |

请求示例：

```
/api/builder/v1/taxonomy/1/word/9287401c64be11eebc6e005056baa089,9287401c64be11eebc6e005056baa089/subclass
```

响应参数：

| 序号 | 字段名称  | 字段类型     | 字段说明           |
| :--- | :-------- | :----------- | :----------------- |
| 1    | {word_id} | list<object> | 输入参数中的词的id |

| 序号 | 字段名称 | 字段类型      | 字段说明     |
| :--- | :------- | :------------ | :----------- |
| 1    | id       | string        | 词的id       |
| 2    | label    | list <object> | 词的基本信息 |
| 3    | level    | object        | 层级信息     |

| 序号 | 字段名称     | 字段类型     | 字段说明     |
| :--- | :----------- | :----------- | :----------- |
| 1    | name         | string       | 翻译         |
| 2    | description  | string       | 描述         |
| 3    | synonym      | list<string> | 同义词       |
| 4    | language     | string       | 语言         |
| 5    | parent_count | int          | 父级词的个数 |
| 6    | child_count  | int          | 子级词的个数 |

响应示例：

```json
{
    "res": {
        "9287401c64be11eebc6e005056baa089": [
            {
                "id": "a79ee03664be11eeb65e005056baa089",
                "label": [
                    {
                        "description": "",
                        "language": "zh_CN",
                        "name": "词2",
                        "synonym": []
                    }
                ],
                "level": {
                    "child_count": 0,
                    "parent_count": 1
                }
            }
        ]
    }
}
```

### 4.10、搜索词

```
GET  /api/builder/v1/taxonomy/{taxonomy_id}/search_word
```

请求参数：

| 序号 | 字段名称    | 字段类型 | 字段位置 | 是否必须 | 长度 | 字段说明                                                     |
| ---- | :---------- | :------- | :------- | :------- | ---- | :----------------------------------------------------------- |
| 1    | taxonomy_id | int      | path     | 是       |      | 术语库id                                                     |
| 2    | query       | string   | query    | 是       | 100  | 搜索词                                                       |
| 3    | field       | string   | query    | 是       | 20   | 搜索范围，可选值： name_and_synonym：搜索所有语言的翻译和同义词    displayed：搜索展示出来的名称 |
| 4    | language    | string   | query    | 否       | 10   | 语言。当field为displayed时，该字段为必传                     |

请求示例：

```
/api/builder/v1/taxonomy/1/search_word?query=xxx&field=name_and_synonym
```

响应参数：

| 序号 | 字段名称 | 字段类型      | 字段说明     |
| :--- | :------- | :------------ | :----------- |
| 1    | id       | string        | 词的id       |
| 2    | label    | list <object> | 词的基本信息 |
| 3    | level    | object        | 层级信息     |

| 序号 | 字段名称     | 字段类型     | 字段说明     |
| :--- | :----------- | :----------- | :----------- |
| 1    | name         | string       | 翻译         |
| 2    | description  | string       | 描述         |
| 3    | synonym      | list<string> | 同义词       |
| 4    | language     | string       | 语言         |
| 5    | parent_count | int          | 父级词的个数 |
| 6    | child_count  | int          | 子级词的个数 |

响应示例：

```json
{
    "res": [
        {
            "id": "word1",
            "label": [
                {
                    "description": "",
                    "language": "zh_CN",
                    "name": "name",
                    "synonym": []
                }
            ],
            "level": {
                "child_count": 0,
                "parent_count": 0
            }
        },
        {
            "id": "a79ee03664be11eeb65e005056baa089",
            "label": [
                {
                    "description": "",
                    "language": "zh_CN",
                    "name": "词2",
                    "synonym": [
                        "name"
                    ]
                }
            ],
            "level": {
                "child_count": 0,
                "parent_count": 1
            }
        }
    ]
}
```

### 4.11、定位词的层级

```
GET  /api/builder/v1/taxonomy/{taxonomy_id}/locate_word
```

请求参数：

| 序号 | 字段名称    | 字段类型 | 字段位置 | 是否必须 | 长度 | 字段说明 |
| ---- | :---------- | :------- | :------- | :------- | ---- | :------- |
| 1    | taxonomy_id | int      | path     | 是       |      | 术语库id |
| 2    | word_id     | string   | query    | 是       | 50   | 词的id   |

请求示例：

```
/api/builder/v1/taxonomy/1/locate_word?word_id=xxx
```

响应参数：

| 序号 | 字段名称 | 字段类型     | 字段说明                       |
| ---- | :------- | :----------- | :----------------------------- |
| 1    | res      | list<string> | 从root至目标词的路径上的词的id |

响应示例：

```json
{
    "res": [
        "root",
        "9287401c64be11eebc6e005056baa089",
        "a79ee03664be11eeb65e005056baa089"
    ]
}
```

### 4.12、删除词

```
POST  /api/builder/v1/taxonomy/{taxonomy_id}/delete_word
```

请求参数：

| 序号 | 字段名称      | 字段类型     | 参数位置 | 是否必须 | 长度 | 字段说明                                                     |
| ---- | :------------ | :----------- | :------- | :------- | ---- | :----------------------------------------------------------- |
| 1    | taxonomy_id   | int          | path     | 是       |      | 术语库id                                                     |
| 2    | word_ids      | list<string> | body     | 是       |      | 词的id列表，例：word1,word2                                  |
| 3    | delete_option | string       | body     | 是       |      | 删除选项：<br />delete_one：仅删除此术语，其下术语将孤立在术语列表中<br />delete_sub：删除此术语及其下所有术语 |

请求示例：

```json
/api/builder/v1/taxonomy/1/delete_word
{
    "word_ids": ["d1397e3c65a111ee9097005056baa089", "9287401c64be11eebc6e005056baa089"],
    "delete_option": "delete_sub"
}
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 字段说明         |
| ---- | :------- | :------- | :--------------- |
| 1    | res      | string   | 返回的结果字符串 |

响应示例：

```json
{
    "res": "success"
}
```

### 4.13、编辑自定义关系

```
POST  /api/builder/v1/taxonomy/{taxonomy_id}/custom_relation/edit
```

请求参数：

| 序号 | 字段名称    | 字段类型     | 参数位置 | 是否必须 | 长度 | 字段说明           |
| ---- | :---------- | :----------- | :------- | :------- | ---- | :----------------- |
| 1    | taxonomy_id | int          | path     | 是       |      | 术语库id           |
| 2    | change_list | list<object> | body     | 是       |      | 对自定义关系的操作 |

| 序号 | 字段名称 | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明                                  |
| :--- | :------- | :------- | :------- | :------- | ---- | :---------------------------------------- |
| 1    | action   | string   | body     | 是       |      | add：新增   remove：删除                  |
| 2    | id       | int      | body     | 否       |      | 自定义关系id，action为remove时必传        |
| 3    | name     | string   | body     | 否       | 100  | 新增自定义关系的名字，action为add时，必传 |

请求示例：

```json
/api/builder/v1/taxonomy/1/custom_relation/edit
{
    "change_list": [
        {
            "action": "add",
            "name": "关系5"
        },
        {
            "action": "remove",
            "id": 3
        }
    ]
}
```

响应参数：

| 序号 | 字段名称   | 字段类型  | 字段说明                                                     |
| :--- | :--------- | :-------- | :----------------------------------------------------------- |
| 1    | new_ids    | object    | 成功添加的自定义关系的id（key为自定义关系名称，value为新增或已存在的的id） |
| 2    | remove_ids | list<int> | 成功删除的自定义关系的id列表                                 |

响应示例：

```json
{
    "res": {
        "new_ids": {
            "关系5": 5
        },
        "remove_ids": [3]
    }
}
```

### 4.14、获取自定义关系列表

```
GET  /api/builder/v1/taxonomy/{taxonomy_id}/custom_relation/list
```

请求参数：

| 序号 | 字段名称    | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明 |
| ---- | :---------- | :------- | :------- | :------- | ---- | :------- |
| 1    | taxonomy_id | int      | path     | 是       |      | 术语库id |

请求示例：

```
/api/builder/v1/taxonomy/1/custom_relation/list
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 字段说明       |
| :--- | :------- | :------- | :------------- |
| 1    | id       | integer  | 自定义关系id   |
| 2    | name     | string   | 自定义关系名称 |

响应示例：

```json
{
    "res": [
        {
            "id": 4,
            "name": "关系4"
        },
        {
            "id": 5,
            "name": "关系5"
        }
    ]
}
```

### 4.15、新建词的属性

```
POST  /api/builder/v1/taxonomy/{taxonomy_id}/relation/ispartof/add
```

请求参数：

| 序号 | 字段名称         | 字段类型     | 参数位置 | 是否必须 | 长度 | 字段说明       |
| ---- | :--------------- | :----------- | :------- | :------- | ---- | :------------- |
| 1    | taxonomy_id      | int          | path     | 是       |      | 术语库id       |
| 2    | start_word_id    | string       | body     | 是       |      | 起点词的id     |
| 3    | end_word_id_list | list<string> | body     | 是       |      | 终点词的id列表 |

请求示例：

```json
/api/builder/v1/taxonomy/1/relation/ispartof/add
{
    "start_word_id": "e0621447680011eeb70f005056baa089",
    "end_word_id_list": ["98a489f168c311eea463005056baa089"]
}
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 是否必须 | 字段说明         |
| ---- | :------- | :------- | :------- | :--------------- |
| 1    | res      | string   | 是       | 返回的结果字符串 |

响应示例：

```json
{
    "res": "success"
}
```

### 4.16、删除词的属性

```
POST  /api/builder/v1/taxonomy/{taxonomy_id}/relation/ispartof/delete
```

请求参数：

| 序号 | 字段名称         | 字段类型     | 参数位置 | 是否必须 | 长度 | 字段说明       |
| ---- | :--------------- | :----------- | :------- | :------- | ---- | :------------- |
| 1    | taxonomy_id      | int          | path     | 是       |      | 术语库id       |
| 2    | start_word_id    | string       | body     | 是       |      | 起点词的id     |
| 3    | end_word_id_list | list<string> | body     | 是       |      | 终点词的id列表 |

请求示例：

```json
/api/builder/v1/taxonomy/1/relation/ispartof/delete
{
    "start_word_id": "e0621447680011eeb70f005056baa089",
    "end_word_id_list": ["98a489f168c311eea463005056baa089"]
}
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 是否必须 | 字段说明         |
| ---- | :------- | :------- | :------- | :--------------- |
| 1    | res      | string   | 是       | 返回的结果字符串 |

响应示例：

```json
{
    "res": "success"
}
```

### 4.17、编辑词的自定义关系

```
POST  /api/builder/v1/taxonomy/{taxonomy_id}/relation/custom/edit
```

请求参数：

| 序号 | 字段名称                | 字段类型     | 参数位置 | 是否必须 | 长度 | 字段说明             |
| ---- | :---------------------- | :----------- | :------- | :------- | ---- | :------------------- |
| 1    | taxonomy_id             | int          | path     | 是       |      | 术语库id             |
| 2    | relation_id             | int          | body     | 是       |      | 自定义关系id         |
| 3    | start_word_id           | string       | body     | 是       |      | 起点词的id           |
| 4    | add_end_word_id_list    | list<string> | body     | 是       |      | 新增的终点词的id列表 |
| 5    | remove_end_word_id_list | list<string> | body     | 是       |      | 删除的终点词的id列表 |

请求示例：

```json
/api/builder/v1/taxonomy/1/relation/custom/edit
{
    "relation_id": 4,
    "start_word_id": "e0621447680011eeb70f005056baa089",
    "add_end_word_id_list": ["98a489f168c311eea463005056baa089"],
    "remove_end_word_id_list": []
}
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 是否必须 | 字段说明         |
| ---- | :------- | :------- | :------- | :--------------- |
| 1    | res      | string   | 是       | 返回的结果字符串 |

响应示例：

```json
{
    "res": "success"
}
```

### 4.18、删除词的自定义关系

```
POST  /api/builder/v1/taxonomy/{taxonomy_id}/relation/custom/delete
```

请求参数：

| 序号 | 字段名称     | 字段类型  | 参数位置 | 是否必须 | 长度 | 字段说明         |
| ---- | :----------- | :-------- | :------- | :------- | ---- | :--------------- |
| 1    | taxonomy_id  | int       | path     | 是       |      | 术语库id         |
| 2    | relation_ids | list<int> | body     | 是       |      | 自定义关系id列表 |
| 3    | word_id      | string    | body     | 是       |      | 词的id           |

请求示例：

```json
/api/builder/v1/taxonomy/1/relation/custom/delete
{
    "relation_ids": [4],
    "word_id": "e0621447680011eeb70f005056baa089"
}
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 是否必须 | 字段说明         |
| ---- | :------- | :------- | :------- | :--------------- |
| 1    | res      | string   | 是       | 返回的结果字符串 |

响应示例：

```json
{
    "res": "success"
}
```

### 4.19、获取词的属性列表

```
GET  /api/builder/v1/taxonomy/{taxonomy_id}/relation/ispartof/list
```

请求参数：

| 序号 | 字段名称    | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明                                |
| ---- | :---------- | :------- | :------- | :------- | ---- | :-------------------------------------- |
| 1    | taxonomy_id | int      | path     | 是       |      | 术语库id                                |
| 2    | word_id     | string   | query    | 是       |      | 词的id                                  |
| 3    | query       | string   | query    | 否       |      | 搜索关键词                              |
| 4    | language    | string   | query    | 否       |      | 语言，当传了参数query时，该参数为必传。 |

请求示例：

```
/api/builder/v1/taxonomy/1/relation/ispartof/list?word_id=e0621447680011eeb70f005056baa089&query=xxx&language=zh_CN
```

响应参数：

| 序号 | 字段名称 | 字段类型     | 字段说明     |
| :--- | :------- | :----------- | :----------- |
| 1    | id       | string       | 词的id       |
| 2    | label    | list<object> | 词的基本信息 |

| 序号 | 字段名称    | 字段类型     | 字段说明 |
| :--- | :---------- | :----------- | :------- |
| 1    | name        | string       | 翻译     |
| 2    | description | string       | 描述     |
| 3    | synonym     | list<string> | 同义词   |
| 4    | language    | string       | 语言     |

响应示例：

```json
{
    "res": [
        {
            "id": "98a489f168c311eea463005056baa089",
            "label": [
                {
                    "description": "",
                    "language": "zh_CN",
                    "name": "词2",
                    "synonym": []
                }
            ]
        }
    ]
}
```

### 4.20、获取词的自定义关系列表

```
GET  /api/builder/v1/taxonomy/{taxonomy_id}/relation/custom/list
```

请求参数：

| 序号 | 字段名称    | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明                                |
| ---- | :---------- | :------- | :------- | :------- | ---- | :-------------------------------------- |
| 1    | taxonomy_id | int      | path     | 是       |      | 术语库id                                |
| 2    | word_id     | string   | query    | 是       |      | 词的id                                  |
| 3    | query       | string   | query    | 否       |      | 搜索关键词                              |
| 4    | language    | string   | query    | 否       |      | 语言，当传了参数query时，该参数为必传。 |

请求示例：

```
/api/builder/v1/taxonomy/1/relation/custom/list?word_id=e0621447680011eeb70f005056baa089&query=xxx&language=zh_CN
```

响应参数：

| 序号 | 字段名称      | 字段类型     | 字段说明         |
| :--- | :------------ | :----------- | :--------------- |
| 1    | relation_id   | int          | 自定义关系id     |
| 2    | relation_name | string       | 自定义关系名称   |
| 3    | words         | list<object> | 有关系的词的列表 |

| 序号 | 字段名称 | 字段类型     | 字段说明     |
| :--- | :------- | :----------- | :----------- |
| 1    | id       | string       | 词的id       |
| 2    | label    | list<object> | 词的基本信息 |

| 序号 | 字段名称    | 字段类型     | 字段说明 |
| :--- | :---------- | :----------- | :------- |
| 1    | name        | string       | 翻译     |
| 2    | description | string       | 描述     |
| 3    | synonym     | list<string> | 同义词   |
| 4    | language    | string       | 语言     |

响应示例：

```json
{
    "res": [
        {
            "relation_id": 4,
            "relation_name": "关系4",
            "words": [
                {
                    "id": "98a489f168c311eea463005056baa089",
                    "label": [
                        {
                            "description": "",
                            "language": "zh_CN",
                            "name": "词2",
                            "synonym": []
                        }
                    ]
                }
            ]
        }
    ]
}
```

### 4.21、根据词的id获取词的信息

```
GET  /api/builder/v1/taxonomy/{taxonomy_id}/word/{word_ids}
```

请求参数：

| 序号 | 字段名称    | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明                    |
| ---- | :---------- | :------- | :------- | :------- | ---- | :-------------------------- |
| 1    | taxonomy_id | string   | path     | 是       |      | 术语库id                    |
| 2    | word_ids    | string   | path     | 是       |      | 词的id列表，例：word1,word2 |

请求示例：

```
/api/builder/v1/taxonomy/1/word/1,2
```

响应参数：

| 序号 | 字段名称 | 字段类型     | 字段说明     |
| :--- | :------- | :----------- | :----------- |
| 1    | id       | string       | 词的id       |
| 2    | label    | list<object> | 词的基本信息 |
| 3    | level    | object       | 层级信息     |

| 序号 | 字段名称    | 字段类型     | 字段说明 |
| :--- | :---------- | :----------- | :------- |
| 1    | name        | string       | 翻译     |
| 2    | description | string       | 描述     |
| 3    | synonym     | list<string> | 同义词   |
| 4    | language    | string       | 语言     |

| 序号 | 字段名称     | 字段类型 | 字段说明     |
| :--- | :----------- | :------- | :----------- |
| 1    | parent_count | int      | 父级词的个数 |
| 2    | child_count  | int      | 子级词的个数 |

响应示例：

```json
{
    "res": {
        "98a489f168c311eea463005056baa089": {
            "label": [
                {
                    "description": "",
                    "language": "zh_CN",
                    "name": "词2",
                    "synonym": []
                }
            ],
            "level": {
                "child_count": 0,
                "parent_count": 0
            }
        }
    }
}
```

## 5、词库管理

### 5.1、新建词库接口

注意：该接口为form-data传参

```
POST  /api/builder/v1/lexicon/add
```

请求参数：

| 序号 | 字段名称     | 字段类型 | 字段位置 | 是否必须 | 长度 | 字段说明       |
| :--- | :----------- | :------- | -------- | :------- | ---- | :------------- |
| 1    | name         | string   | body     | 是       | 50   | 词库名称       |
| 2    | description  | string   | body     | 是       | 150  | 词库描述       |
| 3    | file         | file     | body     | 否       |      | 上传的词库文件 |
| 4    | knowledge_id | int      | body     | 是       |      | 知识网络id     |

请求示例：

```
"name": "ck"
"description": "ck description"
"knowledge_id": 1
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 字段说明         |
| ---- | :------- | :------- | :--------------- |
| 1    | res      | int      | 新建成功的词库id |

响应示例：

```json
{
   "res": 3
}
```

### 5.2、根据模板创建词库接口

```
POST  /api/builder/v1/lexicon/add/template_lexicon
```

请求参数：

| 序号 | 字段名称    | 字段类型 | 字段位置 | 是否必须 | 长度 | 字段说明                                                     |
| :--- | :---------- | :------- | -------- | :------- | ---- | :----------------------------------------------------------- |
| 1    | name        | string   | body     | 是       | 50   | 词库名称                                                     |
| 2    | description | string   | body     | 是       | 150  | 词库描述                                                     |
| 3    | knw_id      | int      | body     | 是       |      | 知识网络id                                                   |
| 4    | mode        | string   | body     | 是       | 50   | 模板类型std（近义词词库）custom（os分词词库）entity_link（实体链接词库） |

请求示例：

```json
{
    "name":"ck",
    "description":"ck description",
    "knw_id":1,
    "mode":"std",
}
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 字段说明     |
| ---- | :------- | :------- | :----------- |
| 1    | res      | int      | 新建的词库id |

响应示例：

```json
{
    "res": 11
}
```

### 5.3、执行词库构建任务接口

```
POST  /api/builder/v1/lexicon/build
```

请求参数：

| 序号 | 字段名称   | 字段类型 | 字段位置 | 是否必须 | 长度 | 字段说明 |
| :--- | :--------- | :------- | -------- | :------- | ---- | :------- |
| 1    | lexicon_id | int      | body     | 是       |      | 词库id   |

请求示例：

```json
{
    "id": 1
}
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 字段说明     |
| ---- | :------- | :------- | :----------- |
| 1    | res      | string   | celery任务id |

响应示例：

```json
{
    "res": "xxxxxxxxxxxxxxxxx"
}
```

### 5.4、获取词库列表接口

```
GET  /api/builder/v1/lexicon/page
```

请求参数：

| 序号 | 字段名称     | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明                                                     |
| :--- | :----------- | :------- | -------- | :------- | ---- | :----------------------------------------------------------- |
| 1    | knowledge_id | int      | query    | 是       |      | 知识网络id                                                   |
| 2    | page         | int      | query    | 是       |      | 第几页                                                       |
| 3    | size         | int      | query    | 是       |      | 一页多少个                                                   |
| 4    | order        | string   | query    | 是       | 5    | 排序方式：正序（asc）逆序（desc）                            |
| 5    | rule         | string   | query    | 是       | 11   | 排序规则：按创建时间（create_time）按最终修改时间（update_time）按名称（name） |
| 6    | word         | string   | query    | 否       | 50   | 搜索词                                                       |

请求示例：

```
/api/builder/v1/lexicon/page?knowledge_id=1&page=1&size=20&order=asc&rule=name
```

响应参数：

| 序号 | 字段名称 | 字段类型     | 是否必须 | 字段说明     |
| :--- | :------- | :----------- | :------- | :----------- |
| 1    | count    | int          | 是       | 词库总个数   |
| 2    | df       | list<object> | 是       | 词库具体信息 |

响应示例：

```json
{
    "count": 3,
    "df":[
            {"id": 1, "name": "ciku1", "columns":[], "status": "success", "error_info": ""},
            {"id": 2, "name": "ciku2", "columns":["a", "b"], "status": "failed", "error_info": "xxxxxx"},
            {"id": 3, "name": "ciku3", "columns":[], "status": "running", "error_info": ""}
    ]
}
```

### 5.5、根据id获取词库信息接口

```
GET  /api/builder/v1/lexicon/detail
```

请求参数：

| 序号 | 字段名称 | 字段类型 | 字段位置 | 是否必须 | 长度 | 字段说明 |
| :--- | :------- | :------- | -------- | :------- | ---- | :------- |
| 1    | id       | int      | query    | 是       |      | 词库id   |
| 2    | page     | int      | query    | 是       |      | 页数     |
| 3    | size     | int      | query    | 是       |      | 每页数量 |

请求示例：

```
/api/builder/v1/lexicon/detail?id=1&page=1&size=20
```

响应参数：

| 序号 | 字段名称     | 字段类型     | 字段说明           |
| :--- | :----------- | :----------- | :----------------- |
| 1    | id           | int          | 词库id             |
| 2    | lexicon_name | string       | 词库名称           |
| 3    | description  | string       | 词库描述           |
| 4    | create_by    | string       | 创建人             |
| 5    | update_by    | string       | 最终操作人         |
| 6    | create_time  | string       | 创建时间           |
| 7    | update_time  | string       | 最终操作时间       |
| 8    | count        | int          | 词汇总数           |
| 9    | word_info    | list<object> | 词汇信息           |
| 10   | columns      | list<string> | 词库列名           |
| 11   | status       | string       | 状态               |
| 12   | error_info   | string       | 错误信息           |
| 13   | mode         | string       | 词库构建使用的模板 |
| 14   | extract_info | object       | 词库构建抽取信息   |

响应示例：

```json
{
    "id": 1,
    "lexicon_name": "ciku1",
    "description": "xxxxxxxxxxxx",
    "create_by": "xiaoming",
    "update_by": "xiaohong",
    "create_time": "2022-07-25 13:47:46",
    "update_time": "2022-07-25 13:47:46",
    "count": 500,
    "columns": ["word", "homoionym"],
    "status": "success",
    "error_info": "",
    "word_info": [
                {"word": "开心", "homoionym": "高兴"},
                {"word": "不开心", "homoionym": "不高兴"},
                {"word": "不开心", "homoionym": "伤心"}
    ],
    "mode": "std",
    "extract_info": {
        "lexicon": [
            {"id": 5, "name":"词库1", "columns": ["c1", "c2"], "separator": ["", "@"]},
            {"id": 6, "name":"词库2", "columns": ["x1", "x2"], "separator": ["", "@"]}
        ],
        "graph": [
            {
                "id": 1,
                "name": "测试图谱"
                "entities": [
                    {"name": "e1", "prop": ["prop1", "prop2"], "separator": ["", "@"], "std_prop":"prop3"},
                    {"name": "e2", "prop": ["prop3", "prop4"], "separator": ["", "|"], "std_prop":"prop3"}
                ]
            }
        ]
    }
}
```

### 5.6、词库内导入词汇接口

```
POST  /api/builder/v1/lexicon/words/import
```

请求参数：

| 序号 | 字段名称 | 字段类型 | 字段位置 | 是否必须 | 长度 | 字段说明                        |
| :--- | :------- | :------- | -------- | :------- | ---- | :------------------------------ |
| 1    | id       | int      | body     | 是       |      | 词库id                          |
| 2    | file     | list     | body     | 是       |      | 导入的词库文件                  |
| 3    | mode     | string   | body     | 是       | 50   | add(新增数据)replace (全部替换) |

响应参数：

| 序号 | 字段名称 | 字段类型 | 字段说明 |
| ---- | :------- | :------- | :------- |
| 1    | res      | string   | success  |

响应示例：

```json
{
   "res": "success"
}
```

### 5.7、词库中新增词汇接口

```
POST  /api/builder/v1/lexicon/words/add
```

请求参数：

| 序号 | 字段名称  | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明 |
| :--- | :-------- | :------- | -------- | :------- | ---- | :------- |
| 1    | id        | int      | body     | 是       |      | 词库id   |
| 2    | word_info | object   | body     | 是       |      | 信息     |

请求示例：

```json
{
    "id": 1,
    "word_info": {"word": "难过", "homoionym": "悲伤"}
}
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 是否必须 | 字段说明 |
| :--- | :------- | :------- | :------- | :------- |
| 1    | res      | string   | 是       | 新增成功 |

响应示例：

```json
{
    "res": "success"
}
```

### 5.8、词库中搜索词汇接口

```
POST  /api/builder/v1/lexicon/words/search
```

请求参数：

| 序号 | 字段名称 | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明       |
| :--- | :------- | :------- | -------- | :------- | ---- | :------------- |
| 1    | id       | int      | body     | 是       |      | 词库id         |
| 2    | word     | string   | body     | 是       | 50   | 词汇内容       |
| 3    | page     | int      | body     | 是       |      | 页码           |
| 4    | size     | int      | body     | 是       |      | 一页的词汇数量 |

请求示例：

```json
{
    "id": 1,
    "page": 2,
    "size" : 10,
    "word": "开心"
}
```

响应参数：

| 序号 | 字段名称 | 字段类型     | 是否必须 | 字段说明     |
| :--- | :------- | :----------- | :------- | :----------- |
| 1    | count    | int          | 是       | 词库总个数   |
| 2    | df       | list<object> | 是       | 词库具体信息 |

响应示例：

```json
{
    "res": {
        "count": 3,
        "df": [
            {"word": "开心", "homoionym": "高兴"},
            {"word": "开心", "homoionym": "兴奋"},
            {"word": "开心", "homoionym": "激动"},
    ]
}
```

### 5.9、词库中编辑词汇接口

```
POST  /api/builder/v1/lexicon/words/edit
```

请求参数：

| 序号 | 字段名称 | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明         |
| :--- | :------- | :------- | -------- | :------- | ---- | :--------------- |
| 1    | id       | int      | body     | 是       |      | 词库id           |
| 2    | old_info | object   | body     | 是       |      | 原始词汇内容     |
| 3    | new_info | object   | body     | 是       |      | 修改后的词汇内容 |

请求示例：

```json
{
    "id": 1,
    "old_info": {"word": "伤心", "homoionym": "不伤心"},
    "new_info": {"word": "伤心", "homoionym": "难过"},
}
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 是否必须 | 字段说明 |
| :--- | :------- | :------- | :------- | :------- |
| 1    | res      | string   | 是       | 编辑成功 |

响应示例：

```json
{
    "res": "success"
}
```

### 5.10、词库中删除词汇接口

```
POST  /api/builder/v1/lexicon/words/delete
```

请求参数：

| 序号 | 字段名称       | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明         |
| :--- | :------------- | :------- | -------- | :------- | ---- | :--------------- |
| 1    | id             | int      | body     | 是       |      | 词库id           |
| 2    | word_info_list | list     | body     | 是       |      | 要删除的词汇信息 |

请求示例：

```json
{
    "id": 1,
    "word_info_list": [
        {"word": "伤心", "homoionym": "难过"},
        {"word": "悲伤", "homoionym": "难过"}
    ]
}
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 是否必须 | 字段说明 |
| :--- | :------- | :------- | :------- | :------- |
| 1    | res      | string   | 是       | 删除成功 |

响应示例：

```json
{
    "res": "success"
}
```

### 5.11、编辑词库接口

```
POST  /api/builder/v1/lexicon/edit
```

请求参数：

如果模板为实体链接词库或近义词库，则 extract_info 中没有 lexicon

如果模板为近义词库，graph中entities中的prop，第一个为标准词属性，且separator中第一个元素应为空

| 序号 | 字段名称     | 字段类型 | 字段位置 | 是否必须 | 长度 | 字段说明         |
| :--- | :----------- | :------- | -------- | :------- | ---- | :--------------- |
| 1    | id           | int      | body     | 是       |      | 词库id           |
| 2    | name         | string   | body     | 是       | 50   | 词库名称         |
| 3    | description  | string   | body     | 是       | 150  | 词库描述         |
| 4    | extract_info | object   | body     | 否       |      | 构建词库抽取信息 |

请求示例：

```json
{
    "id": 1,
    "name": "test",
    "description": "",
    "extract_info": {
        "lexicon": [
            {"id": 5, "columns": ["c1", "c2"], "separator": ["", "@"]},
            {"id": 6, "columns": ["x1", "x2"], "separator": ["", "@"]}
        ],
        "graph": [
            {
                "id": 1,
                "entities": [
                    {"name": "e1", "prop": ["prop1", "prop2"], "separator": ["", "@"], "std_prop": "prop1"},
                    {"name": "e2", "prop": ["prop3", "prop4"], "separator": ["", "|"], "std_prop"："prop3"}
                ]
            }
        ]
    }
}
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 字段说明 |
| ---- | :------- | :------- | :------- |
| 1    | res      | string   | success  |

响应示例：

```json
{
    "res": "success"
}
```

### 5.12、删除词库接口

```
POST  /api/builder/v1/lexicon/delete
```

请求参数：

| 序号 | 字段名称 | 字段类型  | 参数位置 | 是否必须 | 长度 | 字段说明   |
| :--- | :------- | :-------- | -------- | :------- | ---- | :--------- |
| 1    | id_list  | list<int> | body     | 是       |      | 词库id列表 |

请求示例：

```json
{
    "id_list": [1,2,3]
}
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 是否必须 | 字段说明 |
| :--- | :------- | :------- | :------- | :------- |
| 1    | res      | string   | 是       | 删除成功 |

响应示例：

```json
{
    "res": "success"
}
```

### 5.13、词库导出接口

```
POST  /api/builder/v1/lexicon/export
```

请求参数：

| 序号 | 字段名称 | 字段类型  | 参数位置 | 是否必须 | 长度 | 字段说明   |
| :--- | :------- | :-------- | -------- | :------- | ---- | :--------- |
| 1    | id_list  | list<int> | body     | 是       |      | 词库id列表 |

请求示例：

```json
{
    "id_list": [1,2,3]
}
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 是否必须 | 字段说明 |
| :--- | :------- | :------- | :------- | :------- |
| 1    | res      | string   | 是       | 导出成功 |

响应示例：

```json
{
    "res": "success"
}
```

### 5.14、词库模板下载接口

```
POST  /api/builder/v1/lexicon/template
```

请求参数：

| 序号 | 字段名称 | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明 |
| :--- | :------- | :------- | -------- | :------- | ---- | :------- |
|      |          |          |          |          |      |          |

请求示例：

```json

```

响应参数：

| 序号 | 字段名称 | 字段类型 | 是否必须 | 字段说明 |
| :--- | :------- | :------- | :------- | :------- |
|      |          |          |          |          |

响应示例：

```json

```

## 6、数据源管理

### 6.1、测试连接

```
POST  /api/builder/v1/ds/test_connect
```

请求参数：

| 序号 | 字段名称     | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明                                                     |
| :--- | :----------- | :------- | -------- | :------- | ---- | :----------------------------------------------------------- |
| 1    | ds_id        | int      | body     | 是       |      | 数据源ID                                                     |
| 2    | data_source  | string   | body     | 是       | 20   | 数据源类型（mysql、hive、sqlserver、kingbasees、postgresql、clickhouse等） |
| 3    | ds_address   | string   | body     | 是       | 256  | 地址                                                         |
| 4    | ds_port      | int      | body     | 是       |      | 端口                                                         |
| 5    | ds_user      | string   | body     | 是       | 30   | 用户名                                                       |
| 6    | ds_password  | string   | body     | 是       | 500  | 加密后的用户密码                                             |
| 7    | ds_path      | string   | body     | 是       |      | 数据源路径                                                   |
| 8    | vhost        | string   | body     | 是       | 50   | RabbitMQ特殊字段                                             |
| 9    | queue        | string   | body     | 是       | 50   | RabbitMQ特殊字段                                             |
| 10   | connect_type | string   | body     | 是       | 20   | odbc开关（"": 直连    "odbc": odbc连接）                     |

请求示例：

```
{
	"ds_id": 0,
    "data_source": "mysql",
    "ds_address": "10.2.196.58",
    "ds_port":3306,
    "ds_user": "root",
    "ds_password": "TmV3UGFzczEyMyE=",
    "ds_path": "test",
    "vhost": "",
    "queue": "",
    "connect_type": ""
}
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 字段说明 |
| ---- | :------- | :------- | :------- |
| 1    | res      | string   | 测试成功 |

响应示例：

```json
{
   "res": "success"
}
```

### 6.2、获取数据源列表接口

```
GET  /api/builder/v1/ds/page
```

请求参数：

| 序号 | 字段名称 | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明                                                     |
| :--- | :------- | :------- | -------- | :------- | ---- | :----------------------------------------------------------- |
| 1    | page     | int      | query    | 是       |      | 页号                                                         |
| 2    | size     | int      | query    | 是       |      | 每页个数                                                     |
| 3    | knw_id   | int      | query    | 是       |      | 知识网络ID                                                   |
| 4    | order    | string   | query    | 是       | 10   | 排序方式 （ascend：时间正序，旧时间在上   descend：时间倒序，新时间在上） |
| 5    | filter   | string   | query    | 否       | 20   | structured                                                   |
| 6    | ds_type  | string   | query    | 否       | 20   | 数据源类型（mysql、hive、sqlserver、kingbasees、postgresql、clickhouse等） |

请求示例：

```
/api/builder/v1/ds/page?page=1&size=20&knw_id=1&order=ascend&filter=structured&ds_type=mysql
```

响应参数：

| 序号 | 字段名称 | 字段类型     | 字段说明       |
| :--- | :------- | :----------- | :------------- |
| 1    | count    | int          | 数据源总个数   |
| 2    | df       | list<object> | 数据源具体信息 |

| 序号 | 字段名称     | 字段类型 | 字段说明   |
| ---- | :----------- | :------- | :--------- |
| 1    | create_time  | string   | 创建时间   |
| 2    | create_by    | string   | 创建用户   |
| 3    | data_type    | string   | 数据类型   |
| 4    | data_source  | string   | 数据源类型 |
| 5    | ds_address   | string   | 地址       |
| 6    | ds_password  | string   | 密码       |
| 7    | ds_path      | string   | 数据库路径 |
| 8    | ds_port      | int      | 端口       |
| 9    | ds_user      | string   | 用户名     |
| 10   | ds_name      | string   | 数据源名称 |
| 11   | extract_type | string   | 抽取类型   |
| 12   | id           | int      | 数据源id   |
| 13   | knw_id       | int      | 知识网络id |
| 14   | update_time  | string   | 修改时间   |
| 15   | update_by    | string   | 修改用户   |
| 16   | connect_type | string   | 连接方式   |

响应示例：

```json
{
    "res": {
        "count": 1,
        "df": [{
            "create_time": "2023-02-06 04:19:55",
            "create_by": "11c9a837-82e7-45c7-9533-00309a1dba5d",
            "data_type": "structured",
            "data_source": "mysql",                  
            "ds_address": "10.4.107.112",
            "ds_password": "ZWlzb28uY29tMTIz",
            "ds_path": "anydata",
            "ds_port": 3320,
            "ds_user": "root",
            "ds_name": "\u672c\u673amysql",
            "extract_type": "standardExtraction",
            "id": 1,
            "knw_id": 1,
            "update_time": "2023-02-06 04:19:55",
            "update_by": "11c9a837-82e7-45c7-9533-00309a1dba5d",
            "connect_type":"odbc"                   
        }]
    }
}
```

### 6.3、新建数据源接口

```
POST  /api/builder/v1/ds/add
```

请求参数：

| 序号 | 字段名称     | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明                                                     |
| :--- | :----------- | :------- | -------- | :------- | ---- | :----------------------------------------------------------- |
| 1    | ds_name      | string   | body     | 是       | 50   | 数据源名称                                                   |
| 2    | data_source  | string   | body     | 是       | 20   | 数据源类型（mysql、hive、sqlserver、kingbasees、postgresql、clickhouse等） |
| 3    | data_type    | string   | body     | 是       | 20   | 数据类型（structured、unstructured）                         |
| 4    | ds_address   | string   | body     | 是       | 256  | IP                                                           |
| 5    | ds_port      | int      | body     | 是       |      | 端口                                                         |
| 6    | ds_user      | string   | body     | 是       | 30   | 用户                                                         |
| 7    | ds_password  | string   | body     | 是       | 500  | 密码                                                         |
| 8    | ds_path      | string   | body     | 是       |      | 路径                                                         |
| 9    | extract_type | string   | body     | 是       | 20   | 抽取类型                                                     |
| 10   | knw_id       | int      | body     | 是       |      | 知识网络ID                                                   |
| 11   | connect_type | string   | body     | 是       | 20   | 传"": 直连方式    传"odbc": odbc连接                         |

请求示例：

```json
{
    "ds_name": "222",
    "data_source": "mysql",
    "data_type": "unstructured",
    "ds_address": "10.2.196.58",
    "ds_port": 3306,
    "ds_user": "root",
    "ds_password": "MQ==",
    "ds_path": "test",
    "extract_type": "standardExtraction",
    "knw_id": 1,
	"connect_type": ""
}
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 字段说明           |
| ---- | :------- | :------- | :----------------- |
| 1    | ds_id    | int      | 新建成功的数据源id |

响应示例：

```json
{
   "res": "添加成功",
   "ds_id": 1
}
```

### 6.4、编辑数据源接口

```
POST  /api/builder/v1/ds/edit/{ds_id}
```

请求参数：

| 序号 | 字段名称     | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明                                                     |
| :--- | :----------- | :------- | -------- | :------- | ---- | :----------------------------------------------------------- |
| 1    | ds_id        | int      | path     | 是       |      | 数据源id                                                     |
| 2    | ds_name      | string   | body     | 是       | 50   | 数据源名称                                                   |
| 3    | data_source  | string   | body     | 是       | 20   | 数据源类型（mysql、hive、sqlserver、kingbasees、postgresql、clickhouse等） |
| 4    | ds_user      | string   | body     | 是       | 30   | 用户                                                         |
| 5    | ds_password  | string   | body     | 是       | 500  | 密码                                                         |
| 6    | connect_type | string   | body     | 是       | 20   | 传"": 直连方式    传"odbc": odbc连接                         |

请求示例：

```json
{
    "ds_name": "222",
    "data_source": "mysql",
    "ds_user": "root",
    "ds_password": "MQ==",
	"connect_type": ""
}
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 字段说明 |
| ---- | :------- | :------- | :------- |
| 1    | res      | string   |          |

响应示例：

```json
{
   "res": "更新成功"
}
```

### 6.5、删除数据源接口

```
DELETE  /api/builder/v1/ds/delete
```

请求参数：

| 序号 | 字段名称 | 字段类型  | 参数位置 | 是否必须 | 长度 | 字段说明   |
| :--- | :------- | :-------- | -------- | :------- | ---- | :--------- |
| 1    | ds_ids   | list<int> | body     | 是       |      | 数据源的id |

请求示例：

```json
{  
    "ds_ids":[1,2]   
}
```

响应参数：

| 序号 | 字段名称 | 字段类型  | 字段说明   |
| ---- | :------- | :-------- | :--------- |
| 1    | ds_ids   | list<int> | 数据源的id |

响应示例：

```json
{
    "ds_ids":[1,2],
    "res": "success delete dsid  [1,2]  success"
}
```

### 6.6、根据id获取数据源信息

```
GET  /api/builder/v1/ds/detail
```

请求参数：

| 序号 | 字段名称 | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明   |
| :--- | :------- | :------- | -------- | :------- | ---- | :--------- |
| 1    | ds_id    | int      | query    | 是       |      | 数据源的id |

请求示例：

```
/api/builder/v1/ds/detail?ds_id=1
```

响应参数：

| 序号 | 字段名称    | 字段类型 | 字段说明   |
| :--- | :---------- | :------- | :--------- |
| 1    | ds_name     | string   | 数据源名称 |
| 2    | data_source | string   | 数据源类型 |
| 3    | ds_address  | string   | IP         |
| 4    | ds_port     | int      | 端口       |
| 5    | ds_user     | string   | 用户       |
| 6    | ds_password | string   | 密码       |
| 7    | ds_path     | string   | 路径       |

响应示例：

```json
{
    "res": {
        {
            "ds_name": "222",
            "data_source": "mysql",
            "ds_address": "10.2.196.58",
            "ds_port": 3306,
            "ds_user": "root",
            "ds_password": "MQ==",
            "ds_path": "test"
		}
    }
}
```

### 6.7、模糊查询

```
GET  /api/builder/v1/ds/search
```

请求参数：

| 序号 | 字段名称 | 字段类型 | 字段位置 | 是否必须 | 长度 | 字段说明                   |
| :--- | :------- | :------- | -------- | :------- | ---- | :------------------------- |
| 1    | page     | int      | query    | 是       |      | 页码                       |
| 2    | size     | int      | query    | 是       |      | 大小                       |
| 3    | ds_name  | string   | query    | 是       | 50   | 数据源名称                 |
| 4    | order    | string   | query    | 是       | 10   | 排序方式（ascend descend） |
| 5    | knw_id   | int      | query    | 是       |      | 知识网络id                 |

请求示例：

```
/api/builder/v1/ds/search?page=1&size=1&ds_name=k&order=ascend&knw_id=1
```

响应参数：

| 序号 | 字段名称 | 字段类型     | 字段说明       |
| :--- | :------- | :----------- | :------------- |
| 1    | count    | int          | 数据源总个数   |
| 2    | df       | list<object> | 数据源具体信息 |

| 序号 | 字段名称     | 字段类型 | 字段说明   |
| ---- | :----------- | :------- | :--------- |
| 1    | create_time  | string   | 创建时间   |
| 2    | create_by    | string   | 创建用户   |
| 3    | data_type    | string   | 数据类型   |
| 4    | data_source  | string   | 数据源类型 |
| 5    | ds_address   | string   | 地址       |
| 6    | ds_password  | string   | 密码       |
| 7    | ds_path      | string   | 数据库路径 |
| 8    | ds_port      | int      | 端口       |
| 9    | ds_user      | string   | 用户名     |
| 10   | ds_name      | string   | 数据源名称 |
| 11   | extract_type | string   | 抽取类型   |
| 12   | id           | int      | 数据源id   |
| 13   | knw_id       | int      | 知识网络id |
| 14   | update_time  | string   | 修改时间   |
| 15   | update_by    | string   | 修改用户   |
| 16   | connect_type | string   | 连接方式   |

响应示例：

```json
{
    "res": {
        "count": 1,
        "df": [{
            "create_time": "2023-02-06 04:19:55",
            "create_by": "11c9a837-82e7-45c7-9533-00309a1dba5d",
            "data_type": "structured",
            "data_source": "mysql",                  
            "ds_address": "10.4.107.112",
            "ds_password": "ZWlzb28uY29tMTIz",
            "ds_path": "anydata",
            "ds_port": 3320,
            "ds_user": "root",
            "ds_name": "\u672c\u673amysql",
            "extract_type": "standardExtraction",
            "id": 1,
            "knw_id": 1,
            "update_time": "2023-02-06 04:19:55",
            "update_by": "11c9a837-82e7-45c7-9533-00309a1dba5d",
            "connect_type":"odbc"                   
        }]
    }
}
```

### 6.8、数据源复制接口

```
POST  /api/builder/v1/ds/copy/{ds_id}
```

请求参数：

| 序号 | 字段名称     | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明                                                     |
| :--- | :----------- | :------- | -------- | :------- | ---- | :----------------------------------------------------------- |
| 1    | ds_id        | int      | path     | 是       |      | 数据源id                                                     |
| 2    | ds_name      | string   | body     | 是       | 50   | 数据源名称                                                   |
| 3    | data_source  | string   | body     | 是       | 20   | 数据源类型（mysql、hive、sqlserver、kingbasees、postgresql、clickhouse等） |
| 4    | data_type    | string   | body     | 是       | 20   | 数据类型（structured、unstructured）                         |
| 5    | ds_address   | string   | body     | 是       | 256  | IP                                                           |
| 6    | ds_port      | int      | body     | 是       |      | 端口                                                         |
| 7    | ds_user      | string   | body     | 是       | 30   | 用户                                                         |
| 8    | ds_password  | string   | body     | 是       | 500  | 密码                                                         |
| 9    | ds_path      | string   | body     | 是       |      | 路径                                                         |
| 10   | extract_type | string   | body     | 是       | 20   | 抽取类型                                                     |
| 11   | knw_id       | int      | body     | 是       |      | 知识网络ID                                                   |
| 12   | connect_type | string   | body     | 是       | 20   | 传"": 直连方式       传"odbc": odbc连接                      |

请求示例：

```json
{
    "ds_name": "222",
    "data_source": "mysql",
    "data_type": "unstructured",
    "ds_address": "10.2.196.58",
    "ds_port": 3306,
    "ds_user": "root",
    "ds_password": "MQ==",
    "ds_path": "test",
    "extract_type": "standardExtraction",
    "knw_id": 1,
	"connect_type": ""
}
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 字段说明   |
| ---- | :------- | :------- | :--------- |
| 1    | ds_id    | int      | 数据源的id |

响应示例：

```json
{
    "ds_id":1,
    "res": "添加成功"
}
```

### 6.9、获取hive表分区名列表

```
GET  /api/builder/v1/ds/hive/partition/list
```

请求参数：

| 序号 | 字段名称   | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明 |
| :--- | :--------- | :------- | -------- | :------- | ---- | :------- |
| 1    | ds_id      | int      | query    | 是       |      | 数据源id |
| 2    | table_name | string   | query    | 是       |      | 表名     |

请求示例：

```
/api/builder/v1/ds/hive/partition/list?ds_id=1&table_name=xxxx
```

响应参数：

| 序号 | 字段名称 | 字段类型     | 字段说明 |
| ---- | :------- | :----------- | :------- |
| 1    | res      | list<string> | 返回结果 |

响应示例：

```json
// 分区表
{
    "res": ["dt", "step"]
}
 
// 非分区表
{
    "res": []
}
```

### 6.10、预览分区表达式

```
GET  /api/builder/v1/ds/hive/partition/case
```

请求参数：

| 序号 | 字段名称   | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明   |
| :--- | :--------- | :------- | -------- | :------- | ---- | :--------- |
| 1    | expression | string   | query    | 是       |      | 分区表达式 |

请求示例：

```
/api/builder/v1/ds/hive/partition/case?expression=$date_format($hour_add($date_add($current_timestamp(),-1),-1),'YYYY-MM-dd:HH')
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 字段说明         |
| ---- | :------- | :------- | :--------------- |
| 1    | res      | string   | 返回的结果字符串 |

响应示例：

```json
{
    "res": "2023-04-23:13"
}
```

### 6.11、检查分区配置接口

```
POST  /api/builder/v1/ds/hive/partition/check_info
```

请求参数：

| 序号 | 字段名称        | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明 |
| :--- | :-------------- | :------- | :------- | :------- | ---- | :------- |
| 1    | ds_id           | int      | body     | 是       |      | 数据源id |
| 2    | table_name      | string   | body     | 是       |      | 表信息   |
| 1    | partition_infos | object   | body     | 是       |      | 分区配置 |

请求示例：

```json
{
    "ds_id": 1,
    "table_name": "table1",
    "partition_infos": {
        "date": "$date_format($hour_add($date_add($current_timestamp(),-1),-1),'YYYY-MM-dd')",
        "hour": "$date_format($hour_add($date_add($current_timestamp(),-1),-1),'HH')"
    }
}
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 字段说明         |
| ---- | :------- | :------- | :--------------- |
| 1    | res      | string   | 返回的结果字符串 |

响应示例：

```json
// 分区配置正确
{
    "res":{
        "partition_name_error": [],             // 错误的分区字段
        "partition_expression_error": []        // 分区字段错误的
    }
}
 
// 分区配置有误
{
    "res":{
        "partition_name_error": ["date"],       // 表示没有date分区字段
        "partition_expression_error": ["hour"]  // 表示hour分区字段变量有误
    }
}
```

### 6.12、获取表的各字段及其字段类型接口

```
GET  /api/builder/v1/ds/table_field
```

请求参数：

| 序号 | 字段名称    | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明                                                     |
| :--- | :---------- | :------- | -------- | :------- | ---- | :----------------------------------------------------------- |
| 1    | ds_id       | int      | query    | 是       |      | 数据源id                                                     |
| 2    | data_source | string   | query    | 是       | 20   | 数据源类型（mysql、hive、sqlserver、kingbasees、postgresql、clickhouse等） |
| 3    | table_name  | string   | query    | 是       |      | 表名                                                         |
| 4    | model_name  | string   | query    | 否       |      | 模式名 （数据源类型为SQLserver、KingbaseES、postgreSQL时填写） |

请求示例：

```
/api/builder/v1/ds/table_field?ds_id=1&data_source=mysql&table_name=xxx
```

响应参数：

| 序号 | 字段名称 | 字段类型 | 字段说明   |
| ---- | :------- | :------- | :--------- |
| 1    | fields   | object   | 字段及类型 |

响应示例：

```json
{
    "res": {
        "fields": {
            "aaa": "Int32",
            "bbb": "Float32",
            ...
        }
    }
}
```

### 6.13、领域数据sql查询

```
POST  /api/builder/v1/ds/sql
```

请求参数：

| 序号 | 字段名称 | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明    |
| :--- | :------- | :------- | -------- | :------- | ---- | :---------- |
| 1    | ds_id    | int      | body     | 是       |      | 数据源id    |
| 2    | sql      | string   | body     | 是       |      | sql查询语句 |

请求示例：

```json
{
	"ds_id": 1,
	"sql": "xxx"
}
```

响应参数：

| 序号 | 字段名称 | 字段类型   | 字段说明 |
| ---- | :------- | :--------- | :------- |
| 1    | content  | list<list> | 查询结果 |

响应示例：

```json
{
    "res": {
        "content": [
            ["id", "name", "age"],  //字段名称
            [1, "tom", 11],
            [2, "jerry", 22],
            [3, "paul", 33]
        ]
    }
}
```

### 6.14、领域数据表预览

```
GET  /api/builder/v1/ds/preview_data
```

请求参数：

| 序号 | 字段名称    | 字段类型 | 参数位置 | 是否必须 | 长度 | 字段说明                                                     |
| :--- | :---------- | :------- | -------- | :------- | ---- | :----------------------------------------------------------- |
| 1    | ds_id       | int      | query    | 是       |      | 数据源id                                                     |
| 2    | data_source | string   | query    | 是       | 20   | 数据源类型（mysql、hive、sqlserver、kingbasees、postgresql、clickhouse等） |
| 3    | name        | string   | query    | 是       |      | 表名                                                         |
| 4    | model_name  | string   | query    | 否       |      | 模式名 （数据源类型为SQLserver、KingbaseES、postgreSQL时填写） |

请求示例：

```
/api/builder/v1/ds/table_field?ds_id=1&data_source=mysql&name=xxx
```

响应参数：

| 序号 | 字段名称 | 字段类型   | 是否必须 | 字段说明 |
| :--- | :------- | :--------- | :------- | :------- |
| 1    | content  | list<list> | 是       | 预览结果 |

响应示例：

```json
{
    "res": {
        "content": [
            ["id", "name", "age"],  //字段名称
            [1, "tom", 11],
            [2, "jerry", 22],
            [3, "paul", 33]
        ]
    }
}
```
