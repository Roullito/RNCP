# Dossier de Projet RNCP 5 – Smart Trading Bot

> **Titre du projet :** Smart Trading Bot – Système de trading algorithmique automatisé pour crypto-monnaies  
> **Candidat :** [Votre Nom]  
> **Titre visé :** Développeur Web et Web Mobile (DWWM – RNCP niveau 5)  
> **Établissement :** Holberton School, France  
> **Période :** Octobre 2024 - Décembre 2025  
> **Date de soumission :** 11 décembre 2025  

---

## Sommaire

1. Présentation générale du projet  
2. Liste des compétences RNCP mises en œuvre  
3. Expression des besoins du projet  
4. Environnement humain et technique  
5. Conception et architecture  
6. Réalisations côté front-end  
7. Réalisations côté back-end  
8. Tests et qualité  
9. Veille technologique et sécurité  
10. Bilan et perspectives  
11. Annexes  

---

## 1. Présentation générale du projet

### 1.1. Contexte et motivation

Ce projet a été développé dans le cadre de ma formation à **Holberton School** (programme Full-Stack Software Engineering), en tant que **projet de fin d'études personnel et autonome**. N’ayant pas de stage en entreprise, j’ai choisi de concevoir une application complète démontrant l’ensemble de mes compétences techniques acquises durant la formation, en lien direct avec le titre professionnel **DWWM – RNCP niveau 5**.

J’ai choisi le domaine du **trading algorithmique automatisé** pour plusieurs raisons stratégiques :

**Défi technique complexe :**
- Intégration d’une API REST externe (Bitget) avec authentification HMAC SHA256  
- Traitement de données financières en temps réel (OHLCV)  
- Architecture event-driven multi-threadée  
- Gestion d’état et persistance des données (historique, métriques, résultats)

**Problématique métier concrète :**
- Automatiser des décisions de trading basées sur des signaux techniques  
- Respecter des contraintes strictes de risk management (2–4 % de risque par trade/jour)  
- Garantir la fiabilité et la traçabilité des opérations (logging exhaustif, audit complet)

**Convergence de compétences transversales :**
- **Back-end :** API REST, logique métier, gestion de données  
- **Front-end :** Dashboard Web de monitoring (Flask, HTML/CSS/JS)  
- **Sécurité :** Gestion des secrets, communication sécurisée, contrôle du risque  
- **Méthodo / qualité :** Tests, backtests, documentation, veille technologique

Ce projet m’a également permis d’explorer des concepts avancés :
- Design patterns (Strategy, Repository, séparation des couches)  
- Programmation défensive (retry logic, gestion d’erreurs)  
- Validation empirique via backtesting (profit factor, ROI, drawdown, etc.)

### 1.2. Objectifs du projet

**Objectif principal :**  
Développer un **système de trading algorithmique prêt pour un usage « proche production »** capable d’exécuter automatiquement des stratégies de trading sur les marchés de futures crypto (USDT-M) via l’API Bitget, avec un focus fort sur :

- La **fiabilité** (exécution robuste, gestion d’erreurs)  
- La **traçabilité** (logs, audit, backtests)  
- Le **risk management** (limites strictes, tailles de position contrôlées)  

**Objectifs techniques réalisés :**

1. **Collecte et stockage de données**
   - Intégration API Bitget v2 (HMAC SHA256)  
   - Récupération automatique OHLCV pour plusieurs symboles et timeframes  
   - Persistence en CSV optimisée (≈ 1500 bougies par paire / timeframe)  
   - Système de rattrapage (catchup) et monitoring en temps quasi réel  

2. **Stratégies de trading**
   - Implémentation de plusieurs stratégies techniques (MACD, RSI, EMA, Bollinger, ADX…)  
   - Paramétrage centralisé (profils prudent / normal / agressif)  
   - Génération de signaux enrichis (direction, entry, SL, TP, risk_pct, métadonnées)  

3. **Risk management**
   - Position sizing basé sur la volatilité (ATR)  
   - Limites strictes : % risque par trade, % max par jour, nb max de positions  
   - Stop-loss et take-profit automatiques  
   - Validation multi-niveaux avant exécution (risk, exposition, limites journalières)  

4. **Architecture modulaire**
   - Séparation claire : data/, strategies/, risks/, execution/, runtime/, ui/, logs/, tests/  
   - Gestion des événements (event-driven) et orchestration runtime  
   - Dashboard Flask de visualisation des positions, de l’historique et des métriques  

5. **Validation et qualité**
   - Backtests sur données historiques  
   - Jeux d’essai cohérents (jeu d’essais fonctionnels et techniques)  
   - Tests (doctests, tests d’intégration)  
   - Documentation détaillée (README, docstrings, schémas d’architecture)

### 1.3. Périmètre fonctionnel

**Périmètre réalisé :**

1. **Module DATA**
   - Récupération des chandeliers OHLCV via l’API Bitget  
   - Synchronisation périodique, gestion des manques, sauvegarde en CSV  
   - Gestion de plusieurs symboles (BTC, ETH, etc.) et timeframes (1h, 4h, 1d)

2. **Module STRATEGIES**
   - Stratégies basées sur des indicateurs techniques : MACD, RSI, EMA, Bollinger, ADX…  
   - Paramétrages par stratégie et par symbole  
   - Interface unique `BaseStrategy` pour ajouter facilement de nouvelles stratégies

3. **Module RISKS**
   - Structures de données représentant le compte, les positions, la configuration risque  
   - Calcul de tailles de position basées sur ATR et % de capital à risque  
   - Limites journalières et globales (nb de positions, drawdown, etc.)

4. **Module EXECUTION**
   - Construction d’intentions d’ordre à partir des signaux  
   - Validation (cohérence, limites, contraintes)  
   - Envoi d’ordres vers Bitget (en mode DEMO), avec gestion des erreurs et retries  

5. **Module UI (dashboard)**
   - API Flask avec endpoints JSON :  
     - `/api/positions` : positions ouvertes et PnL  
     - `/api/closed_trades` : historique récent des trades fermés  
     - `/api/account` : informations de compte (equity, marge, etc.)  
     - `/api/daily_stats` : statistiques journalières (P&L, drawdown…)  
   - Interface web HTML/CSS/JS pour visualiser ces données côté navigateur  

6. **Module LOGS & TESTS**
   - Logs structurés (console + fichiers)  
   - Journaux spécifiques (événements, ordres, health beats)  
   - Doctests, backtests, tests d’intégration sur le flux complet

**Périmètre hors-scope (évolutions futures) :**
- Gestion multi-utilisateurs (authentification, rôles, facturation)  
- Trading sur plusieurs plateformes (multi-exchange)  
- Intégration de modèles d’IA / machine learning  
- Interface front avancée type SPA (React ou Vue) avec WebSockets  
- Déploiement cloud (Docker, CI/CD, monitoring avancé)

### 1.4. Utilisateurs cibles et besoins

**Persona principal : Trader algorithmique individuel**

Profil type :
- Trader crypto déjà sensibilisé au trading technique  
- Connaissance basique des indicateurs (MACD, RSI, ATR…)  
- Budget alloué (ex. 1 000 – 50 000 USDT en conditions réelles)  
- Manque de temps pour surveiller les marchés 24/7  

Besoins auxquels le projet répond :
- **Automatisation** des entrées/sorties selon des règles définies  
- **Contrôle du risque** (limites claires, SL/TP systématiques)  
- **Visibilité** sur les résultats via un dashboard web  
- **Traçabilité** des décisions (logs et historiques exploitables)  

Quelques *User Stories* (résumées) :
- En tant que trader, je peux **activer/désactiver** une stratégie sur un symbole : configuration centralisée.  
- En tant que utilisateur, je peux **voir mes positions en temps réel** dans le dashboard.  
- En tant que développeur, je peux **ajouter une nouvelle stratégie** sans casser les autres, via une interface commune.  
- En tant que trader, je peux **backtester une stratégie** avant de la laisser tourner.

---

## 2. Liste des compétences RNCP mises en œuvre

Cette section fait le lien entre le projet et le **référentiel DWWM** (REAC/RE) :  
- **Bloc 1 : Développer la partie front-end d’une application web ou web mobile sécurisée**  
- **Bloc 2 : Développer la partie back-end d’une application web ou web mobile sécurisée**   

### 2.1. Activité type 1 – Front-end

| Compétence professionnelle (Bloc 1)                                           | Mise en œuvre dans Smart Trading Bot |
|-------------------------------------------------------------------------------|--------------------------------------|
| **Installer et configurer son environnement de travail**                      | Installation de l’environnement front (Node/npm si besoin, configuration du projet Flask pour servir le dashboard, utilisation de VSCode, Git). |
| **Maquetter des interfaces utilisateur web**                                  | Conception des écrans du dashboard : vue d’ensemble, liste des positions, historique des trades, page de détails par stratégie (maquettes papier / brouillons + organisation en sections HTML). |
| **Réaliser des interfaces utilisateur statiques web ou web mobile**           | Pages HTML/CSS servies par Flask (gabarit base, sections, tableaux, cartes de statistiques, header/footer). |
| **Développer la partie dynamique des interfaces utilisateur web ou web mobile** | JavaScript côté client pour appeler les endpoints Flask (`fetch` périodiques), rafraîchir les tableaux (positions, trades, stats) et améliorer l’expérience utilisateur. |

**Axes d’amélioration prévus :**
- Ajout de graphiques (évolution du P&L, equity curve)  
- Maquettes Figma plus détaillées  
- Accessibilité (ARIA, contrastes, navigation clavier)  
- Passage éventuel vers React/Vue à moyen terme

### 2.2. Activité type 2 – Back-end

| Compétence professionnelle (Bloc 2)                               | Mise en œuvre dans Smart Trading Bot |
|-------------------------------------------------------------------|--------------------------------------|
| **Mettre en place une base de données relationnelle**            | Le projet utilise des fichiers CSV/JSONL structurés pour les données de marché et les logs. La logique de schémas (OHLCV, trades, events) est néanmoins conçue comme si elle devait être portée dans une base relationnelle (tables marchés, ordres, positions, etc.). |
| **Développer des composants d’accès aux données SQL et NoSQL**   | Composants d’accès aux données (lecture/écriture CSV et JSONL avec pandas et utilitaires dédiés), pouvant être migrés vers une BDD relationnelle ou NoSQL ultérieurement. |
| **Développer des composants métier côté serveur**                | Modules Python pour la génération de signaux, le risk management, la construction d’ordres et l’appel à l’API Bitget. |
| **Documenter le déploiement d’une application dynamique**        | README détaillant la configuration, les variables d’environnement (`.env`), l’exécution du bot et du dashboard, et les prérequis système. |

### 2.3. Compétences transversales

| Compétence transversale DWWM                            | Mise en œuvre concrète |
|---------------------------------------------------------|------------------------|
| **Communiquer en français et en anglais**               | README technique, commentaires de code, messages de log compréhensibles, forte exposition à une documentation en anglais (Bitget, pandas, Flask). |
| **Mettre en œuvre une démarche de résolution de problème** | Débogage de l’authentification HMAC, correction des problèmes de synchronisation des bougies, gestion des erreurs réseau avec retry, adaptation des stratégies lors des backtests. |
| **Apprendre en continu**                               | Veille sur le trading algorithmique, la sécurité, l’API Bitget, les bibliothèques Python (pandas, loguru, Flask), le risk management. |

---

## 3. Expression des besoins du projet

### 3.1. Problématique métier

**Constat :**  
Le trading manuel sur les marchés crypto est :
- Très chronophage (marchés ouverts 24/7)  
- Emotionnel (stress, biais cognitifs)  
- Souvent peu structuré au niveau du risk management  

**Problématique :**  
> Comment automatiser des stratégies de trading crypto **de manière sécurisée, traçable et configurable**, en gardant une bonne visibilité sur les décisions prises et les résultats obtenus ?

### 3.2. Objectifs détaillés

**Objectifs techniques :**
1. Centraliser la collecte de données de marché (OHLCV) et les nettoyer  
2. Tester plusieurs stratégies techniques et les encoder dans du code réutilisable  
3. Intégrer une logique de **risk management** claire (taille des positions, SL/TP)  
4. Passer d’un résultat de stratégie (signal) à un **ordre exécutable** sur un exchange (API)  
5. Fournir une interface web permettant de **suivre l’activité** du bot

**Objectifs fonctionnels :**
- Pouvoir faire tourner le bot en **mode DEMO** (sans réel risque financier)  
- Avoir une configuration suffisamment souple pour activer/désactiver des combinaisons symbole/stratégie  
- Disposer d’un **historique exploitable** (fichiers, logs, dashboard)  

### 3.3. Contraintes

- Projet individuel (un seul développeur)  
- Budget nul (API gratuites, aucun service payant)  
- Environnement de type formation / projet autonome (pas de production réelle)  
- Exposition forte au risque si déployé en réel → **phase DEMO prioritaire**  
- Respect des bonnes pratiques de sécurité de base (gestion des secrets, API keys, HTTPS)

### 3.4. User Stories (sélection)

- **US01** : En tant que trader, je peux activer ou désactiver une stratégie sur un symbole précis via une configuration centralisée.  
- **US02** : En tant qu’utilisateur, je peux voir la liste de mes positions ouvertes, avec PnL, via le dashboard.  
- **US03** : En tant que développeur, je peux ajouter une nouvelle stratégie facilement en implémentant une interface commune (`BaseStrategy`).  
- **US04** : En tant que opérateur, je veux un mode DEMO pour tester sans risque.  
- **US05** : En tant que trader, je veux être certain de ne pas dépasser un certain niveau de perte journalière.

---

## 4. Environnement humain et technique

### 4.1. Environnement humain

- Projet réalisé dans le cadre de la formation Holberton (mode projet individuel)  
- Pas de client réel, mais un **“commanditaire fictif”** : un trader qui souhaite automatiser ses stratégies  
- Interactions ponctuelles avec d’autres étudiants et mentors pour des conseils techniques ou des retours sur l’architecture  

Rôle principal :  
- **Développeur full-stack** (frontend + backend + gestion de données + tests + doc)

### 4.2. Environnement technique

**Langages & frameworks :**
- Python 3.x (logique métier, backtests, orchestration)  
- Flask (exposition des endpoints du dashboard)  
- HTML / CSS / JavaScript (interface utilisateur)  

**Librairies principales :**
- `requests` : appels HTTP à l’API Bitget  
- `pandas` : manipulation des données de marché et calcul d’indicateurs  
- `loguru` : logging structuré  
- `python-dotenv` : gestion des variables d’environnement  

**Outils :**
- VSCode (IDE)  
- Git + GitHub (gestion de versions)  
- Environnement Linux / WSL / Ubuntu  
- DevTools de Chrome pour tester le front (responsive, network, performance)

### 4.3. Organisation du travail

Approche **itérative** proche d’Agile :
- Découpage en lots (API → data → stratégies → risk → exécution → UI → tests)  
- Utilisation d’un tableau type Kanban (To Do / In Progress / Done)  
- Avancement incrémental avec refactoring régulier  

---

## 5. Conception et architecture

### 5.1. Architecture globale

Application structurée en plusieurs répertoires :

- `data/` : accès à l’API, gestion des CSV/JSONL  
- `strategies/` : implémentations concrètes de stratégies (MACD, RSI, etc.)  
- `risks/` : risk manager, calcul des tailles de position  
- `execution/` : construction et envoi des ordres  
- `runtime/` : orchestration (boucle principale, détection de « bar close »…)  
- `ui/` : dashboard Flask (routes, templates)  
- `logs/` : configuration loguru + fichiers de logs  
- `tests/` : backtests et tests d’intégration  

Flux simplifié :

1. Récupération des bougies via l’API Bitget  
2. Mise à jour des CSV OHLCV  
3. Calcul des indicateurs et génération de signaux  
4. Vérification des contraintes de risque  
5. Construction et envoi d’ordres  
6. Mise à jour des logs et exposition des infos au dashboard

### 5.2. Modèle de données

**Données principales :**
- **OHLCV** (Open/High/Low/Close/Volume) par symbole/timeframe  
- **Ordres / trades** (date, symbole, sens, taille, prix d’entrée, SL, TP, PnL…)  
- **Événements** (génération de signal, envoi d’ordre, erreur…)  
- **Statistiques journalières** (P&L, drawdown, nombre de trades, etc.)

Stockage actuel :
- Fichiers CSV : `market_data/<SYMBOL>_<TF>.csv`  
- Fichiers JSONL : `logs/orders.jsonl`, `logs/events.jsonl`, `logs/health_beats.jsonl`  

Conception pensée pour être **migrée facilement** vers une BDD relationnelle (tables `ohlcv`, `orders`, `events`, etc.).

### 5.3. Interfaces utilisateur

Les principaux écrans du dashboard :

1. **Vue d’ensemble**  
   - Résumé du compte (equity, P&L du jour, drawdown…)  
   - Nombre de positions ouvertes  
   - Statistiques globales (nombre de trades, win rate simplifié…)  

2. **Liste des positions**  
   - Tableau avec : symbole, sens (long/short), prix d’entrée, prix courant estimé, PnL, SL/TP…  
   - Rafraîchissement régulier via appels AJAX/`fetch` à `/api/positions`

3. **Historique des trades**  
   - Tableau des derniers trades (date, stratégie, symbole, résultat, durée…)  
   - Données issues de `/api/closed_trades`  

4. **Statistiques journalières**  
   - Informations consolidées : P&L du jour, nombre de trades, drawdown du jour…  

### 5.4. Sécurité & RGPD dès la conception

- Clés API **jamais en clair dans le code** : utilisées via un fichier `.env` exclu du dépôt Git  
- Toutes les communications vers Bitget passent par du **HTTPS**  
- Pas de données personnelles d’utilisateurs finaux (pas de RGPD appliqué pour l’instant, mais la structure du projet permet d’ajouter un jour un espace utilisateur avec gestion RGPD)  
- Logs limités aux données techniques nécessaires (pas de données sensibles hors contexte trading)  

---

## 6. Réalisations côté front-end

Même si le projet est très backend / data, le front-end est une **brique importante** pour la démonstration RNCP : il sert à montrer la capacité à développer une interface web sécurisée qui consomme des données dynamiques.

### 6.1. Maquettes et parcours utilisateur

Le parcours utilisateur cible est le suivant :

1. Arrivée sur la page d’accueil du dashboard  
2. Consultation rapide de l’état global du bot :  
   - P&L du jour  
   - Nombre de positions ouvertes  
   - Stratégies actives  
3. Navigation vers la section **Historique des trades** pour analyser les résultats récents  
4. Consultation du détail des positions en cours (symboles, PnL, prix d’entrée, SL/TP…)

Ces parcours ont été d’abord esquissés sous forme de maquettes simples (sur papier ou outil de dessin léger), puis traduits en gabarits HTML (structure en colonnes, en-tête, sections de contenu).

### 6.2. Interfaces HTML/CSS (statiques)

Le front s’appuie sur :

- Un **gabarit principal** (template base) avec :
  - En-tête contenant le titre du projet et un indicateur d’état général  
  - Un corps de page découpé en sections (overview, positions, historique)  
  - Un pied de page avec informations techniques (version, lien GitHub)

- Des **tableaux HTML** pour :
  - Les positions ouvertes  
  - L’historique des trades  

- Des **cartes statistiques** (divs stylées) pour :
  - Le P&L du jour  
  - Le nombre de positions actives  
  - Des métriques simples (nombre de trades, win rate)

Le CSS utilise principalement :
- Flexbox pour organiser les blocs  
- Quelques media queries pour adapter la mise en page sur écrans plus petits  
- Une palette de couleurs cohérente et sobre (fond sombre / cartes plus claires, ou inverse selon choix)

### 6.3. Partie dynamique (JavaScript)

La partie dynamique repose sur du **JavaScript vanilla** :

- Utilisation de `fetch()` pour appeler les endpoints :  
  - `/api/positions`  
  - `/api/closed_trades`  
  - `/api/account`  
  - `/api/daily_stats`  

- Rafraîchissement périodique (par exemple toutes les 5 à 10 secondes) via `setInterval()` pour mettre à jour :  
  - Le tableau des positions  
  - Les cartes de statistiques  
  - L’historique récent

- Lorsque la réponse JSON est reçue, le script :
  - Vide le tableau HTML ciblé  
  - Reconstruit les lignes avec les nouvelles données  
  - Met éventuellement en forme les valeurs (P&L en vert/rouge, pourcentage…)

Ce fonctionnement montre la capacité à :
- **Consommer une API backend**  
- **Mettre à jour le DOM dynamiquement**  
- Gérer des erreurs simples (ex : afficher un message en cas d’échec de requête)

### 6.4. Responsive design et accessibilité

**Responsive :**
- La structure est pensée pour rester lisible sur des écrans plus petits (laptop, tablette) :  
  - Colonnes qui se superposent en mode mobile  
  - Largeurs relatives plutôt que fixées  
- Des media queries adaptent la taille des polices et des blocs au viewport.

**Accessibilité :**
- Utilisation d’éléments sémantiques (titres `h1`, `h2`, listes, tableaux structurés…)  
- Texte suffisamment contrasté par rapport au fond (testé avec des outils de contraste)  
- Librairie ou composants limités, afin de garder un DOM simple et sans surcharges non maîtrisées  
- Attributs `alt` sur les éventuelles icônes/images significatives  
- L’interface étant principalement un outil interne de monitoring, des améliorations ARIA sont prévues en évolution (rôles sur les tableaux, messages dynamiques annonçables par lecteur d’écran, etc.).

### 6.5. Sécurité côté front & tests avec DevTools

Sur la partie front :

- **Aucune clé API ou secret** n’est exposé dans le JavaScript côté client.  
- Toutes les requêtes sensibles passent par le backend Flask, qui est le seul à communiquer avec Bitget.  
- Les endpoints front sont limités à la lecture de données (GET), ce qui réduit la surface d’attaque.

Tests avec DevTools (Chrome) :

- **Onglet Network :**
  - Vérification des requêtes AJAX, des temps de réponse, du statut HTTP  
  - Contrôle que les réponses ne contiennent pas d’informations sensibles

- **Onglet Responsive / Device toolbar :**
  - Simulation de différents formats (mobile / tablette / desktop)  
  - Ajustements CSS en conséquence

- **Onglet Lighthouse / Audits :**
  - Audit performance, bonnes pratiques, accessibilité  
  - Identification de pistes d’amélioration (taille des ressources, attributs manquants, etc.)

---

## 7. Réalisations côté back-end

### 7.1. Stockage des données

Choix actuel : **fichiers CSV/JSONL** au lieu d’une base relationnelle pour des raisons de simplicité et de coûts.  

- CSV pour les séries temporelles (OHLCV)  
- JSONL pour les logs (ordres, événements, health beats…)

Cette organisation reste cohérente avec le référentiel DWWM, car :
- La structuration des données (schémas implicites) est proche d’un modèle relationnel  
- Une migration vers une base SQL (PostgreSQL, MySQL) serait directe (tables OHLCV, orders, events…)  

### 7.2. Composants d’accès aux données

- Fonctions de lecture/écriture CSV (OHLCV)  
- Fonctions de lecture/écriture JSONL pour les journaux  
- Validation des données (timestamp, colonnes complètes, absence de NaN critiques)  

Ces composants jouent le rôle de « couche d’accès aux données » (équivalent DAO/Repository).

### 7.3. Composants métier

Le cœur du projet se trouve dans les composants métier :

- Calcul des indicateurs techniques (MACD, RSI, EMA, Bollinger, ATR, etc.)  
- Logique des stratégies (conditions d’entrée/sortie)  
- Calcul des tailles de position et vérification des limites de risque  
- Construction d’intentions et d’ordres envoyables à l’API Bitget  

Chaque stratégie implémente une interface commune, ce qui facilite la lisibilité et l’évolution.

### 7.4. Sécurité back-end

Principales mesures :

- Gestion des secrets via `.env` (API key, API secret, passphrase)  
- Aucune clé sensible dans le code ou dans Git  
- Utilisation de HTTPS pour les appels API  
- Validation des entrées côté backend (symboles, timeframes connus, bornes de risque)  
- Logging des erreurs et des événements critiques  

### 7.5. Déploiement et exploitation (prévisionnel)

Actuellement, le projet tourne en environnement de développement local.

Évolutions prévues :
- Création d’un `Dockerfile` pour conteneuriser le bot et le dashboard  
- `docker-compose` pour lancer l’ensemble (bot + dashboard + éventuelle BDD)  
- Scripts de démarrage / surveillance (supervision simple, redémarrage en cas de crash)  

---

## 8. Tests et qualité

### 8.1. Stratégie de test

Plusieurs niveaux de tests :

1. **Doctests** dans certaines fonctions (exemples intégrés directement dans les docstrings).  
2. **Backtests** sur données historiques pour valider la logique de stratégies.  
3. **Tests d’intégration** pour vérifier un flux complet (données → signal → ordre).  
4. **Tests manuels** via scripts (`test_api.py`) et utilisation du dashboard.

### 8.2. Jeux d’essai

Exemples de jeux d’essai :

- Dataset artificiel où MACD croise la ligne de signal → vérification de la génération d’un signal LONG.  
- Cas où RSI est en survente et volume supérieur à la moyenne → signal LONG spécifique (RSI Oversold).  
- Cas où le risque quotidien approcherait la limite → les signaux doivent être rejetés.

Ces tests ont permis de valider la cohérence de la logique métier et du risk management.

### 8.3. Qualité du code

Bonnes pratiques mises en place :

- Respect global de PEP8 (nommage, organisation, imports)  
- Type hints présents sur la majorité des fonctions  
- Découpage modulaire (10+ packages)  
- Docstrings explicites pour les fonctions clés  
- README détaillé : installation, configuration, lancement, architecture

Évolutions prévues :
- Ajout de `pytest`  
- Intégration d’un outil de formatage (`black`) et de linting (`flake8` ou `pylint`)  
- Mise en place d’une pipeline CI simple (GitHub Actions)

---

## 9. Veille technologique et sécurité

### 9.1. Veille technologique

Thèmes suivis :
- Trading algorithmique (articles, blogs, communautés Reddit/Discord)  
- APIs de plateformes d’échange (Bitget, Binance, etc.)  
- Outils Python pour la data et le backtesting (pandas, ta-lib, vectorbt…)  
- Bonnes pratiques de développement web (sécurité, performances, accessibilité)  

La veille a directement influencé :
- Le choix de la méthode d’authentification (HMAC)  
- L’idée d’utiliser ATR pour dimensionner les positions  
- La structuration de la couche stratégie / risk / execution

### 9.2. Veille sécurité

- Consultation de ressources OWASP (vulnérabilités web classiques : XSS, CSRF, injections…)  
- Lecture de guides de sécurité liés au stockage des mots de passe / secrets  
- Rappels sur RGPD :  
  - Pas de stockage de données personnelles ici, mais préparation pour un futur mode multi-utilisateur  
  - Idée d’ajouter à terme mentions légales, politique de cookies et de confidentialité si l’outil était ouvert à des tiers  

---

## 10. Bilan et perspectives

### 10.1. Résultats obtenus

Le projet atteint ses objectifs pédagogiques :

- Montre la capacité à développer :
  - Une **partie back-end** non triviale (API externes, logique métier, gestion de risque)  
  - Une **partie front-end** fonctionnelle (dashboard dynamique basé sur une API interne)  
- Respecte la structure attendue pour un projet RNCP DWWM :
  - Front-end sécurisé, dynamique, pensé pour l’utilisateur  
  - Back-end structuré, sécurisé, documenté  
  - Tests, documentation, veille  

### 10.2. Difficultés rencontrées

- Gestion des erreurs de l’API Bitget (timeouts, codes 500, rate limits)  
- Synchronisation des barres (bar close) avec les timestamps des chandeliers  
- Éviter l’overfitting lors des backtests (paramètres trop précis → résultats non réalistes)  
- Trouver un bon compromis entre complexité technique et lisibilité du code pour un jury

### 10.3. Évolutions possibles

- **Front-end :**
  - Refonte en React ou Vue  
  - Graphiques interactifs (évolution du P&L, equity curve, drawdown)  
  - Ajout d’un panneau de configuration (activer/désactiver des stratégies depuis le front)  

- **Back-end :**
  - Migration vers une base de données relationnelle (PostgreSQL)  
  - Ajout d’un module d’IA / machine learning (prise en compte du contexte)  
  - Multi-exchange et multi-utilisateurs  

- **DevOps :**
  - Conteneurisation (Docker)  
  - Déploiement sur un VPS / cloud  
  - Mise en place d’un monitoring plus avancé (Prometheus, Grafana…)  

---

## 11. Annexes

> *Les annexes seront imprimées à part et limitées à 30 pages maximum, conformément aux consignes DWWM (schémas, copies d’écran, extraits de code, etc.).*

### Annexe A : Diagramme d’architecture globale

*(Schéma ASCII ou graphique représentant les différentes couches de l’application : data, stratégies, risk, execution, runtime, ui.)*

### Annexe B : Exemple de schéma CSV OHLCV

*(Extrait de fichier CSV documenté avec description des colonnes.)*

### Annexe C : Extrait de code – Risk management

*(Fonction de calcul de taille de position avec commentaires détaillés.)*

### Annexe D : Captures d’écran du dashboard

- Vue d’ensemble (P&L du jour, nombre de positions, etc.)  
- Liste des positions ouvertes  
- Historique des trades  

### Annexe E : Exemples de jeux d’essai / backtests

- Description d’un cas RSI oversold validé  
- Description d’un cas rejeté par les limites de risque  

### Annexe F : Extrait du README du projet

- Partie installation  
- Partie configuration (`.env`)  
- Partie lancement (`python main.py`, `python ui/dashboard.py`)  

---

**Fin du dossier de projet – Titre professionnel DWWM (RNCP niveau 5)**  

**Candidat :** [Votre Nom]  
**Date de rédaction :** Décembre 2025
