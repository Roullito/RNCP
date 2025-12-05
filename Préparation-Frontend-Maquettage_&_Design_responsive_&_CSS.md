## Module 7 – Frontend : Maquettage, Design Responsive & CSS (RNCP5)

### 7.1. Rôle de ce module dans la préparation RNCP

Ce module fait partie de la préparation **technique Frontend** pour le passage du titre RNCP 5 (DWWM).

L’objectif n’est pas de te donner des “exos à faire”, mais de t’assurer que tu maîtrises assez bien :

- le **maquettage d’une page / application web**,
- le **design responsive**,
- quelques **bases solides en CSS**,

pour :

- **rédiger ton rapport** (dossier de projet) en expliquant tes choix front,  
- **répondre aux questions du jury** pendant l’entretien technique,
- **justifier ton interface** (ex : dashboard du Smart Trading Bot).

> Les projets RNCP sont surtout un **ensemble de ressources, docs, rappels et quizzes**, pas des projets à coder.  
> Le but : te rapprocher au maximum des **questions réelles** déjà posées aux candidats.

---

### 7.2. Le maquettage d’une page web

#### 7.2.1. Définition

Le **maquettage** consiste à **préparer visuellement** ton interface avant de la coder.  
Concrètement, il s’agit de :

- décider **où** seront les blocs (header, sidebar, contenu, footer, boutons…),
- structurer l’information (hiérarchie visuelle, titres, sections),
- penser à l’**expérience utilisateur (UX)** avant de toucher au CSS.

#### 7.2.2. Pourquoi faire du maquettage ?

- Éviter de “coder au hasard” → tu sais où tu vas.
- Gagner du temps → moins de retours en arrière.
- Clarifier l’**expérience utilisateur** (ce que l’utilisateur voit et fait).
- Avoir un support à montrer au jury dans ton dossier / présentation.

Pour ton **Smart Trading Bot**, ça veut dire par exemple :

- Où afficher le **graphique de prix / indicateurs**,
- Où placer les **boutons Start/Stop stratégie**,
- Où afficher l’**historique des trades / PnL**.

#### 7.2.3. À quel moment on maquette ?

- Après la **définition des besoins** (MVP, fonctionnalités),
- Avant ou en parallèle de la **conception technique** (BDD, API),
- Avant d’écrire le gros du **HTML/CSS/JS**.

En pratique : tu peux faire une première version papier / Figma, puis l’affiner au fur et à mesure.

#### 7.2.4. Wireframe, maquette, prototype : c’est quoi ?

- **Wireframe** :  
  - version très simplifiée “en fil de fer” (blocs gris, textes fictifs),
  - se concentre sur la **structure** (pas sur les couleurs / typo),
  - idéal au début.
- **Maquette** (mockup) :  
  - version plus détaillée, avec **couleurs, polices, visuels**, etc.,
  - proche du rendu final.
- **Prototype** :  
  - maquette **cliquable / interactive**,
  - permet de simuler les interactions.

Pour le RNCP5, **un bon wireframe + une ou deux maquettes propres suffisent largement**.

#### 7.2.5. Outils possibles

- **Figma** (le plus courant),
- **Miro**, **Whimsical**, **Excalidraw**,
- Ou même **papier + crayon** (scan ou photo propre).

Le jury ne va pas te sanctionner sur l’outil, mais sur ta capacité à **penser ton interface**.

---

### 7.3. Le design responsive

#### 7.3.1. Qu’est-ce que le design responsive ?

Le **design responsive** permet à ton site de :

- s’adapter à différents **tailles d’écran** (mobile, tablette, desktop),
- rester **lisible** et **utilisable** dans tous les cas.

L’objectif :  
> Une **seule base HTML**, plusieurs dispositions possibles selon la largeur d’écran.

#### 7.3.2. Comment l’appliquer (sans framework)

Sans Bootstrap ou autre framework, tu peux déjà faire du responsive avec :

- **unités relatives** : `%`, `vh/vw`, `em/rem` plutôt que tout en `px`,
- **Flexbox** :
  - `display: flex;`, `justify-content`, `align-items`, `flex-direction`,
- **CSS Grid** :
  - `display: grid;`, `grid-template-columns`, `gap`, etc.,
- **Media queries** :

```css
@media (max-width: 768px) {
  /* Styles pour tablettes / mobiles */
}

@media (max-width: 480px) {
  /* Styles pour petits mobiles */
}
