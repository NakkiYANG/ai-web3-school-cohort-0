# 打卡草稿（2026-05-19）

**今日学习**
- 学习了 NFT `mint()` 场景下的重入风险：`_safeMint` 可能触发 `onERC721Received` 外部回调，在状态尚未更新完全时被重入。
- 修复方向：Checks-Effects-Interactions 或使用 `ReentrancyGuard`。

**今日产出**
- 在学习仓库新增 1 条审计条目（High）：`mint()` 缺少重入保护导致可超发。

**明日行动**
- 补全 NFT 审计助手的 Threat model，并整理 3–5 个常见漏洞 snippet。

**参考链接**
- Repo: https://github.com/NakkiYANG/ai-web3-school-cohort-0
- Finding: tasks/audit-findings/2026-05-19_missing-reentrancy-in-mint.md
