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

Ouvrir `index.html` dans un navigateur. Rien à installer.

La page suit le calendrier réel : chaque jour porte sa date, les flèches ‹ ›
passent d'une semaine à l'autre, **Aujourd'hui** revient à la semaine en cours.
L'alternance A / B se déduit du calendrier une fois la semaine de référence
indiquée dans les options.

- **Bandeau du moment**, en haut : le cours en cours, le suivant, et surtout le
  **temps restant** en gros à droite — avant la fin du cours, avant la reprise
  pendant la pause méridienne, ou avant le prochain cours pendant une
  récréation. Le compte à rebours et les barres de progression se mettent à jour
  chaque seconde, sans recharger la page.
- Le créneau du moment est entouré d'un **halo qui scintille doucement**, dans la
  grille comme dans la vue jour, et la case rappelle le temps restant.
- La page **surveille le dépôt** : une publication faite depuis un autre
  appareil arrive d'elle-même en moins d'une minute, et au retour sur l'onglet.
  Un bandeau le signale. Si des modifications locales ne sont pas publiées, rien
  n'est écrasé : la page prévient et attend.
- **Vacances et jours fériés** (zone A, académie de Bordeaux) : les journées
  concernées apparaissent grisées avec leur libellé, et le bandeau annonce la
  date de reprise.
- **Affaires**, dans la barre : ce qu'il faut préparer pour le prochain jour de
  classe, matière par matière, avec le nombre d'affaires en pastille. La liste
  par matière se modifie depuis le même panneau.
- Une fois le dernier cours passé, le bandeau annonce « journée terminée » et
  la reprise : premier cours, heure, professeur, salle, avec un **décompte
  jusqu'à ce premier cours** — en jours quand la reprise est lointaine. La vue
  jour par jour bascule alors sur cette journée, marquée « prochaine journée »,
  au besoin sur la semaine suivante. Les vacances et les jours fériés sont
  sautés au passage.
- Le **groupe choisi est mémorisé**, comme la semaine de référence : la page
  rouvre sur le vôtre.
- **Semaine entière / jour par jour**, **groupe A / B**, et un thème
  **auto / clair / sombre** — « auto » suit le réglage du téléphone ou de
  l'ordinateur et bascule en direct.
- Sur ordinateur, la semaine entière tient dans l'écran, sans défilement. Sur
  téléphone, la grille tient dans la largeur, les intitulés passent en abrégé.
- Un cours d'une semaine sur deux porte le repère « sem. A / B », un cours
  dédoublé « gr. A / B ». Les cases libres indiquent ce qui s'y tient l'autre
  semaine ou pour l'autre groupe.

## Changements ponctuels

**Options › Changements ponctuels** enregistre, à une date précise, un cours
annulé, un cours remplacé (autre matière, autre salle) ou un cours ajouté. La
grille de base n'est pas touchée : seule la date concernée change, et la case
porte alors la mention « annulé », « remplacé » ou « ajouté ». Ces changements
sont publiés avec le reste et se retirent d'un clic.

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
