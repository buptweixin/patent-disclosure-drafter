---
name: patent-disclosure-drafter
description: generate a complete chinese patent disclosure from a rough invention idea and optional background details. use when the user wants ai to expand a technical concept into a formal patent disclosure that strictly follows a disclosure template, including title, definitions, technical field, background technology, invention purpose, technical solution, embodiments, protectable technical points, drawings, and other supporting sections. prioritize completeness, consistent terminology, and formal disclosure style. use even when the user provides only a rough idea; make reasonable technical assumptions instead of repeatedly asking follow-up questions. do not rely on external search in the first version.
---

# Patent Disclosure Drafter

Treat the task as structured disclosure drafting, not generic brainstorming. The goal is to turn a rough technical idea into a complete, formal Chinese patent disclosure that another patent professional can continue refining.

## Default behavior

- Accept a rough invention idea plus any optional background details.
- Ask as few follow-up questions as possible.
- If details are missing, make technically plausible assumptions and continue drafting.
- Keep terminology stable across all sections.
- Write in formal Chinese suitable for disclosure drafting.
- Do not mention internal reasoning, hidden roles, or system workflow in the output.
- Do not perform external patent search or claim legal certainty in the first version.

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

Read [output_contract.md](references/output_contract.md) before drafting the final response.

## Drafting workflow

1. Normalize the invention idea.
   - Restate the technical object, use scenario, likely mechanism, and expected technical effect.
   - Infer missing but necessary assumptions.

2. Build the background section.
   - Describe the closest plausible prior art.
   - State the main technical problem and optional secondary technical problems.
   - Explain why the problem arises from the prior art.

3. Draft the purpose section.
   - Link the technical problem, technical means, and technical effect in one compact section.

4. Draft the technical solution and embodiments.
   - Describe the core solution.
   - Provide at least two embodiments or meaningful variants by default.
   - Include module relationships, execution flow, working principle, and alternatives as applicable.

5. Extract protectable technical points.
   - Rank them from most important to least important.
   - For each point, explain the benefit relative to the prior art.

6. Add drawing suggestions and other supporting references.
   - Provide useful figure suggestions even if the user did not ask for them.
   - Add keywords, references, or retrieval hints when helpful.

## Hard rules

Always follow these rules:

- Write the main problem as a technical problem, not a business goal or aesthetic goal.
- Keep the title technically specific; avoid vague names when a more precise one is possible.
- Define important terms and abbreviations.
- Keep the same technical object under the same name throughout the disclosure.
- Describe mechanism, structure, process, or control logic rather than only the desired result.
- Provide at least two embodiments or variants unless the user explicitly asks for one.
- Rank protectable technical points by importance.
- Derive beneficial effects from the technical solution, not from marketing language.
- Include the 附图 section and the 其他 section; do not omit them.
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
- contains background technology, a technical problem, an invention purpose, and a concrete technical solution;
- contains at least two embodiments or variants;
- includes protectable technical points with corresponding benefits;
- includes figure suggestions;
- uses consistent terminology;
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
