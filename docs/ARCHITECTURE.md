# Architecture

Le dépôt contient un seul skill, sans code.

```
skills/site-web-sans-look-ia/SKILL.md   # les règles (source de vérité)
docs/                                    # documentation
```

## Fonctionnement

Claude Code lit le front-matter de `SKILL.md` (`name`, `description`) au démarrage. Quand une demande porte sur une page, une maquette ou un site, il charge le fichier entier et suit ses sections.

| Section de SKILL.md | Contenu |
|---|---|
| 1 | Ordre d'exécution (cadrer, références, plan visuel, directions, construire) |
| 2 | Partir du métier |
| 3 | Interdits |
| 4 | Construire (stack, CSS, jeu vidéo) |
| 5 | Outils Claude Code |
| 6 | Vérifier |
| 7 | Livrer (rapport) |
| 8 à 9 | Installation, sécurité |

## Principe de documentation

Les règles ne sont écrites qu'à un endroit, `SKILL.md`. Les documents de `docs/` expliquent comment l'installer et l'utiliser, et renvoient au fichier pour le fond.

Voir aussi : [USAGE.md](USAGE.md), [CONFIGURATION.md](CONFIGURATION.md).
