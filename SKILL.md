---
name: chuangshimao-skills
description: AI image generation skill using GPT-Image-2 model. Supports text-to-image, image-to-image, 15 aspect ratios, and balance query API.
---

# chuangshimao-skills

AI image generation skill powered by GPT-Image-2 model.

## Service Endpoint

**API Base URL**: `https://api.chuangshimao.com/api/v1`

## Capabilities

- **Text-to-Image**: Generate images from text descriptions
- **Image-to-Image**: Generate images from reference image + prompt
- **15 Aspect Ratios**: 1:1, 3:2, 16:9, 9:16, etc.
- **Chinese Support**: Full Chinese prompt support
- **Fast Generation**: Results in ~60 seconds
- **Balance Query**: Check account balance via API

## Pricing

**¥0.1 per image** (pay-per-use, no monthly fee)

## Quick Start

### 1. Get Your API Key

1. Visit **https://chuangshimao.com** and register an account
2. Your API Key is automatically generated after registration (starts with `sk-img2-`)
3. No manual creation needed, just copy and use

### 2. Generate an Image

```json
{
  "prompt": "A beautiful sunset over the ocean, digital art style",
  "size": "16:9"
}
```

## API Reference

### Endpoint

```
POST https://api.chuangshimao.com/api/v1/generate
```

### Headers

```
Authorization: Bearer YOUR_API_KEY
Content-Type: application/json
```

### Request Body

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| prompt | string | Yes | Image description (supports Chinese) |
| size | string | No | Aspect ratio, default "1:1" |
| image_url | string | No | Reference image URL for image-to-image mode |

### Supported Aspect Ratios

| Ratio | Description |
|-------|-------------|
| 1:1 | Square |
| 3:2 | Landscape |
| 2:3 | Portrait |
| 4:3 | Standard landscape |
| 3:4 | Standard portrait |
| 16:9 | Cinematic |
| 9:16 | Mobile story |
| 2:1 | Ultra-wide |
| 1:2 | Ultra-tall |
| 3:1 | Banner |
| 1:3 | Tall banner |
| 21:9 | Ultra-cinematic |
| 9:21 | Ultra-portrait |
| 5:4 | Classic |
| 4:5 | Instagram |

### Response

```json
{
  "code": 0,
  "image_url": "https://cdn.example.com/image.png",
  "prompt": "A beautiful sunset over the ocean",
  "size": "16:9",
  "time": "52.3s"
}
```

## Balance Query

### Endpoint

```
GET https://api.chuangshimao.com/api/v1/balance
```

### Headers

```
Authorization: Bearer YOUR_TOKEN
```

### Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| token | string | Yes | User token (obtained after login) |

### Response

```json
{
  "balance": 28.5,
  "user_id": 1
}
```

## Usage Examples

### Example: Generate a Landscape

```json
{
  "prompt": "A majestic mountain range at sunrise, photorealistic",
  "size": "16:9"
}
```

### Example: Generate a Square Image

```json
{
  "prompt": "一只橘色的猫坐在窗台上,宫崎骏动画风格",
  "size": "1:1"
}
```

### Example: Generate a Portrait

```json
{
  "prompt": "Professional portrait photo of a businesswoman, studio lighting",
  "size": "3:4"
}
```

### Example: Image-to-Image

```json
{
  "prompt": "Convert this into a cyberpunk style image",
  "size": "16:9",
  "image_url": "https://example.com/reference.jpg"
}
```

## Error Handling

| Error Code | Message | Solution |
|------------|---------|----------|
| 400 | prompt不能为空 | Provide a prompt |
| 401 | API Key无效或已过期 | Check your API key |
| 402 | 余额不足，请充值 | Add credits to your account |
| 429 | 请求过于频繁，请稍后再试 | Wait and retry |
| 500 | 生成失败，请稍后重试 | Contact support |

## Code Examples

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

## FAQ

**Q: How long does generation take?**
A: Typically 50-80 seconds depending on server load.

**Q: Can I use generated images commercially?**
A: Yes, all generated images can be used commercially.

**Q: What payment methods are supported?**
A: WeChat Pay, Alipay.

---

*This skill is provided as-is. Usage subject to terms of service.*