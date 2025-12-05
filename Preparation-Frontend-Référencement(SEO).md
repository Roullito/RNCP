## Module 8 – Frontend : Référencement (SEO) & SERP

### 8.1. Rôle de ce module dans la préparation RNCP

Ce module est la **deuxième partie** de la préparation aux compétences **Frontend** pour le RNCP 5 (DWWM).

Objectif :  
Être capable de :

- expliquer ce qu’est le **SEO**,
- citer et appliquer **quelques bonnes pratiques simples** dans une application web,
- comprendre ce qu’est une **SERP**,
- répondre aux **questions classiques du jury** sur le sujet.

---

### 8.2. Définition : qu’est-ce que le SEO ?

**SEO** = *Search Engine Optimization* → **référencement naturel**.

En résumé :

> Le SEO regroupe toutes les techniques qui permettent à un site web d’apparaître **plus haut dans les résultats des moteurs de recherche** (Google, Bing, etc.), **sans payer de publicité**.

Quelques points clés :

- “Naturel” = résultats “organiques”, pas sponsorisés.
- Le but : **augmenter la visibilité** et **le trafic qualifié**.
- Ce n’est pas uniquement du marketing :  
  le développeur joue un rôle important dans :
  - la structure HTML,
  - les balises,
  - les performances techniques.

---

### 8.3. La SERP : c’est quoi ?

**SERP** = *Search Engine Results Page*  
→ la **page de résultats** que tu vois après avoir fait une recherche sur Google.

En général, une SERP contient :

- des résultats “classiques” (liens bleus + description),
- parfois des **extraits enrichis** (rich snippets),
- des encadrés (featured snippets, People Also Ask),
- des résultats locaux (Google Maps),
- des annonces (Ads).

En entretien, tu peux résumer simplement :

> “La SERP, c’est la page qui liste les résultats de recherche. Le SEO vise à améliorer la position de notre site dans cette page.”

---

### 8.4. Comment appliquer le SEO dans un site / app web ?

Pour un développeur web RNCP5, on attend surtout les bases suivantes :

#### 8.4.1. Structure HTML sémantique

- Utiliser les bonnes balises :
  - `<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<footer>`.
  - Un seul `<h1>` par page, puis `<h2>`, `<h3>`, etc. pour structurer le contenu.
- Effet :
  - Aide les moteurs à comprendre le **sujet** et la **hiérarchie** du contenu.

#### 8.4.2. Balises importantes pour le SEO

Les plus classiques à connaître :

- `<title>` : **titre de la page**, affiché dans l’onglet + SERP.
- `<meta name="description">` : courte description de la page (souvent reprise dans la SERP).
- Balises de titres : `<h1>`, `<h2>`, `<h3>`.
- Attributs `alt` sur les images :
  - description de l’image,
  - utile pour l’accessibilité **et** pour le SEO.
- URLs propres :
  - `/strategies/macd` plutôt que `/page.php?id=5`.

Tu peux citer aussi, sans rentrer dans les détails :

- Open Graph (`og:title`, `og:description`),
- `robots.txt` / meta `robots` (index / noindex),
- `sitemap.xml`.

#### 8.4.3. Contenu & mots-clés

- Avoir un **contenu pertinent** et compréhensible.
- Utiliser des **mots-clés** cohérents avec la requête cible, sans bourrage.
- Organiser le contenu avec titres, sous-titres, paragraphes.

#### 8.4.4. Performance & technique

- Vitesse de chargement :
  - images optimisées,
  - CSS/JS minifiés ou raisonnables,
  - éviter les ressources inutiles.
- Mobile-friendly :
  - design **responsive**, lisible sur mobile.
- Pas d’erreurs critiques :
  - liens cassés,
  - erreurs 404 non gérées.

---

### 8.5. Pourquoi faire du SEO dans le cadre d’une application web ?

Même si l’application n’est pas un “blog” ou un “site vitrine”, le SEO est utile :

- Pour un **portfolio de développeur** :  
  → être trouvable par des recruteurs / clients.
- Pour une **app SaaS / dashboard public** :  
  → page d’accueil, documentation, pages marketing, etc.

Dans ton cas :

- Ton **Smart Trading Bot** peut être **accompagné** :
  - d’une **page de présentation** publique (landing page),
  - d’un **portfolio** qui présente le projet.
- Tu peux y appliquer le SEO, même si le dashboard d’admin lui-même n’a pas vocation à être référencé.

---

### 8.6. Notions SEO à connaître (niveau RNCP5)

Liste simple que tu peux retenir / recracher au jury :

1. **SEO = Search Engine Optimization** → améliorer la visibilité d’un site dans les résultats naturels des moteurs de recherche.
2. **SERP** : Search Engine Results Page → la page de résultats après une recherche.
3. Bonnes pratiques basiques :
   - balise `<title>` descriptive,
   - `meta description` claire,
   - un `<h1>` par page,
   - structure sémantique des titres (`<h2>`, `<h3>`…),
   - attributs `alt` sur les images,
   - URLs propres.
4. Importance du :
   - **contenu pertinent**,
   - **performance** (vitesse),
   - **responsive design**,
   - **accessibilité**.

---

### 8.7. Exemples de questions SEO possibles au RNCP

Tu peux t’attendre à des questions du type :

- “Qu’est-ce que le SEO ?”
- “Quelle est la différence entre SEO et publicité Google Ads ?”
- “Qu’est-ce qu’une SERP ?”
- “Citez 3 bonnes pratiques SEO à appliquer dans une page web.”
- “À quoi sert la balise `<title>` ? Et la meta description ?”
- “Comment un développeur peut-il améliorer le SEO d’un site ?”
- “Quelles sont les balises HTML importantes pour le référencement ?”

Tu peux préparer des réponses **Très simples**, par exemple :

- **Définition courte :**  
  *“SEO means Search Engine Optimization. It is about improving a website so that it appears higher in the natural search results of Google.”*

- **Exemple de bonnes pratiques :**  
  *“We can use a clear title tag, a good meta description, semantic headings, alt text for images, and make the page fast and mobile-friendly.”*

---

### 8.8. Application à ton projet (portfolio + Smart Trading Bot)

Pour être crédible devant le jury, tu peux :

1. **Mentionner ton portfolio** :
   - Page d’accueil avec :
     - `<title>` propre,
     - `meta description`,
     - structure en `<h1>`, `<h2>`,
     - texte décrivant ton métier / tes projets (dont le Smart Trading Bot).
2. **Montrer que tu sais faire** :
   - Expliquer ce que tu as mis en place concrètement :
     - balises,
     - structure,
     - responsive,
     - performances.
3. **Relier au bot** :
   - Même si le **dashboard** n’est pas indexé, tu peux dire :
     - “Pour la partie publique (présentation du projet / doc), j’applique les bonnes pratiques SEO de base…”
     - “Pour la partie privée (dashboard), je me concentre plutôt sur UX, accessibilité et performance.”

---

### 8.9. Checklist personnelle – SEO RNCP5

- [ ] Je sais **définir le SEO** en une phrase simple.  
- [ ] Je sais **expliquer ce qu’est la SERP**.  
- [ ] Je peux citer au moins **5 bonnes pratiques SEO** (title, meta description, h1, alt, responsive…).  
- [ ] J’ai au moins **une page (portfolio ou landing page)** où j’applique ces bonnes pratiques.  
- [ ] Je sais expliquer **comment**, en tant que développeur, je peux améliorer le SEO d’un site.  
- [ ] Je suis prêt à répondre à des **questions simples** du jury sur le référencement naturel.

