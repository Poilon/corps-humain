# 🫀 Corps humain 3D — Atlas musculaire interactif

Page statique : un **vrai modèle anatomique 3D** du système musculaire, que tu peux
faire tourner et zoomer, et dont chaque muscle est cliquable pour afficher son **nom
français**, son **nom scientifique (latin)** et son **rôle**.

![aperçu](#)

## Ce que ça contient

- **Modèle anatomique réel** : ~190 maillages issus de **BodyParts3D** (segmentation
  anatomique réelle), regroupés en **52 muscles** nommés, classés par région
  (cou, épaule, dos, poitrine, abdomen, bras, avant-bras, hanche & fessiers, cuisse, jambe).
- Tout est fusionné dans un seul fichier **`muscles.glb`** (~1,6 Mo, compressé Draco).
- Rendu **Three.js** : éclairage d'environnement, tone mapping, contour lumineux sur
  sélection, ombre de contact, fond dégradé.
- Liste latérale avec **recherche**, boutons **vue avant / arrière**, **rotation auto**,
  **transparence** (met en valeur le muscle survolé/sélectionné), **recentrer**.

> ℹ️ Deux muscles (**grand droit de l'abdomen** et **grand dorsal**) sont absents du
> jeu de données BodyParts3D : ils sont **approximés** (forme reconstruite et placée
> d'après les muscles voisins). Ils sont signalés « forme approximée » dans la fiche.

## Lancer en local

⚠️ Cette version charge un fichier 3D (`muscles.glb`). Les navigateurs **bloquent la
lecture de fichiers locaux** quand on ouvre le HTML en double-cliquant (`file://`).
Il faut donc un petit serveur local :

```bash
cd corps-humain
python3 -m http.server 8000
# puis ouvre http://localhost:8000
```

(Sur GitHub Pages, aucun serveur à lancer : tout fonctionne directement.)

## Déploiement sur GitHub Pages

```bash
git init
git add .
git commit -m "Corps humain 3D — atlas musculaire"
git branch -M main
git remote add origin https://github.com/Poilon/corps-humain.git
git push -u origin main
```

Puis **Settings → Pages → Deploy from a branch → `main` / `/(root)`**.
Le site sera en ligne sur :

```
https://poilon.github.io/corps-humain/
```

(Si tu nommes le repo `poilon.github.io`, il sort à la racine `https://poilon.github.io/`.)
Le fichier `.nojekyll` est présent pour servir les fichiers tels quels.

## Commandes (souris)

| Action          | Comment                          |
|-----------------|----------------------------------|
| Tourner autour  | Glisser (bouton gauche)          |
| Zoomer          | Molette                          |
| Déplacer        | Glisser (bouton droit)           |
| Sélectionner    | Cliquer un muscle (ou la liste)  |
| Transparence    | Bouton « Transparence »          |

## Crédits & licence du modèle

Géométrie anatomique : **BodyParts3D**, © The Database Center for Life Science (DBCLS),
sous licence **CC-BY-SA 2.1 Japan**. Le fichier `muscles.glb` est un dérivé (sélection,
fusion, simplification) et reste sous la même licence **CC-BY-SA**. Merci de conserver
l'attribution affichée en bas de la page si tu réutilises le modèle.

Données récupérées via le dépôt open-source
[`jixiangying/anatomy`](https://github.com/jixiangying/anatomy).

## Étendre / modifier

- Le contenu des fiches (noms FR, latin, rôles, région) est dans l'objet `DATA` en haut
  du `<script>` de `index.html`, indexé par identifiant de muscle.
- Pour ajouter d'autres muscles, il faut régénérer `muscles.glb` à partir des OBJ
  BodyParts3D (le pipeline : téléchargement des OBJ → fusion en GLB nommé →
  `gltf-transform simplify` + `draco`).
