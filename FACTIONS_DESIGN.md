# Add-on Wesnoth — 3 factions multijoueur originales

> Document de design prêt pour implémentation (WML, ère compatible Défaut/Âge des Héros).
> Cible : **Wesnoth 1.19.x**. Aucune modification du moteur — uniquement des capacités, types de
> déplacement, spéciaux d'arme et seuils d'XP déjà supportés par le moteur.

---

## 0. Conventions & socle de design (à lire avant les factions)

### Types de dégâts (rappel moteur)
`tranchant` (blade) · `perforant` (pierce) · `contondant` (impact) · `feu` · `froid` · `arcane`.
- **Anti-armure / anti-résistant** → `contondant` (écrase) ou frappes magiques.
- **Anti-haute-défense / esquive** → beaucoup de frappes, ou spécial `magique` (70 % touche) / `tir d'élite`.

### Alignements
`loyal` (+25 % le jour) · `chaotique` (+25 % la nuit) · `neutre` (insensible) · `liminal` (+25 % à l'aube/crépuscule, −25 % en plein jour ET pleine nuit).

### Philosophie de coûts (références Wesnoth)
| Niveau | PV | Coût | XP→suivant |
|---|---|---|---|
| N0 (chair à canon) | 18-28 | 8-12 | 18-24 |
| N1 | 26-44 | 13-19 | 30-48 |
| N2 | 45-62 | 27-40 | 70-150 |
| N3 (élite) | 55-75 | 50-70 | — |
Entretien = niveau de l'unité en or/tour (sauf N0 et unités *fidèles*).

### Capacités & spéciaux utilisés (tous natifs WML)
Capacités : `soin (heals)`, `guérison (cures)`, `régénération (regenerates)`, `commandement (leadership)`, `embuscade (ambush)`, `camouflage nocturne (nightstalk)`, `fermeté (steadfast)`, `illumine`, `submersion`, `[resistance]`/`[leadership]` custom (aura).
Spéciaux d'arme : `poison`, `ralentit (slow)`, `tir d'élite (marksman)`, `magique (magical)`, `charge`, `attaque sournoise (backstab)`, `drain (vol de vie)`, `nuée (swarm)`, `première frappe`.

### Lisibilité des forces/faiblesses
Chaque faction a **une faiblesse dure et lisible** qui sert de contre universel :
- **Couvée de Chitine** → le **feu** + le **jour**.
- **Pacte de Bois-Pourri** → l'**arcane (sacré)** + le **terrain découvert**.
- **Clans de Forge-Garde** → le **contondant + feu** + la **lenteur** (perte du contrôle de carte).

---
---

# FACTION 1 — LA COUVÉE DE CHITINE (insectoïdes)

*Noms suggérés : **La Couvée de Chitine** · L'Essaim Creux · Les Engeances de la Ruche.*

## 1. Fantasme de faction
Une civilisation-ruche d'insectes géants émergée des cavernes profondes d'Irdya. Pas une « race »
au sens classique : une **conscience collective** qui sacrifie l'individu pour la ruche. Elle submerge
par le nombre, le venin et une **évolution biologique fulgurante** — les soldats mûrissent en monstres
en quelques batailles. Native de l'univers Wesnoth via les cavernes, les marais et la nuit.

## 2. Identité de jeu
- Unités **bon marché, jetables, rapides, fragiles** individuellement.
- **Chaotique** (forte la nuit) — sauf quelques piliers neutres.
- **Poison**, **embuscade nocturne**, **synergie de ruche** (soin + commandement de la Reine).
- **Boule de neige** : XP faibles = évolution rapide → snowball si on survit aux premiers tours.
- Style **sacrifice / nuée** : on échange des drones contre du tempo et de l'attrition.

## 3. Liste de recrutement (N1) + meneur
Drone de la Couvée · Moucheron Fileur · Scarabée-Carapace · Épine-de-Venin · Cracheur d'Acide ·
Nourricière · Fouisseur · Broie-Fer  →  **Meneur : Reine de la Couvée**.

## 4. Arbres d'évolution
| Ligne | N1 | N2 | N3 (élite) |
|---|---|---|---|
| Nuée mêlée | Drone de la Couvée | Ravageur | **Faucheur de la Couvée** |
| Vol/éclaireur | Moucheron Fileur | Frelon | **Déchireur du Ciel** |
| Tank | Scarabée-Carapace | Scarabée de Siège | **Scarabée-Bastion** |
| Venin | Épine-de-Venin | Lancier Toxique | **Rôdeur Pestilent** |
| Distance bio | Cracheur d'Acide | Cracheur Caustique | **Gueule Corrosive** |
| Soutien ruche | Nourricière | Matrone de Ruche | **Mère de Ruche** |
| Furtif | Fouisseur | Mante Tapie | **Gueule Nocturne** |
| Anti-armure | Broie-Fer | Mâchoire-Faille | **Brise-Monde** |
| Meneur | — | Reine de la Couvée | **Souveraine de Ruche** |

## 5. Détail unité par unité
> Format : PV / PM / coût / alignement / attaques / capacités / **rôle**.

- **Drone de la Couvée** (N1) — 28 PV / 6 PM / 12 or / chaotique. Mandibules `tranchant 5×3` *(nuée)*.
  *Rôle :* chair à canon de flanc, capture de villages, sacrifice. Évolue vite (XP 28). → Ravageur.
- **Ravageur** (N2) — 44 PV / 6 PM. Mandibules `tranchant 7×3 (nuée)`. *Rôle :* nuée renforcée.
- **Faucheur de la Couvée** (N3) — 58 PV / 7 PM. `tranchant 9×3 (nuée)` + *première frappe*. *Élite évoluée* polyvalente.
- **Moucheron Fileur** (N1, vol) — 22 PV / 9 PM (vole) / 15 or / chaotique. Morsure `tranchant 4×2`.
  *Rôle :* éclaireur, capture, harcèlement. → Frelon.
- **Frelon** (N2, vol) — 34 PV / 9 PM. Dard `tranchant 5×2 (poison)`. *Rôle :* harceleur empoisonneur volant.
- **Déchireur du Ciel** (N3, vol) — 46 PV / 9 PM. `tranchant 7×2 (poison)`. *Rôle :* assassin aérien des blessés.
- **Scarabée-Carapace** (N1) — 44 PV / 4 PM / 17 or / **neutre**. Ruée `contondant 8×2`. **Fermeté**.
  *Rôle :* enclume, tient les lignes jour comme nuit (atténue la faiblesse diurne). → Scarabée de Siège.
- **Scarabée de Siège** (N2) — 56 PV / 4 PM. `contondant 10×2`. **Fermeté**. *Rôle :* mur + casse-armure.
- **Scarabée-Bastion** (N3) — 70 PV / 4 PM. `contondant 13×2`. **Fermeté**. *Rôle :* anvil anti-armure ultime.
- **Épine-de-Venin** (N1) — 26 PV / 6 PM / 15 or / chaotique. Dard `tranchant 5×2 (poison)`.
  *Rôle :* empoisonneur, ramollit tanks/élites. → Lancier Toxique.
- **Lancier Toxique** (N2) — 38 PV / 6 PM. `perforant 7×2 (poison)`. *Rôle :* venin + portée mêlée.
- **Rôdeur Pestilent** (N3) — 50 PV / 7 PM. `perforant 8×3 (poison)`. *Rôle :* attrition de pointe.
- **Cracheur d'Acide** (N1) — 30 PV / 5 PM / 16 or / chaotique. Mêlée `tranchant 4×2` ; **Distance** crachat `contondant 7×2`.
  *Rôle :* soutien à distance, anti-armure à distance (contondant). → Cracheur Caustique.
- **Cracheur Caustique** (N2) — 40 PV / 5 PM. Distance `contondant 9×2`. *Rôle :* artillerie bio.
- **Gueule Corrosive** (N3) — 52 PV / 5 PM. Distance `contondant 11×2`. *Rôle :* **anti-armure à distance** dédié.
- **Nourricière** (N1) — 27 PV / 5 PM / 16 or / **neutre**. **Soin +4**. Mêlée faible `tranchant 3×2`.
  *Rôle :* clé du snowball — maintient l'essaim en vie. → Matrone de Ruche.
- **Matrone de Ruche** (N2) — 40 PV / 5 PM. **Soin +8 · Guérison**. *Rôle :* hôpital mobile.
- **Mère de Ruche** (N3) — 52 PV / 5 PM. **Soin +8 · Guérison**. *Rôle :* soutien d'élite.
- **Fouisseur** (N1) — 30 PV / 6 PM / 17 or / chaotique. Griffes `tranchant 6×2 (attaque sournoise)`. **Camouflage nocturne**.
  *Rôle :* assassin/embusqueur, dévastateur la nuit (invisible). → Mante Tapie.
- **Mante Tapie** (N2) — 42 PV / 6 PM. `tranchant 8×2 (sournoise)`. **Camouflage nocturne**. *Rôle :* tueur de soutiens.
- **Gueule Nocturne** (N3) — 54 PV / 7 PM. `tranchant 10×2 (sournoise)`. **Camouflage nocturne · embuscade**. *Rôle :* terreur nocturne.
- **Broie-Fer** (N1) — 34 PV / 5 PM / 16 or / chaotique. Mandibules broyeuses `contondant 9×2`.
  *Rôle :* **anti-armure** mêlée — fissure nains/constructs/scarabées. → Mâchoire-Faille.
- **Mâchoire-Faille** (N2) — 46 PV / 5 PM. `contondant 12×2`. *Rôle :* perce-tank.
- **Brise-Monde** (N3) — 58 PV / 5 PM. `contondant 15×2`. *Rôle :* anti-armure dévastateur.
- **Reine de la Couvée** (N2, *meneur*) — 50 PV / 5 PM / **neutre**. Mandibules royales `tranchant 7×3` ; **Commandement** (« Esprit de Ruche » : alliés de niveau inférieur adjacents +25 % dégâts).
  *Rôle :* centre de commandement — la protéger = gagner. → Souveraine de Ruche.
- **Souveraine de Ruche** (N3, meneur) — 64 PV / 5 PM. `tranchant 9×3` ; **Commandement · Festin** (gagne des PV en tuant).
  *Rôle :* meneur qui grossit en dévorant — incarne le snowball.

## 6. Attaques & types de dégâts (synthèse)
Mêlée majoritaire `tranchant` (mandibules) ; **venin** = `poison` (Épine, Frelon) ; **anti-armure** = `contondant`
(Scarabée, Broie-Fer, Cracheur) ; à distance = crachat `contondant`. **Aucune attaque de feu** → l'Essaim ne
contre jamais une faiblesse au feu adverse, ce qui le rend dépendant du nombre/poison.

## 7. Interactions de terrain
Type de déplacement **chitine** : excellent en **caverne, forêt, marais** (défense 60-70 %, 1 PM),
moyen en collines, **mauvais en plaine et eau** (insectes terrestres exposés). Les volants ignorent
le terrain (1 PM partout) mais ont une **mauvaise défense** en l'air (cibles faciles pour les archers).

## 8. Philosophie des résistances
- **Chitine légère** : `perforant +10` (carapace dévie), `tranchant 0`, **`contondant −20` · `feu −30` · `froid −20`** · `arcane 0`.
- **Chitine lourde** (Scarabées) : `tranchant +40 · perforant +40 · contondant 0 · feu −20 · froid −10 · arcane 0`.
- **Ailé** (volants) : `perforant −20` (faciles à abattre) · `froid −30` · reste 0/−10.
- Faiblesse signature : **feu** (drakes, mages) et **contondant** (nains, infanterie lourde loyaliste).

## 9. Forces & faiblesses
**Forces :** masse + tempo, domination nocturne, poison d'attrition, mobilité (vol + skitter), évolution rapide, soin de ruche.
**Faiblesses :** unités fragiles, **feu** dévastateur, faibles le jour (atténué par Scarabée/Nourricière/Reine neutres), poison **inutile vs morts-vivants & constructs** (immunisés).

## 10. Matchups vs factions classiques
- **vs Loyalistes (loyal) :** tirer le combat vers la **nuit** ; craindre l'infanterie lourde (contondant) et le mage (feu). Équilibré.
- **vs Rebelles/elfes :** flèches perforantes peu efficaces (carapace), mais **faerie fire (arcane)** et mages (feu) piquent. Le poison ronge les elfes. Serré.
- **vs Morts-vivants (chaotique) :** même cycle jour/nuit ; **poison inutile** (immunité) → désavantage net, miser sur le nombre et le contondant.
- **vs Nains/Knalga :** besoin impératif de l'anti-armure (Broie-Fer/Cracheur) ; nains lents → les déborder.
- **vs Drakes :** **dur** — le feu drakonien (−30) brûle la chitine. Survie via nuit + nombre + poison (drakes non immunisés).
- **vs Nordistes (orcs, chaotique) :** miroir d'alignement ; flèches orques perforantes amorties ; la nuée déborde. Équilibré.

## 11. Préoccupations d'équilibrage MP
- Faction **dépendante du cycle** → garder 3 piliers **neutres** (Scarabée, Nourricière, Reine) obligatoire.
- Snowball par XP faibles → contre-mesure : la *nuée* affaiblit les drones blessés (auto-régulation), et les unités restent fragiles.
- Empilement de poison → bornes Wesnoth standard (ne tue pas, plafond, ne cumule pas au-delà de l'état « empoisonné »).
- **Le feu est le contre voulu** ; ne jamais donner de résistance au feu à l'Essaim.

## 12. Mécanique de faction (réaliste WML)
**« Évolution rapide »** : seuils `experience=` réduits de ~30 % → les insectes mutent vite (snowball). +
**nuée** (drones), **camouflage nocturne** (Fouisseur), **festin** (Reine N3), **soin/commandement** de ruche.
Aucune nouveauté moteur — uniquement de la donnée WML.

## 13. Lore suggéré
Sous Knalga et les Marais d'Effroi dort une intelligence d'essaim, la **Couvée**. Quand une ruche affleure,
elle ne pille pas : elle *assimile*. Chaque bataille la fait muter. Les peuples de surface racontent que tuer
une Couvée jeune est facile — et qu'attendre est fatal.

## 14. Direction artistique & identité de sprite
Exosquelettes chitineux, ailes translucides, **glandes à venin bioluminescentes qui brillent la nuit**
(repère visuel de « fort la nuit »). Couleur d'équipe sur les plaques de carapace et la lueur. Silhouettes :
drones bas et grouillants, Scarabée dôme massif, Mante haute et anguleuse, Reine allongée à abdomen-pondoir.
Animations : trottinement, claquement de mandibules, arcs d'acide, flash vert au poison.

## 15. Noms de faction
**La Couvée de Chitine** (principal) · *L'Essaim Creux* · *Les Engeances de la Ruche*.

---
---

# FACTION 2 — LE PACTE DE BOIS-POURRI (elfes corrompus)

*Noms suggérés : **Le Pacte de Bois-Pourri** · Les Flétris · La Kith d'Écorce-Noire.*

## 1. Fantasme de faction
D'anciens elfes sylvains qui, pour sauver leur forêt mourante, ont pactisé avec une corruption enracinée
sous les arbres-monde. La forêt vit encore — mais *fausse* : champignons phosphorescents, sève noire, ronces
animées. Ce ne sont **pas des elfes verts reskinnés** : ils ont troqué la grâce contre la **domination du terrain**,
le **flétrissement** et la **régénération impie**. Toujours Wesnoth : des elfes, mais ce que la magie sylvaine devient quand elle pourrit.

## 2. Identité de jeu
- **Contrôle du terrain** (forêt = forteresse), **embuscade**, **debuffs** (ralentissement), **régénération** (repousse fongique).
- Pression de **corruption lente** : poison (« flétrissure »), vol de vie, ralentir → attrition + contrôle.
- **Très forts en forêt, faibles en terrain découvert.** Mobilité médiocre — compensée par une **bête rapide**.
- Majorité **neutre**, quelques **chaotiques** ; faiblesse dure : **arcane (sacré)**.

## 3. Liste de recrutement (N1) + meneur
Décocheur d'Épines · Écorce-de-Ronce · Prêtresse-Flétrie · Rôdeur du Crépuscule · Croc-Flétri ·
Garde-Spore · Lame-Maudite · Appel-Malédiction · Épine-Sacrée  →  **Meneur : Esprit de Bois-Pourri**.

## 4. Arbres d'évolution
| Ligne | N1 | N2 | N3 (élite) |
|---|---|---|---|
| Archer corrompu | Décocheur d'Épines | Archer Flétri | **Tireur d'Épines-Noires** |
| Racine/tank | Écorce-de-Ronce | Mur d'Épines | **Colosse Sang-Racine** |
| Druide corrompu | Prêtresse-Flétrie | Druidesse de Flétrissure | **Tisse-Pourriture** |
| Assassin furtif | Rôdeur du Crépuscule | Épine-Nocturne | **Ombre des Bois** |
| Bête compagnon | Croc-Flétri | Croc-Pourri | **Limier de Peste** |
| Soutien fongique | Garde-Spore | Mycéliste | **Seigneur des Spores** |
| Guerrier d'élite maudit | Lame-Maudite | Danse-Lame Maudite | **Champion Ronce-Funeste** |
| Magie à distance | Appel-Malédiction | Lieur de Hex | **Oracle Maudit** |
| Anti-mort-vivant/anti-magie | Épine-Sacrée | Épine Sanctifiante | **Gardien de Bois-Courroux** |
| Ancien/arbre élite | Esprit de Bois-Pourri | Wose-Flétri | **Ancien Bois-Blême** |

## 5. Détail unité par unité
- **Décocheur d'Épines** (N1) — 30 PV / 5 PM / 15 or / neutre. **Embuscade** (forêt). Arc `perforant 5×3` ; dague `tranchant 4×2`.
  *Rôle :* dégâts à distance + embuscade. → Archer Flétri.
- **Archer Flétri** (N2) — 42 PV / 5 PM. Arc `perforant 6×3 (poison)`. **Embuscade**. *Rôle :* harceleur empoisonneur.
- **Tireur d'Épines-Noires** (N3) — 52 PV / 5 PM. Arc `perforant 8×3 (poison · tir d'élite)`. *Rôle :* sniper de forêt.
- **Écorce-de-Ronce** (N1) — 42 PV / 4 PM / 18 or / neutre. **Fermeté**. Coup de ronces `contondant 7×2`.
  *Rôle :* enclume de forêt, mur défensif (pas de régén, moins cher que l'arbre). → Mur d'Épines.
- **Mur d'Épines** (N2) — 54 PV / 4 PM. `contondant 9×2`. **Fermeté**. *Rôle :* bouchon défensif.
- **Colosse Sang-Racine** (N3) — 66 PV / 4 PM. `contondant 12×2`. **Fermeté**. *Rôle :* forteresse vivante.
- **Prêtresse-Flétrie** (N1) — 28 PV / 5 PM / 16 or / neutre. **Soin +4**. Bâton `contondant 4×2` ; lierre `froid 6×2 (ralentit)`.
  *Rôle :* soigneuse **+ contrôle (ralentir)**. → Druidesse de Flétrissure.
- **Druidesse de Flétrissure** (N2) — 40 PV / 5 PM. **Soin +8 · Guérison**. Lierre `froid 7×2 (ralentit)`. *Rôle :* soin + debuff.
- **Tisse-Pourriture** (N3) — 50 PV / 5 PM. **Soin +8 · Guérison**. Malédiction `froid 9×2 (ralentit)`. *Rôle :* contrôle d'élite.
- **Rôdeur du Crépuscule** (N1) — 30 PV / 6 PM / 17 or / **chaotique**. **Embuscade**. Dague `tranchant 6×2 (attaque sournoise)`.
  *Rôle :* assassin de forêt. → Épine-Nocturne.
- **Épine-Nocturne** (N2) — 42 PV / 6 PM. `tranchant 8×2 (sournoise)`. **Embuscade**. *Rôle :* tueur de soutiens.
- **Ombre des Bois** (N3) — 52 PV / 7 PM. `tranchant 10×2 (sournoise)`. **Embuscade · Camouflage nocturne**. *Rôle :* assassin total.
- **Croc-Flétri** (N1) — 34 PV / 8 PM / 14 or / chaotique. Morsure `tranchant 6×2`.
  *Rôle :* **mobilité de la faction** (vitesse 8) — rabat les blessés, contre la lenteur elfique. → Croc-Pourri.
- **Croc-Pourri** (N2) — 46 PV / 8 PM. `tranchant 8×2`. *Rôle :* flanqueur rapide.
- **Limier de Peste** (N3) — 56 PV / 9 PM. `tranchant 9×2 (poison)`. *Rôle :* chasseur empoisonneur véloce.
- **Garde-Spore** (N1) — 26 PV / 5 PM / 16 or / neutre. Distance nuage de spores `contondant 5×3 (poison)` ; mêlée faible.
  *Rôle :* **caster de poison/debuff** (distinct du soin de la druide). → Mycéliste.
- **Mycéliste** (N2) — 36 PV / 5 PM. Spores `contondant 6×3 (poison)`. *Rôle :* poison à distance.
- **Seigneur des Spores** (N3) — 46 PV / 5 PM. Spores `contondant 7×3 (poison)` + **Soin +4** (aura fongique). *Rôle :* attrition + soutien.
- **Lame-Maudite** (N1) — 36 PV / 5 PM / 17 or / neutre. Épée maudite `tranchant 7×2 (drain)`.
  *Rôle :* frontline qui **se soigne en frappant** (la corruption se nourrit). → Danse-Lame Maudite.
- **Danse-Lame Maudite** (N2) — 48 PV / 6 PM. `tranchant 9×2 (drain)`. *Rôle :* bruiser auto-suffisant.
- **Champion Ronce-Funeste** (N3) — 60 PV / 6 PM. `tranchant 11×2 (drain)`. *Rôle :* **élite maudite** durable.
- **Appel-Malédiction** (N1) — 26 PV / 5 PM / 17 or / neutre. Distance flétrissure `froid 7×2 (magique)`.
  *Rôle :* **magie fiable** (magique = 70 % touche) vs hautes esquives ; le froid pique les drakes. → Lieur de Hex.
- **Lieur de Hex** (N2) — 36 PV / 5 PM. `froid 9×2 (magique)`. *Rôle :* dégâts magiques sûrs.
- **Oracle Maudit** (N3) — 46 PV / 5 PM. `froid 11×2 (magique)`. *Rôle :* artilleur magique.
- **Épine-Sacrée** (N1) — 30 PV / 5 PM / 17 or / neutre. Distance épine-de-vie `arcane 6×2` ; **bonne résistance arcane**.
  *Rôle :* **anti-mort-vivant & anti-magie** — l'ironie : le vieux bois hait les *vrais* morts. → Épine Sanctifiante.
- **Épine Sanctifiante** (N2) — 40 PV / 5 PM. `arcane 7×2`. *Rôle :* tueur de morts-vivants.
- **Gardien de Bois-Courroux** (N3) — 50 PV / 5 PM. `arcane 9×2 (magique)`. *Rôle :* contre-caster d'élite.
- **Esprit de Bois-Pourri** (N1, recrutable) — 44 PV / 4 PM / 19 or / neutre. **Régénération**. Écrase `contondant 9×2`. `tranchant/perforant +` résistant, faible **feu**.
  *Rôle :* bruiser régénérant, ancré au terrain (lent). → Wose-Flétri.
- **Wose-Flétri** (N2) — 58 PV / 4 PM. `contondant 12×2`. **Régénération**. *Rôle :* siège auto-soignant.
- **Ancien Bois-Blême** (N3) — 72 PV / 4 PM. `contondant 15×2`. **Régénération**. *Rôle :* **ancien corrompu** capstone.

## 6. Attaques & types de dégâts
Archers `perforant (+poison)` ; druides/casters `froid` (flétrissure/gel) ; assassins `tranchant (sournoise)` ;
ronces/arbres `contondant` ; Lame-Maudite `tranchant (drain)` ; Épine-Sacrée `arcane` (anti-mort-vivant).
La **« flétrissure » = poison** appliquée largement (archers, limiers, spores) = pression de corruption.

## 7. Interactions de terrain
Type **bois-corrompu** : **forêt = défense 70 %, 1 PM** (maîtrise totale) ; correct en marais/collines ;
**médiocre en plaine/eau (déf. ~30-40 %)**. Lenteur générale (4-6 PM) → le **Croc-Flétri** porte la mobilité.
Les unités d'écorce/arbre **régénèrent** : tenir une forêt devient quasi inexpugnable.

## 8. Philosophie des résistances
- Type **bois-corrompu** : `tranchant 0 · perforant 0 · contondant 0 · feu −20 · froid 0 · **arcane −30**`.
- Type **écorce/arbre** : `tranchant +30 · perforant +40 · contondant −10 · **feu −40** · arcane −30 · régénération`.
- Signature : **arcane (sacré) = bête noire** (mages blancs, paladins, prêtresses, chasseurs de morts) ; **feu** sur le bois.

## 9. Forces & faiblesses
**Forces :** forteresse de forêt (70 % + embuscade + régén), boîte à outils de contrôle (ralentir, poison, drain), durabilité.
**Faiblesses :** **arcane** (−30 partout), **feu** sur le bois, **mobilité faible** hors forêt, dépendance à la carte (faibles sur cartes ouvertes), poison **inutile vs morts-vivants**.

## 10. Matchups vs factions classiques
- **vs Loyalistes :** craindre le **Mage Blanc (arcane)** ; les attirer en forêt pour les broyer (déf + embuscade + poison).
- **vs Morts-vivants :** **bon** — l'Épine-Sacrée (arcane) fond les morts ; le poison est inutile (immunité) mais l'arcane porte.
- **vs Rebelles (elfes vanille) :** miroir de forêt ; on a drain/ralentir/poison, **mais leur faerie fire (arcane) FAIT MAL**. Piquant.
- **vs Drakes :** leur **feu** brûle le bois ; mais notre **froid** (Appel-Malédiction) les pique et ils détestent la forêt (basse déf). Dépend du terrain.
- **vs Nains/Knalga :** nains résistent au perforant (nos flèches faiblissent) → passer au **contondant** (ronces) + poison ; caverne vs forêt.
- **vs Nordistes :** nombre orque + nuit ; notre mix neutre/chaotique + la forêt tiennent.

## 11. Préoccupations d'équilibrage MP
- Combo forêt 70 % + embuscade + régén + poison + ralentir + drain = **trop d'outils** → risque d'oppression sur cartes boisées et faiblesse sur cartes ouvertes (faction *swingy*).
- Garde-fous : **déf. hors forêt médiocre**, **PM bas**, **vulnérabilité arcane** comme contre dur, **drain en mêlée seulement**, soin standard (pas de cumul soin+drain illimité).

## 12. Mécanique de faction (réaliste WML)
**« Domination Sylvestre »** : embuscade en forêt + régén des unités d'écorce + déf. 70 %. **« Flétrissure » = poison**
généralisé. **Ralentir** (druides) pour le contrôle. Faiblesse arcane codée dans le type de déplacement. 100 % WML natif.

## 13. Lore suggéré
Quand la Grande Sécheresse tua leur forêt, les elfes d'An-Thar refusèrent de fuir. Ils écoutèrent la voix sous
les racines. La forêt reverdit — noire, fongique, affamée. Désormais ils ne *protègent* plus les bois : ils *sont* les bois,
et tout ce qui y entre nourrit la pourriture.

## 14. Direction artistique & identité de sprite
Elfes à peau d'écorce, excroissances fongiques lumineuses, ramures d'épines, yeux de lueur pâle ; veines
corrompues et lueur de spores en couleur d'équipe (verts maladifs, violets, pourpre-ecchymose). Woses :
écorce noircie, étagères de champignons, sève suintante. Silhouettes anguleuses/asymétriques/envahies —
nettement distinctes des elfes « propres ».

## 15. Noms de faction
**Le Pacte de Bois-Pourri** (principal) · *Les Flétris* · *La Kith d'Écorce-Noire*.

---
---

# FACTION 3 — LES CLANS DE FORGE-GARDE (nains mécaniques)

*Noms suggérés : **Les Clans de Forge-Garde** · La Légion des Rouages · Les Lige-Forge.*

## 1. Fantasme de faction
Des nains qui ont poussé l'ingénierie runique jusqu'à l'art de guerre : **automates de vapeur**, constructs
gravés de runes, mortiers runiques. **Pas de science-fiction** — de l'**ingénierie féerique ancienne** : bronze
riveté, vapeur, rouages, et des **runes** comme source d'énergie (jamais de LED/circuits). Deux classes d'unités :
**nains vivants** (neutres) et **constructs** (race mécanique : insensibles au poison/drain/peste, sans traits, auto-réparation).

## 2. Identité de jeu
- **Lents mais increvables** : hautes résistances, **fermeté**, **auto-réparation** (régén des constructs).
- **Synergie mécanique** : l'ingénieur *répare* les constructs (pas les vivants) → double économie.
- **Positionnel/défensif**, **siège** (mortier feu, canon perforant), **élites chères**.
- **Anti-magie & anti-poison** : constructs résistent à l'arcane et ignorent poison/drain → contre les casters et les empoisonneurs.

## 3. Liste de recrutement (N1) + meneur
Forgeron-Mécano · Cuirassé · Foreur de Vapeur · Tonne-Forge · Mortier-de-Forge · Maître-des-Runes ·
Sentinelle Runique · Brise-Sort  →  **Meneur : Thane de Forge**.

## 4. Arbres d'évolution
| Ligne | N1 | N2 | N3 (élite) |
|---|---|---|---|
| Ingénieur (répare) | Forgeron-Mécano | Maître-Ingénieur | **Maître de Forge** |
| Infanterie mécanique | Cuirassé | Cuirassé Lourd | **Automate de Siège** |
| Char à vapeur | Foreur de Vapeur | Juggernaut de Vapeur | **Béhémoth de Fer** |
| Tireur (arme à feu) | Tonne-Forge | Garde-Tonnerre | **Garde-Dragon Runique** |
| Artillerie/siège | Mortier-de-Forge | Mortier de Siège | **Bombarde Runique** |
| Soutien (runes) | Maître-des-Runes | Garde-Runes | **Grand Runier** |
| Construct runique | Sentinelle Runique | Colosse Runique | **Titan Cœur-de-Rune** |
| Anti-magie | Brise-Sort | Pare-Rune | **Égide de la Forge** |
| Gardien d'élite | *(via N2)* Construct-Rempart | — | **Colosse de Forge** |
| Meneur | — | Thane de Forge | **Seigneur des Runes** |

## 5. Détail unité par unité
- **Forgeron-Mécano** (N1, nain) — 32 PV / 4 PM / 15 or / neutre. **Répare** (soin +4 *uniquement* race mécanique). Clé `contondant 5×2`.
  *Rôle :* maintient les constructs en marche. → Maître-Ingénieur.
- **Maître-Ingénieur** (N2) — 44 PV / 4 PM. **Répare +8** (+ soin +4 des nains). *Rôle :* atelier mobile.
- **Maître de Forge** (N3) — 54 PV / 4 PM. **Répare +8 · Commandement (constructs)**. *Rôle :* chef de chantier.
- **Cuirassé** (N1, construct) — 42 PV / 4 PM / 16 or / neutre, mécanique. **Régénération** (auto-réparation). Bras-marteau `contondant 6×2`.
  *Rôle :* épine dorsale durable. → Cuirassé Lourd.
- **Cuirassé Lourd** (N2) — 54 PV / 4 PM. `contondant 8×2`. **Régén**. *Rôle :* mur avançant.
- **Automate de Siège** (N3) — 66 PV / 4 PM. `contondant 11×2`. **Régén · Fermeté**. *Rôle :* enclume offensive.
- **Foreur de Vapeur** (N1, construct) — 50 PV / 4 PM / 19 or / neutre, mécanique. Ruée `contondant 11×2 (charge)`. **Régén**.
  *Rôle :* bélier lourd (charge = ×2 donné ET subi). → Juggernaut de Vapeur.
- **Juggernaut de Vapeur** (N2) — 62 PV / 4 PM. `contondant 14×2 (charge)`. *Rôle :* perce-ligne.
- **Béhémoth de Fer** (N3) — 74 PV / 4 PM. `contondant 18×2 (charge)`. *Rôle :* **char à vapeur** ultime (cher).
- **Tonne-Forge** (N1, nain) — 34 PV / 4 PM / 17 or / neutre. Bâton-de-tonnerre `perforant 18×1` ; hache `tranchant 4×2`.
  *Rôle :* **burst à distance** (1 frappe énorme) — fissure les hautes-PV/tanks. → Garde-Tonnerre.
- **Garde-Tonnerre** (N2) — 46 PV / 4 PM. `perforant 25×1`. *Rôle :* anti-tank à distance.
- **Garde-Dragon Runique** (N3) — 58 PV / 4 PM. `perforant 32×1`. *Rôle :* sniper anti-élite.
- **Mortier-de-Forge** (N1, construct) — 30 PV / 3 PM / 20 or / neutre, mécanique. Mortier `feu 14×2` (distance) ; mêlée faible.
  *Rôle :* **siège** anti-grappe/anti-armure, immobile (3 PM). → Mortier de Siège.
- **Mortier de Siège** (N2) — 38 PV / 3 PM. `feu 18×2`. *Rôle :* artillerie de zone.
- **Bombarde Runique** (N3) — 48 PV / 3 PM. `feu 22×2`. *Rôle :* déni de zone dévastateur.
- **Maître-des-Runes** (N1, nain) — 30 PV / 4 PM / 16 or / neutre. **Commandement** (« Runes de Guerre »). Marteau `contondant 5×2` ; éclat runique `feu 5×2`.
  *Rôle :* multiplicateur de force. → Garde-Runes.
- **Garde-Runes** (N2) — 42 PV / 4 PM. **Commandement**. `feu 7×2`. *Rôle :* buffeur + appoint feu.
- **Grand Runier** (N3) — 52 PV / 4 PM. **Commandement**. `feu 9×2`. *Rôle :* pilier de soutien.
- **Sentinelle Runique** (N1, construct) — 40 PV / 4 PM / 18 or / neutre, mécanique. **Fermeté · Régén**. Poing runique `contondant 7×2 (magique)`.
  *Rôle :* gardien quasi-indestructible en défense ; le poing magique touche les esquiveurs. → Colosse Runique.
- **Colosse Runique** (N2) — 52 PV / 4 PM. `contondant 9×2 (magique)`. **Fermeté · Régén**. *Rôle :* mur anti-esquive.
- **Titan Cœur-de-Rune** (N3) — 64 PV / 4 PM. `contondant 12×2 (magique)`. **Fermeté · Régén**. *Rôle :* forteresse mobile.
- **Brise-Sort** (N1, nain rune-bouclier) — 36 PV / 4 PM / 17 or / neutre. **Résistance runique** (aura : alliés adjacents +20 % rés. feu/arcane). Hache-rune `tranchant 6×2`.
  *Rôle :* **anti-magie** — contre dur des casters (Rebelles, mages loyalistes, Bois-Pourri). → Pare-Rune.
- **Pare-Rune** (N2) — 46 PV / 4 PM. Aura +30 %. `tranchant 7×2`. *Rôle :* bouclier anti-sorts.
- **Égide de la Forge** (N3) — 56 PV / 4 PM. Aura +30 % · **Fermeté**. `tranchant/contondant 9×2`. *Rôle :* négateur de magie d'élite.
- **Construct-Rempart** (N2, construct — accessible via évolution Sentinelle) — 62 PV / 4 PM, mécanique. **Fermeté · Régén**. Maul `contondant 12×2`.
  *Rôle :* **gardien mécanique d'élite** (cher ~35 or). → Colosse de Forge.
- **Colosse de Forge** (N3) — 74 PV / 4 PM. `contondant 16×2`. **Fermeté · Régén**. *Rôle :* ancre + brise-tout capstone (~70 or).
- **Thane de Forge** (N2, *meneur*) — 52 PV / 4 PM / neutre. **Commandement** (nains ET constructs). Hache-rune `tranchant 8×3`.
  *Rôle :* meneur/buffeur. → Seigneur des Runes.
- **Seigneur des Runes** (N3, meneur) — 64 PV / 4 PM. **Commandement**. `tranchant 10×3` ; rune-éclair `feu 8×2` (distance).
  *Rôle :* commandant capstone.

## 6. Attaques & types de dégâts
Constructs/marteaux = `contondant` ; Tonne-Forge = `perforant 18×1` (burst anti-tank) ; Mortier = `feu` (siège/anti-grappe) ;
Sentinelle = `contondant magique` (anti-esquive) ; runes/casters nains = appoint `feu`. Peu de frappes, gros dégâts = casse les résistants.

## 7. Interactions de terrain
Type **nain** (vivants) : excellent **caverne/colline/montagne** (déf 60-70 %), correct ailleurs. Type **construct** :
lourd, PM 4 partout, **mauvais en marais/eau profonde** ; bon en caverne/plaine dure. **PM 4 généralisé** = lenteur
structurelle → cède le contrôle de carte tôt (faiblesse voulue). Le Mortier (3 PM) ne bouge quasi pas.

## 8. Philosophie des résistances
- **Construct mécanique** : `tranchant +40 · perforant +40 · froid +20 · **arcane +20**` (pas d'âme à smiter) · **`contondant −10` · `feu −20`** ; **immunités poison/drain/peste**.
- **Nain vivant** : `tranchant +20 · perforant +20 · froid +10 · contondant 0 · feu 0 · arcane −10` ; bon en caverne.
- Signature : **mur contre tranchant/perforant/arcane**, **troué par contondant & feu**.

## 9. Forces & faiblesses
**Forces :** durabilité extrême, auto-réparation sans village, **immunité poison/drain**, **anti-magie**, siège à gros dégâts, fermeté.
**Faiblesses :** **lenteur** (PM 4, perd villages/initiative), **contondant + feu** (marteaux, trolls, feu drakonien, boules de feu), **coût élevé** (peu d'unités → vulnérable au débordement/flanc).

## 10. Matchups vs factions classiques
- **vs Couvée de Chitine :** immunité poison + rés. tranchant/perforant → solide en défense ; mais l'anti-armure insecte (contondant) + le débordement par le nombre menacent les nains lents. Tenir les goulets.
- **vs Bois-Pourri :** ignore flétrissure (poison) et magie (arcane) ; mais le contondant des ronces + le drain sur les nains vivants + la mobilité de forêt gênent. Dépend du terrain.
- **vs Loyalistes :** **dur** — infanterie lourde (contondant) + mage (feu) percent les constructs ; s'appuyer sur Tonne-Forge, Brise-Sort vs mages, et tenir collines/cavernes.
- **vs Morts-vivants :** **bon** — drain & poison inutiles (mécaniques), constructs résistent froid/arcane (attaques typiques des morts).
- **vs Drakes :** **dur** — le **feu** (−20) ravage les constructs ; compenser par Tonne-Forge (perforant) et terrains serrés (drakes énormes, basse déf en caverne).
- **vs Knalga (vrais nains) :** miroir thématique ; Forge-Garde plus tanky/lent, moins mobile que les hors-la-loi. Équilibré.
- **vs Nordistes :** contondant orque (troll, grognard) + nombre vs constructs lents et chers → risque de flanc ; tenir les chokes.

## 11. Préoccupations d'équilibrage MP
- Rés. hautes + régén + fermeté + immunités = **très tanky** → **doit** rester **lent (PM 4)**, **vulnérable contondant/feu** et **cher**, sinon oppressant.
- Auto-réparation ignorant les soigneurs → peut figer les parties : **plafonner la régén à +8/tour** (comme les trolls) et limiter par le coût.
- Anti-magie + anti-poison fort contre 2-3 factions → **feu/contondant + faible mobilité = contre universel**. Siège immobile = exploitable par factions rapides (insectes, chauves-souris mortes, drakes) en débordement.

## 12. Mécanique de faction (réaliste WML)
**« Auto-réparation »** : `régénération` sur les constructs + capacité **Répare** de l'ingénieur (un `[heals]` filtré
`race=mechanical`) → les constructs se soignent sans village, les nains dépendent des villages (double économie).
**Immunités mécaniques** (poison/drain/peste) via `race=mechanical`. **Garde runique** : haute rés. arcane/feu +
aura `[resistance]` du Brise-Sort. **Siège** : ranged à grosses frappes, peu nombreuses. Tout 100 % WML natif.

## 13. Lore suggéré
Quand les filons de Forge-Garde s'épuisèrent, les nains cessèrent de creuser et se mirent à *construire*. Ils gravèrent
les vieilles runes des rois-forgerons dans le bronze et l'acier, insufflant la vapeur dans des corps de métal. Leurs
légions ne dorment ni ne saignent — elles rouillent, puis on les répare.

## 14. Direction artistique & identité de sprite
Ingénierie féerique ancienne : bronze/fer riveté, **runes lumineuses** (jamais de circuits/LED), évents de vapeur,
rouages d'horlogerie. Constructs trapus, proportions naines, plaques gravées de runes ; couleur d'équipe sur la
lueur des runes et les bannières. Char à vapeur = chaudière + chenilles rivetées + cheminée. Mortier = canon
rune-gravé. Silhouettes basses, blocs lourds — lisibles « lent et solide ». Sons : cliquetis, sifflement de vapeur, bourdon runique, boom de canon.

## 15. Noms de faction
**Les Clans de Forge-Garde** (principal) · *La Légion des Rouages* · *Les Lige-Forge*.

---
---

# ANNEXE A — Intégration en ère & équilibrage croisé

### Insertion dans l'ère
Chaque faction = un `[multiplayer_side]` (liste `recruit=` des 8 unités N1 + `leader=`/`random_leader=`)
inséré dans une `[era]` custom **ou** ajouté à l'ère par défaut via `[era]`/`[modify_side]`. Cibler ~**240 or**
de départ, 2 villages = équilibre standard. Garder ~8 recrues N1 par faction (parité avec les factions vanille).

### Matrice de matchups (résumé, perspective ligne)
| ↓ vs → | Loyalistes | Rebelles | M-vivants | Knalga | Nordistes | Drakes |
|---|---|---|---|---|---|---|
| **Chitine** | =  | = | défavorable (poison nul) | = (anti-armure requis) | = | **défavorable** (feu) |
| **Bois-Pourri** | = (peur arcane) | piquant (faerie fire) | **favorable** (arcane) | = | = | = (terrain) |
| **Forge-Garde** | **défavorable** (contondant/feu) | favorable (anti-magie) | **favorable** | = | = (flanc) | **défavorable** (feu) |

### Trois leviers d'équilibrage à surveiller en priorité
1. **Chitine** : ne jamais donner de rés. au feu ; garder 3 piliers neutres ; XP faibles mais unités fragiles.
2. **Bois-Pourri** : déf. hors-forêt médiocre + arcane −30 obligatoires ; surveiller cartes 100 % boisées (ban éventuel).
3. **Forge-Garde** : PM 4 inviolable + coût élevé + vuln. contondant/feu ; régén plafonnée à +8.

---

# ANNEXE B — Notes d'implémentation (arborescence add-on)

```
~/.local/share/wesnoth/1.19/data/add-ons/Trois_Factions/
├── _info.cfg                 # métadonnées (type=era)
├── _main.cfg                 # charge units/, factions/, era.cfg ; #textdomain
├── units/
│   ├── chitine/*.cfg         # [unit_type] insectoïdes
│   ├── bois-pourri/*.cfg     # [unit_type] elfes corrompus
│   └── forge-garde/*.cfg     # [unit_type] nains mécaniques
├── factions/
│   ├── chitine.cfg           # [multiplayer_side]
│   ├── bois-pourri.cfg
│   └── forge-garde.cfg
├── eras.cfg                  # [era] regroupant les 3 factions (+ option : ajout à l'ère Défaut)
├── utils/
│   ├── races.cfg             # [race] insectoid, corrupted_elf (mechanical existe déjà)
│   ├── movetypes.cfg         # [movetype] chitine, chitine_lourde, aile, bois-corrompu, ecorce, construct
│   └── abilities.cfg         # capacités custom : Répare (heals filtré mécanique), aura Résistance runique, Esprit de Ruche
└── images/                   # sprites + portraits (placeholder au début : réutiliser/teinter des sprites core)
```

### Pièces WML « nouvelles » mais 100 % natives
- **Répare** = `[heals]` avec `[filter] race=mechanical` (Forgeron-Mécano).
- **Résistance runique** = capacité type `[leadership]` mais `[resistance]` (aura +rés. feu/arcane, Brise-Sort).
- **Évolution rapide** = simples valeurs `experience=` basses sur les unités Chitine.
- **Immunités mécaniques** = automatiques via `race=mechanical`.
- **Embuscade/Camouflage nocturne/Fermeté/Régénération/Commandement/Drain/Poison/Ralentir/Charge/Magique/Nuée/Tir d'élite** = spéciaux & capacités du core, réutilisés.

### Démarrage pragmatique (placeholders)
Pour tester le gameplay AVANT l'art : réutiliser et **teinter** (`~RC()`, `~BG()`) des sprites du core
(insectes → réutiliser bestioles/araignées ; elfes corrompus → elfes + filtres verts/violets ; constructs →
nains + golems/woses). On valide l'équilibrage, on remplace l'art ensuite.
