 # Système de Gestion des Évaluations des Enseignants
 
## Description
Ce projet est un système de gestion des évaluations des enseignants développé en Java avec une base de données SQL. Il permet de gérer les enseignants, les étudiants et les évaluations faites par les étudiants concernant les enseignants.
## Objectifs
 - Améliorer la qualité de l'enseignement en permettant aux étudiants de donner leur feedback
- Faciliter la prise de décision pour les responsables académiques grâce aux données quantitatives et qualitatives
- Centraliser les données des enseignants, étudiants et évaluations dans un système unifié
- Permettre des analyses statistiques avec des outils comme les graphiques
- Assurer la confidentialité des données et l'intégrité du processus
## Structure de la Base de Données
### Tables

- Enseignant (id, nom, prénom, matière)
- Etudiant (id, nom, prénom, email)
- Evaluation (id, enseignant, etudiant, note, commentaire)

### Requêtes SQL pour créer les tables:
```sql
CREATE TABLE `enseignant` (
    `id` INT PRIMARY KEY AUTO_INCREMENT,
    `nom` VARCHAR(50) NOT NULL,
    `prenom` VARCHAR(50) NOT NULL,
    `matiere` VARCHAR(100) NOT NULL
);

CREATE TABLE `etudiant` (
    `id` INT PRIMARY KEY AUTO_INCREMENT,
    `nom` VARCHAR(50) NOT NULL,
    `prenom` VARCHAR(50) NOT NULL,
    `email` VARCHAR(100) UNIQUE NOT NULL
);

CREATE TABLE `evaluation` (
    `enseignant` INT NOT NULL,
    `etudiant` INT NOT NULL,
    `note` DOUBLE NOT NULL,
    `commentaire` VARCHAR(255),
    PRIMARY KEY (enseignant, etudiant),
    FOREIGN KEY (enseignant) REFERENCES Enseignant(id),
    FOREIGN KEY (etudiant) REFERENCES Etudiant(id)
);
```
## Structure du code Java
---
### Beans (Modèles)

- Enseignant.java : Classe représentant un enseignant
- Etudiant.java : Classe représentant un étudiant
- Evaluation.java : Classe représentant une évaluation

### Services

- EnseignantService.java : Gestion des opérations CRUD pour les enseignants
- EtudiantService.java : Gestion des opérations CRUD pour les étudiants
- EvaluationService.java : Gestion des opérations CRUD pour les évaluations

### Connexion à la base de données
- Connexion.java : Classe singleton gérant la connexion à la base de données
### Interface DAO
- IDao.java : Interface définissant les opérations CRUD génériques
### Test 
- Test.java : Classe pour test le code.
### Architecture
L'application est basée sur une architecture client-serveur :
- Client : Une application Java développée avec NetBeans.
- Serveur : Une base de données MySQL pour stocker et récupérer les données.
- Interface Utilisateur : Développée avec SWING pour offrir une expérience utilisateur intuitive et facile à utiliser.

### Technologies Utilisées:

- NetBeans (Java) : Pour le développement de l’application.
- MySQL : Pour la gestion de la base de données.
- SWING : Pour l'interface graphique et rendre l’application facile à utiliser.
