# Cyber-Jianghu-Decision-2B「江湖策」

Cyber-Jianghu（虚境：江湖）玩家侧意图决策模型分发仓。

- 底座：Qwen/Qwen3.5-2B（Apache-2.0）+ StartLux LoRA 配方，自有 trace 微调
- 任务：两段式管线第二段——把"人魂认知摘要 + 世界状态"转成结构化意图
  （act1 动作选择 + 实体绑定），letter logits 直读，零文本生成
- 评测：held-out 352 条（同口径），动作选择 top1 94.0% / top3 98.9%，
  第 2 动作 81.3%，物品绑定覆盖内约 99%

## 文件（Release: model-v1）

| 文件 | 说明 |
| --- | --- |
| manifest.json | 版本清单（版本号、文件字节数、sha256） |
| decision_config.json | letter token ids（32..57）+ 校准温度 1.3742 |
| Cyber-Jianghu-Decision-2B-Q5_K_M.gguf | 默认档位（约 1.41GB） |
| Cyber-Jianghu-Decision-2B-Q4_K_S.gguf | 低配档位（约 1.21GB，可用内存不足时自动降档） |

## 使用

Cyber-Jianghu Agent 默认从本仓拉取（ModelScope 主源 + GitHub 备源，
sha256 逐文件校验）。详见主仓 `crates/agent/docs/decision_model.md`。

## 许可

Apache-2.0（底座与训练代码同许可，数据为自产 trace）。
