このプロジェクトで使う MCP サーバーの設定方法

## context7

context7 は API KEY を取得して使う。
`${CONTEXT7_API_KEY}`は.zshrc などで自分で定義する。

## config.toml 用 (Codex)

```
[mcp_servers.context7]
args = ["-y", "@upstash/context7-mcp", "--api-key", "YOUR_API_KEY"]
command = "npx"
startup_timeout_ms = 20_000

[mcp_servers.next-devtools]
command = "npx"
args = ["-y", "next-devtools-mcp@latest"]
startup_timeout_ms = 30000

[mcp_servers.shadcn]
command = "npx"
args = ["shadcn@latest", "mcp"]
startup_timeout_ms = 30000

[mcp_servers.ai-elements]
command = "npx"
args = ["-y", "mcp-remote", "https://registry.ai-sdk.dev/api/mcp"]
startup_timeout_ms = 30000

[mcp_servers.playwright]
command = "npx"
args = ["@playwright/mcp@latest"]
startup_timeout_ms = 30000

[mcp_servers.chrome-devtools]
command = "npx"
args = ["-y", "chrome-devtools-mcp@latest"]
startup_timeout_ms = 30000

[mcp_servers.motion]
command = "npx"
args = [
  "-y",
  "https://api.motion.dev/registry.tgz?package=motion-studio-mcp&version=1.0.0&token=${MOTION_API_KEY}"
]
```

## mcp.json 用 (Cursor)

```
{
  "mcpServers": {
    "context7": {
      "url": "https://mcp.context7.com/mcp",
      "headers": {
        "CONTEXT7_API_KEY": "${CONTEXT7_API_KEY}"
      }
    },
    "next-devtools": {
      "command": "npx",
      "args": ["-y", "next-devtools-mcp@latest"]
    },
    "shadcn": {
      "command": "npx",
      "args": ["shadcn@latest", "mcp"]
    },
    "ai-elements": {
      "command": "npx",
      "args": ["-y", "mcp-remote", "https://registry.ai-sdk.dev/api/mcp"]
    },
    "playwright": {
      "command": "npx",
      "args": ["@playwright/mcp@latest"]
    },
    "chrome-devtools": {
      "command": "npx",
      "args": ["-y", "chrome-devtools-mcp@latest", "--wsEndpoint=ws://127.0.0.1:9222/devtools/browser/<id>"]
    },
    "motion": {
      "command": "npx",
      "args": [
        "-y",
        "https://api.motion.dev/registry.tgz?package=motion-studio-mcp&version=1.0.0&token=${MOTION_API_KEY}"
      ]
    }
}
}
```

## .mcp.json 用 (Claude Code)
MOTION_API_KEYの変数が展開されないので、一時的に~/.zshrcから変数を取得する運用にする。
```
{
  "mcpServers": {
    "context7": {
      "command": "npx",
      "args": ["-y", "@upstash/context7-mcp", "--api-key", "${CONTEXT7_API_KEY}"]
    },
    "next-devtools": {
      "command": "npx",
      "args": ["-y", "next-devtools-mcp@latest"]
    },
    "shadcn": {
      "command": "npx",
      "args": ["shadcn@latest", "mcp"]
    },
    "ai-elements": {
      "command": "npx",
      "args": ["-y", "mcp-remote", "https://registry.ai-sdk.dev/api/mcp"]
    },
    "playwright": {
      "command": "npx",
      "args": ["@playwright/mcp@latest"]
    },
    "chrome-devtools": {
      "command": "npx",
      "args": ["-y", "chrome-devtools-mcp@latest", "--wsEndpoint=ws://127.0.0.1:9222/devtools/browser/<id>"]
    },
    "motion": {
      "command": "zsh",
      "args": [
        "-c",
        "source ~/.zshrc 2>/dev/null; npx -y \"https://api.motion.dev/registry.tgz?package=motion-studio-mcp&version=1.0.0&token=$MOTION_API_KEY\""
      ]
    }
  }
}
```
