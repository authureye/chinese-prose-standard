# 标准汉语 · Agent Skill

一个约束 AI 中文写作的 skill，管三件事：句子怎么排，标点怎么点，话怎么说。

它解决的是同一个毛病：AI 写出来的中文读着像公文摘要、产品说明或者系统提示词，主语缺一半，一句话拆成三截，结尾还要升华一句。这份规范把这些逐条列成可执行的动作，写完照着改。

## 安装

Claude Code，走插件市场：

```
claude plugin marketplace add <owner>/chinese-prose-standard
claude plugin install chinese-prose-standard@chinese-prose
```

其他 agent 直接放目录。把 `skills/chinese-prose-standard/` 整个复制到对应的 skills 目录即可：

| agent | 全局目录 | 项目内目录 |
| --- | --- | --- |
| Claude Code | `~/.claude/skills/` | `.claude/skills/` |
| Cursor | `~/.cursor/skills/` | `.cursor/skills/` 或 `.agents/skills/` |
| Codex | `~/.codex/skills/` | `.agents/skills/` |
| GitHub Copilot | `~/.copilot/skills/` | `.github/skills/` |

通用的做法是放进 `.agents/skills/`，再把另外两个目录软链过来。

## 里面有什么

```
chinese-prose-standard/
├── SKILL.md                  执行摘要，写作前读这一份
└── references/
    ├── standard-chinese.md   语序与书面规范全文，十三节
    └── ai-tone-blacklist.md  腔调词表与结构清单，四级分档
```

`SKILL.md` 第一节给了一条压过其他所有细则的原则：写出来要像一个中文母语的成年人在说话。判断办法是出声读一遍，要换气的地方就是该断句的地方，读完还得回头重读的，就是没写清楚。

`references/standard-chinese.md` 按定语顺序、状语顺序、虚词位置、长句切分、重点不后置几个维度展开，第十一节列了十种权威资料，包括《现代汉语八百词》、《语法修辞讲话》、GB/T 15834-2011 标点符号用法、BCC 语料库，以及戴浩一的时间顺序原则。

`references/ai-tone-blacklist.md` 是词表，分四档：字面命中的盖章句、结构性的自我表演、通用 AI 套语、霸总腔。末尾有例外条款，引用原文、写小说、用户指定保留这三种情形一律放行。

## 触发方式

skill 平时只暴露 `name` 和 `description` 两行，正文在命中后才加载。所以 description 里写进了真实会说的词：汉语规范、语序、说人话、标准汉语、AI 腔、套话、霸总腔。

也可以显式调用，在 Claude Code 里输入 `/chinese-prose-standard`。

## 来源

改编自一份个人写作准则。「电报体」一节是新增的，原文没有，记的是短句堆砌的另一种表现。公开版删去了与具体模型版本绑定的部分和内部撤销流程，词表与语序规范原样保留。

权威依据见 `references/standard-chinese.md` 第十一节。本仓库是对这些资料的摘要与实践整理，不替代原书。

## 许可

MIT。词表部分属于观察记录，不是语言学结论，按需增删。
