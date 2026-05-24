# Projet-CRM-Wiam-Louze
# MENUI LUXE — Système de Gestion des Commandes

> *L'art du sur-mesure, digitalisé.*

![Status](https://img.shields.io/badge/statut-en%20développement-yellow)
![License](https://img.shields.io/badge/licence-MIT-green)
![Version](https://img.shields.io/badge/version-1.0.0-blue)
![PRs Welcome](https://img.shields.io/badge/PRs-bienvenues-brightgreen)

<p align="center">
  <img src="./assets/logo.jpeg" alt="Menui Luxe Logo" width="200"/>
</p>

---

## 📖 Description du projet

**Menui Luxe** est une maison de menuiserie haut de gamme spécialisée dans le **sur-mesure de luxe** — portes, fenêtres, parquets, dressings et agencements d'exception. Cette application web métier est dédiée à la **gestion des commandes** de l'atelier. Elle centralise le suivi des commandes clients, la gestion des produits et matériaux, ainsi que le pilotage de l'activité via un tableau de bord analytique.

L'objectif est de remplacer les outils manuels (cahiers, fichiers Excel) par une solution numérique intuitive, accessible depuis n'importe quel appareil, permettant aux artisans et gestionnaires de gagner en efficacité et en traçabilité — à la hauteur de l'excellence **Menui Luxe**.

---

## ✨ Fonctionnalités principales

### 📦 Gestion des commandes
- Création, modification et suppression de commandes
- Suivi de l'état des commandes : `En attente` → `En cours` → `Prête` → `Livrée`
- Historique complet des commandes par client
- Génération de bons de commande en PDF

### 👤 Gestion des clients
- Fiche client complète (coordonnées, historique, notes)
- Recherche et filtrage avancés
- Association client ↔ commandes

### 🪚 Gestion des produits & matériaux
- Catalogue de produits (portes, fenêtres, parquets, panneaux, etc.)
- Gestion des stocks avec alertes de seuil bas
- Catégorisation et référencement des matériaux

### 📊 Tableau de bord
- Vue synthétique des commandes du jour / semaine / mois
- Chiffre d'affaires en temps réel
- Indicateurs clés : commandes en retard, produits en rupture
- Graphiques d'évolution de l'activité

### 📈 Statistiques & indicateurs (en Dirhams)

Le tableau de bord intègre des graphiques interactifs de suivi mensuel :

| Indicateur | Valeur 2024 |
|---|---|
| Total commandes | 1 248 |
| Chiffre d'affaires annuel | 3 124 000 DH |
| Panier moyen | 2 503 DH / commande |
| Meilleur mois | Juin (142 commandes — 355 000 DH) |

**Graphiques disponibles :**
- 📊 **Barres + courbe combinées** : nombre de commandes (axe gauche) et CA mensuel en DH (axe droit) — de janvier à décembre
- 🍩 **Anneau trimestriel** : répartition des commandes par trimestre (T1 21% / T2 30% / T3 26% / T4 23%)

> Tous les montants sont exprimés en **Dirhams marocains (DH / MAD)**.

### 🔐 Authentification & rôles
- Connexion sécurisée (JWT)
- Rôles : `Administrateur`, `Gestionnaire`, `Vendeur`

---

## 🛠️ Stack technique

| Couche | Technologie |
|---|---|
| Frontend | React.js + Tailwind CSS |
| Backend | Node.js + Express.js |
| Base de données | MongoDB (Mongoose) |
| Authentification | JWT + bcrypt |
| PDF | PDFKit / react-pdf |
| Tests | Jest + Supertest |
| Déploiement | Docker + Nginx |

---

## 📁 Structure du projet

```
menuisorder/
├── client/                  # Frontend React
│   ├── public/
│   └── src/
│       ├── assets/
│       ├── components/      # Composants réutilisables
│       ├── pages/           # Pages principales
│       │   ├── Dashboard.jsx
│       │   ├── Commandes.jsx
│       │   ├── Clients.jsx
│       │   └── Produits.jsx
│       ├── services/        # Appels API
│       ├── store/           # Gestion d'état (Redux / Zustand)
│       └── App.jsx
│
├── server/                  # Backend Node.js
│   ├── config/              # Configuration DB, env
│   ├── controllers/         # Logique métier
│   ├── middleware/          # Auth, validation
│   ├── models/              # Schémas Mongoose
│   │   ├── Commande.js
│   │   ├── Client.js
│   │   └── Produit.js
│   ├── routes/              # Routes API
│   └── server.js
│
├── .env.example
├── docker-compose.yml
├── package.json
└── README.md
```

---

## 🚀 Installation & lancement en local

### Prérequis

- [Node.js](https://nodejs.org/) v18+
- [MongoDB](https://www.mongodb.com/) (local ou Atlas)
- [Git](https://git-scm.com/)

### Étapes

```bash
# 1. Cloner le dépôt
git clone https://github.com/votre-utilisateur/menuisorder.git
cd menuisorder

# 2. Configurer les variables d'environnement
cp .env.example .env
# Remplir les valeurs dans le fichier .env

# 3. Installer les dépendances (backend)
cd server
npm install

# 4. Installer les dépendances (frontend)
cd ../client
npm install

# 5. Lancer l'application en développement
# Terminal 1 — Backend
cd server && npm run dev

# Terminal 2 — Frontend
cd client && npm start
```

L'application sera accessible sur [http://localhost:3000](http://localhost:3000)

### 🐳 Lancement avec Docker

```bash
docker-compose up --build
```

---

## 🔌 Aperçu des endpoints API

### Commandes
| Méthode | Endpoint | Description |
|---|---|---|
| `GET` | `/api/commandes` | Liste toutes les commandes |
| `GET` | `/api/commandes/:id` | Détail d'une commande |
| `POST` | `/api/commandes` | Créer une commande |
| `PUT` | `/api/commandes/:id` | Modifier une commande |
| `DELETE` | `/api/commandes/:id` | Supprimer une commande |

### Clients
| Méthode | Endpoint | Description |
|---|---|---|
| `GET` | `/api/clients` | Liste tous les clients |
| `POST` | `/api/clients` | Ajouter un client |
| `PUT` | `/api/clients/:id` | Modifier un client |

### Produits
| Méthode | Endpoint | Description |
|---|---|---|
| `GET` | `/api/produits` | Liste tous les produits |
| `POST` | `/api/produits` | Ajouter un produit |
| `PUT` | `/api/produits/:id` | Modifier un produit |

### Authentification
| Méthode | Endpoint | Description |
|---|---|---|
| `POST` | `/api/auth/login` | Connexion utilisateur |
| `POST` | `/api/auth/logout` | Déconnexion |

---

## 🗺️ Roadmap

- [x] Initialisation du projet
- [ ] Module Authentification
- [ ] CRUD Commandes
- [ ] CRUD Clients
- [ ] CRUD Produits & Stocks
- [ ] Tableau de bord analytique
- [ ] Export PDF des bons de commande
- [ ] Notifications (email / in-app)
- [ ] Application mobile (React Native)

---

## 🤝 Contribution

Les contributions sont les bienvenues ! Pour contribuer :

1. Forkez le projet
2. Créez votre branche : `git checkout -b feature/ma-fonctionnalite`
3. Committez vos changements : `git commit -m 'feat: ajout de ma fonctionnalité'`
4. Poussez la branche : `git push origin feature/ma-fonctionnalite`
5. Ouvrez une **Pull Request**

Veuillez consulter le fichier [CONTRIBUTING.md](CONTRIBUTING.md) pour plus de détails.

---

## 📄 Licence

Ce projet est sous licence **MIT**. Voir le fichier [LICENSE](LICENSE) pour plus d'informations.

---

## 👨‍💻 Auteur

Développé avec ❤️ pour **Menui Luxe** — maison de menuiserie haut de gamme, spécialiste du sur-mesure de luxe au Maroc.

> *"L'art du sur-mesure, digitalisé."*
