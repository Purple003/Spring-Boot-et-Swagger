# Student Management - Spring Boot REST API

Application Spring Boot pour la gestion des étudiants avec documentation Swagger/OpenAPI.

## Technologies utilisées

- **Spring Boot 3.2.4**
- **Java 21**
- **MySQL 8**
- **Spring Data JPA** - Persistance des données
- **Hibernate** - ORM
- **Swagger/OpenAPI** - Documentation API
- **Maven** - Gestion des dépendances
- **Lombok** - Réduction du code boilerplate

## Prérequis

- Java 21 ou supérieur
- MySQL 8.0 ou supérieur
- Maven 3.6+
- IntelliJ IDEA (recommandé) ou tout autre IDE Java

## Configuration

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

## Installation et exécution

### Compiler le projet

```bash
mvn clean install
```

### Lancer l'application

```bash
mvn spring-boot:run
```

L'application démarre sur **http://localhost:8080**

## Documentation API (Swagger)

Une fois l'application lancée, accédez à la documentation Swagger :

**http://localhost:8080/swagger-ui.html**
<img width="1893" height="938" alt="Screenshot 2025-11-26 022039" src="https://github.com/user-attachments/assets/9636cb3c-cfd1-47b3-9ca3-76910cdec8ac" />


## Structure de la base de données

La table `student` est créée automatiquement avec la structure suivante :

| Colonne         | Type    | Description              |
|-----------------|---------|--------------------------|
| id              | INT     | Clé primaire (auto-incrémenté) |
| nom             | VARCHAR | Nom de l'étudiant        |
| prenom          | VARCHAR | Prénom de l'étudiant     |
| date_naissance  | DATE    | Date de naissance        |

<img width="1276" height="557" alt="Screenshot 2025-11-26 022101" src="https://github.com/user-attachments/assets/80d7551d-9e1e-447a-8ba9-8be279da44c9" />


## Endpoints REST

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

## Tests

Exécuter les tests unitaires :

```bash
mvn test
```

## Structure du projet

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



## Auteur
Arroche Aya


