# Student Management - Spring Boot REST API

Application Spring Boot pour la gestion des étudiants avec documentation Swagger/OpenAPI.

## 🚀 Technologies utilisées

- **Spring Boot 3.2.4**
- **Java 21**
- **MySQL 8**
- **Spring Data JPA** - Persistance des données
- **Hibernate** - ORM
- **Swagger/OpenAPI** - Documentation API
- **Maven** - Gestion des dépendances
- **Lombok** - Réduction du code boilerplate

## 📋 Prérequis

- Java 21 ou supérieur
- MySQL 8.0 ou supérieur
- Maven 3.6+
- IntelliJ IDEA (recommandé) ou tout autre IDE Java

## ⚙️ Configuration

### 1. Base de données MySQL

Créez la base de données :

```sql
CREATE DATABASE studentdb;
```

### 2. Configuration de l'application

Le fichier `src/main/resources/application.properties` contient :

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/studentdb?serverTimezone=UTC
spring.datasource.username=root
spring.datasource.password=

spring.jpa.show-sql=true
spring.jpa.properties.hibernate.format_sql=true
spring.jpa.hibernate.ddl-auto=update

server.port=8080
```

**Note :** Modifiez `spring.datasource.password` si votre MySQL a un mot de passe.

## 🏗️ Installation et exécution

### Compiler le projet

```bash
mvn clean install
```

### Lancer l'application

```bash
mvn spring-boot:run
```

L'application démarre sur **http://localhost:8080**

## 📚 Documentation API (Swagger)

Une fois l'application lancée, accédez à la documentation Swagger :

**http://localhost:8080/swagger-ui.html**

![Swagger UI](screenshots/swagger.png)

## 🗄️ Structure de la base de données

La table `student` est créée automatiquement avec la structure suivante :

| Colonne         | Type    | Description              |
|-----------------|---------|--------------------------|
| id              | INT     | Clé primaire (auto-incrémenté) |
| nom             | VARCHAR | Nom de l'étudiant        |
| prenom          | VARCHAR | Prénom de l'étudiant     |
| date_naissance  | DATE    | Date de naissance        |

![Base de données](screenshots/database.png)

## 🔌 Endpoints REST

### Créer un étudiant
```http
POST /students/save
Content-Type: application/json

{
  "nom": "LACHGAR",
  "prenom": "Mohamed",
  "dateNaissance": "1985-09-01"
}
```

### Récupérer tous les étudiants
```http
GET /students/all
```

### Supprimer un étudiant
```http
DELETE /students/delete/{id}
```

### Compter les étudiants
```http
GET /students/count
```

### Statistiques par année de naissance
```http
GET /students/byYear
```

## 🧪 Tests

Exécuter les tests unitaires :

```bash
mvn test
```

## 📁 Structure du projet

```
student-management/
├── src/
│   ├── main/
│   │   ├── java/com/example/student_management/
│   │   │   ├── controller/
│   │   │   │   └── StudentController.java
│   │   │   ├── entity/
│   │   │   │   └── Student.java
│   │   │   ├── repository/
│   │   │   │   └── StudentRepository.java
│   │   │   ├── service/
│   │   │   │   └── StudentService.java
│   │   │   └── StudentManagementApplication.java
│   │   └── resources/
│   │       └── application.properties
│   └── test/
│       └── java/com/example/student_management/
│           └── StudentControllerTest.java
├── pom.xml
└── README.md
```

## 🛠️ Corrections apportées

Les erreurs suivantes ont été corrigées :

✅ **Problèmes de compilation**
- Mise à jour Maven Compiler Plugin (3.11.0 → 3.13.0)
- Mise à jour Lombok (1.18.30 → 1.18.34)
- Ajout des arguments `--add-opens` pour compatibilité Java 21

✅ **Erreurs de code**
- Correction des types génériques `ResponseEntity` dans `StudentController`
- Tous les constructeurs utilisent maintenant des types explicites

## 👨‍💻 Auteur

Projet réalisé dans le cadre du TP Spring Boot et Swagger

## 📄 Licence

Ce projet est à usage éducatif.
