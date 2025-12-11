## Module 10 – Frontend : Tester la partie frontend d’une application web (DevTools)

### 10.1. Rôle de ce module dans la préparation RNCP

Ce module est la **4ᵉ partie** de la préparation aux compétences Frontend pour le titre DWWM (RNCP 5).

Objectif : le jour du RNCP, tu dois être capable de :

- **expliquer ce que sont les DevTools** (outils de développement du navigateur),
- **montrer** comment tu testes la partie frontend de ton application,
- **déboguer** “en live” une page (HTML, CSS, JS, responsive),
- **démontrer** que tu sais vérifier :
  - le rendu visuel (layout),
  - le responsive,
  - les erreurs JavaScript,
  - les requêtes réseau (API),
  - les performances (de base).

> Les jurés peuvent te demander :  
> *“Comment avez-vous testé la partie frontend ? Pouvez-vous nous montrer les DevTools ?”*  
> Tu dois être à l’aise pour **ouvrir les DevTools, naviguer dans quelques onglets et expliquer ce que tu fais**.

---

### 10.2. Qu’est-ce que les DevTools ?

Les **DevTools** (Chrome DevTools, Firefox Developer Tools, etc.) sont un ensemble d’outils intégrés dans le navigateur qui permettent de :

- **Inspecter** et modifier le DOM et le CSS en temps réel,
- **Voir les erreurs JavaScript** et exécuter du JS,
- **Analyser les requêtes réseau** (GET, POST, API, status, payload…),
- **Tester le responsive design** sur différentes tailles d’écran,
- **Analyser les performances** (temps de chargement, rendering),
- **Auditer** ton site (accessibilité, SEO, bonnes pratiques),
- **Inspecter le stockage** (cookies, localStorage, sessionStorage…).

Accès rapide (Chrome / Edge / Brave…) :

- Clic droit → **Inspecter**,  
- Ou **F12**,  
- Ou **Ctrl + Shift + I** (Cmd + Option + I sur Mac).

> Important pour le RNCP :  
> Tu n’as pas besoin de tout connaître **en profondeur**, mais tu dois savoir **à quoi servent les principaux onglets** et être capable de les utiliser pour **tester ton front**.

---

### 10.3. Vue d’ensemble des principaux onglets des DevTools

Les noms exacts varient un peu selon les navigateurs, mais l’idée est la même :

- **Elements** (ou Inspector) – DOM + CSS
- **Console** – erreurs JS, logs, exécution de code
- **Network** – requêtes HTTP, API, assets
- **Sources** – code JS, breakpoints (debug)
- **Application / Storage** – cookies, localStorage, sessionStorage, cache…
- **Performance** – profilage des performances (chargement, rendu)
- **Memory** – analyse (plus avancée)
- **Lighthouse / Audits** – audit automatique (perf, SEO, accessibilité)
- **Responsive Design Mode** – simulé via la barre d’outils d’appareil (Device Toolbar)

Tu peux les citer lors de l’entretien, mais surtout **en montrer 3–4 bien maîtrisés** (Elements, Console, Network, responsive, éventuellement Lighthouse).

---

### 10.4. Tester / déboguer le HTML & le CSS (onglet Elements)

#### 10.4.1. Inspection du DOM

- L’onglet **Elements** permet de :
  - voir la structure HTML **réelle** après exécution du JS,
  - survoler des éléments pour voir leur **position et taille**,
  - modifier le HTML à la volée pour tester des idées.

Exemples d’utilisation :

- Vérifier que les bonnes classes sont appliquées.
- Chercher un élément par son texte ou sa classe (Ctrl + F).
- Voir si un élément est bien dans le bon conteneur.

#### 10.4.2. Déboguer le CSS

Toujours dans **Elements**, tu as le panneau de styles :

- Voir tous les styles appliqués sur l’élément sélectionné :
  - règles CSS,
  - fichier source,
  - lignes barrées (styles écrasés par une règle plus spécifique).
- Activer / désactiver une propriété (cocher / décocher).
- Modifier une valeur (couleur, margin, display…) en direct.

Utilités :

- Comprendre pourquoi un élément est **mal positionné**.
- Corriger un bug visuel sans toucher au code source tout de suite.
- Tester rapidement des variantes (padding, flex, grid, etc.)

#### 10.4.3. Box model & calcul des styles

Dans la partie “Computed” / “Layout” :

- Voir le **box model** :
  - content,
  - padding,
  - border,
  - margin.
- Voir les **valeurs finales** après cascade et héritage.

> À l’oral, tu peux dire :  
> “Pour déboguer mon CSS, j’utilise l’onglet Elements pour inspecter le DOM, voir les styles appliqués, comprendre le box model et tester des changements en live.”

---

### 10.5. Tester les erreurs JS & la logique front (Console + Network)

#### 10.5.1. Console

L’onglet **Console** permet de :

- voir les **erreurs JavaScript** (exceptions, erreurs de syntaxe),
- voir les **warnings** (logs, dépréciations),
- exécuter du code JS manuellement.

Exemples d’utilisation :

- Voir les erreurs lorsqu’un bouton ne fonctionne pas.
- Tester une fonction directement :  
  `myFunction(42)`.
- Afficher des valeurs avec `console.log(...)`.

Pour ton **Smart Trading Bot** :

- Vérifier les erreurs lorsqu’une stratégie ne se lance pas,
- Voir si des appels JS vers l’API échouent,
- Vérifier les valeurs calculées (signaux, paramètres…).

#### 10.5.2. Network – suivre les requêtes front ↔ back / API

L’onglet **Network** permet de :

- voir **toutes les requêtes HTTP** faites par la page :
  - type (fetch/XHR, JS, CSS, images),
  - méthode (GET, POST…),
  - status (200, 404, 500, 401…),
  - temps de réponse,
  - taille.
- inspecter :
  - les **headers**,
  - le **payload** envoyé,
  - la **réponse** (JSON, HTML…).

Pour ton bot :

- Suivre les appels à l’API Bitget / back-end :
  - vérifier qu’ils partent bien,
  - voir la réponse (données OHLCV, signaux…),
  - voir les erreurs (ex : 401 si problème de clé, 429 si rate limit, etc.).
- Vérifier les performances (temps des requêtes).
- S’assurer que les endpoints utilisés par le front sont ceux prévus.

> À l’oral :  
> “Pour tester la communication entre mon front et mon back / API, j’utilise l’onglet Network pour vérifier les requêtes, les codes de retour et le contenu des réponses.”

---

### 10.6. Tester le design responsive

#### 10.6.1. Device Toolbar (mode responsive)

Dans les DevTools (Chrome) :

- Cliquer sur l’icône de **téléphone/tablette** (en haut à gauche des DevTools) → cela active la **barre d’outils pour appareils**.
- Tu peux ensuite :
  - simuler différents **tailles d’écran** (iPhone, iPad, custom…),
  - tester l’orientation (portrait / paysage),
  - zoomer / dézoomer.

#### 10.6.2. Vérifier le comportement du layout

Ce que tu dois tester :

- Les éléments restent-ils lisibles ?
- Les blocs ne se chevauchent pas ?
- Les boutons principaux restent accessibles **sans scroll infini** ?
- Les polices ne deviennent pas trop petites ?

Pour ton bot :

- Sur mobile :
  - afficher en priorité les infos clés (statut des stratégies, PnL global),
  - éviter d’essayer de caser l’énorme graphique de la même façon que sur desktop,
  - simplifier les tableaux (scroll horizontal ou version condensée).

> À l’oral, tu peux dire :  
> “J’ai utilisé le mode responsive des DevTools pour vérifier le rendu sur différentes largeurs, et ajuster mes media queries / layout flex/grid en conséquence.”

---

### 10.7. Audits & performance (Lighthouse, Performance…)

#### 10.7.1. Lighthouse / Audits

L’onglet **Lighthouse** (ou **Audits**) permet de lancer :

- un audit automatique sur :
  - les **performances**,
  - l’**accessibilité**,
  - les **bonnes pratiques**,
  - le **SEO** (basique),
  - éventuellement PWA.

Résultat :

- un rapport avec :
  - des **scores** (0–100),
  - des **recommandations** concrètes.

Pour le RNCP5, tu peux :

- lancer un audit sur ta page principale / portfolio,
- garder une **capture du rapport** dans tes annexes,
- mentionner que tu l’as utilisé pour améliorer :
  - les performances,
  - l’accessibilité.

#### 10.7.2. Performance / Memory (niveau basique)

L’onglet **Performance** (ou “Performance & Mémoire”) permet de :

- enregistrer un **profil** du chargement / exécution,
- voir quels scripts / tâches prennent du temps,
- repérer des blocages.

Pour l’oral RNCP5, tu peux rester simple :

- dire que tu sais qu’il existe un outil de profilage des performances,
- que tu l’as utilisé pour vérifier que ta page ne se bloque pas,
- mais tu n’as pas besoin d’entrer dans une analyse très poussée.

---

### 10.8. Application concrète à ton projet « Smart Trading Bot »

Tu peux structurer ta partie “tests frontend” dans le rapport / présentation comme ceci :

1. **Tests visuels & CSS**
   - Objectif : vérifier que le dashboard est lisible, bien mis en page.
   - Outils :
     - onglet Elements,
     - test des styles, du box model.
   - Exemple :
     - correction d’un bug d’alignement dans le tableau des trades.

2. **Tests fonctionnels côté front**
   - Objectif : vérifier que les boutons et formulaires fonctionnent.
   - Outils :
     - Console pour voir les erreurs JS,
     - Network pour vérifier que les actions déclenchent les bonnes requêtes.
   - Exemple :
     - test de “Start/Stop stratégie” et vérification des requêtes envoyées.

3. **Tests de communication front ↔ API**
   - Objectif : s’assurer que les call API renvoient les bonnes données.
   - Outils :
     - Network (statuts, payload, réponses JSON).
   - Exemple :
     - vérification que les données OHLCV sont correctement récupérées dans le front et affichées.

4. **Tests responsive**
   - Objectif : garantir que le dashboard reste utilisable sur petit écran.
   - Outils :
     - Device Toolbar (mode mobile/tablette),
     - media queries CSS.
   - Exemple :
     - adaptation de la disposition entre desktop (graph + tableaux côte à côte) et mobile (blocs empilés).

5. **Tests d’accessibilité & de bonnes pratiques**
   - Objectif : améliorer l’accessibilité et la qualité globale.
   - Outils :
     - audits Lighthouse,
     - éventuels checkers d’accessibilité.
   - Exemple :
     - ajout d’`alt` sur les images, amélioration du contraste, focus visible.

---

### 10.9. Comment l’expliquer au jury RNCP ?

Quelques phrases prêtes à l’emploi (en français et un peu d’anglais si besoin) :

- **Définition :**  
  “Chrome DevTools is the built-in development tool of the browser. It allows me to inspect HTML/CSS, debug JavaScript, monitor network requests and test responsive design.”

- **Pour les tests CSS :**  
  “I use the Elements panel to inspect the DOM, see which CSS rules are applied, and fix layout issues live.”

- **Pour les tests API :**  
  “With the Network tab, I can see all API calls from the frontend, check the HTTP status codes and the JSON responses. It helped me debug the integration with the Bitget API.”

- **Pour le responsive :**  
  “I use the device toolbar to simulate mobile screens and test my media queries. I check that the dashboard remains readable and usable on smaller devices.”

- **Pour l’audit :**  
  “I sometimes run a Lighthouse audit to get a quick overview of performance, accessibility and best practices, then I fix the main issues reported.”

---

### 10.10. Ce qui est attendu concrètement pour le RNCP

- Dans le **rapport de projet** :
  - Avoir une section **“Tests frontend”** où tu expliques :
    - quels cas tu as testés,
    - quels outils tu as utilisés (DevTools, responsive mode, Network…),
    - ce que ça t’a permis de corriger.
  - Tu peux ajouter en **annexe** :
    - captures d’écran des DevTools (Network, Elements, Lighthouse…).

- Lors de la **présentation orale** :
  - Être capable, si on te le demande, d’ouvrir les DevTools sur ton app et :
    - montrer le DOM / CSS,
    - montrer une requête API dans Network,
    - basculer en vue mobile,
    - expliquer ce que tu fais.

> Si tu n’as pas le temps de montrer tout ça pendant la présentation principale,  
> **prévois des slides d’annexe** ou sois prêt à ouvrir la page et les DevTools pendant les questions.

---

### 10.11. Checklist personnelle – Tests frontend & DevTools

- [ ] Je sais **ouvrir les DevTools** et je connais les principaux onglets (Elements, Console, Network, responsive, Lighthouse).  
- [ ] Je sais **inspecter un élément**, voir ses styles et comprendre le box model.  
- [ ] Je sais utiliser la **Console** pour voir les erreurs JS et faire des `console.log`.  
- [ ] Je sais utiliser l’onglet **Network** pour suivre les requêtes API (statuts, payload, réponses).  
- [ ] Je sais activer le **mode responsive** et tester plusieurs tailles d’écran.  
- [ ] Je suis capable de lancer un **audit Lighthouse** et d’interpréter quelques recommandations.  
- [ ] J’ai prévu une **section “tests frontend”** dans mon rapport de projet (avec DevTools mentionné clairement).  
- [ ] Je suis prêt à **montrer rapidement** les DevTools au jury et à expliquer ce que je fais.

