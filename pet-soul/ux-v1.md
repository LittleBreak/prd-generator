# PetSoul 宠灵感 - Stitch UI/UX 设计文档

## 产品概述

**产品名称：** 宠灵感 · PetSoul
**产品定位：** 基于多模态 AI 的宠物情绪解码工具
**设计风格：** 温暖治愈、活泼有趣、年轻化社交风格

---

## 全局设计规范

### 整体风格 Prompt
```
A warm and playful pet companion app. Soft pastel color palette with coral pink as primary color. Rounded corners on all elements. Friendly and approachable typography. Cute micro-interactions. Target audience: young pet owners aged 18-35.
```

### 配色方案
- **主色（Primary）：** 珊瑚粉 #FF6B6B
- **辅助色（Secondary）：** 薄荷绿 #4ECDC4
- **背景色（Background）：** 暖白 #FFF9F5
- **文字色（Text）：** 深灰 #2D3436
- **强调色（Accent）：** 阳光黄 #FFE66D

### 字体风格
```
Use a friendly rounded sans-serif font for body text. Playful hand-drawn style font for headings and pet dialogues.
```

---

## 页面设计详情

### 1. 启动页 / 欢迎页（Splash Screen）

**页面目标：** 品牌展示，情感引入

**Stitch Prompt：**
```
Splash screen for a pet mind-reading app called "PetSoul". Center a cute cat and dog illustration with thought bubbles above their heads. App name "宠灵感" in playful Chinese font below. Soft gradient background from coral pink to cream white. Minimal, warm, and inviting feel.
```

**设计要点：**
- 居中展示品牌 Logo（猫狗剪影 + 思维气泡）
- 产品名称「宠灵感」使用手写风格字体
- Slogan：「读懂主子的内心戏」
- 渐变背景：珊瑚粉 → 暖白色

---

### 2. 首页 / 拍照上传页（Home - Upload）

**页面目标：** 核心功能入口，引导用户上传宠物照片

**Stitch Prompt：**
```
Home page for a pet photo app. Large central area for photo upload with a dashed border placeholder showing a cute paw print icon. Two action buttons below: "Take Photo" with camera icon and "Choose from Album" with gallery icon. Both buttons are pill-shaped with coral pink fill. At the top, show user's pet avatar and greeting "What is your pet thinking today?". Bottom navigation bar with 4 tabs: Home, History, Profile, Settings. Warm cream background, playful and encouraging vibe.
```

**功能元素：**
| 元素 | 描述 | 交互 |
|------|------|------|
| 顶部问候语 | "今天主子在想什么？" | 静态展示 |
| 照片上传区 | 虚线边框 + 爪印图标 | 点击触发上传 |
| 拍照按钮 | 相机图标 + "拍一张" | 调起相机 |
| 相册按钮 | 图库图标 + "从相册选" | 调起相册 |
| 底部导航 | 首页/历史/档案/我的 | Tab 切换 |

**边界情况提示：**
```
Error state for home page: When photo upload fails, show a sad cat illustration with message "上传失败，请重试" and a "Retry" button in coral pink.
```

---

### 3. 人设选择页（Persona Selector）

**页面目标：** 让用户为宠物选择性格人设

**Stitch Prompt：**
```
Persona selection screen for a pet app. Display uploaded pet photo at the top (30% of screen). Below, show a horizontal scrollable row of persona cards. Each card is a rounded rectangle with an emoji icon and persona name: "高冷总裁" with sunglasses emoji, "碎碎念大妈" with chat emoji, "文艺青年" with book emoji, "热血少年" with fire emoji, "毒舌吐槽" with tongue emoji, "卑微打工人" with tired face emoji. Selected card has coral pink border and slight scale-up effect. A "Generate" button at bottom in coral pink. Clean white cards on cream background.
```

**人设卡片设计：**
| 人设名称 | 图标 | 描述标签 |
|----------|------|----------|
| 高冷总裁 | 😎 | 傲娇、冷漠、霸道 |
| 碎碎念大妈 | 💬 | 唠叨、热心、操心 |
| 文艺青年 | 📖 | 忧郁、诗意、敏感 |
| 热血少年 | 🔥 | 元气、活力、中二 |
| 毒舌吐槽 | 👅 | 犀利、幽默、毒舌 |
| 卑微打工人 | 😫 | 疲惫、无奈、社畜 |

**高级人设（付费）Prompt：**
```
Premium persona section with a subtle gold badge "VIP" on each card. Show locked personas with a small lock icon overlay: "甄嬛体", "赛博朋克", "霸总文学", "古风诗词". Cards have a slight frosted glass effect to indicate premium status.
```

---

### 4. AI 生成等待页（Loading State）

**页面目标：** 缓解用户等待焦虑，增加趣味性

**Stitch Prompt：**
```
Loading screen for AI content generation. Show the uploaded pet photo in the center with animated thought bubbles appearing above. A playful loading text below: "正在读取主子的脑电波..." with animated dots. Subtle particle effects or floating paw prints in the background. Progress indicator as a cute cat tail swinging animation. Soft cream background with coral pink accents.
```

**加载文案轮播：**
1. "正在读取主子的脑电波..."
2. "解码猫语中..."
3. "主子正在组织语言..."
4. "翻译内心戏中..."

---

### 5. 生成结果页（Result Display）

**页面目标：** 展示 AI 生成的内心戏，支持选择和操作

**Stitch Prompt：**
```
Result screen showing generated pet inner thoughts. Pet photo displayed at top (40% of screen) with a speech bubble overlay containing generated text. Below the main display, show 3 horizontal dots indicating 3 versions - user can swipe left/right to switch between versions. Current version number shown as "1/3". Action buttons at bottom: "Regenerate" with refresh icon (outline style), "Create Meme" with image icon (filled coral pink), "Share" with share icon (filled mint green). Add a small "Copy text" link below the speech bubble.
```

**交互说明：**
| 操作 | 触发方式 | 反馈 |
|------|----------|------|
| 切换版本 | 左右滑动 | 卡片滑动动画 + 指示器更新 |
| 重新生成 | 点击刷新按钮 | 返回加载状态 |
| 复制文案 | 点击复制链接 | Toast 提示"已复制" |
| 生成梗图 | 点击主按钮 | 跳转梗图编辑页 |

**结果卡片样式 Prompt：**
```
Speech bubble design: Rounded rectangle with a small triangle pointer towards the pet. White background with subtle shadow. Text in dark gray, 16px size. Persona tag shown as a small pill badge (e.g., "高冷总裁") in coral pink at top-left corner of the bubble.
```

---

### 6. 梗图编辑页（Meme Editor）

**页面目标：** 让用户编辑和美化梗图

**Stitch Prompt：**
```
Meme editor screen. Large preview area showing pet photo with text overlay at top (editable). Below the preview, a toolbar with options: Font style selector (horizontal scroll of 5 font previews), Filter selector (3 filter thumbnails: Original, Vintage, B&W), Text position toggle (top/bottom/center). At the bottom, two buttons: "Save to Album" with download icon, "Share" with share icon in coral pink. Show a small watermark "宠灵感" at bottom-right corner of the preview image. Clean interface with white background.
```

**编辑工具栏：**

**字体选择 Prompt：**
```
Font selector showing 5 horizontal scrollable options. Each option is a small preview card showing "Aa" in that font style: 1) Default rounded sans-serif, 2) Bold impact style, 3) Handwritten casual, 4) Pixel retro style, 5) Cute bubble letters. Selected font has coral pink underline.
```

**滤镜选择 Prompt：**
```
Filter selector showing 3 thumbnail previews of the current photo with different filters applied: "Original" with no filter, "Vintage" with warm sepia tone, "B&W" in grayscale. Selected filter has coral pink border.
```

**水印说明：**
- 免费用户：右下角显示「宠灵感」水印
- 付费用户：可选择去除水印

---

### 7. 分享页 / 分享弹窗（Share Sheet）

**页面目标：** 提供便捷的社交分享入口

**Stitch Prompt：**
```
Bottom sheet share menu sliding up from bottom. White rounded-top container with gray drag handle. Title "Share to" centered. Show 4 platform icons in a row: WeChat (green), Moments (colorful ring), Weibo (red), Xiaohongshu (red). Below, a secondary row with: "Save Image" with download icon, "Copy Link" with link icon. Each icon is a circle with the platform logo inside, platform name below in small text. Cancel button at the very bottom as text link.
```

**分享平台配置：**
| 平台 | 图标颜色 | 分享格式 |
|------|----------|----------|
| 微信好友 | #07C160 | 图片 + 小程序卡片 |
| 朋友圈 | 彩色渐变 | 图片 |
| 微博 | #E6162D | 图片 + 话题标签 |
| 小红书 | #FE2C55 | 图片 + 文案 |

---

### 8. 历史记录页（History）

**页面目标：** 展示用户历史生成的内容

**Stitch Prompt：**
```
History page with a grid layout of past generated memes. Two columns of square thumbnail cards. Each card shows the pet photo with a small text preview overlay at bottom. Cards have subtle rounded corners and light shadow. Pull-to-refresh at top. If empty, show an illustration of a cat with empty box and text "还没有内心戏记录，快去生成吧！" with a "Start Now" button. Top has a simple header with "My Creations" title and a filter icon.
```

**空状态 Prompt：**
```
Empty state for history page. Cute illustration of a cat peeking out of an empty cardboard box. Text below: "还没有内心戏记录" in gray. Subtext: "快去生成第一条吧！" A coral pink "Go Create" button below.
```

---

### 9. 宠物档案页（Pet Profile）

**页面目标：** 管理宠物信息，增强个性化体验

**Stitch Prompt：**
```
Pet profile creation/edit screen. Large circular photo upload area at top with camera icon overlay for changing photo. Below, form fields with rounded input boxes: "Pet Name" text input, "Species" dropdown (Cat/Dog/Other), "Gender" toggle buttons (Boy/Girl), "Age" number input with "years old" suffix. A section titled "Personality Tags" with selectable pill-shaped tags: "拆家狂", "社恐", "小公举", "话痨", "吃货", "高冷", etc. Allow multi-select with coral pink fill for selected tags. "Save Profile" button at bottom in coral pink.
```

**性格标签设计 Prompt：**
```
Personality tag selector. Multiple pill-shaped tags arranged in a flexible wrap layout. Unselected tags have white background with gray border. Selected tags have coral pink background with white text. Each tag has subtle tap animation. Some suggested tags: "拆家狂🏠", "社恐😰", "小公举👑", "话痨💬", "吃货🍖", "高冷❄️", "粘人精🤗", "戏精🎭".
```

**宠物档案卡片（列表视图）Prompt：**
```
Pet profile card in a list view. Horizontal card with pet photo on left (rounded square), pet info on right: name in bold, species and age in gray subtext, personality tags as small coral pink pills. Edit icon button at far right. Card has white background with subtle shadow.
```

---

### 10. 会员订阅页（Subscription）

**页面目标：** 展示付费权益，引导用户订阅

**Stitch Prompt：**
```
Subscription/membership page. Top banner with gradient from coral pink to golden yellow, showing "VIP Member" with a crown icon. Below, a comparison table showing Free vs VIP features: "Daily Generations: 5 vs Unlimited", "Watermark: Yes vs No", "Premium Personas: Locked vs All Access", "Fonts & Filters: Basic vs Full Library". Each VIP benefit has a checkmark in gold. Two pricing cards below: Monthly "¥12/month" and Yearly "¥98/year" with "Best Value" badge. Subscribe button in gradient coral to gold. Small terms text at bottom.
```

**权益对比表 Prompt：**
```
Feature comparison table. Two columns: Free (gray header) and VIP (gold gradient header). Rows showing features with X mark for free and checkmark for VIP. Features: "Unlimited daily usage", "Remove watermark", "All premium personas", "All fonts and filters", "Priority generation queue", "Exclusive new features". Clean grid layout with alternating row backgrounds.
```

**定价卡片 Prompt：**
```
Two pricing cards side by side. Monthly card: white background, "¥12/month" in large coral text, "Cancel anytime" subtext. Yearly card: golden gradient border, "¥98/year" with strikethrough "¥144" original price, "Save 32%" badge in gold, "Best Value" ribbon at top corner. Selected card has subtle glow effect.
```

---

### 11. 个人中心页（User Profile / Settings）

**页面目标：** 用户账户管理和设置

**Stitch Prompt：**
```
User profile and settings page. Top section with user avatar (or default pet icon if not set), username, and VIP badge if subscribed. Below, menu list with icons: "My Pets" with paw icon, "My Favorites" with heart icon, "Subscription" with crown icon, "Settings" with gear icon, "Help & Feedback" with question mark icon, "About Us" with info icon. Each menu item is a horizontal row with icon, text, and right chevron. Bottom shows app version number. Clean white cards on cream background.
```

**设置子页面 Prompt：**
```
Settings page with toggle options. Menu items: "Push Notifications" with toggle switch, "Auto-save to Album" with toggle switch, "Image Quality" with "High/Medium/Low" selector, "Clear Cache" with cache size shown (e.g., "23.5 MB"), "Privacy Policy" and "Terms of Service" as links. Simple list layout with dividers between items.
```

---

### 12. 免费次数用尽弹窗（Usage Limit Modal）

**页面目标：** 引导免费用户付费或观看广告

**Stitch Prompt：**
```
Modal popup for usage limit reached. Center modal with rounded corners on a dimmed background. Sad cat illustration at top. Title: "今日免费次数已用完" in bold. Two options below: "Watch Ad for +1 Use" with play button icon (outline style), "Upgrade to VIP" with crown icon (filled coral pink, highlighted). Small text link at bottom: "明天再来" to dismiss. Modal has subtle shadow and slide-up animation.
```

---

### 13. 主子朋友圈页（Pet Moments）— 第二阶段

**页面目标：** 生成模拟朋友圈界面的趣味图片

**Stitch Prompt：**
```
Pet Moments generator page - creates fake social feed posts for pets. Preview area showing a mockup of WeChat Moments style: pet avatar and pet name at top-left, generated text as the post content, pet photo below the text, timestamp showing "Just now", and auto-generated comments from "virtual pet friends" like "隔壁旺财" saying "汪汪！" or "楼上肥橘" with a like. Below the preview, options to customize: pet name input, enable/disable virtual comments toggle. "Generate Moments Card" button in coral pink at bottom.
```

---

### 14. 宠物信件页（Pet Letter）— 第二阶段

**页面目标：** 展示宠物写给主人的信件

**Stitch Prompt：**
```
Pet Letter display page with a warm emotional design. Background resembles aged paper or parchment texture. Letter content in a handwritten-style font, starting with "亲爱的铲屎官：" and signed with the pet's name and a paw print stamp at the bottom. Decorative envelope illustration at top. Content is AI-generated based on user's pet history. "Share This Letter" button and "Save as Image" button at bottom. Soft warm cream background with subtle vintage edges.
```

---

## 交互与动效规范

### 微交互 Prompt
```
Micro-interactions: Buttons should have subtle scale-down effect on press (0.95x). Cards have gentle lift animation on tap. Success actions trigger a small confetti burst of paw prints. Loading states use bouncing dots or tail-wagging animation. Page transitions are smooth slide-left/right for navigation, slide-up for modals.
```

### 空状态设计 Prompt
```
Empty states: Use cute pet illustrations (cat or dog) with relevant props. Neutral gray text for primary message, lighter gray for secondary. Always include a clear call-to-action button in coral pink. Examples: cat in empty box for no history, sleeping cat for no notifications, confused cat with question mark for errors.
```

### 错误状态设计 Prompt
```
Error states: Show a concerned or apologetic pet illustration. Error message in dark gray, not red (to keep friendly tone). Always provide a retry action or alternative path. Network error shows cat tangled in yarn representing "connection issues". API failure shows cat shrugging with "服务开小差了，请稍后再试".
```

---

## 组件库速查

### 按钮样式
```
Primary button: Pill-shaped, coral pink (#FF6B6B) background, white text, subtle shadow.
Secondary button: Pill-shaped, white background, coral pink border and text.
Text button: No background, coral pink text, for less important actions.
Disabled button: Light gray background, darker gray text, no interactions.
```

### 卡片样式
```
Standard card: White background, 12px border-radius, subtle drop shadow (0 2px 8px rgba(0,0,0,0.08)), 16px padding.
Elevated card: Same as standard but larger shadow for emphasis.
Interactive card: Adds gentle lift animation and border highlight on tap.
```

### 输入框样式
```
Text input: Rounded rectangle, light gray background (#F5F5F5), 8px padding, darker gray placeholder text, coral pink border on focus.
```

### 标签/徽章样式
```
Tag pill: Small rounded rectangle, coral pink background for selected, gray border for unselected, 8px horizontal padding.
Badge: Small circular or pill indicator, used for counts or status (e.g., VIP badge in gold).
```

---

## 设计验收清单

- [ ] 所有页面使用统一的配色方案
- [ ] 所有按钮和可点击元素有明确的交互反馈
- [ ] 空状态和错误状态有友好的插图和文案
- [ ] 表单输入有清晰的占位符和验证提示
- [ ] 加载状态有趣味性动画，缓解等待焦虑
- [ ] 分享图片包含品牌水印（免费版）
- [ ] 付费功能有明确的锁定/解锁状态展示
- [ ] 页面层级不超过 3 层，操作路径简洁
- [ ] 核心功能（拍照→生成→分享）可在 3 步内完成

---

## 附录：快速 Prompt 模板

### 新增页面模板
```
[Page Type] for PetSoul pet app. [Main content description]. [Layout details]. [Key interactive elements]. Warm cream background, coral pink primary color, friendly and playful style.
```

### 修改元素模板
```
On the [page name], [specific element]: [change description]. Keep the warm, playful aesthetic consistent with the app's coral pink theme.
```

### 添加功能模板
```
Add [feature name] to [page name]. [Feature description and behavior]. Style should match existing UI: rounded corners, coral pink accents, friendly typography.
```
