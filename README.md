# TP2 – GitHub Actions (Python)

**Nom :** ElMahjoubi Aymane  
**Dépôt GitHub :** TP2-ElMahjoubiAymane

---
## 🎯 Objectif du TP

Ce TP a pour but de mettre en place un workflow d’intégration continue (CI) à l’aide de GitHub Actions.

L’objectif est de :
- créer un dépôt GitHub conforme aux consignes,
- assurer que le projet Python compile sans erreur,
- configurer un workflow GitHub Actions,
- exécuter automatiquement les tests unitaires,
- ajouter des captures d’écran dans le README,
- rédiger un petit rapport décrivant le travail réalisé.

---
## 📁 Structure du projet

Le projet est organisé de la manière suivante :

TP2-ElMahjoubiAymane/
├── app.py
├── init.py
├── requirements.txt
├── README.md
├── rapport_TP2.md
├── tests/
│ ├── test_app.py
│ └── init.py
└── .github/
└── workflows/
└── python-ci.yml
---
## ⚙️ Workflow GitHub Actions

Le fichier suivant permet d’exécuter automatiquement les tests unitaires à chaque **push** ou **pull request** sur la branche `main`.

Voici le contenu du workflow :

```yaml
name: Python CI

on:
  push:
    branches: [ "main" ]
  pull_request:
    branches: [ "main" ]

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v3

      - name: Set up Python
        uses: actions/setup-python@v4
        with:
          python-version: "3.10"

      - name: Install dependencies
        run: |
          pip install -r requirements.txt

      - name: Add project root to PYTHONPATH
        run: echo "PYTHONPATH=$GITHUB_WORKSPACE" >> $GITHUB_ENV

      - name: Run tests
        run: pytest


## 🧪 Tests unitaires

Les tests unitaires permettent de vérifier automatiquement le bon fonctionnement du projet.  
Voici un exemple de test présent dans le fichier `tests/test_app.py` :

```python
from app import add

def test_add():
    assert add(2, 2) == 4
## 📸 Captures d’écran

Voici quelques captures illustrant l'exécution du workflow et du projet :

### ✔️ Workflow GitHub Actions réussi 
![Workflow réussi](captures/workflow.png)
