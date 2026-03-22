# patent-disclosure-drafter

用于从粗糙创新点生成中文专利交底书的 Codex skill 源码仓库。

这个仓库保存的是 skill bundle 本身，而不是评测 harness。skill 的核心目标是：

- 把简短技术想法扩展成完整的中文专利交底书草案
- 固定输出九个章节，并保持章节顺序稳定
- 强化术语一致性、实施例完整性、技术要点提炼和附图输出
- 默认生成可渲染的 Mermaid 附图

## Repository Layout

- `SKILL.md`: skill 主说明文件，也是主要可变对象
- `agents/openai.yaml`: skill 的界面元数据
- `references/output_contract.md`: 固定输出契约
- `references/figure_generation.md`: 附图生成规范
- `references/template_mapping.md`: 软件、AI、结构类发明的模板映射
- `references/examples.md`: 风格与完整性示例

## Usage

这个仓库通常有两种使用方式：

1. 作为本地 skill 源码直接维护和迭代
2. 作为 `patent_agent_drafter` 的被评测对象参与 `evaluate` / `evolve`

如果你已经有评测 harness，可以像下面这样引用当前 skill 目录：

```bash
uv run patent-evolve evaluate \
  --skill-dir ../patent-disclosure-drafter \
  --judge-model gpt-5.4
```

## Design Notes

- 默认少追问，优先做技术上合理的显式补全
- 不默认做外部检索，不承诺新颖性或授权结果
- 软件/AI 类发明强调模块、数据流、控制逻辑和实施例差异
- 结构类发明强调装配步骤、锁定逻辑、受力路径和限位关系
- `SKILL.md` 是核心入口；引用资料用于补充固定约束和风格锚点

## Status

当前仓库用于维护 `patent-disclosure-drafter` 的可演进版本，并已独立托管到 GitHub。
