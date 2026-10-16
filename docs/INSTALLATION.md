# Installation

Prérequis : Claude Code, et git pour cloner le dépôt. Aucun autre outil n'est requis.

## Personnelle (tous vos projets)

```bash
git clone https://github.com/RAAAAAGEEEEE/claude-skill-site-web-sans-look-ia.git
mkdir -p ~/.claude/skills
cp -r claude-skill-site-web-sans-look-ia/skills/site-web-sans-look-ia ~/.claude/skills/
ls ~/.claude/skills/site-web-sans-look-ia
```

La dernière commande doit afficher `SKILL.md`.

## Par projet

Depuis la racine du dépôt de votre projet :

```bash
mkdir -p .claude/skills
cp -r /chemin/vers/claude-skill-site-web-sans-look-ia/skills/site-web-sans-look-ia .claude/skills/
```

Remplacez `/chemin/vers/` par l'endroit où vous avez cloné ce dépôt.

## Dans claude.ai (import d'une archive)

Créez une archive zip qui contient le dossier `site-web-sans-look-ia` avec `SKILL.md` à l'intérieur, puis importez-la dans les réglages des skills de claude.ai. Depuis la racine du dépôt cloné :

```bash
cd skills
python3 -m zipfile -c ../site-web-sans-look-ia.zip site-web-sans-look-ia
```

## Outils facultatifs

Impeccable (détection automatique) : `npx impeccable install`. Playwright et le serveur MCP Figma s'installent selon leur propre documentation. Sans eux, le skill prévoit un repli manuel (section 6 de [SKILL.md](../skills/site-web-sans-look-ia/SKILL.md)).

## Vérifier

Relancez Claude Code, puis demandez : « Quels skills sont disponibles ? ». `site-web-sans-look-ia` doit apparaître. En cas d'échec : [TROUBLESHOOTING.md](TROUBLESHOOTING.md).
