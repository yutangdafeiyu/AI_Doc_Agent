# AI 工程化开发

现代的 AI 工程化开发模式通常是采用 AI Agent + LLM + Skill + MCP + Context Engineering 的模式。

## AI Agent

AI Agent 是 LLM 的代理人，例如 Trae、Cursor、GitHub Copilot、豆包 等都是 AI Agent。这些 Agent 的工作就是在用户和 LLM 中间充当代理人，在工程体系中用户只与 AI Agent 进行交互，AI Agent 与 LLM 进行交互以后再向用户输出结果。

## LLM

LLM 指的是大语言模型，例如 Gemini、ChatGPT、DeepSeek 等都是 LLM 大模型。现代的 AI 工程化开发模式中 LLM 作为大脑承担工作。

## MCP

‌MCP 通常指“模型上下文协议”（Model Context Protocol）,他的作用是为 Agent 提供外部资源能力，作为插件为 Agent 提供拓展，以接入第三方服务。例如 lanhuMCP、FigmaMCP。

## Context Engineering 与 Prompt Engineering

- Prompt Engineering 提示词工程 是指对提示词进行优化，旨在 LLM 可以针对提示词中的设定，需要说出非常清晰和具体的要求而达到输出符合我们预期的结果，但当 AI Agent 需要连续工作几小时、处理几十万字的信息时，光写好提示词不够了，你需要动态管理整个上下文。原因很简单：AI 和人类 一样，工作记忆是有限的。
  研究发现，随着上下文长度增加，模型回忆信息的准确率会下降。这个现象叫"context rot"（上下文腐化）——就像人脑塞入太多信息后，会记不清哪件事更重要。在早期 AI 浪潮中，Prompt Engineering 被广泛运用，但是在工程化体系中，由于上下文长度的限制，Prompt Engineering 无法满足复杂场景的需求。

- Context Engineering 上下文工程。当下构建 AI 应用的重点正在从 Prompt Engineering 转向 Context Engineering。如果是提示词工程是写出精彩的指令。而上下文工程是指在提示词工程的基础上，为这条指令之前和之后发生什么，记忆什么、从记忆或工具中提取什么、整个对话如何构建。两种并不是竞争的实践，Prompt Engineering 只是 Context Engineering 这台大机器中的一小部分。

## Skill

skill 是指一个被标准封装用于处理特定需求的封闭单元。可以被 agent 自主判断，自主调用用于完成特定任务


1.  rule和skill的创建技巧
2.  项目代码模版知识库
3.  自动化按步骤执行任务：6A 工作流的配置 https://juejin.cn/post/7541420187121713161
4.  流水线工作，多Agent协同
