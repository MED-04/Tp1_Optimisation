# TP optimisation NumPy — mode d'emploi (VS Code)

## Structure
    tp_optimisation/
      data/            <- CSV (les 3 fournis + Diabetes/Iris/Wine complétés) ; les .npz images viennent avec 00_donnees
      notebooks/       <- 00_donnees, 01_regression, 02_classification, 03_clustering (.ipynb, autonomes)
      rapport.tex      <- rapport LaTeX (les \todo en rouge sont à compléter)
      *.py             <- mêmes codes en scripts (facultatif : python ex1_regression.py ...)

## 1. Installation (terminal VS Code)
    python -m venv .venv
    .venv\Scripts\activate          # Windows   (Linux/Mac : source .venv/bin/activate)
    pip install -r requirements.txt ipykernel
Extensions VS Code : *Python* et *Jupyter*. Ouvrir le dossier `tp_optimisation`, ouvrir un notebook,
choisir le kernel `.venv` (en haut à droite), puis **Run All**.

## 2. Ordre d'exécution
1. `00_donnees.ipynb` : vérifie `data/`, télécharge MNIST et Fashion-MNIST (OpenML, Internet, quelques minutes)
   -> crée `data/mnist_50k_10k_10k.npz` et `data/fashion_mnist_50k_10k_10k.npz`. Les fichiers existants ne sont jamais écrasés.
2. `01_regression.ipynb` (~2-5 min)
3. `02_classification.ipynb` (CSV ~2 min ; chaque jeu d'images peut prendre 10-40 min sur CPU)
4. `03_clustering.ipynb` (CSV < 1 min ; images ~5-20 min chacun)
Chaque notebook a une cellule de configuration (budget d'époques, `fast=5000` pour tester vite sur les images).
Si les .npz manquent, 02 et 03 ignorent les images et le disent.

## 3. Sorties
Chaque notebook écrit dans `notebooks/results/` (tableaux .csv/.tex, résultats bruts, figures) et crée `results.zip`.
Le zip du notebook 03 contient tout : c'est lui qu'il faut renvoyer pour compléter le rapport.

## 4. Rapport
    pdflatex rapport.tex   (deux fois)
Copier `notebooks/results/` à côté de `rapport.tex` (ou lancer pdflatex depuis `notebooks/` avec le .tex copié).
