# Claude API 使用指南

## 前言

### 不支持区域

[Claude API 文档](https://console.anthropic.com/docs/api)不支持香港节点以及国内，台湾节点可用

### 申请 API 权限

[前往申请](https://www.anthropic.com/earlyaccess)

### 申请 API keys

- 登录 [Console](https://console.anthropic.com/login?selectAccount=&returnTo=https%3A%2F%2Fconsole.anthropic.com%2Faccount%2Fkeys)
  > 目前新用户暂时无法注册登录，需要先通过申请

![](./disabled.png)

- 前往 Account Settings 获取 API Keys

## 使用

- 安装 TS 依赖（[仓库地址](https://github.com/anthropics/anthropic-sdk-typescript)）

```TypeScript
yarn add @anthropic-ai/sdk
// or
npm install @anthropic-ai/sdk
```

- 设置 API Key 环境变量

```TypeScript
ANTHROPIC_API_KEY=YOUR_API_KEy
```

- 代码 demo

```TypeScript
import "dotenv/config";
import { AI_PROMPT, Client, HUMAN_PROMPT } from "@anthropic-ai/sdk";

const apiKey = process.env.ANTHROPIC_API_KEY;
if (!apiKey) {
  throw new Error("The ANTHROPIC_API_KEY environment variable must be set");
}

const client = new Client(apiKey);

client
  .complete({
    prompt: `${HUMAN_PROMPT} How many toes do dogs have?${AI_PROMPT}`,
    stop_sequences: [HUMAN_PROMPT],
    max_tokens_to_sample: 200,
    model: "claude-v1",
  })
  .then((finalSample) => {
    console.log(finalSample.completion);
  })
  .catch((error) => {
    console.error(error);
  });
```

### API Reference 文档

https://console.anthropic.com/docs/api/reference
