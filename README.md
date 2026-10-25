# Callistenik — v0.3

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
- **15 / 20 min** : 2 ou 3 tours du circuit.
- **🦵 Préserver les jambes** : pour aujourd'hui seulement (jour de course) → pas de squats, fentes, cardio.
- **🤫 Silencieux** : aucun saut (mémorisé).
- **🗣️ Voix** : annonces en français.
- **↻ Autre séance** : en tire une autre pour aujourd'hui.
- Pendant la séance : tap sur l'écran = pause, −10 / +10 s, ⏭ = passer, Quitter (2 taps).
- Si tu n'entends rien : remonte le volume et désactive le mode silencieux de l'iPhone.

## Formats et progression (v0.3)
- **Lun / Mar / Jeu / Dim : Circuit** — effort adaptatif (30 à 45 s) dans des créneaux de 60 s.
- **Mer / Sam : Pyramide** — 30 → 45 s (→ 30 s en 20 min).
- **Ven : Tabata** — blocs de 8 × (20 s / 10 s) en alternant 2 exercices.
- Chaque exercice principal a **3 niveaux** (départ au niveau 2).
- Ressenti en fin de séance : 😌 trop facile ×2 → niveau supérieur (et +5 s en circuit) ; 💪 parfait ×3 → +5 s ; 🥵 trop dur → −5 s puis niveau inférieur. On peut changer d'avis : le dernier choix compte.
- Pendant l'effort : **↓ Version plus facile** baisse le niveau immédiatement.
- **Suivi** : ✕ pour supprimer une séance (2 taps), Progression, Sauvegarder / Restaurer (fichier JSON), remise à zéro des niveaux.

## Pour tester sur ordinateur
`index.html?fast=20` accélère le minuteur ×20 ; `index.html?date=2026-10-31` affiche la séance d'un autre jour.
