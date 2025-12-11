## Module 11 – Frontend : RGPD & protection des données (RNCP5)

### 11.1. Rôle de ce module dans la préparation RNCP

Ce module traite du **RGPD** et de la **protection des données personnelles**, un point **très surveillé** par les jurés RNCP.

Pour le titre DWWM (RNCP5), on attend de toi que tu saches :

- ce qu’est le **RGPD** (et globalement à quoi il sert),
- ce qu’est la **CNIL** et son rôle,
- identifier si ton projet **manipule des données personnelles**,
- montrer que tu as pris **quelques précautions techniques simples**,
- en parler dans ton **rapport** et à l’**oral**.

> Même si ton projet n’est pas un “gros site grand public”, le fait de **connaître les bases RGPD** montre que tu es un **développeur responsable**.  
> C’est exactement ce que les jurés veulent voir.

---

### 11.2. La CNIL : c’est quoi ?

#### 11.2.1. Définition

La **CNIL** = *Commission Nationale de l’Informatique et des Libertés*.

En France, c’est l’autorité publique indépendante qui :

- veille à la **protection des données personnelles**,
- s’assure que les organisations respectent le **RGPD** et la loi “Informatique et Libertés”,
- informe les citoyens sur leurs droits,
- peut **contrôler** et **sanctionner** en cas de non-respect.

> Au jury, tu peux dire :  
> “La CNIL, c’est l’autorité française qui contrôle l’application du RGPD et protège les données personnelles des citoyens.”

#### 11.2.2. Ce que la CNIL fait concrètement

- Publie des **guides pratiques** (dont un **guide RGPD pour les développeurs**),
- donne des **recommandations** sur :
  - les **mots de passe**,
  - la durée de **conservation** des données,
  - la **sécurité** minimale,
  - les **cookies / traceurs**, etc.
- Peut intervenir en cas de :
  - fuite de données,
  - non-respect des droits des personnes,
  - utilisation abusive de données.

---

### 11.3. Le RGPD : les bases à maîtriser

#### 11.3.1. Qu’est-ce que le RGPD ?

**RGPD** = *Règlement Général sur la Protection des Données* (en anglais GDPR).

C’est un **règlement européen** qui encadre :

> la **collecte**, le **stockage**, le **traitement** et le **partage** des **données personnelles** des personnes situées dans l’UE.

Objectifs :

- Protéger la **vie privée**,
- Donner des **droits** aux personnes,
- Imposer des **obligations** aux organisations (entreprises, associations, etc.).

#### 11.3.2. Qu’est-ce qu’une “donnée personnelle” ?

Une **donnée personnelle**, c’est :

> toute information qui permet d’identifier directement ou indirectement une personne physique.

Exemples :

- Directement :
  - nom, prénom,
  - email,
  - numéro de téléphone,
  - adresse postale,
  - numéro de client, etc.
- Indirectement :
  - identifiant de session,
  - adresse IP (dans certains cas),
  - identifiant de compte,
  - données de localisation, etc.

Même si tes données sont “techniques”, si on peut remonter à une personne, c’est de la **donnée perso**.

#### 11.3.3. Quelques notions de base

- **Responsable de traitement** : celui qui décide “pourquoi” et “comment” les données sont traitées.
- **Sous-traitant** : celui qui traite les données pour le compte du responsable (ex : hébergeur).
- **Personne concernée** : l’utilisateur, le client, la personne dont les données sont traitées.

Même si tu ne vas pas faire du juridique, tu dois comprendre ces mots.

#### 11.3.4. Principes importants pour un développeur

Sans rentrer dans les articles de loi, retiens surtout :

1. **Finalité** : les données sont collectées pour un objectif clair et légitime.
2. **Minimisation** : tu ne collectes que ce qui est **strictement nécessaire**.
3. **Limitation de durée** : tu ne gardes pas les données **plus longtemps que nécessaire**.
4. **Sécurité** : tu protèges les données (mots de passe, accès, logs).
5. **Transparence** : tu expliques ce que tu fais avec les données.
6. **Droits des personnes** : accès, rectification, effacement, etc.

---

### 11.4. Comment le RGPD entre dans un projet RNCP ?

Même pour un “simple projet RNCP”, tu dois te poser la question :

> “Est-ce que mon application manipule des données personnelles ? Si oui, lesquelles et pour quoi faire ?”

#### 11.4.1. Cas typiques en RNCP5

- **Portfolio / site vitrine** :
  - formulaire de contact (nom, email, message),
  - éventuellement suivi statistique (analytics).
- **Application web avec comptes utilisateurs** :
  - email, mot de passe,
  - profil, préférences, historique.
- **Application B2B / dashboard** :
  - données de clients,
  - identifiants, logs, etc.

#### 11.4.2. Cas de ton Smart Trading Bot (exemple)

Pour ton **Smart Trading Bot**, tu peux avoir :

- Données **techniques** :
  - historique de prix, signaux, trades… (pas des données perso).
- Éventuelles données perso si :
  - il y a des comptes utilisateurs (login / password),
  - tu stockes un email,
  - tu logs des adresses IP, des identifiants, etc.

Même si ton projet est **monoutil perso** pour toi, tu peux expliquer au jury :

- que tu as **réfléchi à la protection** des données (clés API, logs, accès),
- que si demain tu l’ouvrais à d’autres utilisateurs, tu appliquerais des mesures RGPD simples.

---

### 11.5. Comment avoir un site “RGPD-friendly” à ton niveau ?

Tu n’es pas DPO, mais tu peux déjà faire beaucoup en tant que développeur.

#### 11.5.1. Étape 1 – Cartographier les données

Se poser les questions :

1. Quelles **données** je collecte ?
   - Ex : nom, email, message dans un formulaire, logs, cookies…
2. Où sont-elles **stockées** ?
   - BDD, fichiers logs, localStorage…
3. Pourquoi je les collecte ? (**finalité**)
   - Répondre à un message, afficher une fonctionnalité, garantir la sécurité, etc.
4. Combien de temps je les garde ?
   - Durée définie ou au minimum le principe de ne pas les conserver “à vie” sans raison.

#### 11.5.2. Étape 2 – Minimisation

- Ne collecter que ce qui est **utile** :
  - si tu n’as besoin que de l’email, ne demande pas l’adresse postale.
- Ne pas conserver des données “au cas où” sans raison.

> Exemple dans un formulaire de contact :  
> Demander *nom + email + message* est souvent suffisant.  
> Pas besoin de date de naissance, adresse complète, etc.

#### 11.5.3. Étape 3 – Information de l’utilisateur (transparence)

- Prévoir au minimum une **page ou un paragraphe** “Protection des données / Confidentialité” qui explique :
  - quelles données tu collectes,
  - pour quoi faire,
  - qui y a accès,
  - comment on peut te contacter pour exercer ses droits.

Même sur un petit projet, tu peux avoir un texte simple dans ton portfolio.

#### 11.5.4. Étape 4 – Consentement (notamment cookies / trackers)

- Si tu utilises des **cookies techniques** indispensables (session, panier, etc.) :
  - pas besoin de gros bandeau de consentement, mais tu peux l’expliquer dans ta politique de confidentialité.
- Si tu utilises des **cookies de tracking / analytics** (Google Analytics sans anonymisation IP, par exemple) :
  - là, il faut un **bandeau de consentement** clair,
  - respecter le choix de l’utilisateur (ne pas déposer le cookie si refus).

Pour le RNCP, c’est surtout la **démarche** qui compte :

> montrer que tu sais faire la différence entre “strictement nécessaire” et “suivi marketing / stats”.

#### 11.5.5. Étape 5 – Sécurité minimale

- Pour les **mots de passe** :
  - jamais stockés en clair,
  - utiliser un **hachage** (bcrypt, argon2, etc.) côté back.
- Pour les **clés sensibles** (ex : clés API Bitget) :
  - **jamais** dans le code versionné,
  - stockées en variables d’environnement,
  - pas dans le localStorage côté front.
- Pour les **logs** :
  - éviter de logguer des infos sensibles (mots de passe, numéros, tokens),
  - si tu logs des IDs, rester raisonnable.

Tu peux faire référence aux recommandations de la **CNIL** sur les mots de passe (longueur, complexité, etc.), sans rentrer dans les détails chiffrés.

---

### 11.6. Application concrète à ton projet (Smart Trading Bot + portfolio)

#### 11.6.1. Smart Trading Bot

Quelques points que tu pourras valoriser devant le jury :

- **Clés API Bitget** :
  - pas en dur dans le code,
  - pas envoyées au front,
  - stockage sécurisé (config côté serveur, `.env` non versionné).
- **Logs** :
  - pas de stockage des secrets dans les logs,
  - logs orientés technique (erreurs, succès d’appels, etc.).
- **Éventuels utilisateurs à venir** :
  - si tu ajoutes un système d’authentification :
    - hachage des mots de passe,
    - expliciter la finalité (accès à l’interface, historique perso),
    - prévoir un moyen de suppression de compte.

Tu peux dire au jury :

> “Actuellement, mon projet manipule surtout des données techniques de marché.  
> Cependant, j’ai appliqué des principes RGPD sur la sécurité des données (clés API, logs) et je sais que si j’ouvrais le service à d’autres utilisateurs, il faudrait définir clairement les finalités, les durées de conservation, les droits d’accès, etc.”

#### 11.6.2. Portfolio / page de présentation

C’est l’endroit **idéal** pour montrer que tu as intégré le RGPD :

- Formulaire de contact :
  - champs minimaux,
  - mention “Vos données ne sont utilisées que pour répondre à votre message”.
- Politique simple de confidentialité :
  - expliquer que :
    - tu ne revends pas les données,
    - tu gardes éventuellement l’email dans ta boîte de réception,
    - le visiteur peut demander la suppression de son message.
- Cookies :
  - si pas d’analytics / trackers → le dire clairement ;
  - si analytics → bandeau de consentement + respects des choix.

---

### 11.7. Questions typiques de jury sur le RGPD

On peut te poser par exemple :

1. **“Qu’est-ce que le RGPD ?”**  
   → Règlement européen sur la protection des données personnelles.

2. **“Qu’est-ce que la CNIL ?”**  
   → Autorité française qui veille au respect des lois sur la protection des données.

3. **“Votre application traite-t-elle des données personnelles ? Lesquelles ?”**  
   → Tu expliques ce que tu stockes (ou non).

4. **“Qu’avez-vous mis en place pour respecter le RGPD à votre niveau ?”**  
   → Tu cites :
   - minimisation des données,
   - informations utilisateur,
   - sécurité des mots de passe / clés,
   - gestion des cookies.

5. **“Quels sont les droits des utilisateurs sur leurs données ?”** (niveau simple)  
   - droit d’accès,
   - droit de rectification,
   - droit à l’effacement (“droit à l’oubli”),
   - éventuellement portabilité.

6. **“En tant que développeur, que pouvez-vous faire pour aider à la conformité RGPD ?”**  
   - cartographier les données,
   - limiter ce qu’on collecte,
   - sécuriser les données,
   - documenter ce qui est fait.

Prépare 2–3 réponses **courtes** que tu sais dire sans réfléchir.

---

### 11.8. Fiche mémo – phrases prêtes pour l’oral

- **Définition RGPD :**  
  “Le RGPD est un règlement européen qui encadre la collecte et le traitement des données personnelles pour protéger la vie privée des utilisateurs.”

- **CNIL :**  
  “La CNIL est l’autorité française qui contrôle l’application du RGPD et conseille sur la protection des données.”

- **Lien avec ton projet :**  
  “Dans mon projet, j’ai surtout des données techniques, mais j’ai quand même appliqué des principes RGPD comme la protection des clés API, la minimisation des données, et je pourrais facilement étendre ces principes si j’ajoute des utilisateurs.”

- **En tant que dev :**  
  “As a developer, I can help with GDPR by minimizing collected data, securing storage and access, avoiding logging sensitive information, and clearly informing users about how their data is used.”

---

### 11.9. Checklist personnelle – RGPD & projet RNCP

- [ ] Je sais expliquer **ce qu’est le RGPD** en 1–2 phrases.  
- [ ] Je sais expliquer **ce qu’est la CNIL** et son rôle.  
- [ ] J’ai identifié si mon projet **manipule des données personnelles** (et lesquelles).  
- [ ] Je sais citer au moins **3 principes RGPD** (finalité, minimisation, sécurité…).  
- [ ] Mon projet applique **au moins quelques bonnes pratiques simples** :
  - minimisation des données collectées,
  - protection des mots de passe / clés,
  - gestion raisonnable des logs,
  - information minimale des utilisateurs.  
- [ ] J’ai une idée de ce que je dirai si on me demande :
  - “Comment votre projet respecte-t-il le RGPD ?”
- [ ] Je me sens capable de répondre à des questions de base sur le RGPD pendant l’entretien technique ou final.

