# Template Mapping

This reference explains how to preserve the rigor of a structural disclosure template for software, AI, algorithmic, and multi-agent inventions.

## Core mapping rule

When the template asks for structural detail, translate that requirement into the most natural technical structure for the invention type.

- mechanical invention → physical components, connection relationships, positional relationships
- electronic system → hardware modules, signal paths, interface relationships
- software system → modules, data flow, control flow, API relationships, execution sequence
- algorithm / AI invention → model components, feature pipeline, training or inference flow, feedback logic
- multi-agent invention → role decomposition, task routing, shared artifacts, scoring logic, revision loop
- vision-language / embodied perception invention → multi-view inputs, scene representation, spatial grounding, uncertainty estimation, tool-calling for close-up review, controller feedback loop

Do not use the “software” label as an excuse for abstract writing.

## Section-by-section guidance

### 背景技术
For software or AI inventions:
- describe the closest plausible baseline workflow or system;
- explain how that baseline works technically;
- identify concrete technical deficiencies such as terminology drift, unstable structure, weak section completeness, poor evidence mapping, or insufficient embodiment detail.

### 发明创造的目的
State:
- the technical architecture or mechanism,
- the technical problem solved,
- the expected technical effect.

### 技术方案以及具体实施例
For software or AI inventions, describe:
- functional modules,
- data inputs and outputs,
- upstream and downstream relationships,
- control flow or execution sequence,
- working principle,
- meaningful alternative variants.

Useful embodiment pairs include:
- cloud deployment vs edge deployment,
- centralized orchestration vs distributed collaboration,
- rule-assisted generation vs model-driven generation,
- single-pass generation vs structured two-pass drafting.

For vision-language or embodied perception inventions, additionally describe:
- image, video, depth map, point cloud, or text prompt inputs;
- how the model builds scene-level spatial representation, object grounding, or relative-distance estimation;
- when uncertainty or occlusion triggers a second-pass tool call such as zoom, recapture, OCR, thermal imaging, or another viewpoint;
- how global scan results and local review results are fused into a final decision.

### 发明内容的技术要点
For software or AI inventions, protectable technical points may include:
- the method for converting a rough idea into a structured disclosure,
- the mechanism for keeping terminology consistent across sections,
- the section-wise drafting sequence,
- the handoff logic between drafting stages,
- the embodiment generation strategy.

For vision-language or embodied perception inventions, protectable technical points may additionally include:
- the scene quantization or spatial reasoning mechanism,
- the cross-view object association or device grounding method,
- the uncertainty-driven active review trigger,
- the fusion logic between global scan and local detail verification.

### 附图
For software or AI inventions, suggested figures may include:
- overall architecture diagram,
- module relationship diagram,
- message or data flow diagram,
- scoring or revision loop diagram,
- sequence diagram.

When possible, render these figures directly as Mermaid blocks in the disclosure:
- architecture and data flow → `flowchart LR` or `flowchart TB`
- interaction timing → `sequenceDiagram`
- state transitions → `stateDiagram-v2`

For vision-language or embodied perception inventions, high-value figure choices include:
- global scan architecture diagram,
- scene graph or spatial grounding flow diagram,
- uncertainty-triggered local review flow diagram,
- multi-robot or multi-camera coordination diagram.

For device or structure inventions, Mermaid should be used as a functional schematic rather than a dimensional engineering drawing. Prioritize:
- component relationship diagram,
- assembly sequence diagram,
- locking or limiting logic diagram,
- force transmission path diagram.
