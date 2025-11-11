# QR Bus App — Gestion de montée des étudiants

## Description
Application complète pour gérer la montée des étudiants dans un bus via QR codes sécurisés avec signature HMAC.
Comprend :

- Backend Express + SQLite
- Frontend React (Vite)
- Signature HMAC pour sécuriser les QR Codes
- Interface admin pour suivre et exporter les présences
- Dockerfiles pour frontend et backend
- docker-compose.yml pour exécution rapide

## Installation et lancement

### Avec Docker (recommandé)

1. Cloner ou extraire le projet
2. Lancer la stack :
```bash
docker compose up --build
```
3. Accéder au frontend : http://localhost:3000
4. Backend API : http://localhost:4000/api

### Sans Docker

**Backend :**
```bash
cd backend
npm install
cp .env.example .env  # modifier les clés API et HMAC_SECRET
node server.js
```

**Frontend :**
```bash
cd frontend
npm install
npm run dev
```

## Utilisation

- Ajouter des étudiants via le formulaire frontend
- Générer QR signé pour chaque étudiant
- Scanner le QR pour enregistrer la présence (vérification HMAC côté backend)
- Accéder à l'interface Admin pour filtrer et exporter les présences

## Sécurité

- HMAC secret ne doit **jamais** être exposé côté client
- Utiliser HTTPS en production
- Protéger l'accès à l'admin et aux API via clé/API Key ou JWT
- Prévoir rotation de clé HMAC pour ré-émission des QR Codes

## Structure du projet

```
qr-bus-app/
├── backend/       # Backend Express + SQLite + HMAC
├── frontend/      # Frontend React + QR Scanner / Generator / Admin
├── docker-compose.yml
├── README.md
```

## Commandes utiles Docker

- Build & lancer la stack : `docker compose up --build`
- Arrêter : `docker compose down`
- Voir logs backend : `docker logs -f qr_backend`
- Voir logs frontend : `docker logs -f qr_frontend`
