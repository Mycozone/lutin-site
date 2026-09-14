# lutin-site

Landing page de **Lutin** — carnet de cueillette mycologique.
En ligne sur [lelutin.app](https://lelutin.app).

## Déploiement

Hébergé sur Vercel, relié à ce dépôt. **Tout commit sur `main` déclenche un
redéploiement automatique.** Rien à faire d'autre : ni bascule de domaine,
ni recréation de projet.

Site statique : aucune compilation, aucune dépendance, aucun outil de build.

## Fichiers

| Fichier | Rôle |
|---|---|
| `index.html` | La landing complète — CSS et JS inclus dans le fichier |
| `mentions-legales.html` | Éditeur, hébergeur, avertissement mycologique |
| `confidentialite.html` | RGPD : finalité, base légale, sous-traitants, droits |
| `ecran-accueil.jpg` | Capture de l'accueil de l'app, pour le hero |
| `fig-pluie.jpg` `fig-terrain.jpg` `fig-carnet.jpg` | Captures recadrées des trois blocs de valeur |
| `calque-*.jpg` | Les quatre calques de carte, pour le carrousel |
| `lutin-apple-touch-180.png` | Icône iOS |

## Points techniques à connaître avant modification

**Le logo n'est pas un fichier.** Il est défini une seule fois en `<symbol id="lutin">`
au début du `<body>`, puis appelé par `<use href="#lutin"/>` à quatre endroits :
en-tête (40 px), section bêta (38 px), section crème (46 px), pied de page (36 px).
Il hérite de `currentColor`, donc `color:var(--gold)` suffit à le teinter.
La section crème bascule automatiquement en or profond via l'override de `--gold`.

En dessous de 40 px, les yeux et le sourire du glyphe ne font plus qu'un pixel :
ne pas réduire les tailles actuelles.

**Le fond** combine trois halos en dégradé radial, un filet lumineux, un grain
`feTurbulence` en mode `overlay`, et un réseau mycélien SVG à 55 % d'opacité.
Les tracés du mycélium sont dans un `<defs>` et référencés deux fois par `<use>`
— hero et section bêta — pour ne stocker la géométrie qu'une fois.

**Le formulaire bêta** est un popup Tally, identifiant `yPab6d`. Un repli est prévu :
si un bloqueur empêche le chargement du script, le bouton ouvre `tally.so/r/yPab6d`
dans un nouvel onglet.

**Les grilles** utilisent `minmax(0,1fr)` et non `1fr`. C'est nécessaire : sans cela,
les images à attribut `width` empêchent les colonnes de rétrécir et la page déborde
horizontalement.

## Sources des données citées

Open-Meteo (AROME HD), IGN (Plan IGN, BD Forêt v2), INRAE (carte des sols) —
données publiques sous Licence Ouverte Etalab.
