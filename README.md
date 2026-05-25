# Projet-CRM-Wiam-Louze
# 🪵 MenuiOrder — Gestion des Commandes Menuiserie

<div align="center">

![Version](https://img.shields.io/badge/version-1.0.0-blue?style=for-the-badge)
![Status](https://img.shields.io/badge/status-en%20développement-orange?style=for-the-badge)
![License](https://img.shields.io/badge/licence-MIT-green?style=for-the-badge)
![React](https://img.shields.io/badge/React-18-61DAFB?style=for-the-badge&logo=react&logoColor=white)
![Node](https://img.shields.io/badge/Node.js-20-339933?style=for-the-badge&logo=nodedotjs&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-15-4169E1?style=for-the-badge&logo=postgresql&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-5-3178C6?style=for-the-badge&logo=typescript&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-ready-2496ED?style=for-the-badge&logo=docker&logoColor=white)

**Application web de gestion des commandes pour Menui Luxe**
*Menuiserie haut de gamme — Cycle complet : devis → fabrication → pose → facturation → SAV*

[Démo live](#) · [Documentation API](#) · [Signaler un bug](../../issues) · [Proposer une fonctionnalité](../../issues)

</div>

---

## 📋 Table des matières

- [À propos du projet](#-à-propos-du-projet)
- [Fonctionnalités](#-fonctionnalités)
- [Stack technique](#-stack-technique)
- [Architecture du projet](#-architecture-du-projet)
- [Installation](#-installation)
- [Utilisation](#-utilisation)
- [API Reference](#-api-reference)
- [Roadmap](#-roadmap)
- [Contribuer](#-contribuer)
- [Licence](#-licence)

---

## 🏢 À propos du projet

**MenuiOrder** est une application web métier développée pour **Menui Luxe**, entreprise spécialisée dans la fabrication et la pose de menuiseries haut de gamme (portes, fenêtres, volets, agencements sur mesure).

### Problème résolu

Avant ce projet, la gestion des commandes reposait sur des outils dispersés :
- Devis sur tableurs Excel non centralisés
- Suivi de fabrication par email
- Planning de pose sur tableau blanc
- Facturation manuelle avec risque d'oubli
- Aucune traçabilité SAV

> **MenuiOrder** centralise l'intégralité du cycle de commande dans une seule interface, du premier contact client jusqu'au suivi après-vente.

### Cycle de commande couvert

```
PROSPECT → DEVIS → SIGNATURE → COMMANDE FOURNISSEUR → FABRICATION → PLANIFICATION POSE → RÉCEPTION → FACTURATION → SAV
```

---

## ✨ Fonctionnalités

### 📁 Gestion des clients
- Fiche client complète (coordonnées, historique, notes)
- Segmentation B2B / B2C (particuliers, architectes, promoteurs)
- Historique de toutes les commandes, devis et interventions
- Notifications SMS et email automatiques

### 📝 Devis et commandes
- Création de devis avec catalogue produits (bois, PVC, aluminium)
- Calcul automatique HT / TTC avec gestion de la TVA
- Gestion des produits sur mesure et variantes
- Statuts de devis : `brouillon` → `envoyé` → `accepté` → `refusé` → `expiré`
- Relance automatique des devis non signés
- Signature électronique intégrée
- Conversion devis → bon de commande en 1 clic
- Génération automatique des commandes fournisseurs à la signature

### 🏭 Suivi de fabrication
- Tableau de bord de production (kanban)
- Suivi des délais fournisseurs
- Alertes sur retards de livraison
- Gestion des stocks et approvisionnements

### 📅 Planning des poses
- Calendrier partagé des équipes de pose
- Attribution des chantiers par disponibilité
- Accès mobile aux fiches chantier (adresse, plans, notes)
- Export PDF du planning hebdomadaire

### 🔧 Réception chantier
- Rapport de pose numérique (tablette / mobile)
- Prise de photos directement intégrée
- Signature électronique du client sur site
- Archivage automatique dans la fiche client

### 💶 Facturation
- Génération de facture depuis la commande (sans ressaisie)
- Suivi des paiements et relances automatiques
- Conformité facturation électronique (norme française, sept. 2026)
- Export comptable : Sage, EBP, CSV

### 🛠️ SAV
- Création de tickets SAV depuis la fiche commande
- Suivi des interventions et garanties
- Historique des réclamations par client et par chantier
- Planification des entretiens périodiques

### 📊 Tableau de bord
- KPI en temps réel : CA en cours, devis en attente, chantiers planifiés
- Graphiques de performance commerciale
- Alertes et notifications centralisées

---

## 🛠️ Stack technique

| Couche | Technologie | Version |
|--------|-------------|---------|
| **Frontend** | React + TypeScript | 18 / 5 |
| **UI Framework** | Tailwind CSS | 3.x |
| **Composants UI** | shadcn/ui | latest |
| **State management** | Zustand | 4.x |
| **Requêtes API** | TanStack Query | 5.x |
| **Formulaires** | React Hook Form + Zod | latest |
| **Backend** | Node.js + Express | 20 / 4.x |
| **ORM** | Prisma | 5.x |
| **Base de données** | PostgreSQL | 15 |
| **Authentification** | JWT + bcrypt | — |
| **Upload fichiers** | Multer + S3 | — |
| **Email / SMS** | Nodemailer + Twilio | — |
| **PDF** | Puppeteer | latest |
| **Tests** | Vitest + Supertest | — |
| **Conteneurisation** | Docker + Docker Compose | — |
| **CI/CD** | GitHub Actions | — |

---

## 📁 Architecture du projet

```
menuiorder/
├── 📂 client/                    # Application React (frontend)
│   ├── 📂 src/
│   │   ├── 📂 components/        # Composants réutilisables
│   │   │   ├── 📂 ui/            # Composants de base (shadcn)
│   │   │   ├── 📂 forms/         # Formulaires métier
│   │   │   └── 📂 layouts/       # Structures de page
│   │   ├── 📂 pages/             # Pages de l'application
│   │   │   ├── Dashboard.tsx
│   │   │   ├── Clients.tsx
│   │   │   ├── Commandes.tsx
│   │   │   ├── Devis.tsx
│   │   │   ├── Planning.tsx
│   │   │   ├── Facturation.tsx
│   │   │   └── SAV.tsx
│   │   ├── 📂 hooks/             # Hooks personnalisés
│   │   ├── 📂 stores/            # État global (Zustand)
│   │   ├── 📂 services/          # Appels API
│   │   ├── 📂 types/             # Types TypeScript
│   │   └── 📂 utils/             # Fonctions utilitaires
│   └── package.json
│
├── 📂 server/                    # API REST (backend)
│   ├── 📂 src/
│   │   ├── 📂 controllers/       # Logique des routes
│   │   │   ├── clients.controller.ts
│   │   │   ├── commandes.controller.ts
│   │   │   ├── devis.controller.ts
│   │   │   ├── planning.controller.ts
│   │   │   ├── facturation.controller.ts
│   │   │   └── sav.controller.ts
│   │   ├── 📂 routes/            # Définition des routes
│   │   ├── 📂 middlewares/       # Auth, validation, erreurs
│   │   ├── 📂 services/          # Logique métier
│   │   ├── 📂 prisma/            # Schéma et migrations BDD
│   │   │   └── schema.prisma
│   │   └── 📂 utils/             # PDF, email, SMS
│   └── package.json
│
├── 📂 .github/
│   └── 📂 workflows/
│       ├── ci.yml                # Tests automatiques
│       └── deploy.yml            # Déploiement automatique
│
├── docker-compose.yml            # Configuration Docker
├── docker-compose.dev.yml        # Configuration développement
└── README.md
```

---

## 🚀 Installation

### Prérequis

Assurez-vous d'avoir installé :

- [Node.js](https://nodejs.org/) >= 20.x
- [Docker](https://www.docker.com/) >= 24.x
- [Git](https://git-scm.com/)

### 1. Cloner le dépôt

```bash
git clone https://github.com/menui-luxe/menuiorder.git
cd menuiorder
```

### 2. Configurer les variables d'environnement

```bash
# Backend
cp server/.env.example server/.env

# Frontend
cp client/.env.example client/.env
```

Renseigner les variables dans `server/.env` :

```env
# Base de données
DATABASE_URL="postgresql://user:password@localhost:5432/menuiorder"

# Authentification
JWT_SECRET="votre_secret_jwt_ultra_securise"
JWT_EXPIRES_IN="7d"

# Email (Nodemailer)
SMTP_HOST="smtp.gmail.com"
SMTP_PORT=587
SMTP_USER="votre@email.com"
SMTP_PASS="votre_mot_de_passe"

# SMS (Twilio)
TWILIO_ACCOUNT_SID="ACxxxxxxxx"
TWILIO_AUTH_TOKEN="xxxxxxxx"
TWILIO_PHONE_NUMBER="+33xxxxxxxxx"

# Stockage fichiers (AWS S3 ou compatible)
S3_BUCKET="menuiorder-uploads"
S3_REGION="eu-west-3"
S3_ACCESS_KEY="xxxxxxxx"
S3_SECRET_KEY="xxxxxxxx"

# Environnement
NODE_ENV="development"
PORT=3001
```

### 3. Lancer avec Docker (recommandé)

```bash
# Démarrer tous les services (BDD + backend + frontend)
docker-compose -f docker-compose.dev.yml up -d

# Vérifier que les conteneurs tournent
docker-compose ps
```

### 4. Lancer sans Docker (développement)

```bash
# Installer les dépendances
cd server && npm install
cd ../client && npm install

# Lancer PostgreSQL (via Docker uniquement pour la BDD)
docker run -d \
  --name menuiorder-db \
  -e POSTGRES_USER=user \
  -e POSTGRES_PASSWORD=password \
  -e POSTGRES_DB=menuiorder \
  -p 5432:5432 \
  postgres:15

# Appliquer les migrations Prisma
cd server && npx prisma migrate dev

# Injecter les données de démonstration
npx prisma db seed

# Lancer backend et frontend en parallèle
npm run dev        # depuis /server  → http://localhost:3001
npm run dev        # depuis /client  → http://localhost:5173
```

---

## 💻 Utilisation

### Accès à l'application

| Service | URL |
|---------|-----|
| Application web | http://localhost:5173 |
| API REST | http://localhost:3001/api |
| Documentation API (Swagger) | http://localhost:3001/api/docs |
| Prisma Studio (BDD) | http://localhost:5555 |

### Comptes de démonstration

| Rôle | Email | Mot de passe |
|------|-------|--------------|
| Administrateur | admin@menuiluxe.fr | `Admin1234!` |
| Commercial | commercial@menuiluxe.fr | `Demo1234!` |
| Poseur | poseur@menuiluxe.fr | `Demo1234!` |

### Commandes utiles

```bash
# Générer une migration après modification du schéma Prisma
npx prisma migrate dev --name nom_de_la_migration

# Ouvrir l'interface graphique de la BDD
npx prisma studio

# Lancer les tests
npm run test

# Lancer les tests avec couverture
npm run test:coverage

# Build de production
npm run build

# Vérifier le linting
npm run lint
```

---

## 📡 API Reference

L'API REST complète est documentée via **Swagger UI** à l'adresse `/api/docs`.

### Principaux endpoints

```
# Authentification
POST   /api/auth/login
POST   /api/auth/logout
POST   /api/auth/refresh

# Clients
GET    /api/clients
POST   /api/clients
GET    /api/clients/:id
PUT    /api/clients/:id
DELETE /api/clients/:id

# Devis
GET    /api/devis
POST   /api/devis
GET    /api/devis/:id
PUT    /api/devis/:id
POST   /api/devis/:id/signer
POST   /api/devis/:id/convertir-commande

# Commandes
GET    /api/commandes
POST   /api/commandes
GET    /api/commandes/:id
PATCH  /api/commandes/:id/statut

# Planning
GET    /api/planning
POST   /api/planning/pose
PUT    /api/planning/pose/:id

# Facturation
GET    /api/factures
POST   /api/factures
GET    /api/factures/:id/pdf
POST   /api/factures/:id/envoyer

# SAV
GET    /api/sav
POST   /api/sav
GET    /api/sav/:id
PATCH  /api/sav/:id/statut
```

---

## 🗺️ Roadmap

### Version 1.0 — MVP *(en cours)*
- [x] Authentification et gestion des rôles
- [x] Gestion des clients
- [x] Création et gestion des devis
- [x] Conversion devis → commande
- [ ] Suivi de fabrication (kanban)
- [ ] Planning des poses
- [ ] Génération de factures PDF
- [ ] Module SAV

### Version 1.1 — Mobilité
- [ ] Application mobile React Native pour les poseurs
- [ ] Mode hors-ligne (offline first)
- [ ] Signature électronique sur tablette
- [ ] Prise de photos sur chantier

### Version 1.2 — Intégrations
- [ ] Connexion ERP (Sage, EBP)
- [ ] Synchronisation catalogue fabricants (HerculePro)
- [ ] Conformité facturation électronique (PDP, septembre 2026)
- [ ] Export comptable automatisé

### Version 2.0 — Intelligence
- [ ] Tableau de bord analytique avancé
- [ ] Prévision de chiffre d'affaires
- [ ] Alertes intelligentes sur délais
- [ ] Chatbot SAV automatisé

---

## 🤝 Contribuer

Les contributions sont les bienvenues ! Voici comment participer :

### Processus de contribution

```bash
# 1. Forker le dépôt
# 2. Créer une branche pour votre fonctionnalité
git checkout -b feature/nom-de-la-fonctionnalite

# 3. Commiter vos changements (convention Conventional Commits)
git commit -m "feat: ajout du module de planification des poses"

# 4. Pousser sur votre fork
git push origin feature/nom-de-la-fonctionnalite

# 5. Ouvrir une Pull Request
```

### Convention de commits

| Type | Description |
|------|-------------|
| `feat` | Nouvelle fonctionnalité |
| `fix` | Correction de bug |
| `docs` | Documentation uniquement |
| `style` | Formatage, pas de changement logique |
| `refactor` | Refactorisation du code |
| `test` | Ajout ou modification de tests |
| `chore` | Maintenance, dépendances |

### Standards de code

- TypeScript strict activé
- Linting : ESLint + Prettier
- Tests obligatoires pour toute nouvelle route API
- Couverture de code minimum : 70 %

---

## 📄 Licence

Ce projet est sous licence **MIT**. Voir le fichier [LICENSE](LICENSE) pour plus de détails.

```
MIT License — Copyright (c) 2026 Menui Luxe
```

---

## 👥 Auteurs

| Nom | Rôle | GitHub |
|-----|------|--------|
| Équipe Menui Luxe | Développement & conception | [@menui-luxe](https://github.com/menui-luxe) |

---

<div align="center">

Développé avec ❤️ pour **Menui Luxe** — Menuiserie haut de gamme

</div>
