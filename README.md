# Woodland Astral Tarot

🌿 **Live demo:** [wangyuyanyan.github.io/Woodland-Tarot](https://wangyuyanyan.github.io/Woodland-Tarot/)

A gesture-controlled AI tarot web app built as a portfolio project. Draw cards by holding your fist over the carousel, reveal them with an open palm, and receive a streaming AI interpretation grounded in Jungian psychology and narrative therapy. All 78 card illustrations were designed personally in Alphonse Mucha's Art Nouveau style.

---

## Features

- **Gesture control via MediaPipe** — no mouse or touch required. Scroll the carousel by moving your hand left or right; hold a fist for 1 second to select a card; hold an open palm to trigger the reading
- **Streaming AI readings** — powered by DeepSeek LLM, structured into three sections: poetic card interpretation, psychological reflection on your specific question, and actionable guidance
- **Original Art Nouveau artwork** — all 78 tarot card illustrations designed personally in the style of Alphonse Mucha
- **3D card carousel** — CSS `preserve-3d` arc layout with real-time hand-position light tracing and flip reveal animations
- **Cinematic reveal sequence** — after drawing three cards, a full-screen close-up presents each card before transitioning to the reading
- **Synthesized ambient audio** — three sound effects built entirely with Web Audio API, no external audio files
- **Forest firefly background** — 85 fireflies rendered on Canvas with sinusoidal brightness pulsing and drifting green mist
- **Privacy-first** — camera data processed locally only, API key stored in your browser's localStorage, nothing sent to any server except DeepSeek directly
- **Reading history** — last 30 readings saved locally with date, question, cards, and full interpretation

## Tech Stack

MediaPipe Hands · DeepSeek API · Web Audio API · Canvas API · Vanilla JS · CSS3 3D Transforms

## Usage

1. Clone the repo and open `index.html` in a browser (or visit the live demo above)
2. Allow camera access when prompted
3. Go to Settings and add your [DeepSeek API key](https://platform.deepseek.com/)
4. Hold an open hand in front of the camera for 3 seconds to begin

## Note on AI-assisted development

This project was built with Claude as a development partner. All architecture decisions, UX design, prompt engineering, and card artwork are my own — AI assistance was used to accelerate implementation, not replace authorship. See [PROMPTS.md](./PROMPTS.md) for a full record of the development process.

---
---

# Woodland Astral Tarot（深空林地塔罗）

🌿 **在线体验：** [wangyuyanyan.github.io/Woodland-Tarot](https://wangyuyanyan.github.io/Woodland-Tarot/)

一个以手势控制为核心交互方式的 AI 塔罗占卜 Web 应用，作为个人作品集项目开发。通过摄像头手势抽取三张牌，张开手掌触发解读，结合荣格心理学与叙事疗法框架，由大语言模型生成流式个性化解读。78 张牌面插画均为本人原创，采用阿尔丰斯·穆夏新艺术风格设计。

---

## 功能特性

- **MediaPipe 手势识别** — 无需鼠标或触屏。手向左/右移动控制牌阵滚动；居中握拳保持 1 秒选牌；张开手掌触发解读
- **流式 AI 解读** — 接入 DeepSeek 大模型，解读分三段结构输出：诗意牌意解说、结合提问的心理层面剖析、可落地的行动建议
- **原创新艺术风格插画** — 78 张塔罗牌面由本人独立设计，风格参照阿尔丰斯·穆夏
- **3D 卡牌轮播** — CSS `preserve-3d` 弧形排列，实时手部位置光照追踪与翻牌动画
- **电影感揭牌时刻** — 三张牌选完后，全屏特写依次呈现每张牌，再过渡至解读界面
- **合成环境音效** — 三组音效完全通过 Web Audio API 代码合成，不依赖外部音频文件
- **森林萤火虫背景** — Canvas 绘制 85 只萤火虫，正弦函数控制亮度脉动，配合漂移绿雾带
- **隐私优先架构** — 摄像头数据仅本地处理，API Key 仅存于浏览器 localStorage，除 DeepSeek 接口外不经过任何服务器
- **解读历史记录** — 本地保存最近 30 条记录，含日期、问题、抽牌结果与完整解读文本

## 技术栈

MediaPipe Hands · DeepSeek API · Web Audio API · Canvas API · 原生 JS · CSS3 3D 变换

## 使用方式

1. 克隆仓库后用浏览器打开 `index.html`（或直接访问上方在线链接）
2. 允许摄像头权限
3. 进入设置，填入你的 [DeepSeek API Key](https://platform.deepseek.com/)
4. 在摄像头前张开手掌保持 3 秒，开始体验

## 关于 AI 辅助开发

本项目以 Claude 作为开发协作工具。所有架构决策、交互设计、提示词工程及牌面视觉设计均为本人完成，AI 辅助用于加速实现过程，而非替代创作主体。完整的开发提示词迭代记录见 [PROMPTS.md](./PROMPTS.md)。
