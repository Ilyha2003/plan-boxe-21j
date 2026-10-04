# 21 Jours Avant le Club

Application web autonome : le programme de boxe sur 21 jours, installable sur le téléphone et utilisable hors ligne.

## Mettre en ligne sur GitHub Pages

1. Sur [github.com/new](https://github.com/new), crée un dépôt nommé `plan-boxe-21j`. Laisse-le **public** (GitHub Pages n'accepte les dépôts privés que sur les offres payantes).
2. Sur la page du dépôt vide, clique **uploading an existing file**, puis dépose **tous** les fichiers de ce dossier — `index.html`, `manifest.webmanifest`, `sw.js`, les trois `.png`, `.nojekyll` et ce `README.md`. Commit.
3. Onglet **Settings** → **Pages** (menu de gauche). Sous *Build and deployment*, choisis **Deploy from a branch**, branche `main`, dossier `/ (root)`. Save.
4. Attends une à deux minutes. L'adresse apparaît en haut de la page Pages : `https://<ton-pseudo>.github.io/plan-boxe-21j/`.

En ligne de commande, si tu préfères :

```bash
cd plan-boxe-21j
git init -b main
git add -A
git commit -m "Plan boxe 21 jours"
git remote add origin https://github.com/<ton-pseudo>/plan-boxe-21j.git
git push -u origin main
```

Puis l'étape 3 ci-dessus dans l'interface GitHub.

## Installer sur le téléphone

Ouvre l'adresse `https://<ton-pseudo>.github.io/plan-boxe-21j/` dans le navigateur du téléphone.

- **iPhone (Safari)** : bouton Partager → *Sur l'écran d'accueil*. Safari n'installe une application web que depuis Safari, pas depuis Chrome.
- **Android (Chrome)** : menu ⋮ → *Installer l'application* (ou *Ajouter à l'écran d'accueil*).

L'icône apparaît alors comme une vraie application, sans barre d'adresse. Après la première ouverture, tout fonctionne sans connexion : les fichiers sont mis en cache par `sw.js`. Seules les vidéos YouTube demandent évidemment du réseau.

## Où va ta progression

Les séances cochées, la date de départ et le journal de poids sont enregistrés dans le **stockage local du navigateur**, sur l'appareil où tu utilises l'application. Conséquences à connaître :

- Rien ne part sur un serveur. Personne d'autre ne voit tes données, et le dépôt GitHub public ne les contient pas.
- Les données ne se synchronisent **pas** entre ton téléphone et ton ordinateur : chaque appareil a son propre suivi.
- Vider les données de navigation du site effacerait le suivi. Le bouton **Sauvegarder le suivi**, à côté du formulaire de pesée, télécharge un fichier JSON de secours.

Le dépôt étant public, la page elle-même (donc le poids de départ de 83,5 kg et l'objectif) est lisible par qui a l'adresse. Si ça te gêne, remplace ces valeurs dans `index.html` avant de publier, ou héberge le dossier ailleurs — un glisser-déposer sur [app.netlify.com/drop](https://app.netlify.com/drop) donne une adresse privée en quelques secondes, sans dépôt public.

## Modifier le contenu

Tout est dans `index.html`, sans dépendance à installer.

- Le détail des 21 jours : tableau `DAYS` (type de séance, point technique, vidéo).
- La charge par semaine : tableau `WEEKS` (durée de corde, nombre de rounds, intervalles, objectifs).
- Les circuits A, B et C : objet `CIRCUITS`, une entrée par semaine.
- L'assiette et les chiffres : directement dans le HTML, section *L'assiette*.

Après une modification, pense à incrémenter `CACHE` dans `sw.js` (`plan-boxe-21j-v1` → `-v2`), sinon les téléphones qui ont déjà installé l'application continueront à servir l'ancienne version depuis leur cache.
