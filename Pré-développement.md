## Module 6 – RNCP5 : Introduction, Pré-développement & Exemples de dossiers

### 6.1. Avant de coder : poser le projet correctement

Avant de développer une application pour le RNCP5, il est impératif de clarifier :

- **L’idée du projet**
  - Exemple (Smart Trading Bot) : automatiser et suivre des stratégies de trading crypto via une application web.
- **Le périmètre**
  - Ce qui est inclus : MVP (collecte de données, stratégies de base, dashboard).
  - Ce qui est exclu : fonctionnalités futures (IA avancée, multi-tenant, trading réel, etc.).
- **Les fonctionnalités**
  - Fonctionnalités majeures, listées clairement (backtests, exécution des signaux, interface web, historique des trades, etc.).
- **Pour qui ?**
  - Profil utilisateur : développeur / trader technique qui veut tester des stratégies, ou utilisateur interne.
- **La méthodologie de travail**
  - Organisation : Kanban / Trello, TODO → In progress → Done.
  - Sprints / priorités : MVP d’abord, features bonus ensuite.
- **La conception**
  - Modèle de données (ERD / MCD, tables SQL).
  - Schémas UML si utile (architecture, séquence), mais pas obligatoires.
  - Architecture de l’application (front ↔ back ↔ BDD ↔ API).
- **L’environnement de travail**
  - Humain : projet solo ou en équipe ? interactions avec mentors / staff ?
  - Technique : OS, IDE, Git, GitHub, outils de tests, etc.
- **Les technologies choisies**
  - Front : HTML, CSS, JS (+ éventuel framework).
  - Back : Python / Node / autre, API REST.
  - BDD : SQL (focus particulièrement important pour le RNCP5).
- **Les tests**
  - Types de tests prévus :
    - Tests manuels (clics, scénarios),
    - Tests d’API (Postman, Insomnia),
    - Tests unitaires éventuels.
  - Comment tu construis tes **jeux d’essai** (données en entrée / résultats attendus).
- **La documentation**
  - Commentaires de code quand c’est utile (pas partout).
  - README structuré (installation, configuration, lancement, tests, déploiement).
  - Documentation des fichiers de config (variables d’environnement, clés API, etc.).
- **Le déploiement**
  - Où / comment tu pourrais déployer : serveur, PaaS, Docker…
  - Même si ce n’est pas en prod, tu dois **savoir expliquer la démarche**.
- **La maintenance & le lancement**
  - Comment corriger un bug, mettre à jour une stratégie, suivre les logs.
  - Comment lancer officiellement ton “produit” (cas d’usage concret).

---

### 6.2. Bagages nécessaires en développement front-end

Pour le RNCP5 DWWM, tu dois avoir des bases solides côté front :

#### 6.2.1. Responsive design

- Savoir créer des pages **responsives** avec :
  - **Flexbox**
  - **CSS Grid**
  - **Media queries**
- Application à ton projet :
  - Dashboard du Smart Trading Bot utilisable sur différents écrans (au moins desktop + un format plus petit).

#### 6.2.2. Accessibilité

- Comprendre ce qu’est l’**accessibilité** (a11y).
- Savoir comment rendre un site plus accessible :
  - Balises sémantiques (`<header>`, `<main>`, `<nav>`, etc.),
  - Attributs `alt`, labels, navigation clavier,
  - Contrastes et tailles de police.
- Exigence RNCP5 :
  - **Connaissances de base obligatoires**,
  - Tu dois soit appliquer quelques règles sur ton projet, soit savoir expliquer comment tu le ferais.

#### 6.2.3. SEO

- Savoir ce qu’est le **SEO** (Search Engine Optimization).
- Connaître quelques règles simples :
  - Titres (`<title>`, `<h1>`…),
  - Meta description,
  - Balises sémantiques,
  - Structure logique du contenu.
- Pour un dashboard interne, le SEO est secondaire, mais tu peux montrer ta compréhension sur un autre projet (ex. portfolio).

#### 6.2.4. HTML, CSS, DOM, JavaScript & devtools

- Maîtriser les bases :
  - **HTML** : structure, balises sémantiques.
  - **CSS** : styles, layout, responsive.
  - **DOM** : manipuler le DOM avec JS.
  - **JavaScript** : événements, fetch/AJAX, mise à jour de l’UI.
- Savoir utiliser les **devtools** du navigateur pour :
  - Inspecter le DOM,
  - Suivre les requêtes réseau,
  - Déboguer les erreurs JS,
  - Vérifier les styles CSS.

---

### 6.3. Bagages nécessaires en développement back-end

#### 6.3.1. API & API REST

- Savoir ce qu’est une **API** et une **API REST** :
  - Ressources, endpoints, méthodes HTTP, codes de statut.
- Savoir tester une API avec :
  - Postman, Insomnia, ou équivalent.
- Savoir ce qu’est une API **propre et sécurisée** :
  - Validation des entrées,
  - Gestion propre des erreurs,
  - Pas de fuite d’infos sensibles.

Application à ton bot :

- Endpoints pour :
  - Lancer/arrêter une stratégie,
  - Récupérer des données (signals, PnL, historique),
  - Accéder aux run de backtests.

#### 6.3.2. Base de données

- Savoir créer une BDD (SQL principalement) :
  - Tables, clés primaires/étrangères, types, contraintes.
- Sécuriser contre les **injections SQL** :
  - Requêtes paramétrées,
  - ORM éventuellement.
- Savoir la rendre évolutive :
  - Ajout de colonnes / tables sans casser l’existant.
- Savoir la tester :
  - Jeux d’essai, scripts, tests automatiques ou manuels.

Application à ton bot :

- Modéliser les entités :
  - Actifs (BTC, ETH…),
  - Bougies OHLCV,
  - Trades,
  - Stratégies et exécutions.

#### 6.3.3. Architecture & MVC

- Comprendre l’**architecture** de ton app :
  - Où se trouve le front,
  - Où se trouve le back,
  - Où est la BDD,
  - Quels liens avec l’API Bitget.
- Savoir expliquer une architecture **MVC** :
  - Model (données/BDD),
  - View (interfaces),
  - Controller (logique qui relie les deux).
- Même sans framework MVC strict, tu dois être capable de situer :
  - ce qui joue rôle de “Model”,  
  - ce qui joue rôle de “Controller”,  
  - ce qui joue rôle de “View”.

#### 6.3.4. Composants métier

- Savoir ce qu’est un **composant métier** (business logic) :
  - Code qui implémente les règles métier de ton application.
- Pour ton bot :
  - Calcul d’indicateurs (MACD, RSI…),
  - Décision BUY/SELL selon des règles,
  - Gestion du risque.

#### 6.3.5. Déploiement

- Exigence RNCP5 :
  - **Déployer ton app** ou au moins **savoir expliquer clairement** comment tu le ferais.
- Exemples :
  - Déploiement sur un VPS Linux avec serveur web,
  - Containerisation avec Docker,
  - Hébergement sur une plateforme (Railway, Render, etc.).

---

### 6.4. Autres connaissances attendues

#### 6.4.1. Organisation & Kanban

- Savoir gérer son travail avec un **tableau Kanban** (Trello suffit) :
  - Colonnes : À faire / En cours / Fait.
- Montrer que tu sais :
  - Prioriser,
  - Suivre l’avancement,
  - Découper un gros projet en tâches.

#### 6.4.2. Agile & Scrum (bases)

- Savoir définir :
  - Méthode **Agile**,
  - **Scrum** (sprints, backlog, daily, review…),
  - Rôles (Product Owner, Scrum Master, Dev Team).
- Pas besoin de savoir gérer une équipe, juste comprendre les **principes**.

#### 6.4.3. RGPD

- Comprendre les bases :
  - Données personnelles,
  - Consentement,
  - Minimisation des données, droit à l’oubli.
- Expliquer comment tu limites les données sensibles (logs, BDD…).

#### 6.4.4. DevOps (bases)

- Ce n’est pas exigé, mais des jurés peuvent poser des questions.  
  Savoir répondre simplement sur :
  - Qu’est-ce que le **DevOps** ?
  - Qu’est-ce que le **CI/CD** ?
  - Qu’est-ce que **Docker** ?
  - Différence entre **conteneurisation** et **virtualisation**.

---

### 6.5. Ce qui n’est PAS obligatoire (mais que tu peux utiliser)

- **Merise** :
  - Tu n’es pas obligé de tout maîtriser.
  - Tu dois savoir **lire un ERD / MLD** et l’implémenter en SQL.
  - Si aucun diagramme n’est fourni, un **ERD simple + code SQL** suffisent.
- **UML** :
  - Non obligatoire.
  - Tu peux l’utiliser si ça t’aide (diagrammes de séquence, classes, déploiement…).
- **Gestion de projet / équipe** :
  - Pas demandé en profondeur pour le RNCP5 (plutôt RNCP6).
- **DevOps avancé** :
  - Kubernetes, pipelines complexes, etc. non attendus.

---

### 6.6. Exemples de dossiers RNCP5 – comment s’en servir

Exemples donnés (Holberton) :

- Dossier de **Marc-Antoine** – 2 blocs de compétences DWWM.
- Dossier d’**Edouard Halimi** – 2 blocs DWWM.
- Dossiers de **Sofiane Slimane**, **Tony Nemouthe**.
- Présentation de **Florian Meignan** – 2 blocs DWWM.

> ⚠️ Attention :  
> - Le logo en bas de page a évolué.  
> - Dans la partie **“compétences du référentiel couvertes par le projet”**, il faut bien **associer chaque compétence à une partie précise du projet**.

Quand tu les consultes, regarde particulièrement :

1. **La structure** :
   - Comment ils découpent leurs projets (contextes, objectifs, env. technique, réalisations).
   - Comment ils présentent les compétences.

2. **Le niveau de détail** :
   - Ni trop flou, ni du code brut partout.
   - Beaucoup de schémas, captures, tableaux, jeux d’essai.

3. **Les liens compétences ↔ projet** :
   - Comment ils justifient CP1–CP8 à travers les fonctionnalités de leurs projets.

4. **Le ton et la mise en page** :
   - Style pro mais simple.
   - Titres clairs, numérotation propre.
   - Logo à jour et mentions correctes du titre.

Ces exemples ne sont pas à copier, mais à utiliser comme **références de qualité** pour ton dossier “Smart Trading Bot + projets complémentaires”.

---

### 6.7. Checklist personnelle – Pré-développement & inspiration

- [ ] J’ai clarifié **idée, périmètre, fonctionnalités et cible** de mon projet.  
- [ ] Je suis capable de présenter l’**architecture complète** (front, back, BDD, API).  
- [ ] Je maîtrise les **bases front** (responsive, accessibilité, SEO, JS, devtools).  
- [ ] Je maîtrise les **bases back** (API REST, BDD SQL, composants métier, sécurité).  
- [ ] Je sais expliquer comment je **déploierais** mon application.  
- [ ] J’ai lu au moins **1 ou 2 exemples de dossiers RNCP5** et repéré :
  - la structure,
  - la façon de lier compétences ↔ parties du projet.  
- [ ] Je sais lire un **ERD** et l’implémenter en SQL.  
- [ ] Je peux expliquer rapidement **Agile/Scrum, RGPD, DevOps (bases)** si on me questionne.

