---
name: chuangshimao-skills
description: 基于 GPT-Image-2 模型的 AI 图像生成技能。只需提供文字描述和图片比例即可生成图片。支持15种常用比例。
---

# chuangshimao-skills

基于 GPT-Image-2 模型的 AI 图像生成技能。

## 服务地址

**API 基础地址**: `https://api.chuangshimao.com/api/v1`

## 功能特性

- **文生图**：输入文字描述，生成精美图片
- **15种比例**：支持 1:1、16:9、9:16 等常用比例
- **中文支持**：完美支持中文提示词
- **极速生成**：约 60 秒出图

## 收费标准

**按量付费：¥0.1/张**

不收月费，不设套餐，用多少付多少。

## 快速开始

### 第一步：获取 API Key

1. 访问 **https://chuangshimao.com** 注册账号
2. 注册成功后，API Key 在个人中心自动生成（以 `sk-img2-` 开头）
3. 无需手动创建，直接复制使用

### 第二步：生成图片

```json
{
  "prompt": "一只橘色的猫坐在窗台上晒太阳，宫崎骏动画风格",
  "size": "16:9"
}
```

## API 文档

### 请求地址

```
POST https://api.chuangshimao.com/api/v1/generate
```

### 请求头

```
Authorization: Bearer YOUR_API_KEY
Content-Type: application/json
```

### 请求参数

| 参数 | 类型 | 必填 | 说明 |
|------|------|------|------|
| prompt | string | 是 | 图片描述（支持中文） |
| size | string | 否 | 图片比例，默认 "1:1" |

### 支持的图片比例

| 比例 | 说明 |
|------|------|
| 1:1 | 正方形 |
| 3:2 | 横图 |
| 2:3 | 竖图 |
| 4:3 | 标准横图 |
| 3:4 | 标准竖图 |
| 16:9 | 电影宽屏 |
| 9:16 | 手机竖屏 |
| 2:1 | 超宽横图 |
| 1:2 | 超窄竖图 |
| 3:1 | 横版Banner |
| 1:3 | 竖版Banner |
| 21:9 | 电影级超宽屏 |
| 9:21 | 超长竖图 |
| 5:4 | 经典画框 |
| 4:5 | Instagram风格 |

### 响应示例

```json
{
  "code": 0,
  "image_url": "https://cdn.example.com/image.png",
  "prompt": "一只橘色的猫坐在窗台上",
  "size": "16:9",
  "time": "52.3s"
}
```

## 使用示例

### 示例一：生成风景图

```json
{
  "prompt": "日出时分的雪山，风景摄影，4K高清",
  "size": "16:9"
}
```

### 示例二：生成头像

```json
{
  "prompt": "一只橘色的猫坐在窗台上,宫崎骏动画风格",
  "size": "1:1"
}
```

### 示例三：生成人物肖像

```json
{
  "prompt": "一位优雅的女性商人肖像，专业摄影棚灯光",
  "size": "3:4"
}
```

## 错误处理

| 错误码 | 错误信息 | 解决方案 |
|--------|----------|----------|
| 400 | prompt不能为空 | 请提供图片描述 |
| 401 | API Key无效或已过期 | 检查 API Key 是否正确 |
| 402 | 余额不足，请充值 | 去充值页面充值 |
| 429 | 请求过于频繁，请稍后再试 | 稍等片刻后重试 |
| 500 | 生成失败，请稍后重试 | 联系客服处理 |

## 代码示例

### cURL

```bash
curl -X POST https://api.chuangshimao.com/api/v1/generate \
  -H 'Authorization: Bearer YOUR_API_KEY' \
  -H 'Content-Type: application/json' \
  -d '{
    "prompt": "一只橘猫坐在窗台上看夕阳，水彩画风格",
    "size": "16:9"
  }'
```

### Python

```python
import requests

url = 'https://api.chuangshimao.com/api/v1/generate'
payload = {
    'prompt': '一只橘猫坐在窗台上看夕阳，水彩画风格',
    'size': '16:9'
}
headers = {'Authorization': 'Bearer YOUR_API_KEY', 'Content-Type': 'application/json'}
response = requests.post(url, json=payload, headers=headers)
print(response.json())
```

### JavaScript

```javascript
const response = await fetch('https://api.chuangshimao.com/api/v1/generate', {
  method: 'POST',
  headers: {
    'Authorization': 'Bearer YOUR_API_KEY',
    'Content-Type': 'application/json'
  },
  body: JSON.stringify({
    prompt: '一只橘猫坐在窗台上看夕阳，水彩画风格',
    size: '16:9'
  })
});
const data = await response.json();
console.log(data.image_url);
```

## 常见问题

**Q: 生成一张图需要多长时间？**
A: 通常 50-80 秒，具体取决于服务器负载。

**Q: 生成的图片可以商用吗？**
A: 可以，生成的图片版权归你所有，可用于商业用途。

**Q: 支持哪些支付方式？**
A: 支持微信支付、支付宝。

---

*本技能包按「原样」提供，使用即表示同意服务条款。*