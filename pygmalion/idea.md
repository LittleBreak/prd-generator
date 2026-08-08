# Pygmalion - AI 简笔画生成精美图片

## 产品愿景

大多数人没有绘画功底，但也会希望将一些天马行空的想法变成现实，将简单的线稿变成一副精美的画作。

Pygmalion 是一个移动端优先的 H5 应用，用户可以通过简笔画板绘制草图、涂抹色块，选择预设风格并输入文字描述，一键让 AI 将涂鸦变成精美的画作。

---

## 核心用户流程

```
打开应用 → 选择画风/风格 → 进入画板绘制草图
→ 输入文字描述（可选）→ 点击生成 → 等待 AI 生成 → 预览最终图 → 保存到相册
```

### 详细流程

1. **首页**：展示预设风格卡片，用户选择一个风格进入画板
2. **画板页**：使用画笔、形状、橡皮擦等工具绘制草图，并可涂抹色块表达颜色意图
3. **描述输入**：画板下方或弹窗输入 prompt 文字描述（可选），进一步说明想要的效果
4. **生成等待**：点击"生成"按钮，展示 loading 动画，等待 AI 返回结果
5. **结果预览**：全屏展示生成的图片，提供"保存到相册"和"重新生成"操作
6. **不满意可返回画板调整后重新生成**

---

## MVP 功能清单

### P0 - 核心功能

| 功能模块 | 说明 |
|---------|------|
| **风格选择** | 提供 4 种预设风格：动漫/卡通、水彩/油画、像素风、写实/摄影；用户也可自由输入 prompt 微调 |
| **Canvas 画板** | 基于 Fabric.js 实现，支持触摸绘画，移动端手势适配 |
| **画笔工具** | 可调粗细和颜色的自由画笔，用于线稿绘制 |
| **橡皮擦** | 可调大小的擦除工具 |
| **色块涂抹** | 选择颜色后粗略涂抹区域，表达颜色意图（如天空涂蓝色块）|
| **形状工具** | 矩形、圆形、三角形等基础几何形状快速绘制 |
| **撤销/重做** | 操作历史的撤回和恢复 |
| **Prompt 输入** | 文字输入框，用户可描述想要的画面细节 |
| **AI 生成** | 将画板内容（导出为图片）+ 风格 + prompt 发送到后端，调用 Google Gemini API (Nano Banana) 生成 512x512 图片 |
| **结果预览** | 全屏展示生成结果 |
| **保存到相册** | 将生成图片下载/保存到用户设备相册 |


---

## 核心技术方案

### 整体架构

采用 **Next.js 全栈方案**，前后端统一在一个项目中，通过 Route Handlers 实现 API 层，Vercel 一键部署。

```
┌──────────────────────────────────────────────────┐
│               Next.js (App Router)                │
│                                                   │
│  ┌──────────────────── 页面层 ──────────────────┐ │
│  │  /             风格选择页                      │ │
│  │  /canvas       画板页 (Fabric.js, client only)│ │
│  │  /preview      结果预览页                      │ │
│  └───────────────────────────────────────────────┘ │
│                                                   │
│  ┌──────────────── API 层 (Route Handlers) ─────┐ │
│  │  /api/generate   AI 生成接口（代理 + 限额）    │ │
│  └──────┬────────────────────────────────────────┘ │
└─────────┼────────────────────────────────────────┘
          │ API Call
┌─────────┴───────────────────────────────────────┐
│          Google Gemini API (Nano Banana)           │
│                                                   │
│   模型：gemini-2.5-flash-image (快速)              │
│         gemini-3-pro-image-preview (高质量)        │
│                                                   │
│   核心能力：                                        │
│   - 图像编辑（输入草图 + prompt → 生成精美图片）      │
│   - 多轮对话式迭代编辑                               │
│   - 多参考图输入（最多 14 张）                       │
│   - 多种输出分辨率和宽高比                           │
└───────────────────────────────────────────────────┘
```

### 技术栈

| 技术 | 选型 | 说明 |
|------|------|------|
| 全栈框架 | **Next.js 14+ (App Router)** | React 全栈框架，前后端统一，自带路由、API 层、SSR 能力 |
| Canvas | **Fabric.js** | 成熟的对象化 Canvas 库，内置图形对象、事件系统、序列化能力，适合画板场景。需 `dynamic import` + `ssr: false` 客户端加载 |
| 状态管理 | **Zustand** | 轻量级，管理画板状态、风格选择、生成状态等 |
| 样式 | **Tailwind CSS** | Next.js 内置支持，移动端适配方便 |
| 移动端适配 | **postcss-px-to-viewport** | px 自动转 vw/vh，适配不同屏幕 |
| API 层 | **Route Handlers** | Next.js 内置，同源调用无跨域问题，服务端隐藏 API Key |
| 部署 | **Vercel** | Next.js 原生支持，Serverless 架构，零运维。注意 Serverless Function 超时限制（免费版 10s，Pro 60s） |
| 语言 | **TypeScript** | 全栈类型安全，前后端共享类型定义 |

### AI 生成核心流程

```
1. 前端：Fabric.js canvas.toDataURL() 导出画板内容为 PNG base64
2. 前端：将 {image_base64, style, prompt} 发送到后端 /api/generate
3. 后端：校验每日额度
4. 后端：组装 Gemini API 请求
         - 将用户草图作为输入图片（base64 编码）
         - 根据用户选择的风格，注入对应的风格 prompt 前缀
         - 合并用户自定义 prompt
         - 构造指令如 "Transform this sketch into a [style] artwork. [user_prompt]"
5. 后端：调用 Gemini API（Nano Banana），等待生成完成
6. 后端：解析响应，提取生成的图片 base64 返回前端
7. 前端：展示生成结果，提供保存操作
```

### AI API 方案：Google Gemini (Nano Banana)

| 项目 | 说明 |
|------|------|
| **模型（快速）** | `gemini-2.5-flash-image` — 速度优先，适合日常生成，MVP 首选 |
| **模型（高质量）** | `gemini-3-pro-image-preview` — 支持 Thinking 推理，高保真输出，文字渲染能力强 |
| **核心能力** | 图像编辑：输入图片 + 文字 prompt → 生成新图片。天然支持"草图 + 描述 → 精美图片"的工作流 |
| **输入格式** | base64 编码的 PNG/JPEG + 文字 prompt |
| **输出格式** | base64 编码的图片（inline_data） |
| **输出分辨率** | 支持 1K / 2K / 4K，支持多种宽高比（1:1, 3:4, 9:16 等） |
| **多轮编辑** | 支持对话式多轮迭代，用户可对生成结果继续调整（后续迭代可用） |
| **参考图** | 单次请求最多 14 张参考图，可实现主体一致性 |
| **SDK** | `@google/genai` (Node.js) |
| **认证** | API Key（`GEMINI_API_KEY` 环境变量，服务端持有） |
| **水印** | 所有生成图片含 SynthID 数字水印；免费/Pro 账户有可见水印，Ultra 无可见水印 |

#### MVP 模型策略

- 默认使用 `gemini-2.5-flash-image`（快速、成本低）
- 后续可提供"高质量生成"选项，切换为 `gemini-3-pro-image-preview`

#### 调用示例（服务端 Route Handler）

```typescript
import { GoogleGenAI } from "@google/genai";

const ai = new GoogleGenAI({ apiKey: process.env.GEMINI_API_KEY });

const response = await ai.models.generateContent({
  model: "gemini-2.5-flash-image",
  contents: [
    {
      parts: [
        { inlineData: { mimeType: "image/png", data: sketchBase64 } },
        { text: `Transform this sketch into a ${style} artwork. ${userPrompt}` },
      ],
    },
  ],
  config: {
    responseModalities: ["image", "text"],
  },
});

// 提取生成的图片
const imagePart = response.candidates[0].content.parts.find(
  (part) => part.inlineData
);
const generatedImageBase64 = imagePart.inlineData.data;
```

### 关键技术点

1. **草图引导生成**：Gemini 的图像编辑能力支持"输入图片 + 文字指令 → 生成新图片"，用户的草图和色块会被模型理解为构图和颜色意图的参考
2. **色块意图识别**：用户涂抹的色块会被 Gemini 自然理解为颜色分布意图——模型会参考输入图的颜色和空间布局
3. **风格 Prompt 工程**：每种预设风格对应一套精心调校的 prompt 模板，如动漫风格包含 `anime style, cel shading, vibrant colors, ...`，与用户 prompt 拼接后发送给 Gemini
4. **移动端画板体验**：Fabric.js 需要处理 touch 事件、双指缩放、防误触等移动端特有的交互问题
5. **生成耗时处理**：Gemini 图像生成通常需要数秒，前端需要友好的 loading 状态和超时处理
6. **网络可达性**：Gemini API 为海外服务，需确认部署环境的网络可达性（Vercel 海外节点可直连）
