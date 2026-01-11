# Livrables du Lab MLOps : Lab 3 – Versionnement des données et pipelines ML avec DVC

## Compte Rendu  
**Réalisé par : Fahd El Attar**

Ce laboratoire a pour objectif d’introduire **DVC (Data Version Control)** afin de :
- Versionner les datasets sans alourdir Git
- Mettre en place un remote de stockage
- Construire un pipeline ML reproductible
- Garantir la traçabilité et la reproductibilité des expériences

---

## Étape 1 : Initialisation de DVC dans le projet

Ouvrir un terminal dans le dossier du projet :

![Terminal project folder](screenshots/image1.png)

Initialiser DVC :

![DVC init](screenshots/image2.png)

Vérifier les fichiers créés :

![DVC files created](screenshots/image3.png)

---

## Étape 2 : Versionner les données brutes avec DVC

Versionner le dataset généré dans le lab précédent :

![DVC add raw data](screenshots/image4.png)

Afficher le contenu du dossier `data/` :

![Data folder](screenshots/image5.png)

Ajouter les fichiers nécessaires au versionnement Git :

![Git add dvc files](screenshots/image6.png)

### Résultat attendu
- `data/raw.csv` n’est plus suivi par Git
- Seul `raw.csv.dvc` est versionné
- Git reste léger, DVC gère les gros fichiers

---

## Étape 3 : Configuration d’un remote DVC

Créer un dossier pour le stockage distant :

![Create remote folder](screenshots/image7.png)

Déclarer le dossier comme remote principal :

![DVC remote add](screenshots/image8.png)

Versionner la configuration :

![Git add config](screenshots/image9.png)

---

## Étape 4 : Push des données vers le remote DVC

Envoyer les données vers le remote :

![DVC push](screenshots/image10.png)

Vérifier que le dossier `dvc_storage/` contient des fichiers de hash :

![DVC storage](screenshots/image11.png)

---

## Étape 5 : Simulation d’une collaboration (suppression et récupération)

Supprimer localement le dataset :

![Delete local data](screenshots/image12.png)

Vérifier que le fichier n’existe plus :

![Empty data folder](screenshots/image13.png)

Récupérer les données depuis DVC :

![DVC pull](screenshots/image14.png)

---

## Étape 6 : Versionner les données transformées

Ajouter les données transformées au suivi DVC :

![DVC add processed data](screenshots/image15.png)

Puis :

![Git add processed](screenshots/image16.png)

Enfin :

![Git commit processed](screenshots/image17.png)

### Résultat attendu
Toutes les données nécessaires au pipeline ML sont versionnées proprement et traçables.

---

## Étape 7 : Création d’un pipeline reproductible (`dvc.yaml`)

Créer le pipeline :

![DVC stage prepare](screenshots/image18.png)

Ajouter l’étape d’entraînement :

![DVC stage train](screenshots/image19.png)

Ajouter l’évaluation du modèle :

![DVC stage evaluate](screenshots/image20.png)

Versionner le pipeline :

![Git add dvc yaml](screenshots/image21.png)

### Résultat attendu
DVC enregistre dans `dvc.yaml` :
- Les dépendances
- Les sorties
- Les commandes du pipeline

---

## Étape 8 : Reproduction automatique du pipeline

Ajouter un `print` dans `src/prepare_data.py` :

![Modify prepare_data](screenshots/image22.png)

Observer l’impact sur le pipeline :

![DVC repro](screenshots/image23.png)

### Résultat attendu
Seules les étapes impactées sont réexécutées, garantissant une reproductibilité totale.

---

## Conclusion

Ce lab démontre la puissance de **DVC** dans un contexte MLOps :

- Séparation claire entre code, données et modèles
- Versionnement efficace des datasets volumineux
- Pipelines reproductibles et traçables
- Base solide pour la collaboration et l’industrialisation ML

DVC devient ainsi un pilier essentiel d’un système MLOps fiable et professionnel.
