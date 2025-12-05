## Module 2 – Méthodologie de la rédaction du projet

### 2.1. Rappels officiels (DWWM – REV / REAC)

- Titre : **DWWM – Développeur Web et Web Mobile (RNCP 5)**  
- Dossier de projet (titre complet) :  
  - **30 à 50 pages** hors page de garde, sommaire et annexes  
  - **Annexes : 30 pages max**  
- Un **seul dossier de projet** pour l’ensemble des projets  
- Un **seul support de présentation (diaporama)** pour l’ensemble des projets   

Pour les **projets réalisés pendant la formation**, le **plan officiel du dossier** est :   

1. **Liste des compétences mises en œuvre** dans le cadre du projet  
2. **Expression des besoins** du projet (objectifs + limites)  
3. **Environnement technique**  
4. **Réalisations** permettant la mise en œuvre des compétences

---

### 2.2. Logique de rédaction (vue simple)

L’idée du dossier, c’est de montrer au jury que tu sais :

1. **Quelles compétences DWWM** tu mobilises (front + back).  
2. **Quel besoin réel tu adresses** (cahier des charges / expression des besoins).  
3. **Avec quels outils et quelle architecture** tu travailles (environnement technique).  
4. **Ce que tu as réellement réalisé**, avec des preuves (maquettes, schémas, code, tests, veille, sécurité…).

---

### 2.3. Application à mon projet principal – « Smart Trading Bot »

Mon projet support principal pour le RNCP5 est :

> **Smart Trading Bot – Application web de pilotage et de suivi de stratégies de trading crypto (API Bitget, mode démo)**

Il servira à démontrer notamment :

- **Back-end** :  
  - Base de données (OHLCV, trades, stratégies, logs)  
  - Composants d’accès aux données  
  - Composants métier (indicateurs, stratégies, moteur de trading)   
- **Front-end** via un **dashboard web** :  
  - Interfaces pour choisir les actifs et stratégies  
  - Affichage des résultats (trades, PnL, backtests)  
  - Interaction avec le back-end (API)

---

### 2.4. Squelette du chapitre « Smart Trading Bot » dans le dossier

> Ce squelette respecte le plan officiel pour les projets réalisés en formation.   

#### 2.4.1. Liste des compétences mises en œuvre

- CP1 – Installer et configurer son environnement de travail  
- CP2 – Maquetter des interfaces utilisateur web ou web mobile  
- CP3 – Réaliser des interfaces utilisateur statiques web ou web mobile  
- CP4 – Développer la partie dynamique des interfaces utilisateur web ou web mobile  
- CP5 – Mettre en place une base de données relationnelle  
- CP6 – Développer des composants d’accès aux données SQL et NoSQL  
- CP7 – Développer des composants métier côté serveur  
- CP8 – Documenter le déploiement d’une application dynamique web ou web mobile   

*(Plus tard, une table de synthèse liera chaque compétence à une partie précise du projet.)*

#### 2.4.2. Expression des besoins du projet

- **Contexte**  
  - Besoin d’un outil pour automatiser / tester des stratégies de trading crypto en environnement sécurisé (démo).  
- **Objectifs**  
  - Collecter des données de marché (OHLCV)  
  - Calculer des indicateurs techniques (RSI, MACD, etc.)  
  - Lancer des backtests  
  - Exécuter les signaux en mode démo  
  - Offrir une interface web simple de pilotage et de visualisation  
- **Périmètre fonctionnel**  
  - Ce que le projet fait réellement (**MVP**)  
  - Ce qui est hors-périmètre (gestion multi-utilisateurs avancée, IA temps réel, trading réel, etc.)  
- **Contraintes**  
  - Techniques : API Bitget, gestion des clés, volumétrie des données, perf raisonnable  
  - Sécurité : protection des clés API, validation des entrées/sorties, gestion des erreurs  
  - Organisationnelles : temps, niveau attendu DWWM, contraintes du centre de formation

#### 2.4.3. Environnement technique

- **Front-end**  
  - Technologies : HTML, CSS, JavaScript (ou framework choisi)  
  - Outils de maquettage : Figma / autre  
- **Back-end**  
  - Langage : Python  
  - Librairies principales : gestion HTTP, indicateurs techniques, etc.  
  - Structuration en modules : data, strategies, trading, API…  
- **Données & stockage**  
  - Type de base (SQL/NoSQL ou fichiers structurés)  
  - Schéma global (tables ou structures pour OHLCV, trades, stratégies, logs)  
- **Outils projet**  
  - Git / GitHub  
  - Virtualenv / gestion de dépendances  
  - Éventuelle containerisation (Docker) pour le dev

#### 2.4.4. Réalisations permettant la mise en œuvre des compétences

- **Front-end** (CP2–CP4)  
  - Maquettes du dashboard (sélection d’actif, vue PnL, historique des trades)  
  - Pages HTML/CSS (interfaces principales)  
  - Logique JS pour consommer l’API et mettre à jour l’UI  
- **Back-end** (CP5–CP7)  
  - Schéma de la base de données (conceptuel + physique)  
  - Composants d’accès aux données (lecture/écriture OHLCV, trades, etc.)  
  - Composants métier (calcul d’indicateurs, génération de signaux, exécution des stratégies)  
- **Sécurité & qualité**  
  - Gestion des clés API (non commitées, variables d’environnement, etc.)  
  - Validation des entrées / sorties, gestion des erreurs  
  - Logs d’exécution  
- **Tests & jeux d’essai**  
  - Jeu d’essai pour une fonctionnalité représentative (par exemple : exécution d’une stratégie MACD sur une période donnée)  
  - Données en entrée / attendues / obtenues + analyse des écarts   
- **Veille technique & sécurité**  
  - Thèmes : sécurité des API, trading, vulnérabilités web / back-end  
  - Décisions techniques prises suite à cette veille

---

### 2.5. Lien avec la présentation orale

Pour les projets réalisés en formation, la **présentation orale** suit le même triptyque que le dossier :   

1. **Expression des besoins**  
2. **Environnement technique**  
3. **Réalisations permettant la mise en œuvre des compétences**

> Le chapitre “Smart Trading Bot” tel qu’il est structuré ci-dessus servira de base directe au **support de présentation (slides)** du jury.
