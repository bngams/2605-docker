# syntax=docker/dockerfile:1

# FROM: choisir une image de base adaptée à l'application
# + taille, + sécu ...
# node:lts...
FROM node:24.15-alpine3.22

# Définir le répertoire de travail dans l'image
WORKDIR /app

# Optimiser les étapes de build et le cache
# éviter de rejouer le npm install à chaque fois
COPY package.json .
RUN npm install --production

# Copier le reste des fichiers après l'installation des dépendances
COPY . .

# possibilités HEALTHCHECK  
# (plus haut dans le Dockerfile pour éviter de refaire les étapes...)

# Avec un script de santé personnalisé
# COPY healthcheck.sh .
# RUN chmod +x healthcheck.sh
# HEALTHCHECK --interval=30s --timeout=30s --start-period=5s --retries=3 CMD ["./healthcheck.sh"]

# Avec une simple requête HTTP
# Attention à installer curl en amont
RUN apk update && apk add --no-cache curl
HEALTHCHECK --interval=30s --timeout=30s --start-period=5s --retries=3 CMD [ "curl", "-f", "http://localhost:3000" ]

# Lancement de l'application
CMD ["node", "src/index.js"]

# Documentation port exposé
EXPOSE 3000