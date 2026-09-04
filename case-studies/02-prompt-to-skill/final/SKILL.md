---
name: xianxia-heavenly-image2
description: Compile or repair English GPT Image 2 prompts for cinematic live-action xianxia heavenly-realm scenes from Chinese or English briefs. Use for heavenly palaces, cloud realms, celestial ceremonies, journeys, intimate scenes, or action scenes that must preserve the user's fixed 21:9 silk-banner, Tang/Song architecture, porcelain-relief, and no-text visual DNA; do not use for non-heavenly realms, video direction, or other image-model syntax unless the user explicitly asks to adapt the result.
---

# Xianxia Heavenly Image 2

Turn a short or detailed scene idea into one coherent, production-ready prompt for `gpt-image-2`. Preserve the series identity while changing only the scene-specific content.

## Inputs

Require only a scene, event, or primary subject. Accept Chinese or English.

Use any supplied time, weather, characters, action, camera position, mood, palette, architecture type, exclusions, reference images, or locked variables. When these are absent, make restrained choices that support the scene instead of asking a questionnaire. Ask only when the scene itself is missing or two user requirements cannot coexist.

## Permanent visual DNA

Every result must preserve all five invariants:

1. **Exact 21:9 frame.** Treat this as both a composition rule and an output setting.
2. **Visible hanging silk banner.** Give it a plausible architectural attachment and environmental behavior. It must not read as a neat, symmetrical decorative border.
3. **Recognizable Tang- and Song-inspired Chinese architecture.** Include at least one architectural anchor even in cloud, action, or close-character scenes. Create a unified heavenly design language rather than a strict archaeological reconstruction.
4. **Secondary porcelain relief.** Embed restrained white or metallic-white crackle-glaze deity relief in stonework, wall panels, balustrades, column bases, gates, or another architectural carrier. Never make it the hero subject or a freestanding monumental idol.
5. **No text.** Exclude readable writing, calligraphy, inscriptions, signage, decorative lettering, pseudo-characters, text-like glyphs, logos, and watermarks. Keep plaques blank or replace their content with clearly non-linguistic abstract cloud relief.

Hard constraints override preferences. If the user explicitly asks to remove or contradict an invariant, state the conflict and request a decision rather than silently violating the skill.

For detailed placement patterns, material language, and targeted repairs, read [references/celestial-visual-dna.md](references/celestial-visual-dna.md).

## Workflow

1. Extract the scene's narrative subject, action, location, emotional tone, and supplied restrictions.
2. Separate scene variables from the five permanent invariants. If the user requests a single-variable change, name the changed variable internally and lock all others.
3. Choose a physically plausible camera location and eye line. Avoid floating, omniscient, or game-camera viewpoints unless the user explicitly requires one.
4. Build readable depth with foreground, midground, main subject, and distance. The banner may occupy any suitable layer but must have a spatial reason to exist.
5. Select an architectural carrier appropriate to the scene and express Chinese identity through structure—rooflines, eaves, dougong, beams, columns, stone bases, terraces, bridges, gates, or balustrades—not through text.
6. Integrate the porcelain relief into that architecture and keep its scale, contrast, and detail subordinate to the main subject.
7. Place people and action with believable scale, grouping, gaze, contact, and partial occlusion. Use figures to reveal scale or narrative rather than to form a staged display.
8. Establish one motivated primary light source. Make atmosphere, shadows, silk, jade, stone, porcelain, metal, and clothing respond consistently.
9. Compile the prompt in concise labeled sections. State `photorealistic` or an equivalent real-camera intent once to engage the requested live-action look. Prefer concrete spatial and material descriptions over stacked quality adjectives or exact lens specifications.
10. Check every invariant, spatial continuity, visual hierarchy, lighting consistency, and prompt contradictions. Repair only the failed module and check again.

## Visual judgment

- Favor an observed, physically possible moment over a centered promotional tableau.
- Create grandeur through scale, negative space, depth, and small human activity rather than ornament density.
- Keep gold, silver, glow, mist, grain, and supernatural effects restrained and subordinate to architecture and narrative.
- Let the silk interrupt or reveal space irregularly; do not let it accidentally hide the primary read of the scene.
- Use atmospheric depth without turning every distance layer into undifferentiated white fog.
- Preserve matte jade, stone, porcelain, and fabric character. Avoid generic glossy game-render surfaces.
- Do not repeat adjectives when a concrete placement, material, or relationship would be more actionable.

## GPT Image 2 output

Return one English prompt by default. Use this maintainable order, omitting empty sections:

```text
IMAGE 2 PROMPT

Format and medium:
Scene and narrative:
Composition and camera:
Architecture and spatial depth:
Characters and action:
Lighting, atmosphere, and materials:
Permanent constraints:

GENERATION SETTINGS
model: gpt-image-2
size: 2688x1152
quality: high
```

Use `1792x768` and `quality: medium` only when the user asks for a faster draft. Both sizes are exact 21:9. Keep exclusions and invariants inside the main prompt rather than inventing a separate negative-prompt syntax.

Do not add multiple variants, a rationale, or an image-generation call unless requested. If material assumptions affect the result, place a short `Assumptions` note before the prompt.

## Check and repair

Before returning the result, verify:

- the settings and composition specify exact 21:9;
- the banner is visible, attached, naturally affected by the scene, and not a symmetrical frame;
- Tang/Song-inspired structure is recognizable and spatially integrated;
- porcelain deity relief is present, architectural, and secondary;
- no readable or text-like marks are requested anywhere;
- the camera can plausibly occupy its stated position;
- foreground, subject, and distance remain legible;
- the primary subject wins over fixed visual motifs;
- action, bodies, scale, and occlusion are believable;
- light direction, atmosphere, and material response agree;
- the image reads as live-action cinematic xianxia, not a glossy game render or staged poster;
- the prompt explicitly requests a photorealistic or real-camera result without relying on excessive lens jargon;
- no clauses duplicate or cancel one another.

If a check fails, revise the smallest responsible section. Never delete a permanent invariant as a repair. For a single-variable edit, repeat the preserve list and ensure unrelated composition, identity, geometry, lighting, or styling has not drifted.

When diagnosing quality drift or comparing against the user's original successful result, read [examples/heavenly-gate-reference.md](examples/heavenly-gate-reference.md). Treat it as a calibration example, not as a universal scene template.
