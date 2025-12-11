# Dossier de Projet RNCP 5 – Smart Trading Bot

> **Titre du projet :** Smart Trading Bot – Plateforme de trading crypto automatisé
> 
> **Titre visé :** Développeur Web et Web Mobile (DWWM – RNCP niveau 5)
> 
> **Contexte :** Projet réalisé dans le cadre de la formation Holberton School et de la préparation au titre RNCP 5.

> ⚠️ Ce document est une **base de travail**. Il est volontairement incomplet et doit être **personnalisé et enrichi** par toi : exemples concrets, captures, extraits de code, métriques, ressentis, etc. L’objectif final est d’atteindre **30–50 pages** (hors page de garde, sommaire et annexes).

---

## 1. Présentation générale du projet

### 1.1. Contexte et motivation

- Présenter ton parcours (formation, intérêt pour le trading / la data / la crypto).
- Expliquer pourquoi tu as choisi de réaliser un **bot de trading crypto** comme projet RNCP :
  - automatiser des stratégies que tu faisais à la main ;
  - tester des stratégies techniques (MACD, RSI, etc.) sur un historique de données ;
  - explorer la convergence entre **développement backend**, **API**, **données financières** et, à terme, **IA**.

👉 **À compléter par toi** avec ton histoire personnelle, ton contexte précis, ton lien avec le trading.

### 1.2. Objectifs du projet

- Objectif principal : développer une **application web / backend** capable de :
  - se connecter à une **API d’exchange crypto** (ex. Bitget en mode demo) ;
  - récupérer et stocker des **données de marché** (OHLCV, volumes…) ;
  - exécuter des **stratégies de trading** configurables ;
  - journaliser les décisions & résultats (logs, historique de trades) ;
  - offrir une interface de consultation (UI web ou ligne de commande + visualisation possible).

- Objectifs secondaires (exemples) :
  - structure de code modulable (pour ajouter facilement de nouvelles stratégies) ;
  - intégrer des notions de **sécurité** (gestion des clés API, validation des entrées, logs) ;
  - préparer une future intégration **IA / machine learning** pour optimiser les décisions.

### 1.3. Périmètre fonctionnel

- **Inclus dans le périmètre** (à adapter selon ton vrai projet) :
  - Ingestion de données de marché pour plusieurs actifs (BTC, ETH, altcoins). 
  - Stockage des données dans un format structuré (BDD ou fichiers sérialisés).
  - Implémentation de plusieurs **stratégies de trading** (ex. MACD cross, RSI oversold, DCA…).
  - Simulation ou exécution réelle de trades sur un environnement de demo.
  - Console ou interface web minimale pour lancer/stopper le bot, voir l’état global.

- **Hors périmètre** (exemples) :
  - Gestion d’un portefeuille multi‑utilisateurs complet (KYC, facturation…).
  - Analyse fondamentale poussée (news, réseaux sociaux…) — prévu comme évolution.
  - Interface mobile native.

👉 **À compléter et préciser** pour cadrer clairement ton projet et éviter que le jury te demande des fonctionnalités non prévues.

### 1.4. Utilisateurs cibles

- **Utilisateur principal :** toi / un trader individuel souhaitant automatiser une partie de sa stratégie.
- **Besoin principal :** déléguer l’exécution de signaux techniques à un système fiable et configurable.
- **Contraintes :**
  - besoin de transparence (comprendre pourquoi le bot a pris telle décision) ;
  - besoin de sécurité (ne pas exposer les clés API, éviter les pertes massives) ;
  - besoin de monitoring (historique des actions, performances). 

👉 Tu peux formaliser ces besoins sous forme de **personas + user stories**.

---

## 2. Liste des compétences RNCP mises en œuvre

Cette section doit faire le lien entre ton projet et les **compétences du référentiel DWWM** (REAC).

### 2.1. Activité type 1 – Développer la partie front‑end

Même si ton projet est très backend, tu dois montrer que tu as :

- Maquetté des interfaces UI (tableaux de bord, listes de trades, configuration des stratégies).
- Réalisé des pages HTML/CSS responsives.
- Développé la partie dynamique (JS / framework) pour interagir avec l’API backend.

> Suggestion : présenter ce front comme une **interface de monitoring** et de **pilotage du bot**.

**Tableau exemple (à compléter)** :

| Compétence REAC (AT1)                                                | Comment elle est couverte dans le projet                                     |
| --------------------------------------------------------------------- | ----------------------------------------------------------------------------- |
| Maquetter des interfaces utilisateur web ou web mobile               | Maquettes du dashboard de suivi des stratégies, écran de configuration, etc. |
| Réaliser des interfaces utilisateur statiques web ou web mobile      | Pages HTML/CSS du dashboard, vue des trades, etc.                             |
| Développer la partie dynamique des interfaces utilisateur web/mobile | Appels AJAX / fetch au backend, rafraîchissement des données, filtres, etc.  |

### 2.2. Activité type 2 – Développer la partie back‑end

C’est le cœur de ton projet.

**Compétences clés :**

- Mettre en place une base de données relationnelle (ou au minimum un stockage structuré robuste).
- Développer des composants d’accès aux données (lecture/écriture des prix, des trades, des stratégies…).
- Développer des composants métier côté serveur (logique de trading, gestion du risque, ordres…).

**Tableau exemple (à compléter)** :

| Compétence REAC (AT2)                                   | Comment elle est couverte dans le projet                                           |
| -------------------------------------------------------- | --------------------------------------------------------------------------------- |
| Mettre en place une base de données relationnelle        | Schéma BDD pour OHLCV, ordres, stratégies, résultats, etc.                        |
| Développer des composants d’accès aux données SQL/NoSQL  | DAO / repository pour lire les prix, insérer des ordres, récupérer les résultats. |
| Développer des composants métier côté serveur            | Classes de stratégies, moteur de décision, gestion du risque.                     |

### 2.3. Compétences transversales

- Communiquer (README, documentation, logs explicites, messages d’erreur clairs).
- Mettre en œuvre une démarche de résolution de problème (investigation de bugs, erreurs API…).
- Apprendre en continu (veille sur nouvelles API, sur la sécurité des bots, nouvelles librairies Python…).

👉 Tu peux ajouter un tableau ou une liste décrivant 2–3 situations concrètes où ces compétences ont été mobilisées.

---

## 3. Expression des besoins du projet

### 3.1. Problématique métier

Formuler la problématique de base :

- « Comment automatiser de manière **sécurisée et configurable** l’exécution de stratégies de trading crypto en se basant sur des signaux techniques, tout en gardant une **visibilité claire** sur les décisions prises et leurs résultats ? »

### 3.2. Objectifs détaillés

- Automatiser le processus **collecte → analyse → décision → exécution → log**.
- Permettre la **configuration** des stratégies (actif, time frame, paramètres MACD/RSI, etc.).
- Simulation ou execution en conditions quasi‑réelles (demo trading, paper trading, logs).
- Préparer un socle pour des **améliorations futures** (ajout d’IA, plus de stratégies, interface plus riche, etc.).

### 3.3. Limites et contraintes

- Projet réalisé par **un seul développeur** sur une période limitée.
- Budget infrastructure restreint → utilisation de services gratuits / peu coûteux.
- Environnement **demo** pour limiter les risques financiers réels.

### 3.4. User stories (exemples à adapter)

- En tant que **trader**, je veux pouvoir **activer/désactiver** une stratégie pour un actif donné.
- En tant que **trader**, je veux **visualiser l’historique des trades** exécutés par le bot.
- En tant que **développeur**, je veux **ajouter une nouvelle stratégie** sans casser les autres.

---

## 4. Environnement humain et technique

### 4.1. Environnement humain

- Projet réalisé **en formation** (Holberton School), sans entreprise d’accueil.
- Rôle : développeur fullstack / backend unique sur le projet.
- Interactions possibles : échanges avec mentors, autres étudiants, etc. (à décrire si pertinent).

### 4.2. Environnement technique

- **Langage principal** : Python.
- **API d’exchange** : Bitget (mode demo trading) ou autre.
- **Base de données** : à préciser (PostgreSQL, MySQL, SQLite, etc.) ou équivalent (fichiers Parquet/CSV structurés).
- **Framework web / API** : Flask, FastAPI, Django REST, ou APIs internes si pas de front web complet.
- **Frontend** (si présent) : HTML/CSS/JS (éventuellement framework JS ou simple templates).
- **Outils** :
  - Git / GitHub.
  - Docker (si utilisé).
  - Postman / curl pour les tests d’API.
  - VSCode / environnement Linux.

👉 Décrire précisément **ce que tu utilises réellement**.

### 4.3. Organisation du travail

- Méthode : Kanban (Trello/Notion/board GitHub) avec backlog, “en cours”, “terminé”.
- Découpage en lots :
  - ingestion des données ;
  - stockage ;
  - indicateurs techniques ;
  - stratégies ;
  - gestion des ordres ;
  - interface, tests, sécurité, doc.

---

## 5. Conception et architecture

### 5.1. Architecture globale de l’application

Décrire la structure logique du bot :

- Couches ou modules (exemple) :
  - `api_client` : communication avec Bitget (auth, signatures, endpoints).
  - `data` : stockage / lecture des données de marché (OHLCV, tickers…).
  - `indicators` : calcul des indicateurs techniques (MACD, RSI, etc.).
  - `strategies` : implémentation des stratégies de décision (buy/sell/hold).
  - `trading` : exécution des ordres, gestion du risque, suivi des positions.
  - `ui` : interface CLI ou web.
  - `logs` : journalisation des événements.

- Type d’architecture : monolithe structuré, avec séparation claire des responsabilités.

Un **diagramme d’architecture** (à ajouter en annexe) aidera beaucoup.

### 5.2. Modèle de données

- Présenter un **schéma conceptuel** (entités + relations), par exemple :
  - `Asset` (id, symbole, nom…)
  - `Candle` (id, asset_id, timestamp, open, high, low, close, volume…)
  - `Strategy` (id, nom, paramètres…)
  - `Trade` (id, asset_id, strategy_id, type, quantité, prix, timestamp, PnL…)

- Expliquer les **choix de BDD** (SQL vs fichiers / NoSQL) et les contraintes.

### 5.3. Interfaces utilisateur (maquettes)

- Décrire les maquettes réalisées :
  - page d’accueil / dashboard ;
  - vue détail d’une stratégie ;
  - historique des trades / performances.

- Expliquer comment tu as pensé le **parcours utilisateur**.

### 5.4. Prise en compte de la sécurité et du RGPD dès la conception

- Stockage des clés API (jamais en clair dans le code, .env, chiffrement possible).
- Limitation des logs pour éviter de stocker des infos sensibles inutilement.
- Préparation d’une politique de suppression des données si tu ajoutes des comptes utilisateurs.

---

## 6. Réalisations côté front‑end

> Si ton projet ne possède pas encore de front complet, cette partie peut décrire soit une interface minimale existante, soit ce que tu as commencé à mettre en place et ce que tu prévois (mockups, PoC).

### 6.1. Maquettes et parcours

- Intégrer (ou décrire) quelques maquettes d’écran.
- Expliquer comment elles ont évolué au fil du développement.

### 6.2. Interfaces HTML/CSS (statiques)

- Décrire la structure générale (layout, header/footer, navigation).
- Donner 1–2 exemples de pages (dashboard, page stratégie) avec leurs sections principales.

### 6.3. Partie dynamique (JS / framework)

- Décrire comment les données du backend sont affichées / rafraîchies.
- Expliquer les interactions principales (boutons, filtres, formulaires de config…).

### 6.4. Responsive design et accessibilité

- Décrire comment tu as géré le responsive (media queries, flex/grid…).
- Citer quelques bonnes pratiques d’accessibilité mises en place.

### 6.5. Sécurité côté front + tests DevTools

- Expliquer les précautions côté front (pas de clé API exposée, appels au backend sécurisé…).
- Décrire quelques tests faits via DevTools (responsive, performances, audit Lighthouse).

---

## 7. Réalisations côté back‑end

### 7.1. Base de données

- Décrire l’installation ou la mise en place de la BDD.
- Fournir un extrait du **script de création** des tables principales.
- Expliquer les choix de types, d’index éventuels (sur `asset_id`, `timestamp` par ex.).

### 7.2. Composants d’accès aux données

- Décrire les fonctions / classes qui :
  - insèrent des bougies dans la BDD ;
  - lisent les historiques ;
  - sauvegardent les trades / positions.

- Expliquer comment tu gères les erreurs (ex. API down, incohérence de données).

### 7.3. Composants métier (logique de trading)

- Décrire une ou deux **stratégies** en détail (MACD, RSI, DCA…).
- Expliquer la logique d’entrée/sortie de position.
- Parler de la **gestion du risque** (taille de position, stop loss éventuel, limites d’exposition…).

### 7.4. Sécurité côté back‑end

- Gestion des **secrets** (clés API) :
  - où elles sont stockées ;
  - comment elles sont chargées ;
  - comment tu évites de les commiter.

- Validation des entrées (paramètres de stratégie, symboles, time frame…).
- Appels API dans une optique défensive (timeouts, retries, gestion des codes d’erreur).

### 7.5. DevOps et déploiement (si applicable)

- Décrire toute tentative de :
  - conteneurisation (Docker) ;
  - script de déploiement ;
  - documentation pour lancer le bot sur un serveur distant.

Même si tu n’as pas (encore) déployé en production, tu dois **au moins savoir expliquer comment tu le ferais**.

---

## 8. Tests et qualité

### 8.1. Stratégie de test

- Expliquer les types de tests mis en place :
  - tests unitaires sur les fonctions d’indicateurs / stratégies ;
  - tests d’intégration sur la chaîne complète ;
  - tests manuels via scripts ou outils (Postman, CLI…).

### 8.2. Jeux d’essai

- Décrire un ou plusieurs **jeux d’essai** :
  - données en entrée (ex. séquence de bougies) ;
  - résultat attendu (signal BUY/SELL, ordres simulés) ;
  - résultat obtenu ;
  - analyse des écarts.

### 8.3. Qualité du code

- Normes de nommage, découpage en modules.
- Documentation interne (docstrings, README, commentaires).
- Utilisation d’outils (linters, formatters) si applicable.

---

## 9. Veille technologique et sécurité

### 9.1. Veille sur les technologies utilisées

- API Bitget / autres exchanges.
- Librairies Python pour le trading / la data.
- Nouvelles approches pour la gestion des risques, la mesure de performance, etc.

### 9.2. Veille sur les vulnérabilités et la sécurité

- Problématiques de sécurité propres aux bots de trading (exposition des clés, DDoS, etc.).
- Vulnérabilités générales web/backend (injections, XSS, CSRF… même si moins directement présentes ici).
- Mesures mises en place dans ton projet suite à cette veille.

---

## 10. Bilan et perspectives

### 10.1. Résultats obtenus

- Synthèse de ce que fait ton bot aujourd’hui, de manière fiable.
- éventuellement quelques métriques (nombre de stratégies, actifs gérés, volume de données traité…).

### 10.2. Difficultés rencontrées

- Techniques (latence API, gestion des erreurs, architecture, performances…).
- Organisationnelles (temps, priorisation, courbe d’apprentissage sur certains concepts).

### 10.3. Améliorations et évolutions prévues

- Ajout d’une interface web plus poussée (gestion visuelle des stratégies, dashboards avancés).
- Mise en place de backtests plus robustes et de métriques de performance (Sharpe, max drawdown…).
- Intégration progressive de **modules IA / ML** pour aider à la prise de décision.
- Renforcement de la sécurité (meilleure gestion des secrets, surveillance, alertes, monitoring).

---

## 11. Annexes (à créer et compléter)

Les annexes peuvent contenir :

- Maquettes (Figma / Miro).
- Diagrammes d’architecture et ERD.
- Extraits de code significatifs (front + back).
- Jeux d’essai détaillés (tableaux).
- Captures d’écran de l’interface / des logs / de DevTools / de Postman.

> 💡 Conseil : n’hésite pas à **référencer les annexes** depuis le corps du document (ex. « cf. Annexe A – Schéma BDD »).

---

**Rappel :** ce document est un **squelette**. L’objectif est que tu le reprennes, que tu réécrives certaines parties avec tes mots, que tu développes chaque section pour raconter **ton** projet, dans **ton** style, tout en respectant les attendus du RNCP 5.
