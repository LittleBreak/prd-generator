# Product Requirements Document: PetSoul (宠灵感)

**Status:** Draft | **Owner:** [TBD]
**Last Updated:** 2026-01-19

---

## 1. Problem & Opportunity

### Problem Statement

Pet owners constantly wonder what their pets are thinking. When a cat stares at a wall or a dog gives a guilty look, owners instinctively imagine their pet's inner thoughts—but have no fun, shareable way to express this imagination.

### Opportunity

- **Market Size:** 70M+ pet-owning households in China alone; pet content consistently ranks among top-performing social media categories
- **Viral Potential:** Pet content with humorous captions has proven viral mechanics (memes, short videos)
- **Technology Timing:** Multimodal AI (GPT-4o, Claude 3.5 Sonnet, Gemini 1.5 Pro) now provides accurate animal expression/pose recognition

### Goals & Objectives

| Goal | Description |
|------|-------------|
| **Primary** | Create a delightful, shareable pet content generation tool |
| **Secondary** | Build emotional connection between users and the app through personalized pet profiles |
| **Business** | Establish a freemium model with sustainable unit economics |

### Success Metrics (KPIs)

| Metric | Target (MVP) | Target (6 months) |
|--------|--------------|-------------------|
| Daily Active Users (DAU) | 1,000 | 50,000 |
| Share Rate | 30% of generations shared | 40% |
| D7 Retention | 15% | 25% |
| Conversion to Premium | - | 5% |
| Avg. API Cost per User | < ¥0.5/day | < ¥0.3/day |

---

## 2. Target Audience

### Primary Persona: "The Proud Pet Parent"

- **Demographics:** 18-35 years old, urban, active on social media (Xiaohongshu, WeChat Moments, Douyin)
- **Behavior:** Takes 5-10+ photos of their pet weekly; frequently shares pet content
- **Motivation:** Wants to entertain friends and express the "personality" they see in their pet
- **Pain Point:** Generic pet captions feel unoriginal; wants unique, funny content

### Secondary Persona: "The Casual Pet Lover"

- **Demographics:** Any age, may not own a pet
- **Behavior:** Enjoys pet content; occasionally photographs friends' pets or strays
- **Motivation:** Quick entertainment; wants to try the "viral thing" they saw online

### User Stories

| Priority | User Story |
|----------|------------|
| **[P0]** | As a pet owner, I want to upload a photo of my pet and instantly get a funny "inner monologue" so that I can share it on social media |
| **[P0]** | As a user, I want to choose different personality styles (sassy, dramatic, shy) so that the generated text matches how I see my pet |
| **[P0]** | As a user, I want to generate a shareable meme image with text overlay so that I can post directly to social platforms |
| **[P1]** | As a returning user, I want to save my pet's profile (name, personality) so that future generations feel more personalized |
| **[P1]** | As a user, I want to see 3 different caption options so that I can pick the best one |
| **[P2]** | As a user, I want to generate a "Pet Moments" fake social feed image so that I can create more elaborate shareable content |
| **[P2]** | As a long-term user, I want to receive occasional "letters from my pet" based on my upload history so that I feel emotionally connected |

---

## 3. The Solution

### 3.1 Functional Requirements

#### Core Module: Snapshot Decode (快拍解码)

| ID | Requirement | Priority |
|----|-------------|----------|
| F1 | System must accept image upload (camera or gallery) in JPG/PNG format, max 10MB | P0 |
| F2 | System must use Vision API to identify: pet species, facial expression, body posture, environment, objects | P0 |
| F3 | System must generate pet "inner monologue" text (50-150 characters) based on image analysis + selected persona | P0 |
| F4 | System must provide 3 alternative caption versions per generation | P1 |
| F5 | System must support regeneration with same image | P1 |

#### Persona Module: Personality Lab (性格实验室)

| ID | Requirement | Priority |
|----|-------------|----------|
| F6 | System must offer 5+ preset persona templates: "Aloof Emperor", "Drama Queen", "Shy Bean", "Hot-blooded Youth", "Gossipy Auntie" | P0 |
| F7 | Users can create and save pet profiles with: name, species, personality tags | P1 |
| F8 | Premium personas available: "Palace Drama Style", "Cyberpunk", "Shakespearean" | P2 |

#### Output Module: Meme Maker (一键梗图)

| ID | Requirement | Priority |
|----|-------------|----------|
| F9 | System must overlay generated text on original image with legible styling | P0 |
| F10 | System must provide 3+ text layout templates | P1 |
| F11 | System must add subtle watermark/logo to generated images | P0 |
| F12 | Generated images must include scannable QR code linking to app | P1 |
| F13 | "Pet Moments" mode: generate fake WeChat Moments UI with pet friend comments | P2 |

#### Sharing & Retention

| ID | Requirement | Priority |
|----|-------------|----------|
| F14 | One-tap save to device gallery | P0 |
| F15 | One-tap share to WeChat, Xiaohongshu, Douyin | P1 |
| F16 | Daily free generation limit (3/day for free users) | P1 |
| F17 | Push notification: "Letter from your pet" based on historical uploads | P2 |

### 3.2 User Experience (UX)

#### Core User Flow

```
┌─────────────┐     ┌─────────────┐     ┌─────────────┐     ┌─────────────┐
│   Launch    │────▶│ Upload/Take │────▶│  Select     │────▶│  View 3     │
│   App       │     │   Photo     │     │  Persona    │     │  Results    │
└─────────────┘     └─────────────┘     └─────────────┘     └──────┬──────┘
                                                                   │
                    ┌─────────────┐     ┌─────────────┐            │
                    │   Share     │◀────│  Generate   │◀───────────┘
                    │   Image     │     │  Meme       │
                    └─────────────┘     └─────────────┘
```

#### Key UX Principles

1. **Time to Value < 30 seconds:** User should see first result within 30 seconds of opening app
2. **One-hand Operation:** All primary actions reachable with thumb
3. **Delight in Details:** Loading animations feature pet-themed illustrations
4. **Immediate Shareability:** Generated meme should look "native" to social platforms

#### Wireframes

> *[Link to Figma - TBD]*

### 3.3 Non-Functional Requirements

| Category | Requirement |
|----------|-------------|
| **Performance** | Image analysis + text generation must complete in < 5 seconds (P95) |
| **Performance** | Meme image generation must complete in < 2 seconds |
| **Scalability** | Architecture must support 10,000 concurrent users |
| **Reliability** | 99.5% uptime for core generation feature |
| **Security** | Images must not be stored beyond session unless user opts into profile |
| **Privacy** | Clear consent flow for camera/gallery access |
| **Localization** | MVP in Simplified Chinese; English as P2 |

---

## 4. Scope & Logistics

### In Scope (MVP)

- Single photo upload and analysis
- 5 preset persona templates
- 3 meme layout templates
- Basic text-on-image generation
- Save to gallery
- Daily generation limits (3 free / unlimited premium)

### Out of Scope (MVP)

| Feature | Reason |
|---------|--------|
| Video analysis | Technical complexity; defer to v2 |
| Multi-pet detection in single image | Edge case; defer |
| Pet profile history/timeline | Requires backend infra; defer to v1.5 |
| "Letters from pet" push notifications | Requires engagement data; defer to v2 |
| Brand partnership integrations | Requires user base first |
| Physical merchandise ordering | Separate business line |
| Dialogue mode for multiple pets | Complex prompt engineering; defer |

### Dependencies

| Dependency | Owner | Status |
|------------|-------|--------|
| Multimodal API access (GPT-4o or Claude) | External | Available |
| WeChat Mini Program approval | Platform | Pending |
| CDN for image delivery | Infra | TBD |
| Payment integration (WeChat Pay) | Infra | TBD |

### Release Plan

| Phase | Scope | Timeline |
|-------|-------|----------|
| **Alpha** | Core generation flow, 3 personas, 1 meme template, internal testing | Week 1-2 |
| **Beta** | 5 personas, 3 templates, WeChat sharing, limited external users (500) | Week 3-4 |
| **GA v1.0** | Full MVP, monetization enabled, public launch | Week 5-6 |
| **v1.5** | Pet profiles, generation history | Week 8-10 |
| **v2.0** | Push notifications, video support exploration | TBD |

---

## 5. Monetization Model

### Freemium Structure

| Tier | Price | Features |
|------|-------|----------|
| **Free** | ¥0 | 3 generations/day, 5 basic personas, watermarked output |
| **Premium** | ¥12/month or ¥98/year | Unlimited generations, all personas, no watermark, priority processing |

### Future Revenue Streams (Post-MVP)

- **Ad-supported unlocks:** Watch ad for +1 free generation
- **Brand partnerships:** Native ad integration in generated captions
- **Merchandise:** Print-on-demand for generated memes

---

## 6. Questions & Risks

### Open Questions

| Question | Owner | Due Date |
|----------|-------|----------|
| Which multimodal API offers best cost/quality tradeoff for animal images? | Tech Lead | Before Alpha |
| WeChat Mini Program content moderation requirements for AI-generated text? | Product | Before Beta |
| Optimal daily free limit to balance engagement vs. conversion? | Growth | Post-Beta A/B test |

### Risks & Mitigations

| Risk | Likelihood | Impact | Mitigation |
|------|------------|--------|------------|
| API costs exceed projections | Medium | High | Implement caching for similar images; explore self-hosted models |
| Low retention after initial viral spike | High | Medium | Pet profile feature; "letters" engagement loop |
| Generated content flagged as inappropriate | Low | High | Content moderation layer; banned phrase list |
| Copycat competitors | High | Medium | Focus on UX polish and persona quality; build brand |

---

## 7. Acceptance Criteria

### P0 User Story: Basic Generation Flow

**Given** a user uploads a clear photo of a pet
**When** they select a persona and tap "Generate"
**Then** the system displays 3 different caption options within 5 seconds
**And** each caption is contextually relevant to the image content
**And** the user can generate a meme image with any selected caption

### P0 User Story: Meme Generation

**Given** a user has selected a caption
**When** they tap "Create Meme"
**Then** a shareable image is generated with text overlay within 2 seconds
**And** the image includes a subtle watermark
**And** the user can save to gallery with one tap

---

## Appendix

### A. Persona Template Examples

| Persona | Sample Output (for cat staring at wall) |
|---------|----------------------------------------|
| Aloof Emperor | "凝视虚空，思考这个家的未来。结论：没有未来，除非罐头加量。" |
| Drama Queen | "你们不懂...那面墙里...住着我前世的爱人..." |
| Hot-blooded Youth | "那只蚊子以为飞到墙上我就看不见了？！天真！！！" |

### B. Competitive Landscape

| Competitor | Strength | Our Differentiation |
|------------|----------|---------------------|
| Generic meme generators | Broad use case | Pet-specialized AI; persona depth |
| Pet camera apps | Hardware integration | Pure software; lower barrier |
| Social media filters | Platform native | Richer AI-generated content |

---

*This is a living document. Please add comments and questions directly.*
