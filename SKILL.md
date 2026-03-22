---
name: patent-disclosure-drafter
description: generate a complete chinese patent disclosure from a rough invention idea and optional background details. use when the user wants ai to expand a technical concept into a formal patent disclosure that strictly follows a disclosure template, including title, definitions, technical field, background technology, invention purpose, technical solution, embodiments, protectable technical points, drawings, and other supporting sections. prioritize completeness, consistent terminology, formal disclosure style, and renderable figures in the drawings section. use even when the user provides only a rough idea; make reasonable technical assumptions instead of repeatedly asking follow-up questions. do not rely on external search in the first version.
---

# Patent Disclosure Drafter

Treat the task as structured disclosure drafting, not generic brainstorming. Turn a rough technical idea into a complete Chinese patent disclosure that another patent professional can directly refine.

## Operating mode

- Accept a rough invention idea plus any optional background details.
- Ask as few follow-up questions as possible.
- If details are missing, make technically plausible assumptions and continue drafting.
- Keep terminology stable across all sections.
- Write in formal Chinese suitable for disclosure drafting.
- Do not mention internal reasoning, hidden roles, or system workflow in the output.
- Do not perform external patent search or claim legal certainty in the first version.
- Keep the draft compact but concrete. Avoid repetitive filler, and do not restate the same invention summary in every section.
- Prefer a dense, usable first draft, but do not underwrite key sections. When detail is sparse, expand technical mechanism, module relationships, control logic, parameter choices, and embodiment differences instead of staying short.
- By default, generate renderable diagrams in the 附图 section instead of stopping at textual figure suggestions.

## Required output

Always produce a complete disclosure that follows this exact section order unless the user explicitly asks for a different format:

1. 初拟的发明（或实用新型）名称
2. 名词解释
3. 所属技术领域
4. 背景技术
5. 发明创造的目的
6. 发明创造的技术方案以及具体实施例
7. 发明人认为要保护的发明内容的技术要点以及相应的有益效果
8. 附图
9. 其他

The heading text should match the section names above exactly. Optional numbering is allowed, but do not rename, merge, omit, or reorder sections. Do not add extra top-level sections before or after them.

## Output Contract

Use [output_contract.md](references/output_contract.md) as the fixed output contract. The final response must contain only the disclosure itself, with the nine required headings in the exact order above.
Read [figure_generation.md](references/figure_generation.md) before drafting the 附图 section.

## Drafting workflow

1. Normalize the invention idea.
   - Restate the technical object, use scenario, likely mechanism, and expected technical effect.
   - Classify the invention as one of: software/system, AI/algorithm, device/structure, or mixed software-hardware.
   - Infer missing but necessary assumptions without stopping.

2. Lock terminology before drafting.
   - Choose 4-6 canonical technical terms or abbreviations only.
   - Define each term once in 名词解释.
   - Reuse every canonical term at least once in sections 4-7.
   - Remove synonyms. One concept should have one stable name.

3. Build the background section.
   - Describe the closest plausible prior art.
   - State the main technical problem and optional secondary technical problems.
   - Explain why the problem arises from the prior art.
   - Prefer explicit wording such as `现有技术通常采用...` and `现有技术至少存在以下技术问题...`.
   - Keep the problem technical rather than commercial.

4. Draft the purpose section.
   - Link the technical problem, technical means, and technical effect in one compact section.
   - Prefer explicit wording such as `本发明的目的在于...` or `本实用新型的目的在于...`.

5. Draft the technical solution and embodiments.
   - Describe the core solution with concrete structure, relationships, workflow, and control logic.
   - Use explicit subheadings `实施例一` and `实施例二` by default. Add more embodiments only when they add technical value.
   - Include module relationships, execution flow, working principle, and alternatives as applicable.
   - Make this the longest section of the disclosure.
   - Expand this section until the prose of section 6 is no less than 2000 Chinese characters.
   - For sparse user input, add technically reasonable defaults in the embodiments instead of apologizing for missing data.

6. Extract protectable technical points.
   - Rank them from most important to least important.
   - For each point, explain the benefit relative to the prior art.
   - Always provide at least 3 numbered points.
   - Prefer the pattern `技术特征 + 作用机制 + 有益效果`.

7. Plan and generate figures.
   - Decide the figure set before writing section 8. By default, prepare at least `图1` and `图2`, and add `图3` only when it materially improves clarity.
   - Map invention type to figure types, such as `系统架构图` / `模块关系图` / `流程图` / `时序图` / `结构示意图` / `装配流程图` / `受力或控制关系图`.
   - Reuse the canonical terminology from 名词解释 and section 6 inside figure labels.
   - Generate renderable Mermaid code blocks directly in section 8 unless the user explicitly asks for text-only figure descriptions.

8. Add other supporting references.
   - In the 其他 section, include concrete retrieval hints, optional standards/interfaces, or implementation notes rather than generic filler.

## Section contract

### 1. 初拟的发明（或实用新型）名称

- Use a technically specific title.
- Avoid vague names such as `一种智能方法` when the mechanism can be stated more precisely.

### 2. 名词解释

- Define 4-6 important technical terms or abbreviations only.
- Use one canonical term per concept and remove synonyms.
- Format each entry as `术语：定义` on its own line.
- Do not place numbered prefixes, bullets, or parentheses before the term itself.
- Write each term so it can be reused verbatim in later sections.
- Do not define terms that never appear later.

### 3. 所属技术领域

- State the direct technical field and, when useful, the application scenario.
- Keep it concise.

### 4. 背景技术

- Describe the closest plausible baseline system, structure, or workflow.
- Explicitly state the main technical problem and, when helpful, one or two secondary technical problems.
- Explain the cause of each problem, not just the consequence.
- Frame the problem technically rather than commercially.
- Do not compress this into a single short sentence. Make the prior-art -> defect -> cause chain explicit.

### 5. 发明创造的目的

- Explicitly connect `待解决的技术问题 -> 采用的技术手段 -> 达到的技术效果`.
- Keep it compact, but ensure the purpose is clearly traceable to the background problems.
- Do not write only a slogan such as `提高效率`.

### 6. 发明创造的技术方案以及具体实施例

Unless the user explicitly asks for a different structure, organize this section in the following order:

1. 总体技术方案或总体结构
2. 关键组成部分/功能模块/部件关系
3. 数据流、信号流、连接关系或装配关系
4. 工作原理、控制逻辑或执行流程
5. 实施例一
6. 实施例二
7. 可替代方案或可选变体

Apply the right technical vocabulary for the invention type:

- software/system: modules, interfaces, data, control flow, orchestration, deployment, scoring logic
- AI/algorithm: feature pipeline, model input/output, training or inference flow, feedback logic, routing strategy
- device/structure: components, connection relationships, positional relationships, assembly steps, locking or limiting mechanism, force/signal transmission path
- mixed system: explain both physical structure and software coordination where relevant

To keep the disclosure technically concrete, section 6 should naturally use several technical nouns that fit the invention, such as `模块` `单元` `装置` `步骤` `流程` `控制` `数据` `接口` `策略` `逻辑` `部署` `训练` `推理` `评分`. Use only the ones that genuinely match the invention type.
For device/structure inventions, do not stop at listing parts. Explicitly add a short paragraph for `装配步骤` or `安装流程`, and another paragraph for `锁定控制逻辑` or `受力传递逻辑`, so the mechanism is described in action rather than as a static parts list.

### 7. 发明人认为要保护的发明内容的技术要点以及相应的有益效果

- Use an ASCII numbered list from highest importance to lowest importance, such as `1.` `2.` `3.`.
- Provide at least 3 technical points by default.
- Each point should include both the protectable feature and the corresponding beneficial effect relative to prior art.
- Keep the points concrete enough to support later claim drafting.
- Prefer wording such as `通过...，从而...，其有益效果在于...`.

### 8. 附图

- Always provide at least 2 figures.
- Each figure must contain:
  - one sentence such as `图1为...` or `图2为...`;
  - one Mermaid code block immediately after the sentence.
- Prefer one figure for overall structure and one figure for process/control/assembly logic.
- Use exact figure names that are technically meaningful for the invention type.
- Keep figure labels aligned with the canonical terms already defined in 名词解释.
- Use Mermaid that can render in standard markdown viewers. Prefer `flowchart TB/LR`, `sequenceDiagram`, or `stateDiagram-v2`.
- For device/structure inventions, use Mermaid to draw a functional schematic of component relationships, assembly sequence, locking path, or force transmission path. Do not pretend it is a dimensioned CAD drawing.
- If the platform obviously cannot render Mermaid or the user explicitly forbids code blocks, fall back to textual figure descriptions only, but default behavior is to output Mermaid.

### 9. 其他

- Provide at least 3 concrete items, such as retrieval keywords, candidate IPC/CPC directions, optional standards or interfaces, engineering assumptions, or future narrowing directions.
- Do not leave this section as a single vague sentence.

## Length floor

- The prose of section 6 `发明创造的技术方案以及具体实施例` must be no less than 2000 Chinese characters.
- The full disclosure prose must be no less than 4000 Chinese characters.
- Headings and Mermaid code blocks do not count toward the prose floor.
- If the draft is still short, expand sections 4, 6, 7, and 9 with additional technical detail rather than adding filler.
- Prefer expanding with mechanism, workflow, control conditions, signal/data paths, assembly constraints, variant differences, operating thresholds, and failure handling.

## Response budget

- Target total prose of roughly 4000-5500 Chinese characters when the user does not request a different depth.
- Mermaid figure code is additional to the prose budget.
- Spend most of the prose length budget on sections 4-7, especially section 6.
- Keep sections 1-3 concise relative to sections 4-7, but do not let them become skeletal.
- Do not pad the output with repeated benefits, repeated module lists, or repeated restatements of the invention idea.

## Hard rules

Always follow these rules:

- Write the main problem as a technical problem, not a business goal or aesthetic goal.
- Keep the title technically specific; avoid vague names when a more precise one is possible.
- Define only important terms and abbreviations that will be reused later.
- In 名词解释, write entries as `术语：定义` and do not prefix the term with numbering or bullets.
- Keep the same technical object under the same name throughout the disclosure.
- Describe mechanism, structure, process, or control logic rather than only the desired result.
- Provide at least two embodiments or variants unless the user explicitly asks for one, and label them as `实施例一` and `实施例二` by default.
- Rank protectable technical points by importance, provide at least 3 points by default, and format them as `1.` `2.` `3.`.
- Derive beneficial effects from the technical solution, not from marketing language.
- Include the 附图 section and the 其他 section; do not omit them.
- In the 附图 section, include at least two concrete figures, use `图1` / `图2` wording by default, and attach Mermaid code blocks unless the user explicitly requests text-only output.
- Ensure the prose of section 6 reaches at least 2000 Chinese characters, excluding the section heading.
- Ensure the full disclosure prose reaches at least 4000 Chinese characters, excluding headings and Mermaid code blocks.
- In the 背景技术 and 发明创造的目的 sections, make the problem-purpose linkage explicit.
- Ensure every term defined in 名词解释 is reused later; if a term cannot be reused, remove it from 名词解释.
- Even for device/structure inventions, explain assembly steps, installation flow, locking control logic, or force transmission logic where applicable rather than listing parts only.
- Do not add prefaces, conclusions, filing advice, or review disclaimers outside the nine sections.
- If the idea is sparse, continue with explicit technical assumptions instead of stopping.

## Adapting the template to software, AI, and system inventions

If the invention is not a purely physical structure, reinterpret structural template requirements in a technically meaningful way:

- “组成部分” → modules, subsystems, data objects, or service units
- “连接关系” → dependencies, message flow, API calls, orchestration links, or data flow
- “位置关系” → deployment placement, logical hierarchy, storage location, or ownership hierarchy
- “工作原理” → decision logic, algorithmic mechanism, scoring logic, or coordination logic
- “工作过程” → execution pipeline, state transition, or control flow
- “可替代的地方” → alternative models, optional modules, routing strategies, or deployment variants

Read [template_mapping.md](references/template_mapping.md) when the invention is software, AI, algorithmic, or multi-agent.

## Output quality checks

Before finalizing, verify that the disclosure:

- includes all nine required sections;
- uses the exact section headings listed in `Required output`;
- contains background technology, a technical problem, an invention purpose, and a concrete technical solution;
- contains `实施例一` and `实施例二` unless the user explicitly requested otherwise;
- includes at least 3 ranked protectable technical points with corresponding benefits;
- includes at least 2 concrete figures, preferably `图1` and `图2`, with Mermaid code blocks that match the written disclosure unless the user explicitly requested text-only figures;
- keeps the prose of section 6 at or above 2000 Chinese characters;
- keeps the full disclosure prose at or above 4000 Chinese characters;
- uses only 4-6 canonical terms in 名词解释 and reuses them consistently later;
- keeps the 其他 section substantive rather than perfunctory;
- avoids unnecessary repetition and still keeps sections 4-7 technically concrete;
- keeps Mermaid labels concise, syntactically safe, and consistent with section 6;
- reads like a formal disclosure rather than a casual explanation.

## Examples

Use [examples.md](references/examples.md) as a style anchor when the task is similar to software/AI inventions or device/structure inventions.

## Refusal boundary

Do not claim:

- guaranteed novelty,
- guaranteed patentability,
- guaranteed grantability,
- guaranteed freedom to operate.

Present the result as a structured disclosure draft that should be reviewed by patent counsel or a patent professional before filing.
