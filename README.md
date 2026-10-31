# 全局协作宪法（通用版）

一套给 AI 编程助手（Codex、Claude Code 通用）的全局行为规则：动手前先计划，按风险分级授权，交付前强制 review，修完沿用户原路径复现，经验分两条轨道沉淀成记忆。

在线阅读、复制和下载：<https://zeyu.zeylane.com/agents/>

## 文件

| 文件 | 用途 | 放到 |
|---|---|---|
| [`AGENTS.md`](AGENTS.md) | 规则正文，共 11 节 | `~/AGENTS.md` |
| [`CLAUDE.md`](CLAUDE.md) | 一行引用，让 Claude Code 载入 `~/AGENTS.md` | `~/.claude/CLAUDE.md` |

## 安装

1. 下载规则正文。已有 `~/AGENTS.md` 时这条命令只提示、不覆盖：

   ```bash
   test -e ~/AGENTS.md && echo "~/AGENTS.md 已存在，请先备份或手动合并" || curl -fsSL https://raw.githubusercontent.com/hellojx852872210-cmyk/agents-constitution/main/AGENTS.md -o ~/AGENTS.md
   ```

   然后把 `<你的称呼>`、`<项目>` 换成自己的。`~/llm-wiki`、`~/.agent-harness` 这类路径是建议约定，可按自己的目录改。

2. Codex：建一个软链接。已有 `~/.codex/AGENTS.md` 时会报 File exists 并停下。

   ```bash
   mkdir -p ~/.codex && ln -s ../AGENTS.md ~/.codex/AGENTS.md
   ```

3. Claude Code：在 `~/.claude/CLAUDE.md` 末尾追加一行引用，原有内容会保留。

   ```bash
   mkdir -p ~/.claude && echo '@~/AGENTS.md' >> ~/.claude/CLAUDE.md
   ```

验证：新开一个会话，问它「你读到 AGENTS.md 了吗，第 4 节讲什么」。

## 六条要点

- **先计划再动手**：简单任务一句话写清；多步骤用 checklist；高风险要带备份、回滚和授权门。（§2）
- **五道风险门**：只读、本地可逆直接做；外发、生产、真实资金必须当轮明确授权。（§4）
- **几条写死的硬线**：不打印密钥；生产机不编译；整份 JSON 的配置只合并目标键，不整包覆盖。（§4）
- **修完要复现**：沿用户原路径再走一遍才算修好，单元测试和接口探测只算旁证。（§6）
- **跨模型交叉审查**：作者是哪家模型，就换另一家来复核；第二意见先核对原文再采纳。（§6）
- **双轨记忆**：工具自带 memory 负责召回，Wiki 负责可审计的长期知识；规则晋升要有证据、能回滚。（§7）

## 说明

这是从一份实际在用的个人规则脱敏整理出来的通用版：去掉了个人称呼、具体项目、事故细节和内部路径，方法论条款保持原样。欢迎按自己的工作方式删改。

## 许可

[MIT](LICENSE)：可自由使用、修改和再分发。
