# Popularité des langages de programmation sur Stack Overflow

Ce projet étudie l’évolution de la popularité des langages et technologies sur Stack Overflow, avec un intérêt particulier pour le langage **R**. L’analyse est réalisée en R dans le notebook [`notebook.ipynb`](notebook.ipynb).

## Contenu du projet

| Fichier | Rôle |
|---|---|
| [`notebook.ipynb`](notebook.ipynb) | Analyse, calculs et visualisations en R |
| [`stack_overflow_data.csv`](stack_overflow_data.csv) | Jeu de données utilisé par le notebook : une ligne par tag et par année |
| [`by_tag_year.csv`](by_tag_year.csv) | Jeu de données alternatif contenant les colonnes `year`, `tag`, `number` et `year_total` ; il n’est pas utilisé directement par le notebook actuel |
| [`prog_lang.jpg`](prog_lang.jpg) | Image affichée en introduction du notebook |

## Analyse réalisée

Le notebook :

1. charge les données de `stack_overflow_data.csv` ;
2. affiche un aperçu des premières lignes ;
3. calcule la part des questions associées au tag `r` chaque année et affiche son évolution ;
4. affiche la part de R en 2020 ;
5. identifie les cinq tags ayant reçu le plus de questions entre 2015 et 2020 ;
6. compare leur évolution en pourcentage au moyen d’un graphique.

Les colonnes principales de `stack_overflow_data.csv` sont :

| Colonne | Description |
|---|---|
| `year` | Année de la question, de 2008 à 2020 |
| `tag` | Tag Stack Overflow associé à la question |
| `num_questions` | Nombre de questions portant ce tag pour l’année concernée |
| `year_total` | Nombre total de questions posées cette année-là |

## Exécution locale avec JupyterLab

Cette méthode permet d’exécuter directement le fichier `.ipynb`, sans Google Colab.

### 1. Installer R et les dépendances

R doit être installé sur la machine. Depuis un terminal, lancer R puis exécuter :

```r
install.packages(c("readr", "dplyr", "ggplot2"))
install.packages("IRkernel")
IRkernel::installspec(user = TRUE)
```

### 2. Installer JupyterLab

Si Jupyter n’est pas encore installé :

```bash
python3 -m pip install jupyterlab
```

### 3. Démarrer le notebook

Dans le dossier du projet :

```bash
jupyter lab
```

Une page s’ouvrira dans le navigateur. Ouvrir `notebook.ipynb`, vérifier que le kernel **R** est sélectionné, puis utiliser **Run All** ou exécuter les cellules une par une.

Les fichiers CSV et l’image doivent rester dans le même dossier que le notebook, car le code utilise des chemins relatifs comme `stack_overflow_data.csv` et `prog_lang.jpg`.

## Exécution avec Google Colab

Le projet peut également être exécuté dans Google Colab, sans installer R ni JupyterLab sur l’ordinateur.

1. Ouvrir [Google Colab](https://colab.research.google.com/).
2. Aller dans **Fichier → Importer un notebook**.
3. Sélectionner `notebook.ipynb` depuis l’ordinateur, ou importer le notebook depuis GitHub.
4. Dans Colab, sélectionner **Exécution → Exécuter toutes les cellules**.

Pour que le notebook trouve les données, importer également les fichiers suivants dans l’espace de travail Colab :

- `stack_overflow_data.csv`
- `prog_lang.jpg`

Pour les importer, utiliser l’icône de dossier à gauche dans Colab, puis l’icône d’envoi de fichiers. Les fichiers doivent être placés dans le même dossier de travail que le notebook. Si Colab demande de choisir un kernel, sélectionner un environnement **R**.

> Remarque : selon la configuration de Colab, le support du kernel R peut nécessiter une configuration supplémentaire. L’exécution locale avec JupyterLab et `IRkernel` reste la méthode la plus directement compatible avec ce notebook R.

## Exécution avec RStudio

RStudio est pratique pour modifier et analyser le code R, mais ce fichier est un notebook Jupyter (`.ipynb`). Pour l’exécuter de manière fiable dans RStudio :

1. installer les packages R avec la commande ci-dessus ;
2. créer un fichier R, par exemple `analyse.R` ;
3. y copier les cellules de code du notebook ;
4. placer `analyse.R` dans le dossier du projet ;
5. ouvrir le fichier dans RStudio et exécuter le code.

Le répertoire de travail doit être le dossier du projet. Dans RStudio, on peut le définir avec :

```r
setwd("chemin/vers/Manipulation de donnée avec R")
```

Une autre possibilité consiste à ouvrir le notebook avec JupyterLab tout en utilisant RStudio uniquement pour éditer les fichiers R.

## Exécution en ligne de commande

Pour vérifier que les packages sont installés :

```bash
Rscript -e 'library(readr); library(dplyr); library(ggplot2); print("Dépendances OK")'
```

Le notebook reste toutefois le format principal du projet, car il contient les graphiques et les résultats affichés cellule par cellule.

## Remarques

- Les données sont déjà présentes dans le dépôt : aucun téléchargement supplémentaire n’est nécessaire pour reproduire l’analyse.
- Le fichier `stack_overflow_data.csv` contient environ 420 000 lignes ; son chargement peut prendre quelques secondes.
- Les graphiques sont générés avec `ggplot2` et s’affichent directement dans JupyterLab.
- Les données couvrent la période 2008–2020 ; les résultats ne décrivent donc pas nécessairement la popularité actuelle des langages.

