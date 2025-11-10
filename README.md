# AI Suspended Ball Chat

一个功能强大的AI聊天组件，支持流式响应、图片上传、语音播报、历史记录管理等功能。可以作为悬浮球或独立面板使用。
![Snipaste_2025-08-31_19-48-18.png](https://free.picui.cn/free/2025/08/31/68b437f266289.png)

**《组件落地场景体验1-AI简历助手》**: [https://luckycola.com.cn/public/resume/#/resume](https://luckycola.com.cn/public/resume/?t=123456789#/resume)

**《组件落地场景体验2-AI编程助手》**: [https://luckycola.com.cn/public/dist/onlineCodeEditor.html#/editor](https://luckycola.com.cn/public/dist/onlineCodeEditor.html?t=123456789#/editor)

---

## ✨ 特性

- 🤖 **AI对话**: 支持与AI进行自然语言对话
- 📡 **双模式请求**: 支持普通请求和流式响应两种模式
- 🖼️ **图片上传**: 支持图片上传和AI图像识别
- 🎤 **语音输入**: 支持语音转文字输入，便捷的语音交互
- 🔊 **语音播报**: 支持AI回复内容的语音播报
- 📝 **获取AI消息**: 支持将AI内容插入到用户的编辑器或其他应用
- 💾 **历史记录**: 本地存储对话历史，支持历史记录管理
- 🎨 **主题切换**: 支持白天/夜间模式切换
- 🔗 **引用内容**: 支持选择引用页面中(上传)的文本作为上下文
- 📱 **自定义接口**: 支持用户自定义后端接口
- 🔧 **高度可配置**: 丰富的配置选项和回调函数
- 🚀 **TypeScript支持**: 完整的TypeScript类型定义
- ☎️ **问题工单搜集**: 支持搜集需人工处理的问题

## 📦 安装

```bash
npm install ai-suspended-ball-chat
# 或
yarn add ai-suspended-ball-chat
# 或
pnpm add ai-suspended-ball-chat
```

## 🚀 快速开始

### 基础使用

#### 流式响应模式

```vue
<template>
  <div id="app">
    <SuspendedBallChat
      :url="apiUrl"
      :app-name="appName"
      :domain-name="domainName"
      :enable-streaming="true"
      :enable-context="true"
      :enable-local-storage="true"
      :enable-voice-input="true"
      :callbacks="callbacks"
    />
  </div>
</template>

<script>
import { SuspendedBallChat } from 'ai-suspended-ball-chat'

export default {
  name: 'App',
  components: {
    SuspendedBallChat
  },
  data() {
    return {
      apiUrl: 'https://your-api-endpoint.com/chat',
      appName: 'my-app',
      domainName: 'user123',
      callbacks: {
        onUserMessage: (message) => {
          console.log('用户发送消息:', message)
        },
        onAssistantMessage: (message) => {
          console.log('AI回复:', message)
        },
        onError: (error) => {
          console.error('发生错误:', error)
        }
      }
    }
  }
}
</script>
```

#### 普通请求模式

```vue
<template>
  <div id="app">
    <SuspendedBallChat
      :url="apiUrl"
      :app-name="appName"
      :domain-name="domainName"
      :enable-streaming="false"
      :enable-context="true"
      :enable-local-storage="true"
      :enable-voice-input="true"
      :callbacks="callbacks"
    />
  </div>
</template>

<script>
import { SuspendedBallChat } from 'ai-suspended-ball-chat'

export default {
  name: 'App',
  components: {
    SuspendedBallChat
  },
  data() {
    return {
      apiUrl: 'https://your-api-endpoint.com/chat',
      appName: 'my-app',
      domainName: 'user123',
      callbacks: {
        onUserMessage: (message) => {
          console.log('用户发送消息:', message)
        },
        onAssistantMessage: (message) => {
          console.log('AI回复:', message)
        },
        onError: (error) => {
          console.error('发生错误:', error)
        }
      }
    }
  }
}
</script>
```

### 使用ChatPanel组件

```vue
<template>
  <div>
    <ChatPanel
      :url="apiUrl"
      :app-name="appName"
      :domain-name="domainName"
      :enable-streaming="true"
      :enable-context="true"
      :callbacks="callbacks"
      @close="handleClose"
    />
  </div>
</template>

<script>
import { ChatPanel } from 'ai-suspended-ball-chat'

export default {
  name: 'App',
  components: {
    ChatPanel
  },
  data() {
    return {
      apiUrl: 'https://your-api-endpoint.com/chat',
      appName: 'my-app',
      domainName: 'user123',
      callbacks: {
        onUserMessage: (message) => {
          console.log('用户发送消息:', message)
        },
        onAssistantMessage: (message) => {
          console.log('AI回复:', message)
        },
        onError: (error) => {
          console.error('发生错误:', error)
        }
      }
    }
  },
  methods: {
    handleClose() {
      console.log('聊天面板已关闭')
    }
  }
}
</script>
```

### 使用Composition API

```vue
<template>
  <div id="app">
    <SuspendedBallChat
      :url="apiUrl"
      :app-name="appName"
      :domain-name="domainName"
      :enable-streaming="true"
      :enable-context="true"
      :enable-local-storage="true"
      :enable-voice-input="true"
      :callbacks="callbacks"
    />
  </div>
</template>

<script setup>
import { SuspendedBallChat } from 'ai-suspended-ball-chat'

const apiUrl = 'https://your-api-endpoint.com/chat'
const appName = 'my-app'
const domainName = 'user123'

const callbacks = {
  onUserMessage: (message) => {
    console.log('用户发送消息:', message)
  },
  onAssistantMessage: (message) => {
    console.log('AI回复:', message)
  },
  onError: (error) => {
    console.error('发生错误:', error)
  }
}
</script>
```

### 自定义图标

你可以通过 `custom-icon-url` 属性来自定义悬浮球的图标：

```vue
<template>
  <div id="app">
    <SuspendedBallChat
      :url="apiUrl"
      :app-name="appName"
      :domain-name="domainName"
      custom-icon-url="https://example.com/your-custom-icon.png"
      :enable-streaming="true"
      :enable-context="true"
      :enable-local-storage="true"
    />
  </div>
</template>

<script setup>
import { SuspendedBallChat } from 'ai-suspended-ball-chat'

const apiUrl = 'https://your-api-endpoint.com/chat'
const appName = 'my-app'
const domainName = 'user123'
</script>
```

**注意事项：**
- 支持PNG、JPG、SVG等常见图片格式
- 建议使用28x28像素或更大尺寸的图片
- 如果不提供 `custom-icon-url`，将使用默认的SVG图标
- 自定义图标会自动适应悬浮球的大小和样式

### 自定义AI助手头像

你可以通过 `assistant-config` 属性来自定义AI助手的头像：

```vue
<template>
  <div id="app">
    <SuspendedBallChat
      :url="apiUrl"
      :app-name="appName"
      :domain-name="domainName"
      :assistant-config="assistantConfig"
      :enable-streaming="true"
      :enable-context="true"
      :enable-local-storage="true"
    />
  </div>
</template>

<script setup>
import { SuspendedBallChat } from 'ai-suspended-ball-chat'

const apiUrl = 'https://your-api-endpoint.com/chat'
const appName = 'my-app'
const domainName = 'user123'

const assistantConfig = {
  avatar: 'https://example.com/assistant-avatar.png',
  name: '智能助手',
  description: '您的专属AI助手'
}
</script>
```

**注意事项：**
- 支持PNG、JPG、SVG等常见图片格式
- 建议使用32x32像素或更大尺寸的图片
- 如果不提供 `assistant-config.avatar`，将使用默认的SVG图标
- 自定义头像会自动适应头像容器的大小和样式

## 📋 API 参考

### SuspendedBallChat Props

| 属性名 | 类型 | 默认值 | 说明 |
|--------|------|--------|------|
| `url` | `string` | `'/nlweb/query'` | API接口地址 |
| `app-name` | `string` | `'ai-chat'` | 应用名称 |
| `domain-name` | `string` | `'user'` | 用户域名 |
| `disable-input` | `boolean` | `'false'` | 是否禁用输入框 |
| `custom-placeholder` | `string` | `'请输入你的问题...'` | 输入框的placeholder |
| `size` | `'small' \| 'medium' \| 'large'` | `'medium'` | 聊天面板大小 |
| `location` | `'left-top' \| 'left-center' \| 'left-bottom' \| 'right-top' \| 'right-center' \| 'right-bottom'` | `'right-center'` | 悬浮球位置 |
| `custom-icon-url` | `string` | - | 自定义悬浮球图标URL |
| `max-input-length` | `number` | `2000` | 用户输入最大字符数限制 |
| `enable-streaming` | `boolean` | `true` | 是否启用流式响应 |
| `enable-context` | `boolean` | `true` | 是否启用上下文记忆 |
| `enable-local-storage` | `boolean` | `true` | 是否启用本地存储 |
| `storage-key` | `string` | `'ai-chat-history'` | 本地存储键名 |
| `max-history-count` | `number` | `20` | 最大历史记录数量 |
| `enable-image-upload` | `boolean` | `false` | 是否启用图片上传 |
| `supported-custom-context` | `boolean` | `false` | 否启用页面内容(文件内容)选择引用功能 |
| `enable-voice-input` | `boolean` | `true` | 是否启用语音输入 |
| `enable-auto-speech` | `boolean` | `false` | 是否启用AI助理完成输出后自动语音播报 |
| `title` | `string` | `'AI助手'` | 聊天面板标题 |
| `show-header` | `boolean` | `true` | 是否显示头部 |
| `show-close-button` | `boolean` | `true` | 是否显示关闭按钮 |
| `show-clear-button` | `boolean` | `true` | 是否显示清除按钮 |
| `show-theme-toggle` | `boolean` | `false` | 是否显示白天/夜间模式切换按钮 |
| `show-feedback-button` | `boolean` | `false` | 是否显示工单提交按钮 |
| `welcome-config` | `WelcomeConfig` | - | 欢迎界面配置 |
| `preset-tasks` | `PresetTask[]` | - | 预设任务列表 |
| `assistant-config` | `AssistantConfig` | - | AI助手配置 |
| `custom-request-config` | `CustomRequestConfig` | - | 自定义请求配置 |
| `callbacks` | `ChatCallbacks` | - | 回调函数 |

### ChatPanel Props

| 属性名 | 类型 | 默认值 | 说明 |
|--------|------|--------|------|
| `url` | `string` | `'/nlweb/query'` | API接口地址 |
| `app-name` | `string` | `'ai-chat'` | 应用名称 |
| `domain-name` | `string` | `'user'` | 用户域名 |
| `disable-input` | `boolean` | `'false'` | 是否禁用输入框 |
| `custom-placeholder` | `string` | `'请输入你的问题...'` | 自定义输入框的placeholder |
| `max-input-length` | `number` | `2000` | 用户输入最大字符数限制 |
| `enable-streaming` | `boolean` | `true` | 是否启用流式响应 |
| `enable-context` | `boolean` | `true` | 是否启用上下文记忆 |
| `enable-local-storage` | `boolean` | `true` | 是否启用本地存储 |
| `storage-key` | `string` | `'ai-chat-history'` | 本地存储键名 |
| `max-history-count` | `number` | `20` | 最大历史记录数量 |
| `enable-image-upload` | `boolean` | `false` | 是否启用图片上传 |
| `supported-custom-context` | `boolean` | `false` | 否启用页面内容(文件内容)选择引用功能 |
| `enable-voice-input` | `boolean` | `true` | 是否启用语音输入 |
| `enable-auto-speech` | `boolean` | `false` | 是否启用AI助理完成输出后自动语音播报 |
| `title` | `string` | `'AI助手'` | 聊天面板标题 |
| `show-header` | `boolean` | `true` | 是否显示头部 |
| `show-close-button` | `boolean` | `true` | 是否显示关闭按钮 |
| `show-clear-button` | `boolean` | `true` | 是否显示清除按钮 |
| `show-theme-toggle` | `boolean` | `false` | 是否显示白天/夜间模式切换按钮 |
| `show-feedback-button` | `boolean` | `false` | 是否显示工单提交按钮 |
| `welcome-config` | `WelcomeConfig` | - | 欢迎界面配置 |
| `preset-tasks` | `PresetTask[]` | - | 预设任务列表 |
| `assistant-config` | `AssistantConfig` | - | AI助手配置 |
| `custom-request-config` | `CustomRequestConfig` | - | 自定义请求配置 |
| `callbacks` | `ChatCallbacks` | - | 回调函数 |

### Events

| 事件名 | 参数 | 说明 |
|--------|------|------|
| `close` | - | 聊天面板关闭时触发 |

### Methods

#### SuspendedBallChat Methods

| 方法名 | 参数 | 返回值 | 说明 |
|--------|------|--------|------|
| `sendMessage` | `message: string` | - | 主动发起AI对话 |
| `getChatState` | - | `ChatState` | 获取聊天状态 |
| `clearHistory` | - | - | 清除对话历史 |
| `stopRequest` | - | - | 停止当前请求 |
| `isStreaming` | - | `boolean` | 检查是否正在流式响应 |
| `openPanel` | - | - | 打开聊天面板 |
| `closePanel` | - | `boolean` | 关闭聊天面板 |
| `isPanelVisible` | - | `boolean` | 检查面板是否可见 |

#### ChatPanel Methods

| 方法名 | 参数 | 返回值 | 说明 |
|--------|------|--------|------|
| `sendMessage` | `message: string` | - | 主动发起AI对话 |
| `getChatState` | - | `ChatState` | 获取聊天状态 |
| `clearHistory` | - | - | 清除对话历史 |
| `stopRequest` | - | - | 停止当前请求 |
| `isStreaming` | - | `boolean` | 检查是否正在流式响应 |
| `scrollToBottom` | - | - | 滚动到底部 |

## 🔌 自定义后端接口需要返回数据格式

### 流式响应格式（Server-Sent Events）

**响应头设置：**
```
Content-Type: text/event-stream
Cache-Control: no-cache
Connection: close
Access-Control-Allow-Origin: *
```

**数据格式：**
每行返回一个JSON对象，以`\n\n`分隔

```json
{"code": 0, "result": "Vue.js是一个用于构建", "is_end": false}
{"code": 0, "result": "用户界面的渐进式", "is_end": false}
{"code": 0, "result": "JavaScript框架。", "is_end": false}
{"code": 0, "result": "", "is_end": true}
```

**字段说明：**
| 字段 | 类型 | 说明 |
|------|------|------|
| `code` | `number` | 状态码，0表示成功 |
| `result` | `string` | 返回的文本内容片段 |
| `is_end` | `boolean` | 是否为最后一个数据块 |

**node后端流式响应示例：**
```javascript
// node后端流式响应示例
let mockDataArr = [
  {"code": 0, "result": "# Vue.js特点介绍\n\n", "is_end": false},
  {"code": 0, "result": "## 1. 渐进式框架\n", "is_end": false},
  {"code": 0, "result": "Vue.js采用渐进式设计，", "is_end": false},
  {"code": 0, "result": "可以逐步集成到现有项目中。\n\n", "is_end": false},
  {"code": 0, "result": "## 2. 响应式数据绑定\n", "is_end": false},
  {"code": 0, "result": "数据变化时自动更新DOM，", "is_end": false},
  {"code": 0, "result": "无需手动操作。\n\n", "is_end": false},
  {"code": 0, "result": "```javascript\n", "is_end": false},
  {"code": 0, "result": "// Vue响应式示例\n", "is_end": false},
  {"code": 0, "result": "data() {\n  return {\n", "is_end": false},
  {"code": 0, "result": "    message: 'Hello Vue!'\n", "is_end": false},
  {"code": 0, "result": "  }\n}\n```\n\n", "is_end": false},
  {"code": 0, "result": "以上就是Vue.js的主要特点。", "is_end": false},
  {"code": 0, "result": "", "is_end": true}
]

// 流式响应示例
res.writeHead(200, {
  'Content-Type': 'text/event-stream',
  'Cache-Control': 'no-cache',
  'Connection': 'close',
  'Access-Control-Allow-Origin': '*'
})

mockDataArr.forEach((data, index) => {
  // 注意：每行返回一个JSON对象，以'\n\n'分隔
  res.write(JSON.stringify(data) +'\n\n');
  if (index === mockDataArr.length - 1) {
    res.end()
  }
})
```

### 普通响应格式（JSON）

**成功响应：**
```json
{
  "code": 0,
  "result": {
    "answer": "Vue.js是一个用于构建用户界面的渐进式JavaScript框架。它具有以下特点：\n\n1. **渐进式框架**：可以逐步采用\n2. **响应式数据绑定**：数据变化自动更新视图\n3. **组件化开发**：提高代码复用性\n4. **虚拟DOM**：提升性能\n5. **易学易用**：学习成本低"
  }
}
```

### 错误响应格式

**错误响应统一格式：**
```json
{
  "code": 1,
  "message": "错误描述",
  "error": "详细错误信息"
}
```

**常见错误码：**
| 错误码 | 说明 |
|--------|------|
| `0` | 成功 |
| `1` | 参数错误 |
| `2` | 认证失败 |
| `3` | 服务限流 |
| `4` | 服务异常 |
| `5` | 上下文过长 |

**错误响应示例：**
```json
{
  "code": 1,
  "message": "参数错误",
  "error": "query参数不能为空"
}
```

```json
{
  "code": 4,
  "message": "服务异常",
  "error": "AI服务暂时不可用，请稍后重试"
}
```

## 🔌 使用官方提供的AI接口

**如果你不希望自己去实现这个接口,您也可以选择官方提供的API接口**

接口文档:[https://luckycola.com.cn/public/docs/shares/sdk/ai-assistant.html](https://luckycola.com.cn/public/docs/shares/sdk/ai-assistant.html)

```js
<SuspendedBallChat
  :app-name="appName"
  :domain-name="domainName"
  :enable-streaming="true"
  :enable-context="true"
  :enable-local-storage="true"
  :callbacks="callbacks"
  url="https://luckycola.com.cn/aiTools/openAiAssistant"
  :custom-request-config="{
    headers: {
      'X-Custom-Header': 'custom-value',
    },
    customParams: {
      // 自定义的系统提示词
      systemPrompt: '你是一位精通各种编程语言的高级工程师,可以帮我用户解答各种编程问题.',
      // 官网(luckycola.com.cn)[用户中心]获取的AppKey
      appKey: '643d*********a'
    },
    requestParamProcessor: (baseParams, customParams) => {
      // ...
    }
    // ...组件其他详细配置请查看组件文档:https://www.npmjs.com/package/ai-suspended-ball-chat
/>
```


## 🎨 样式自定义

### 自定义主题

组件支持通过CSS变量自定义主题：

```css
:root {
  /* 主色调 */
  --ai-chat-primary-color: #007bff;
  --ai-chat-secondary-color: #6c757d;
  
  /* 背景色 */
  --ai-chat-bg-color: #ffffff;
  --ai-chat-panel-bg: #f8f9fa;
  
  /* 文字颜色 */
  --ai-chat-text-color: #262626;
  --ai-chat-text-muted: #595959;
  
  /* 边框颜色 */
  --ai-chat-border-color: #f0f0f0;
  
  /* 阴影 */
  --ai-chat-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
}
```

### 自定义样式

你可以通过CSS覆盖默认样式：

```css
/* 自定义悬浮球样式 */
.chat-bubble {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%) !important;
}

/* 自定义聊天面板样式 */
.chat-panel-container {
  border-radius: 20px !important;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2) !important;
}
```

## 🔧 高级配置

### 自定义请求配置

```javascript
const customRequestConfig = {
  headers: {
    'Authorization': 'Bearer your-token',
    'Content-Type': 'application/json'
  },
  timeout: 30000,
  retryCount: 3,
  retryDelay: 1000
}
```

### 欢迎界面配置

```javascript
const welcomeConfig = {
  title: '欢迎使用AI助手',
  description: '我是您的智能助手，有什么可以帮助您的吗？',
  avatar: 'https://example.com/avatar.png'
}
```

### 否启用页面内容(文件内容)选择引用功能

```javascript
<SuspendedBallChat
  :supported-custom-context="true"
/>
```

### AI助手配置

```javascript
const assistantConfig = {
  avatar: 'https://example.com/assistant-avatar.png',
  name: '智能助手',
  description: '您的专属AI助手'
}
```

### 预设任务配置

```javascript
const presetTasks = [
  {
    icon: '💡',
    title: '创意写作',
    description: '帮助您进行创意写作和内容创作'
  },
  {
    icon: '📊',
    title: '数据分析',
    description: '协助您进行数据分析和可视化'
  },
  {
    icon: '🔧',
    title: '技术支持',
    description: '提供技术问题和编程帮助'
  }
]
```

### 消息插入功能使用示例

新增的"获取AI消息"功能允许用户将AI回复的内容直接插入到其他应用或编辑器中，这在代码编辑器、文档编辑等场景中非常有用。

**启用插入功能：**

```javascript
<SuspendedBallChat
  :enable-insert-message="true"
  :callbacks="callbacks"
/>
```

**注意：** `enable-insert-message` 默认为 `false`，需要显式设置为 `true` 才能显示插入按钮。

```javascript
// 示例：将AI回复插入到代码编辑器
const callbacks = {
  clickAssistantMsgCallback: (message, index, messageObj) => {
    console.log('AI回复消息:', message, index, messageObj);
  }
}
```

### 回调函数配置

```javascript
const callbacks = {
  // 用户发送消息时触发
  onUserMessage: (message) => {
    console.log('用户消息:', message)
  },
  
  // AI回复时触发
  onAssistantMessage: (message) => {
    console.log('AI回复:', message)
  },
  
  // 流式响应开始
  onStreamStart: () => {
    console.log('开始流式响应')
  },
  
  // 流式响应进行中
  onStreamProgress: (partialMessage) => {
    console.log('流式响应进度:', partialMessage)
  },
  
  // 流式响应结束
  onStreamEnd: (fullMessage) => {
    console.log('流式响应结束:', fullMessage)
  },
  
  // 发生错误时触发
  onError: (error) => {
    console.error('错误:', error)
  },
  
  // 历史记录加载时触发
  onHistoryLoad: (history) => {
    console.log('历史记录:', history)
  },
  
  // 历史记录保存时触发
  onHistorySave: (history) => {
    console.log('保存历史记录:', history)
  },
  
  // 点击AI助理消息"插入含义"按钮时触发
  clickAssistantMsgCallback: (message, index, messageObj) => {
    console.log('插入含义:', { message, index, messageObj })
  },
  
  // 工单提交时触发
  onFeedbackSubmit: (data) => {
    console.log('工单提交:', data)
    // data 包含:
    // - issue: string (问题标题，最多30字)
    // - description: string (问题描述，最多2000字)
    // - images: FeedbackImageData[] (图片数组，最多3张)
    // - contact: string (联系方式，邮箱或手机号)
    
    // 示例：发送到后端
    fetch('/api/feedback', {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify({
        issue: data.issue,
        description: data.description,
        images: data.images.map(img => img.base64), // 使用base64
        contact: data.contact
      })
    })
    
    // 或者使用FormData上传原始文件
    const formData = new FormData()
    formData.append('issue', data.issue)
    formData.append('description', data.description)
    formData.append('contact', data.contact)
    data.images.forEach((img, index) => {
      formData.append(`image_${index}`, img.file) // 使用原始File对象
    })
    fetch('/api/feedback', {
      method: 'POST',
      body: formData
    })
  }
}
```

## 🎫 工单提交功能

组件支持收集需要人工处理的问题反馈，方便用户提交工单。

### 启用工单功能

```vue
<template>
  <SuspendedBallChat
    :show-feedback-button="true"
    :callbacks="callbacks"
  />
</template>

<script>
export default {
  data() {
    return {
      callbacks: {
        onFeedbackSubmit: (data) => {
          console.log('收到工单:', data)
          // 处理工单提交
          this.submitFeedback(data)
        }
      }
    }
  },
  methods: {
    async submitFeedback(data) {
      try {
        // 方式1: 使用JSON格式（base64图片）
        const response = await fetch('/api/feedback', {
          method: 'POST',
          headers: { 'Content-Type': 'application/json' },
          body: JSON.stringify({
            issue: data.issue,
            description: data.description,
            images: data.images.map(img => ({
              base64: img.base64,
              name: img.name,
              type: img.type,
              size: img.size
            })),
            contact: data.contact
          })
        })
        
        if (response.ok) {
          alert('工单提交成功！')
        }
      } catch (error) {
        console.error('工单提交失败:', error)
      }
    }
  }
}
</script>
```

## 📱 响应式设计

组件完全支持响应式设计，在不同屏幕尺寸下都能提供良好的用户体验：

- **桌面端**: 完整的聊天界面，支持拖拽和调整大小
- **平板端**: 适配中等屏幕，优化触摸交互
- **移动端**: 移动优先设计，支持手势操作

## 🔒 安全性

- 支持HTTPS请求
- 输入内容过滤和清理
- 防止XSS攻击
- 安全的本地存储

## 🌐 浏览器支持

- Chrome 88+
- Firefox 85+
- Safari 14+
- Edge 88+

## 📋 类型定义

### AssistantConfig

```typescript
interface AssistantConfig {
  avatar?: string      // AI助手头像URL
  name?: string        // AI助手名称
  description?: string // AI助手描述
}
```


## ❓ 常见问题

### Q: 样式不生效怎么办？

A: 从v0.1.33版本开始，样式已经内联到JS中，不再需要单独导入CSS文件。直接导入组件即可：

```javascript
import { SuspendedBallChat } from 'ai-suspended-ball-chat'
// 不需要再导入 CSS 文件
```

### Q: 如何自定义API接口？

A: 通过`url`属性设置API接口地址，通过`custom-request-config`配置请求参数：

```javascript
<SuspendedBallChat
  :url="'https://your-api.com/chat'"
  :custom-request-config="{
    headers: { 'Authorization': 'Bearer token' },
    timeout: 30000
  }"
/>
```

### Q: 如何禁用流式响应？

A: 设置`enable-streaming="false"`即可：

```javascript
<SuspendedBallChat :enable-streaming="false" />
```

### Q: 如何清除聊天历史？

A: 通过ref调用`clearHistory`方法：

```javascript
const chatRef = ref()

const clearHistory = () => {
  chatRef.value.clearHistory()
}
```

### Q: 如何获取聊天状态？

A: 通过ref调用`getChatState`方法：

```javascript
const chatRef = ref()

const getState = () => {
  const state = chatRef.value.getChatState()
  console.log('聊天状态:', state)
}
```

### Q: 如何启用/禁用语音输入功能？

A: 通过`enable-voice-input`属性控制语音输入功能：

```javascript
<!-- 启用语音输入 -->
<SuspendedBallChat :enable-voice-input="true" />

<!-- 禁用语音输入 -->
<SuspendedBallChat :enable-voice-input="false" />
```

### Q: 如何限制登录后才能使用?

A: 可以通过`disable-input`配合`custom-placeholder`属性来实现：

原理逻辑是: 如果用户未登录就禁用输入框并通过输入框的placeholder提示“登录后可发送消息”

```vue
<template>
  <div id="app">
    <SuspendedBallChat
      :disable-input="!isLogin"
      :custom-placeholder="isLogin ? '请输入你的消息' : '登录后可发送消息'"
    />
  </div>
</template>

<script setup>
import { ref } from 'vue'
import { SuspendedBallChat } from 'ai-suspended-ball-chat'

const isLogin = ref(false)
const apiUrl = 'https://your-api-endpoint.com/chat'
const appName = 'my-app'
const domainName = 'user123'
```

### Q: 语音输入不工作怎么办？

A: 请检查以下几点：

1. 确保浏览器支持Web Speech API
2. 确保已授权麦克风权限
3. 确保网站使用HTTPS协议（本地开发可使用localhost）
4. 检查浏览器控制台是否有错误信息

支持的浏览器：
- Chrome 25+
- Firefox 44+
- Safari 14.1+
- Edge 79+

### Q: 如何自定义语音输入的语言？

A: 目前语音输入默认使用中文简体（zh-CN）.

###  Q: 如何在小助理消息中支持解析mermaid语法

A: 如果需要支持解析mermaid语法请提前在你的项目中引入资源:https://cdn.jsdelivr.net/npm/mermaid@11.10.1/dist/mermaid.min.js

### Q: 组件是否支持“深度思考模式”模式？

A: beta版本已支持,如需使用请下载beta版本,主版本中将不支持“深度思考模式”模式。

### 📦 包体积优化建议

由于本组件支持代码高亮、数学公式等诸多功能，包体积较大。在业务场景使用建议按需加载：

#### 1. 动态导入（推荐）

```javascript
// 在需要时才加载组件
const loadChatComponent = async () => {
  const { SuspendedBallChat } = await import('ai-suspended-ball-chat')
  return SuspendedBallChat
}
```

#### 2. 路由懒加载

```javascript
// router.js
const routes = [
  {
    path: '/chat',
    component: () => import('ai-suspended-ball-chat').then(m => m.SuspendedBallChat)
  }
]
```

#### 3. 条件渲染（组合式 API）

```vue
<template>
  <div>
    <button @click="showChat = true">打开AI助手</button>
    <SuspendedBallChat
      v-if="showChat"
      :url="apiUrl"
      :app-name="appName"
      :domain-name="domainName"
    />
  </div>
</template>

<script setup>
import { ref } from 'vue'
import { SuspendedBallChat } from 'ai-suspended-ball-chat'

const showChat = ref(false)
const apiUrl = ref('your-api-url')
const appName = ref('your-app-name')
const domainName = ref('your-domain-name')
</script>
```

#### 4. 使用Suspense（Vue 3）

```vue
<template>
  <Suspense>
    <template #default>
      <SuspendedBallChat
        :url="apiUrl"
        :app-name="appName"
        :domain-name="domainName"
      />
    </template>
    <template #fallback>
      <div>加载中...</div>
    </template>
  </Suspense>
</template>

<script setup>
import { SuspendedBallChat } from 'ai-suspended-ball-chat'
</script>
```

#### 5. 按需导入特定功能

```javascript
// 如果只需要聊天面板，可以只导入ChatPanel
import { ChatPanel } from 'ai-suspended-ball-chat'

// 或者按需导入工具函数
import { createChatInstance } from 'ai-suspended-ball-chat'
```



#### 6. 组合式API按需加载

```vue
<template>
  <div>
    <button @click="loadChat">加载AI助手</button>
    <component :is="chatComponent" v-if="chatComponent" />
  </div>
</template>

<script setup>
import { ref } from 'vue'

const chatComponent = ref(null)

const loadChat = async () => {
  if (!chatComponent.value) {
    const { SuspendedBallChat } = await import('ai-suspended-ball-chat')
    chatComponent.value = SuspendedBallChat
  }
}
</script>
```

#### 7. 工厂函数模式

```javascript
// chatFactory.js
export const createChatComponent = async (type = 'SuspendedBallChat') => {
  const { [type]: Component } = await import('ai-suspended-ball-chat')
  return Component
}

// 在组件中使用（组合式 API）
<script setup>
import { createChatComponent } from './chatFactory'
import { ref, onMounted } from 'vue'

const SuspendedBallChat = ref(null)
const ChatPanel = ref(null)

onMounted(async () => {
  SuspendedBallChat.value = await createChatComponent('SuspendedBallChat')
  ChatPanel.value = await createChatComponent('ChatPanel')
})
</script>
```

**优化效果：**
- 初始包体积减少 60-80%
- 首屏加载速度提升
- 按需加载，提升用户体验
- 支持多种Vue版本和写法

## 📄 问题与交流

 1、问题建议可提交issue:
 https://github.com/mingle1998/AISuspendedBallChat/issues

 2、或者加入我们的QQ群:  592895347

 3、组件npm地址:
 https://www.npmjs.com/package/ai-suspended-ball-chat
