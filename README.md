# Emploi du temps — 1ST2S1

Emploi du temps personnel : groupe A par défaut, les deux alternances de
semaine, le groupe B consultable en option.
Une page HTML autonome, sans dépendance ni connexion.

```
edt-1st2s1/
├── index.html   la page à ouvrir
├── data.js      le contenu de l'emploi du temps (seul fichier à corriger)
└── README.md
```

## Consulter

Ouvrir `index.html` dans un navigateur, directement depuis le dossier.
Rien à installer.

Quatre sélecteurs en haut de page : **semaine A / B**, **semaine entière /
jour par jour**, **groupe A / B** et **thème clair / sombre**. Le thème suit
d'abord celui du système, puis votre choix, gardé d'une visite à l'autre.

- Sur ordinateur, la semaine entière tient dans l'écran : ni défilement
  horizontal, ni vertical. Sur téléphone, la grille tient dans la largeur, les
  intitulés passent en abrégé (BPH, Maths, EMC…) et la vue jour par jour reste
  le confort de lecture.
- Un cours qui ne revient qu'une semaine sur deux porte le repère « sem. A »
  ou « sem. B » ; un cours dédoublé porte « gr. A » ou « gr. B ». Les cases
  libres indiquent ce qui s'y tient l'autre semaine ou pour l'autre groupe.
- Les créneaux sans cours restent visibles, marqués « Libre », et la pause
  méridienne coupe la journée.
- La page se cale sur le moment présent : le jour courant est encadré et porte
  la mention « aujourd'hui », l'heure en cours est surlignée dans les deux vues,
  et la vue jour par jour s'ouvre directement sur la bonne journée. Le week-end,
  c'est le lundi qui est visé, sous la mention « prochain jour ». Le bouton
  **Aujourd'hui** y ramène à tout moment, et les repères se remettent à l'heure
  chaque minute.
- **Options › Semaine en cours** : indiquez une fois si la semaine qui commence
  est A ou B. La page ouvre ensuite d'elle-même la bonne semaine, en suivant
  l'alternance du calendrier, et l'indique à côté du titre.
- Le bouton **Options**, à droite de la barre, déplie le récapitulatif des
  enseignements, le mode modification, la publication sur GitHub, le
  téléchargement, l'impression et la légende des couleurs.

## Corriger

1. Ouvrir **Options**, puis **Mode modification › Activer**.
2. Écrire directement dans les cases : matière, professeur, salle, note.
3. Sur une case vide : **+ Ajouter un cours**. Sur une case remplie : changer la
   matière (couleur), passer de 1 h à 2 h, ou supprimer.
4. Les corrections sont gardées sur l'appareil au fil de la saisie ; un bandeau
   rappelle qu'elles ne sont pas encore publiées.

Le mode modification agit sur le groupe et la semaine affichés : corriger une
case en groupe B ne touche pas le groupe A.

## Publier depuis la page

**Options › Publier sur GitHub** écrit les corrections dans le dépôt, sans
téléchargement ni manipulation de fichier.

1. Sur GitHub, créer un jeton à portée fine : *Settings › Developer settings ›
   Personal access tokens › Fine-grained tokens*. Le limiter à ce seul dépôt,
   permission **Contents : Read and write**, avec une date d'expiration.
2. Dans **Réglages**, renseigner le dépôt (`utilisateur/edt-1st2s1`), la
   branche, le fichier à mettre à jour et le jeton, puis **Mémoriser**.
3. **Publier maintenant** crée un commit avec le contenu à jour.

Le jeton reste dans le stockage local du navigateur : il n'est écrit ni dans
`data.js`, ni dans la page exportée. **Oublier le jeton** l'efface. Un jeton
saisi sur un appareil partagé devrait être révoqué depuis GitHub après usage.

Si la publication échoue alors que la page est ouverte depuis un fichier local,
c'est le navigateur qui bloque l'appel : ouvrir la page depuis une adresse web
(Netlify, Cloudflare Pages) règle le problème. Le téléchargement manuel reste
disponible dans tous les cas.

## Mettre en ligne sur GitHub Pages

```bash
cd edt-1st2s1
git init
git add .
git commit -m "Emploi du temps 1ST2S1"
gh repo create edt-1st2s1 --public --source=. --push
```

Puis, dans le dépôt : **Settings › Pages › Build and deployment**, source
*Deploy from a branch*, branche `main`, dossier `/ (root)`. Une minute plus
tard, la page est à l'adresse `https://<utilisateur>.github.io/edt-1st2s1/`.
Le fichier unique reste accessible en ajoutant `emploi-du-temps-1ST2S1.html`
à cette adresse.

Sur iPhone comme sur Android, « Ajouter à l'écran d'accueil » depuis le
navigateur donne une icône qui ouvre l'emploi du temps en plein écran.

Après une publication depuis la page, `data.js` est rechargé avec un paramètre
unique : la nouvelle version s'affiche sans vider le cache. Le CDN de GitHub
met environ une minute à se mettre à jour.

### À propos de la confidentialité

GitHub Pages n'est proposé qu'à partir d'un dépôt public sur le plan gratuit.
Avec GitHub Pro, le dépôt peut rester privé, mais **le site publié reste
public** : seul GitHub Enterprise Cloud sait protéger une page par
authentification. Dans tous les cas, quiconque connaît l'adresse peut lire
l'emploi du temps — il contient le nom de l'établissement, la classe et les
professeurs, pas d'information personnelle vous concernant.

Si cela ne convient pas, deux solutions gardent une adresse web privée :
Netlify ou Cloudflare Pages déploient un dépôt privé avec mot de passe. Le
dossier peut aussi rester dans un cloud personnel, ou le fichier unique être
simplement gardé sur le téléphone.

## Version en fichier unique

`emploi-du-temps-1ST2S1.html` contient tout : la page et les données.
Il s'ouvre seul, sans le reste du dossier — pratique pour vérifier ou envoyer
par message, avant tout dépôt sur GitHub. Son bouton « Enregistrer une copie »
télécharge une nouvelle version du fichier avec vos corrections à l'intérieur.

Les deux fichiers partent des mêmes données. Si vous corrigez dans la version
unique, reportez `data.js` (ou remplacez simplement les deux fichiers) pour que
le dépôt reste à jour.
