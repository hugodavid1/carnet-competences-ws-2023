# Docker

> ✔️ Auto validation par l'étudiant

## 🎓 J'ai compris et je peux expliquer

- la création d'une image docker ✔️
- l'éxécution d'un container ✔️
- l'orchestration de containers avec docker-compose ✔️

## 💻 J'utilise

### Un exemple personnel commenté ✔️

Docker compose (dev) utilisé dans le cadre de notre projet de group

```yaml
services:
  backend: # service name
    build: # building
      context: ./2023-09-wns-rouge-renthub-back # where building image
      target: dev #building dev case in Dockerfile
    ports:
      - 5000:5000
    volumes:
      - ./2023-09-wns-rouge-renthub-back/src/:/app/src/ #volume (memory) in container
      - assets:/app/public/ #assets (images, fonts etc...) in our container
    env_file: ./2023-09-wns-rouge-renthub-back/.env # env file path
  postgres:
    image: postgres
    env_file: ./2023-09-wns-rouge-renthub-back/.env
    volumes:
      - postgres-data:/var/lib/postgresql/data
    ports:
      - "5433:5432"
  frontend:
    build:
      context: ./2023-09-wns-rouge-renthub-front
      target: dev
    ports:
      - 3001:3000 # local:container
    volumes:
      - ./2023-09-wns-rouge-renthub-front/src:/app/src
volumes:
  postgres-data:
  assets:
```

### Utilisation dans un projet ✔️

Docker compose utilisé dans un projet d'école (the good corner)

[[text](https://github.com/hugodavid1/the-good-corner/tree/dev)](...)

### Utilisation en production si applicable ✔️

```yaml
services:
  backend:
    image: renthub/backend:latest
    environment:
      - POSTGRES_DB=renthub
      - POSTGRES_USER=megakrash
      - POSTGRES_PASSWORD=r541bCPpxFwBBZB8
      - DB_PORT=5432
      - DB_PORT_LOCAL=5434
      - DB_HOST=postgres
      - DB_HOST_LOCAL=localhost/127.0.0.1
      - DOCKER_LOGS=false
      - BACKEND_PORT=5000
      - FRONTEND_URL=http://localhost:3000
      - MAIL_HOST=ssl0.ovh.net
      - MAIL_PORT=587
      - MAIL_USER=contact@renthub.shop
      - MAIL_PASSWORD=r541bCPpxFwBBZB8
      - RECAPTCHA_SECRET_KEY=6LctKSQpAAAAAL2L3b-MLjme0l1vtLbGrxIH13M3
      - JWT_SECRET_KEY=4de7484e5d63f0739cacc469b44ceb42b9c3e8cfd317c443e3e16c0c3d53cbb3
      - JWT_VERIFY_EMAIL_SECRET_KEY=LTz29f+zpPAbrDactZIR4OP94WzPPW24C8uXr+AUlikug6+GmTgOZsoHs5Nh9pofP1tb9lHlczQLJHVdxu1ivQ5T
  postgres:
    image: postgres
    volumes:
      - /var/lib/postgresql/data
    environment:
      - POSTGRES_DB=renthub
      - POSTGRES_USER=megakrash
      - POSTGRES_PASSWORD=r541bCPpxFwBBZB8
  frontend:
    image: renthub/frontend:latest
  nginx:
    stop_grace_period: 0s
    image: nginx:1.21.3
    restart: always
    ports:
      - ${GATEWAY_PORT:-8000}:80
    volumes:
      - ./nginx.conf:/etc/nginx/nginx.conf
      - ./logs:/var/log/nginx
```

Description : Compose utilisé en production pour déployer notre application Renthub. Ici qu'un seul service "nginx" qui lui est accessible depuis l'exterieur grâce la variable {Gateway_PORT} sur le port 8000. Celle ci nous renverra sur le nginx de production qui lui redirigera vers les bon services front/back a travers l'utilisation des reverse proxy. On peut voir qu'on créer un fichier nginx.conf qui lui sera copier dans notre container pour permettre cette redirection.

### Utilisation en environement professionnel ✔️

Utilisé dans le cadre de l'alternance. (Application propriétaire, pas de possibilité de visionnage)

## 🌐 J'utilise des ressources

### Titre

- lien
- description

```

```
