# Mascotte — Théodore & Giulia

Système de récompense maison pour les enfants. Une mascotte, des étoiles à gagner chaque jour, un cadeau au bout de 180 jours.

## Stack

HTML/CSS/JS pur, zéro dépendance, zéro build. Stockage `localStorage` (par appareil/navigateur).

## Lancer en local

```sh
cd ~/Code/mascotte-recompenses
python3 -m http.server 8000
```

Puis ouvrir http://localhost:8000

## Déploiement

Hébergé sur **Cloudflare Pages**, déployé sur `https://mascotte.screenplayeditor.app`.

Le déploiement est automatique sur chaque push sur `main` (via l'intégration GitHub de Cloudflare Pages).

```sh
git push origin main
```

## Installation sur l'écran d'accueil iPad/iPhone

Les meta tags PWA (`apple-mobile-web-app-capable`, manifest, icônes) permettent d'installer le site comme une app :

1. Ouvrir le site dans Safari
2. Bouton "Partager" → "Sur l'écran d'accueil"
3. L'icône Mascotte apparaît, l'app s'ouvre en plein écran

## Améliorations possibles

- **Synchro entre appareils** : actuellement chaque appareil a son propre `localStorage`. Pour partager les progrès entre l'iPad de Théodore et celui de Giulia (ou avec le téléphone parent), il faudrait un backend léger (Cloudflare KV ou D1, ou Firebase).
- **Service worker** : pour faire fonctionner l'app offline. Pas encore implémenté.
- **Mascotte image en fichier séparé** : actuellement la même image base64 est embarquée 4 fois dans le HTML (~400 Ko inutiles). La sortir dans un `mascotte.jpg` réduirait le HTML d'environ 75%.
- **Sons / vibrations** : sur les récompenses, ajouter un petit son et `navigator.vibrate()` sur mobile.
- **Notifications push** : rappel du soir si l'enfant n'a pas encore validé sa journée.
- **Mode parent protégé** : actuellement l'espace parent est accessible sans mot de passe. Un code PIN à 4 chiffres serait plus sûr.
