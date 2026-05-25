# Forge-Garde — Prompts de génération d'images (1 par unité)

Chaque prompt est **autonome** (prêt à coller dans ChatGPT / Midjourney / Stable Diffusion / DALL·E).
Objectif : **vrai pixel-art** lisible à petite taille (sprite Wesnoth ~72px, fond transparent, vue 3/4 sud-est).

## Pourquoi insister sur le pixel-art

Les images « peinture » détaillées (1024px) deviennent **floues** une fois réduites à 72px puis ré-agrandies
par le moteur Wesnoth. Un rendu pixel-art (contours durs, palette limitée, **pas d'anti-aliasing**) reste
**net** à la réduction. D'où les directives ci-dessous, intégrées au début de chaque prompt.

**Directives de style communes (déjà incluses dans chaque prompt) :**
> Retro 16-bit pixel-art game sprite (SNES JRPG style), transparent background, single figure facing
> lower-right in 3/4 top-down view, top-left light. **Hard pixel edges, bold dark 1-pixel outline, flat cel
> shading, small limited palette, dithering for gradients. NO anti-aliasing, NO soft blur, NO smooth
> gradients, NO painterly rendering.** Readable as a tiny ~72px sprite.

**Negative prompt commun (à coller dans le champ négatif si dispo) :**
`anti-aliasing, smooth shading, soft edges, blurry, painterly, gradient, 3d render, photorealistic, sci-fi, neon, LED, glowing circuitry, modern firearm, multiple figures, text, watermark, white background, drop shadow`

> Astuce technique : après génération, peindre les **zones d'équipe en magenta pur (#FF00FF)** pour
> que le moteur Wesnoth les recolore par joueur (indiqué « TC: … » à la fin de chaque prompt).
>
> Astuce cadrage : demande la figure **bien centrée et grande dans le cadre** (peu de vide autour) — les
> effets qui débordent (runes flottantes, fumée) rapetissent la silhouette une fois recadrée à 72px.

---

## Nains vivants

**Forgeron-Mécano (GG Gearwright, N1)**
> Retro 16-bit pixel-art game sprite, SNES JRPG style, transparent background, single figure facing lower-right, 3/4 top-down view, top-left light. Hard pixel edges, bold dark 1px outline, flat cel shading, small limited palette, dithered gradients, NO anti-aliasing, NO blur, NO smooth gradients, NO painterly look. A stout bearded dwarf field-engineer in a heavy leather apron and crystal-lens goggles, holding a glowing rune-etched wrench, a satchel of brass tools at his belt, oil-stained hands. Ancient fantasy dwarven engineering: riveted bronze and iron, glowing runes as the only light. No sci-fi, no neon. TC: apron trim + wrench glow.

**Maître-Ingénieur (GG Master Engineer, N2)**
> Retro 16-bit pixel-art game sprite, SNES JRPG style, transparent background, single figure facing lower-right, 3/4 top-down view, top-left light. Hard pixel edges, bold dark 1px outline, flat cel shading, small limited palette, dithered gradients, NO anti-aliasing, NO blur, NO smooth gradients, NO painterly look. An older master dwarf engineer wearing a backpack rig with two articulated mechanical repair-arms over his shoulders, glowing rune-wrench, reinforced leather apron, brass dials on the pack. Ancient fantasy engineering, riveted bronze/iron, runic glow only. No sci-fi, no neon. TC: pack rune-glow + arm joints.

**Tonne-Forge (GG Thundersmith, N1)**
> Retro 16-bit pixel-art game sprite, SNES JRPG style, transparent background, single figure facing lower-right, 3/4 top-down view, top-left light. Hard pixel edges, bold dark 1px outline, flat cel shading, small limited palette, dithered gradients, NO anti-aliasing, NO blur, NO smooth gradients, NO painterly look. A broad dwarf gunner bracing a stout rune-etched brass hand-cannon (a thick fantasy thunder-tube, NOT a modern gun), wisps of smoke at the muzzle, a small axe at his hip, soot on his beard. Ancient fantasy dwarven engineering, bronze/iron, runic glow. No sci-fi, no modern firearm. TC: cannon rune-engravings.

**Garde-Tonnerre (GG Thunderguard, N2)**
> Retro 16-bit pixel-art game sprite, SNES JRPG style, transparent background, single figure facing lower-right, 3/4 top-down view, top-left light. Hard pixel edges, bold dark 1px outline, flat cel shading, small limited palette, dithered gradients, NO anti-aliasing, NO blur, NO smooth gradients, NO painterly look. A veteran dwarf cannoneer in a braced firing stance with a larger reinforced rune hand-cannon resting on a support fork, ear-guards, heavier armor, smoke and ember at the muzzle. Ancient fantasy engineering, riveted bronze/iron, runic glow. No sci-fi. TC: cannon runes + muzzle ember.

**Maître-des-Runes (GG Runesmith, N1)**
> Retro 16-bit pixel-art game sprite, SNES JRPG style, transparent background, single figure facing lower-right, 3/4 top-down view, top-left light. Hard pixel edges, bold dark 1px outline, flat cel shading, small limited palette, dithered gradients, NO anti-aliasing, NO blur, NO smooth gradients, NO painterly look. A dwarf runesmith holding a rune-hammer and chisel, three small glowing runic sigils orbiting close around him, a compact anvil strapped to his back, leather and bronze attire. Ancient fantasy dwarven engineering, runic glow only. No sci-fi, no neon. TC: the floating runic sigils.

**Garde-Runes (GG Rune Warden, N2)**
> Retro 16-bit pixel-art game sprite, SNES JRPG style, transparent background, single figure facing lower-right, 3/4 top-down view, top-left light. Hard pixel edges, bold dark 1px outline, flat cel shading, small limited palette, dithered gradients, NO anti-aliasing, NO blur, NO smooth gradients, NO painterly look. A senior dwarf runesmith wielding a glowing rune-staff, a few orbiting runic sigils kept close to the body, ornate bronze pauldrons, an open rune-tome at his belt. Ancient fantasy engineering, riveted bronze, runic glow. No sci-fi. TC: rune-staff head + sigils.

**Brise-Sort (GG Spellbreaker, N1)**
> Retro 16-bit pixel-art game sprite, SNES JRPG style, transparent background, single figure facing lower-right, 3/4 top-down view, top-left light. Hard pixel edges, bold dark 1px outline, flat cel shading, small limited palette, dithered gradients, NO anti-aliasing, NO blur, NO smooth gradients, NO painterly look. A stocky dwarf warden bearing a large rune-warded tower shield (aegis) projecting a faint translucent protective dome, a rune-axe in the other hand, ward-sigils etched across the shield. Ancient fantasy dwarven engineering, bronze/iron, runic glow. No sci-fi, no neon. TC: shield dome + ward runes.

**Pare-Rune (GG Runeward, N2)**
> Retro 16-bit pixel-art game sprite, SNES JRPG style, transparent background, single figure facing lower-right, 3/4 top-down view, top-left light. Hard pixel edges, bold dark 1px outline, flat cel shading, small limited palette, dithered gradients, NO anti-aliasing, NO blur, NO smooth gradients, NO painterly look. An armored dwarf magic-warden behind a tall heavy rune-aegis emitting a stronger protective dome, dense ward-sigils, reinforced runic plate armor, rune-axe. Ancient fantasy engineering, riveted bronze, runic glow only. No sci-fi. TC: aegis dome + plate runes.

**Thane de Forge (GG Forge Thane, N2, meneur)**
> Retro 16-bit pixel-art game sprite, SNES JRPG style, transparent background, single figure facing lower-right, 3/4 top-down view, top-left light. Hard pixel edges, bold dark 1px outline, flat cel shading, small limited palette, dithered gradients, NO anti-aliasing, NO blur, NO smooth gradients, NO painterly look. A commanding dwarf lord-engineer in ornate rune-engraved bronze armor, holding a two-handed rune battle-axe and a small control-scepter, a banner pauldron, authoritative stance. Ancient fantasy dwarven engineering, runic glow. No sci-fi, no neon. TC: armor runes + banner.

**Seigneur des Runes (GG Runelord, N3)**
> Retro 16-bit pixel-art game sprite, SNES JRPG style, transparent background, single figure facing lower-right, 3/4 top-down view, top-left light. Hard pixel edges, bold dark 1px outline, flat cel shading, small limited palette, dithered gradients, NO anti-aliasing, NO blur, NO smooth gradients, NO painterly look. A majestic dwarf rune-lord crowned with floating runes, master rune-axe crackling with a runic bolt, regal rune-plate armor, commanding aura. Slightly larger heroic silhouette (~80px). Ancient fantasy dwarven engineering, riveted bronze and gold, runic glow only. No sci-fi, no neon. TC: crown runes + axe bolt + cape.

---

## Constructs (cœur-de-rune lumineux = couleur d'équipe)

**Cuirassé (GG Ironclad, N1)**
> Retro 16-bit pixel-art game sprite, SNES JRPG style, transparent background, single automaton facing lower-right, 3/4 top-down view, top-left light. Hard pixel edges, bold dark 1px outline, flat cel shading, small limited palette, dithered gradients, NO anti-aliasing, NO blur, NO smooth gradients, NO painterly look. A squat humanoid bronze automaton with dwarf-like proportions, riveted armor plates, a glowing magenta rune-core in its chest, one blocky hammer-fist arm, faint steam venting from the joints, heavy and slow-looking. Slightly larger silhouette (~80px). Ancient fantasy dwarven engineering, NO sci-fi, no neon, no circuitry. TC: chest rune-core.

**Cuirassé Lourd (GG Heavy Ironclad, N2)**
> Retro 16-bit pixel-art game sprite, SNES JRPG style, transparent background, single automaton facing lower-right, 3/4 top-down view, top-left light. Hard pixel edges, bold dark 1px outline, flat cel shading, small limited palette, dithered gradients, NO anti-aliasing, NO blur, NO smooth gradients, NO painterly look. A heavier bronze-and-iron war automaton with massive shoulder pauldrons, thicker riveted plating, a large glowing rune-core, two hammer-fists, more steam vents, immovable stance. Large silhouette (~84px). Ancient fantasy engineering, no sci-fi, no neon. TC: rune-core + shoulder runes.

**Foreur de Vapeur (GG Steam Crawler, N1)**
> Retro 16-bit pixel-art game sprite, SNES JRPG style, transparent background, single machine facing lower-right, 3/4 top-down view, top-left light. Hard pixel edges, bold dark 1px outline, flat cel shading, small limited palette, dithered gradients, NO anti-aliasing, NO blur, NO smooth gradients, NO painterly look. A steam ram-construct on riveted tracks with a pointed drilling ram prow, a fat boiler and a smokestack belching steam, brass pressure dials, glowing rune-core. Large silhouette (~84px). Ancient fantasy dwarven engineering, no sci-fi, no neon. TC: boiler rune-core + gauges.

**Juggernaut de Vapeur (GG Steam Juggernaut, N2)**
> Retro 16-bit pixel-art game sprite, SNES JRPG style, transparent background, single machine facing lower-right, 3/4 top-down view, top-left light. Hard pixel edges, bold dark 1px outline, flat cel shading, small limited palette, dithered gradients, NO anti-aliasing, NO blur, NO smooth gradients, NO painterly look. A colossal steam siege-ram on heavy tracks, a huge reinforced ram prow, an oversized boiler with glowing red-hot seams (about to overpressure), multiple smokestacks venting, brass gauges in the red. Very large silhouette (~90px). Ancient fantasy engineering, no sci-fi, no neon. TC: rune-core + glowing seams.

**Mortier-de-Forge (GG Forgemortar, N1)**
> Retro 16-bit pixel-art game sprite, SNES JRPG style, transparent background, single emplacement facing lower-right, 3/4 top-down view, top-left light. Hard pixel edges, bold dark 1px outline, flat cel shading, small limited palette, dithered gradients, NO anti-aliasing, NO blur, NO smooth gradients, NO painterly look. A near-immobile rune-mortar: a stout upward-angled mortar tube on a heavy iron tripod, glowing embers inside the barrel, a tiny brass clockwork servant beside it. Slightly larger silhouette (~80px). Ancient fantasy dwarven engineering, no sci-fi, no neon. TC: barrel ember-glow runes.

**Mortier de Siège (GG Siege Mortar, N2)**
> Retro 16-bit pixel-art game sprite, SNES JRPG style, transparent background, single emplacement facing lower-right, 3/4 top-down view, top-left light. Hard pixel edges, bold dark 1px outline, flat cel shading, small limited palette, dithered gradients, NO anti-aliasing, NO blur, NO smooth gradients, NO painterly look. A reinforced siege rune-mortar with a wider rune-banded barrel on a bolted iron carriage, intense ember-glow in the bore, brass aiming dials, smoke. Large silhouette (~84px). Ancient fantasy engineering, no sci-fi, no neon. TC: bore glow + barrel runes.

**Sentinelle Runique (GG Rune Sentinel, N1)**
> Retro 16-bit pixel-art game sprite, SNES JRPG style, transparent background, single automaton facing lower-right, 3/4 top-down view, top-left light. Hard pixel edges, bold dark 1px outline, flat cel shading, small limited palette, dithered gradients, NO anti-aliasing, NO blur, NO smooth gradients, NO painterly look. A guardian automaton covered in a dense network of glowing runic lines, a broad shield-like torso, a rune-fist that flares with light, planted defensive stance. Slightly larger silhouette (~80px). Ancient fantasy dwarven engineering, bronze/iron, runic glow only, no sci-fi, no neon. TC: the runic line network.

**Colosse Runique (GG Rune Colossus, N2)**
> Retro 16-bit pixel-art game sprite, SNES JRPG style, transparent background, single automaton facing lower-right, 3/4 top-down view, top-left light. Hard pixel edges, bold dark 1px outline, flat cel shading, small limited palette, dithered gradients, NO anti-aliasing, NO blur, NO smooth gradients, NO painterly look. A towering fortress-automaton sheathed in a full grid of glowing runes, massive plated body, two glowing rune-fists, immovable bastion stance, faint steam. Very large silhouette (~88px). Ancient fantasy engineering, no sci-fi, no neon. TC: full rune grid.

**Carcasse (GG Wreck)**
> Retro 16-bit pixel-art game sprite, SNES JRPG style, transparent background, single object facing lower-right, 3/4 top-down view, top-left light, dark muted palette. Hard pixel edges, bold dark 1px outline, flat cel shading, dithered gradients, NO anti-aliasing, NO blur, NO smooth gradients, NO painterly look. A collapsed broken dwarven automaton, dull grey tarnished metal, snapped joints, a DEAD extinguished rune-core (no glow), a thin wisp of smoke rising, slumped on the ground. Ancient fantasy engineering wreckage, no sci-fi, no neon. TC: none (dead metal, no team color).
