# Examples

Use these examples as style anchors for completeness and technical specificity.

## Example 1: software / VLM invention

### User input
“结合大模型的三维空间量化和推理能力，让巡检机器人先全局扫描厂房，自动定位烟雾报警器、消防警铃等设备的位置和相对距离；若发现疑似遮挡或损坏，再调用局部高清放大工具复核灭火器压力表等细节。”

### Good output characteristics
- The title is technically specific.
- 背景技术 describes existing single-frame detection or rule-based inspection systems, and explains why they miss spatial relationships, occlusions, or fine-grained defects.
- The technical problem is framed as weak 3D spatial reasoning, unstable device grounding, or lack of active reinspection capability.
- The technical solution describes global scan, scene representation, spatial grounding, uncertainty scoring, and local zoom or recapture tools.
- At least two embodiments are provided, such as depth-assisted reconstruction vs multi-view reconstruction, or wheeled robot vs drone platform.
- Protectable points are ranked and linked to advantages.
- 附图 not only names architecture, flow, or sequence diagrams, but also includes renderable Mermaid code blocks that show the global-to-local review loop.

### Weak output characteristics
- The background says only “工业巡检误报率高” without describing the current technical pipeline.
- The technical problem is written as “提高效率” without linking it to spatial inference or detail verification.
- The solution says only “use VLM to inspect” with no modules, data flow, or tool-calling logic.
- There is only one embodiment.

## Example 2: device / structure invention

### User input
“设计一种支持全局扫描和局部高清复核的巡检终端结构，要求能在工业机器人平台上稳定工作，并在广角扫描和长焦复核之间快速切换。”

### Good output characteristics
- 背景技术 describes existing single-camera or rigidly mounted inspection terminals and where field of view, vibration stability, or close-up capability become bottlenecks.
- The technical problem is mechanical, optical, or structural.
- The solution explains components, positional relationships, calibration or installation flow, and switching / locking mechanism between scan mode and review mode.
- At least two embodiments are provided, such as coaxial wide-angle + zoom layout and split wide-angle + zoom layout, or mechanical lock plus electromagnetic assist.
- Protectable points are concrete and ordered by importance.
- 附图 includes functional schematics for component relationships, installation sequence, and locking or force / control transmission path, preferably as Mermaid blocks.

### Weak output characteristics
- There is only a list of parts with no connection or positional relationships.
- There is no installation flow, calibration flow, or switching / locking logic.
- No concrete embodiment differences are explained.
