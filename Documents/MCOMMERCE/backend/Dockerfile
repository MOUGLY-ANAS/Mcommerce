# Utiliser une image de base Node.js
FROM node:18.16.0

# Définir le répertoire de travail dans le conteneur
WORKDIR /app/backend

# Copier les fichiers package.json et package-lock.json dans le répertoire de travail
COPY package.json ./

# Installer les dépendances du backend
RUN npm install

# Copier le reste des fichiers du backend dans le répertoire de travail
COPY . .

# Exposer le port sur lequel le backend écoute
EXPOSE 4000

# Définir la commande pour démarrer le backend
CMD [ "npm", "start" ]