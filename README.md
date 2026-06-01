# 🫀 Corps humain 3D — Atlas anatomique complet

Page statique : un atlas 3D de **tout le corps humain** (~2234 structures réelles
issues de BodyParts3D), explorable au doigt/à la souris, avec **filtres**.

## Contenu — 11 systèmes, ~2234 structures

| Système | Pièces | Fichier |
|---|---|---|
| 💪 Muscles | 418 | `muscular.glb` |
| 🦴 Squelette | 249 | `skeletal.glb` |
| 🧠 Nerveux (encéphale, œil, nerfs crâniens) | 173 | `nervous.glb` |
| ❤️ Cardiovasculaire (cœur + arbre vasculaire) | 1065 | `cardiovascular.glb` |
| 🫁 Respiratoire (voies aériennes, larynx) | 144 | `respiratory.glb` |
| 🍽️ Digestif | 152 | `digestive.glb` |
| 💧 Urinaire | 6 | `urinary.glb` |
| ⚧ Reproducteur (masculin) | 12 | `reproductive.glb` |
| 🧬 Endocrinien | 4 | `endocrine.glb` |
| 🛡️ Lymphatique | 2 | `lymphatic.glb` |
| 🧴 Tégument (peau) | 9 | `integumentary.glb` |

Chaque structure est **cliquable individuellement**, avec un **nom français**
(traduit automatiquement) et son **nom scientifique** (latin/anglais, exact).
Les données sont dans `systems.json` (généré).

## Filtres

- **Par système** : chips en haut, superposables + bouton **✦ Tout** (tout afficher/masquer).
- **Par région du corps** : Tête, Cou, Thorax, Abdomen, Bassin, Membres… (2ᵉ rangée de chips).
- **Recherche globale** : cherche dans **tous** les systèmes à la fois (FR + scientifique) ;
  un résultat charge et affiche son système automatiquement.
- **Transparence / écorché** : curseur d'opacité **par système** (dans l'en-tête de chaque
  système dans la liste) pour voir à travers.

## Rendu

Three.js : éclairage d'environnement, tone mapping, contour lumineux sur la sélection
(desktop), ombre de contact, fond dégradé. Chargement **à la demande** par système
(le 1ᵉʳ écran ne charge que les muscles). Tous les systèmes partagent le même repère,
donc s'alignent parfaitement.

## Lancer en local

Les modèles sont des fichiers `.glb` → il faut un serveur (les navigateurs bloquent
`file://`) :

```bash
cd corps-humain
python3 -m http.server 8000   # http://localhost:8000
```

Sur GitHub Pages, aucun serveur : ça marche directement.

## Limites du jeu de données (BodyParts3D)

- « Nerveux » = encéphale + nerfs crâniens/œil (pas de nerfs périphériques).
- « Respiratoire » = voies aériennes + larynx (pas de parenchyme pulmonaire).
- « Reproducteur » = anatomie masculine uniquement.
- Noms FR du long tail (micro-vaisseaux, sous-parties) parfois approximatifs ;
  le nom scientifique affiché reste exact.

## Crédits & licence

Géométrie : **BodyParts3D**, © The Database Center for Life Science (DBCLS),
**CC-BY-SA 2.1 Japan**. Les `.glb` sont des dérivés (sélection, fusion, simplification,
compression Draco) sous la même licence. Données via le dépôt
[`jixiangying/anatomy`](https://github.com/jixiangying/anatomy).
