# 图像编辑提示词模板

模板以英文便于跨模型使用，用户沟通保持中文。可按目标模型改为中文。填入照片的具体区域；删除不适用字段。不要把未替换的变量直接提交给模型。

## Image Editing Prompt

```text
[Task and Input Roles]
Edit the supplied real photograph. Image 1 is the edit target.
{If another image is included: identify its index and role. A style reference guides ONLY graphic language, not objects, identity, text, framing or architecture.}
Create one reality-anchored mixed-media campaign image.

[Intervention Scale]
Mode: {strong-campaign by default, or subtle-surface only when requested/required}.
For strong-campaign: the editable environment must become a visually dominant, large-scale illustrated world. Define {main graphic footprint}, {large motif dimensions relative to the carrier}, {continuous background extension where applicable}, and {photographic anchor zone}. Do not reduce the edit to narrow trim, tiny mural panels or scattered decorative symbols. Quiet zones may be large cream or solid-color graphic masses.

[Original Image Preservation]
Retain {aspect ratio, framing, subject location and other source-led composition constraints}.
Hard-lock {concrete P0 identity, shape and exact existing text details}.
Keep {P1 silhouette, spatial skeleton, opening layout and physical relationships}. Transform {P2 material/surface attributes on those same structures} at large scale; do not confuse structural preservation with preserving all surface appearance. Hard-locked subject attributes remain photographic.

[Main Subject]
{Visible subject, position, pose, proportions, identifying details} stays photographic, with its original materials and natural edges.

[Environment]
Keep {specific calm photographic zones, ground/support surface, contextual structures}.
Transform only {named editable surface locations and boundaries}.

[Graphic Intervention]
Concept: {one coherent source-related idea}.
The principal graphic area is {specific physical carrier}; graphics behave as {painted mural / printed wrapping / graphic panel}.
Use {chosen theme-specific motifs}. {Specify integrated sky/background extension for strong mode when space permits; broad masses can extend beyond frame edges}.
Keep {doors, windows, recesses, foreground objects} readable and correctly layered.

[Illustration Style]
Bold flat editorial illustration, large clean print-like color blocks, soft naïve geometry, slightly irregular clean contours, {outline choice}, minimal shading and gradients. Use a limited recurring motif vocabulary, scaled from large masses to sparse accents.

[Composition]
Follow {original visual path and main graphic location}; maintain a clear photographic hero and a calm region at {location}. Do not fill every available space.

[Perspective]
Conform surface graphics to {specific wall/ground/other planes}; foreshorten toward {observable direction}, fold naturally at {corner}, and let {foreground object} occlude the graphic surface. Preserve original geometry and depth. Integrated background graphics have their own coherent composition and sit behind the original subject; do not apply wall foreshortening to a graphic sky.

[Color Palette]
{Warm/cool main color relationship}, balanced with {neutral}, using {source-derived color} as a bridge. Respect {supplied brand palette if any}. Concentrate vivid color in graphic areas; retain plausible photographic color.

[Photography]
Preserve the source camera viewpoint and lens character. Keep {skin/fur/glass/metal/food/fabric} believable and distinct.

[Lighting]
Maintain {observed light direction, softness and temperature}. Retain support/contact shadows. Graphic motifs remain flat while their physical surfaces retain environmental shading.

[Depth of Field]
{Preserve observed focus relationships; do not invent blur when absent}.

[Motion]
{Keep the scene static / preserve existing directional motion and subject sharpness}.

[Texture]
Retain natural material differences and edge detail. Avoid uniform waxy smoothing, fake embossing and plastic CGI surfaces.

[Commercial Art Direction]
One unified illustration system, controlled density, intentional scale and visual hierarchy. Convey {purpose/mood} through the relationship of the photographic subject and graphic environment.

[Image Quality]
Clean integrated edges, readable structure, no halos, coherent depth, faithful subject details. {Requested dimensions/aspect ratio as a desired result, not a guarantee}.

[Constraints]
Change only {editable zones}. Preserve {critical locks repeated briefly}.
{No new text or logos / add only the user's exact supplied text at the specified location}.
Do not copy objects, flags, characters or lettering from the style reference.
Avoid {the relevant photo-specific failures from the list below}.
```

“保留文字”与“不新增文字”可同时成立，不能用 `no text` 指令删除原包装/牌照。无独立 negative 参数的工具，将禁止项写进 Constraints，不虚构该参数。

## Negative Prompt / 禁止项

按当前照片选取，不把无关人脸、车轮等全部堆进每次 Prompt。strong-campaign 额外避免：tiny decorative murals, narrow trim-only edits, weak graphic presence, sparse small stickers, repetitive miniature wallpaper。轻度模式不用这些规模禁项。

```text
full-scene cartoonization, generic AI illustration, random graffiti or unrelated doodles,
sticker-like graphics detached from surfaces, arbitrary floating icons,
incorrect perspective, warped structural geometry, flattened windows and recesses,
altered subject identity or proportions, redesigned product or packaging,
modified original lettering or logos, deformed wheels, bad anatomy,
plastic CGI materials, waxy skin, fake HDR, excessive glow,
fluorescent neon palette, excessive gradients, inconsistent shadows,
invented reflections, random typography, fake logos, illegible added text,
uniform graphic density, decorative clutter covering the subject,
cutout halos, random blur, overprocessed photographic textures
```

## 禁止原因

| 问题 | 影响 | 提示词修正方向 |
|---|---|---|
| 漂浮贴纸 | 无空间归属 | 指定载体、边界、透视与遮挡 |
| 整幅卡通化 | 摄影锚点消失 | 指定真实保留区与材质 |
| 建筑变形 | 空间关系失真 | 指明门窗、转角与轮廓不变 |
| 身份/包装改变 | 主体不再可信 | 重复原图保护项并判为关键缺陷 |
| 全屏碎花 | 主体与图形均无主次 | 放大主块、减少母题、指定净区 |
| 霓虹与假 HDR | 偏离印刷感 | 图形区饱和，摄影区保持自然 |
| 假字/假 Logo | 信息错误且明显失真 | 仅使用提供的精确资产/文字 |
| 随机模糊/发光 | 掩盖融合错误 | 修正边缘和空间逻辑，保留原摄影行为 |
