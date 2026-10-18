# AGENTS.md — 给 AI Agent 的工作指引

人类读者请看 [README.md](README.md)。

## 这个仓库是什么

`cyb-mlps-level-checker` 是 SynomosAI 平台的**声明式域 Profile 骨架**（domain/1.0），不是可运行 SDK，也不是已上线产品。当前状态 RESERVED：四件套已建好，等待有资质的运营方认领并填注 `operator` / `checker_endpoint`。

核心资产：`domain.manifest.json`（声明）、`gate-map.json`（摩擦五级）、`privacy.json`（隐私）、`checker.io.json`（MCP 契约）。

## 可用的工作命令

```bash
git clone https://github.com/SynomosAI/cyb-mlps-level-checker.git
cd cyb-mlps-level-checker
cat domain.manifest.json                  # 通读声明
python -m json.tool domain.manifest.json  # 校验 JSON 合法
```

本仓无运行时依赖；**不要尝试「运行」本仓**。

## 约定（Do）

- 修改属性或红线后，必须同步 `gate-map.json`（每条红线都要有对应规则），并重新跑平台校验器自测。
- 新增属性时同步更新 `privacy.json` 的 `data_categories[].attr_keys`。
- 保持 `checker.io.json` 的输出状态词表（shown / missing / expired / unverifiable）不变。

## 禁止（Don't）

- 不要自行定级，也不要输出「已符合等保要求 / 已合规」类结论——定级权在专家评审与公安机关。
- 不要改动 `LICENSE` / `LICENSE-CONTENT` 的版权主体，不要改 `CODEOWNERS`。
- 不要提交任何密钥、真实备案证明编号或测评报告；示例证据用占位指纹。
- 不要建议降低定级、规避测评、简化安全措施或事后补材料。

## 边界

本域只覆盖等保定级、公安机关备案、等级测评、关基认定与叠加义务属性的出示与核验；不替代专家评审与公安机关的定级决定，不构成法律意见。
