# Dépannage

## Le skill n'apparaît pas

- Vérifiez le chemin : `ls ~/.claude/skills/site-web-sans-look-ia` doit afficher `SKILL.md`. Le fichier ne doit pas être dans un sous-dossier de plus.
- Relancez Claude Code après l'installation.
- Pour une installation par projet, lancez Claude Code depuis la racine du projet.

## Le skill ne se déclenche pas

Nommez-le dans la demande : « suis le skill site-web-sans-look-ia ».

## `npx impeccable detect` échoue

Impeccable est facultatif. Sans lui, le skill prévoit des contrôles manuels et le rapport indique « détection automatique : N/A » (section 6 de [SKILL.md](../skills/site-web-sans-look-ia/SKILL.md)). Pour les erreurs de l'outil, voir son dépôt : https://github.com/pbakaus/impeccable

## L'import dans claude.ai est refusé

Vérifiez que l'archive contient le dossier `site-web-sans-look-ia` à sa racine, avec `SKILL.md` dedans (pas le fichier seul).

Voir aussi : [INSTALLATION.md](INSTALLATION.md), [LIMITATIONS.md](LIMITATIONS.md).
