# 百聆 (Bailing)

**百聆** 是一个开源的语音对话助手，旨在通过语音与用户进行自然的对话。该项目结合了语音识别 (ASR)、语音活动检测 (VAD)、大语言模型 (LLM) 和语音合成 (TTS) 技术，这是一个类似GPT-4o的语音对话机器人，通过ASR+LLM+TTS实现，提供高质量的语音对话体验，端到端时延800ms。百聆旨在无需GPU的情况下，实现类GPT-4o的对话效果，适用于各种边缘设备和低资源环境。


## 项目特点

- **高效开源模型**：百聆使用了多个开源模型，确保高效、可靠的语音对话体验。
- **无需GPU**：通过优化，可本地部署，仍能提供类GPT-4的性能表现。
- **模块化设计**：ASR、VAD、LLM和TTS模块相互独立，可以根据需求进行替换和升级。


## 项目简介

百聆通过以下技术组件实现语音对话功能：

- **ASR**: 使用 [FunASR](https://github.com/modelscope/FunASR) 进行自动语音识别，将用户的语音转换为文本。
- **VAD**: 使用 [silero-vad](https://github.com/snakers4/silero-vad) 进行语音活动检测，以确保只处理有效的语音片段。
- **LLM**: 使用 [deepseek](https://github.com/deepseek-ai/DeepSeek-LLM) 作为大语言模型来处理用户输入并生成响应，极具性价比。
- **TTS**: 使用 [edge-tts](https://github.com/rany2/edge-tts) [ChatTTS](https://github.com/2noise/ChatTTS) MacOS say进行文本到语音的转换，将生成的文本响应转换为自然流畅的语音。


## 框架说明

![百聆流程图](assets/bailing_flowchart.png)

其中Robot负责打断相关的能力，以及各模块的串联

| 播放器状态 | 是否说话 | 说明 |
|----------|----------|----------|
| 播放中 | 未说话 | 正常 |
| 播放中 | 说话 | 打断场景 |
| 未播放| 未说话 | 正常 |
| 未播放| 说话 | VAD判断，ASR识别 |

## 展示

[对话演示1](https://www.zhihu.com/zvideo/1818998325594177537)

[对话演示2](https://www.zhihu.com/zvideo/1818994917940260865)





## 功能特性

- **语音输入**：通过 FunASR 进行准确的语音识别。
- **语音活动检测**：使用 silero-vad 过滤无效音频，提升识别效率。
- **智能对话生成**：依靠 deepseek 提供的强大语言理解能力生成自然的文本回复，极具性价比。
- **语音输出**：通过 edge-tts 将文本转为语音，为用户提供逼真的听觉反馈。
- **支持打断**：配置打断策略，支持关键字和语音打断

## 项目优势

- **高质量语音对话**：整合了优秀的ASR、LLM和TTS技术，确保语音对话的流畅性和准确性。
- **轻量化设计**：无需高性能硬件即可运行，适用于资源受限的环境。
- **完全开源**：百聆完全开源，鼓励社区贡献与二次开发。

## 安装与运行

### 依赖环境

请确保你的开发环境中安装了以下工具和库：

- Python 3.8 或更高版本
- `pip` 包管理器
- FunASR、silero-vad、deepseek、edge-tts 所需的依赖库

### 安装步骤

1. 克隆项目仓库：

    ```bash
    git clone https://github.com/wwbin2017/bailing.git
    cd bailing
    ```

2. 安装所需依赖：

    ```bash
    pip install -r requirements.txt
    ```

3. 配置环境变量：

打开config/config.yaml 配置ASR TTS LLM等相关配置

4. 运行项目：

    ```bash 
    cd server
    python server.py # 启动后端服务，也可不执行这一步
    ```
    
    ```bash
    python main.py
    ```

## 使用说明

1. 启动应用后，系统会等待语音输入。
2. 通过 FunASR 将用户语音转为文本。
3. silero-vad 进行语音活动检测，确保只处理有效语音。
4. deepseek 处理文本输入，并生成智能回复。
5. edge-tts, ChatTTS, MacOs say 将生成的文本转换为语音，并播放给用户。


## Roadmap

- [x] 基本语音对话功能
- [ ] 支持插件调用
- [ ] 支持WebRTC
- [ ] 类JARVIS个人助手
- [ ] 英语口语练习


## 贡献指南

欢迎任何形式的贡献！如果你对百聆项目有改进建议或发现问题，请通过 [GitHub Issues](https://github.com/wwbin2017/bailing/issues) 进行反馈或提交 Pull Request。

## 开源协议

该项目基于 [MIT 许可证](LICENSE) 开源。你可以自由地使用、修改和分发此项目，但需要保留原始许可证声明。

## 联系方式

如有任何疑问或建议，请联系：

- GitHub Issues: [项目问题追踪](https://github.com/wwbin2017/bailing/issues)

---

## 免责声明

百聆 (Bailing) 是一个开源项目，旨在用于个人学习和研究目的。使用本项目时，请注意以下免责声明：

1. **个人用途**：本项目仅用于个人学习和研究，不适用于商业用途或生产环境。
2. **风险和责任**：使用百聆 (Bailing) 可能会导致数据丢失、系统故障或其他问题。我们对因使用本项目而导致的任何损失、损害或问题不承担任何责任。
3. **支持**：本项目不提供任何形式的技术支持或保证。用户应自行承担使用本项目的风险。

在使用本项目之前，请确保您已了解并接受这些免责声明。如果您不同意这些条款，请不要使用本项目。

感谢您的理解与支持！
