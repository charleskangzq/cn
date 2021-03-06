# queryRefreshTaskById


## 描述
根据taskId查询刷新预热任务

## 请求方式
GET

## 请求地址
https://cdn.jdcloud-api.com/v1/task/{taskId}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**taskId**|String|True| |域名组id|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](queryrefreshtaskbyid#result)| |
|**requestId**|String| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**task**|[RefreshTask](queryrefreshtaskbyid#refreshtask)| |
### <div id="refreshtask">RefreshTask</div>
|名称|类型|描述|
|---|---|---|
|**createDate**|String|任务创建时间,UTC时间|
|**failed**|Float|任务失败率|
|**success**|Float|任务成功率|
|**taskId**|String|刷新预热的任务id|
|**id**|Long|数据库表id|
|**retryStatus**|String|重试状态(unretry:不重试,retry:重试)|
|**taskStatus**|String|任务状态(running:执行中,success:成功,failed:失败)|
|**taskType**|String|刷新预热类型,(url:url刷新,dir:目录刷新,prefetch:预热)|
|**urlTasks**|[UrlTask[]](queryrefreshtaskbyid#urltask)|详细的任务|
### <div id="urltask">UrlTask</div>
|名称|类型|描述|
|---|---|---|
|**taskType**|String|刷新预热类型,(url:url刷新,dir:目录刷新,prefetch:预热)|
|**url**|String|刷新预热的url|
|**status**|String|任务状态(running:执行中,success:成功,failed:失败)|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**404**|NOT_FOUND|
