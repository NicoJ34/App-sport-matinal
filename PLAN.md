# Callistenik — Plan détaillé

> App matinale : une séance de 15–20 min au poids du corps, **tapis de sol uniquement** (pas de chaise, table, mur, barre). Lancement depuis iPhone 13 mini.

---

## 1. Choix technique

**Une PWA (web app installable) en un seul fichier HTML**, hébergée gratuitement sur GitHub Pages.

| Option | Verdict |
|---|---|
| **PWA (HTML/JS) + GitHub Pages** | ✅ Retenu. Gratuit, pas d'App Store, s'ouvre en plein écran depuis l'écran d'accueil, marche hors-ligne. |
| App native Swift | ❌ Compte développeur Apple (99 €/an) ou réinstallation tous les 7 jours. Trop lourd. |
| Raccourci iOS / Notes | ❌ Pas de minuteur guidé, pas d'adaptation. |

**Installation sur l'iPhone** : ouvrir l'URL dans **Safari** → bouton Partager → « Sur l'écran d'accueil ». L'icône se lance comme une vraie app (plein écran, sans barre Safari). Chrome iOS ne permet pas l'installation PWA aussi proprement → utiliser Safari pour installer, peu importe ensuite.

**Stack** : HTML + CSS + JavaScript vanilla, aucun framework, aucun serveur, aucun compte.
- `index.html` (UI + logique)
- `exercises.js` (bibliothèque d'exercices)
- `manifest.json` (nom, icône, plein écran)
- `sw.js` (service worker → hors-ligne)
- `icon-180.png` (icône écran d'accueil iOS)

**Contraintes iPhone 13 mini** : viewport 375 × 812 pt → typo grosse et lisible à 2 m (minuteur ≥ 96 px), boutons ≥ 60 px, tout utilisable d'une main / au pouce, respect de l'encoche (`env(safe-area-inset-*)`).

---

## 2. Écrans

1. **Accueil (« Aujourd'hui »)**
   - Titre de la séance du jour (ex. « Haut du corps + gainage »), durée (15 ou 20 min), liste des exercices.
   - Bouton géant **Démarrer**.
   - Boutons secondaires : « Autre séance », « Préserver les jambes » (jour de course), « Mode silencieux » (sans sauts).
   - Série en cours (🔥 jours consécutifs).

2. **Séance (guidée)**
   - Nom de l'exercice + consigne courte (1–2 lignes, ex. « Dos plat, coudes à 45° »).
   - Minuteur géant décompte, barre de progression globale.
   - « Ensuite : … » pendant la récup.
   - Gestes : tap = pause, glisser = passer, bouton −/+ 10 s.
   - Voix (synthèse FR) : « Pompes, 40 secondes… 3, 2, 1, repos ». Bips aux 3 dernières secondes.

3. **Fin**
   - Résumé (durée, exercices), puis 1 question : **Trop facile / Parfait / Trop dur** → ajuste la prochaine séance.

4. **Historique** : calendrier des séances faites, série, total du mois.

5. **Réglages** : durée par défaut, voix on/off, bips on/off, mode silencieux par défaut, niveau de départ, jours « Préserver les jambes » (jours de course).

---

## 3. Structure d'une séance (15–20 min)

| Bloc | Durée | Contenu |
|---|---|---|
| **Échauffement** | 3 min | 6 × 30 s de mobilité (rotations, cat-cow, squat lent…) |
| **Bloc principal** | 10–14 min | Circuit de 5–6 exercices, 2–3 tours |
| **Retour au calme** | 2–3 min | 4–6 étirements de 30 s |

**Formats du bloc principal** (tournent dans la semaine pour varier) :
- **Circuit** : 40 s effort / 20 s repos, 5 exos × 2–3 tours.
- **EMOM** : chaque minute, X répétitions, le reste = repos.
- **Tabata** : 20 s / 10 s × 8, sur 2 exercices (court et intense).
- **Pyramide** : 30-40-50-40-30 s.

Le moteur ajuste le nombre de tours pour tomber pile sur 15 ou 20 min.

---

## 4. Bibliothèque d'exercices (tapis seul)

Chaque exercice a 3 niveaux (régression → progression). Tag `bruit` = sauts (exclus en mode silencieux). Tag `jambes` = exclu en mode « Préserver les jambes ».

### Poussée (haut du corps)
| Niv. 1 | Niv. 2 | Niv. 3 |
|---|---|---|
| Pompes genoux | Pompes | Pompes archer |
| Pompes pike genoux | Pompes pike | Pompes pike pieds rapprochés + tempo lent |
| Pompes mains larges genoux | Pompes diamant | Pompes diamant tempo 3-1-3 |
| — | Pompes hindoues | Pompes hindoues + maintien |
| Shoulder taps sur genoux | Planche → pompe (up-downs) | Pompes explosives `bruit` |

### Tirage (le point faible sans barre — on compense)
- Superman Y-T-W (allongé ventre)
- Reverse snow angels
- Superman pulls (tirer coudes vers les hanches, allongé ventre)
- Planche inversée sur les talons (mains au sol derrière)
- Bird dog (stabilité dos)

### Jambes `jambes`
| Niv. 1 | Niv. 2 | Niv. 3 |
|---|---|---|
| Squat au poids du corps | Squat tempo 3-1-1 | Squat pistol assisté (main au sol) / squat cosaque |
| Fente arrière | Fentes alternées | Fentes sautées `bruit` |
| Pont fessier | Pont fessier unijambe | Pont unijambe tempo + maintien |
| Squat sumo pulsé | Squat chaise **sans chaise** (maintien squat 90°, dos libre) | Squat sauté `bruit` |
| Mollets debout | Mollets unijambe | Mollets unijambe tempo |
| Fente latérale | Squat cosaque | Shrimp squat assisté |

### Gainage
- Planche avant (coudes / bras tendus / bras tendus + lever bras)
- Planche latérale (genoux / pieds / + lever jambe)
- Hollow hold (genoux pliés → tendu → hollow rocks)
- Dead bug
- Mountain climbers (lents en mode silencieux)
- Bear crawl sur place / bear hold
- Crunch inversé, V-ups

### Cardio `bruit` (désactivable)
- Jumping jacks (version silencieuse : step jacks)
- High knees (silencieux : marche genoux hauts)
- Burpees (silencieux : burpee sans saut, en reculant les pieds)
- Skater hops (silencieux : fente latérale rapide)

### Échauffement / mobilité
Rotations bras, cat-cow, chien tête en bas ↔ cobra, world's greatest stretch, squat profond tenu, rotations de hanches à 4 pattes, balancements de jambes.

### Retour au calme
Posture de l'enfant, étirement pigeon, étirement ischios assis, quadriceps allongé sur le côté, torsion allongée, cobra.

> Cible : ~50 exercices au total pour la v1. Consignes rédigées par nous (pas d'images copiées) ; icône/emoji ou petit pictogramme SVG simple par catégorie.

---

## 5. Programmation de la semaine

Rotation par défaut (modifiable) :

| Jour | Thème | Format |
|---|---|---|
| Lun | Poussée + gainage | Circuit |
| Mar | Mobilité + jambes légères | Circuit doux |
| Mer | Full body | EMOM |
| Jeu | Tirage (dos) + gainage | Circuit |
| Ven | Full body | Tabata + circuit |
| Sam | Jambes + core (ou mobilité si sortie longue) | Pyramide |
| Dim | Mobilité / récupération active | Flow 15 min |

**Lien avec la course à pied — option « Préserver les jambes »** : activable d'un tap le matin (ou automatiquement sur les jours de course choisis dans les Réglages) → la séance devient haut du corps + tirage + gainage + mobilité, zéro exercice de jambes fatigant (pas de squats, fentes, sauts). Seuls restent des mouvements de mobilité de hanches et un pont fessier léger.

**Règles du générateur** :
- Jamais 2 jours de suite le même groupe principal.
- Pas d'exercice identique deux jours d'affilée.
- Alternance poussée / jambes / gainage dans un circuit (récupération locale).
- Toujours au moins 1 exercice de tirage par semaine sur 2 séances.
- Séance **déterministe pour la date** (graine = date) : même séance si on rouvre l'app le même matin ; bouton « Autre séance » pour en tirer une autre.

---

## 6. Progression adaptative

- Chaque exercice a un **niveau courant** (1–3) et des durées de travail (30 / 40 / 45 s).
- Après chaque séance :
  - **Trop facile** → +5 s de travail ou passage au niveau supérieur après 2 « trop facile » sur un même exercice.
  - **Parfait** → inchangé (+1 compteur ; 3 « parfait » d'affilée → +5 s).
  - **Trop dur** → −5 s ou niveau inférieur.
- Bouton par exercice pendant la séance : « Trop dur → version facile » (bascule immédiate vers le niveau 1).
- Semaine de décharge automatique toutes les 4–5 semaines (volume −30 %).

---

## 7. Données (stockage local, aucun compte)

```js
// exercises.js
{ id: "pushup", name: "Pompes", cat: "push", tags: [],
  levels: [
    { name: "Pompes genoux", cue: "Corps aligné des genoux à la tête" },
    { name: "Pompes", cue: "Coudes à 45°, poitrine au sol" },
    { name: "Pompes archer", cue: "Un bras plié, l'autre tendu sur le côté" }
  ],
  unilateral: false }

// localStorage "callistenik_state"
{ settings: { duration: 20, voice: true, beeps: true, silent: false, runDays: [2,6] },
  levels: { pushup: 2, squat: 2, ... },
  workTime: { pushup: 40, ... },
  history: [ { date: "2026-10-26", theme: "push_core", duration: 1180, feedback: "ok" } ] }
```

- Export / import JSON dans Réglages (sauvegarde manuelle, au cas où).
- Une app ajoutée à l'écran d'accueil iOS garde son propre stockage (pas effacé par Safari).

---

## 8. Pièges iPhone à gérer

| Problème | Solution |
|---|---|
| L'écran se verrouille pendant la séance | **Screen Wake Lock API** (Safari iOS ≥ 16.4) + rappel « garde l'écran allumé » sinon. |
| Minuteur qui dérive / se fige si l'app passe en arrière-plan | Calculer le temps à partir de `Date.now()` (heure de fin), pas en comptant des ticks `setInterval`. |
| Le son ne joue pas | iOS exige un tap avant tout son → débloquer Web Audio + voix sur le bouton « Démarrer ». |
| Bouton silencieux de l'iPhone coupe les bips | `navigator.audioSession.type = "playback"` (Safari 17+) ; sinon prévenir dans l'app. |
| Pas de vibration | `navigator.vibrate` n'existe pas sur iOS → on compte sur son + voix + flash de couleur à l'écran. |
| Voix française | `speechSynthesis` avec voix `fr-FR` (Thomas / Amélie dispo sur iOS). |
| Rappel du matin | Pas de notif simple sans serveur → **Raccourcis iOS > Automatisation > Heure de la journée (ex. 6h45) > Ouvrir l'URL** de l'app (exécution sans confirmation possible). |

---

## 9. Feuille de route

### v0.1 — MVP (1 soirée)
- [x] `index.html` unique : écran Accueil + écran Séance + écran Fin
- [x] ~25 exercices, niveau fixe, 1 format (circuit 40/20)
- [x] Générateur par jour de la semaine
- [x] Minuteur robuste (basé sur l'heure), bips, wake lock
- [x] Publication GitHub Pages → test sur l'iPhone

### v0.2 — Vraie app
- [x] `manifest.json` + icône + `sw.js` (hors-ligne, plein écran)
- [x] Voix FR, pause / passer / ±10 s
- [x] Historique + série 🔥
- [x] Mode silencieux, choix 15/20 min

### v0.3 — Intelligent
- [x] ~60 exercices, 3 niveaux (exercices principaux)
- [x] Feedback de fin → progression adaptative + bouton « version plus facile » en séance
- [x] Formats Tabata (ven.) / Pyramide (mer., sam.) / Circuit adaptatif (autres jours) — EMOM écarté : demande de compter des répétitions
- [x] Mode « Préserver les jambes » (manuel, pour la journée) — auto par jour de course : à faire
- [x] Export / import JSON + suppression d'une séance + remise à zéro des niveaux

### v0.4 — Confort
- [ ] Automatisation Raccourcis iOS du matin
- [ ] Pictogrammes SVG simples par exercice
- [ ] Stats mensuelles

---

## 10. Tests

- Test sur l'iPhone 13 mini réel à chaque version (Safari + app installée).
- Scénarios : écran qui reste allumé 20 min, mode avion (hors-ligne), interruption appel / retour, bouton silencieux activé, séance du même jour rouverte = même séance.
- Vérifier que chaque séance générée dure 15 ou 20 min à ±30 s près (petit test automatique sur 365 dates).

---

## 11. Arborescence finale

```
Callistenik/
├── PLAN.md
├── index.html
├── exercises.js
├── manifest.json
├── sw.js
├── icon-180.png
└── README.md   (comment installer sur l'iPhone)
```
