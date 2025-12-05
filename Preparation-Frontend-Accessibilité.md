## Module 9 – Frontend : Accessibilité Web (RNCP5)

### 9.1. Rôle de ce module dans la préparation RNCP

Ce module est la **troisième partie** de la préparation Frontend pour le titre DWWM (RNCP5).

Objectif :  
Tu dois :

- comprendre ce qu’est **l’accessibilité web**,
- savoir **pour qui** on le fait,
- connaître les **grandes règles et standards** (W3C, WCAG, RGAA, WAI, ARIA),
- être capable de citer et d’appliquer **quelques bonnes pratiques HTML / CSS**,
- répondre à des **questions simples** du jury sur l’accessibilité.

> On ne te demande pas d’être expert a11y, mais d’avoir **des bases solides** et de montrer que tu prends le sujet au sérieux.

---

### 9.2. Concepts & acronymes à connaître

#### 9.2.1. W3C

- **W3C** = *World Wide Web Consortium*.
- C’est l’organisme international qui définit les **standards du Web** :
  - HTML, CSS, etc.
  - et aussi les **recommandations d’accessibilité** (via WAI / WCAG).

> C’est une référence “officielle” : quand tu cites le W3C, tu montres que tu t’appuies sur des standards reconnus.

#### 9.2.2. Accessibilité web

L’**accessibilité web**, c’est le fait de rendre un site ou une application :

- utilisable par des personnes avec :
  - déficience visuelle (malvoyance, cécité),
  - déficience auditive,
  - handicap moteur,
  - troubles cognitifs,
- dans des contextes variés :
  - écran petit,
  - mauvaise connexion,
  - usage au clavier uniquement, etc.

En résumé :

> L’accessibilité, c’est **permettre à tout le monde d’utiliser le site**, quelles que soient ses capacités ou son contexte.

#### 9.2.3. WAI

- **WAI** = *Web Accessibility Initiative*.
- C’est une initiative du W3C dédiée à l’accessibilité numérique.
- Elle produit notamment les **WCAG**, des documents, tutoriels, etc.

Tu peux la retenir comme :  
> “La branche accessibilité du W3C.”

#### 9.2.4. WCAG

- **WCAG** = *Web Content Accessibility Guidelines*.
- Ce sont les **recommandations internationales** pour rendre le contenu web accessible.
- Elles sont structurées autour de 4 grands principes (facile à citer au jury) :
  - **P**erceivable (perceptible),
  - **O**perable (utilisable),
  - **U**nderstandable (compréhensible),
  - **R**obust (robuste).  
  → Acronyme **POUR** (en français, souvent : *Perceptible, Utilisable, Compréhensible, Robuste*).

Pour le RNCP5, tu dois surtout :

- savoir que WCAG existe,
- savoir que ce sont les **bases internationales**,
- pouvoir citer 2–3 exemples de règles (contraste, textes alternatifs, navigation clavier…).

#### 9.2.5. RGAA

- **RGAA** = *Référentiel Général d’Amélioration de l’Accessibilité*.
- C’est la **traduction / adaptation française** des WCAG pour les services publics (administrations, etc.).
- Il fournit :
  - des **critères**,
  - des **tests**,
  - des **checklists** par thématique.

Pour toi, ça sert surtout de **référence** :

- tu peux dire que tu t’inspires du RGAA (et des WCAG) pour vérifier quelques points de base sur tes interfaces.

#### 9.2.6. ARIA / WAI-ARIA

- **ARIA** = *Accessible Rich Internet Applications*.
- C’est un ensemble d’**attributs HTML** pour aider les technologies d’assistance (lecteurs d’écran, etc.) à comprendre les interfaces riches (menus dynamiques, modales, SPA…).

Exemples :

- `role="navigation"`, `role="button"`, `role="dialog"`,
- `aria-label`, `aria-labelledby`, `aria-expanded`, `aria-hidden`, etc.

Important :

- ARIA **complète** le HTML sémantique, mais ne le remplace pas.
- On commence toujours par :
  - un HTML propre,
  - une structure logique,
  - puis on ajoute ARIA **si nécessaire**.

---

### 9.3. Pour qui fait-on l’accessibilité ?

Pour :

- les personnes aveugles ou malvoyantes (lecteurs d’écran),
- les personnes daltoniennes (contrastes, couleurs),
- les personnes avec handicap moteur (navigation clavier, gros clics),
- les personnes sourdes (sous-titres, pas de contenu audio-only sans alternative),
- les personnes avec difficultés de compréhension (texte clair, structure simple),

Mais aussi pour :

- les gens sur mobile,
- ceux avec une connexion lente,
- ceux dans un environnement bruyant ou très lumineux, etc.

Message simple à retenir pour le jury :

> L’accessibilité aide les personnes en situation de handicap, mais **améliore aussi l’expérience pour tout le monde**.

---

### 9.4. Comment rendre un site plus accessible ? (notions de base)

Tu n’as pas besoin d’être expert RGAA/WCAG, mais tu dois connaître et appliquer **quelques bons réflexes HTML / CSS / UX**.

#### 9.4.1. HTML sémantique

- Utiliser les bonnes balises :
  - `<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<footer>`.
- Utiliser une hiérarchie cohérente de titres :
  - 1 seul `<h1>`,
  - puis `<h2>`, `<h3>` pour structurer le contenu.

Effet : les lecteurs d’écran peuvent naviguer plus facilement.

#### 9.4.2. Texte alternatif & images

- Toujours mettre un `alt` **pertinent** sur les images importantes :
  - Ex : `alt="Graphique montrant l’évolution du PnL de la stratégie MACD"` pour ton bot.
- Pour les images purement décoratives :
  - `alt=""` (alt vide) pour que le lecteur d’écran les ignore.

#### 9.4.3. Contraste & lisibilité

- Vérifier le contraste entre le texte et l’arrière-plan :
  - utiliser des outils comme **Contrast Finder**.
- Éviter :
  - texte gris clair sur fond blanc,
  - petits textes illisibles.
- Prévoir :
  - tailles de police raisonnables,
  - suffisamment d’espace entre les éléments.

#### 9.4.4. Navigation clavier

- S’assurer que :
  - on peut naviguer dans les éléments interactifs avec la touche **Tab**,
  - l’**ordre de tabulation** est logique,
  - les éléments focusables ont un **focus visible** (bordure, surbrillance).
- Éviter les composants JS qui :
  - ne sont accessibles que à la souris,
  - empêchent le focus sur certains éléments.

#### 9.4.5. Formulaires & labels

- Toujours associer les champs de formulaire avec des `label` (`for` + `id`).
- Indiquer clairement les erreurs et champs obligatoires :
  - message texte,
  - pas uniquement la couleur.

#### 9.4.6. ARIA (niveau de base)

- Utiliser ARIA selon les besoins :
  - `role="button"` pour un élément non standard qui agit comme un bouton (mais le mieux reste d’utiliser `<button>`),
  - `aria-label` pour décrire un bouton qui n’a pas de texte visible (ex : icône seule),
  - `aria-expanded` pour indiquer l’état d’un menu repliable.

---

### 9.5. Outils et ressources utiles

- **Validateurs d’accessibilité** :
  - checkers en ligne (Axe, WAVE, etc.),
  - intégrations dans les devtools.
- **Guides & référentiels** :
  - Site du **W3C** et de la **WAI**,
  - **WCAG** pour les règles globales,
  - **RGAA** pour les critères et tests (par thématique).
- **Outils de contrastes** :
  - *Contrast Finder* pour vérifier si ton texte est suffisamment lisible.

Pour un RNCP5, il suffit de montrer que :

- tu sais que ces outils existent,
- tu en as utilisé au moins un (ou que tu sais comment le faire).

---

### 9.6. Application à ton projet « Smart Trading Bot »

Quelques exemples concrets faciles à placer dans ton dossier / ton oral :

- **Structure du dashboard** :
  - `<header>` avec le titre de l’app,
  - `<nav>` pour les onglets (Stratégies, Historique, Paramètres),
  - `<main>` pour le contenu principal.
- **Graphiques & tableaux** :
  - `aria-label` ou `aria-describedby` pour décrire un graphique important,
  - caption / header de colonnes explicites dans les tableaux de trades.
- **Boutons de contrôle** :
  - utiliser de vrais `<button>` (pas des `<div>` cliquables),
  - ajouter un texte clair (“Start strategy”, “Stop strategy”).
- **Contrastes & couleurs** :
  - ne pas indiquer seulement BUY/SELL par la couleur (rouge/vert),
  - ajouter du texte ou une icône et vérifier les contrastes.
- **Navigation clavier** :
  - vérifier que l’on peut :
    - lancer/stopper une stratégie au clavier,
    - naviguer dans le tableau de trades avec Tab / flèches.

Tu peux dire au jury par exemple :

> “J’ai appliqué quelques règles de base d’accessibilité : structure sémantique, textes alternatifs pour les graphiques, navigation clavier sur les principaux contrôles, et vérification du contraste sur les couleurs critiques.”

---

### 9.7. Questions possibles au RNCP sur l’accessibilité

Exemples de questions typiques :

- “Qu’est-ce que l’accessibilité web ?”
- “Pourquoi est-ce important ?”
- “Qu’est-ce que WCAG ? Et RGAA ?”
- “Citez 3 bonnes pratiques pour rendre un site plus accessible.”
- “Qu’est-ce que ARIA ? Dans quel cas est-ce utile ?”
- “Comment avez-vous pris en compte l’accessibilité dans vos projets ?”

Tu peux te préparer des réponses courtes comme :

- **Définition :**  
  “Web accessibility means making websites usable by as many people as possible, including people with disabilities.”

- **Exemple de bonnes pratiques :**  
  “Use semantic HTML, alt text on images, good color contrast, and allow full keyboard navigation.”

---

### 9.8. Checklist personnelle – Accessibilité RNCP5

- [ ] Je sais expliquer simplement **ce qu’est l’accessibilité web** et pourquoi elle est importante.  
- [ ] Je peux dire ce que sont **W3C**, **WAI**, **WCAG**, **RGAA** et **ARIA** (même de façon très synthétique).  
- [ ] Je connais au moins **5 bonnes pratiques HTML/CSS** pour améliorer l’accessibilité.  
- [ ] Je sais citer **au moins un outil** de vérification d’accessibilité / contraste.  
- [ ] Je peux expliquer comment j’ai pris en compte l’accessibilité dans **au moins un de mes projets** (portfolio, dashboard, etc.).  
- [ ] Je me sens capable de répondre à 2–3 questions du jury sur le sujet sans paniquer.

