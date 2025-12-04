# 利用するライブラリ・フレームワーク

- ライブラリは必要になった時にだけ、最小限の構成でセットアップすることを心がけてください。
- ライブラリを追加・削除した場合は必ず「利用中のライブラリ・フレームワーク」を更新してください。
- これらのライブラリの使用方法について、専用のMCPがない場合、 Context7 MCP ツールを用いて正しいバージョンのドキュメントを参照してください。

- 基本となる構成
  - node 管理: nodenv
  - package manager: bun
  - linter・formatter: biome
  - language: Typescript
  - validation: Zod
  - flamework: Nextjs 16 next-devtools-mcp
  - CSS: tailwind css
  - component: shadcn(use mcp), Vercel AI Elements(use mcp)
  - animation: motion-plus(旧Framer motionの有料上位版)
  - icon: lucide-react
  - hosting: Vercel
- 必要があれば順次追加(ユーザーの許可が必要)
  - AI・LLM: Vercel AI SDK
    - model provider: Vercel AI Gateway
      - gemini-2.5-flash-lite(汎用タスク)
      - grok-4-fast-non-reasoning(少し高度なタスク)
  - Auth: Better Auth(Auth.js に近いシンプルなもの)
  - DB・ベクトル DB: Turso
  - ORM: Drizzle
  - mail: Resend
  - email api: Resend
  - store: Zustand（useContext で十分な場合は必要なし）
  - Unit, Integration, and E2E Testing: Vitest + Playwright
  - Backend (queue, microservices, Kafka, SQS, heavy AI processing): Vercel Workflow (with the use workflow directive)
  - cron: Vercel cron jobs

# 利用中のライブラリ・フレームワーク

-
