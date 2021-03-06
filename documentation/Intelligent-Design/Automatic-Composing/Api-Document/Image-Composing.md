# 智能合图

## 接口描述
智能合图服务是稳定、高效、智能的图片设计工具，用户输入图片和文案素材，可快速输出图片设计结果。系统会围绕输入的内容综合运用图像识别、风格识别等技术，完成素材解析、排版、配色等复杂费力的设计步骤。

## 请求说明

### 1.请求地址
http://wkq5y1h4uomy.cn-north-1.jdcloud-api.net/api/compose/design

### 2.请求方式
POST

### 3. 请求参数
该接口采用 `FormData` 格式上传，如有不明白请参考demo！

#### （1）body请求参数
- `service`: 必传，`1` 表示自定义模板合图，`2` 表示智能多尺寸模板合图
- `template_id`: 模板 id，如果 `service` 传 `1`， 必传；如果 `service` 传 `2`， 如果传模板 id，则使用该模板 id 进行合图，如果不传，则会智能匹配三张模板进行合图
- `tag`: 模板风格，如果 `service` 传 `2`，可通过该参数指定所需风格，可选值为：
  - `1`: 简约中性
  - `2`: 清新淡雅
  - `3`: 绚丽强烈
  - `4`: 炫酷新潮
  - `5`: 神秘硬朗
  - `6`: 未来硬朗
  - `7`: 粉嫩柔美
  - `8`: 活泼喜庆
- `images`: 可选，商品图片，如果需要传多张图片，设置多个 `images` field 即可。如果不传则使用默认商品图
- `texts`: 可选，文案，传 JSON 字符串，如 `["文案1","文案2"]`。如果不传则使用默认文案
- `sizes`: 需要输出的尺寸，传 JSON 字符串，如 `[{"width": 100, "height": 100}]`, 如果 `service` 传 `2`，该参数则必传，否则不传，**最多传 10 个尺寸**。

### 4. 请求示例
Request：

```http
POST /api/compose-image HTTP/1.1
Host: http://wkq5y1h4uomy.cn-north-1.jdcloud-api.net/
Content-Type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW


Content-Disposition: form-data; name="images"; filename="/Users/zhushijie/Documents/test-psd-800x600.psd

------WebKitFormBoundary7MA4YWxkTrZu0gW--
Content-Disposition: form-data; name="texts"

["文案1","文案2"]
------WebKitFormBoundary7MA4YWxkTrZu0gW--
Content-Disposition: form-data; name="sizes"

[{"width": 100, "height": 100}]
------WebKitFormBoundary7MA4YWxkTrZu0gW--
Content-Disposition: form-data; name="service"

<SERVICE>
------WebKitFormBoundary7MA4YWxkTrZu0gW--
```
## 返回说明

### 1. 返回参数

#### （1）公共返回参数

|名称|类型|示例值|描述|
|---|---|---|---|
|code|string | 1001 | 参见-[系统级错误码](https://docs.jdcloud.com/cn/image-matting/error-codes) |
|msg|string | 查询成功 | 参见-[系统级错误码](https://docs.jdcloud.com/cn/image-matting/error-codes) |
|result|object | {...} | 结果 |

#### （2）业务返回参数
result参数信息

|名称|类型|示例值|描述|
|---|---|---|---|
|status|string | 0 | 返回结果，0表示成功；非0为对应错误号，参见错误码-业务级错误码|
|requestid|string | 6979e9bd79b944b49e0d6e74079d5098 | 请求id |
|message|string | success | 结果状态，成功为 success |
|result|object | {} | 处理后的对象 |

### 2. 返回示例
当 `service` 为 `1` 时，Success：

```http
HTTP/1.1 200
Content-Type: application/json

{
    "code": 10000,
    "msg": "查询成功",
    "result": {
        "image_url": "https://img30.360buyimg.com/tu/jfs/t1/80487/39/15221/177188/5dcbab45E5b7a420d/fdc002d76f4e40f0.jpg",
        "status": 0,
        "message": "OK",
        "requestId": "45d7a845-420f-450d-8460-fbddf3feafa1"
    }
}
```

当 `service` 为 `2` 时，并传 `template_id` 时，Success：

```http
HTTP/1.1 200
Content-Type: application/json

{
    "code": 10000,
    "msg": "查询成功",
    "result": {
        "images": [
            {
                "size": {
                    "width": 400,
                    "height": 300
                },
                "url": "https://img10.360buyimg.com/tu/jfs/t1/70821/38/15777/27694/5dd63c7fE3ac8c9af/173ce88476017ceb.jpg"
            }
        ],
        "status": 0,
        "message": "OK",
        "requestId": "45d7a845-420f-450d-8460-fbddf3feafa1"
    }
}
```

当 `service` 为 `2` 时，不传 `template_id` 时，Success：

```http
HTTP/1.1 200
Content-Type: application/json

{
    "code": 10000,
    "msg": "查询成功",
    "result": {
        "images": [
            // template 1
            [
                {
                    "size": {
                        "width": 400,
                        "height": 300
                    },
                    "url": "https://img10.360buyimg.com/tu/jfs/t1/70821/38/15777/27694/5dd63c7fE3ac8c9af/173ce88476017ceb.jpg"
                },
                ...
            ],
            // template 2
            [
                {
                    "size": {
                        "width": 400,
                        "height": 300
                    },
                    "url": "https://img10.360buyimg.com/tu/jfs/t1/70821/38/15777/27694/5dd63c7fE3ac8c9af/173ce88476017ceb.jpg"
                },
                ...
            ],
            // template 3
            [
                {
                    "size": {
                        "width": 400,
                        "height": 300
                    },
                    "url": "https://img10.360buyimg.com/tu/jfs/t1/70821/38/15777/27694/5dd63c7fE3ac8c9af/173ce88476017ceb.jpg"
                },
                ...
            ],
        ],
        "status": 0,
        "message": "OK",
        "requestId": "45d7a845-420f-450d-8460-fbddf3feafa1"
    }
}
```

# 获取智能设计模板列表

## 接口描述
用于查询智能合图的模板列表接口。

## 请求说明

### 1.请求地址
http://wkq5y1h4uomy.cn-north-1.jdcloud-api.net/api/intel-templates

### 2.请求方式
GET

### 3. 请求参数

#### （1）query 参数：
- `page`: 必传，第几页
- `per_page`: 必传，每页几个

### 4. 请求示例

``` http
GET /api/intel-templates HTTP/1.1
Host: http://wkq5y1h4uomy.cn-north-1.jdcloud-api.net
```

## 返回说明

Success:
```http
HTTP/1.1 200
Content-Type: application/json

{
    "data": {
        "templates": [
            {
                "id": "xxx",
                "name": "test-psd-800x600.psd",
                "thumbnail": "http://img14.360buyimg.com/tu/jfs/t1/51772/29/14975/12882/5dc138f0Edefc0f37/0a6747da912db6a8.jpg",
                "size": {
                    "height": 600,
                    "width": 800
                },
            },
            ...
        ],
        "total: 23
    }
}

```
