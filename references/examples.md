# Examples

Use these examples as style anchors for completeness and technical specificity.

## Example 1: software / AI invention

### User input
“做一个基于多智能体的自动专利交底书生成工具，用户只提供创新点，系统自动补全背景技术、拆解技术问题并生成完整交底书。”

### Good output characteristics
- The title is technically specific.
- 背景技术 describes existing single-pass drafting systems or template-only systems.
- The technical problem is framed as unstable section completeness, weak terminology consistency, or insufficient embodiment detail.
- The technical solution describes modules, data flow, and drafting stages.
- At least two embodiments are provided.
- Protectable points are ranked and linked to advantages.
- 附图 not only names architecture, flow, or sequence diagrams, but also includes renderable Mermaid code blocks.

### Weak output characteristics
- The background says only “patent writing is difficult”.
- The technical problem is written as “提高工作效率” without technical mechanism.
- The solution says only “use AI to generate patents” with no modules or workflow.
- There is only one embodiment.

## Example 2: device / structure invention

### User input
“设计一种可快速拆装且稳定性更高的模块化支架结构。”

### Good output characteristics
- 背景技术 describes existing bracket structures and where looseness occurs.
- The technical problem is mechanical or structural.
- The solution explains components, connection relationships, assembly flow, and locking mechanism.
- At least two embodiments are provided, such as buckle-based locking and screw-assisted locking.
- Protectable points are concrete and ordered by importance.
- 附图 includes functional schematics for component relationships, assembly sequence, and locking or force transmission path, preferably as Mermaid blocks.
