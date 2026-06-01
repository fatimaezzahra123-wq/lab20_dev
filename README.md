# 📒 NumberBook

Application Android connectée à un backend distant, développée dans le cadre du cours **Programmation Mobile : Android avec Java**.

---

## 🎥 Démo vidéo

[![Demo](https://img.shields.io/badge/YouTube-Voir%20la%20démo-red?logo=youtube)](https://youtu.be/kMGvMjFknTg?si=T3xntN5eL5dAtGTc)

---

## 📐 Architecture globale

```
Application Android
        │
        ▼
   Retrofit (HTTP)
        │
        ▼
  Backend PHP (XAMPP)
        │
        ▼
   MySQL (numberbook)
```

---

## 🗂️ Structure du projet Android

```
com.example.numberbook
│
├── Contact.java          # Modèle de données
├── ApiResponse.java      # Réponse JSON du serveur
├── ContactApi.java       # Interface Retrofit
├── RetrofitClient.java   # Configuration Retrofit
├── ContactAdapter.java   # Adapter RecyclerView
└── MainActivity.java     # Activité principale
```

---

## 🗂️ Structure du backend PHP

```
numberbook-api/
│
├── config/
│   └── Database.php       # Connexion PDO MySQL
│
├── model/
│   └── Contact.php        # Modèle métier
│
├── service/
│   └── ContactService.php # Logique d'accès aux données
│
└── api/
    ├── insertContact.php  # POST — Insérer un contact
    ├── getAllContacts.php  # GET  — Récupérer tous les contacts
    └── searchContact.php  # GET  — Rechercher par nom ou numéro
```

---

## ✨ Fonctionnalités

- 📋 Lecture des contacts système Android via `ContentResolver`
- 🔐 Gestion de la permission `READ_CONTACTS`
- 📱 Affichage dans un `RecyclerView`
- ☁️ Synchronisation des contacts vers un serveur MySQL distant
- 🔍 Recherche distante par nom ou numéro de téléphone
- 🌐 Communication HTTP via `Retrofit` + `Gson`

---

## 🛠️ Technologies utilisées

| Technologie | Rôle |
|---|---|
| Retrofit 2.11.0 | Communication HTTP avec le backend |
| Gson | Conversion JSON ↔ objets Java |
| RecyclerView | Affichage performant de la liste |
| ContentResolver | Accès aux contacts système Android |
| PHP + PDO | Backend REST |
| MySQL | Base de données distante |
| XAMPP | Serveur local Apache + MySQL |

---

## 🗄️ Base de données

```sql
CREATE DATABASE IF NOT EXISTS numberbook
CHARACTER SET utf8mb4
COLLATE utf8mb4_unicode_ci;

CREATE TABLE contact (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(150) NOT NULL,
    phone VARCHAR(50) NOT NULL,
    source VARCHAR(50) DEFAULT 'mobile',
    created_at DATETIME DEFAULT CURRENT_TIMESTAMP
);
```

---

## 🔗 Endpoints API

| Méthode | URL | Description |
|---|---|---|
| POST | `/api/insertContact.php` | Insérer un contact |
| GET | `/api/getAllContacts.php` | Récupérer tous les contacts |
| GET | `/api/searchContact.php?keyword=ali` | Rechercher par nom ou numéro |

---

## 🚀 Lancer le projet

### Backend
1. Installe **XAMPP**
2. Place le dossier `numberbook-api` dans `C:\xampp\htdocs\`
3. Démarre **Apache** et **MySQL**
4. Crée la base via phpMyAdmin

### Android
1. Clone le repo :
```bash
git clone https://github.com/TON_USERNAME/NumberBook.git
```
2. Ouvre dans **Android Studio**
3. Dans `RetrofitClient.java`, adapte l'URL :
   - Émulateur → `http://10.0.2.2/numberbook-api/api/`
   - Téléphone physique → `http://TON_IP/numberbook-api/api/`
4. Sync Gradle et lance **Run ▶️**

> Min SDK : 24 — Target SDK : 36

---

## 🧪 Tests réalisés

| Test | Résultat |
|---|---|
| Chargement des contacts système | ✅ |
| Demande de permission READ_CONTACTS | ✅ |
| Synchronisation vers MySQL | ✅ |
| Recherche distante par nom | ✅ |
| Affichage dans RecyclerView | ✅ |

---


## 👩‍💻 Auteur
FATIMAEZZAHRA ENNASSIRI
