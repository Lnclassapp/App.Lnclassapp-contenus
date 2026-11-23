# Leçons à reprendre

Les 54 leçons encore hors de `../lecons/`, sur les 438 sorties de `../lecons/` par le chantier [`base-de-lecons`](https://github.com/Lnclassapp/App.Lnclassapp/blob/Develop/docs/chantiers/base-de-lecons/memo.md) (2026-11-06). Les 45 leçons de Tle C, les 45 de Tle D, les 32 de Tle A1, les 31 de Tle A2 et les 10 d'Histoire-Géographie de Tle y sont revenues au format complet, ainsi que les 105 fichiers des leçons 1 à 5 de chaque série et matière de 1ère et les 27 de 2nde (chantiers [`lecons-tle-c-comme-thales`](https://github.com/Lnclassapp/App.Lnclassapp/blob/Develop/docs/chantiers/lecons-tle-c-comme-thales/memo.md), [`lecons-tle-d-comme-thales`](https://github.com/Lnclassapp/App.Lnclassapp/blob/Develop/docs/chantiers/lecons-tle-d-comme-thales/memo.md), [`lecons-tle-a1-comme-thales`](https://github.com/Lnclassapp/App.Lnclassapp/blob/Develop/docs/chantiers/lecons-tle-a1-comme-thales/memo.md), [`lecons-tle-a2-comme-thales`](https://github.com/Lnclassapp/App.Lnclassapp/blob/Develop/docs/chantiers/lecons-tle-a2-comme-thales/memo.md) et [`lecons-tle-comme-thales`](https://github.com/Lnclassapp/App.Lnclassapp/blob/Develop/docs/chantiers/lecons-tle-comme-thales/memo.md), #484 ; [`lecons-1ere-2nde-debut`](https://github.com/Lnclassapp/App.Lnclassapp/blob/Develop/docs/chantiers/lecons-1ere-2nde-debut/memo.md)). Ici, rien n'est chargé par Develop, Staging ni le jeu standard.

Chaque fichier garde son chemin `<catégorie>/<niveau-série>/<matière>/<leçon>.json`. Le classement fichier par fichier est dans [`classement.tsv`](https://github.com/Lnclassapp/App.Lnclassapp/blob/Develop/docs/chantiers/base-de-lecons/classement.tsv) (catégorie `traitee` pour un fichier revenu par `lecons-1ere-2nde-debut`).

| Catégorie | Fichiers | Ce qui manque |
|---|---:|---|
| [`format-v1/`](format-v1/) | 54 | tout : le format 1 est refusé à l'import (`format_retired`), la leçon est à réécrire en v3 |

Les 72 fichiers de `sujets-manquants/` et les 17 de `exercices-et-sujets-manquants/`, tous de 1ère, sont revenus dans `lecons/` le 2026-11-23 (chantier `contenus-1ere-rangs-6-a-10`, issue #678) : 4 sujets de devoir de 4 exercices chacun, et un second exercice par notion pour les 17 derniers.

## Règle de retour

Un fichier revient dans `lecons-traitees/<niveau-série>/<matière>/` (même chemin, sans la catégorie) quand il a le format complet (4 blocs et 2 exercices par notion, 4 problèmes, 4 sujets de devoir de 4 exercices) et que `ruby script/contenus/valider.rb <fichier>` ne rend aucune erreur. Il quitte alors `a-reprendre/` dans le même commit. Pour que le jeu standard le charge, l'ajouter aussi à `db/seeds/standard/jeu.yml`.
