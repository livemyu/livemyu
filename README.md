# Huang Yu · 黄宇

**中山大学毕业生** ｜ 方向：**音频可视化** 与 **语音大模型（Speech-LLM）**

我做两件相互衔接的事：把音频「看」清楚，把语音「接」进语言模型。
偏好**可复现、离线优先、工程可用**的开源实现——核心链路不依赖 GPU、
不依赖网络，能在一台普通机器（甚至 CI 日志里）端到端跑通并复现结果。

<p>
  <img alt="Python" src="https://img.shields.io/badge/Python-3.10%2B-3776AB?logo=python&logoColor=white">
  <img alt="NumPy" src="https://img.shields.io/badge/NumPy-013243?logo=numpy&logoColor=white">
  <img alt="SciPy" src="https://img.shields.io/badge/SciPy-8CAAE6?logo=scipy&logoColor=white">
  <img alt="PyTorch" src="https://img.shields.io/badge/PyTorch%20(optional)-EE4C2C?logo=pytorch&logoColor=white">
  <img alt="DSP" src="https://img.shields.io/badge/DSP-STFT%20%2F%20Mel%20%2F%20MFCC-4c7">
  <img alt="Offline first" src="https://img.shields.io/badge/Offline--first-Reproducible-2a9d8f">
</p>

---

## 🔬 研究与工程兴趣

- **音频 / 声谱可视化**：波形、STFT、梅尔谱、色度、声谱图，以及交互式浏览与离线导出。
- **语音接入 LLM**：语音编码器 / 离散语音单元 → 语言模型的「语音理解、语音问答、语音指令跟随」链路。
- **可复现工程**：确定性算法、纯 Python 参考内核、可选后端、严格类型检查与 CI 全流程。

---

## 📦 开源项目

下面是本账号上真实存在、可直接查阅与运行的仓库。

### [`audioscope`](https://github.com/livemyu/audioscope) — 音频可视化工具包

波形 / STFT / 梅尔谱 / 色度 / 声谱图等多种可视化，支持交互式浏览与离线导出，面向音频分析与教学。

- 🧮 **NumPy / SciPy 内核**：DSP 基于成熟科学计算库，结果可与 librosa 相互印证。
- 🎨 **绘图后端可选**：内置 ASCII 渲染与自带的极简 PNG 编码器，**没有 matplotlib 也能出图**。
- 🔎 **交互式浏览**：`Browser` 在长音频上滑动视口、翻页、按时间定位与缩放。
- 📴 **离线可跑**：核心与导出零重型依赖，适合远程终端、CI 日志与课堂演示。

```bash
audioscope --tone 440 --duration 2 mel          # 无需音频文件即可上手
```

`Python` · `MIT`

### [`voxlink`](https://github.com/livemyu/voxlink) — 语音大模型（Speech-LLM）工具包

把语音编码器 / 离散语音 token 接入大语言模型，实现**语音理解、语音问答与语音到文本指令跟随**的参考实现。

- 🔗 **清晰可替换的链路**：`波形 → 特征前端(MFCC) → 离散语音单元(k-means 码本) → 提示拼装 → 语言模型(n-gram) → 解码(贪心/beam) → 文本`。
- 🧩 **纯 Python 参考内核**：无强制运行时依赖，`numpy` / `torch` 后端可选，任一环节都可换成更强实现。
- 🎯 **确定性 & 可复现**：完全离线运行，能在 CI 中端到端复现，内置 WER / CER 评估。

```bash
voxlink demo                                     # 端到端演示
voxlink eval manifest.jsonl --model model/       # 评估 WER/CER
```

`Python` · `Apache-2.0`

---

## 🧭 正在推进

- 更真实的语音编码器接口（对接外部特征）与连续表示 + 投影的第二条接入路径。
- 重采样加入抗混叠滤波；可选的神经语言模型后端适配示例。
- 让 `audioscope` 与 `voxlink` 共享同一套前端特征约定，打通「可视化 ↔ 建模」。

---

> 关注可复现、离线优先的音频与语音工程。欢迎在各仓库的 Issues 中交流与反馈。
