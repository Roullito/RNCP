# Dossier de projet – Titre professionnel DWWM (Niveau 5)
## Projet support : Smart Trading Bot

---

## 0. Informations générales

- **Titre du projet** : Smart Trading Bot – Application web de trading crypto en environnement de démonstration
- **Candidat** : [Prénom NOM]
- **Centre de formation** : Holberton School – Campus Thonon-les-Bains
- **Titre visé** : Développeur Web et Web Mobile (DWWM – Niveau 5)
- **Période de réalisation du projet** : [dates]
- **Contexte** : Projet réalisé dans le cadre de la formation (et Demo Day Holberton)

---

## 1. Compétences DWWM mobilisées (synthèse)

### 1.1. Activités types

- AT1 : Développer la partie front-end d’une application web ou web mobile sécurisée
- AT2 : Développer la partie back-end d’une application web ou web mobile sécurisée

### 1.2. Compétences professionnelles ciblées

- CP1 : Installer et configurer son environnement de travail en fonction du projet web ou web mobile
- CP2 : Maquetter des interfaces utilisateur web ou web mobile
- CP3 : Réaliser des interfaces utilisateur statiques web ou web mobile
- CP4 : Développer la partie dynamique des interfaces utilisateur web ou web mobile
- CP5 : Mettre en place une base de données relationnelle
- CP6 : Développer des composants d’accès aux données SQL et NoSQL
- CP7 : Développer des composants métier côté serveur
- CP8 : Documenter le déploiement d’une application dynamique web ou web mobile

> Une table récap’ viendra à la fin (section 9.2) pour montrer clairement quelles parties du projet prouvent chaque compétence.

---

## 2. Contexte et présentation du projet

### 2.1. Présentation personnelle et de la formation

- Parcours avant Holberton
- Objectifs de reconversion / montée en compétence
- Rôle du projet dans le parcours (RNCP5 + Demo Day)

### 2.2. Contexte du projet “Smart Trading Bot”

- Besoin général : automatiser et sécuriser l’exécution de stratégies de trading sur des actifs crypto
- Environnement : API Bitget en mode demo, application web interne (non publique)
- Positionnement : outil d’aide à la décision + automatisation partielle

### 2.3. Objectifs du projet

- Objectifs techniques (collecte de données, stratégies, exécution des ordres, interface web…)
- Objectifs pédagogiques (couverture CP1–CP8 du DWWM)
- Contraintes générales (sécurité, gestion des erreurs, performance raisonnable, lisibilité du code…)

---

## 3. Expression des besoins

### 3.1. Besoins “métier”

- Pouvoir tester différentes stratégies (MACD, RSI, DCA…) sur données historiques
- Suivre en temps réel ou quasi temps réel les signaux de marché
- Visualiser l’historique des trades et la performance globale (PnL)

### 3.2. Besoins utilisateurs

- Interface web simple pour :
  - Choisir l’actif (BTC, ETH, etc.)
  - Activer / désactiver une stratégie
  - Consulter les backtests et les résultats en cours
- Retour d’information clair en cas d’erreur (API, réseau, validation)

### 3.3. Périmètre fonctionnel retenu

- Ce qui est inclus (MVP)
- Ce qui est exclu ou différé (v2, fonctionnalités IA, multi-utilisateurs avancé, etc.)

### 3.4. Contraintes

- Techniques (langages, API Bitget, BDD, hébergement)
- Sécurité (gestion des clés API, validation des entrées, logs, RGPD si applicable)
- Accessibilité / UX de base (lisibilité, responsive dashboard)

---

## 4. Environnement de travail (CP1)

### 4.1. Environnement matériel et logiciel

- OS, IDE (VSCode), navigateurs utilisés
- Stack front (HTML/CSS/JS ou framework choisi)
- Stack back (Python, framework web éventuel, librairies, BDD)

### 4.2. Gestion de version et collaboration

- Utilisation de Git et GitHub
- Organisation du dépôt (branches, conventions de commit, pull requests si applicable)

### 4.3. Conteneurs et services

- Services nécessaires (BDD, API externes, éventuelle containerisation pour le dev)
- Justification des choix

### 4.4. Veille liée à l’environnement de travail

- Outils surveillés (nouvelles versions, failles de sécurité, guidelines)
- Impact sur le projet (mise à jour, bonnes pratiques adoptées)

---

## 5. Réalisations front-end (AT1 : CP2, CP3, CP4)

### 5.1. Maquettage des interfaces (CP2)

- Outil de maquettage utilisé (Figma, papier, autre)
- Maquettes principales :
  - Écran d’accueil / sélection des actifs
  - Dashboard de stratégie (signaux, statut, PnL)
  - Vue historique des trades
- Schéma d’enchaînement des écrans

### 5.2. Interfaces statiques (CP3)

- Structuration HTML des pages
- Mise en forme CSS
- Approche responsive (desktop / mobile)
- Prise en compte de l’accessibilité de base

### 5.3. Interfaces dynamiques (CP4)

- Logique côté client : appels à l’API back-end, mise à jour dynamique des vues
- Gestion des formulaires / saisies utilisateurs
- Gestion des états (chargement, erreur, succès, etc.)

### 5.4. Sécurité, tests et qualité côté front

- Validation des entrées côté client (en complément du back)
- Prise en compte des risques simples (XSS, exposition d’infos sensibles)
- Jeu d’essai et scénarios de tests front
- Outils éventuels de qualité / linting

---

## 6. Réalisations back-end (AT2 : CP5, CP6, CP7)

### 6.1. Modélisation et mise en place de la base de données (CP5)

- Schéma conceptuel des données (actifs, bougies OHLCV, trades, stratégies, logs…)
- Schéma physique (tables, clés primaires/étrangères, contraintes)
- Mise en place de la base de tests + jeux d’essai

### 6.2. Composants d’accès aux données (CP6)

- Accès aux données (lecture / écriture OHLCV, trades, paramètres de stratégie)
- Gestion des erreurs, des conflits d’accès éventuels
- Vérification et validation des entrées avant écriture en base
- Tests unitaires et tests orientés sécurité sur ces composants

### 6.3. Composants métier côté serveur (CP7)

- Description des principales stratégies implémentées (ex : MACD Cross, DCA…)
- Architecture logicielle (couches, modules, classes)
- Gestion des signaux : génération, filtrage, envoi vers le module d’exécution
- Approche défensive (gestion d’erreurs, cas limites)

### 6.4. Communication avec l’API Bitget

- Description des endpoints utilisés (données de marché, ordres, etc.)
- Gestion des clés API (stockage, utilisation, sécurité)
- Politique de gestion des erreurs et des timeouts

### 6.5. Sécurité serveur

- Contrôles des entrées
- Logs de sécurité
- Points de vigilance identifiés (et mesures prises)

### 6.6. Jeux d’essai, tests unitaires et résolution de problèmes

- Jeux d’essai représentatifs pour une ou plusieurs fonctionnalités critiques
- Stratégie de tests (unitaires, intégration, manuels)
- Exemple concret de bug / dysfonctionnement et méthode de résolution

---

## 7. Déploiement et documentation (CP8)

### 7.1. Procédure de déploiement

- Environnement cible (dev / test / démonstration)
- Pré-requis (dépendances, variables d’environnement, services externes)
- Étapes détaillées pour déployer l’application (back + front)

### 7.2. Scripts et automatisation

- Scripts de lancement / déploiement existants
- Pistes d’amélioration vers CI/CD (intégration / déploiement continus)

### 7.3. Veille liée au déploiement / DevOps

- Bonnes pratiques identifiées (sécurité, résilience, etc.)
- Impact potentiel sur le projet

---

## 8. Veille technologique et sécurité

### 8.1. Organisation de la veille

- Thèmes suivis : sécurité Web, API, crypto, RGPD, etc.
- Sources (ANSSI, OWASP, CNIL, docs Bitget, etc.)

### 8.2. Vulnérabilités et bonnes pratiques identifiées

- Vulnérabilités typiques pour ce type de projet (XSS, injections, fuites de clé API…)
- Contre-mesures mises en place dans le projet

### 8.3. Impact concret sur Smart Trading Bot

- Décisions techniques influencées par la veille
- Exemples de corrections ou d’améliorations de sécurité

---

## 9. Bilan et perspectives

### 9.1. Bilan personnel et technique

- Compétences acquises / renforcées
- Difficultés rencontrées et solutions apportées
- Ce que tu referais différemment

### 9.2. Tableau de synthèse CP1 → CP8

> Tableau à compléter avec pour chaque compétence :
> - Description courte
> - Partie du projet qui la démontre (chapitre / fonctionnalité)
> - Éventuelles annexes associées

### 9.3. Évolutions possibles du projet

- Améliorations techniques envisagées
- Ouverture vers l’IA / ML pour la prise de décision
- Évolutions possibles de l’interface utilisateur

---

## Annexes (max. 30 pages)

- A1. Maquettes complètes du dashboard
- A2. Schémas BDD (conceptuel + physique)
- A3. Extraits de code représentatifs (front + back)
- A4. Jeux d’essai détaillés (jeu de tests sur une fonctionnalité clé)
- A5. Captures d’écran de l’application en fonctionnement
- A6. Exemples de résultats de backtests / journaux d’exécution
