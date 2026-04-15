# Claude Skill Hub

Curated external plugins and skills worth installing on a per-project basis.
To install any plugin: `claude plugin install [install-command]`
To use a specific skill in a project, paste the raw SKILL.md URL into your project CLAUDE.md.

---

## Vercel Plugin
**Repo:** https://github.com/vercel/vercel-plugin
**Install:** `claude plugin install vercel@vercel`
**Use when:** Building or deploying anything on Vercel — Next.js, AI apps, serverless functions.

| Skill | Raw URL | Use for |
|---|---|---|
| nextjs | https://raw.githubusercontent.com/vercel/vercel-plugin/main/skills/nextjs/SKILL.md | Next.js App Router projects |
| ai-sdk | https://raw.githubusercontent.com/vercel/vercel-plugin/main/skills/ai-sdk/SKILL.md | AI-powered features, chat, streaming |
| ai-gateway | https://raw.githubusercontent.com/vercel/vercel-plugin/main/skills/ai-gateway/SKILL.md | Multi-provider AI routing |
| vercel-functions | https://raw.githubusercontent.com/vercel/vercel-plugin/main/skills/vercel-functions/SKILL.md | Serverless, Edge, Fluid Compute |
| deployments-cicd | https://raw.githubusercontent.com/vercel/vercel-plugin/main/skills/deployments-cicd/SKILL.md | CI/CD, preview URLs, rollbacks |
| vercel-storage | https://raw.githubusercontent.com/vercel/vercel-plugin/main/skills/vercel-storage/SKILL.md | Blob, Edge Config, Neon, Upstash |
| auth | https://raw.githubusercontent.com/vercel/vercel-plugin/main/skills/auth/SKILL.md | Clerk, Descope, Auth0 |
| shadcn | https://raw.githubusercontent.com/vercel/vercel-plugin/main/skills/shadcn/SKILL.md | shadcn/ui component system |
| routing-middleware | https://raw.githubusercontent.com/vercel/vercel-plugin/main/skills/routing-middleware/SKILL.md | Request interception, rewrites |
| workflow | https://raw.githubusercontent.com/vercel/vercel-plugin/main/skills/workflow/SKILL.md | Durable workflows, crash recovery |
| react-best-practices | https://raw.githubusercontent.com/vercel/vercel-plugin/main/skills/react-best-practices/SKILL.md | React/TSX quality review |
| turbopack | https://raw.githubusercontent.com/vercel/vercel-plugin/main/skills/turbopack/SKILL.md | Next.js bundler optimization |
| vercel-sandbox | https://raw.githubusercontent.com/vercel/vercel-plugin/main/skills/vercel-sandbox/SKILL.md | Sandboxed code execution |
| env-vars | https://raw.githubusercontent.com/vercel/vercel-plugin/main/skills/env-vars/SKILL.md | Environment variable management |
| marketplace | https://raw.githubusercontent.com/vercel/vercel-plugin/main/skills/marketplace/SKILL.md | Vercel Marketplace integrations |
| verification | https://raw.githubusercontent.com/vercel/vercel-plugin/main/skills/verification/SKILL.md | End-to-end flow verification |
| next-upgrade | https://raw.githubusercontent.com/vercel/vercel-plugin/main/skills/next-upgrade/SKILL.md | Next.js version upgrades |
| chat-sdk | https://raw.githubusercontent.com/vercel/vercel-plugin/main/skills/chat-sdk/SKILL.md | Slack/Telegram/Discord bots |
| next-cache-components | https://raw.githubusercontent.com/vercel/vercel-plugin/main/skills/next-cache-components/SKILL.md | Next.js 16 cache components |
| next-forge | https://raw.githubusercontent.com/vercel/vercel-plugin/main/skills/next-forge/SKILL.md | next-forge monorepo SaaS starter |
| runtime-cache | https://raw.githubusercontent.com/vercel/vercel-plugin/main/skills/runtime-cache/SKILL.md | Ephemeral per-region cache |
| vercel-cli | https://raw.githubusercontent.com/vercel/vercel-plugin/main/skills/vercel-cli/SKILL.md | Vercel CLI commands |
| bootstrap | https://raw.githubusercontent.com/vercel/vercel-plugin/main/skills/bootstrap/SKILL.md | Project bootstrapping |
| vercel-agent | https://raw.githubusercontent.com/vercel/vercel-plugin/main/skills/vercel-agent/SKILL.md | AI code review, incident investigation |

---

## Claude-Mem (Persistent Memory)
**Repo:** https://github.com/thedotmack/claude-mem
**Install:** `claude plugin install claude-mem@thedotmack`
**Use when:** Any project where you want Claude to remember context across sessions.

| Skill | Raw URL | Use for |
|---|---|---|
| make-plan | https://raw.githubusercontent.com/thedotmack/claude-mem/main/plugin/skills/make-plan/SKILL.md | Detailed phased implementation plans |
| do | https://raw.githubusercontent.com/thedotmack/claude-mem/main/plugin/skills/do/SKILL.md | Execute phased plans with subagents |
| smart-explore | https://raw.githubusercontent.com/thedotmack/claude-mem/main/plugin/skills/smart-explore/SKILL.md | Token-efficient AST code search |
| mem-search | https://raw.githubusercontent.com/thedotmack/claude-mem/main/plugin/skills/mem-search/SKILL.md | Cross-session memory search |
| timeline-report | https://raw.githubusercontent.com/thedotmack/claude-mem/main/plugin/skills/timeline-report/SKILL.md | Project journey narrative report |

---

## UI/UX Pro Max
**Repo:** https://github.com/nextlevelbuilder/ui-ux-pro-max-skill
**Install:** `claude plugin install ui-ux-pro-max@ui-ux-pro-max-skill`
**Use when:** Any frontend project — landing pages, dashboards, design systems.

| Skill | Raw URL | Use for |
|---|---|---|
| ui-ux-pro-max | https://raw.githubusercontent.com/nextlevelbuilder/ui-ux-pro-max-skill/main/.claude/skills/ui-ux-pro-max/SKILL.md | Full UI/UX design (50+ styles, 161 palettes) |
| design | https://raw.githubusercontent.com/nextlevelbuilder/ui-ux-pro-max-skill/main/.claude/skills/design/SKILL.md | General design guidance |
| ui-styling | https://raw.githubusercontent.com/nextlevelbuilder/ui-ux-pro-max-skill/main/.claude/skills/ui-styling/SKILL.md | CSS/styling patterns |
| brand | https://raw.githubusercontent.com/nextlevelbuilder/ui-ux-pro-max-skill/main/.claude/skills/brand/SKILL.md | Brand identity |
| design-system | https://raw.githubusercontent.com/nextlevelbuilder/ui-ux-pro-max-skill/main/.claude/skills/design-system/SKILL.md | Design system creation |
| banner-design | https://raw.githubusercontent.com/nextlevelbuilder/ui-ux-pro-max-skill/main/.claude/skills/banner-design/SKILL.md | Banner/ad design |
| slides | https://raw.githubusercontent.com/nextlevelbuilder/ui-ux-pro-max-skill/main/.claude/skills/slides/SKILL.md | Slide deck design |

---

## Figma (Anthropic Official)
**Repo:** https://github.com/anthropics/claude-plugins-official
**Install:** `claude plugin install figma@claude-plugins-official`
**Use when:** Implementing Figma designs or generating Figma files from code.

| Skill | Raw URL | Use for |
|---|---|---|
| figma-implement-design | https://raw.githubusercontent.com/anthropics/claude-plugins-official/main/plugins/figma/skills/figma-implement-design/SKILL.md | Figma design → production code |
| figma-generate-design | https://raw.githubusercontent.com/anthropics/claude-plugins-official/main/plugins/figma/skills/figma-generate-design/SKILL.md | App → Figma layout |
| figma-generate-library | https://raw.githubusercontent.com/anthropics/claude-plugins-official/main/plugins/figma/skills/figma-generate-library/SKILL.md | Build design system in Figma |
| figma-use | https://raw.githubusercontent.com/anthropics/claude-plugins-official/main/plugins/figma/skills/figma-use/SKILL.md | Prerequisite for all Figma tool calls |
| figma-code-connect | https://raw.githubusercontent.com/anthropics/claude-plugins-official/main/plugins/figma/skills/figma-code-connect/SKILL.md | Figma Code Connect templates |
| figma-create-design-system-rules | https://raw.githubusercontent.com/anthropics/claude-plugins-official/main/plugins/figma/skills/figma-create-design-system-rules/SKILL.md | Generate design system rules |
