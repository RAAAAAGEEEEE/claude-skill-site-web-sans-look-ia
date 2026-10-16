---
name: site-web-sans-look-ia
description: Pour concevoir, construire ou revoir une page, une maquette ou un site web (vitrine, SaaS, page de jeu) afin qu'il ressemble à un site fait par des humains et pas à un template généré par IA. Méthode, interdits, stack et CSS modernes à jour d'octobre 2026, outils Claude Code (frontend-design, Impeccable, Playwright, Figma MCP) et vérification avant livraison.
---

# Sites web sans look « IA »

Version 2.0.0 du 16/10/2026. Sources datées en fin de fichier.

**Périmètre :** pages, maquettes, sites vitrines, pages de jeu, interfaces SaaS, refontes.
**Hors périmètre :** identité de marque complète (logo : utiliser un skill dédié), rédaction longue (utiliser un skill de rédaction), back-end.

Si le projet a déjà un design system (CLAUDE.md, tokens, `globals.css`, charte), il prime ; ces règles comblent les trous.

## 1. Ordre d'exécution

1. **Cadrer** (aucun code) : écrire `PRODUCT.md` ou une note de cadrage de 10 lignes : sujet, publics, tâche n°1 du visiteur, ton, contraintes, matière réelle disponible (captures, logo, vidéos, textes). Avec Impeccable installé : `/impeccable init` écrit ce fichier.
2. **Références** : relever 2 sites réels du secteur et leurs conventions (structure, pas l'identité).
3. **Plan visuel** avant le code : 4 à 6 couleurs nommées avec leur rôle, rôles typographiques (une famille, ou deux très distinctes), concept de mise en page en une phrase, l'unique animation d'entrée. Relire ce plan et retirer tout ce qui est générique.
4. **Directions** : si la direction n'est pas fixée, livrer 2 ou 3 variantes sur la même matière, chacune avec un parti pris nommé.
5. **Construire** (section 4), puis **vérifier** (section 6), puis **livrer** (section 7).

En mode **revue** d'un site existant : sauter 3-4, lancer la détection (section 6), classer les problèmes par gravité, corriger ce qui est demandé, revérifier.

## 2. Partir du métier, pas d'un template

- La page d'accueil sert la tâche n°1 : souvent une recherche, une liste, un bouton d'achat ou de téléchargement, une démo jouable. Pas un slogan géant.
- Matière réelle d'abord : captures, vidéos courtes, logo, textures du produit. Le décor générique (blobs, halos, illustrations 3D) remplace une matière qu'on n'a pas.
- Données réelles uniquement ; en maquette, une valeur inconnue s'écrit XX et la page le dit.

## 3. Interdits (signes d'une page générée)

**Mise en page**
- Héros plein écran, gros slogan vague, deux boutons centrés.
- Rangée de 3-4 « gros chiffres » en tuiles ; grille de 3 cartes identiques ; cartes dans des cartes ; piles de tuiles-icônes ; bordure colorée sur le côté gauche des cartes.
- Petit surtitre en capitales (« eyebrow ») sur chaque section ; sections numérotées 01, 02, 03 sans vraie séquence.
- Chaque page qui retombe sur la médiane : mêmes blocs, même rythme, même symétrie.

**Couleur et matière**
- Dégradés violet/bleu, boutons en dégradé, néon, glassmorphism, halos lumineux, point qui pulse.
- Crème + terracotta ; quasi-noir + une couleur acide ; « beige IA » ; noir ou gris purs au lieu de neutres teintés ; texte gris sur fond coloré.
- Ombres douces et `rounded-2xl` sur tout.

**Typographie et texte**
- Inter, Roboto, Arial, Space Grotesk par défaut ; titre en serif italique « display » sans raison.
- Un mot du titre mis en couleur d'accent ; titres creux interchangeables (« Build faster. Ship smarter. »).
- « Découvrez », « Révolutionnez », « Boostez », superlatifs, lorem ipsum.

**Mouvement et décor**
- Fondu + glissement vers le haut sur chaque section ; easing élastique ou rebond partout ; carrousels ; lecture automatique avec son.
- Emojis en décor, icônes au trait génériques (Sparkles…), personnages de banque d'images trop lisses.

## 4. Construire

**Stack (octobre 2026)**
- Petit site (1 à 5 pages) : HTML + CSS natif (variables, `@layer`, nesting), aucun framework. Servi tel quel par nginx ou n'importe quel hébergement statique.
- Site plus grand ou contenu en Markdown : Astro 6 (sortie statique, API Fonts pour l'auto-hébergement des polices, CSP stable ; Node 22+).
- Tailwind v4 est optionnel ; le CSS natif suffit pour une vitrine.
- Pas de JavaScript pour faire joli : réservé au comportement (lecteur vidéo au clic, menu, formulaire).

**CSS moderne utilisable sans repli** (Baseline au 16/10/2026) : container queries, `:has()`, `color-mix()`, `oklch`/`oklab`, couleurs relatives, `light-dark()`, `text-wrap: balance`, `@scope`, `@starting-style`, `popover`, `<dialog>`, polices variables, view transitions dans un même document.

**Avec amélioration progressive seulement** (pas encore partout, Firefox en retard) : transitions entre pages (`@view-transition { navigation: auto; }`), animations au défilement (`animation-timeline`, à placer dans `@supports (animation-timeline: view())` avec un état final lisible sans animation), anchor positioning (repli : `popover`/`dialog`), `text-wrap: pretty`.

**Règles de construction**
- Tokens sur `:root` (couleurs nommées par rôle, espacements, rayons), mode sombre via variables ; contraste AA ; couleurs d'état doublées d'un mot.
- Typographie choisie pour le sujet, auto-hébergée (aucun appel à un CDN de polices), lignes de moins de 80 caractères, chiffres tabulaires pour les données.
- Grille asymétrique (8/4, 7/5), blocs de tailles inégales, un ou deux points focaux par écran ; filets fins plutôt que cartes.
- Une seule animation d'entrée orchestrée ; tout mouvement respecte `prefers-reduced-motion`.
- Cibles tactiles ≥ 44 px, focus visible, aucun défilement horizontal à 390 px, navigation au clavier.
- Médias : vidéos en `<video muted loop playsinline>` avec poster, chargées au clic pour les vidéos tierces ; images avec texte alternatif et dimensions ; un état « sans visuel » typographique soigné.

**Page de jeu vidéo (cas particulier)**
- Au-dessus de la ligne de flottaison : nom du jeu, une phrase qui dit ce que fait le joueur, le bouton d'action principal (jouer, wishlist, télécharger) et une boucle de gameplay réelle.
- Steam : widget officiel en iframe (`store.steampowered.com/widget/<appid>/`). App Store : badge officiel Apple non modifié, noir par défaut, hauteur ≥ 40 px, marge d'un quart de sa hauteur, lien tiré d'Apple Marketing Tools, mentions de marque Apple dans les mentions légales.
- 3 ou 4 boucles de 3 à 6 s montrant chacune une mécanique différente ; vidéo muette en boucle plutôt que GIF sur le site.
- Page presse statique : fiche technique, bande-annonce téléchargeable, 8 à 15 captures, logos, zip des visuels.
- Références dont la structure marche : celestegame.com (boutiques en barre, grille de captures, presse en pied de page), playbalatro.com (menu court, boutons par plateforme).

## 5. Outils Claude Code

| Outil | Rôle | Coût |
|---|---|---|
| Skill `frontend-design` (Anthropic, plugin officiel) | Planifier la direction avant le code, plancher qualité | Gratuit |
| Skill Impeccable (`npx impeccable install`, Apache-2.0) | `/impeccable critique`, `audit`, `polish`, `quieter`, `typeset`, `layout`… ; `npx impeccable detect <dossier ou url>` : règles déterministes sans IA (code 0 propre, 2 problèmes) | Gratuit |
| Playwright MCP ou script de capture | Captures desktop et mobile à chaque itération, contrôles écrits (débordement, contraste, focus) | Gratuit |
| Serveur MCP Figma (`https://mcp.figma.com/mcp`) | Lire un design existant, pousser une page sur le canevas pour la retoucher | Lecture limitée par offre ; écriture sur canevas gratuite en bêta ; `generate_image` et les retouches IA consomment des crédits |

- Le code reste la source de vérité ; Figma n'est utile que si quelqu'un retouche dans Figma.
- Ne jamais utiliser `generate_image` (Figma ou autre service payant) pour des maquettes sans accord explicite : préférer la matière réelle du projet ou des formes dessinées en CSS/SVG.

## 6. Vérifier avant de livrer

1. Captures réelles à 1440 px et 390 px, regardées (pas seulement générées).
2. `npx impeccable detect` sur le dossier ou l'URL locale si Impeccable est installé ; corriger jusqu'au code 0 ou justifier chaque exception.
3. Relire la page contre la section 3 : toute section qui pourrait appartenir à n'importe quel site est refaite avec un élément propre au métier.
4. Contrôles : pas de défilement horizontal à 390 px, contraste AA, focus visible, `prefers-reduced-motion` respecté, aucune requête vers un tiers non voulue (polices, analytics).

**Repli** : si Impeccable ou Playwright ne sont pas disponibles, faire les contrôles 1, 3 et 4 à la main et l'écrire dans le rapport (« détection automatique : N/A »).

## 7. Livraison

- Un lien consultable (page publiée ou serveur de prévisualisation) + captures desktop et mobile.
- Variantes : une planche par variante, nommée par son parti pris.
- Rapport court :

```
Variante B « Plateau » — https://… (desktop + mobile)
Détection : impeccable detect → 0 problème
Contrôles : 390 px sans débordement, contraste AA, focus visible, animations coupées en mouvement réduit
Écarts assumés : surtitre unique sur la section presse (convention des pages presse)
```

## 8. Installation

- Personnelle : copier ce dossier dans `~/.claude/skills/site-web-sans-look-ia/`.
- Par projet : le copier dans `.claude/skills/site-web-sans-look-ia/` du dépôt.
- Optionnel : `npx impeccable install` pour la détection automatique.

## 9. Sécurité et confidentialité

Le skill n'envoie rien par lui-même. `impeccable detect` tourne en local. Le serveur MCP Figma envoie le contenu de la page à Figma : seulement si l'utilisateur l'a demandé. Ne jamais mettre de données personnelles réelles dans une maquette.

## Sources (consultées le 16/10/2026)

- frontend-design : github.com/anthropics/claude-code/tree/main/plugins/frontend-design (SKILL.md mis à jour le 02/09/2026)
- Impeccable 4.6.0 (15/10/2026) : github.com/pbakaus/impeccable, impeccable.style
- Figma MCP : help.figma.com/hc/en-us/articles/39888612464151 ; developers.figma.com/docs/figma-mcp-server/write-to-canvas ; developers.figma.com/docs/figma-mcp-server/rate-limits-access
- Astro 6 : astro.build/blog/astro-6 (10/03/2026)
- Baseline : api.webstatus.dev (16/10/2026), developer.chrome.com/docs/web-platform/view-transitions/cross-document, web.dev/blog/interop-2026 (12/02/2026)
- Marqueurs « look IA » (blogs, pas d'étude indépendante) : wildsite.substack.com/p/what-looks-like-ai-slop (02/10/2026), 925studios.co/blog/ai-slop-design-tells
- Steam widget : partner.steamgames.com/doc/marketing/widget ; badge Apple : developer.apple.com/app-store/marketing/guidelines
