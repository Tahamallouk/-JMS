# TP 9-1 — Java Message Service (JMS) avec Apache ActiveMQ

Ce projet correspond au **TP 9-1 dédié à Java Message Service (JMS)**.  
Il a pour objectif de mettre en œuvre la **communication asynchrone entre applications Java** en utilisant la spécification **JMS** et le broker **Apache ActiveMQ**.

Le TP couvre les deux modèles fondamentaux de messagerie JMS :
- **Point-to-Point (Queue)**
- **Publish / Subscribe (Topic)** avec gestion des **Durable Subscribers**

---

## 📌 Sommaire
1. Objectifs du TP  
2. Concepts JMS  
3. Stack technique  
4. Architecture du projet  
5. Modules du projet  
6. Broker ActiveMQ  
7. Démarrage rapide  
8. Tests et démonstrations  
9. Auteur  
10. Licence  

---

## 🎯 Objectifs du TP
- Comprendre le fonctionnement et l’architecture JMS
- Mettre en place un broker de messages
- Implémenter :
  - un **Producer**
  - un **Consumer**
- Manipuler :
  - les **Queues** (communication 1-to-1)
  - les **Topics** (communication 1-to-N)
- Tester le mécanisme des **Durable Subscribers**
- Observer l’échange des messages via la console ActiveMQ

---

## 🧠 Concepts JMS

### 🔹 Queue (Point-to-Point)
- Chaque message est consommé par un seul consumer
- Une fois traité, le message est retiré de la queue
- Modèle adapté aux traitements asynchrones

### 🔹 Topic (Publish / Subscribe)
- Les messages sont diffusés à plusieurs subscribers
- Les **Durable Subscribers** reçoivent les messages même s’ils étaient déconnectés

---

## 🛠️ Stack technique

| Technologie | Version |
|------------|--------|
| Java | 17 |
| JMS API | Jakarta JMS |
| Apache ActiveMQ | 6.1.4 |
| Maven | ✔ |
| IntelliJ IDEA | Ultimate |
| Système | macOS |

---

## 🏗️ Architecture du projet
tp9-1-jms-activemq/
├── jms-activemq-queue-example/
│ ├── JmsQueueProducer.java
│ ├── JmsQueueConsumer.java
│ └── Main.java
│
├── jms-activemq-topic-producer-example/
│ ├── Article.java
│ ├── IConstants.java
│ ├── JmsTopicProducer.java
│ └── Main.java
│
├── jms-activemq-topic-consumer-example/
│ ├── Article.java
│ ├── IConstants.java
│ ├── JmsTopicConsumer.java
│ └── Main.java
│
└── README.md

---

## 🧩 Modules du projet

| Module | Description |
|------|------------|
| jms-activemq-queue-example | Implémentation JMS basée sur les Queues |
| jms-activemq-topic-producer-example | Producer JMS pour les Topics |
| jms-activemq-topic-consumer-example | Consumer JMS avec abonnement durable |

---

## 🧱 Broker ActiveMQ
- **URL du broker** : `tcp://localhost:61616`
- **Console Web** : `http://localhost:8161/admin`
- **Login** : `admin`
- **Mot de passe** : `admin`

Apache ActiveMQ est utilisé comme **Message Oriented Middleware (MOM)** afin d’assurer l’échange asynchrone des messages.

---

## 🚀 Démarrage rapide

### 1️⃣ Prérequis
- Java 17
- Apache ActiveMQ 6.1.4
- IntelliJ IDEA
- Git

### 2️⃣ Lancer ActiveMQ

Depuis le terminal :
cd apache-activemq-6.1.4/bin
./activemq start

Accéder ensuite à la console web :
http://localhost:8161/admin

Identifiants :
- Login : `admin`
- Password : `admin`

---

## 🔗 Tests et démonstrations

## 👤 Auteur

**Mohammed Taha Mallouk**  
Étudiant Ingénieur — MIAGE  
TP réalisé dans le cadre du module J2EE  

Java · JMS · Apache ActiveMQ · Asynchronous Messaging

---

## 📄 Licence

Projet distribué sous **licence MIT**.  
Utilisation, modification et redistribution autorisées à des fins pédagogiques.

© 2025 — Mohammed Taha Mallouk

