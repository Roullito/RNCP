
# RNCP Preparation – Backend – Sécurité, Infrastructure & Tests (RNCP5)

## 1. Rôle de ce module dans la préparation RNCP

Ce module fait partie de la préparation **Backend** pour le titre **DWWM (RNCP 5)**.

Objectifs côté jury :

- Vérifier que tu as **conscience des enjeux de sécurité** dans une application web.
- Voir si tu connais **les principales failles** (au moins : SQLi, XSS, CSRF).
- Comprendre si tu es capable de **protéger ton application** :
  - hashage des mots de passe,
  - chiffrement,
  - gestion des secrets,
  - HTTPS, principe de moindre privilège…
- T’entendre expliquer **l’architecture** de ton appli (monolithe, couches, MVC…).
- Te voir décrire **comment tu as testé ton backend / API** (Postman, jeux de tests, etc.).

Ce qu’on attend de toi :

> Pas d’être expert en cybersécurité, mais d’être un **développeur responsable** qui connaît les bases, sait les expliquer, et a mis en place des mesures simples dans son projet.

---

## 2. Architectures d’application web

### 2.1. Application monolithique

**Définition :**

Une **application monolithe** regroupe dans un même bloc applicatif :

- le **frontend** (templates / vues / endpoints JSON),
- la **logique métier** (services, règles métier),
- l’accès aux **données** (DAO, ORM),
- souvent un seul déploiement (un serveur / conteneur).

C’est **naturel** pour un projet RNCP :

- un backend (API + logique métier),
- une BDD,
- un front (ou une SPA qui consomme ton API),
- tout dans un même repo / application.

Phrase à ressortir :

> « Mon projet est une application monolithique : le frontend, la logique métier et l’accès à la base de données sont regroupés dans la même application. »

---

### 2.2. Architecture en couches (multi-couches)

On découpe l’appli en **couches** (layers) ayant chacune une responsabilité :

1. **Couche présentation**  
   - Vue : HTML, JSON, API REST, templates…
2. **Couche logique métier**  
   - Calculs, règles métier, validations, stratégie…
3. **Couche d’accès aux données**  
   - Requêtes SQL, ORM, Repositories…
4. **Couche base de données**  
   - MySQL, PostgreSQL, etc.

Bénéfices :

- Code plus **lisible** et **maintenable**.
- Tests plus faciles (tu peux tester une couche sans les autres).
- Possibilité d’évoluer vers des architectures plus complexes plus tard.

---

### 2.3. Modèle MVC (Model – View – Controller)

**MVC** = **M**odel – **V**iew – **C**ontroller.

- **Model**  
  Représentation des données + logique associée.  
  Ex : classes `User`, `Trade`, `Strategy` reliées à la BDD.

- **View**  
  Ce que l’utilisateur reçoit :
  - HTML,
  - JSON renvoyé par ton API,
  - templates.

- **Controller**  
  Point d’entrée :
  - reçoit la requête HTTP,
  - appelle la logique métier / le modèle,
  - renvoie la réponse (View).

Même si ton framework ne s’appelle pas “MVC”, tu peux souvent faire la correspondance.

Phrase à ressortir :

> « Dans mon projet, les modèles représentent les entités de base de données, les contrôleurs gèrent les routes / endpoints, et les réponses JSON ou templates jouent le rôle de vues. »

---

### 2.4. Microservices (culture générale)

**Architecture microservices** :

- L’appli est découpée en **petits services indépendants** :
  - service “users”,
  - service “orders”,
  - service “billing”, etc.
- Chaque service :
  - a son propre code,
  - peut avoir sa propre BDD,
  - communique par API ou messages.

Pour un RNCP5 :

- Tu ne dois pas les implémenter,
- Mais tu peux expliquer que **ton projet est volontairement monolithique** pour rester simple, adapté à un projet perso.

---

## 3. Bases de la sécurité backend

### 3.1. Principes généraux

Quelques notions classiques :

- **CIA** (Confidentialité, Intégrité, Disponibilité) :
  - **Confidentialité** : seules les personnes autorisées peuvent voir les données.
  - **Intégrité** : les données ne sont pas modifiées de manière illégitime.
  - **Disponibilité** : l’application est accessible quand on en a besoin.

- **Defense in depth** (Défense en profondeur) :
  - on multiplie les couches de protection :
    - code sécurisé,
    - BDD bien configurée,
    - serveur sécurisé,
    - réseau filtré, etc.

- **PoLP (Principle of Least Privilege)** – Principe de moindre privilège :
  - chaque compte / service / process a **le minimum de droits nécessaires**, pas plus.

---

## 4. Hashing vs Chiffrement (Encryption)

### 4.1. Hashing (hachage)

- Fonction qui prend une donnée (ex : mot de passe) → renvoie une **empreinte** (hash) de taille fixe.
- **Non réversible** (en pratique) : on ne doit pas retrouver le mot de passe à partir du hash.
- Utilisé pour :
  - stocker les **mots de passe**,
  - vérifier l’**intégrité** de données (checksums).

Caractéristiques :

- Même entrée → même hash.
- Un petit changement → hash totalement différent.

Bonnes pratiques :

- Ne jamais stocker les mots de passe en clair.
- Utiliser des algorithmes adaptés aux mots de passe :
  - `bcrypt`, `argon2`, `PBKDF2`…

> À l’oral :  
> « Hashing is one-way and used to store passwords securely. We don’t decrypt a hash, we compare hashes. »

---

### 4.2. Chiffrement (encryption)

- Transforme une donnée lisible (**plaintext**) en donnée illisible (**ciphertext**).
- **Réversible** : on peut récupérer la donnée d’origine avec une **clé**.
- Utilisé pour :
  - protéger des données qu’on doit relire :
    - numéros de carte, données sensibles…
  - sécuriser les communications :
    - HTTPS (TLS).

Types :

- Chiffrement **symétrique** : même clé pour chiffrer/déchiffrer.
- Chiffrement **asymétrique** : clé publique / clé privée.

> À l’oral :  
> « Encryption is reversible with a key. It’s used when we need to read the data again, for example in HTTPS. »

---

### 4.3. Différence à retenir

- **Hashage** : irréversible → idéal pour mot de passe.
- **Chiffrement** : réversible → idéal pour données à relire et pour les communications (HTTPS, etc.).

---

## 5. Principales failles de sécurité à connaître

### 5.1. Injection SQL (SQLi)

**Principe :**

- Construire une requête SQL en concaténant directement des **données utilisateur** → l’utilisateur peut injecter du SQL.

Exemple vulnérable :

```sql
"SELECT * FROM users WHERE email = '" + user_input + "';"
```

**Risques :**

- Lire des données sensibles,
- Modifier / supprimer des données,
- Contrôler tout ou partie de la BDD.

**Protection :**

- Utiliser des **requêtes paramétrées** (prepared statements),
- Utiliser un **ORM** correctement (pas de concat sauvage),
- Valider / filtrer les entrées utilisateur,
- Appliquer le **PoLP** au compte BDD (pas de droits `DROP TABLE` inutiles).

---

### 5.2. XSS (Cross-Site Scripting)

**Principe :**

- Injection de **JavaScript malveillant** dans une page web,
- Le script s’exécute dans le navigateur de la victime, comme si ça venait du site.

Exemples :

- Rendre du HTML provenant de l’utilisateur sans échappement.
- Utiliser `innerHTML` avec des données non filtrées.

**Risques :**

- Vol de cookies / tokens,
- Défacement visuel,
- Redirections malveillantes,
- Exécution d’actions au nom de l’utilisateur.

**Protection :**

- **Échapper** systématiquement les données utilisateur affichées (HTML-escape),
- Éviter `innerHTML` si possible,
- Filtrer / nettoyer les entrées,
- Mettre en place une **Content Security Policy (CSP)** si possible.

---

### 5.3. CSRF (Cross-Site Request Forgery)

**Principe :**

- Forcer un utilisateur déjà **authentifié** à faire une requête involontaire vers le site où il est connecté (grâce aux cookies de session).

Exemple :

- L’utilisateur est connecté à ton app,
- Il visite un site malveillant contenant un formulaire caché qui envoie un `POST` vers ton site pour changer son mot de passe ou lancer une action sensible,
- Son navigateur envoie automatiquement les **cookies** → l’action est exécutée comme si l’utilisateur l’avait voulue.

**Risques :**

- Modification de données,
- Actions sensibles déclenchées sans consentement.

**Protection :**

- **Jetons CSRF** :
  - token unique dans les formulaires / requêtes sensibles,
  - vérifié côté serveur.
- Cookies avec attribut `SameSite`,
- Confirmation supplémentaire pour les actions critiques (MFA, re-authentication, etc.).

---

## 6. Autres notions de sécurité importantes

### 6.1. HTTPS, SSL / TLS

- **HTTP** : données en clair sur le réseau.
- **HTTPS** : HTTP + **TLS** → données chiffrées en transit.

**TLS (anciennement SSL)** :

- Utilise des certificats (PKI),
- Garantit :
  - **Confidentialité** : personne ne lit les échanges,
  - **Intégrité** : les données ne sont pas altérées,
  - **Authenticité** : le client sait à qui il parle (certificat valide).

Même si ton projet RNCP n’est pas déployé en prod, tu dois :

- Comprendre le principe,
- Savoir qu’en production, il faut **obligatoirement** utiliser HTTPS.

> Phrase :  
> « HTTPS uses TLS to encrypt communications between client and server, preventing attackers from reading or modifying the data in transit. »

---

### 6.2. Monitoring & logs

**Monitoring :**

- Surveiller l’état de l’appli :
  - uptime,
  - erreurs,
  - temps de réponse,
  - charge serveur.

**Logs :**

- Traces des événements :
  - requêtes,
  - exceptions,
  - décisions métier (utile pour un bot de trading : signaux, ordres envoyés, réponses de l’API…).

Points importants :

- Ne pas logguer de **données sensibles** (mots de passe, clés, tokens),
- Utiliser les logs pour **détecter les comportements anormaux** (ex : nombreuses erreurs 401/403).

---

### 6.3. Backup de base de données

Pourquoi :

- Se protéger contre :
  - suppression accidentelle,
  - corruption de données,
  - crash serveur.

Bonnes pratiques :

- Faire des **sauvegardes régulières**,
- **Tester la restauration** (un backup non testé n’est pas un vrai backup),
- Protéger les fichiers de sauvegarde (car ils contiennent toutes les données).

Exemple classique pour MySQL : `mysqldump` (invoqué en ligne de commande ou via un script).

---

### 6.4. PoLP – Principle of Least Privilege

**Principe de moindre privilège :**

> Chaque utilisateur / process / service n’a que les **permissions minimales nécessaires** pour accomplir sa tâche, rien de plus.

Exemples :

- Utilisateur BDD pour ton app :
  - pas de droits `DROP DATABASE`,
  - seulement `SELECT/INSERT/UPDATE/DELETE` sur quelques tables.
- Clés API d’échange :
  - si tu fais uniquement du read-only → clé en lecture seule,
  - si tu fais du demo trading → limiter les marchés, comptes, etc.
- Process système :
  - l’application tourne sous un utilisateur non root.

---

## 7. Tests backend & API

### 7.1. Types de tests

- **Tests unitaires**  
  - Testent une fonction / méthode isolée.
  - Exemple : fonction de calcul d’indicateur (MACD, RSI…) avec des entrées connues → vérifier le résultat.

- **Tests d’intégration**  
  - Testent plusieurs couches ensemble (route → logique métier → BDD).
  - Exemple : endpoint `POST /strategies` → vérifie :
    - validation des données,
    - insertion en BDD,
    - réponse HTTP correcte.

- **Tests end-to-end / manuels**  
  - Scénario complet du point de vue utilisateur.
  - Exemple : “Créer une stratégie, lancer le bot, récupérer des trades, vérifier qu’ils s’affichent dans le dashboard.”

---

### 7.2. Tests avec Postman (ou Insomnia, etc.)

**Rôle de Postman :**

- Appeler tes endpoints API,
- Configurer les **routes, méthodes, headers, body JSON**,
- Voir les réponses (code HTTP, JSON, messages d’erreur),
- Organiser des **collections de requêtes**.

Pour ton rapport RNCP, tu peux :

- Décrire les principaux scénarios testés avec Postman, par exemple :
  - création de ressource (201),
  - validation d’erreur (400),
  - accès interdit (401/403),
  - ressource non trouvée (404).
- Ajouter en **annexe** des **captures d’écran**:
  - requête,
  - réponse.

---

### 7.3. Jeux de tests (test cases)

Un **jeu de test** =

1. **Contexte / prérequis** (ex : BDD avec telle donnée),
2. **Entrée** (données envoyées dans la requête),
3. **Action** (endpoint ou fonction appelée),
4. **Résultat attendu** (code HTTP, contenu de réponse, état en BDD).

Exemples pour un bot / API :

1. **Création de stratégie valide**  
   - Entrée : JSON avec paramètres cohérents (périodes positives, etc.).  
   - Résultat attendu : HTTP 201, objet créé, enregistrement en BDD.

2. **Création de stratégie invalide**  
   - Entrée : JSON avec période négative.  
   - Résultat attendu : HTTP 400 avec message d’erreur clair, aucun enregistrement créé.

3. **Récupération de trades**  
   - Entrée : `GET /trades?strategy_id=XYZ`.  
   - Résultat attendu : HTTP 200, liste JSON des trades correspondant à la stratégie.

4. **Erreur d’appel vers un provider externe**  
   - Simulation d’échec (API indisponible / mauvaise clé).  
   - Résultat attendu : gestion d’erreur propre :
     - pas de crash,
     - message d’erreur clair,
     - log côté serveur.

---

## 8. Ce qui est attendu concrètement (rapport + oral)

### 8.1. Dans le dossier de projet (rapport RNCP)

On s’attend à trouver :

1. **Une section “Architecture de l’application”** :
   - monolithique ou non,
   - architecture en couches,
   - lien avec MVC (si pertinent),
   - éventuellement un diagramme simple (composants / BDD).

2. **Une section “Sécurité & données”** :
   - hashage des mots de passe (si auth),
   - gestion des secrets (clés API dans `.env`, non commit),
   - protection contre SQLi (requêtes paramétrées),
   - mention de XSS/CSRF si l’appli est exposée via des formulaires / front,
   - HTTPS (au moins comme recommandation pour une mise en production),
   - lien avec le **RGPD** (si données personnelles).

3. **Une section “Tests backend & API”** :
   - description des scénarios de test,
   - utilisation de Postman / tests unitaires,
   - jeux de tests / jeux d’essai,
   - captures d’écran en annexe.

---

### 8.2. Pendant l’oral RNCP

Tu dois être capable de :

- **Expliquer simplement** :
  - ce qu’est une injection SQL, une XSS, une CSRF,
  - la différence hashage / chiffrement,
  - le principe de moindre privilège,
  - la différence monolithe / microservices.

- **Relier ces notions à ton projet** :
  - “Voici comment je stocke les mots de passe / clés API.”
  - “Voici comment j’évite SQL injection.”
  - “Voici comment je teste mes endpoints d’API avec Postman.”

- **Montrer** (si on te le demande) :
  - un appel d’API dans Postman,
  - un test d’erreur,
  - un extrait de ton code (requêtes paramétrées, gestion des erreurs).

---

## 9. Fiche mémo – Phrases prêtes pour le jury

- **Hash vs Encryption :**  
  *“Hashing is one-way and used to store passwords securely. Encryption is reversible with a key and used when we need to read the data again, for example HTTPS.”*

- **SQL Injection :**  
  *“SQL injection happens when user input is concatenated directly into SQL queries. I prevent it with parameterized queries and by limiting database privileges.”*

- **XSS :**  
  *“XSS is when malicious JavaScript is injected into a page. I avoid it by escaping user input before rendering it in HTML and by avoiding unsafe DOM APIs.”*

- **CSRF :**  
  *“CSRF forces a logged-in user’s browser to send unwanted requests. We can prevent it with CSRF tokens, SameSite cookies and confirmation for sensitive actions.”*

- **PoLP :**  
  *“The principle of least privilege means giving each component only the permissions it really needs, like using a restricted database user for the app.”*

- **Tests backend :**  
  *“I used Postman and defined several test cases to check both success and error scenarios for my API endpoints. I documented the test data and the results in my report.”*

---

## 10. Checklist personnelle – Sécurité, Infra & Tests (RNCP5)

- [ ] Je sais expliquer la différence **hashage / chiffrement** avec des mots simples.
- [ ] Je sais définir **SQL injection**, **XSS**, **CSRF** et citer une mesure de protection pour chacune.
- [ ] Je connais le **principe de moindre privilège (PoLP)** et j’ai un exemple concret dans mon projet.
- [ ] Je peux situer mon projet dans une **architecture monolithique en couches** et l’expliquer au jury.
- [ ] Mon dossier de projet contient une section **“Sécurité & protection des données”**.
- [ ] J’ai défini des **jeux de tests backend / API** et je les ai exécutés (Postman, tests unitaires…).
- [ ] J’ai quelques **captures d’écran** de tests (API, erreurs, succès) à mettre en annexe.
- [ ] Je me sens capable de répondre à plusieurs questions du jury sur la sécurité et les tests backend sans paniquer. 😈
