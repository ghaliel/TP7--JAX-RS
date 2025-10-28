# 💰 Bank Account Management System — JAX-RS & Spring Boot

Un **système de gestion de comptes bancaires** développé avec **Spring Boot** et **JAX-RS (Jersey)**.  
Ce projet expose une **API RESTful complète** permettant la création, la consultation, la mise à jour et la suppression de comptes bancaires, avec **support JSON et XML**, et **base de données H2 en mémoire**.

---

## 📚 Table des matières
1. [Fonctionnalités](#-fonctionnalités)  
2. [Technologies utilisées](#-technologies-utilisées)  
3. [Prérequis](#-prérequis)  
4. [Installation](#-installation)  
5. [Configuration](#-configuration)  
6. [Utilisation](#-utilisation)  
7. [API Endpoints](#-api-endpoints)  
8. [Formats de données](#-formats-de-données)  
9. [Tests](#-tests)  
10. [Démonstration](#-démonstration)  
11. [Structure du projet](#-structure-du-projet)  
12. [Auteur](#-auteur)

---

## ✨ Fonctionnalités
- 💳 Créer un nouveau compte bancaire  
- 📖 Lister tous les comptes  
- 🔍 Consulter un compte par ID  
- ✏️ Mettre à jour un compte existant  
- 🗑️ Supprimer un compte  
- 📊 Gestion des types de comptes : **Courant** / **Épargne**  
- 📝 API RESTful construite avec **JAX-RS (Jersey)**  
- 🔄 Support des formats **JSON** et **XML**  
- 💾 Base de données **H2 en mémoire**

---

## 🛠️ Technologies utilisées
| Catégorie | Outil / Version |
|------------|----------------|
| Framework backend | **Spring Boot 3.5.7** |
| REST API | **JAX-RS (Jersey 3.1.1)** |
| Base de données | **H2 Database (In-Memory)** |
| ORM | **Spring Data JPA / Hibernate** |
| XML Binding | **JAXB 4.0** |
| Build Tool | **Maven** |
| Utilitaire | **Lombok** |
| Version Java | **Java 17** |

---

## 📦 Prérequis
Avant de commencer, assurez-vous d’avoir installé :
- ☕ **Java JDK 17+**
- 📦 **Maven 3.9+** (ou utilisez le wrapper fourni)
- 🔧 **Git**

---

## 🚀 Installation
```bash
# Cloner le projet
git clone <url-du-repository>
cd TP7-JAX-RS

# Compiler le projet
mvn clean install
```
Sous Windows :
mvn.cmd clean install


## ⚙️ Configuration
Fichier principal : src/main/resources/application.properties
# Application
spring.application.name=TP7-JAX-RS

# H2 Database
spring.datasource.url=jdbc:h2:mem:bankdb
spring.datasource.driverClassName=org.h2.Driver
spring.datasource.username=sa
spring.datasource.password=

# JPA / Hibernate
spring.jpa.database-platform=org.hibernate.dialect.H2Dialect
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true

# Console H2
spring.h2.console.enabled=true
spring.h2.console.path=/h2-console

# Jersey
spring.jersey.application-path=/api

## 💻 Utilisation
Démarrer l’application
```bash
mvn spring-boot:run
```
L’application sera disponible sur 👉 http://localhost:8082

Accéder à la console H2

👉 http://localhost:8082/h2-console

Paramètres :

JDBC URL : jdbc:h2:mem:bankdb  
Username : sa  
Password : (laisser vide)

🔌 API Endpoints
| Méthode    | Endpoint                   | Description                | Format     |
| ---------- | -------------------------- | -------------------------- | ---------- |
| **POST**   | `/api/banque/comptes`      | Créer un compte            | JSON / XML |
| **GET**    | `/api/banque/comptes`      | Récupérer tous les comptes | JSON / XML |
| **GET**    | `/api/banque/comptes/{id}` | Récupérer un compte par ID | JSON / XML |
| **PUT**    | `/api/banque/comptes/{id}` | Mettre à jour un compte    | JSON / XML |
| **DELETE** | `/api/banque/comptes/{id}` | Supprimer un compte        | —          |

## 🧾 Exemples de requêtes
curl -X POST http://localhost:8080/api/banque/comptes \
-H "Content-Type: application/json" \
-d '{
  "solde": 15000.50,
  "dateCreation": "2025-10-27",
  "type": "COURANT"
}'
Créer un compte (XML)
curl -X POST http://localhost:8080/api/banque/comptes \
-H "Content-Type: application/xml" \
-d '<compte>
  <solde>25000.00</solde>
  <dateCreation>2025-10-27</dateCreation>
  <type>EPARGNE</type>
</compte>'

## 📊 Formats de données

JSON
{
  "id": 1,
  "solde": 15000.50,
  "dateCreation": "2025-10-27",
  "type": "COURANT"
}
XML
<compte>
  <id>1</id>
  <solde>15000.50</solde>
  <dateCreation>2025-10-27</dateCreation>
  <type>COURANT</type>
</compte>
Types de comptes

COURANT : Compte courant

EPARGNE : Compte épargne

##🧪 Tests
Exécuter les tests unitaires :
```bash
mvn test
```
## 🎬 Démonstration
Litse Des Comptes:
<img width="1546" height="935" alt="Screenshot 2025-10-28 114826" src="https://github.com/user-attachments/assets/f048a3ad-300d-4fad-94e2-ef8744cb8027" />
Console H2 :
<img width="1060" height="469" alt="Screenshot 2025-10-28 114835" src="https://github.com/user-attachments/assets/e7770227-18f5-4877-b213-3e64ad7aa1e7" />


## 📁 Structure du projet

TP7-JAX-RS/


├── src/


│   ├── main/


│   │   ├── java/org/example/tp7jaxrs/


│   │   │   ├── Tp7JaxRsApplication.java


│   │   │   ├── config/MyConfig.java


│   │   │   ├── controllers/CompteRestJaxRSAPI.java


│   │   │   ├── entities/{Compte.java, TypeCompte.java}


│   │   │   └── repositories/CompteRepository.java


│   │   └── resources/application.properties


│   └── test/java/org/example/tp7jaxrs/


├── pom.xml


└── README.md


## 🧩 Description rapide

Tp7JaxRsApplication.java : Point d’entrée Spring Boot

MyConfig.java : Configuration de Jersey (JAX-RS)

CompteRestJaxRSAPI.java : Contrôleur REST principal

Compte.java / TypeCompte.java : Entités JPA

CompteRepository.java : Interface CRUD Spring Data JPA

## 👨‍💻 Auteur


Ghali EL ASRI-ghaliel



