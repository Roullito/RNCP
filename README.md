# RNCP5 – Préparation & Plan Global

**Titre du projet RNCP :** Smart Trading Bot – Plateforme de trading crypto automatisé (RNCP 5 – DWWM)

Ce README centralise **toute ta préparation RNCP5** autour de ton projet de bot de trading :

- Rappel des **livrables officiels** (dossier de projet, dossier professionnel, support, etc.).
- Synthèse des **modules de préparation** (frontend, backend, sécurité, RGPD, tests, entretien, questionnaire…).
- **Plan de construction** de ton dossier RNCP pour le bot de trading.
- Roadmap / to‑do list pour organiser ton travail jusqu’au jour J.

> ⚠️ Références officielles à garder en tête (toujours prioritaires) :
> - **REV2 DWWM** (Référentiel d’évaluation RNCP 5 DWWM)
> - **REAC DWWM** (Référentiel Emploi Activités Compétences)
> - Guides Holberton : dossier projet, dossier pro, support de présentation, questionnaire pro, entretien final.

---

## 1. Vue d’ensemble du passage RNCP 5 (DWWM)

Pour ton titre **DWWM – Développeur Web et Web Mobile (niveau 5)**, tu dois préparer plusieurs éléments en amont de la session :

1. **Dossier de projet** (ton rapport technique principal)
2. **Support de présentation orale** (diaporama)
3. **Dossier professionnel (DP)**
4. Participation aux épreuves :
   - **Questionnaire professionnel** (QCM + questions ouvertes)
   - **Présentation de projet + entretien technique**
   - **Entretien final**

### 1.1. Livrables et deadlines (à adapter avec ton campus)

- **Dossier de projet terminé** → à envoyer à l’équipe campus **au plus tard J‑15**.
- **Support de présentation** → à envoyer **au plus tard J‑7** pour relecture.
- **Dossier professionnel + livret d’évaluation signé** → généralement **entre J‑7 et J‑1** (à confirmer avec ton staff).

Garde ces dates visibles dans ton planning (Notion, Trello, tableau blanc…).

---

## 2. Synthèse des modules de préparation RNCP

Cette section résume les concepts clés vus dans les modules RNCP, pour que tu puisses justifier tes choix le jour J.

### 2.1. Préparation non‑technique

- **Méthodologie de la rédaction du projet**
  - Dossier de projet RNCP 5 : **entre 30 et 50 pages** (hors page de garde, sommaire, annexes).
  - Plan aligné sur le **REV2 DWWM** : liste des compétences, contexte, expression des besoins, environnement technique/humain, réalisations, sécurité, tests, veille.
- **Dossier Professionnel (DP)**
  - Document centré sur **ton parcours** et **tes expériences**, pas seulement ton projet RNCP.
  - Au moins **un exemple par activité type** du titre (front + back).
- **Support de présentation orale**
  - Diaporama pour présenter **le projet** pendant ~35 minutes.
  - Pas de “note de synthèse” ni d’intro en anglais : remplacé par le **questionnaire professionnel**.
- **Questionnaire professionnel**
  - Test écrit (sans Internet) : QCM + questions ouvertes (FR & EN).
  - Porte sur des notions théoriques (web, réseaux, sécurité, outils, environnement technique…).
- **Entretien final**
  - 15–20 min, non technique, centré sur :
    - ta vision du **métier de développeur**,
    - ta compréhension des **blocs RNCP**,
    - ta **culture pro**, ton projet professionnel, ta capacité à te situer dans le métier.

---

### 2.2. Frontend – Maquettage & Design responsive

- **Maquettage / wireframes / mockups**
  - Savoir expliquer : pourquoi tu as maquetté, avec quels outils (Figma, Miro…), quelles versions (mobile, desktop).
  - Être capable de montrer un **parcours utilisateur** simple (dashboard, écran de stratégie, détail d’un trade, etc.).

- **Design responsive**
  - Comprendre et expliquer l’usage de :
    - **Flexbox**, **CSS Grid**, **media queries**.
  - Démontrer que ton interface de bot de trading s’adapte au moins à **mobile + desktop**.

---

### 2.3. Frontend – SEO (Référencement)

Même si ton bot de trading n’est pas un blog public, tu dois comprendre :

- Ce qu’est le **SEO** (Search Engine Optimization).
- Pourquoi c’est utile (visibilité, trafic organique, compréhension par les moteurs de recherche).
- Quelques bonnes pratiques :
  - Balises `<title>`, `<meta description>`, `<h1>…<h6>`.
  - URLs propres, textes alternatifs (`alt`) pour les images.
  - Performances, temps de chargement, responsive (impact sur le SEO).

Tu peux dire que tu as **intégré les bases du SEO**, ou que ton projet pourrait être **étendu** avec une partie publique optimisée SEO (landing page du bot, documentation, etc.).

---

### 2.4. Frontend – Accessibilité

Tu dois savoir parler de :

- **Accessibilité web** : rendre le site utilisable par le plus grand nombre (y compris handicap visuel, moteur, cognitif…).
- Rôles de :
  - **W3C**, **WAI**, **WCAG**, **RGAA**, **ARIA**.
- Exemples concrets que tu peux citer pour ton projet :
  - Contraste suffisant texte/fond.
  - Texte alternatif sur les icônes importantes.
  - Navigation clavier possible sur les boutons critiques (sauver une stratégie, lancer/arrêter le bot…).
  - Structure sémantique (`<main>`, `<nav>`, `<section>`, etc.).

---

### 2.5. Frontend – Tests (DevTools)

On attend de toi que tu saches **tester ton frontend avec les DevTools** (Chrome ou autre) :

- Inspecter HTML/CSS, modifier le DOM à la volée.
- Debugger le CSS, vérifier les marges, alignements, z‑index.
- Tester le **responsive** avec les modes “mobile/tablette/desktop”.
- Profiler les performances (onglets Performance, Network) si nécessaire.
- Utiliser l’onglet “Lighthouse” / “Audit” pour voir :
  - performances,
  - accessibilité,
  - bonnes pratiques.

Dans ton rapport et ton support, tu pourras ajouter **quelques captures** de DevTools comme preuve de tests frontend.

---

### 2.6. RGPD & CNIL

Tu dois être capable de répondre à des questions comme :

- Qu’est‑ce que le **RGPD** ?
- Qu’est‑ce que la **CNIL** ?
- Comment rendre une application plus **conforme au RGPD** ?

Pour ton bot de trading, tu peux évoquer :

- Limitation des données collectées (principe de minimisation).
- Information claire de l’utilisateur sur les données utilisées (logs de trades, API keys chiffrées, etc.).
- Sécurisation des données sensibles (hash/chiffrement, séparation des secrets, rotation des clés…).
- Droits des utilisateurs (accès, rectification, suppression du compte).

---

### 2.7. Backend – Sécurité, Infrastructure & tests

Points clés à maîtriser pour l’oral et le rapport :

- **Architecture**
  - Monolithe structuré (séparations `data/`, `strategies/`, `trading/`, `ui/`, etc.).
  - Compréhension du modèle **MVC** et de la séparation responsabilités.

- **Sécurité**
  - Injections SQL, XSS, CSRF (même si ton app est surtout backend/API, tu dois connaître ces failles).
  - **Hashing vs chiffrement** des mots de passe / API keys.
  - HTTPS, certificats SSL/TLS.
  - Principe de moindre privilège (PoLP) : droits minimums en BDD, sur le système, dans les rôles utilisateur.

- **Tests backend**
  - Tests unitaires (sur fonctions critiques : calcul de signaux, gestion du risque, ordres de trading…).
  - Tests d’intégration (API + base de données + exchange mocké).
  - Tests manuels (Postman, curl, scripts Python).

Tu dois prévoir dans ton dossier projet un **jeu d’essai représentatif** :

- Données en entrée (ex : série de bougies OHLCV).
- Résultat attendu (ex : signal “BUY” ou “SELL”, ordre simulé, logs).
- Résultat obtenu + analyse des écarts.

---

## 3. Plan pour construire ton RNCP autour du bot de trading

### 3.1. Dossier de projet (Rapport principal)

Ton dossier de projet RNCP 5 devra suivre, pour un projet réalisé en formation, le plan officiel suivant :

1. **Liste des compétences mises en œuvre** (front + back + transversales)
2. **Expression des besoins** du projet
3. **Environnement technique**
4. **Réalisations** permettant la mise en œuvre des compétences

👉 Pour rendre ça plus complet et lisible, on va utiliser un **plan enrichi** dans le fichier dédié `RNCP_Dossier_Projet_Smart_Trading_Bot.md` (cf. fichier séparé). Celui‑ci sera organisé grosso modo en :

- Présentation du projet & contexte
- Liste des compétences RNCP couvertes
- Expression des besoins & périmètre
- Environnement humain & technique
- Conception & architecture (maquettes, ERD, architecture applicative)
- Réalisations front‑end
- Réalisations back‑end
- Tests & qualité
- Sécurité & RGPD
- Veille technologique & sécurité
- Bilan et perspectives

Tu pourras **l’étoffer progressivement** jusqu’à atteindre les 30–50 pages.

---

### 3.2. Dossier Professionnel (DP)

Pour le DP, l’idée est de montrer **comment ton parcours et tes expériences** valident les **compétences du titre**.

Plan possible (basé sur les templates officiels) :

1. **Présentation du candidat**
2. **Parcours de formation et expériences professionnelles**
3. **Activité type 1 – Frontend**
   - Exemple 1 : projet RNCP (UI bot de trading)
   - Exemple 2 : autre projet Holberton (portfolio, HBnB web, etc.)
4. **Activité type 2 – Backend**
   - Exemple 1 : Smart Trading Bot (API, BDD, stratégies, sécurité)
   - Exemple 2 : autre projet (API Flask/Django, projet SQL, etc.)
5. **Compétences transversales** (communication, autonomie, veille, etc.)
6. **Projet professionnel**
7. **Déclaration sur l’honneur**

Ce README te sert de **checklist** : à chaque fois que tu avances sur ton dossier projet, pense à quels exemples ajouter aussi au DP.

---

### 3.3. Support de présentation (diaporama)

Ton support devra suivre l’esprit du REV2 :

- **Introduction rapide**
  - Qui tu es, contexte de la formation, titre visé.

- **Expression des besoins & périmètre**
  - Pourquoi un bot de trading ?
  - Pour qui ? (persona utilisateur)
  - Objectifs et limites du projet.

- **Environnement technique**
  - Stack (Python, API Bitget, BDD, front éventuel, outils).

- **Réalisation frontend**
  - 1–2 maquettes, schéma de navigation.
  - captures d’écran + points sur la sécurité + responsive + accessibilité.

- **Réalisation backend**
  - Schéma BDD, extraits de code métier et d’accès aux données.
  - Explication de la logique de trading.
  - Sécurité (hash, encrypt, gestion des clés API, validation des entrées).

- **Tests & veille**
  - Jeu d’essai, tests unitaires/intégration.
  - Veille sécurité (bots de trading, API crypto, vulnérabilités web).

- **Conclusion**
  - Difficultés, réussites, améliorations futures.

Ce plan détaillé sera rédigé dans un fichier séparé (`RNCP_Support_Presentation_Smart_Trading_Bot.md`) si tu veux plus tard.

---

### 3.4. Questionnaire pro & entretiens

- **Questionnaire professionnel**
  - Réviser : fondamentaux web, Git, API, HTTP, sécurité, RGPD, outils type GitHub, Linux, Node/Python selon ton parcours.
  - T’entraîner sur des mini‑QCM maison.

- **Entretien technique**
  - Être capable de **naviguer dans ton code** (repo GitHub) en live.
  - Expliquer clairement tes choix techniques (ex : pourquoi tel design de stratégie, telle BDD, telle lib Python, etc.).
  - Montrer comment tu testes (front + back).

- **Entretien final**
  - Préparer 2–3 réponses solides sur :
    - ta vision du métier de développeur,
    - ton projet pro (court/moyen terme),
    - ton positionnement sur la sécurité, le RGPD, la qualité.
  - Faire 1 ou 2 **mock interviews** avec des collègues.

---

## 4. Roadmap RNCP – Smart Trading Bot

Tu peux utiliser cette checklist comme guide pratique.

### 4.1. Étape 1 – Cadrage du projet

- [ ] Valider le **titre du projet** et le pitch (3–5 lignes).
- [ ] Rédiger une **expression des besoins** claire (contexte, objectifs, limites).
- [ ] Définir les **utilisateurs cibles** et leurs besoins.

### 4.2. Étape 2 – Alignement RNCP (compétences)

- [ ] Relire le **REAC DWWM** et identifier les compétences front + back.
- [ ] Lister dans un tableau **compétence → section du projet** où elle est couverte.
- [ ] Commencer à remplir la section « liste des compétences mises en œuvre » dans le dossier projet.

### 4.3. Étape 3 – Conception & architecture

- [ ] Finaliser ou clarifier l’**architecture globale** du bot (dossiers, modules, flux de données).
- [ ] Formaliser un **schéma BDD** (ERD) propre.
- [ ] Produire 2–4 **maquettes UI** (si UI web) + parcours utilisateur.

### 4.4. Étape 4 – Documentation technique

- [ ] Documenter les principales **stratégies de trading** (MACD, RSI, etc.).
- [ ] Documenter les **flux de données** (Bitget → ingestion → stockage → stratégie → ordre → logs).
- [ ] Documenter la **gestion des erreurs**, des timeouts API, des cas limite.

### 4.5. Étape 5 – Rédaction du dossier de projet

- [ ] Créer `RNCP_Dossier_Projet_Smart_Trading_Bot.md` (base fournie dans ce repo).
- [ ] Remplir progressivement chaque section à partir du code et des notes.
- [ ] Ajouter des **captures d’écran**, schémas, extraits de code significatifs.
- [ ] Vérifier la cohérence avec le **plan officiel REV2**.

### 4.6. Étape 6 – Dossier professionnel

- [ ] Récupérer le **template officiel DP DWWM**.
- [ ] Choisir 1–2 **expériences ou projets** par bloc RNCP.
- [ ] Rédiger les descriptions (contexte, missions, résultats, compétences mobilisées).

### 4.7. Étape 7 – Support de présentation

- [ ] Construire la **trame des slides**.
- [ ] Ajouter screenshots, schémas, extraits de code clé.
- [ ] Chronométrer une présentation complète (~35 min).

### 4.8. Étape 8 – Entraînements finaux

- [ ] Simuler la **présentation + entretien technique** avec un collègue.
- [ ] Simuler l’**entretien final** (20 min, questions non techniques).
- [ ] Préparer un mini mémo papier (ou mental) avec :
  - 3 points forts du projet,
  - 3 difficultés majeures,
  - 3 axes d’amélioration,
  - ton projet pro.

---

## 5. Organisation des fichiers dans ton repo

Suggestion d’arborescence pour ton dépôt RNCP / trading bot :

```text
.
├── README.md                              # Ce fichier
├── RNCP_Dossier_Projet_Smart_Trading_Bot.md
├── RNCP_Dossier_Professionnel_notes.md    # (facultatif, brouillon DP)
├── RNCP_Support_Presentation_notes.md     # (facultatif, plan des slides)
├── docs/
│   ├── maquettes/
│   ├── diagrammes/
│   ├── jeux_de_test/
│   └── captures_ecran/
└── src/                                   # Code du bot de trading
    ├── data/
    ├── indicators/
    ├── strategies/
    ├── trading/
    ├── api_client/
    └── ui/
```

Tu pourras bien sûr adapter cette structure à ton repo existant.

---

## 6. Conclusion

Ce README est ton **hub RNCP** :

- Il résume les **attendus officiels**.
- Il te donne un **plan concret** pour transformer ton bot de trading en **dossier RNCP conforme**.
- Il sert de **checklist vivante** pendant toute la préparation.

Le fichier séparé `RNCP_Dossier_Projet_Smart_Trading_Bot.md` sera ton **rapport technique** principal, que tu enrichiras jusqu’à atteindre le niveau attendu (30–50 pages avec schémas, extraits de code, captures…).

Garde ce repo propre, versionné, et pense à l’image qu’il donnera au jury (et à de futurs recruteurs).
