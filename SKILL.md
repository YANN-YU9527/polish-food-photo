---
name: polish-food-photo
description: Clean and reframe food photographs by removing distracting objects and visible text, then re-rendering and outpainting the dish at a fixed restaurant-style frontal oblique camera angle. Use when a user attaches a food or dish photo and asks to remove clutter, logos, watermarks, captions, labels, or other writing; clean the table or background; expand the canvas; uncrop the plate; reveal the full plate; standardize the viewing angle; or create a polished restaurant-style composition.
---

# Polish Food Photo

Use the image generation/editing tool for every edit. Do not simulate the edit with a text-only response or ordinary image-processing code.

## Workflow

1. Inspect the attached image before editing. Identify the food, plate boundary, crop direction, removable distractions, every visible text-like region, table texture, lighting direction, shadows, camera angle, plate angle, and depth of field. Check the food, garnish, plate, props, background, center, corners, and edges for words, letters, numbers, logos, captions, labels, signatures, watermarks, UI overlays, or ghosted glyphs.
2. Preserve the dish as the visual source of truth. Keep the food's ingredients, portions, arrangement, color, doneness, garnish, texture, and intentional non-text plate decoration unchanged unless the user explicitly requests otherwise.
3. Remove all visible text-like elements by default, including readable or partial words, letters, numbers, logos, captions, labels, signatures, watermarks, UI overlays, and residual character-shaped strokes. Remove them whether they appear over the food, on the plate, on props, or in the background. Reconstruct the covered food or surface from neighboring texture, color, lighting, and structure. Preserve a specific text or logo only when the user explicitly asks to keep it.
4. Remove unrelated clutter such as tissues, packaging, cables, hands, stray utensils, crumbs outside the intended styling, background dishes, or distracting table objects. Keep intentional non-text props when they support the composition or the user asks to retain them.
5. Re-render the plate and dish at the canonical camera angle defined below, regardless of the source camera angle. Treat this as an intentional viewpoint conversion, not an outpaint that preserves source perspective. Preserve the dish identity, ingredients, portions, relative arrangement, plate design, and materials while reconstructing newly visible or hidden surfaces consistently.
6. Outpaint beyond the crop far enough to show the full plate with a small, natural margin around it. Reconstruct missing edges from the target curvature, material, rim thickness, pattern, highlights, reflections, and the canonical perspective. Extend the table or background consistently.
7. Match the source white balance, exposure, shadows, reflections, focus falloff, grain, and image quality while converting the camera geometry to the canonical angle. Avoid inventing extra food, duplicate utensils, warped geometry, false text, or a second plate.
8. Lock the output camera and plate pose to the canonical target: fixed elevation, centered frontal orientation, zero sideways yaw, zero roll, broad horizontal rim ellipse, level front rim, and visible front outer wall. Do not preserve a conflicting source viewpoint unless the user explicitly asks to keep the original angle.
9. Generate the edited image directly without asking for confirmation when the request and source image are sufficient. If the target image is missing, ask the user to attach it.
10. Inspect the result at normal view and close view before accepting it. Compare the output against the canonical-angle acceptance criteria below and scan the food, garnish, vessel, props, background, center, corners, and edges for readable text, logo fragments, repeated glyphs, or faint character-shaped residue. If the angle is outside tolerance, run one corrective edit that changes the viewpoint only while preserving the dish. If text remains, run one corrective edit limited to the remaining text regions. Also correct any remaining clutter, cropped plate edge, inconsistent rim, or malformed vessel geometry.

## Canonical Plate-Angle Target

Use this angle by default for every food-photo cleanup, even when the input was photographed from above, from the side, or at a rotated angle:

- center the vessel horizontally in a straight-on frontal oblique view;
- set the camera approximately 25 degrees above the plate plane, with an acceptable range of 24 to 26 degrees;
- use approximately zero sideways yaw and zero roll; keep the front rim level and the vessel's left and right sides symmetrical;
- for circular plates, target a rim ellipse minor-axis/major-axis ratio of 0.40 to 0.43; this ratio is the primary geometric acceptance test;
- show the plate interior clearly while retaining a distinct front outer wall below the front rim; the rear rim sits higher in the frame;
- use a natural normal-to-short-telephoto food-photography perspective with limited wide-angle distortion;
- keep the full vessel visible with a small natural margin, without a second plate or duplicated food.

For square, rectangular, oval, or irregular vessels, keep the same 24-to-26-degree camera elevation, frontal alignment, zero yaw, and zero roll; infer the target perspective from the vessel's real geometry instead of forcing a circular ellipse. For deep bowls, preserve their actual wall depth while keeping the same camera elevation.

If the source is far from the target angle, reconstruct occluded surfaces conservatively from visible evidence. Preserve ingredient identity, count where discernible, portions, colors, doneness, garnish, and relative placement. Do not claim pixel-exact preservation after a large viewpoint change. If the user explicitly asks to preserve the original angle or names another angle, follow that request instead of the canonical target.

### Angle Acceptance Check

Before accepting an edit:

1. Confirm the camera reads as roughly 25 degrees above the plate plane, not top-down and not table-level.
2. For a round plate, verify the visible rim ellipse minor/major ratio is 0.40 to 0.43.
3. Confirm the front rim is nearly horizontal, lateral yaw is absent, roll is absent, and the plate is centered.
4. Confirm the front outer wall remains clearly visible and the entire vessel fits in frame.
5. If any item fails, run one targeted corrective edit that changes only camera/plate geometry and preserves the dish, lighting, plate identity, and background.

## Edit Prompt Template

Use this intent in the image-editing prompt and adapt it to the visible scene:

> Edit the supplied food photograph. Remove unrelated distracting objects and remove every visible word, letter, number, logo, caption, label, signature, watermark, UI overlay, and residual text-shaped mark unless the user explicitly names an item to retain. Reconstruct the underlying food, plate, prop, or background naturally with no blur patch or ghost lettering. Re-render the dish and vessel at the fixed canonical camera angle: centered straight-on frontal oblique view, camera 24 to 26 degrees above the plate plane, zero sideways yaw, zero roll, level front rim, and clearly visible front outer wall. For a circular plate, the target rim ellipse minor-axis/major-axis ratio must be 0.40 to 0.43. For non-circular vessels, use the same camera elevation and alignment without changing the vessel's real shape. Preserve the dish identity, ingredients, portions, relative arrangement, plate design, lighting, white balance, depth of field, reflections, grain, and photographic realism. Expand the canvas to reveal the entire vessel with a natural margin. Do not create extra food, tableware, duplicated objects, warped geometry, false text, or a second plate.

Add explicit keep/remove instructions derived from the image and the user's wording. List every detected text region under the remove instructions. Request the canonical target angle by default and repeat its numeric tolerances in every corrective edit. Preserve the source angle only when the user explicitly asks for it. Choose the smallest expansion that comfortably contains the full plate at the new viewpoint.

## Output

Return the edited image in the conversation. State briefly that clutter and visible text were removed and the full plate was restored. Mention only material limitations that remain visible.
