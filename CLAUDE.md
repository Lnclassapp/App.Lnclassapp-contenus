# Contenus Lnclass

Ce dépôt (public) contient les leçons de Lnclass et la méthode pour les écrire. Décision : ADR-0134 de l'application `Lnclassapp/App.Lnclassapp` (chantier `contenus-depot-dedie`). Le mode d'emploi complet est dans [`README.md`](README.md).

## Règles

- **Public** : jamais de secret (jeton, clé, PIN, mot de passe), jamais de donnée d'élève, d'enseignant ou d'établissement réel. Un secret poussé par erreur est révoqué, pas seulement effacé.
- **Rédiger, corriger** : la skill `/lecon` de l'application joue le circuit (rédacteur, relecteur indépendant, validateur pédagogique, `valider.rb`). Les règles de rédaction vivent dans [`prompts/prompt-redaction.md`](prompts/prompt-redaction.md) (source unique) ; pour un lot par niveau et matière, [`prompts/prompt-redaction-lot.md`](prompts/prompt-redaction-lot.md).
- **Contrôle** : `ruby <application>/script/contenus/valider.rb <fichier>`, toujours depuis l'application (il lit les règles du domaine). La CI de ce dépôt le relance sur chaque leçon modifiée de `lecons/`.
- **Branches** : `contenus/<slug>` depuis `main`, une PR vers `main`, prête, qui vit moins d'un jour. Jamais de poussée directe ni de `--force` sur `main`.
- **Vers l'application** : une PR applicative vers `Develop`, produite par `ruby script/contenus/synchroniser.rb <clone de ce dépôt>` à un SHA de `main`. On ne corrige jamais une leçon dans `docs/contenus/lecons-traitees/` de l'application : sa CI le refuse.
- **Réponses courtes** au porteur, en français ; secrets jamais dans le chat.

## Arborescence

| Dossier | Contenu | Lu par l'application |
|---|---|---|
| `lecons/<niveau>-<série>/<matière>/*.json` | Leçons relues, format `lnclass.course-tree` v3, qui passent `valider.rb` | Oui, par copie figée (synchronisation) |
| `a-reprendre/` | Leçons mises de côté (format incomplet ou ancien) | Non |
| `progressions/` | Progressions DPFC 2026-2027 | Non (deux copies figées servent de fixtures de test dans l'application) |
| `prompts/` | Prompts de rédaction | Non |
