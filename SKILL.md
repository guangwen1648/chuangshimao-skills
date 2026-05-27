---
name: chuangshimao-skills
description: AI image generation skill using GPT-Image-2 model. Generate images from text descriptions with support for multiple aspect ratios. Features include text-to-image, image editing, and style transfer capabilities.
---

# chuangshimao-skills

A versatile AI image generation skill powered by GPT-Image-2 model.

## Service Endpoint

**API Base URL**: `https://api.chuangshimao.com/api/v1`

## Capabilities

- **Text-to-Image**: Generate images from text descriptions
- **Multiple Ratios**: Support for 15 aspect ratios (1:1, 3:2, 16:9, 9:16, etc.)
- **High Resolution**: 1K resolution output
- **Chinese Support**: Full Chinese prompt support
- **Fast Generation**: Results in ~30 seconds

## Pricing

**¥0.1 per image** (pay-per-use, no monthly fee)

No free credits. No subscription. Pay only for what you use.

## Quick Start

### 1. Get Your API Key

1. Visit **https://chuangshimao.com** and register an account
2. Navigate to **Personal Center → API Key Management**
3. Generate a new API key (starts with `sk-img2-`)

### 2. Configure the Skill

```bash
# Set your API key as environment variable
export IMG2_API_KEY="sk-img2-your-key-here"
```

### 3. Generate Your First Image

```json
{
  "prompt": "A beautiful sunset over the ocean, digital art style",
  "size": "16:9",
  "resolution": "1k"
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
| size | string | No | Aspect ratio (default: 1:1) |
| resolution | string | No | Output resolution (default: 1k) |
| image_url | string | No | Reference image URL for editing |

### Supported Aspect Ratios

| Ratio | Description |
|-------|-------------|
| 1:1 | Square |
| 3:2 | Landscape |
| 2:3 | Portrait |
| 4:3 | Standard landscape |
| 3:4 | Standard portrait |
| 16:9 | Cinematic |
| 9:16 | MobileStory |
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
  "image_url": "https://your-cdn.com/image.png",
  "prompt": "A beautiful sunset over the ocean",
  "size": "16:9",
  "resolution": "1k",
  "time": "25.3s"
}
```

## Usage Examples

### Example 1: Generate a Landscape Image

```json
{
  "prompt": "A majestic mountain range at sunrise, photorealistic, 4K",
  "size": "16:9",
  "resolution": "1k"
}
```

### Example 2: Generate a Portrait

```json
{
  "prompt": "A professional portrait photo of a businesswoman, studio lighting",
  "size": "3:4",
  "resolution": "1k"
}
```

### Example 3: Social Media Cover

```json
{
  "prompt": "Modern tech startup office, team collaboration, bright and airy",
  "size": "16:9",
  "resolution": "1k"
}
```

## Image Editing

To edit an existing image, provide the `image_url` parameter:

```json
{
  "prompt": "Transform this photo into an anime style",
  "size": "1:1",
  "image_url": "https://example.com/photo.jpg"
}
```

## Best Practices

### Writing Good Prompts

1. **Be specific**: Include details about subject, setting, style
2. **Mention art style**: "digital art", "photorealistic", "oil painting"
3. **Include lighting**: "natural light", "studio lighting", "golden hour"
4. **Add atmosphere**: "mysterious", "cheerful", "dramatic"

### Good Prompt Examples

```
"一只橘色的猫坐在窗台上,阳光透过窗户洒落,宫崎骏动画风格,温暖色调"
↓
English: "An orange cat sitting on a windowsill, sunlight streaming through, Studio Ghibli animation style, warm tones"

"未来城市夜景,霓虹灯闪烁,赛博朋克风格,下雨的街道反射灯光"
↓
English: "Futuristic city night scene, neon lights glowing, cyberpunk style, rainy street reflecting lights"
```

### Choosing the Right Ratio

| Use Case | Recommended Ratio |
|----------|------------------|
| Social media feed | 1:1 or 4:5 |
| Twitter/X post | 16:9 |
| Instagram story | 9:16 |
| Blog header | 16:9 or 21:9 |
| Product showcase | 3:4 or 4:5 |

## Error Handling

| Error Code | Message | Solution |
|------------|---------|----------|
| 400 | prompt不能为空 | Provide a prompt |
| 401 | API Key无效或已过期 | Check your API key |
| 402 | 余额不足，请充值 | Add credits to your account |
| 429 | 请求过于频繁，请稍后再试 | Wait and retry |
| 500 | 生成失败，请稍后重试 | Contact support |

## Rate Limits

- **Concurrent requests**: 2 per API key
- **Requests per minute**: 10 per API key
- **Maximum prompt length**: 2000 characters

## FAQ

**Q: How long does generation take?**
A: Typically 25-60 seconds depending on complexity.

**Q: Can I use generated images commercially?**
A: Yes, all generated images can be used commercially.

**Q: What payment methods are supported?**
A: WeChat Pay, Alipay, and major credit cards.

**Q: Is there a free trial?**
A: New users receive ¥10 in free credits (100 images).

## Support

For issues or questions:
- Check the documentation
- Contact support team

---

*This skill is provided as-is. Usage subject to terms of service.*