# Forge-Garde — add-on Wesnoth (faction naine mécanique)

Add-on **de type ère** pour Wesnoth 1.19. Ajoute la faction multijoueur originale
**Forge-Garde** : nains ingénieurs runiques, automates de vapeur et constructs gravés de runes.

Faction **lente mais increvable**, **anti-magie** et **anti-poison**, taillée pour le **siège** et le
combat **positionnel**. Les constructs (race mécanique) **s'auto-réparent** et ignorent poison/drain/peste ;
les nains vivants dépendent des villages.

## Installation (déjà faite sur cette machine)

L'add-on est relié par lien symbolique dans le userdata du jeu :

```
~/.local/share/wesnoth/1.19/data/add-ons/Forge_Garde  ->  ~/_/wesnoth-factions/Forge_Garde
```

Pour une autre machine : copier le dossier `Forge_Garde/` dans `<userdata>/data/add-ons/`.

## Jouer

1. Lancer le jeu : `cd ~/_/wesnoth && ./build/wesnoth --data-dir ~/_/wesnoth`
2. **Multijoueur** → **Partie locale** (Hotseat / vs IA).
3. Choisir l'une des deux ères fournies :
   - **« Défaut + Forge-Garde »** (`era_forge_garde`) — les 7 factions classiques **+** Forge-Garde. À utiliser pour jouer Forge-Garde **contre** les factions de référence.
   - **« Forge-Garde (solo) »** (`era_forge_garde_solo`) — miroir Forge-Garde, pratique pour tester/équilibrer.
4. Côté faction, choisir **Forge-Garde**.

## Roster v1 (8 recrues N1 → N2, meneur N2 → N3)

| Recrue (N1) | Rôle | Particularité |
|---|---|---|
| Forgeron-Mécano | soin | **Répare** : soigne seulement les constructs |
| Cuirassé | tank | construct, auto-réparation |
| Foreur de Vapeur | bélier | charge (×2 donné/subi) |
| Tonne-Forge | tireur | bâton de tonnerre `perforant 18×1` |
| Mortier-de-Forge | siège | `feu 14×2`, presque immobile |
| Maître-des-Runes | soutien | commandement |
| Sentinelle Runique | gardien | fermeté + poing `magique` |
| Brise-Sort | anti-magie | aura **protection runique** (+feu/+arcane) |
| **Thane de Forge** *(meneur)* | commandant | commandement, → Seigneur des Runes (N3) |

## Forces / faiblesses

- **Forces :** durabilité, auto-réparation sans village, immunité poison/drain (constructs), anti-magie, siège à gros dégâts.
- **Faiblesses (contre voulu) :** **contondant + feu**, **lenteur** (PM 4 → cède villages/initiative), unités **chères**.

## Statut

- **v1 = N1 + N2 jouables et validés** (chargement headless OK, IA vs IA sans erreur).
- À venir : niveaux **N3** complets des 8 lignes, art custom (sprites actuels = placeholders du core), puis les 2 autres factions (Chitine, Bois-Pourri).
- Design complet : voir `../FACTIONS_DESIGN.md`.
