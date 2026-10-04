# 示例与场景演练

以下均为假设示例，用于演示迁移方法，不是已读取或生成的实际照片，不声称通过视觉验收。

## Example Input：静态人像街拍

用户上传竖版照片：人物位于右侧，左后方是一面占据主要背景、斜向后延伸的米色墙，墙上有窗框，前景栏杆遮挡一部分墙面。自然柔光，无运动模糊。请求“用 reality-wrap 改造”。

## Example Analysis

- 主体与脸、服装、手势为 P0；窗框、栏杆、地面与建筑轮廓为 P1；左侧不透明墙面为 P2。
- 不预设天空为 P3。主图形区覆盖整块可改左墙，不收成小面板；栏杆盖住图形；斜墙上的图案随墙面向远处缩小。
- 概念：人物保持真实，侧后方整块墙面成为巨幅暖色花形与宽阔青蓝波浪组成的城市花园，插画主导可改背景。
- 母题仅花形、叶形、波浪三类；奶油白留白；从人物现有服装选择连接色，实际读图后确定。
- 保留静态摄影与原景深，不改变机位，不新增文字。

## Example Final Prompt

```text
Edit the uploaded portrait photograph into a reality-anchored mixed-media campaign. The uploaded portrait is the edit target; do not replace its scene.
Preserve the original portrait aspect ratio, camera view, person's position, face, hair, body proportions, clothing, hands and pose. Keep the person fully photographic with natural skin and fabric texture.
Transform only the opaque beige wall on the left and behind the person into a painted flat editorial graphic surface. The mural must dominate the entire editable wall at thumbnail scale, with oversized motifs spanning substantial portions of the wall rather than small decorative panels. Create a city-garden concept using large coral and warm yellow flower shapes, restrained teal leaves and blue waves, balanced by substantial cream areas. Keep three recurring motif families with a clear large-to-small hierarchy. Use slightly irregular clean contours, minimal shading and no decorative 3D effects.
Follow the existing oblique wall perspective and reduce graphic scale as the wall recedes. Preserve window frames, recesses, architectural edges and floor geometry. Keep the foreground railing photographic and in front of the mural. Leave a calm graphic zone around the person's silhouette.
Maintain the source soft daylight, wall shading, contact shadows, original depth of field and static scene. Do not add motion blur. Preserve photographic pavement and the different textures of skin, fabric and metal.
Do not add text or logos. Do not alter the person's identity or outfit. Avoid floating stickers, arbitrary doodles, flattened windows, changed geometry, cutout halos, neon glow, waxy skin and full-scene cartoonization.
```

## Additional routing cases

| 请求与原图 | 正确动作 | 需防止的误用 |
|---|---|---|
| 商品瓶置于桌面与背景板，标签需保留 | 锁瓶体和标签；改背景板/局部桌面；保留接触阴影 | 用“无文字”删标签、凭空加车、全幅追焦 |
| 建筑照片，无人物汽车 | 建筑结构为锚点；指定墙面表皮为改区；保留真实开口 | 因“主体不能动”拒绝改墙，或把楼整体重建 |
| 宠物近景，几乎没有背景 | 说明载体有限；问是否允许扩背景；可先给局部策略 | 强行覆盖毛发以凑介入比例 |
| 汽车停在围墙前 | 锁车辆、牌照与轮毂；围墙改图形；保留静态 | 自动添加追焦、改车轮设计 |
| 只要 Prompt，不出图 | 分析与完整编辑提示词交付 | 自动调用生成工具 |
| 只有风格参考，没有待改照片 | 请求目标原图；可先介绍方法 | 编辑参考成图并声称改了用户照片 |
| 提供目标照＋品牌色，禁止黄色 | 以品牌色组织暖冷/明暗层级；不使用参考黄色 | 把参考配色当不可变规则 |
| 无可用图像编辑工具 | 提供完整 Prompt，明确未生成 | 自动切到需额外授权的 API，或假称已有成品 |

## 强度回归用例

默认人像、停放汽车、白底商品：图形主导可改背景，主体依然摄影。天空面积大的建筑：主动评估连续图形背景扩展，不默认保持整片实拍天空。用户明确只改一面小墙：尊重局部限制，使用轻度模式。主体占满背景：说明范围受限，不为了面积改变身份。所有场景都避免把寺院示例的莲花或配色当唯一答案。
