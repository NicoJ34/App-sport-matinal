# Callistenik — v2.0

Séance matinale de 15–20 min au poids du corps, tapis de sol uniquement.

## Tester tout de suite
Ouvre la version publiée par Claude (lien dans la conversation) dans Safari sur l'iPhone.

## Installer comme une vraie app (GitHub Pages, gratuit)
1. Dépôt : https://github.com/NicoJ34/App-sport-matinal
2. Dépôt → Settings → Pages → Source : `main` / `(root)` → Save.
3. Après ~1 min, l'app est sur `https://nicoj34.github.io/App-sport-matinal/`.
4. Sur l'iPhone, ouvre cette URL dans **Safari** → Partager → **Sur l'écran d'accueil**.

## Rappel automatique le matin
App Raccourcis → Automatisation → **+** → Heure de la journée (ex. 6h45, jours voulus) → **Exécuter immédiatement** → action « Ouvrir les URL » avec l'URL ci-dessus.

## Utilisation
- **Du jour / Full body / Tabata / Étirements** : séance prévue pour le jour, ou au choix un Full body (pyramide), un Tabata ou ~5 min d'étirements après course (+ haut du corps en option) — tous les jours, dimanche compris (choix valable pour la journée).
- **15 / 20 min** : 2 ou 3 tours du circuit (masqué en mode Étirements).
- **🦵 Préserver les jambes** : pour aujourd'hui seulement (jour de course) → pas de squats, fentes, cardio.
- **🤫 Silencieux** : aucun saut (mémorisé).
- **🗣️ Voix** : annonces en français.
- **↻ Autre séance** : en tire une autre pour aujourd'hui.
- Pendant la séance : tap sur l'écran = pause, −10 / +10 s, ⏭ = passer, Quitter (2 taps).
- Si tu n'entends rien : remonte le volume et désactive le mode silencieux de l'iPhone.

## Formats et progression
- **Lun / Mar / Jeu / Dim : Circuit** — effort adaptatif (30 à 45 s) dans des créneaux de 60 s.
- **Mer / Sam : Pyramide** — 30 → 45 s (→ 30 s en 20 min).
- **Ven : Tabata** — blocs de 8 × (20 s / 10 s) en alternant 2 exercices.
- Chaque exercice principal a **3 niveaux** (départ au niveau 2).
- Ressenti en fin de séance : 😌 trop facile ×2 → niveau supérieur (et +5 s en circuit) ; 💪 parfait ×3 → +5 s ; 🥵 trop dur → −5 s puis niveau inférieur. On peut changer d'avis : le dernier choix compte.
- Pendant l'effort : **↓ Version plus facile** baisse le niveau immédiatement.
- **Suivi** : ✕ pour supprimer une séance (2 taps), Progression, Sauvegarder / Restaurer (fichier JSON), remise à zéro des niveaux.

## Strava (v2.0) — envoi automatique
Chaque séance terminée est envoyée sur Strava (type **Workout**, en intérieur) avec le détail : format, échauffement, exercices et niveaux, étirements, puis le ressenti dès que tu le donnes.
1. Sur **strava.com/settings/api**, crée une application : nom libre (ex. Callistenik), site `https://nicoj34.github.io`, **Authorization Callback Domain : `nicoj34.github.io`**.
2. Dans l'app : **Suivi › Strava** → colle le **Client ID** et le **Client Secret** → **Connecter Strava** → autorise.
3. C'est tout : les séances suivantes partent seules. Sans réseau, elles attendent et partent au retour du réseau.
- Les identifiants restent sur le téléphone (jamais dans le dépôt ni dans la sauvegarde JSON).
- Si le retour de Strava s'ouvre hors de l'app : connecte-toi là, touche **Copier le code**, puis colle-le dans l'app (« coller un code de connexion »).
- Supprimer une séance dans le Suivi ne la supprime pas sur Strava.

## Pour tester sur ordinateur
`index.html?fast=20` accélère le minuteur ×20 ; `index.html?date=2026-10-31` affiche la séance d'un autre jour.
