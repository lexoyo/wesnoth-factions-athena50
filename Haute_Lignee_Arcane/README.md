# La Haute Lignée Arcane — add-on Wesnoth (faction élitiste)

Add-on **de type ère** pour Wesnoth 1.19. Ajoute la faction multijoueur originale
**La Haute Lignée Arcane** (ID interne `high_arcane_lineage`) : mages nobles de lignées
impériales. Peu d'unités, très chères, très puissantes — perdre une unité fait mal.

ID interne EN : `High_Arcane_Lineage` · race `highborn_arcane` (Noble Arcane / Nobles Arcanes).

## Structure des fichiers

```
Haute_Lignee_Arcane/
├── _main.cfg                 # point d'entrée : macros -> [units] -> eras -> tests
├── _info.cfg                 # métadonnées (type=era)
├── eras.cfg                  # 2 ères : "Défaut + Haute Lignée" et "Haute Lignée (solo)"
├── factions/
│   └── high-arcane-lineage.cfg   # [multiplayer_side] (meneur Archonte, 7 recrues)
├── units/
│   ├── high-arcane-units.cfg     # 17 unités (recrues + avancements + Archonte)
│   └── summons.cfg               # 3 serviteurs astraux temporaires
├── utils/
│   ├── race.cfg              # [race] highborn_arcane (+ pool de traits standard)
│   ├── movetypes.cfg         # hal_noble (mage) / hal_guard (garde)
│   ├── abilities.cfg         # ABILITY_HAL_AEGIS, WEAPON_SPECIAL_HAL_PURGE
│   ├── animations.cfg        # HAL_ANIMS (anims placeholder sur sprite unique)
│   └── summon.cfg            # invocation (menu clic-droit + expiration ~2 tours)
├── tests/
│   └── tests.cfg            # test_hal_load (headless) + hal_showcase (galerie)
└── images/units/high-arcane-lineage/   # (vide) -> y déposer l'art custom
```

## Installer / jouer

Symlink (machine de dev) ou copie du dossier `Haute_Lignee_Arcane/` dans
`<userdata>/data/add-ons/`. Puis : **Multijoueur → Partie locale**, ère **« Défaut + Haute
Lignée Arcane »**, faction **La Haute Lignée Arcane** (meneur **Archonte Impérial**).

Lancement direct (sans menus) :
```
wesnoth -t hal_showcase --data-dir <racine_wesnoth>   # galerie de toutes les unités
wesnoth -u test_hal_load --data-dir <racine_wesnoth>  # validation headless (exit 8 = PASS)
```

## Roster (coûts)

| Recrue (N1) | Coût | → N2 | → N3 |
|---|---|---|---|
| Héritier Arcanique | 24 | Noble Arcaniste | Prince-Mage |
| Garde d’Azur | 36 | Égide Royale | — |
| Dame des Étoiles | 33 | Dame Astrale | Duchesse Céleste |
| Adepte Temporel | 39 | Chronolord | — |
| Invocateur Noble | 42 | Grand Conjurateur | — |
| Dragonmage de Sang *(N2)* | 56 | Sage Draconique Impérial *(N3)* | — |
| Inquisiteur du Sang Pur | 34 | Grand Inquisiteur | — |
| **Archonte Impérial** *(meneur N4)* | 90 | — | — |

Serviteurs invoqués (temporaires) : Gardien Astral, Lame Flottante, Esprit Noble.

## Mécaniques (Wesnoth natif, lisibles)

- **Magie partout** : la plupart des attaques à distance sont `magical` (touche à 70 %),
  types arcane / feu / froid, avec des pointes `marksman` (Duchesse, Dragonmage, Archonte).
- **Égide royale** (`ABILITY_HAL_AEGIS`) : Égide Royale & Archonte donnent +20 % de
  résistance feu/froid/arcane à eux-mêmes et aux alliés adjacents. Anti-magie d'élite.
- **Châtiment** (`WEAPON_SPECIAL_HAL_PURGE`) : l'Inquisiteur inflige +50 % de dégâts aux
  morts-vivants.
- **Commandement** : Noble Arcaniste, Prince-Mage, Archonte donnent le bonus de dégâts
  d'aura natif aux alliés adjacents de niveau inférieur.
- **Invocation** (Invocateur / Grand Conjurateur) : clic droit sur une case **libre
  adjacente** → « Invoquer un serviteur astral ». Coûte le tour de l'invocateur ; le
  serviteur disparaît après ~2 tours. Compense le faible nombre d'unités.
- **Contrôle temporel** : Adepte/Chronolord (slow, froid, drain, firststrike, escarmoucheur,
  translocation).
- **Régénération** (Archonte, +8) : soigne aussi le poison chaque tour → immunité de fait
  au poison.

## Équilibrage — philosophie « surpuissant par unité, équilibré par le coût »

Forces : burst magique élevé, dégâts arcane/feu/froid, excellent en duel, auras
(commandement + égide), scaling tardif, meneur monstrueux. Faiblesses **voulues** :
- très peu d'unités (recrues à 24–56 or, meneur à 90) ;
- faible **contrôle de villages** (peu de corps, mobilité moyenne, `villages_per_scout=8`) ;
- fragile à l'**encerclement**, au **poison**, au **drain**, à la **pression à distance de
  masse** et au **spam de mêlée bon marché** ;
- erreurs **chères** : perdre une unité est économiquement douloureux ;
- contrôle de carte faible en début de partie.

### Note sur l'Archonte (9 attaques)
Les 9 attaques sont **assumées** (cf. cahier des charges) : arsenal total couvrant
blade/arcane/feu/froid/impact, du multi-coups (15×5) au snipe (38×1) au duel (40×1
firststrike). L'UI les liste proprement. Garde-fous d'équilibre : c'est un **meneur N4 à
108 PV** qui, s'il meurt, fait **perdre la partie** — donc surexposer l'Archonte est un
risque mortel. Aucune attaque n'a été réduite ; si le méta montre que c'est trop fort, le
levier le plus simple est de baisser le nombre de coups des nukes (ex. 28×3 → 24×3).

## TODO — art & sons

**Sprites custom** à déposer dans `images/units/high-arcane-lineage/` (72×72, ou 80×80 pour
Archonte/Sage Draconique/Duchesse), fond transparent, vue 3/4 SE, zones d'équipe en magenta.
Identité : robes ornées, or/ivoire/bleu/violet/argent, sigils flottants, lames cérémonielles.

Pour chaque unité (id ci-dessous), prévoir : base `<id>.png`, `-attack-*`, `-ranged-*`,
`-defend.png`, `-death-*`, + miss/projectiles. Tant que l'art manque, les unités utilisent
des **placeholders** du jeu de base (mages/drakes/esprits) et les **animations** sont
dérivées du sprite unique (déplacement + teinte + projectiles core) — rien ne casse.

- heritier-arcanique, noble-arcaniste, prince-mage
- garde-azur, egide-royale
- dame-etoiles, dame-astrale, duchesse-celeste
- adepte-temporel, chronolord
- invocateur-noble, grand-conjurateur
- dragonmage-sang, sage-draconique
- inquisiteur-sang-pur, grand-inquisiteur
- archonte-imperial
- gardien-astral, lame-flottante, esprit-noble

**Sons** : froid sans son dédié dans le core → placeholder `magic-faeriefire.ogg` (TODO :
son de glace custom). Le reste utilise des sons du core (sword-1, spear, mace, staff,
claws, flame-big, lightning, magic-faeriefire).

**Traits custom (TODO optionnel)** : « Sang Noble » (+10 % rés. arcane) et « Éducation
Impériale » (+1 dégât magique) — laissés en TODO pour rester stable ; la résistance arcane
d'élite est déjà dans les movetypes.

## Checklist de test

- [x] L'add-on charge sans erreur WML (`-u test_hal_load` → PASS / exit 8).
- [x] Ère + faction + invocation chargent et tournent (IA-vs-IA headless, exit 0, 0 erreur).
- [x] Galerie visuelle OK (`-t hal_showcase`).
- [ ] En MP local : l'ère apparaît, la faction est sélectionnable, le meneur Archonte est posé.
- [ ] Recrutement des 7 recrues, avancements N1→N2→N3, AMLA des unités finales.
- [ ] Specials visibles et fonctionnels : magical, marksman, slow, firststrike, drain, châtiment.
- [ ] Invocation : menu clic-droit sur case libre adjacente, serviteur posé, disparaît après ~2 tours.
- [ ] Aucune image rouge manquante (placeholders core en place).
