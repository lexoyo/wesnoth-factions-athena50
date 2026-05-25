# Forge-Garde — installation manuelle

Faction multijoueur originale pour **The Battle for Wesnoth 1.19**.
Pas de serveur, pas de compte : tu copies un dossier, tu relances le jeu.

## Pré-requis

- **Wesnoth 1.19** (même branche que celle utilisée pour créer l'add-on).
  Vérifie ta version dans le menu principal du jeu (en bas). Une 1.18 ou 1.16 **ne chargera pas** l'add-on.

## 1. Récupérer le dossier

À partir de `Forge_Garde.zip` : **décompresse-le**. Tu obtiens un dossier nommé exactement :

```
Forge_Garde/
├── _main.cfg
├── _info.cfg
├── units/  factions/  eras.cfg  images/  utils/  tests/  ...
```

> ⚠️ Le dossier **doit** s'appeler `Forge_Garde` (avec le tiret bas, cette casse). C'est codé en dur dans l'add-on — le renommer le casse.

## 2. Trouver le dossier add-ons de Wesnoth

| OS | Chemin |
|---|---|
| **Linux** | `~/.local/share/wesnoth/1.19/data/add-ons/` |
| **Windows** | `Documents\My Games\Wesnoth1.19\data\add-ons\` |
| **macOS** | `~/Library/Application Support/Wesnoth_1.19/data/add-ons/` |

Astuce : le jeu t'indique son dossier de données dans **Préférences → Général → « Ouvrir le répertoire des données utilisateur »** (puis va dans `data/add-ons/`). Si `data/` ou `add-ons/` n'existent pas, crée-les.

## 3. Y déposer le dossier

Place `Forge_Garde/` directement dans `add-ons/`. Résultat attendu :

```
<userdata>/data/add-ons/Forge_Garde/_main.cfg
```

> ⚠️ Erreur classique : un dossier en trop. Si tu obtiens `add-ons/Forge_Garde/Forge_Garde/_main.cfg`, remonte le dossier d'un cran.

## 4. Lancer et jouer

1. (Re)lance Wesnoth.
2. **Multijoueur → Partie locale** (Hotseat ou contre l'IA).
3. Choisis une ère fournie par l'add-on :
   - **« Défaut + Forge-Garde »** — les factions classiques **+** Forge-Garde (pour jouer contre les factions de référence).
   - **« Forge-Garde (solo) »** — miroir Forge-Garde (test/équilibrage).
4. Côté faction, choisis **Forge-Garde**.

Tu peux aussi inspecter les unités sans lancer de partie : **Aide → Unités → Nains** (les unités « Forge-Garde »).

## Désinstaller

Supprime simplement le dossier `Forge_Garde/` du répertoire `add-ons/`.

## Ça ne marche pas ?

- **L'ère n'apparaît pas** → mauvais dossier, ou dossier doublé (cf. étape 3), ou mauvaise version de Wesnoth (étape 0).
- **Erreurs au démarrage** → vérifie que tout le contenu du zip est présent (surtout `_main.cfg` à la racine de `Forge_Garde/`).
- **Sprites manquants / carrés rouges** → le dossier `images/` n'a pas été copié entièrement.
