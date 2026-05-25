# Forge-Garde — Direction artistique & propositions d'images

> Les sprites actuels sont des **placeholders** (nains/trolls du core). Ce document propose
> l'identité visuelle cible, unité par unité, + les contraintes techniques Wesnoth + des
> prompts prêts à l'emploi pour un générateur d'images.

## Identité visuelle de la faction

**Genre : ingénierie féerique ancienne.** Bronze et fer rivetés, vapeur, rouages d'horlogerie,
et des **runes lumineuses** comme source d'énergie. **Zéro science-fiction** : pas de LED, pas de
néon, pas de circuits imprimés — tout ce qui « brille » est runique.

- **Palette :** métaux chauds (bronze, laiton, fer patiné), cuir, bois sombre ; accent unique de
  **lueur runique** pour l'énergie.
- **Couleur d'équipe (team-color) :** portée par la **lueur des runes + le cœur des constructs +
  bannières**. Dans le sprite source, ces zones sont peintes en **magenta pur** → le moteur les
  recolore selon le joueur.
- **Lumière :** source en **haut-à-gauche** (convention Wesnoth).

**Trois familles lisibles au premier coup d'œil :**
1. **Nains vivants** (ingénieurs, tireurs, runesmiths, thane) — trapus, barbus, cuir + outils,
   proportions naines classiques.
2. **Constructs** (automates) — silhouettes **blocky, basses, lourdes**, un **cœur-de-rune**
   lumineux visible, vapeur aux jointures. Doivent se lire « lent et increvable ».
3. **Carcasse** — construct effondré, métal **gris/éteint**, cœur-de-rune **mort**, fumée. « Mort mais récupérable. »

## Contraintes techniques (sprites Wesnoth)

- **Taille :** ~72×72 px par frame de base (constructs lourds jusqu'à ~90×90). Pixel art, **fond transparent**.
- **Vue :** 3/4 légèrement plongeante, unité orientée **vers le sud-est**.
- **Team color :** zones d'équipe en **magenta** (#FF00FF et sa rampe) → recolorées par le moteur.
- **Minimum jouable :** 1 frame de base/unité. Idéal : + idle / attack / defend + animation de mort.
- **Style :** palette restreinte, contours nets, léger dithering, ombrage cohérent.

## Briefs unité par unité

### Nains vivants
| Unité | Silhouette & détail signature | Zone team-color |
|---|---|---|
| **Forgeron-Mécano** → Maître-Ingénieur | Tablier de cuir, lunettes à lentilles de cristal, **clé runique** qui luit ; au N2, sac à dos mécanique avec **bras-outils articulés** | liseré du tablier + lueur de la clé |
| **Tonne-Forge** → Garde-Tonnerre | **Canon-à-main runique** trapu en laiton (PAS une arme à feu moderne), fumée à la gueule ; N2 posture calée, protection d'oreilles | gravures runiques du canon |
| **Maître-des-Runes** → Garde-Runes | Marteau + burin, **sigles runiques flottants** en orbite, enclume dans le dos ; N2 bâton runique | les sigles flottants |
| **Brise-Sort** → Pare-Rune | **Pavois/aegis runique** projetant un léger dôme protecteur, hache runique ; N2 aegis plus grande | dôme + wards de l'aegis |
| **Thane de Forge** → Seigneur des Runes | Lord-ingénieur, **armure runique ornée**, hache de commandement, sceptre de contrôle ; N3 couronne de runes + foudre runique | runes de l'armure + bannière |

### Constructs (race mécanique, cœur-de-rune visible)
| Unité | Silhouette & détail signature | Zone team-color |
|---|---|---|
| **Cuirassé** → Cuirassé Lourd | Automate humanoïde **trapu**, plaques de bronze rivetées, **cœur-de-rune** en torse, bras-marteau blocky, vapeur aux jointures ; N2 pauldrons massifs | cœur-de-rune en torse |
| **Foreur de Vapeur** → Juggernaut | Construct-bélier sur chenilles/pattes, **prow de forage**, **grosse chaudière + cheminée** crachant la vapeur, manomètres en laiton ; N2 **coutures de chaudière rouge-incandescent** (télégraphie l'explosion) | jauges + lueur de chaudière |
| **Mortier-de-Forge** → Mortier de Siège | **Emplacement** quasi immobile : tube-mortier runique sur trépied de fer, braise dans le canon, petit automate-servant ; N2 tube renforcé | braise du canon |
| **Sentinelle Runique** → Colosse Runique | Construct **couvert d'un dense réseau de runes lumineuses**, build « bouclier », **poing runique qui flashe** en frappant ; N2 grille de runes intégrale | tout le réseau de runes |
| **Carcasse** | Construct **effondré**, métal gris terne, joints brisés, **cœur-de-rune éteint**, filet de fumée | (aucune — métal mort) |

## Gabarit de prompt (générateur d'images)

> Wesnoth-style unit sprite, **72x72 pixel art, transparent background**, 3/4 top-down view facing
> lower-right, top-left light source, limited muted palette, crisp outlines. Subject: **[brief de l'unité]**.
> Ancient fantasy dwarven engineering — riveted bronze and iron, steam, glowing **runes** as the only
> light source, NO sci-fi / NO neon / NO circuitry. Team-color accent (rune glow) in **magenta**. Single
> centered figure, full body, game asset.

**Exemple — Cuirassé :** « …Subject: a squat humanoid bronze automaton, dwarf proportions, riveted
armor plates, a glowing magenta rune-core in its chest, a blocky hammer-arm, faint steam from the
joints, heavy and slow-looking… »

## Options de production (au choix)

- **A —** Je rédige ce doc + un **prompt complet par unité** (prêt à coller dans un générateur).
- **B —** Je fabrique tout de suite des **placeholders différenciés** en recolorant/compositant des
  sprites du core (ImageMagick) : teinte bronze sur les constructs, cœur coloré, carcasse en gris,
  etc. → les unités deviennent distinctes en jeu immédiatement (en attendant l'art final).
- **C —** Je cherche des **sprites existants** réutilisables (add-ons UMC mécaniques/golems), avec
  vérification de licence (GPL/CC).
