# site-web-sans-look-ia

Skill Claude Code pour concevoir, construire ou revoir un site web qui ne ressemble pas à un template généré par IA.

## Le problème

Un modèle livré à lui-même produit la même page : héros plein écran, trois cartes identiques, dégradé violet, titre creux. Le visiteur le repère en une seconde et perd confiance.

## Pour qui

Les développeurs et indépendants qui construisent des sites vitrines, des pages de jeu ou des interfaces SaaS avec Claude Code, et qui veulent un résultat tenu par un humain.

## Ce que le skill apporte

- Une méthode en cinq étapes : cadrer, relever des références, fixer un plan visuel, construire, vérifier.
- Une liste d'interdits concrets (mise en page, couleur, typographie, mouvement).
- Un état du CSS utilisable sans repli et du CSS à n'employer qu'en amélioration progressive, daté du 16/10/2026.
- Un cas particulier : la page de jeu vidéo (Steam, App Store).
- Le bon usage des outils compatibles : `frontend-design`, Impeccable, Playwright, serveur MCP Figma.
- Une checklist de vérification et un rapport de livraison court.

## Statut

Version 2.0.0, stable. Ce sont des règles écrites, sans code ni script : rien à compiler, rien à exécuter. Les sources datées sont en fin de [SKILL.md](skills/site-web-sans-look-ia/SKILL.md).

## Prérequis

- Claude Code.
- Facultatif : Node.js pour `npx impeccable`, Playwright pour les captures.

## Quickstart

Installation personnelle :

```bash
git clone https://github.com/RAAAAAGEEEEE/claude-skill-site-web-sans-look-ia.git
mkdir -p ~/.claude/skills
cp -r claude-skill-site-web-sans-look-ia/skills/site-web-sans-look-ia ~/.claude/skills/
ls ~/.claude/skills/site-web-sans-look-ia
```

La dernière commande doit afficher `SKILL.md`. Relancez ensuite Claude Code, puis demandez par exemple : « Construis la page d'accueil de mon outil en suivant le skill site-web-sans-look-ia. » Installation par projet et import dans claude.ai : [docs/INSTALLATION.md](docs/INSTALLATION.md).

## Exemple de sortie

Rapport de livraison demandé par la section 7 du skill (exemple illustratif) :

```
Variante B « Plateau » — https://… (desktop + mobile)
Détection : impeccable detect → 0 problème
Contrôles : 390 px sans débordement, contraste AA, focus visible, animations coupées en mouvement réduit
Écarts assumés : surtitre unique sur la section presse (convention des pages presse)
```

## Architecture

Un seul fichier de règles, chargé par Claude Code quand la tâche porte sur un site. Détail : [docs/ARCHITECTURE.md](docs/ARCHITECTURE.md).

## Configuration

Aucune. Voir [docs/CONFIGURATION.md](docs/CONFIGURATION.md).

## Sécurité et confidentialité

Le skill n'envoie rien par lui-même. Le serveur MCP Figma, si vous l'activez, envoie le contenu de la page à Figma. Voir la section 9 du [SKILL.md](skills/site-web-sans-look-ia/SKILL.md). Le dépôt ne contient ni code exécutable ni secret.

## Limites

- Le skill réduit le look « IA », il ne remplace ni un designer ni du contenu réel.
- Les marqueurs de ce look viennent de blogs de praticiens, pas d'une étude indépendante.
- L'état du CSS est daté du 16/10/2026 et vieillira.

Liste complète : [docs/LIMITATIONS.md](docs/LIMITATIONS.md).

## Feuille de route (non contractuelle)

- Revue des règles CSS à chaque mise à jour de Baseline.
- Exemples avant/après, si des cas publiables apparaissent.

## Contribuer

Les suggestions et corrections sont bienvenues : [CONTRIBUTING.md](CONTRIBUTING.md).

## Licence

MIT, voir [LICENSE](LICENSE).

## Documentation

- [Architecture](docs/ARCHITECTURE.md)
- [Installation](docs/INSTALLATION.md)
- [Utilisation](docs/USAGE.md)
- [Configuration](docs/CONFIGURATION.md)
- [Dépannage](docs/TROUBLESHOOTING.md)
- [Limites](docs/LIMITATIONS.md)
- [Mentions légales et attributions](docs/LEGAL_AND_ATTRIBUTION.md)
- [Journal des changements](CHANGELOG.md)
