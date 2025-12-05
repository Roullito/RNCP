## Module 4 – Support de présentation orale

### 4.1. Rôle du support de présentation

Le support de présentation (les **slides**) sert à :

- Structurer ton discours pendant la **présentation de projet**.
- Aider le jury à visualiser :
  - le **contexte**,
  - les **besoins**,
  - l’**architecture / environnement technique**,
  - les **réalisations** (front + back),
  - la **sécurité**, les **tests**, la **veille**, etc.
- Servir de **base visuelle** pour certaines questions pendant l’entretien technique.

Le support **complète** ce que tu dis à l’oral :  
> il ne doit pas être un copier/coller de ton discours, mais un **squelette visuel + mots-clés**.

---

### 4.2. Nouveautés & cadre officiel

- La **note de synthèse** n’est plus demandée (ancien format).  
- L’ancienne **introduction orale en anglais** est remplacée par le **questionnaire professionnel en anglais** au début de l’épreuve.  
  → Tu ne fais donc **plus d’introduction “Hello my name is…”** en anglais devant le jury.

- Tu dois préparer **un seul support** pour tous les projets que tu présentes.  
- Le support doit être **envoyé au staff au plus tard J-7** (une semaine avant l’épreuve) pour vérification.

---

### 4.3. Logique du plan des slides (alignée avec le REV)

Pour un projet réalisé en formation, le référentiel d’évaluation organise la présentation autour de :  

1. **Expression des besoins**  
2. **Environnement technique**  
3. **Réalisations permettant la mise en œuvre des compétences**

Ton support doit donc suivre cette logique.

---

### 4.4. Structure recommandée des slides – Smart Trading Bot (DWWM)

Objectif : 12 à 18 slides max, **1 à 2 minutes par slide**.

> Exemple de structure que tu pourras adapter :

1. **Slide 1 – Titre & identité**
   - Titre : “Smart Trading Bot – Application web de trading crypto (mode démo)”
   - Nom, titre visé (DWWM), centre (Holberton)

2. **Slide 2 – Plan de la présentation**
   - Contexte & besoins  
   - Environnement technique  
   - Réalisations front-end (AT1)  
   - Réalisations back-end (AT2)  
   - Sécurité, tests & veille  
   - Bilan & perspectives

3. **Slide 3 – Contexte**
   - Problématique : automatiser des stratégies de trading crypto en environnement sécurisé (démo)  
   - Utilisateurs ciblés : développeur / trader technique, usage perso / labo  
   - Contexte formation : projet de fin d’année (Demo Day) + support RNCP

4. **Slide 4 – Expression des besoins**
   - Besoins principaux :
     - Récupérer et stocker des données de marché (OHLCV)
     - Tester des stratégies (backtest)
     - Exécuter les signaux en mode démo
     - Visualiser les résultats via une interface web
   - Périmètre retenu (MVP) vs périmètre futur (v2, IA…)

5. **Slide 5 – Architecture générale**
   - Schéma global :
     - Front web (dashboard)  
     - API / back-end  
     - Base de données  
     - API Bitget (mode demo)  
   - Flèches et légende simples (qui parle à un jury non-trader)

6. **Slide 6 – Environnement technique**
   - Front : HTML/CSS/JS (ou framework prévu)  
   - Back : Python (+ libs principales)  
   - Données : type de stockage / BDD  
   - Outils : GitHub, virtualenv, etc.

7. **Slide 7 – Réalisations front (AT1) – Maquettes & pages**
   - Capture(s) de maquettes (Figma / autre) : page dashboard, historique des trades…  
   - Points clés : responsive, lisibilité, organisation des infos

8. **Slide 8 – Réalisations front (AT1) – Dynamique**
   - Diagramme simple : navigateur → API → affichage  
   - Exemple d’interaction :
     - Sélection de la stratégie
     - Rafraîchissement des données
     - Retour visuel (succès / erreur)

9. **Slide 9 – Réalisations back (AT2) – Données & BDD**
   - Schéma de la BDD (tables ou structures principales : OHLCV, trades, stratégies, logs)  
   - Explication rapide du choix (relationnel / fichiers structurés, etc.)

10. **Slide 10 – Réalisations back (AT2) – Composants métier**
    - Bloc “stratégies” : MACD, RSI, DCA…  
    - Bloc “moteur d’exécution” : génère des ordres, enregistre les trades  
    - Comment ces briques se parlent (diagramme ultra simple)

11. **Slide 11 – Sécurité & qualité**
    - Gestion des clés API (séparation code / secrets, .env…)  
    - Validation des entrées / sorties  
    - Gestion des erreurs (logs, messages)  
    - Quelques tests / jeux d’essai représentatifs

12. **Slide 12 – Veille & bonnes pratiques**
    - Thèmes de veille : sécurité des API, bonnes pratiques web, trading / volatilité…  
    - Exemples de décisions influencées par la veille

13. **Slide 13 – Bilan & perspectives**
    - Ce qui fonctionne aujourd’hui  
    - Compétences DWWM travaillées (front + back)  
    - Évolutions envisagées : UI plus poussée, IA/ML, déploiement cloud…

14+. **Slides d’annexes (backup)**
    - Captures supplémentaires du dashboard  
    - Schémas plus détaillés (architecture, BDD)  
    - Extraits de logs / exemples de résultats de backtests  
    - Diagrammes que tu n’es pas certain d’avoir le temps de présenter

> Ces slides d’annexes servent de **support en cas de questions** du jury.

---

### 4.5. Bonnes pratiques pour le support

- **Lisibilité avant tout** :
  - Police assez grande
  - Peu de texte, mots-clés / bullets
  - Contraste correct (fond clair / texte foncé ou inverse)

- **1 idée principale par slide**
  - Évite les slides fourre-tout avec 8 blocs différents
  - Préfère dupliquer un slide plutôt que le surcharger

- **Lien constant avec les compétences DWWM**
  - AT1 / AT2, CP1 → CP8 : pense régulièrement “ce slide prouve quoi ?”

- **Lien avec le dossier de projet**
  - Les schémas / captures peuvent reprendre ceux du rapport
  - Mais en version simplifiée / plus visuelle

- **Préparation orale**
  - T’entraîner à voix haute (idéalement avec un public)
  - Viser 1–2 minutes par slide  
  - Travailler les transitions (“Nous avons vu les besoins, passons maintenant à l’architecture…”)
  - Anticiper des questions typiques en ayant des slides de backup

---

### 4.6. Checklist personnelle – Support de présentation

- [ ] J’ai un seul support pour l’ensemble de mes projets.  
- [ ] Ma présentation suit le plan :  
      *Besoins → Environnement technique → Réalisations → Sécurité / qualité → Bilan / perspectives*.  
- [ ] Mon projet principal “Smart Trading Bot” est clairement mis en avant.  
- [ ] Je montre des éléments **front** (AT1) et **back** (AT2).  
- [ ] J’ai quelques slides d’annexes au cas où le jury pose des questions techniques.  
- [ ] J’ai relu mon support pour vérifier lisibilité et cohérence.  
- [ ] J’ai envoyé mon support au staff **au plus tard J-7**.  
- [ ] Je me suis entraîné à voix haute sur la durée et les transitions.
