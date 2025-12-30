# TP 8 — Architecture Microservices avec Spring Cloud (Bank App)

Ce projet correspond au **TP 8 portant sur l’architecture microservices**.  
Il vise la réalisation d’une **application bancaire distribuée** en s’appuyant sur **Spring Boot** et **Spring Cloud**, afin de mettre en pratique les concepts clés des architectures modernes orientées services.

L’application repose sur les composants suivants :
- Découverte automatique des services
- Centralisation de la configuration
- Passerelle API unique
- Microservices métier indépendants
- Communication inter-services
- Gestion de la résilience et des pannes

---

## 📌 Sommaire

1. Fonctionnalités  
2. Stack technique  
3. Architecture globale  
4. Microservices  
5. Ports & URLs  
6. Démarrage rapide  
7. Tests & démonstrations  
8. Auteur  
9. Licence  

---

## ✅ Fonctionnalités

### 🧩 Architecture Microservices
- Enregistrement et découverte des services grâce à **Eureka**
- Routage centralisé des requêtes via **Spring Cloud Gateway**
- Externalisation des configurations à l’aide de **Spring Cloud Config**
- Rechargement dynamique des paramètres via `/actuator/refresh`

### 🏦 Services métier
- **Customer Service**
  - Gestion des informations clients
  - Base de données H2 en mémoire
- **Account Service**
  - Gestion des comptes bancaires
  - Communication distante avec Customer Service
  - Mise en place d’un Circuit Breaker avec mécanisme de secours

### 🛡️ Résilience
- Utilisation de **Resilience4J**
- Activation automatique d’un fallback en cas d’indisponibilité
- Message retourné : `Source not available`

---

## 🛠️ Stack technique

| Technologie | Version |
|------------|--------|
| Java | 17 |
| Spring Boot | 3.5.8 |
| Spring Cloud | 2025.0.0 |
| Maven | ✔ |
| Eureka Server | ✔ |
| Spring Cloud Config | ✔ |
| Spring Cloud Gateway | ✔ |
| OpenFeign | ✔ |
| Resilience4J | ✔ |
| Spring Data JPA | ✔ |
| H2 Database | ✔ |

---

## 🏗️ Architecture globale
bank-app/
├── discovery-service/ # Serveur de découverte (Eureka)
├── config-service/ # Serveur de configuration centralisée
├── gateway-service/ # Passerelle API
├── customer-service/ # Microservice Client
├── account-service/ # Microservice Compte
└── README.md

### Architecture logique
Client
│
▼
API Gateway (9999)
│
├── CUSTOMER-SERVICE (8084)
└── ACCOUNT-SERVICE (8083)
│
└── OpenFeign → CUSTOMER-SERVICE

---

## 🧩 Microservices

| Service | Rôle |
|--------|------|
| discovery-service | Registre des services |
| config-service | Configuration centralisée |
| gateway-service | Point d’entrée unique |
| customer-service | Gestion des clients |
| account-service | Gestion des comptes avec Feign et Circuit Breaker |

---

## 🌐 Ports & URLs

| Service | Port | URL |
|--------|------|-----|
| Eureka Server | 8761 | http://localhost:8761 |
| Config Server | 8888 | http://localhost:8888 |
| Gateway | 9999 | http://localhost:9999 |
| Customer Service | 8084 | http://localhost:8084 |
| Account Service | 8083 | http://localhost:8083 |

---

## 🚀 Démarrage rapide

### Prérequis
- Java 17  
- Maven  
- Git  
- IntelliJ IDEA / VS Code  

### Ordre de démarrage
1. discovery-service  
2. config-service  
3. gateway-service  
4. customer-service  
5. account-service  

---

## 🔗 Tests & démonstrations

### Accès direct
- Clients :  
  http://localhost:8084/customers  
- Comptes :  
  http://localhost:8083/api/accounts  

### Accès via la Gateway
- Clients :  
  http://localhost:9999/CUSTOMER-SERVICE/customers  
- Comptes :  
  http://localhost:9999/ACCOUNT-SERVICE/api/accounts  
### Test du Circuit Breaker (Resilience4J)

1. Arrêter le service `customer-service`
2. Appeler l’endpoint suivant via la Gateway :
   
   http://localhost:9999/ACCOUNT-SERVICE/api/accounts/{id}

3. Résultat attendu :

```json
{
  "firstName": "Source not available",
  "lastName": "Source not available"
}
Rafraîchissement dynamique de la configuration

Modifier le fichier customer-service.properties dans le dépôt de configuration

Exécuter la requête suivante pour recharger la configuration :

POST http://localhost:8084/actuator/refresh

Vérifier la prise en compte de la nouvelle configuration :

GET http://localhost:8084/configTest

👤 Auteur

Mohammed Taha Mallouk
Étudiant Ingénieur — MIAGE
Projet académique portant sur l’architecture Microservices avec Spring Cloud

📄 Licence

Projet distribué sous licence MIT.
Utilisation, modification et redistribution autorisées à des fins pédagogiques.

© 2025 — Mohammed Taha Mallouk
