# /!\ réflexions pour le choix du from
# EOL, compatibilité, taille de l'image, etc.
FROM node:24.15-alpine3.22

WORKDIR /app

# /!\ a ignorer les fichiers initules => .dockerignore
# COPY . .

# Optimiser les étapes de build et le cache
# éviter de rejouer le npm install à chaque fois
COPY package*.json ./
RUN npm install

# Copier le reste des fichiers après l'installation des dépendances
COPY . .

# Documentation de l'exposition du port
EXPOSE 80

# Commande de démarrage de l'application
CMD ["node", "index.js"]